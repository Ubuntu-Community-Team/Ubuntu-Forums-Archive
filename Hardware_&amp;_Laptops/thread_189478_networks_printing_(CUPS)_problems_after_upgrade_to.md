---
title: "networks printing (CUPS) problems after upgrade to Dapper"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by Poldi on 2006-06-05
hi all.

I have several PCs, all running Dapper, one of them as a CUPS-printserver.

some of the PCs discover the printer just fine and all are in the same subnet, so I know the server is configured correctly.

one PC seems to have a corrupted cups-configuration. let me explain: discovery yields no result, but I cannot create new printers manually or _delete_ the one local printer I have configured in the past either. all this is via gnome-cups-manager. I am trying as the primary (sudo-able) user still this looks a bit like a permission problem.

the main differency between this PCs and the others is that this one was dist-upgraded since Warty-preview, while the others are of Hoary or Breezy descendance.

where (which dir) are printers created?
what access rights must what user(s) have there?
how can I completely throw away my configuration regarding printers and start fresh and new? (removing cups* via Synaptic and reinstalling was not enough, it seems).

tanks and regards,
Carsten

---

