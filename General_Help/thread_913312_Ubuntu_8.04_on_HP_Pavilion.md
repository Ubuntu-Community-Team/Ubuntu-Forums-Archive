---
title: "Ubuntu 8.04 on HP Pavilion"
date: 2008-09-07
forum: General Help
---

### Post by jasex on 2008-09-07
This is a new HP Pavilion... the ones with the silver touch panel...

it sends the installer from the usplash to the busy box screen, and I believe it is due to maybe SATA drives... any help?

---

### Post by quibbler on 2008-09-08
> **jasex said:**
> This is a new HP Pavilion... the ones with the silver touch panel...

it sends the installer from the usplash to the busy box screen, and I believe it is due to maybe SATA drives... any help?
Press F6 to run with other options.
Edit the first entry by getting rid of "quiet splash" and add
"all_generic_ide" (without the quotes) to the end of the line.
Then boot. Hope this helps.

Regards quibbler

---

