---
title: "Tearing on Rotate Cube/Wall?"
date: 2008-10-07
forum: General Help
---

### Post by jorwex on 2008-10-07
Hey all,

Since building a new PC I've had this problem when I rotate the compiz cube. Till now I was using 0.7.4, but I just upgraded to 0.7.6 and I still have the same issues.

The relevant hardware I guess is my motherboard: Abit IP35 Pro XE
& my video card: eVGA 9600GT SC

I installed my driver using envyng-gtk a month or two ago when I built the PC, and it failed the autodetection method, but said I can manually choose a driver and I chose the latest. I'm a bit fuzzy as to how envy negotiates updates and all, but it appears I'm using the latest driver available on nVidia's website which at the time of this post is 173.14.12. I don't believe that's what the version I first installed, so I guess it's been updating.

Here's some video evidence. In this vid I've hit the hotkey to start rotating, and I slowly drag from one virtual desktop to another:
[http://www.youtube.com/v/I3o947ybvj8](http://www.youtube.com/v/I3o947ybvj8)

and here's a vid of it switching using the buttons in the lower right of the gnome panel:
[http://www.youtube.com/v/1Di_X3r6jj8](http://www.youtube.com/v/1Di_X3r6jj8)

All the other effects I've tried seem to work okay (i.e. Expose zoom out plugin is smooth). I did notice that on my old PC (nvidia 6600 agp, athlon 2500+, asus a7n8x-e), I think there was an entry for in restricted drivers, but there isn't for my new pc. 

Any tips? Should I hold out and see if Intrepid fixes it?

---

### Post by el-mar01 on 2008-10-07
You could try the latest NVIDIA BETA drivers. They fix a few slow GTK issues and improve Compiz a bit.

Latest Nvidia driver here:

[http://www.nvnews.net/vbulletin/showthread.php?t=120052](http://www.nvnews.net/vbulletin/showthread.php?t=120052)

How to install a .run driver (you will have to do funky stuff like removing your xorg.conf file and killing your X server)

[http://www.nvnews.net/vbulletin/showthread.php?t=115916](http://www.nvnews.net/vbulletin/showthread.php?t=115916) (look at the code box)

Also I HIGHLY recommend you perform these performance tweaks after you installed the driver:

[http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

Another thing .. make sure you have "sync to v-blank" enabled on both the Compiz Config Settings Manager (in General > Display Settings) and the NVIDIA X Server settings (OpenGL part I think) ... further you should increase the refresh rate to 200 in the CCSM as well. (you could actually try this first before you install the BETA driver .. but the newer BETA driver fixes some annoying GTK performace issues so its probably good to install the latest BETA driver)

---

### Post by jorwex on 2008-10-09
Aha! The vblank fix did it. I wonder why I didn't have that problem before with my old computer...

---

### Post by jorwex on 2008-10-09
False alarm. Still doesn't work. I got excited cuz it switched desktops fluidly by pressing the bottom right corner button, but it still doesn't work when you drag windows across.

Also, for some reason teh latest Beta driver on their site was 177.78, but when i checked their official website, the non-beta was 177.80...weird..

I tried both.  Any other ideas?

---

