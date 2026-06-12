---
title: "[SOLVED] Ubuntu drive thinks it's a fat"
date: 2008-09-11
forum: Hardware
---

### Post by DariusS on 2008-09-11
hey, not sure if anyone will be able to help on this one, but I'm still hopeful.
the other day, I plugged a dell HDD into my machine to help a friend access some files. the drive had a dell recovery partition that, upon rebooting, my bios tried to boot off of. the recovery partition then seemed to try to "recover" my ubuntu drive. Now I can't boot into linux and when I boot off a liveCD, the drive in question shows up as a 256GB, and next to it is a 56MB drive as well (the drive is only a 120GB). I'm hoping that only the mbr or the like is messed up and I can recover my data. I don't really need to fix the install, I just need access. Does anyone know of a program (open source or freeware, Linux or XP) that will help in recovering my data?

Thanks.

---

### Post by qstraza on 2008-09-11
boot live cd and type fdisk -l to check the partitions, then try mounting them and look whats on them, maybe you will see your files, hopefully, but you probably already tried that...

---

### Post by DariusS on 2008-09-11
Ok, (in live session currently)

fdisk -l output:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           7       56196    6  FAT16
/dev/sda2               8       29988   240822382+   7  HPFS/NTFS
/dev/sda3           29989       30393     3253162+  db  CP/M / CTOS / ...

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00031caf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS

```

and obviously /dev/sda is my ubuntu drive. as you can see, the file systems are all out of whack.

When I try to mount, this is what I get, along with the dmesg | tail report

```

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /home/ubuntu/Documents
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[  422.796853] attempt to access beyond end of device
[  422.796855] sda: rw=0, want=481757217, limit=234441648
[  422.796858] attempt to access beyond end of device
[  422.796860] sda: rw=0, want=481757218, limit=234441648
[  422.796862] attempt to access beyond end of device
[  422.796864] sda: rw=0, want=481757219, limit=234441648
[  422.796867] attempt to access beyond end of device
[  422.796869] sda: rw=0, want=481757220, limit=234441648
[  422.829351] EXT3-fs error (device sda2): ext3_check_descriptors: Block bitmap for group 0 not in group (block 65569184)!
[  422.829696] EXT3-fs: group descriptors corrupted!

```

group descriptors corrupted? is there any way to force a read as ext2/3?

please don't tell me I'm screwed! I still have faith there is a way to rewrite the TOC or something. I just have SO much stuff on this drive I don't want to lose.

---

### Post by qstraza on 2008-09-11
well i dont think you can mount as ext becouse its not linux formated anymore, i guess that hp thing reformated your ubuntu drive and your data is kinda lost...

hope someone else can help you...

---

### Post by DariusS on 2008-09-11
ok, I figured it out!!!
WOOT!!

so, if anyone else comes into a similar problem, what I did is under the live session of Ubuntu Hardy, I opened up synaptic and installed testdisk (partition recovery tool, CL only, needed to enable universe in repos) and ran
```
sudo testdisk
```

this gave me some options on which disk to check, etc. and was able to analyze the partitions and rewrite the partition tables. 

Note: this did not fix the boot problem, I can access it only through liveCD. I could however reinstall grub, but is not my intention. just backing up all my data.

---

