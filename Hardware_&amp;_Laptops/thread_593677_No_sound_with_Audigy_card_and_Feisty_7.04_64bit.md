---
title: "No sound with Audigy card and Feisty 7.04 64bit"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by Starrfoxx on 2007-10-27
I recently bought a used Audigy SB1394 EAX HD Sound card, Model SB0090.  It works great with Windows XP, naturally.  With my Ubuntu 64bit 7.04, it is "seen" but there is no sound.  I have read the following thread:

[http://ubuntuforums.org/showthread.php?t=47488]("http://ubuntuforums.org/showthread.php?t=47488")

I have tried the steps there, but no luck.  Does anyone else have any ideas?  I'm not sure about upgrading to Gutsy just yet, because I have some things configured just the way I like them in Feisty.

---

### Post by Voltairine on 2007-11-02
I'm a brand new user to linux (as of today!) and was having the same problem with the same sound card but unbuntu 7.10.  After trying various fixes on the forum I found that unchecking "audigy analog/digital output jack" worked.  I found the menu for this option by right clicking the audio icon in the upper right menu bar, selecting volume control, and clicking the "switches" tab.

Maybe this solution would work for you as well?  Good luck!

---

### Post by jasonwstone on 2007-11-23
Great Thanks,
Jason

---

### Post by TNakos on 2007-11-23
If that doesn't work a problem i had with alsa was becuase i had 2 audio cards enebaled in the bios causing alsa to call the one i wanted "card 1" and the other "card 0" card 0 is what is default.

---

