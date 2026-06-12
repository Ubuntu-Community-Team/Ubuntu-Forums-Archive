---
title: "Hauppauge WinTV PVR - No Sound .."
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by Cordan on 2005-07-12
Hi guys,

i have a Hauppauge WinTV PVR running under Ubuntu. All works perfect with tvtime, but i dont get any sound out of the TV Card =(

Im using a cable between the lineout of the TV-Card to the Line-In of the soundcard but it dont works (on the windows xp system the cable/sound and the tv card work).

Any Tips where to look for Hints?

Thank you very much in advance =)

---

### Post by DrKayBee on 2005-07-12
What card is this? Can you tell me the model number and the driver it is running off of? (ie. cx88 or ivtv?)

---

### Post by Cordan on 2005-07-13
I will post that data as soon as I get home ;)

---

### Post by tristan on 2005-07-13
Have you tried...

tvtime -x /dev/mixer:cd

This will start tvtime and will allow you to control the volume on the CD input, using the left and right arrows.

---

