# JukeBox
## ~avatar avatar @unplugged
Eine Jukebox mit dem @boardname@ programmieren lernen.


## ~ @unplugged
Lerne eine wenn dann Bedingung zu nutzen indem du eine Jukebox programmierst. 
Bei der Jukebox kannst du mit den Tasten A und B wählen welche Melodie abgespielt werden soll.


## Schritt 1: Lass eine Melodie abspielen
Nutze den Block ``||input:Wenn Knopf A+B gedrückt||`` und ``||music:SpieleMelodie [Dadadum] Widerholde [einmal||`` um die Melodie einemal apsielen zu lassen nachdem die Tasten A+B gedrückt wurden.
```blocks 
input.onButtonPressed(Button.AB, function () {
      music.startMelody(music.builtInMelody(Melodies.Dadadadum), MelodyOptions.Once)
      })
```

## Schritt 2: Mehrere Lieder speichern
Wenn du wie im Vorherigen Sritt nur diese Blöcke nutzt kannst du mit dem Calliope nur drei Melodien abspielen lassen. 
Z.B. 
- wenn Knopf a gedrückt wird spiele Dadadadum
- wenn Knopf b gedrückt wird spiele Entertainer
- wenn Knopf a+b gedrückt wird spiele Funk <br>
<p>
Um noch mehr Melodien verwenden zu können nehmen wir den ``||logic:Wenn dann ansonsten ||`` Block aus der Gruppe ``||logic:Logik ||`` und erweiteren diesen mit Klick auf das + Symbol.
Nun kann unter jeden einzelnen ``||logic:Wenn dann ||`` abschnitt eine Melodie geschoben werden.
Um später die Lieder auswählen zu können Verwenden wir die ``||variables:Variable ||`` ``||variables:Titelnummer ||``
Diese Variable kann mit den Vergleichen welche ebenfalls unter ``||logic:Logik ||`` zu finden sind mit einer Zahl z.B. von 1 bis 7 verglichen werden

```blocks
input.onButtonPressed(Button.AB, function () {
    if (Titelnummer == 1) {
        music.startMelody(music.builtInMelody(Melodies.Dadadadum), MelodyOptions.Once)
    } else if (Titelnummer == 2) {
        music.startMelody(music.builtInMelody(Melodies.Entertainer), MelodyOptions.Once)
    } else if (Titelnummer == 3) {
        music.startMelody(music.builtInMelody(Melodies.Ode), MelodyOptions.Once)
    } else if (Titelnummer == 4) {
        music.startMelody(music.builtInMelody(Melodies.Nyan), MelodyOptions.Once)
    } else if (Titelnummer == 5) {
        music.startMelody(music.builtInMelody(Melodies.Birthday), MelodyOptions.Once)
    } else if (Titelnummer == 6) {
        music.startMelody(music.builtInMelody(Melodies.Blues), MelodyOptions.Once)
    } else if (Titelnummer == 7) {
        music.startMelody(music.builtInMelody(Melodies.Chase), MelodyOptions.Once)
    }
})
```


## Schritt 3: Auswahl der Titelnummer
Nun soll mit den Blöcken ``||input:Wenn Knopf A gedrückt||`` bzw. ``||input:Wenn Knopf B gedrückt||`` die ``||variables:Titelnummer ||`` um eins veringert bzw. um eins erhöht werden. 
Nehme dazu den Block ``||variables:ändere [Titelnummer] um (1)||``
Nachdem ändern der Titelnummer soll dies auf dem Calliope mit ``||basic:Zeige Zahl ||`` angezeigt werden.
```blocks

let Titelnummer = 0
input.onButtonPressed(Button.A, function () {

        Titelnummer += -1

    basic.showNumber(Titelnummer)
})

input.onButtonPressed(Button.B, function () {

        Titelnummer += 1

    basic.showNumber(Titelnummer)
})


```

## Schritt 4 Verbessunger der Titelauswahl
Bisher sollte deine Jukebox auch schon funktioniert haben. Vielleicht hast du auch schon festgestellt, dass wenn du ganz oft auf den ``||input: Knopf B||`` druückst eine höhere ``||variables:Titelnummer ||`` wie 7 einstellen kannst obwohl unsere höchste Titelnummer die 7 ist. Um dies zu verhindern können wir wieder die ``|logic:wenn dann ansonsten Bedingung|`` verwenden.
Schiebe hierzu je eine ``|logic: wenn dann ansonsten|`` bedinungung unter die Blöcke ``||input:Wenn Knopf A gedrückt||`` bzw. ``||input:Wenn Knopf B gedrückt||``.
Diese ``|logic: wenn dann ansonsten|`` solltest du dann so lesen wie: <br>
wenn, Titelnummer > 0 dann <br>
ändere Titelnummer um -1 <br>
ansonsten <br>
setze Titelnummer auf 7 <br>
Nach der ``|logic: wenn dann ansonsten|`` bedinungung soll wieder die ``||basic:Zeige Zahl ||`` angezeigt werden <br>

Für die Taste B kannst du es ebenso versuchen nur, dass bei einer Titelnummer kleiner 7 diese erhöht und ansonsten auf 0 gesetzt werden soll.

```blocks
let Titelnummer = 0
input.onButtonPressed(Button.A, function () {
    if (Titelnummer > 0) {
        Titelnummer += -1
    } else {
        Titelnummer = 7
    }
    basic.showNumber(Titelnummer)
})
input.onButtonPressed(Button.B, function () {
    if (Titelnummer < 7) {
        Titelnummer += 1
    } else {
        Titelnummer = 0
    }
    basic.showNumber(Titelnummer)
})
```


## ~ @unplugged 

Es ist geschafft du solltest nun die Titelnummern deiner Jukebox durch schalten können und mit Druck beider Knöpfen den gewünschten Titel abspielen lassen. 
Um das Programm noch zu erweitern kannst du gerne versuchen Mithilfe der Blöcke aus dem bereich Musik deine eigene Melodie zu programmieren.


> Diese Seite bei [https://r00b1nh00d.github.io/einfachejukebox/](https://r00b1nh00d.github.io/einfachejukebox/) öffnen

## Als Erweiterung verwenden

Dieses Repository kann als **Erweiterung** in MakeCode hinzugefügt werden.

* öffne [https://makecode.calliope.cc/](https://makecode.calliope.cc/)
* klicke auf **Neues Projekt**
* klicke auf **Erweiterungen** unter dem Zahnrad-Menü
* nach **https://github.com/r00b1nh00d/einfachejukebox** suchen und importieren

## Dieses Projekt bearbeiten ![Build Status Abzeichen](https://github.com/r00b1nh00d/einfachejukebox/workflows/MakeCode/badge.svg)

Um dieses Repository in MakeCode zu bearbeiten.

* öffne [https://makecode.calliope.cc/](https://makecode.calliope.cc/)
* klicke auf **Importieren** und dann auf **Importiere URL**
* füge **https://github.com/r00b1nh00d/einfachejukebox** ein und klicke auf Importieren

## Blockvorschau

Dieses Bild zeigt den Blockcode vom letzten Commit im Master an.
Die Aktualisierung dieses Bildes kann einige Minuten dauern.

![Eine gerenderte Ansicht der Blöcke](https://github.com/r00b1nh00d/einfachejukebox/raw/master/.github/makecode/blocks.png)

#### Metadaten (verwendet für Suche, Rendering)

* for PXT/calliopemini
<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");</script>
