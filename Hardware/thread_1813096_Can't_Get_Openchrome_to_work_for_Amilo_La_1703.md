---
title: "Can't Get Openchrome to work for Amilo La 1703"
date: 2011-07-27
forum: Hardware
---

### Post by CosSin on 2011-07-27
I have tried every tutorial that shows how to install Openchrome but still after booting in normal mode, the display goes to a black screen.  Can't do anything but shutdown either keeping the power button pressed for 3 secondes or taking out the battery and power source. Looking in Xorg.0.log it tells that "last line is incomplete".
I would like some help as how to go about resolving this issue. 
Ubuntu version 11.04, 2.6.38-10
Openchrome installed via Ubuntu Software Center

---

### Post by CosSin on 2011-07-27
More info: if i select openchrome as the driver the system gets to the screen where for a second it shows Ubuntu version 11.04, then it goes to a black screen and freezes. I configured the xorg.conf over and over. Got the scripts from this forum to install openchrome to config the xorg.conf file acordingly for my video card etc. The system still hangs. I changed the vram size from bios from 64 to 128 back to 64. No change.

---

### Post by jadabra on 2011-08-14
I am having a (different) openchrome problem with the same machine and am writing a post about it right now.
Just 2 quick questions:
Where exactly can you "select" openchrome as driver?
What exactly did you install from the repositories (and which r's)? I am asking because I searched for the drivers in Synaptic and they seemed to be already installed.

Thanks

---

### Post by CosSin on 2011-08-15
You can set up "openchrome" as a driver in your /etc/X11/xorg.conf, 

Section "Device"
  Identifier  "Card0"
**  Driver "openchrome"**
  BoardName "unknown"
EndSection

---

