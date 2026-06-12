---
title: "Replacing Nvidia card with Radeon, what potential problems can I expect?"
date: 2011-02-16
forum: Hardware
---

### Post by Gabtel on 2011-02-16
Hi, I'm using Ubuntu 10.10 on a 4 core 64 bit AMD CPU with Nvidia card. I would like to replace that card with Radeon one, however I'm not certain whether I should proceed and what problems can I expect. To be more specific, I currently have Nvidia proprietary drivers installed, what would happen if I shut down the computer, replace the card with the new one and boot Ubuntu? I presume that Xorg won't start? How do I install new drivers without Xorg, or maybe I should uninstall Nvidia drivers before installing the new card? Also what other problems can I expect, I have heard that Radeon drivers on Linux are not as stable as Nvidia's, is that true? Should I expect any other problems?

---

### Post by An Sanct on 2011-02-16
If possible, uninstall proprietary drivers and make sure, that VESA mode works ok, before switching the graphic card. This way, you can be certain, that the next time you start with the new card installed, you will have video. After that, install the appropriate proprietary drivers for the new card.

You shouldn't have any other problems. I switched the whole mobo today and found out, that i could still boot normally into X (I did a full reinstall after that, because I had other non HW related problems).

---

### Post by Gabtel on 2011-02-16
Thanks, **An Sanct**! I'm gonna uninstall proprietary drivers and proceed.

---

