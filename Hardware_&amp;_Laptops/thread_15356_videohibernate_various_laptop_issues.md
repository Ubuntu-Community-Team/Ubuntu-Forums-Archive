---
title: "video/hibernate various laptop issues"
date: 2005-02-13
forum: Hardware &amp; Laptops
---

### Post by herbo on 2005-02-13
I put ubuntu (hoary developnment snapshot 20050204) on my compaq evo 1020v laptop and it mostly works well (although I must admit gentoo on my desktop pc is more fun to play with :) ), except for a couple of minor issues:

1) TV-Out - This laptop uses an ATI IGP 340 chipset for which I use the xorg radeon driver to make work (2D works fine and 3D works okay, but is very slow due a lack of TCL), however I cannot seem to get video out (through the s-video socket) working. Has anyone acheived working tv out with this graphics chipset?

2) Hibernation - According to this:  [http://www.ubuntulinux.org/wiki/HoaryPMResults](http://www.ubuntulinux.org/wiki/HoaryPMResults) suspend to disk should work but although my laptop suspends okay, when it tries to come back from hibernation the screen gets messed up and the laptop basically locks up. I am not using any binary graphics drivers, so has anyone any strategies or settings as to to allow hibernate to work? (suspend to ram also locks the laptop up when trying to resume)

3) Speedstep - This laptop uses a combo ATI/ALi northbridge/southbridge chipset and speedstep support appears to be lacking. I can use the P4_CLOCKMOD module, but this will only change the CPU frequency, not voltage or anything else. Some premilinary support was created for this chipset at [http://www.poupinou.org/cpufreq/speedstep-ali.html](http://www.poupinou.org/cpufreq/speedstep-ali.html). However this appears to be discontinued and I can't find any information about it. Does anyone know what happened to ALI speedstep support?

4) The gnome battery charge monitor icon never changes regardless of the power status. I.e even if the AC power is unpluggged, It will still think that the system is running on AC power despite it reporting that the battery status correctly (i.e 95% battery). This would seem to be a bug in the gnome battery charge monitor. Has anyone else noticed this?

---

### Post by kdavison007 on 2005-02-13
I have similar problems to what you're explaining.  I've pretty much given up on ACPI support for my HP Pavillion 5900.  It will sleep, but not wake.  The battery monitor works, but like you're saying it will get "stuck" at a setting.  It will stay at say 95% for 40minutes and then the next thing I know it jumps down to 30%.  I don't think it's a problem with the gnome meter.  I think it's just that ACPI support from x86 laptops just sucks.  If I do a cat /proc/acpi/battery/BAT1/state I get the same information.  

I heard we'll be getting better support in Hoary.  You can search around and probably find some hacks to get things working a little better, but it's not going to be easy.

---

### Post by herbo on 2005-02-14
Sadly it looks I will have to keep Windows XP on my laptop for a while longer...I specifically need: Quicken, Ms Money, S-Video and Hibernation to work and for the moment all works in progress...

Tis a shame, because having never used a debian system before I found Ubuntu really cool. Coming from a Gentoo background, which I have set up on my desktop pc where it works almost flawlessly (living on the edge has its disadvantages - see breakmygentoo for an example). I guess Ubuntu would work fine too, but I wanted something simple and quick to maintain on my laptop....

Ah well Ubuntu stays, but so does Windows  :-| . Ubuntu worked much better than I expected. I am especially pleased that the all my modem was was picked up and worked automatically (wireless card, video, sound, touchpad etc..).

---

