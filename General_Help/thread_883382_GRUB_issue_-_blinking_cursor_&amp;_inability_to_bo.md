---
title: "GRUB issue - blinking cursor &amp; inability to boot from live cd"
date: 2008-08-07
forum: General Help
---

### Post by 4Play on 2008-08-07
Hello, I am experiencing very strange problemas with grub's boot process:

I have a dual boot ubuntu 8.04 64bit / Vista 64bit on a Dell XPS M1530.

it has been working fine for a while, but all of a sudden, when I turn on the PC, all I get is a black screen with a white blinking cursor ( _ ) at the top of the screen...nothing else.
I managed to get into the system by using a super grub boot CD, but before I got to that point I tried to boot into ubuntu's live CD, but got an IO error reading the disk (i was initially using a CD I got by mail from ubuntu.org) so I got a fresh image and burned it..same thing, the "check disk for errors" option also yields the same result. I find it extremely improbable that both disks are bad, especially because I installed my current installation from the CD that I got by mail.

This is what geometry (hd0) yields:

> geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0xde
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x82
   Partition num: 6,  Filesystem type is ext2fs, partition type 0x83


and find /boot/grub/stage1 -> > (hd0,6)

my menu.lst has the following setup:

> title		Ubuntu
root		(hd0,6)
savedefault
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5cf30022-9385-430e-a102-97aa732ce546 ro quiet splash i8042.nomux=1
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Windows Vista
root		(hd0,1)
makeactive
chainloader	+1

I dont know why grub doesn't seem to be able to find the boot files, all the parameters seem to be correct, but I must be missing something here...

The "IO Error" on the CD's also intrigues me, since I managed to install from the CD, but for some bizarre reason, I cant boot from it...must be soething related to my system BIOS. This is very frustrating because I want to resize/create new linux partitions, and since I only have a / and a swap now, I cant resize from within linux..I need to be able to boot from a live-cd.

Running a Dell XPS M1530 with the A10 bios revision btw...

anyway, if anyone can shed some light on these issues I would be eternally grateful.

Thanks :)

---

### Post by 4Play on 2008-08-08
erm....i "solved"this myself..turns out simply running grub-install hd0 solved the issue...I have no idea why gurb seems to have uninstalled itself from the boot sector, but anyway, the solution was very simple, but at 2 am even simple solutions get complex :p

---

