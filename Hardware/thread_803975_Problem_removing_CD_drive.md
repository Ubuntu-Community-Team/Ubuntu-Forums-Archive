---
title: "Problem removing CD drive"
date: 2008-05-22
forum: Hardware
---

### Post by SirNelsonGap on 2008-05-22
Hi - New member here.

I have installed Ubuntu on a pc intended for Ubuntu use only.  Do do so I borrowed a Cd drive from another PC.  Install went well and pc boots fine.  However, I now want to remove the CD drive and put it back where it belongs.  When I remove it the PC no longer boots, but prompts for me to insert bootable media.  On at least one occasion it attempted to boot, but didn't go into ubuntu, may have stopped in grub butI'm not sure.

What can I do to make sure the pc will still boot after the CD drive is removed?  I have tried to removed the cd drive from the bios list of bootable devices.

ASUS P5KPL
both CD and HD IDE

Any help appreciated

---

### Post by mc4man on 2008-05-22
Every bios is different, what you're probably looking for (in set up) is a list of your drives ( - should say something like cd-rom reader). You'd want to remove it or set it to off. Make sure your turning off or disabling the cdrom not hdd
If your unsure post back what you see and or options

---

### Post by SirNelsonGap on 2008-05-25
Problem solved.

Although the HD links were set to master, it didn't seem to be recognised as such when the CD was removed.  I changed the link to 'simple' and all seems OK now.  Maybe its because it's an old drive (4.3G from an old W95 machine).

Anyway all is fine now.  :)

---

