---
title: "Dual booting windowsXP and ubuntu ON SEPERATE DRIVES"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by Orbo on 2005-01-24
I know there are other threads that address the issue of dual booting, but all of those deal with partitioning one drive.  My question is, how would I go about installing Ubuntu on the other HDD so I can keep my already present Windows XP installation on the main HDD.  Is the MBR of Windows XP going to be a problem in this situation?

---

### Post by akurashy on 2005-01-24
if grub tells you that hda is your main then hdb must be your second HD drive i guess

---

### Post by cheleb on 2005-01-24
[QUOTE=Orbo]I know there are other threads that address the issue of dual booting, but all of those deal with partitioning one drive.  My question is, how would I go about installing Ubuntu on the other HDD so I can keep my already present Windows XP installation on the main HDD.[/QUOTE]
Hi Orbo,

maybe there's an easier way to do this but here is my suggestion.

Assuming your XP installation is on your primary master hd ( which is must be, because windows doesn't want to be on any secondary ide bus ) do the following.
Attach your XP-hd to the secondary master channel.
Attach the hd ubuntu is supposed to be installed on to the primary master channel.
Install ubuntu as you normally would do.
At some point setup detects your win installation and writes this information into your grub menu.lst. Unfortunately this doesn't work "out of the box" so you have to tweak that file a little bit.
Open /boot/grub/menu.lst and add this [COLOR=Navy]before[/COLOR] the "boot (hd1,0)" statement in your windows section.
```
map (hd0, hd1)
map (hd1, hd0)
``` 
This makes the windows bootloader think it is installed on an primary hd although it really isn't.

[QUOTE=Orbo]Is the MBR of Windows XP going to be a problem in this situation?[/QUOTE]Since both Systems are on separate hd's the MBR of your XP-installation is not affected at all.

Worked for me(tm). I banned Windows out of my life a half year ago so i can't say if this is still valid. good luck!

Cheers,
cheleb

---

### Post by Marquis_de_Carabas on 2005-01-24
I don't see why this would be a problem. I've had a few distros installed split across two hard drives before and never had to do anything more than add a couple of entries to Grub (and that was only because I was trying out several Linux distros and sometimes they didn't notice each other - they all found the Windows XP install).

Just install Ubuntu on the second hard drive, and put Grub on the MBR of the first hard drive (the one with Windows on). It's really no more difficult than that (or at least it never was for me).

---

### Post by wainop on 2005-01-25
I installed ubuntu on HDb with Windows XP on HDa.
When the grub boot menu came up I selected windows.
It started to boot in windows, but then quit and switched to ubuntu.
I could not boot windows.,so I reinstalled  windows. I have had trouble
with grub,using red hat.

---

### Post by Buffalo Soldier on 2005-01-25
[QUOTE=wainop]I installed ubuntu on HDb with Windows XP on HDa. When the grub boot menu came up I selected windows. It started to boot in windows, but then quit and switched to ubuntu. I could not boot windows.,so I reinstalled  windows. I have had trouble with grub,using red hat.[/QUOTE]Did you installed GRUB on hd**a** or hd**b**?

---

