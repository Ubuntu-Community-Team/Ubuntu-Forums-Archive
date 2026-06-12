---
title: "Wrong menu.lst entry for windows"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by geovino on 2009-05-08
I installed Ubuntu 9.04 on a laptop w/ Vista and Mint 5. I replaced Mint 5 w/ 9.04. But the bootloader doesn't work. Here's the menu list now:

Ubuntu is installed but the bootloader doesn't work. The menu.list needs to be adjusted.

here's the menu.list

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5c3a8782-9e1a-4d4e-bd0e-63ccafbeb09d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5c3a8782-9e1a-4d4e-bd0e-63ccafbeb09d ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5c3a8782-9e1a-4d4e-bd0e-63ccafbeb09d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5c3a8782-9e1a-4d4e-bd0e-63ccafbeb09d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5c3a8782-9e1a-4d4e-bd0e-63ccafbeb09d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

Here's the partition table:


What do you think needs to be changed for the Windows entry to work?

---

### Post by dandnsmith on 2009-05-08
> **geovino said:**
> 
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

Here's the partition table:


What do you think needs to be changed for the Windows entry to work?

the rootnoverify line should be:
*rootnoverify (hd0,1)*
but the rest should be OK

---

### Post by geovino on 2009-05-08
> **dandnsmith said:**
> the rootnoverify line should be:
*rootnoverify (hd0,1)*
but the rest should be OK

It actually was (hd0,1) originally and that didn't work either.

---

### Post by dandnsmith on 2009-05-08
If that thumbnail pic is to be believed, then the filesystem is on sda2 which is (hd0,1). I do wonder what happened to sda1 - is there a partition which got deleted (and really had the vital stuff for booting)?

The only other detail, and this wouldn't affect the issue, is that the boot flag is already set, so the makeactive is not needed.

---

### Post by geovino on 2009-05-08
the menu was OK, it was Vista that was picky. I was going to dump Vista completely, but I thought I wanted  to have both OSs on one hdd for now. So I ran the recovery and system disks that Acer sent me and I got Vista installed again and then reinstalled Ubuntu and then everything was OK :)

Jaunty is the best Ubuntu so far! 

Problem Solved!

---

### Post by geovino on 2009-05-14
I decided that Vista is not needed at all so I reinstalled Ubuntu 9.04 on the entire hard drive. 

Now I really solved the problem. :)

---

