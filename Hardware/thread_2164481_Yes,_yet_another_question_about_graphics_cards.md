---
title: "Yes, yet another question about graphics cards"
date: 2013-07-31
forum: Hardware
---

### Post by benedict-m-holland on 2013-07-31
So I am going to post this because I can't seem to find any up-to-date information. I realized that I could actually play a game on ubuntu by downloading games on Steam. Before I do this, I realize that I do need a graphics card. I currently have an i7 southbridge and though the GPU is decent at running stuff, it is not really designed for games. So I have been using linux for years and I know the debate between Nvidia and ATI and honestly, I just need a graphics card which has stable drivers. What is the better alternative? Also, what is a "good" graphics card? I think I am looking for something with between 512MB to 1GB or ram and the best frame rate possible. Please note that I am not looking for the BEST graphics card out there (since it won't be supported anyway). Since graphics cards seem to change every few minutes, I am curious what is good. Also, is there a list which is maintained? Basically, I am looking for the most stable and decent graphics card. What are the recommendations? 

Thanks in advance.

---

### Post by lah7 on 2013-07-31
In my experience, I have found Nvidia's Linux drivers to be a lot more stable and easier to get working compared to ATI's.

My system has Radeon HD Graphics onboard (sharing memory with the system) and could run a certain game at ~50-60fps but I found that if that same game was to be ran for hours, the entire system would lock up. This disappeared when I bought an Nvidia GeForce GTX 650 (1 GB), and that same game would run at ~100-150fps, but I usually have V-Sync turned on due to screen tearing. If it can run at a solid 60 fps, it should look good! I'm not a gamer myself, but for 3D performance, this Nvidia PCI card does the job well, mainly used for Compiz effects.

Although both the Linux drivers for ATI and Nvidia are improving constantly, so it depends on you on whether you want performance or price.

---

### Post by papibe on 2013-07-31
Hi benedict-m-holland.

I've have very good experiences with Nvidia cards. The new driver on the repositories works very well with Steam and HiB games.

This would be the general way to get the level you need:

In the Nvidia world the second digit indicates the entry level. For instance: 2**1**0, 5**1**0, and 6**1**0, are the lowest entry level. These cards are just OK for gaming. There would be very good for a HTPC since all of them reproduce HD video though.

High performance cards would be: 5**8**0, 6**6**0, 6**7**0 and 7**7**0.

A good compromise could be mid level like 5**4**0, 5**5**0, 6**5**0, etc

Hope it helps.
Regards.

---

### Post by Yellow Pasque on 2013-07-31
GTX650Ti is what I always recommend as best bang for buck. If you're running at higher resolutions or like higher effects, GTX660.

---

### Post by Merrattic on 2013-08-03
Thanks for all the advice, just what I needed. Not a gamer, not needing "full force" / frame rate ;) so picked up a reasonable bargain GTX 650 1GB off the bay for £65, brand new :) Will take the strain off my i5 4670k when it finally arrives....

---

### Post by Merrattic on 2013-08-24
But it gives me video tearing on Xubuntu, even with compositing turned off.  (I am running 12.04.2 64 bit on my new machine)

The only workaround I have found for this is as follows:

1. If using mplayer, use gl/vdpau as the video mode, not xv
2. Change the environment variable to overlay, by adding the following line to .bashrc
```
VDPAU_NVIDIA_NO_OVERLAY=1
```

I also get a strange ripple effect when scrolling with Firefox, minimised this by installing the "YestAnotherSmoothScrolling" extension and playing with the settings

---

### Post by Yellow Pasque on 2013-08-24
To get rid of tearing with xfce, I use compton compositing manager (with glx backend).

---

### Post by Merrattic on 2013-08-25
Thanks Temujin, compton installed and doing a good job :D

---

