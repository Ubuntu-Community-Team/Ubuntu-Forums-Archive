---
title: "Need help with Intel Video card + widescreen monitor"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by fuzzymonkey on 2007-03-13
I am trying to switch from Windows to Linux. After looking at several distributions I decided on Ubuntu. I tried installing both Edgy Eft and Fiesty Fawn but run into the same problem in both (and all other Linux distros for that matter), I can't figure out how to set up my integrated Intel 82865G graphics card to run at the 1440x900 resolution that my Samsung 941BW monitor likes. (It works fine in Windows XP). I have tried installing the 915 resolution hack and using it both automatically (through some other disto) and manually. Every time I get the same result: A very distorted image in the top right corner of my monitor that appears to be the top left bit of the desktop. I tried running the Xorg configuration thing and manually entering the refresh rates from my users manual but it had them right. If it helps, I will take a picture of my screen when this happens so you know what I mean. I am a fairly experienced Windows user but a Linux newbie. Help would be appreciated.
Question: Can my Intel card run 3D desktops (Compiz/Beryl)?
Question 2: I'm looking at a good deal on a ATI X1550 (~$90 after rebates, including shipping), would that solve my problems (I would be using DVI instead of VGA if I got it)?
Thanks in advance

---

### Post by TwoWordz on 2007-03-13
hello fuzzymonkey, 

To make your videocard work at 1440x900, you just have to edit xorg.conf.

```
sudo nano /etc/X11/xorg.conf
```

Find the section where all the resolutions are and the resolution you want.

Ex.:
```

SubSection "Display"
                Depth     24
                Modes    "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection

```

And yes, your card supports beryl using AIGLX.

You won't see any difference between DVI and VGA. This card is not a good deal anyway. 

TW

---

