---
title: "A strange series of problems involving resolutions and my i810 chipset"
date: 2009-05-27
forum: Hardware
---

### Post by Thuren on 2009-05-27
Hi!
I installed Ubuntu JJ yesterday but just like many other people I couldn't set any resolution above 1024*768.
So I tried the solutions proposed on different forums etc:

1. Run 915resolution 
Didn't work, not compatible with my intel drivers or something like that (couldn't even install it)

2. Run "sudo dpkg-reconfigure -phigh xserver-xorg"
No effect.

3. Run  "sudo dpkg-reconfigure xserver-xorg"
Never got to select anything graphics related, just keyboard stuff. After all the keyboard choices it printed
"warning: overwriting possibly-customized configuration file"
and that was the end of that.
No change to xorg.conf.

Then there was a lot of "change this or that parameter in xorg.conf" suggestions, which was pretty hard since my xorg.conf looks like this: (except comments)
> 
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
Any suggestions? I've been able to run ubuntu without these problems before.

It's a 945GM card btw.

---

### Post by Thuren on 2009-05-28
Very weird. I was not able to increase my resolution via the GUI tool (System - preferences - screen), but using xrandr did the trick!

---

