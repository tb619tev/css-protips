<p align="center">
  <img src="https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg" width="200" alt="light bulb icon">
</p>



# CSS Protips [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

Een verzameling tips om uw CSS skills pro.

>Voor andere grote lijsten check out  [@sindresorhus](https://github.com/sindresorhus/)'s curated list of [awesome lists](https://github.com/sindresorhus/awesome/).

## Inhoudsopgave


*[Protips](#protips)
*[Ondersteuning](#Ondersteuning)
*[vertalingen](#vertalingen)
*[bijdrage richtsnoeren](CONTRIBUTING.md)

## Protips

1.[Gebruik een CSS Reset](#Gebruik-een-CSS-Reset)
1.[erven'box-sizing'](#erven-box-sizing)
1.[gebruik :niet()/Unapply grenst aan Navigation](#gebruik :niet()/Unapply grenst aan Navigation)
1.[Add `line-height` to `body`](#add-line-height-to-body)
1.[Vertically-Center iets](#Vertically-Center-iets)
1.[kommagescheiden lijst](#kommagescheiden-lijst)
1.[Items selecteren met negatieve nth-kind](#Items-selecteren-met-negatieve-nth-kind)
1.[gebruik SVG voor pictogrammen](#gebruik-SVG-voor-pictogrammen)
1.[gebruiken de "Lobotomized Owl" Selector](#gebruiken-de-"Lobotomized-Owl"-Selector)
1.[Gebruik max hoogte voor pure CSS Sliders](#Gebruik-max-hoogte-voor-pure-CSS- Sliders)
1.[Equal-Width Tabelcellen](#Equal-Width-Tabelcellen)
1.[ontdoen van marge Hacks met Flexbox](#ontdoen-van-marge-Hacks-met-Flexbox)
1.[Gebruik Attribute Selectors met lege banden](#Gebruik-Attribute-Selectors-met-lege -banden)
1.[stijl "Default" Links](#stijl-"Default"-inks)
1.[consistente verticaal ritme](#consistente-verticaal-ritme)
1.[intrinsieke verhouding dozen](#intrinsieke-verhouding-dozen)
1.[stijl gebroken beelden](#stijl-gebroken-beelden)
1.[Gebruik rem voor wereldwijde omvang; Gebruik em voor lokale Sizing](#Gebruik-rem- voor-wereldwijde-omvang;-Gebruik-em voor-lokale-Sizing)
1.[Verberg Autoplay filmpjes die niet gedempt](#Verberg-Autoplay-filmpjes-die-niet-gedempt)
1.[gebruik :wortel voor een flexibele](#gebruik-:wortel-voor-een-flexibele)
1[.set font-size op formulier elementen voor een betere mobiele ervaring](#set-font-size-op-formulier-elementen-voor-een betere-mobiele-ervaring)


### Gebruik een CSS Reset

CSS resets gebruiksbeleid stijl consistentie tussen verschillende browsers met een schone lei voor styling elementen. U kunt een CSS reset bibliotheek zoals normaliseert, et al., of u kunt een eenvoudigere reset aanpak:

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

Nu elementen worden ontdaan van marges en paddings en 'box-sizing' helpt u bij het beheren van lay-outs met het CSS box model.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

""Opmerking:"" Als u de [erven'box-sizing'](#erven-box-sizing)tip hieronder ziet u soms niet de 'box-sizing 'eigendom in uw CSS gereset.


### Erven 'box-sizing'

laat 'box-sizing' overgeërfd worden van 'html':

```css
html {
  box-sizing: border-box;
}

*, *::before, *::after {
  box-sizing: inherit;
}
```



Dit maakt het gemakkelijker om 'box-sizing' in plugins of andere onderdelen die hefboomwerking ander gedrag.

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


### Gebruik ':niet()'/Unapply grenst aan navigatie in

plaats van over de grens...

```css
/* add border */
.nav li {
  border-right: 1px solid #666;
}
```

...En vervolgens uit het laatste element...

```css
/* remove border */
.nav li:last-child {
  border-right: none;
}
```


...De ':niet()' pseudo-klasse gelden alleen voor de elementen die u wilt:

```css
.nav li:not(:last-child) {
  border-right: 1px solid #666;
}
```


Zeker, kunt u '.nav li + li' of zelfs '.nav li:first-child ~ li,' maar met ':niet()'De intentie is zeer duidelijk en de CSS selector bepaalt de grenzen aan de manier waarop een mens zou beschrijven.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>

### Voeg line-height op

je niet hoeft toe te voegen 'line-height' op elk '<p>', '<h*>' et al. afzonderlijk. In plaats daarvan, toevoegen aan berichttekst `body`:

```css
body {
  line-height: 1.5;
}
```

#### [Demo](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>

Deze manier tekstgedeelten kan overnemen van `body` lichaam.



### Niets Vertically-Center


Nee, het is geen zwart magie, kunt u echt centrum elementen verticaal:

```css
html, body {
  height: 100%;
  margin: 0;
}

body {
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
  display: -webkit-flex;
  display: flex;
}
```

Wilt centrum iets anders? Verticaal, horizontaal...alles, altijd en overal? CSS-Tricks heeft een mooie write-up om op te doen[a nice write-up](https://css-tricks.com/centering-css-complete-guide/) .


**Opmerking**:Laat bij sommige buggy gedrag een  [buggy behavior](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) flexbox in IE11.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


### Kommagescheiden lijsten

maken lijstitems die eruit ziet als een echte, door komma's gescheiden lijst:


```css
ul > li:not(:last-child)::after {
  content: ",";
}
```

Gebruik de ':niet()' pseudo-class dus geen komma wordt toegevoegd aan het laatste item.


**Opmerking**: Deze tip is misschien niet ideaal voor toegankelijkheid, specifiek screenreaders. En kopiëren/plakken vanuit de browser werkt niet met CSS gegenereerd content. Ga voorzichtig te werk.

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


### Items selecteren met negatieve 'nth-kind'

Gebruik negatieve 'nth-kind' in CSS om items te kunnen selecteren van 1 tot n.

```css
li {
  display: none;
}

/* select items 1 through 3 and display them */
li:nth-child(-n+3) {
  display: block;
}
```


Of omdat u al hebt geleerd over het gebruik ':niet()', probeer dan[using `:not()`](#use-not-to-applyunapply-borders-on-navigation:


```css
/* select all items except the first 3 and display them */
li:not(:nth-child(-n+3)) {
  display: none;
}
```
Nou dat was vrij eenvoudig.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>



### Gebruik SVG voor pictogrammen
Er is geen enkele reden om geen gebruik te maken van SVG voor pictogrammen:

```css
.logo {
  background: url("logo.svg");
}
```

SVG weegschaal is goed voor alle soorten resolutie en wordt hierbij ondersteund door alle browsers die terug leid naar IE9(http://caniuse.com/#search=svg). Zo sloot het .png-, .jpg- of .gif-jif-whatev bestanden.

**Opmerking**: Als u SVG icon-alleen knoppen voor slechtzienden gebruikers en de SVG niet wordt geladen, dit zal bijdragen tot het behoud van toegankelijkheid:

```css
.no-svg .icon-only::after {
  content: attr(aria-label);
}
```

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>



###Gebruik de "Lobotomized Owl" Selector

Misschien een vreemde naam maar met behulp van de universele selector (*) met het aangrenzende broertje selector ( ) een krachtige CSS-functionaliteit:

```css
* + * {
  margin-top: 1.5em;
}
```

In dit voorbeeld worden alle elementen in de flow van het document , die hierbij andere elementen volgen en ontvangt 'margin-top': '1.5em'.

Voor meer informatie over de "lobotomized owl" selector, lees Heydon Pickering's post [Heydon Pickering's post](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls)op een lijst *A List Apart*.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>

###  Gebruik max hoogte voor pure CSS Sliders

werktuig CSS-only sliders met max hoogte met overloop verborgen:

```css
.slider {
  max-height: 200px;
  overflow-y: hidden;
  width: 300px;
}

.slider:hover {
  max-height: 600px;
  overflow-y: scroll;
}
```


Het element vormt de `max-height` max-hoogtewaarde op hangen en de schuifbalk geeft als gevolg van de overloop.

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>

### Equal-Width Tabelcellen

Tabellen kan moeizaam zijn om mee te werken, dus probeer met behulp van het 'tabel-layout': vast om cellen op gelijke breedte te stellen:


```css
.calendar {
  table-layout: fixed;
}
```

Pijn-vrij table layouts.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>

### Ontdoen van marge Hacks met Flexbox

bij het werken met kolom dakgoten kunt ontdoen van ne-, eerste- en laatste kind hacks via flexbox's space-tussen eigendom:


```css
.list {
  display: flex;
  justify-content: space-between;
}

.list .person {
  flex-basis: 23%;
}
```

Nu kolom dakgoten verschijnen altijd gelijkmatig verdeelde.

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


###  Gebruik attribuut Selectors met lege Links

links tonen wanneer de '<a>'-element heeft geen tekst, maar het 'href' attribuut heeft een link:

```css
a[href^="http"]:empty::before {
  content: attr(href);
}
```

Dat is best handig.

#### [Demo](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


#### Stijl "Default" Links

Voeg een stijl voor "default" links:

```css
a[href]:not([class]) {
  color: #008000;
  text-decoration: underline;
}
```

Nu links die ingevoegd via een CMS `class`, dat meestal niet een klassekenmerk, zal een onderscheid zonder boodschap die de cascade.

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>

### Consistente verticaal ritme

Gebruik een universele selector (*) binnen een element om een consistent verticaal ritme:

```css
.intro > * {
  margin-bottom: 1.25rem;
}
```

Consistente verticaal ritme geeft een visuele esthetiek die content wordt veel beter leesbaar zijn.

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


### Intrinsieke verhouding dozen


Een vak te maken met een intrinsieke verhouding, alles wat je hoeft te doen is van toepassing Top of Bottom padding aan een div:

```css
.container {
  height: 0;
  padding-bottom: 20%;
  position: relative;
}

.container div {
  border: 2px dashed #ddd;
  height: 100%;
  left: 0;
  position: absolute;
  top: 0;
  width: 100%;
}
```

Met 20% voor vulling maakt de hoogte van het vak gelijk aan 20% van de breedte. Ongeacht de breedte van het weergave venster kind div houdt zijn beeldverhouding (100%/20% = 5:1).

#### [Demo](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


### Stijl gebroken beelden

gebroken beelden meer esthetisch aangenaam met een beetje CSS:

```css
img {
  display: block;
  font-family: Helvetica, Arial, sans-serif;
  font-weight: 300;
  height: auto;
  line-height: 2;
  position: relative;
  text-align: center;
  width: 100%;
}
```

Voeg nu pseudo-elementen regels om een gebruiker bericht en URL referentie van het gebroken beeld:

```css
img::before {
  content: "We're sorry, the image below is broken :(";
  display: block;
  margin-bottom: 10px;
}

img::after {
  content: "(url: " attr(src) ")";
  display: block;
  font-size: 12px;
}
```

Meer informatie over styling voor dit patroon in [Ire Aderinokun](https://github.com/ireade/)'s [origineel bericht](http://bitsofco.de/styling-broken-images/).


<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


Gebruik 'rem' voor wereldwijde omvang; Gebruik 'em' voor lokale Sizing
na het instellen van de basis de lettergrootte op de hoofdpartitie ('html { font-size: 100%; }'); stel de lettergrootte voor tekstgedeelten 'em':

```css
h2 {
  font-size: 2em;
}

p {
  font-size: 1em;
}
```

Then set the font-size for modules to 'rem':

```css
article {
  font-size: 1.25rem;
}

aside .module {
  font-size: .9rem;
}
```

Now each module becomes compartmentalized and easier to style, more maintainable, and flexible.

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


### Verberg Autoplay filmpjes die niet gedempt

Is dit een geweldige truc voor een aangepaste user stylesheet. Voorkom overbelasting van een gebruiker met het geluid van een video die screen modus die afgespeeld word wanneer de pagina geladen is. Als het geluid niet gedempt wordt. Video moet niet gewezen worden (don't show video ) :

```css
video[autoplay]:not([muted]) {
  display: none;
}
```

Nogmaals, we profiteren van de :niet() [`:not()`](#use-not-to-applyunapply-borders-on-navigation)pseudo-class.

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


### Gebruik :wortel'root' voor flexibele Type

het type font size in een responsieve lay-out moet kunnen aanpassen met elk deelvenster. U berekent de tekengrootte op basis van het deelvenster hoogte en breedte met :wortel'root':


```css
:root {
  font-size: calc(1vw + 1vh + .5vmin);
}
```

Nu kunt u gebruik maken van de wortel , de eenheid dat is gebaseerd op de waarde dat is berekend door :wortel 'root':

```css
body {
  font: 1rem/1.6 sans-serif;
}
```
#### [Demo](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>


### Set 'font-size' op formulier elementen voor een betere mobiele ervaring


te vermijden mobiele browsers (iOS Safari, et al.) vanaf het inzoomen op een HTML formulier elementen als een <select> vervolgkeuzelijst wordt aangetikt, 'font-size' op de selectieschakelaar regel:

```css
input[type="text"],
input[type="number"],
select,
textarea {
  font-size: 16px;
}
```

:dancer:

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>

## Support

Current versions of Chrome, Firefox, Safari, Opera, Edge, and IE11.

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>

## Translations

* [Español](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/es-ES)
* [Français](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/fr-FR)
* [Italiano](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/it-IT)
* [日本語](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ja-JP)
* [Português do Brasil](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/pt-BR)
* [Русский](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/ru-RU)
* [简体中文](https://github.com/AllThingsSmitty/css-protips/tree/master/translations/zh-CN)

<sup>[terug naar inhoudsopgave](#tafel-van-inhoud)</sup>

