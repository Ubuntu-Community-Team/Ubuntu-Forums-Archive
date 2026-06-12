---
title: "ATI driver slowness"
date: 2009-08-15
forum: Hardware
---

### Post by Miker75 on 2009-08-15
I've just installed Mythbuntu and installed the 9.7 ATI driver, however, it seems that the UI is still as slow as it was when I was not using the fglx driver?

The xorg.conf file has this listed (which I assume is correct?):

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        BusID       "PCI:1:0:0"
        Driver  "fglrx"
EndSection


But mouse movements on the desktop are still slow (2 updates per second I'd say..maybe 3)..

The card in question is a Radeon 4650, which should be more than fast enough....

Any ideas?

---

### Post by Yellow Pasque on 2009-08-15
See if adding this to the Device section of /etc/X11/xorg.conf helps:
```
Option "XAANoOffscreenPixmaps" "true"
```

---

### Post by Miker75 on 2009-08-15
Doesn't seem to change...

I just tried playing back a DVD in MythTV, and while the screen was completely corrupted, it *was* updating at a decent framerate... so maybe it's just the Ubuntu UI that's slow for some reason...

Also, when running the ATI Catalyst Control Centre, it does report all the specifications of the video card, so I'm assuming the driver is loaded and running?

Researching the problem a bit more leads me to be curious about the USB controller...as it seemed that a read from a USB stick was god awful slow as well (mouse is USB).
At the moment I'm stuck with an old ATI SB400 USB controller... any way of fixing this?

---

