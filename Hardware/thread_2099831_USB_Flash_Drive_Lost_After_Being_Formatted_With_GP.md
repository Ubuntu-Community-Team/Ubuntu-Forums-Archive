---
title: "USB Flash Drive Lost After Being Formatted With GParted"
date: 2012-12-30
forum: Hardware
---

### Post by BinPax on 2012-12-30
Hello Every body, and than you for reading my problem first, and thank you for trying to help me.

first i was just copying audio file into my 2G USB flash drive, then i had a problem saying that it cannot copy files into the drive any more, i tried removing it and trying again, but it didn't work. but the files already copied in the drive where working just fine and i was able to read them. but after the problem remaining i decided to format the drive using Disques, but somehow this didn't work. when i chose to format the drive, nothing happens and i get no error messages.
so i tried Gparted and it worked, i formatted the drive FAT32 but, after this, the drive doesn't show up, in Ubuntu, disques, windows or even GPArted. but the drive is still working because its a mp3 reader, when i try to use it just says that there are now files in it, ( because of formatting it off-course )

and this problem reminds me of another i had a month ago with a 320g drive, that i formatted it using a windows low level formatting tool. the formatting took me about 5 hours, but after it the drive doesn't show up on Ubuntu or windows.

So if there is anyway i can restore the flash drive first ( because its my friends, not mine ) or to restore my 320 hard drive
Thanks for helping :) 
any ideas will be very welcome ):P

---

### Post by ahallubuntu on 2012-12-30
To be clear: you created one large partition on your flash drive, with Gparted?  And then formatted it with FAT32?  Does it show up as /dev/sdb1 (assuming sdb is your flash drive)?

---

### Post by ivotkl on 2012-12-30
Ok, first of all: For the USB flash drive to be seen by Windows, it should have been formatted under fat32 or NTFS (if this last option is available).

Second thing, you said it did not allow you to remove it. Do you mean unmount / eject? If you hard removed it without safely removing drive, you might have done permanent damage to it. Some pendrives/USB sticks do not have safe remove option by default and you might break them .

Are you sure USB port is working? have you tried with something else? Please connect the device on same USB port and post the output of the following command:

```
lsusb
sudo parted -l
sudo fdisk -l
```

lsusb command should give you the output of the unused USB ports and the one in use by your stick should show you the HW specifications.
Here is mine:
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
```

Then, you should be able to see its "dev" name with this command:
```
sudo fdisk -l
```

Here is mine:
```
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x39113910

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS/exFAT
/dev/sda2        83891430   312576704   114342637+   f  W95 Ext'd (LBA)
/dev/sda5       100663353   310472189   104904418+   b  W95 FAT32
/dev/sda6        83891556   100663289     8385867   83  Linux
/dev/sda7       310472253   312576704     1052226   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8006 MB, 8006074368 bytes
13 heads, 13 sectors/track, 92525 cylinders, total 15636864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    15636863     7814400    c  W95 FAT32 (LBA)
```

Finally, sudo parted -l should show you if the USB stick full storage capability is recognized by your OS.
```
sudo parted -l
```
```
$ sudo parted -l
Model: ATA WDC WD1600AABS-6 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  43.0GB  43.0GB  primary   ntfs            boot
 2      43.0GB  160GB   117GB   extended                  lba
 6      43.0GB  51.5GB  8587MB  logical   ext4
 5      51.5GB  159GB   107GB   logical   fat32
 7      159GB   160GB   1077MB  logical   linux-swap(v1)


Model: Kingston DataTraveler 108 (scsi)
Disk /dev/sdb: 8006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  8006MB  8002MB  primary  fat32        boot, lba
```

_*Assuming you see the USB stick on the output of lusb:*_

Now, if you see your device connected on your lsusb output, you might need to create with root privileges a folder inside /media (change folder if it does not apply to your OS) named usb (for example) and then mount it with same privileges and give it 777 or 770 or 700 permission (7 stands for read, write and execute).

Codes would be, in this order:
```
sudo makedir /media/usb
sudo mount /dev/sdxx /media/usb
sudo chmod /dev/sdxx 777
```

On second and third line, both letters "x" should be replaced by the appropriate letter and number on your USB as shown on sudo fdisk -l command. For example, in my case it would be sdb1. /media/usb needs to be replaced with the folder you desire (it needs to be on /media or similar folder in your OS where mounted partitions show).

If you don't see your USB stick on lsusb, I think (I've been using Ubuntu only for 3 years and haven't dived into the depths of the command line yet) it is a hardware issue on the USB stick or on the port.

By the way, I still cannot unmount the usb stick after doing below solution. So, I have to shutdown the PC for safe removal.

Hope it helped you at least a bit. Please post output of above commands before doing anything (including steps under underlined title).

**Edit:** Please show me the output of:
[code]fsck /dev/sdxx[code]

Once again, replace "xx" with your correct device output on commands shown above.

I'm also thinking the boot sector could be broken, I believe it can be fixed with fsck.

---

### Post by BinPax on 2012-12-30
> **ahallubuntu said:**
> To be clear: you created one large partition on your flash drive, with Gparted?  And then formatted it with FAT32?  Does it show up as /dev/sdb1 (assuming sdb is your flash drive)?

noo it doesn't show up as dev/sdb1 !!

---

### Post by BinPax on 2012-12-30
> **ivotkl said:**
> Ok, first of all: For the USB flash drive to be seen by Windows, it should have been formatted under fat32 or NTFS (if this last option is available).

Second thing, you said it did not allow you to remove it. Do you mean unmount / eject? If you hard removed it without safely removing drive, you might have done permanent damage to it. Some pendrives/USB sticks do not have safe remove option by default and you might break them .

Are you sure USB port is working? have you tried with something else? Please connect the device on same USB port and post the output of the following command:

```
lsusb
sudo parted -l
sudo fdisk -l
```

lsusb command should give you the output of the unused USB ports and the one in use by your stick should show you the HW specifications.
Here is mine:
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
```

