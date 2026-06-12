---
title: "Intel p55: Fakeraid install with dmraid"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by mtparrish on 2009-09-28
Just a bit of context:  I'm doing a dual-boot (Windows 7 / Ubuntu 9.04) install on an intel p55 bios controlled raid 0 array.  Most of the procedure I've been following comes from [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) and [http://wiki.debian.org/DebianInstaller/SataRaid](http://wiki.debian.org/DebianInstaller/SataRaid).

Here's what I've done to get this far:
Boot into the live cd

```
$ sudo apt-get install dmraid
$ sudo dmraid -ay
```Create an ext3 and swap partition.
Use the ubiquity installer without installing grub.

Without restarting:
```
$ sudo swapoff -a
$ sudo mount /dev/mapper/isw_whatever05 /target
$ sudo mount --bind /dev /target/dev
$ sudo mount --bind /dev /target/dev
$ sudo mount -t proc proc /target/proc
$ sudo mount -t sysfs sys /target/sys
$ sudo cp /etc/resolv.conf /target/etc/resolv.conf 
$ sudo chroot /target
# apt-get update 
# apt-get install dmraid
# apt-get install grub
# mkdir /boot/grub
# cp /usr/lib/grub/x86_64-pc/* /boot/grub/
# grub --no-curses --device-map=/dev/null
grub> device (hd0,4) /dev/mapper/isw_whatever05
grub> device (hd0) /dev/mapper/isw_whatever0
grub> root (hd0,4)
grub> setup(hd0)
```All goes well and I update-grub, edit my menu.lst to add windows, update-grub again and reboot.
Grub then lets me successfully load Windows, but fails to load Ubuntu -- dmesg shows corrupt superblocks on my ext3.

This has consistently happened on several attempts.  Since I'm using new hardware, I'm not sure if it's a bug or my procedure.  I would consider using purely software raid (mdam) only as a last resort since I would greatly prefer to have Windows running on raid 0 as well.

Any help, suggestions, or resources would be greatly appreciated.

---

### Post by mtparrish on 2009-09-28
Also worth mentioning for anybody else attempting this:

Windows 7 actually uses a portion of unpartitioned drive space for their boot loader.  This 8MB chunk is typically located either at the beginning of your primary drive (not just the drive you installed on) or immediately before the "System Reserved" partition.

My grub menu.lst entry uses root(0,1) instead of rootnoverify and points to the installation partition as opposed to system reserved.

I'm also discovering that it may be possible to use mdadm in linux and the dynamic drive in windows to achieve independent, partition-based software raid.

I would still love to get dmraid working though.

---

### Post by mtparrish on 2009-09-29
No clue what fixed it, but the above procedure eventually worked.
On my last attempt, I deleted my extended partitions and recreated them.

Maybe it was just coincidence?

---

