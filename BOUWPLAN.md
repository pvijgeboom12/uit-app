# Bouwplan UIT-app – MVP "agenda eerst, kaart later"

Status: concept, 22 nov 2026. Wacht op akkoord van Pieter voordat er code komt.
Bron van besluiten: AGENT-doc "AGENT – UIT-app – overdracht" (Drive, map _AGENTS).

## 1. Wat de MVP is

Een gecureerde uitagenda voor Amsterdam, meteen publiek. Je opent de site en ziet wat er vanavond, dit weekend en deze week te doen is dat de moeite waard is. Curatie op smaak en sfeer, niet op volledigheid.

Wel: poptempels, cabaret, underground, live muziek in cafés, jazzcafés, DJ's en dance, R&B, plekken als Bitterzoet.
Niet: grote commerciële shows, ballet.

De buurtkaart komt later als tweede weergave op dezelfde data. Daarom slaan we vanaf dag één bij elke venue de coördinaten op.

## 2. Onderscheid

De concurrent is Mood (musicofourdesire.com), een Amsterdamse muziekfeed. Wij onderscheiden ons op breedte binnen een smaak: cabaret, jazzcafés en R&B naast elkaar, gekozen door een redactie en niet door een algoritme dat alles toont.

## 3. Stack (aanname, uit4 staat nog open)

Cloudflare Pages + D1 + Workers, net als Walhalla. Dan is er één stack, één werkwijze en één deploy-route. Het alternatief was Next.js + Supabase + Vercel. Kies je dat, dan veranderen alleen hoofdstuk 3 en 6.

## 4. Data

- Venues: een vaste startlijst met naam, buurt, adres, lat/lng, website, agenda-URL en genres. De lijst staat in het oude productgesprek en moet nog hierheen.
- Events: titel, venue, datum en tijd, genre-tags, prijs of "gratis", ticketlink en bron.
- Bronnen: (a) scrapen van de agendapagina's per venue, (b) nieuwsbrieven die binnenkomen op het nieuwsbriefadres (uit3), geparsed zoals bij Walhalla.
- TicketSwap alleen als deeplink, geen scraping.
- Curatie: elk event krijgt de status kandidaat, gekozen of afgewezen. Alleen "gekozen" is publiek. Een stijlgids met tien voorbeelden van wel en tien van niet (open punt 7) wordt de basis voor automatisch voorselecteren.

## 5. Schermen MVP

1. Agenda: vanavond, dit weekend en deze week, met een filter op genre.
2. Event-detail: wat, waar, wanneer, prijs, ticketlink en waarom wij het kiezen (één zin).
3. Venue-pagina: alle gekozen events van één plek.
4. Redactie (achter login, alleen Pieter): kandidaten goedkeuren of afwijzen.

Later: kaartweergave, nieuwsbrief, favorieten.

## 6. Fasering

| Fase | Wat | Klaar als |
|---|---|---|
| 0 | Besluiten: naam (uit2), adres (uit3), stack (uit4), venuelijst | Alles staat in het AGENT-doc |
| 1 | D1-schema, venues inladen, handmatig events invoeren, agenda-pagina | Preview-URL met echte events van 10 venues |
| 2 | Scrapers voor de 10 belangrijkste venues en de nieuwsbrief-parser | Dagelijkse run vult kandidaten |
| 3 | Redactiescherm en curatie-regels uit de stijlgids | Pieter cureert een week in minder dan 15 minuten per dag |
| 4 | Livegang op eigen domein | Pieter zegt "zet live" |

## 7. Wat op Pieter wacht

- Appnaam kiezen (uit2).
- Nieuwsbriefadres aanmaken, bijvoorbeeld uit@waterproofmedia.com (uit3).
- Stack bevestigen (uit4).
- Akkoord op dit bouwplan.

## 8. Grenzen

Niets live zetten, versturen of geld uitgeven zonder akkoord van Pieter. Captcha's en bevestigingsmails bij het aanmelden voor nieuwsbrieven doet Pieter zelf.
