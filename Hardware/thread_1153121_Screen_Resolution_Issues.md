---
title: "Screen Resolution Issues"
date: 2009-05-08
forum: Hardware
---

### Post by Bruno De Barros on 2009-05-08
Hi! I had a CRT on my Ubuntu, I use the NVIDIA accelerated drivers (version 180), so that I'd be able to make use of the 3D capabilities of my graphics card, apparently. It worked perfectly. The problem is, I changed to a new LCD screen (Novita 22" 2202WHD), yet the NVIDIA driver display tool (when I try to open the normal Ubuntu display, it tells me that I should use it, so I do) says I still am using my CRT (it says JEN JT229x6-3 (CRT-0 on GPU-0). :( So I tried clicking Detect Displays. Nothing. I reinstalled the driver. Nothing. I uninstalled it. It screwed my monitor up, because it started saying Out Of Range, I think the Vertical Refresh Rate was out of range... So I plugged the old monitor back in, and back to installing the driver. Now I can use my LCD again. But I can only get to 1280x960, when the maximum resolution of this screen is 1680x1050. Does anybody have any suggestions on what I should do? :confused:

Thank you very much in advance. :)

---

### Post by kay-man on 2009-05-08
You might try manually adding the 1680x1050 resolution to your /etc/X11/xorg.conf and then try to select it.

---

### Post by Bruno De Barros on 2009-05-08
I tried that already, Googled a lot, but I can't find the Modes line which I can edit. My Screen section of the xorg.conf file is as follows:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Virtual     1280 960
        Depth       24
    EndSubSection
EndSection
```

:(

---

### Post by fourthofjuly on 2009-05-08
> **Bruno De Barros said:**
> Hi! I had a CRT on my Ubuntu, I use the NVIDIA accelerated drivers (version 180), so that I'd be able to make use of the 3D capabilities of my graphics card, apparently. It worked perfectly. The problem is, I changed to a new LCD screen (Novita 22" 2202WHD), yet the NVIDIA driver display tool (when I try to open the normal Ubuntu display, it tells me that I should use it, so I do) says I still am using my CRT (it says JEN JT229x6-3 (CRT-0 on GPU-0). :( So I tried clicking Detect Displays. Nothing. I reinstalled the driver. Nothing. I uninstalled it. It screwed my monitor up, because it started saying Out Of Range, I think the Vertical Refresh Rate was out of range... So I plugged the old monitor back in, and back to installing the driver. Now I can use my LCD again. But I can only get to 1280x960, when the maximum resolution of this screen is 1680x1050. Does anybody have any suggestions on what I should do? :confused:

Thank you very much in advance. :)
install envyng - is hassle free - got 1440 x 900 resolution working with my nvidia 7200 card & 17" widescreen lcd 

[http://albertomilone.com/envyngfaq.html#A]("http://albertomilone.com/envyngfaq.html#A")

hope that helps...

---

### Post by DJYoshaBYD on 2009-05-08
i use the same driver for my 8600gt, and it works perfectly with my LCD.. as a matter of fact, I was able to use the LCD without the Nvidia driver even installed... 

are you using the gnome display manager? try doing this..

go to a terminal
```
sudo nvidia-settings
```

enter your password, and change all your settings here.. then click "save to xorg.conf" or something like that.. this works every time for me.. I dont really use gnome display manager unless im using a PC with no 3d card, and just need the basic display

---

### Post by Bruno De Barros on 2009-05-08
The solution to my issues is PATHETIC. I don't know HOW it happened, but I'm darn glad it did. A few hours after cursing the whole world over the fact that I bought a new screen and couldn't make the most out of it, I decided to boot onto my Windows XP, to see if it worked. It detected the new screen, installed it, and I set the resolution to the maximum allowed by the screen (1680x1050). I then hit my head on the desk, and realized, sadly, that I'd probably be much better off without the hassle of trying to be using Linux. Everything seemed to work on Windows. Then I sighed, and booted my Linux again. I had some work to do. That's when I realize that my monitor's resolution had gone back to 1024x768. I hit my head on the desk again (not LITERALLY. :P) and went to change the resolution settings. As I click the dropdown, suddenly all the resolutions are there, and I can change them! :-D I set it to 1680x1050, and I am now happy as a clam.

My question... SINCE WHEN DOES WINDOWS INFLUENCE LINUX?! :confused::confused::confused:

---

### Post by DJYoshaBYD on 2009-05-08
it doesnt have anything to do with it.. maybe you didnt reboot after installing the drivers? it wont load the driver until reboot, unless you manually do it... 

Linux is helllllaaaa easy to learn.. its just different... just roll with it.... lol

---

### Post by Bruno De Barros on 2009-05-08
Yeah I was thinking maybe I did some weird trick and never rebooted after it. xD Oh well. Another one of those things that will bug me for life, because if I ever format my Linux, I won't know what I did to fix it. xD Yeah, I love Linux, I'm just trying to get used to it. :)

---

### Post by DJYoshaBYD on 2009-05-08
yeah.. i bet when you do have to reinstall, if will go smoother.. the VERY first thing you should do is install your video drivers after an install.. it makes things alot easier.. you should REALLY update BEFORE installing the drivers, but it wont hurt them if you dont...

---

### Post by Bruno De Barros on 2009-05-08
Yeah I've installed Ubuntu several times already, but I always gave up on it because Windows had something that I really needed, or it was just faster (on my old computer, Ubuntu 8.10 was a bit less responsive than Windows XP), but now I've got a much better PC, plus I've learnt how to live without most of my Windows Apps, and use Linux Apps instead, so now I'm okay :D

---

### Post by DJYoshaBYD on 2009-05-08
almost every windows app has an open source alternative, except music software.. lol... you dont have to live without them.. you just replace them with better, more community driven apps...

GNOME (ubuntu) tends to use up more power than XFCE (Xubuntu).. I use xubuntu on my laptop, and its WAY faster than my windows partition and GNOME...

---

