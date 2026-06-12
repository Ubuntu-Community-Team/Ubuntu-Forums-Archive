---
title: "Gnome sensors applet CPU Temp. report unlikely ??"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by Rab_C_Nesbitt on 2007-05-18
Hi guys!  (And thanks in advance for your support!!!)

Been playing with Feisty Fox for 2 days now, blown away by how easy and effective it is – compared to a well known vole....

Confused a bit on temperature monitoring on CPU.  I run a home-built PC based on a FoxConn 
K7S741GXMG-6L, Sempron 3000+, 512Mb etc etc.. (It all worked fine, first time, with UBUNTU, bit of playing round with display resolution but now sorted...), dual boot with XP.

The BIOS Hardware Health monitor reports temperature around 60 deg C, as does “PC Wizard” under Windows XP.  Under UBUNTU, Gnome sensors applet reports 40 deg, as does acpi -t. And that 40 deg never changes, whereas the hardware monitor changes a bit, as does XP software monitoring, particularly if stressing the processor.  They also report other stuff – CPU fan speed, Hard disk temp... 

I'm kinda inclined to believe the hardware BIOS monitor, and XP, and don't know what to do next...   Any advice gratefully received... 

When I try “sudo sensors – detect” I get 

============ start cut 'n paste ==============
phillip@phillip-desktop-SEMP3000:~$ sudo sensors -detect

Password:

sensors: invalid option -- d

Try `sensors -h' for more information

phillip@phillip-desktop-SEMP3000:~$ 

=================end cut 'n paste ========

Yours aye
Very much a newbie...

Rab
Fort William
Scottish Highlands
Looking out over the sea & the mountains ...

---

### Post by davidshere on 2007-05-22
you have a space in there.  try

```
sensors-detect
```

---

