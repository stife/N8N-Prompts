# N8N-Prompts

Kurze Sammlung gebrauchsfertiger Prompts und Prompt-Vorlagen für n8n-Workflows (z. B. OpenAI-, HTTP- oder Custom-LLM-Nodes). Ziel ist es, wiederverwendbare, getestete Prompts für häufige Automatisierungs‑ und Textverarbeitungsaufgaben bereitzustellen.

## Inhalt
- /prompts — nach Kategorie geordnete Prompt-Dateien (z. B. email, summarize, translate, extract)
- /examples — n8n-Beispiele bzw. minimal Workflows, die Prompts verwenden
- README.md — Überblick & Quick-Start

## Warum dieses Repo?
- Schnell einsatzfähige Prompt-Vorlagen für gängige Use-Cases
- Konsistente Struktur für einfache Integration in n8n-Workflows
- Community-getriebene Verbesserungen und Anpassungen

## Quick Start

1. Prompt auswählen (z. B. prompts/email/summarize-en.md).
2. Prompt in einen n8n-Node einfügen:
   - Bei Verwendung des OpenAI-/LLM-Nodes: setze das Prompt-Feld auf die ausgewählte Vorlage, ersetze Variablen mit Expressions wie {{ $json["body"] }}.
   - Bei Verwendung eines HTTP-Request-Nodes: sende den Prompt im Request-Body an die LLM-API.
3. Testen — bei Bedarf prompt-tunen.

Beispiel (OpenAI-/LLM-Node-Konfiguration, Pseudobeispiel):
```
Model: gpt-4o
Input: Du bist ein präziser Assistent. Fasse den folgenden Text zusammen:
{{ $json["text"] }}

Max tokens: 300
Temperature: 0.2
```

Beispiel-Prompt (Summarize — Deutsch):
```
Du bist ein präziser Assistent. Fasse den folgenden Text in maximal 5 Sätzen zusammen. Gib die Zusammenfassung in gut lesbarem Deutsch aus und liste optional 3 wichtige Stichpunkte.
Text:
{{input_text}}
```

## Kategorien (Vorschlag)
- summarize — Zusammenfassungen von Texten/Meetings
- extract — Extraktion strukturierter Daten (z. B. JSON) aus Freitext
- translate — Übersetzungen mit Kontext und Stilvorgaben
- email — Formulierung oder Zusammenfassung von E-Mails
- code — Code-Refactorings, Erklärungen, Tests

## Beitrag (How to contribute)
1. Fork the repo.
2. Erstelle einen Feature-Branch (z. B. add/summarize-de).
3. Lege deine Prompt-Datei unter einer geeigneten Kategorie an: prompts/<kategorie>/<kurzer-name>.md
   - Dateiname: lower-case, words-separated-by-dashes.md
   - Dateiformat: Markdown mit einer kurzen Beschreibung, Beispiel-Input und Output-Constraints
4. Öffne einen Pull Request mit einer kurzen Beschreibung und Beispiel-Outputs/Tests.

Beispiel-Datei-Struktur:
```
prompts/
  summarize/
    meeting-summary-de.md
examples/
  workflows/
    summarize-demo.json
```

## Best Practices für Prompts
- Explizit sein: gewünschte Form (Kurz, Stichpunkte, JSON-Schema)
- Kontext liefern: relevante Metadaten (Sprache, Ton, Format)
- Temperatur niedrig halten (0–0.3) für deterministische Ergebnisse
- Wenn strukturierter Output nötig ist, JSON-Schema als Anweisung beifügen

## Lizenz
MIT — siehe LICENSE

## Kontakt
Issues & PRs sind willkommen. Für Rückfragen: @stife (GitHub).