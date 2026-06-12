---
title: "NVIDIA Graphics Card Issues...I assume?"
date: 2008-06-22
forum: Hardware
---

### Post by lordtitanikus on 2008-06-22
Hi

I'm running Ubuntu on my laptop with a NVIDIA 256MB Geforce GO 7300.  It ran fantastically well until last week when updating.  When it re-started, it said it could not detect the monitor or graphics card.  Since then I've had headaches with the resolution, as now it looks real bad, with the desktop screen magnified even when the enhanced zoom is off.  Compviz is installed, and envyNG seems to work fine now.  But the resolution is really, really bad.

I'm a complete Ubuntu noob (so guide me as if I were a 2yr old), and can't think of using anything else.  Please help!

---

### Post by lordtitanikus on 2008-06-22
Ok, so I got the resolution working OK, after reinstalling Usplash, and my NVIDIA X-server settings have come alive (or I've just noticed them : \  like I said, complete noob).

My question is now can I get better resolution settings, or is what X-server offers is law?  Any help would be very, very appreciative.

---

### Post by hotweiss on 2008-06-22
1. sudo apt-get remove nvidia*
2. sudo envyng -g
3. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 169, and finally click Apply.
4. Once the installation is completed, reboot and you will once again have a crisp screen.

---

