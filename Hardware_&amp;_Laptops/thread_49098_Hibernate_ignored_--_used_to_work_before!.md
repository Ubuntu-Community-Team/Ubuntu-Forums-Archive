---
title: "Hibernate ignored -- used to work before!"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by André on 2005-07-15
Hi everybody,

i just did a fresh Hoary installation because i borked up my system a bit too much for my opinion :-) System is a DELL INSPIRON 8600. I am using the "ati" not the "fglrx" module for video output.

Stupid me forgot to partition a swap device during installation so hiebrnation didn't work.

But now i created a swap partition on /dev/hda10. Here the output of fdisk:

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/hda1               1           7       56196   de  Dell Utility
/dev/hda2               8          31      192780   83  Linux
/dev/hda3              32        1247     9767520   83  Linux
/dev/hda4            1248        9729    68131665    5  Erweiterte
/dev/hda5            1248        2463     9767488+  83  Linux
/dev/hda6            2464        4287    14651248+  83  Linux
/dev/hda7            4288        6111    14651248+  83  Linux
/dev/hda8            6112        7935    14651248+  83  Linux
/dev/hda9            7936        9152     9775521   83  Linux
/dev/hda10           9153        9729     4634721   82  Linux Swap / Solaris

I already did a restart (for the new table), a mkswap and swapon /dev/hda10. In my menu.lst there is the line # kopt=root=/dev/hda3 resume=/dev/hda10 ro.

When i hibernate my system now, it's copying everything (i can see the black screen and my HD work) but when i reboot it just starts like a normal reboot and doesn't use the hibernate features (like just bringing up the GUI and that quick). It just ignores hibernation :-(

Any ideas??

Greetings
André

P.S.: I wasn't too sure about this option

# kopt=root=/dev/hda3 resume=/dev/hda10 ro

so i also tried 

kopt=root=/dev/hda3 resume=/dev/hda10 ro

Still doesn't work. I think that was absolutely wrong because now all my mounted devices were unclean and the boot proces is still the same :-(

---

### Post by André on 2005-07-15
I think this was the wrong forum. Posted the same in Laptop support.

@Mod: Please delete this one.

Greetings
André

---