Then, you should be able to see its "dev" name with this command:
```
sudo fdisk -l
```

Here is mine:
```
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x39113910

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS/exFAT
/dev/sda2        83891430   312576704   114342637+   f  W95 Ext'd (LBA)
/dev/sda5       100663353   310472189   104904418+   b  W95 FAT32
/dev/sda6        83891556   100663289     8385867   83  Linux
/dev/sda7       310472253   312576704     1052226   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8006 MB, 8006074368 bytes
13 heads, 13 sectors/track, 92525 cylinders, total 15636864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    15636863     7814400    c  W95 FAT32 (LBA)
```

Finally, sudo parted -l should show you if the USB stick full storage capability is recognized by your OS.
```
sudo parted -l
```
```
$ sudo parted -l
Model: ATA WDC WD1600AABS-6 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  43.0GB  43.0GB  primary   ntfs            boot
 2      43.0GB  160GB   117GB   extended                  lba
 6      43.0GB  51.5GB  8587MB  logical   ext4
 5      51.5GB  159GB   107GB   logical   fat32
 7      159GB   160GB   1077MB  logical   linux-swap(v1)


Model: Kingston DataTraveler 108 (scsi)
Disk /dev/sdb: 8006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  8006MB  8002MB  primary  fat32        boot, lba
```

_*Assuming you see the USB stick on the output of lusb:*_

Now, if you see your device connected on your lsusb output, you might need to create with root privileges a folder inside /media (change folder if it does not apply to your OS) named usb (for example) and then mount it with same privileges and give it 777 or 770 or 700 permission (7 stands for read, write and execute).

Codes would be, in this order:
```
sudo makedir /media/usb
sudo mount /dev/sdxx /media/usb
sudo chmod /dev/sdxx 777
```

On second and third line, both letters "x" should be replaced by the appropriate letter and number on your USB as shown on sudo fdisk -l command. For example, in my case it would be sdb1. /media/usb needs to be replaced with the folder you desire (it needs to be on /media or similar folder in your OS where mounted partitions show).

If you don't see your USB stick on lsusb, I think (I've been using Ubuntu only for 3 years and haven't dived into the depths of the command line yet) it is a hardware issue on the USB stick or on the port.

By the way, I still cannot unmount the usb stick after doing below solution. So, I have to shutdown the PC for safe removal.

Hope it helped you at least a bit. Please post output of above commands before doing anything (including steps under underlined title).

**Edit:** Please show me the output of:
[code]fsck /dev/sdxx[code]

Once again, replace "xx" with your correct device output on commands shown above.

I'm also thinking the boot sector could be broken, I believe it can be fixed with fsck.


heres the output of the commands :


lsusb 

Bus 001 Device 002: ID 0ac8:c33f Z-Star Microelectronics Corp. Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


sudo parted -l

Model: ATA TOSHIBA MK3265GS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  105GB  105GB   primary   ntfs            boot
 2      105GB   320GB  215GB   extended                  lba
 6      105GB   159GB  53.7GB  logical   ext4
 7      159GB   161GB  2147MB  logical   linux-swap(v1)
 5      161GB   320GB  159GB   logical   ntfs

sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbcf3b704

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   204796619   102398278+   7  HPFS/NTFS/exFAT
/dev/sda2       204799998   625121279   210160641    f  W95 Ext'd (LBA)
/dev/sda5       313856000   625121279   155632640    7  HPFS/NTFS/exFAT
/dev/sda6       204800000   309657599    52428800   83  Linux
/dev/sda7       309659648   313853951     2097152   82  Linux swap / Solaris

Partition table entries are not in disk order


fsck /dev/sdxx


fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
fsck.ext2: No such file or directory while trying to open /dev/sdxx
Possibly non-existent device?

i am new to linux so i didn't understand much in the commands.

---

### Post by ivotkl on 2012-12-30
Don't worry about fsck. It checks filesystems for errors.

However, in this case, lsusb does not show USB device. Can you post the output of lsusb after connecting the pendrive on a different USB slot. Can yoyu check if that slot works by plugin in your webcam? (Assuming it works).

By the way, it would be a bit easier to recognise the output codes if you use BBcode command called "code" between [ ] at the beginning and between [/ ] at the end.

---

