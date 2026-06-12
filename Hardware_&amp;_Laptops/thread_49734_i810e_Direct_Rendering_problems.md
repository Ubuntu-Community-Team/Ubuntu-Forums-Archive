---
title: "i810e Direct Rendering problems"
date: 2005-07-17
forum: Hardware &amp; Laptops
---

### Post by Awalton on 2005-07-17
Round 8 ended today with complete and total failure. I've really got to get this working, else I go back to Windows (I'm developing an OpenGL game, and not having accelleration is no longer an option).

So. I'm completely lost on what to do. I've tried everything everyone's suggested, and grepped my heart out through the forums, but couldn't find anything usable.

Here's the error I'm getting now (after hours of probing through configs):

(EE) I810(0): [dri] Not enough memory for dma buffers.  Disabling DRI

What's that mean exactly? It should have plenty of memory.. The machine has 512MB of ram, the video card is an intel integrated chipset, but under Windows it can play games like Quake 3 which means OpenGL works fine for the card, even if it's not as fast as newer computers (it's my corp's desktop).

Any ideas?

---

### Post by jasmuz on 2005-07-17
On Windows, the video accelaration is done by DirectX (software), not via hardware.
These intel chipsets lack proper accelaration as other cards do.

---

### Post by MetalMusicAddict on 2005-07-17
[QUOTE=Awalton]Round 8 ended today with complete and total failure. I've really got to get this working, else I go back to Windows (I'm developing an OpenGL game, and not having accelleration is no longer an option).

So. I'm completely lost on what to do. I've tried everything everyone's suggested, and grepped my heart out through the forums, but couldn't find anything usable.

Here's the error I'm getting now (after hours of probing through configs):

(EE) I810(0): [dri] Not enough memory for dma buffers.  Disabling DRI

What's that mean exactly? It should have plenty of memory.. The machine has 512MB of ram, the video card is an intel integrated chipset, but under Windows it can play games like Quake 3 which means OpenGL works fine for the card, even if it's not as fast as newer computers (it's my corp's desktop).

Any ideas?[/QUOTE]
The "i810" drivers have seemed to be a problem for alot of people. I cant get accelleration working on my laptop in Horay. Now I have played with Breezy and it seems to be fixed there but its not final.

---

### Post by varunus on 2005-07-17
That error is caused by a buggy BIOS that incorrectly reports the amount of video ram available to the card.  You need at least 8 MB for DRI, and some BIOSes can report as low as 2 MB.  To fix this, try the following:

open up your xorg.conf file with 
```
sudo gedit /etc/X11/xorg.conf
``` 

Scroll down to the Device section and find the line that looks like this:
```

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection
```

Make it look like this:
```

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        VideoRam        65536  #However much you want to use for VRAM, will steal from system RAM
        BusID           "PCI:0:2:0"
EndSection
```

Hopefully that will work for you. If not, there are a few other tricks to get DRI working.  It worked for me out of the box...good luck.

Also, do you have the agpgart kernel module loaded?  You can check with "lsmod" in a console.

---

