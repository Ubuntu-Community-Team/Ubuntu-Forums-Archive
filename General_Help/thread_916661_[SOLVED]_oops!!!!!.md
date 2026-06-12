---
title: "[SOLVED] oops!!!!!"
date: 2008-09-11
forum: General Help
---

### Post by jamesxross on 2008-09-11
help! i installed hardy on an external hard drive tonight, and i must have been too eager and not paying as much attention as i should have, or something. i accidently moved my grub to the external (i think this is what happened, anyway). when i try to boot with the external unplugged, i get a GRUB error 21. this is a problem because the computer is a laptop that i regularly use for taking notes in class, and i wouldn't be able to have the external there with me to turn my computer on. thanks in advance :)

---

### Post by Rocket2DMn on 2008-09-11
Moved to General Help - please don't post support questions in the Tutorials & Tips forum, this is for guides and HowTos only, and the require staff approval.  Consider this a bump for your thread.

---

### Post by kokkus on 2008-09-11
Type the following commands:

sudo grub

Then you will get a grub prompt. From the grub prompt:

root(hd2,0)

setup(hd2)

quit


This assumes that your new install is sdc partition 1.

(Wrote by Titan8990)

---

### Post by jamesxross on 2008-09-11
sorry, rocket. i was anxious for help and couldn't determine where to post. thanks for the bump :)

i'm into a whole new world of trouble now. i can boot into ubuntu, but not into windows any more. when i try to mount my internal hard drive while in ubuntu (sda, my system calls it) this is what i get:

> root@jimmy-laptop:/home/jimmy# mount -t ntfs-3g /dev/sda1 /mnt
Unexpected clusters per mft record (-127).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

there's not anything 100% essential on the windows drive, but there are some things that would make life a lot easier when i go to reinstall (i'll probably set up a dual-boot with XP first, then ubuntu, all on the internal [80gb] and then just use the external as storage)

this is complicated by the fact that i'm at college (about an hour and a half from home) and left my xp install discs at home, but i'll jump that hurdle when i come to it.

---

### Post by jamesxross on 2008-09-11
i was able to get my windows back! i never thought i'd be so glad to see that xp splash screen. i used a utility called TestDisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) from within my ubuntu installation, and was able to repair the partition table for my windows drive. i think i'm gonna wait to try this all again when i have my xp discs handy, just to be safe :) thanks for the help.

---

