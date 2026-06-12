---
title: "[SOLVED] Remove GRUB menu options?"
date: 2008-09-24
forum: General Help
---

### Post by SiHa on 2008-09-24
Hi,

I think thi sis probably quite a simple task, but don't want to be left with an unbootable system by tinkering blind!

I've been running an XP / Ubuntu dual-boot for quite a while now (the wife's not ready to abandon Windows yet) with Ubuntu on an old drive I had hanging around (literally - it's suspended off the IDE cable)

Naturally, I want to get rid of this extra drive. I took the plunge last night and installed Mythbuntu 8.04.1 on the main drive, letting the installer take care of the repartitioning. Everything is fine, but I forgot to pull the spare drive before install so now GRUB has the legacy Ubuntu install as an option at the bottom.

During the install, I noticed that GRUB was installed on hd(0), so I assume I can just comment out these legacy options and pull the drive?

TIA,

Simon

---

### Post by Elfy on 2008-09-24
Should be fine to do so as long as hd0 isn't the one hanging off a floppy piece of cable :) personally if the drive is not on the way out I would just use it as extra data storage...

To edit the menu list - run this from a terminal, Ctrl+O, Enter to save then Ctr+X to exit 

```
sudo nano -B /boot/grub/menu.lst
```

Remove the entries you want to lose from there.

Nice to see someone else local :)

---

### Post by SiHa on 2008-09-24
Thanks.

I probably will use the old drive as extra storage, but will most likely just use it on a USB-IDE adaptor when I need it.

Out of interest, why the '-B'? (Backup?)

Keep up the good work forestboy (or girl...?)

Cheers,

Simon

---

### Post by Elfy on 2008-09-24
yep it's for a backup, I think it does it anyway but...

a male piskie :)

---

### Post by SiHa on 2008-09-25
...from Cornwall originally?

---

### Post by Elfy on 2008-09-25
No - local to here, so a pixie rather than piskie lol.

---

