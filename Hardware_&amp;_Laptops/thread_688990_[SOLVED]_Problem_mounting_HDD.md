---
title: "[SOLVED] Problem mounting HDD"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by HanaD on 2008-02-05
i am using Ubuntu 7.10 on X61 tablet.

The problem is that my external hard drive is not mounted automatically, also when i try to mount it from terminal i get an message :
hana@X61Tablet:~$ sudo mount /dev/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

fdisk -l output:

hana@X61Tablet:~$ sudo fdisk -l
Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xe11595f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10612    80226688+   7  HPFS/NTFS
/dev/sda2           11395       11533     1050840   82  Linux swap / Solaris
/dev/sda3           10613       11394     5911920   12  Compaq diagnostics
/dev/sda4           11534       12921    10493280   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    c  W95 FAT32 (LBA)


But, surprisingly i can use this hard drive on my desktop which i salso running Ubuntu7.10 without any problem, it mounts automatically on my desktop

can anyone help me please, as i am not able to access any of my data.

Regards,
Hana

---

### Post by Crashmaxx on 2008-02-06
Check your settings in System>Preferences>Removable Drives and Media.

And you first command doesn't work because you are not telling it where to mount. Create a folder in /media called whatever you like, let's say usb1. Then make sure it has permissions and is owned by you. Then do the command again with /media/usb1 at the end. It will look something like this:
```

sudo mkdir /media/usb1
sudo chown -R hana:hana /media/usb1
sudo chmod -R 755 /media/usb1
sudo mount /dev/sdb1 /media/usb1

```
And it should show up on your desktop. But hopefully messing with the first setting will fix it.

Also, are you having it plugged in on boot, or plugging it into the running system? It handles that differently, so try plugging it into the running system.

---

### Post by HanaD on 2008-02-07
but do i always have to run this command in order to mount my hard drive.
i also noticed that even the live USB i made for Ubuntu, only mounts the casper, and the other partition that was FAT16 on that usb could not automatically mount,

i think there is some problem mounting the windows filesystems.
this is not so on other machines that i use with same OS.

how can i get them to mount when i plug them in?

removable drives and media have mount options checked,

please help.

---

### Post by Crashmaxx on 2008-02-07
Ok, well the best way to do it is to edit add the partitions to your fstab file. Its a little technical, but all you'll really be doing is adding a line to this file to tell it what to put where and who can access it. After that is setup, the worst you would have to do is type one command, but you should be able to get it to always mount automatically and in the same place.

Go ahead and read this:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=(mount](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=(mount))
You will want to look at the "Mounting partitions manually" section, the script may work, but I've never used it.

Hopefully that will give you a good start. If you still have trouble just ask.

---

### Post by HanaD on 2008-02-08
yeah thanks for that forum,
actually that was a great help but i have one little query left,

when i plug in that drive in USB it gives me a message "Invalid mount option when attempting to mount the volume"

have no clue, and why is it that i get this message only on my laptop not desktop?

works fine with desktop.

REgards,
Hana

---

### Post by p_quarles on 2008-02-08
Support thread moved to Hardware & Laptops.

---

### Post by Crashmaxx on 2008-02-10
> **HanaD said:**
> yeah thanks for that forum,
actually that was a great help but i have one little query left,

when i plug in that drive in USB it gives me a message "Invalid mount option when attempting to mount the volume"

have no clue, and why is it that i get this message only on my laptop not desktop?

works fine with desktop.

REgards,
Hana

Post the contents of your /etc/fstab and I'll try to see what is wrong. Probably put in a bad option.

---

### Post by HanaD on 2008-03-14
This is my output from etc/fstab, dont know hoe and why but the hard disk started showing up automatically suddenly,

Thanks anyhow,

Regards,
Hana

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=7838a812-4912-4a31-9bac-0230db3b75d9 /               reiserfs notail          0       1
# /dev/sda1
UUID=F2201F06201ED189 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=F055-48D8  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=8697b141-1b99-4d0e-8cea-e5ad02bd4bb1 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Endolith on 2008-04-27
USB drives shouldn't be handled by fstab at all, should they?

[http://ubuntuforums.org/showthread.php?t=608210](http://ubuntuforums.org/showthread.php?t=608210)

---

