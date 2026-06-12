---
title: "Cannot set optimal resolution with ATI drivers"
date: 2009-04-24
forum: Hardware
---

### Post by baskinsy on 2009-04-24
I have just installed Ubuntu 9.04 64bit on my PC with an ATI HD4670 and a 22" monitor. I have installed the ATI drivers with the restricted drivers manager.

I cannot set my monitors resolution to the optimal 1680x1050. It stays at 1600x1200 and it is a little blurry.

I have searched the forum and tried almost everything.

My xorg.conf (with some adjustments after initial install) is:

```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1680x1050"
        HorizSync   30-66
        VertRefresh 50-61
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        Modes    "1680x1050"
        EndSubSection
EndSection
```

The optimal resolution is not listed on ATI control center or GNOME display properties.

Any suggestions?

---

### Post by jamessnell on 2009-04-24
Have you tried downloading and installing the latest ATI drivers straight from their website? I'm using 9.4 from over there on Jackolope and all looks good on my Radeon HD 2600..

---

### Post by baskinsy on 2009-04-24
> **jamessnell said:**
> Have you tried downloading and installing the latest ATI drivers straight from their website? I'm using 9.4 from over there on Jackolope and all looks good on my Radeon HD 2600..

I prefer to stay within the PMS for evaluation purposes.

---

### Post by jamessnell on 2009-04-24
Then I'd recommend you give 9.04 a little bit more maturation time - I mean, it was released yesterday :P

---

### Post by baskinsy on 2009-04-24
> **jamessnell said:**
> Then I'd recommend you give 9.04 a little bit more maturation time - I mean, it was released yesterday :P

You got a point.... but if someone has a suggestion that fixes the problem sooner, it will be good.:)

---

### Post by jamessnell on 2009-04-24
> **baskinsy said:**
> You got a point.... but if someone has a suggestion that fixes the problem sooner, it will be good.:)

Ahh, you have a point too. The way things get fixed is people report issues and others work on them..

:)

---

