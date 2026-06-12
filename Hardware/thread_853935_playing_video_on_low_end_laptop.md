---
title: "playing video on low end laptop"
date: 2008-07-09
forum: Hardware
---

### Post by theRightNee on 2008-07-09
recently installed ubuntu on a 500 mhz/256 RAM laptop, using a standalone openbox window manager to reduce the load...my main purpose for this laptop is playing videos, but i cannot get that to work, my question is: is this even possible? can i play video on this machine?

---

### Post by kostkon on 2008-07-09
Maybe you can. But, what is your problem currently? Do the videos play slow?

---

### Post by Qinjuehang on 2008-07-09
What is your problem and what graphics are you using? (Intel 915?)

---

### Post by theRightNee on 2008-07-09
my apologies, the graphics card is an onboard trident cyberblade i7, and the videos play just very very slowly...i believe if i cut the framerate to 15 fps it could play smoothly, but i do not want to go through the process of converting vdieos

---

### Post by theRightNee on 2008-07-10
bump?

---

### Post by kostkon on 2008-07-10
I would recommend you to try to use *Mplayer* and play with the various video output drivers it offers.

*Mplayer* is a highly customisable player and you will be able to find a configuration where the videos play fine (even at the expense of some image quality, but what can you do).

I would recommend you to give [its documentation]("http://www.mplayerhq.hu/DOCS/") a good read. Lastly, check what it says about *Trident* cards [here]("http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#trident") and [here]("http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#vidix-trident").

---

### Post by eriqjaffe on 2008-07-10
> **kostkon said:**
> I would recommend you to try to use *Mplayer* and play with the various video output drivers it offers.

*Mplayer* is a highly customisable player and you will be able to find a configuration where the videos play fine (even at the expense of some image quality, but what can you do).

I would recommend you to give [its documentation]("http://www.mplayerhq.hu/DOCS/") a good read. Lastly, check what it says about *Trident* cards [here]("http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#trident") and [here]("http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#vidix-trident").If the box is going to be dedicated to video playback, you might also want to look into using something like Geexbox.  I've run video smoothly on a 550mhz desktop with it, you may have good luck with it.  At the least, it's a Live CD that loads the OS into RAM, so you can try it out without touching your current install - if it works well, you can install it to the hard drive.

---

