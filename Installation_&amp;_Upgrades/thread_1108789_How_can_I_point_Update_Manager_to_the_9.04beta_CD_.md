---
title: "How can I point Update Manager to the 9.04beta CD instead of Online Download?"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by TBerk on 2009-03-28
I can either:

A) Install 9.04 beta via CD, it wants to install parallel to the existing 8.10. (Including resizing partitions, etc.)

B) Run ```
$sudo update-manager -d
``` and get an opportunity to install 9.04 via an internet download.

But, since I already spent time downloading a large 9.04beta iso (and subsequently burned it to CD), can't I just point to it's source files and have an upgrade pull from a local source?


TBerk

---

### Post by zvacet on 2009-03-28
I don´t think it is possible to do upgrade from live CD.If I´m wrong let somebody correct me.

---

### Post by cariboo on 2009-03-28
You have to burn the iso to a cd, then just insert the cd and it will give you the opertunity to upgrade.

I did a clean install last night, there was still  over 160 packages that needed to be upgraded, as there was a problem with one of the python files on the beta CD

Jim

---

### Post by TBerk on 2009-03-28
As it turns out I did not get an opportunity to upgrade (from the Live! CD I had burned). Install option wanted to Install 9.04 side by side w/ 8.10 (.14).

I ended up copying my data over tot he WinXP partition (it was only a few Gigs.) Deleting the old linux partitions (which needed some clean up any way in my case,) and installing from the CD.

Currently I ma dual booting XP & Ubuntu 9.04beta. 28Mar09.

And yes, after the initial install a great deal of core files were 'patched' immediately (via Synaptec..).


TBerk

---

