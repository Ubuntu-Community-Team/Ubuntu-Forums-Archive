---
title: "Sound card recognised by knoppix but not ubuntu"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by caspar_wrede on 2005-06-02
My sound works with knoppix 3.6  but not with ubuntu hoary. So I guess I need to "transfer" my settings. Which settings are they and how do I do it?

Thanks, Caspar.

---

### Post by az on 2005-06-02
There is a bug in esd (used  by gnome).  Esd does not release the sound card and other aplications do not make sound.  It varies from machine to machine, not affecting all sound cards.  

KDE uses arts, and does not have this problem.  Do you get any sound at all?  

[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)
(see item number three)

---

### Post by caspar_wrede on 2005-06-02
[QUOTE=azz]There is a bug in esd (used  by gnome).  Esd does not release the sound card and other aplications do not make sound.  It varies from machine to machine, not affecting all sound cards.  

KDE uses arts, and does not have this problem.  Do you get any sound at all?  

[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)
(see item number three)[/QUOTE]


I get no sound at all.

I have loaded and unloaded artsd, esd and polypaudio. speaker-test gives no result when no sound demon is loaded and alsa-mixer is not the problem either (i.e. all volumes are up).

 Apparently a sound device is installed: see output from lspci -v:

```

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Unknown device 1849:7012
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at dc00 [size=256]
        I/O ports at d800 [size=128]
        Capabilities: <available only to root>

``` 

But I know however that my device is ac97 compatible. What do I need to do?

---

