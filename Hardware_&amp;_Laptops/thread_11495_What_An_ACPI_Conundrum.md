---
title: "What An ACPI Conundrum"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by skarard on 2005-01-17
Well my deal here with ubuntu really sucks.

First problem... go on put grub in your MBR, it's harmless (well it has been a few years since this problem has been around) WHAM BAM no more hardware layer for windows... OOPS. 

Next well this is a shame,
when installing ubunta my keyboard didn't work... i knew what to do my problem is acpi so linux acpi=off. Nicly kept the same boot paramters when i started ubuntu for the first time when i wanted to configure everything... then hotplug orperation not permitted. with 2 items 

modprobe: FATAL: error inserting pciehp
modprobe: FATAL: error inserting shpchp

(taken from another post in the forum)

Then i read up on what these where about. so i turned acpi on by removing it from boot paramaters. THEN i couldn't use my keyboard to do the configuration. I have no windows and no ubuntu.

Royaly screwed. I have managed to get the hal.dll file back in the past with much annoyance and it's not configured properly for windows it was as though it is generic so i have no power management.. on my laptop. which oh my sucks. 

I thought oh ok ubuntu doesn't work maybe i will just have a windows only operating system. I do feel let down by the "look it's fine to over write your MBR", if they hadn't of said that i would have checked the forum etc.

---

### Post by Buffalo Soldier on 2005-01-17
First, it's ubuntU. Not ubuntA.

Second, I'm sorry that you installation did not turn out fine. I think most of us have had that problem. I have had the same problem installing Ubuntu on my friends computer. Luckily Ubuntu works perfectly on my computer.

I'm not really good at trouble shooting. But I'm sure many of UbuntuForums user are and would like to extend a helping hand. Nevertheless before they can help you, they would need some detail description of your problem, your computer specification, what was the error message and etc.

But as far as installing GRUB on the MBR. I personally have not encountered that problem. I've installed Ubuntu on 2 desktop and 1 laptop.

Eventhough your first experience (I assume, sorry if I'm wrong) with GNU/Linux is not a good one, I would like to welcome you to the GNU/Linux world and hope the less than wonderful experience did not kill your spirit.

---

### Post by skarard on 2005-01-17
Well I looked in to the Windows hal.dll error.

I have encounted this before but i have onec again fixed it with greater sucess this time.

What happend in my installation is that i had gentoo installed before a logical drive and that confused matters. As it was when i installed ubuntu it was installed at a primary drive which means some of the partion lables got moved around.

When grub was installed there was no problem overwriting the MBR but it was windows boot loader that had a problem. It was looking in a diffent sector of the disk for the HAL.dll. so it couldn't find it. THe windows error is misleading on that count.

to fix this problem you need a windows xp install disc/recovery disk.
[http://www.wown.com/j_helmig/wxprcons.htm](http://www.wown.com/j_helmig/wxprcons.htm)

You get to the recovery consol and then select your windows installation

Type in:

Attrib -H -R -S C:\Boot.ini
DEL C:\Boot.ini
BootCfg /Rebuild
Fixboot

Taken from: [http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

I had to type each attrib in by them self (eg. attrib -H C:\boot.ini (nextline) attrib -R C:\boot.ini)

If you are having problem type in cd c:\ then type dir and you should see what attributes to remove from boot.ini.

when you rebuild it will ask you for a name put some thing like windows xp home, and remember what you typed. then you can leave the boot params empty unless u know what you need.

then fixboot and after than you can reboot your computer remove the windows xp disc and you should be able to boot in to windows with the new configureation.

---

