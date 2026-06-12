---
title: "X.org freezing a LOT with fglrx drivers, Radeon Mobility 9000"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by Seth on 2005-04-28
This has been happening for a long time, but it's only recently gotten annoying enough to ask for help (shipped my desktop home and have been running only the laptop and Ubuntu).

About once a day Ubuntu just hard-locks. Mouse isn't responsive, pressing the power button doesn't shut things off, nothing. Leaving it alone doesn't help. The fan goes wild. I've been unable to SSH into the box, but another user with my symptoms says X.org is eating 99.9% of processor time. I'm almost sure it's X.org's fault.

I just installed America's Army on the laptop today. I can run it for about 5-10 minutes and it locks every time without fail. Sometimes in the past, however, it's locked when I wasn't running a 3D game at the time.

This laptop is a Dell Inspiron 600m, and the worst decision I ever made for it was getting the ATI card. But now I'm stuck with it ;) I've read all the fglrx threads but can't find any Hoary people having problems with freezing. Help?

---

### Post by odix on 2005-04-29
Maybe you will find your answers [here](http://www.rage3d.com/board/forumdisplay.php?f=88) .
I've a Dell Inspiron 8200 also with a M9, I've used several drivers (ATI, XIG, OpenSource). I always returned to open source (xfree,xorg) drivers, they give me the best stability for working, for playing ?

My driver investigations:

xig: vmware (proplem with full screen), ut2004 (perfect, fast), doom3 (not supported), 2D perfomance (fast)
ati: vmware (proplem with full screen), ut2004(slow), doom3 (slow), 2D perfomance (slow)
xorg: vmware (no problem), ut2004(unplayable), doom3 (didn't start), 2D perfomance (fast)

So you can see, if you own a ATI card, it depends on what you wanna do to select the correct driver :-(

odiX

---

### Post by Seth on 2005-04-29
[QUOTE=odix]Maybe you will find your answers [here](http://www.rage3d.com/board/forumdisplay.php?f=88) .
I've a Dell Inspiron 8200 also with a M9, I've used several drivers (ATI, XIG, OpenSource). I always returned to open source (xfree,xorg) drivers, they give me the best stability for working, for playing ?

My driver investigations:

xig: vmware (proplem with full screen), ut2004 (perfect, fast), doom3 (not supported), 2D perfomance (fast)
ati: vmware (proplem with full screen), ut2004(slow), doom3 (slow), 2D perfomance (slow)
xorg: vmware (no problem), ut2004(unplayable), doom3 (didn't start), 2D perfomance (fast)

So you can see, if you own a ATI card, it depends on what you wanna do to select the correct driver :-(

odiX[/QUOTE]
 After about three hours of sifting through that stuff, this seems to have solved ALL freezes. I played America's Army for an hour with zero freezing; before I couldn't play more than 5 minutes.

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
        Option          "UseInternalAGPGART"    "no"
        Option          "KernelModuleParm"      "agplock=0;agp_try_unsupported=1"
        Option          "AGPMask"               "0x00000010"
        Option          "AGPv3Mask"             "0x00000010"
EndSection
```

---

