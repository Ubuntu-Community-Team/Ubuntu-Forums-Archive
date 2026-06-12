---
title: "Dual Screen Setup with xrandr -- Presentation starts on Laptop"
date: 2008-05-25
forum: Hardware
---

### Post by buschi on 2008-05-25
Hello everybody!

I am running Hardy and want to show a presentation on a projector (VGA) while seeing some notes etc on my laptop screen (LVGS). Therefore, I cannot clone. I succeeded in getting a signal to the external monitor -- however, as soon as I start an OpenOffice presentation or "xpdf -fullscreen", the "fullscreen" is my laptop and the external monitor stays as it was.

Of course, I could consider showing the presentation on my laptop while having the notes on the projector ;), but I would highly appreciate if someone knew a fix.


I edited my xorg.conf to contain:
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"

# added this subsection for vga output of 1024x768 above the screen (1280x800)
        SubSection      "Display"
        Virtual         1280 1600
        EndSubSection
EndSection

```

and switch the external monitor on with

```

xrandr --output LVDS --auto --pos 0x800 --output VGA --auto --mode 1024x768 --pos 0x0

```

I tried to put the external monitor above and below the laptop monitor, that doesn't seem to matter.

Thanks for any answer,
Sebastian.

---

### Post by stevebarnes on 2008-05-25
Hey Sebastian, I can only reinfoirce the question! I'm now on Mint, a Ubuntu derivative, and it offers exactly the screen managemwnt Ubuntu does. I also checked out Fedora, PC Linux and a couple of others just to see if I could get a projector going with my Toshiba Satellite notebook. It's all to no avail!

This seems to be a real problem area in linux. If people are to take Linux as a desktop seriously, someone has to address this. I teach courses, and use XP Pro as a standard, but it crashed when I was interstate, and I installed Ubuntu as an attempted rescue. Several weeks later, it's nice to have MINT on my personal laptop, but I'm having to use another notebook to run presentations on now!

Problems I've had:
1. not recignising the projector
2. Completely losing any screen image when the notebook gets past the OS selection OR after log off to reset the X-config.

I did (on PC-Linux?) get a duplicate screen going once, but after re-boot is was a mess anyway!

I'll be very interested on any progress in this space.

All the best,

---

### Post by sindrejh on 2009-11-02
Same problem here, but still no solution. Ubuntu 9.10

Edit: Found a temporary solution... I had already tried different settings both in OOo's and Ubuntu's display settings (tried both mirroring and big desktop) with no luck. But the solution was to place the two screens above in stead of aside each other. Looks like a bug, so maybe I will have to report it. But is it in Ubuntu or OOo? I think probably Ubuntu.

---

