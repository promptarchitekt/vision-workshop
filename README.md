# Vision Workshop

Standalone-Webanwendung für den Realize Your Vision Workshop.

## Was es ist

Eine einzelne HTML-Datei (`public/index.html`) — keine Dependencies, kein Build-Step, kein Backend.  
Teilnehmer öffnen die URL, geben ihren Namen ein und arbeiten lokal im Browser.  
Daten werden per `localStorage` gespeichert (pro Person, per Name).

## Fragen & Struktur

| Block | Fragen | Thema |
|-------|--------|-------|
| 1 | 1–6 | Fundament (Vision, Mission, Werte, Why, USP) |
| 2 | 7–12 | Markt & Kunde (Persona, Problem, Lösung, Markt, Wettbewerb, Geschäftsmodell) |
| 3 | 13–16 | Umsetzung (Angebot, Vertrieb, Ressourcen, Roadmap) |
| 4 | 17–18 | Zahlen & Ziele |
| — | Pitch | 6-Element Pitch Builder mit Live-Vorschau |

## Features

- Auto-Save in localStorage (pro User-Name isoliert)
- JSON-Export der eigenen Antworten
- Insights-Tagging pro Frage (Muster / Erkenntnis / Differenzierung / Kompetenz / Offene Frage)
- Drucken / PDF-Export
- 100% offline-fähig — keine externen Requests

## Bekannte Grenze

Die aktuelle Session-Wiederaufnahme ist fuer Einzelgeraete sauber geeignet.
Wenn mehrere Teilnehmer denselben Browser auf demselben Geraet nutzen, sollte der Browser zwischen den Sessions getrennt oder geleert werden, da die Rueckkehrer-Logik derzeit nicht hart pro Person auswaehlt.

## Deploy (Vercel)

```bash
# Repo auf GitHub pushen, dann:
# vercel.com → New Project → GitHub Repo auswählen → Deploy
# Root Directory: / (nicht /public — Vercel erkennt public/ automatisch)
```

## Lokale Vorschau

```bash
cd public && python3 -m http.server 8080
# → http://localhost:8080
```

## Nächster Schritt: Supabase-Anbindung

Wenn zentrale Datensammlung gewünscht:  
`localStorage.setItem(...)` → `fetch('/api/save', { body: JSON.stringify(state) })`  
+ Supabase-Tabelle `workshop_responses (id, name, company, answers, insights, pitch, created_at)`
