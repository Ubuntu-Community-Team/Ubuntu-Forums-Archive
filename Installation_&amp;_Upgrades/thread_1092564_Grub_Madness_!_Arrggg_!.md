---
title: "Grub Madness ! Arrggg !"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by killpotts on 2009-03-10
Hello all.

I've been trying to install to an external Hard drive for quite some time, and I finally had some success in that all the files for boot have made it to the external device. Unfortunatly, despite that fact that I went into advanced and made sure GRUB was to be installed on the external, it still failed anywayy and I get a Grub error 21 when I attempt to boot from USB ( go figure. )

So now I am back in the live CD trying to figure out how to fix grub.

This is what I tried:


```
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c9e3c9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         767        9729    71995297+   7  HPFS/NTFS
/dev/sda2               1         766     6152863+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000065c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         305     2449881   83  Linux
/dev/sdb2             306       19457   153838440    5  Extended
/dev/sdb5           17901       19457    12506571   82  Linux swap / Solaris
/dev/sdb6             306       17180   135548374+  83  Linux
/dev/sdb7           17181       17900     5783368+  82  Linux swap / Solaris

Partition table entries are not in disk order
root@ubuntu:~# grub-install /dev/sdb1
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```




*Sdb is my external device that I tried to install linux to.


So basically I can't install Grub to the Boot partition because it "can't find device for /boot:" ? So it recognizes that its a boot sector but at the same time thinks it is not ?

I'm stumped

Is there anything I can do to fix Grub that can be done from the Live CD ?

---

### Post by killpotts on 2009-03-10
Also useful to know for anyone trying to help me, my internal HD is dead\on its last legs.

---

### Post by Neo_The_User on 2009-03-10
sorry can't help. ask one of the forum admins or mods. how about just doing it the normal way? everything one 1 partiton and hard drive and just one operating system and thats it? Guided use entire disk??

---

