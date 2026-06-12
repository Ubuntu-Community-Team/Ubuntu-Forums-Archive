---
title: "mount -t vfat /dev/sdb1 /media/stick"
date: 2010-12-16
forum: Hardware
---

### Post by muuwt1 on 2010-12-16
hello,
hoping i wouldnt have to resort to posting. ive done my research still no luck. running mint 10. trying to mount my 8 gig HP flashdrive bc it wont automount...

```
eee mo # lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 03f0:3207 Hewlett-Packard 
Bus 001 Device 002: ID 13d3:5071 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
eee mo # fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00062080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19087   153309184   83  Linux
/dev/sda2           19087       19458     2978817    5  Extended
/dev/sda5           19087       19458     2978816   82  Linux swap / Solaris

Disk /dev/sdb: 8015 MB, 8015282176 bytes
247 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1022     7825423    c  W95 FAT32 (LBA)
eee mo # mount -t vfat /dev/sdb1 /media/stick
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
/media/stick is an existing directory.
any suggestions? mint 10 is whack? thank you great ubuntu community

---

### Post by coffeecat on 2010-12-16
Did you see this?

> **muuwt1 said:**
> ```
eee mo # mount -t vfat /dev/sdb1 /media/stick
[COLOR=Red]mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error[/COLOR]
```

It looks as though you could have a corrupted filesystem. Have you tried mounting the stick in Windows?

Also, try this:

```
udisks --mount /dev/sdb1
```**Don't do that command as root.** But I doubt whether it would work anyway if the fs is damaged.

---

### Post by madoba on 2011-11-19
Help, I have this same error when trying to mount a usb disk. 
[COLOR=Red]wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/COLOR]
that, I might add, would mount perfectly fine, prior to when I created a backup of my picture directory. 

ok I backed it up with this command [COLOR=Black](**sudo tar cvf /dev/sbd1 . **  )[/COLOR]

Ok here are the details, after executing this command it put a bunch of gibberish files on the usb thumb disk but apparently that's what is was suppose to do because I could  untar the files 
(**tar xvf /dev/sdb1**)
into another directory and recover the files I just backed up. Ok everything seems fine. I don't know why the backup was created like it was, but it was my first backup to a usb thumb disk. I'm still learning. Maybe I just happened to look at the wrong page from google. The command described was how to backup to Tape, I thought it would be fine for Disk.

However when I unmounted the usb and plugged it back in and restarted the computer, the usb would not mount.

I did a lsusb and found it.
**lsusb**
Bus 001 Device 006: ID 0781:5530 SanDisk Corp. 

I then looked in the dmesg to identify the correct device
**dmesg**
[  247.185730] sd 7:0:0:0: [sdb] Write Protect is off
[  247.185737] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  247.185741] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  247.190405] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  247.195803]  sdb: sdb1
[  247.198478] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  247.198487] sd 7:0:0:0: [sdb] Attached SCSI removable disk

when i attempted to mount it with this command. (yes another google page)
**sudo mount -t vfat uid=me gid=users /dev/sdb /home/me/Desktop/flash**

  I got this error
mount: [COLOR=Red]wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/COLOR]

**dmesg** shows
[  360.981267] FAT: bogus number of reserved sectors
[  360.981274] VFS: Can't find a valid FAT filesystem on dev sdb.
[  402.113575] EXT3-fs (sdb): error: can't find ext3 filesystem on dev sdb.

Help, How in the world was it working fine when I first backedup to the usb thumb drive, only to give me the finger when I rebooted and attempted to remount the disk thumb drive.

---

