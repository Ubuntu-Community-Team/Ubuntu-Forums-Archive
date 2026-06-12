---
title: "Trouble Mounting USB Device"
date: 2008-06-22
forum: Hardware
---

### Post by zumbrujm on 2008-06-22
Recently, I purchased a Sony NWZ-A816 MP3 Player.  This device is supposed to act as simply a mass storage device, requiring no specific software in order to sync.  After two weeks of using it without a problem, it will no longer connect to Ubuntu.  I don't know what commands I should use to mount it from the terminal, but it no longer automounts.  It will automount on XP, however.  

After searching around the forums, I came across this command:
```
dmesg | tail
```

The output of this is:
```
[  148.635097] attempt to access beyond end of device
[  148.635100] sdb: rw=0, want=4294967292, limit=7503872
[  148.635106] attempt to access beyond end of device
[  148.635109] sdb: rw=0, want=4294967292, limit=7503872
[  357.260226] tifm0 : demand removing card from socket 0:1
[  357.260281] mmc1: card 9177 removed
[  365.369027] tifm_core: MMC/SD card detected in socket 0:1
[  365.696062] mmc1: new SD card at address 9177
[  365.696279] mmcblk0: mmc1:9177 SD01G 1006080KiB 
[  365.696334]  mmcblk0: p1

```

If someone would help me decipher this response, and help me figure out how to get my device recognized again, I would appreciate it.  Thanks!

---

### Post by nick_h on 2008-06-23
Have a look at:
```
sudo fdisk -l
```

It should mount automatically.  You could try and mount it using the *mount* command, for the manual page type:
```
man mount
```

---

### Post by Odrodzona-Sarmacja on 2008-06-23
Looks like 127gb fat32 error to me. Ubuntu is a modern os and should be able to use space on it above 127gb. Personally I would try setting the mounting of it in /etc/fstab and then if i disconnected it and connected again I would just use "sudo mount -a" in terminal. It could be something with XP handling hard drives. Windows can cause hard drives to fail automount on Ubuntu. Try "sudo blkid" and if this hd is listed there then it is mountable by Ubuntu at least manually.

---

### Post by zumbrujm on 2008-06-23
Hey Guys,

I was able to mount it manually by looking up its location (/dev/sdb1, /dev/sdc1, etc.), and then using
```

sudo mount -t vfat /dev/sdb1 /mnt/Walkman

```

The output of 
```
sudo fdisk =l

```
is
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4479    35977536   83  Linux
/dev/sda3           12040       12161      979965   82  Linux swap / Solaris

Disk /dev/mmcblk0: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              21      167680     1005958+   6  FAT16
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 3841 MB, 3841982464 bytes
1 heads, 62 sectors/track, 30257 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.
Note: sector size is 2048 (not 512)

Disk /dev/sdc1: 2199.0 GB, 2199023253504 bytes
1 heads, 62 sectors/track, 17318416 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdc1p1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.

```

The device in question is /dev/sdc1 which is a 4 Gb mp3 player acting as a mass storage device.  It says it is 2199.0 GB though...

Also, how would I get this to mount automatically?  I edited /etc/fstab to:
```

#Getting Walkman to automount
/dev/sdb1 /mnt/Walkman	vfat	defaults	0	0

```

Thanks again for your help.

---

