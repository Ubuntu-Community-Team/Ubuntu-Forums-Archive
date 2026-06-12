---
title: "HP LaserJet P1006, faint/light print [SOLVED]"
date: 2010-03-29
forum: Hardware
---

### Post by kevinfishburne on 2010-03-29
For anyone using an HP LaserJet P1006 printer under Ubuntu 9.10, choosing the HPIJS P1006 driver results in anything small being printed very faint. For example, small text and thin lines (Google Maps) appear faint. Larger text looks fine, but photos also print out far too light.

A workaround I recently discovered is to choose instead the HP LaserJet P1505 driver, which appears to print properly. I chose to use the new PPD rather than import settings from the old one, though it may make no difference.

---

### Post by balmar on 2010-07-30
Sooooo many thanks for this! :-)

---

### Post by kevinfishburne on 2010-07-30
> **balmar said:**
> Sooooo many thanks for this! :-)
You're welcome. I don't think previous versions of Ubuntu had this problem, so the P1006 driver must have changed somehow.

Did this work for you in 9.10 or 10.04? I haven't tested to see if it's still happening in Lucid.

---

### Post by balmar on 2010-07-30
It seems from file attributes that I got this printer and installed hplip (from HP's site) in May, 2008. As far as I can recall I have had this problem from the beginning, with all actual versions of Ubuntu, including Lucid recently, but maybe they haven't touched my hplip installation, I don't know. Lucid now seemed to install something automatically, but that had the same lightness problem. I tried to google after it once or twice but yours is the first solution I found. It was particularly annoying with prints from Google Maps.

---

