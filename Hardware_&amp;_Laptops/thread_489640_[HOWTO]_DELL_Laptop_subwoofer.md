---
title: "[HOWTO] DELL Laptop subwoofer"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by fmaste on 2007-07-01
This may help. It works for me with a DELL Inspiron 9400.
Under Feisty my subwoofer is working out of the box, I believe you are using Feisty.
Open your volume control (the one near the clock by default), go to File->Change Device and make sure you have selected the one that says "Alsa Mixer". Now in Edit->Preferences check the one that says LFE and a new slider will appear to let you control your subwoofer.
The little problem is that the master volume is not working as the master one. what you can do is make then work in parallel, both Master and LFE go up and down at the same time. To do this right click on the volume icon (by default near the clock) and select Prefefences, select the one that says Alsa mixer and them select Master and by holding CTRL on you keyboard select also LFE. Now if you also want this behavior with your volume keys do the same the lower part of the device section in System->Preferences->Sound.

You can also select PCM instead of Master and LFE, play a little with the different combinations and select the one you prefer, I prefer Master and LFE.

---

### Post by Yhippa on 2008-02-13
This fixed the subwoofer problem on my Dell XPS M170.  Thanks for the help!

---

