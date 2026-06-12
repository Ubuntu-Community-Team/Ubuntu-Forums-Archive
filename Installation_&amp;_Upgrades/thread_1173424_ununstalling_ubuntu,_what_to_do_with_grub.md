---
title: "ununstalling ubuntu, what to do with grub?"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by reinaldistic on 2009-05-29
ok, i am uninstalling ubuntu on my family's pc, after years of sharing computers i finnally have my own, so i want to make theirs pure windows (coz it's the only OS they will use)so, i already got a partition manager and all, i was wondering, how do i uninstall ubuntu, (i got gparted live cd) unless i have to use the ubuntu cd which i still have i will use gparted, so, how do i uninstall ubuntu (8.10) and what will happen with grub, can i replace it with the original windows stuff, or will it keep doing what it does on it's own? (i would rather get the original windows stuff, but if it's not possible just instruct me so that they dont have to select the windows just go straight to it on bootup) please help me they wont like it if i leave ubuntu's grub there (that's why they got me my own pc mostly)

---

### Post by SuperSonic4 on 2009-05-29
I would be easiest to use an Ubuntu Live CD to remove the partition ubuntu resides on, possibly extend windowds into the space left. Then grab a windows disc and fixmbr from the setup

---

### Post by rpaar63 on 2009-05-30
many of us don't have a "windows" disc, my systems came with windows preinstalled, but without a proper install disc. Just one of those restore discs, so the "fixmbr" solution isn't an option.

Got to this [[COLOR="Blue"]site[/COLOR]]("http://dimio.altervista.org/eng/") and scroll down to "HDHacker" donwload this standalone, no install needed program.It is a Windows Program, put it on a usb drive, it will save the mbr to a file. when i gave my wife my old laptop i took the ubuntu off of it for her.

 I loaded HDHacker from a usb drive on another system with XP on it and saved the MBR to a file, then put the usb drive into the laptop i was removing ubuntu from.
 I loaded the mbr from the file and used "load sector from file" and the used the "write sector on disk" options. the GRUB boolader is now gone, it will boot into XP as though ubuntu was never there.
Now load your favorite partioning software to remove or resize the partions to what suits you. I have a usb drive with Partion magic on it that i use.

Rob

---

