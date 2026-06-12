---
title: "2 Video cards, 3 monitors"
date: 2011-03-11
forum: Hardware
---

### Post by charileb000 on 2011-03-11
im having a few problems with linux - it appears most of the people who develop it dont have unusual configurations to test their code!

i have tried SUSE, spending alot of time trying to get it to work but ditched it because of a bug (which i doubt they will fix), so i am trying ubuntu

the hardware i am having troubles with is:

*motherboard's sata controller, GA-8i945G Pro, on the ich7r (82801GB/GR/GH *in win)
*ATI X700 (in a PCIE 1x slot) (bootup card) CRT monitor, runs best at 1280x1024 47HZ interlaced - left
*NV GF7800GTX (in a 16x slot) two monitors, LCD (1280x1024 native) - center, CRT 1280x1024 67HZ non-interlaced - right


the controller has two simular HDDs and this is being seen as a stripe with the name &quot;linux device-mapper (striped)&quot; on /dev/mapper/isw_dhfiebjffi_2x200GB , but the actual setup is individual seagate drives - it was a stripe but one developed bad sectors which i cant map as bad for some reason (easy in win9x) so computer crashes instead when accessing there.
Ubuntu sees my 2x200GB as having the first &quot;half&quot; partitioned, the other half as having no partitions/free. SUSE had &quot;minor&quot; problems with this,(not being able to read the NTFS partitions in 11.3, but can read them in 11.2) and is able to see them, could install on it if i wanted to but i wouldnt trust it!.

Windows has no troubles with my video card setup (and the refreshrates - inf files), i have had multiple graphics cards since win98, and little troubles except that S3 cards as secondary controllers was ditched in w2000. linux on the other hand is apparently not designed for any configuration other than one card only and defined refreshrates, but could be because of multiple desktops.


UB installed ok on a seperate IDE drive, only using the ATI card. i then followed the instructions  on [http://www.ubuntugeek.com/how-to-install-nvidia-drivers-in-ubuntu-feisty-or-later-versions.html](http://www.ubuntugeek.com/how-to-install-nvidia-drivers-in-ubuntu-feisty-or-later-versions.html) to enable the NVIDIA card, i was given three options, the last had (recommended) instead of (the version number). 


after download and reboot computer and it dont work - boot up monitor goes to powersaving, sometimes not, once it had a black screen with black, green , black, blue bars at about the height where the Ubuntu logo would be. in suse, it seemed to overwrite my ati card config and GUI booted on the NV card, i couldnt tell if it had drivers in SUSE or not, but because i couldnt check if it had drivers, i assumed none and installed something propriatry.

GRUB was invisible (though i wish it werent) so i had to look online to find the Shift method (it should say &quot;GRUB loading, hold SHIFT for options&quot;), and got it to show text instead of nothing during boot (i prefer it give text), and it of course it was an X problem, but i cant shift to runlevel 3....  pressed e, removed the junk that said to hide stuff and put a 3 on the end, Ctrl-X to boot and it ignored my 3 command. i dislike editing the xorg thing is there any EASY way of seting up multiple graphics cards?

firstly i dont know if it is even loading a driver for the card (before the bad driver install, i tried LSPCI and DPKG as said on [http://www.cyberciti.biz/faq/linux-detect-if-vga-driver-is-installed-not/](http://www.cyberciti.biz/faq/linux-detect-if-vga-driver-is-installed-not/) and i cant understand DPKG and i am guessing there is no GUI for showing installed drivers (otherwise that page would have said it) did u know that gates had something like that back in 3.1/95... overdue for one i think! im just grumpy - why so hard....   and i dont know how to get my &quot;comfortable&quot; refreshrates as i did in windows either....

because of the large amount of effort i put into SUSE, only to fail, i think i will ask everyone first. 

the failure (bug) in suse, there was two, one that LeftOf didnt work, and putting the mouse over to the left monitor resulted in an X crash with the mouse cursor flickering on the screen edge, and (i think) jumping to the other screen (solved by using rightof only). the other bug was intermittant and would have the same symptom between the screens on the NV card, but would only happen like 4 times per day which was still annoying... WZ2100 ran on the three monitors (the devs only designed for 2 monitors max so it was centered across the three screens, but no image on ati card due to known problems, so had 75% of the game visible). other than these things, three screens worked well.

using a liveCD installed to HDD. 10.04LTS (LL)


Charlie.

---

