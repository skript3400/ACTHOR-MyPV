# Auslesen von AC-THOR MyPV

Die `myPV.html` Datei wurde nur als Skizze erstellt, sie dient nur als Ausgangspunkt zum
leichteren Auslesen des MyPV-Acthors/zur Visualisierung oder Weiterverarbeitung der Leistungsdaten des AC-THOR MyPV Geräts solange keine Dokumentation für die MyPV-API öffentlich ist. Im konkreten fall stellt die html-datei eine interaktive Webseite bereit, die es ermöglicht, die Leistungsdaten für verschiedene Jahre in Form eines Diagramms anzuzeigen.

## API-Call:
http://192.168.xxx.xxx/chart.jsn?chd=1&chm=1&chy=${year}&chpl=12&cht=2&cha=0&chp1=3&chp2=4  
Vermutete Bedeutung der Query-Parameter, dem offiziellen Webinterface entnommen
- chd chart date
- chm chart month
- chy chart year
- chpl chart plot points (12 for year, 24 for day, 31 for month)
- cht unknown
- cha unknown
- chp1 selector for 1st datapoint-type in json response e.g. 3: "Leistung"-Parameter
- chp2 selector for 2nd datapoint-type in json response e.g. 4: "Netz-Leistung"-Parameter 

## Funktion der Datei

Die Hauptfunktion der `myPV.html` Datei besteht darin, die Leistungsdaten des AC-THOR MyPV Geräts zu visualisieren. Dies wird durch ein GET-Request erzielt, welcher dem offiziellen Webinterface entnommen wurde.
Die genaue lokale IP muss vorher noch in der .html Datei geändert werden.
Die Webseite bietet folgende Funktionen:

- **Jahresauswahl**: Ein Dropdown-Menü ermöglicht die Auswahl des Jahres, für das die Leistungsdaten angezeigt werden sollen.
- **Datenabruf**: Beim Ändern der Jahresauswahl werden die entsprechenden Leistungsdaten vom Server abgerufen.
- **Diagrammerstellung**: Die abgerufenen Daten werden in einem Diagramm dargestellt, das mit der Chart.js Bibliothek erstellt wird.
- **Fehlerbehandlung**: Falls beim Abrufen der Daten ein Fehler auftritt, wird eine Fehlermeldung angezeigt.

## Technische Details
- **JavaScript-Funktionen**:
  - `populateYearOptions()`: Füllt das Dropdown-Menü mit den letzten fünf Jahren bis zum aktuellen Jahr.
  - `fetchData(year)`: Holt die Daten für das ausgewählte Jahr vom Server und gibt sie als JSON zurück.
  - `createChart()`: Erstellt das Diagramm basierend auf den abgerufenen Daten.