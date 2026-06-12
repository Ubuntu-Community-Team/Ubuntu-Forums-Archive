---
title: "Dual screens questions"
date: 2009-09-05
forum: Hardware
---

### Post by rapt0rjezuz on 2009-09-05
On WindonsXP I was running one screen through my VGA onboard Gefore 6100 and another through my Geforce 7950GT OC. How would I do this on Ubuntu?

Any help is appreciated!:popcorn:

EDIT: I have a display hooked up to my Geforce 6100 (using my 7950 as main) but it doesnt see the display, I'm pretty sure I just need to install the proper driver for the 6100 right? How would I do this?

heres my xorg.conf, is there anyway i can edit this to use my onboard VGA too?

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

---

### Post by Fafler on 2009-09-05
Both card are supported by the binary nvidia driver. Go System -> Administration -> NVIDIA X Server Settings. Use the utility to detect and configure the second monitor and save the configuration.

---

### Post by rapt0rjezuz on 2009-09-05
it does not detect it

---

### Post by rapt0rjezuz on 2009-09-05
bumping for justice, so i know I need to add another Device into my xorg.conf after a quick chat on IRC, but I still dont know HOW to do this. I really need help with this!

I need to know how to add another Device and set Screen to use both devices I THINK, or do I need to add another Screen section for the new Device?

---

### Post by utnubuuser on 2009-09-05
Hello  -- Not sure if this applies in this case, but I was reading a thread last week about using a card in conjuction with an onboard video chip, and they were saying that it wasn't possible to.
The gist of the thread was that as soon as a pci(e) video is plugged into a slot, the onboard video is bypassed.
I'd like to be able to use my onboard video as well as a card so I could have 2 monitors.
If this is possible, I'd sure like to know how.

---

