---
title: "Western Digital 'My Book' 3TB not Mounting but is being shown in Terminal."
date: 2017-05-21
forum: Hardware
---

### Post by youbob1212 on 2017-05-21
I just updated from Ubuntu 16.04 to 17 version, and on the previous version, I had no problems seeing my external hard disk. And this was after I disable that protection lock that kept me from opening it in the past. Now, I can't see my drive! I don't have any other OS to test it out. I had a dual boot of Windows but when I decided to update Ubuntu versions I had gotten rid of Winblows. 

So I have installed NTFS drivers. Still, can't see it.   You know Let me show you want I'm seeing from the terminal. 

lsusb 
```

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 1d57:ad17 Xenta 
Bus 004 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 004 Device 005: ID 0d8c:0005 C-Media Electronics, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 003: ID 1058:1140 Western Digital Technologies, Inc. My Book Essential (WDBACW)
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2357:0103  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




```

sudo fdisk -l 

```

Disk /dev/mapper/sda5_crypt: 931 GiB, 999689289728 bytes, 1952518144 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/mapper/ubuntu--vg-root: 915 GiB, 982524100608 bytes, 1918992384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/mapper/ubuntu--vg-swap_1: 16 GiB, 17163091968 bytes, 33521664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sdb: 2.7 TiB, 3000558944256 bytes, 732558336 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes



```

This is what I get when I try to mount it. 

sudo mount /dev/sdb /mnt 

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb,       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.



```

To pull up on more information. 


dmesg | tail

```
[ 1015.354278] scsi 8:0:0:1: Enclosure         WD       SES Device       1019 PQ: 0 ANSI: 6
[ 1015.397865] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 1015.397949] sd 8:0:0:0: [sdb] 732558336 4096-byte logical blocks: (3.00 TB/2.73 TiB)
[ 1015.398195] ses 8:0:0:1: Attached Enclosure device
[ 1015.398292] sd 8:0:0:0: [sdb] Write Protect is off
[ 1015.398295] sd 8:0:0:0: [sdb] Mode Sense: 47 00 10 08
[ 1015.398437] ses 8:0:0:1: Attached scsi generic sg3 type 13
[ 1015.399052] sd 8:0:0:0: [sdb] No Caching mode page found
[ 1015.399060] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 1025.433185] sd 8:0:0:0: [sdb] Attached SCSI disk



```


Other things that I tried. 

e2fsck -f -b 32768 /dev/sdb
e2fsck -f -b 32768 /dev/sdb

```
e2fsck 1.43.4 (31-Jan-2017)
e2fsck: Bad magic number in super-block while trying to open /dev/sdb


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>



```


I feel like I'm up *hit creek without a paddle here. I don't know what else to do. I CANNOT reformat this drive because it has important data on it.

---

### Post by oldfred on 2017-05-21
Did you last open the NTFS partition with Windows 8 or later?
That probably left it with fast start up/hibernation on.
And best way to remove it is to use Windows.

Linux cannot do many Windows maintenance. And definitely cannot run chkdsk, which you will periodically need. Did you make a Windows repair disk? If you want to keep NTFS that is the minimum you must have.
The fsck is for ext4 formatted partitions only, it does not work on other Linux formats.

I have seen this, but only suggest it if you have good backups.
 Force removal of hiberfil from Ubuntu
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

This may let you see data in read only mode. Make sure not mounted elsewhere as you can have only one mount.
Force mount, read only (ro), change example with sda3 to your correct NTFS partition:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows

---

### Post by youbob1212 on 2017-05-21
Well no! I last used ubuntu 16.04, it worked fine, but now it's not working after reinstalling Ubuntu to the new 17 version and allowing it to fill up my 1tb hard drive. The only thing that is really different now is that I used encryption for my main hard drive, but that shouldn't really change anything. Damn! I hate it when things work fine for a minute then don't even start to work after a really big upgrade. 

I think my solution might be to get an image of Windows onto a VM and use it's HD tools.

---

### Post by oldfred on 2017-05-21
If only needed occasionally to run chkdsk, you can just use installer as repair console.

But if not using Windows, or connecting to Windows system, better not to use NTFS.

---

### Post by Yellow Pasque on 2017-05-21
> **youbob1212 said:**
> sudo mount /dev/sdb /mnt 

You're doing it wrong. It should be /dev/sdb**1** (or the number of whatever partition you're trying to use).

---

### Post by youbob1212 on 2017-05-21
mount: special device /dev/sdb1 does not exist

---

