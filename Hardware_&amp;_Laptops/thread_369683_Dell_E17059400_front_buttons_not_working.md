---
title: "Dell E1705/9400 front buttons not working"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by SnowPunk98 on 2007-02-24
By following the guide in the following link I was able to get the builtin subwoofer working: [http://ubuntuforums.org/showthread.php?t=335285](http://ubuntuforums.org/showthread.php?t=335285)

However after doing this the front buttons on my laptop do not work correctly (they did before the fix). It seems now that the PCM controls the volume etc but I can't seem to get it all to work right. Does anyone know a fix to this problem or is anyone else having this same problem?

---

### Post by SnowPunk98 on 2007-02-25
Anyone having the same problems or know how to fix it?

---

### Post by SnowPunk98 on 2007-02-27
bump

---

### Post by fmaste on 2007-07-01
Under Feisty my subwoofer is working out of the box, I believe you are using Feisty.
Open your volume control (the one near the clock by default), go to File->Change Device and make sure you have selected the one that says "Alsa Mixer". Now in Edit->Preferences check the one that says LFE and a new slider will appear to let you control your subwoofer.
The little problem is that the master volume is not working as the master one. what you can do is make then work in parallel, both Master and LFE go up and down at the same time. To do this right click on the volume icon (by default near the clock) and select Prefefences, select the one that says Alsa mixer and them select Master and by holding CTRL on you keyboard select also LFE. Now if you also want this behavior with your volume keys do the same the lower part of the device section in System->Preferences->Sound.

You can also select PCM instead of Master and LFE, play a little with the different combinations and select the one you prefer, I prefer Master and LFE.

---

