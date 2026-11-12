# Deutsche Formeln – persönliche Windows-Vorschau

Diese Arbeitskopie basiert exakt auf GridCraft **v0.19.1** und übernimmt die noch
nicht veröffentlichte deutsche Formelunterstützung aus dem bestehenden
[Upstream-PR #3020](https://github.com/storytold/gridcraft/pull/3020)
(Stand `be85a7826a209e605670f24274399ca2ab9c305f`). Die ursprüngliche Implementierung
und die Funktionstabelle stammen aus diesem Beitrag und dessen dort dokumentierter
Vorarbeit; sie werden hier nicht als eigene Neuentwicklung ausgegeben.

## Benutzung

1. Vorhandene Arbeitsmappen vor Tests sichern. Die Vorschau zunächst separat aus
   dem portablen ZIP starten, nicht die vorhandene Installation überschreiben.
2. **Ansicht → Anzeigesprache → Deutsch** auswählen (englische Oberfläche:
   **View → Interface language → Deutsch**).
3. Beispielsweise in leere Zellen eingeben:
   - `=SUMME(1,5;2,25)` ergibt **3,75**.
   - `=WENN(2>1;"Ja";"Nein")` ergibt **Ja**.
   - `=ZÄHLENWENN(A1:A10;">0")` zählt positive Werte.
4. Die Oberfläche zeigt deutsche Funktionsnamen; Engine, CLI, MCP, Steuerkanal und
   gespeicherte XLSX-Formeln behalten die kanonische englische Syntax.

## Umfang und Grenzen

- 420 übersetzte Funktionsnamen; Namen wie MAX und INDEX bleiben unverändert.
- Semikolon zwischen Argumenten, Dezimalkomma, WAHR/FALSCH, Unicode in
  Autovervollständigung und deutsche Fehlerliterale innerhalb von Formeln.
- Kein vollständiges deutsches Zahlen-/Datumsformatpaket: insbesondere ist der
  Punkt bei normaler Zahleneingabe **kein** deutscher Tausendertrenner.
- Strukturierte Tabellenbezeichner und als Zellresultat angezeigte Fehlerwerte
  bleiben im Umfang des übernommenen PR englisch.
- Dies ist eine **unsignierte Vorschau**, keine offizielle GridCraft-Veröffentlichung.
  Windows kann deshalb eine Herausgeber-/SmartScreen-Warnung anzeigen.
- Ein Update auf eine offizielle Version ohne diesen Patch ersetzt die Erweiterung.

## Erstellung und Prüfung

Der separate persönliche Workflow `German Windows preview` verwendet ausschließlich
vorhandene gemeinsame Upstream-Workflows: Windows-Tests über `gate.yml`, parallel dazu
Paketierung mit `release.yml` im Modus `dry-run`. Pakete dürfen erst nach erfolgreichen
Tests als geprüft weitergegeben werden. Er veröffentlicht keine Releases,
signiert keine Pakete und startet keine kostenpflichtigen macOS-Runner. Die gemeinsame
Paketierung erstellt zusätzlich die dort fest vorgesehenen Linux-/ARM-Pakete.
Die Eingriffe in die CI dienen nur dieser persönlichen Vorschau, nicht einem
Funktions-PR an das Originalprojekt.

Ein Quellcode-Commit oder gestarteter Workflow ist noch kein erfolgreich geprüftes
Windows-Paket. Maßgeblich sind die tatsächlichen Testergebnisse und heruntergeladenen
Artefakte des jeweiligen Laufs.
