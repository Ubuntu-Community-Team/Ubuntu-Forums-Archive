---
title: "All kinds of ___buntu problems with new system!"
date: 2011-05-13
forum: Hardware
---

### Post by AoSteve on 2011-05-13
Alright, first.. Let's get hardware down.

ASRock Extreme6 P67 motherboard, P67 based
16GB Corsair blah blah 1600mhz DDR3 or whatnot
Asus nVidia GTX 550 Ti  (1GB)
Onboard sound

First, the only variant I've actually got to install correctly has been Kubuntu 11.04.   However, the graphics drivers are; well somewhat buggy.  

Problem 1:   Tried fresh install of 11.04.   If I have Windows Installed (I know..  I have to have it though; don't hold it against me) I can't get the new grub to install.   I'm guessing this is a pretty big problem already; so whatever with that.  I can get around it by installing Ubuntu first then messing with grub later.  

However;  The graphics driver with Ubuntu 11.04 and xUbuntu are both acting strange as can be.   I get an odd resolution; believe it's 1024x768 but my monitor won't show and the nVidia utiliy won't show anything.  

Using the additional drivers tool; there's NO drivers on this system that apply to it?  I'm pretty sure my nVidia based card should be on that list.   Whatever; I'll install the nVidia current driver through synaptic right?   Yeah; doesn't get me very far.  The nvidia driver won't activate; whether I manually include it in the xorg.conf file or not.

So, let's try the 173 driver..  SAME problem..  Maybe GTX 550 Ti isn't supported yet?

Problem 2 & 3 :    Using older CD's and trying to update to 11.04 and possibly getting the driver to install correctly results in the SAME problem.  However, it bypasses the grub problem and lets me install next to Windows the same way Kubuntu does.  10.10 and 10.4 do the same thing.   I don't think 9.xx is gonna do me any justice at all in this time.   

Problem 4 :  Sound..  While I don't have any drivers for my video and desktop effects can't be activated aside from Kubuntu (but I think you can without the nVidia drivers properly installed and active??) I've got nowhere.   I tried downloading mangle (Linux based Ventrillo Client).   With my old machine I never had a single problem with it.  Now; the recipients of my voice chat only hear static.   However, if I play music through the line-in port they can hear the music fine?

I'm all kinds of confused.

So here's my question(s)..

Is there anyway to install 11.04 along side of an existing Windows 7 install?

Anyone else have a problem and/or a fix for the GTX 550 Ti line of nVidia cards?

The onboard sound is RL892 or something similar and supposedly is fully supported by (most) distributions of Linux.   Is there a problem with the Kubuntu/Ubuntu driver or is it more likely software related?

Thanks ahead of time guys!

Been a Ubuntu user since 7.10 and don't want to go without my GNOME!  (I miss my panels :( )

---

### Post by AoSteve on 2011-05-15
Just a bump;  hope someone can help.   However there is an update...

I fooled with it today, and no matter what I do, it won't activate the nVidia drivers :\   Kinda bummed about that;  No OpenGL gaming for me? LOL

---

### Post by cchhrriiss121212 on 2011-05-15
Try installing the latest driver manually:
[http://www.nvidia.com/object/linux-display-amd64-270.41.06-driver.html](http://www.nvidia.com/object/linux-display-amd64-270.41.06-driver.html)

---

