---
title: "Kingston 32GB USB Drive NTFS not working"
date: 2014-09-23
forum: Hardware
---

### Post by rzvann-u on 2014-09-23
Hello. 
First of all, I am a newbie here, so please excuse all my difficulties. 
Second, I have a Kingston 32GB DTSE9 USB Drive which is now in a manner of speaking broken. 
It's story: I tried to put on it Evolve OS with dd command. It manage to copy the iso on drive, in terminal all showed ok. When I tried to boot from drive, it gave me the error "Check machine state" and after that, it rebooted. 
I saw I can't figure how to do it, I formated using Gparted back to its state, NTFS partition. It was ok. I put on it some files from a friend's Windows machine, I almost filled its space. I plugged it in my Gnome Ubuntu 14.04.1 laptop, started copying the files when at a moment the copying process stopped and the drive disappeared from Nautilus. From then, this is all complicated.  

When I plug it in, the notification sound plays.
It does not appear in Gparted nor in Nautilus.
In Disk Utilities it appears as GENERIC USB Mass Storage (1.00) and it shows NO MEDIUM. (screenshot)
In **fdsik -l** it doesn't appear 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

In **lsusb **I think it is **JMTek, LLC. Transcend Flash disk, **but since it is a Kingston drive, I am not sure.

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1bcf:2883 Sunplus Innovation Technology Inc. 
Bus 001 Device 005: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
**[COLOR=#ff0000]Bus 003 Device 007: ID 0c76:0005 JMTek, LLC. Transcend Flash disk[/COLOR]**
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**dmesg **give me this

[ 3741.344993] usb 3-1: new high-speed USB device number 7 using xhci_hcd
[ 3741.362195] usb 3-1: New USB device found, idVendor=0c76, idProduct=0005
[ 3741.362198] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 3741.362200] usb 3-1: Product: USB Mass Storage
[ 3741.362202] usb 3-1: Manufacturer: GENERIC 
[ 3741.362305] usb 3-1: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
[ 3741.362308] usb 3-1: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes
[ 3741.362484] usb-storage 3-1:1.0: USB Mass Storage device detected
[ 3741.362676] scsi9 : usb-storage 3-1:1.0
[ 3743.128257] scsi 9:0:0:0: Direct-Access     GENERIC  USB Mass Storage 1.00 PQ: 0 ANSI: 0 CCS
[ 3743.128671] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 3743.129459] sd 9:0:0:0: [sdb] Attached SCSI removable disk



The **ntfsck** /dev/sdb command doesn't revolve anything
Error opening partition device: No medium found

In Windows, Disk manager recognize the drive as F:, but without a partion. I am unable to format it or to open it. I tried all kind of partioning programs, but not a single one helped me.

So, I came here, hoping that someone would finally help me rescue the drive.

Thank you in advance.

---

### Post by sudodus on 2014-09-23
Welcome to the Ubuntu Forums :-)

A quick question before going into details: Is there anything you need to rescue from the pendrive, or can you start trying to make a good partition table and file system again?

---

### Post by rzvann-u on 2014-09-23
I guess by now everything is lost, so I do not care about the data. Luckily, I have a backup.  At the moment, all I want is the drive working fine, no matter how.

---

### Post by varunendra on 2014-09-23
I'll follow the thread with curiosity. Since in my experience, the "medium not found" type errors have so far been a dead-end to me - possible (my personal assumption, don't believe it!) indication of the storage chip or the circutry connecting to it being damaged or disconnected, in which case, it would be like a card reader without a memory card in it. :|

---

### Post by sudodus on 2014-09-23
Then I suggest that you try ***mkusb*** according to this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

It does suffer from bad partition tables or file systems, because it simply overwrites what is on the pendrive. mkusb uses ***dd*** under the hood, it actually 'only' makes the process safer, helps you avoid overwriting another drive by mistake.

I don't know if ***Evolve OS*** comes as a hybrid iso file.

mkusb works to install many operating systems by direct cloning / flashing / copying the iso file to the target device (pendrive). It requires that the iso file is a hybrid iso file. If it is not a hybrid file, you can make it hybrid with the commands (start with a copy if you want to keep the original file)

```
cp -p file.iso file-hybrid.iso
```

```
isohybrid file-hybrid.iso
```

which overwrites it the original file with the hybrid file.

---

### Post by sudodus on 2014-09-23
> **varunendra said:**
> I'll follow the thread with curiosity. Since in my experience, the "medium not found" type errors have so far been a dead-end to me - possible (my personal assumption, don't believe it!) indication of the storage chip or the circutry connecting to it being damaged or disconnected, in which case, it would be like a card reader without a memory card in it. :|

Yes, there is such a risk. Unfortunately pendrives are easily damaged beyond repair. I think we'll soon find out, but I hope it is only a 'software' damage, and suggest to try a few things before giving it up.

---

### Post by rzvann-u on 2014-09-23
Thank you for the reply.
mkusb shows me only the hard drive, my primary drive, so I have no luck to select the USB drive.
Any idea?

---

### Post by rzvann-u on 2014-09-23
I tried with Ubuntu Gnome 14.04.1 .iso, hoping that will make a usb installation  drive. But when I tried to select my USB device, it only showed the hard drive (sda).

---

### Post by sudodus on 2014-09-23
Some simple things to try:

- Have you tried all USB ports in the computer?
- Try after rebooting to connect the pendrive!
- Try in another computer, if the pendrive will show up (Windows, Linux, MacOS, whatever is available for you).

If still no go, I'm afraid [varunendra]("http://ubuntuforums.org/member.php?u=1043629") was right. The pendrive is dead.

---

### Post by rzvann-u on 2014-09-23
I reinstalled Ubuntu Gnome 14.04. Nothing changed. I tried all the usb ports. Rebooted over and over again. Nothing. But I found something quite interesting for me. The BIOS shows the usb device.

---

### Post by mastablasta on 2014-09-23
does it show up in windows? if so it could be a check disk needs to be run or it could also be that partition table is destroyed.

or it is faulty and should be confined to the bin.

---

### Post by rzvann-u on 2014-09-23
Right now, I can't find a windows machine. Is on the internet a rescue cd/something that can be written on cd/usb that has these tools?

---

### Post by sudodus on 2014-09-23
Be prepared that the pendrive might be dead ...

I don't know a high quality replacement tool for Windows ***chkdsk*** (check disk). If you cannot find a Windows computer (or in general, another computer), then wait until you find one, and test if the pendrive

- can be seen
- can be repaired

Some pendrives cooperate better with some computers and not so well with other computers. Sometimes a USB hub can solve the problem. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives
[/URL]

---

### Post by oldfred on 2014-09-23
When you used dd to copy an ISO to the flash drive that is not a standard partition table but an image.
Then when you formatted with NTFS did you create a partition table? Since random data is in partition table location that often can be difficult. 
And we have seen several cases even with 3TB drives where Windows formatted the drive, not creating any partition. That is then like a large floppy drive.
Linux then may see drive as a loop device, if it mounts it. But obviously shows no partition table.

Do either of these show anything?
sudo parted -l
sudo fdisk -lu

---

### Post by rzvann-u on 2014-09-23
I formatted using GParted, but I don't know for sure if I created a partition table. Sorry for the inconvenience. 
[B]
sudo parted -l[/B] outputted this

Model: ATA Hitachi HTS72757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End    Size    File system     Name  Flags
 1      1049kB  538MB  537MB   fat32                 boot
 2      538MB   742GB  742GB   ext4
 3      742GB   750GB  8000MB  linux-swap(v1)


and [B]sudo fdisk -lu

[/B]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.



So, I am not sure if this helps. But, I found in **mkusb **a command in* Help *menu which shows something.
**sudo ls -l /dev/disk/by-id**
total 0
lrwxrwxrwx 1 root root  9 sep 23 20:22 ata-Hitachi_HTS727575A9E364_J3740084J0K73E -> ../../sda
lrwxrwxrwx 1 root root 10 sep 23 18:38 ata-Hitachi_HTS727575A9E364_J3740084J0K73E-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 sep 23 18:38 ata-Hitachi_HTS727575A9E364_J3740084J0K73E-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 sep 23 18:38 ata-Hitachi_HTS727575A9E364_J3740084J0K73E-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 sep 23 18:38 ata-Slimtype_DVD_A_DS8A9SH_3208703_693242410473 -> ../../sr0
**lrwxrwxrwx 1 root root  9 sep 23 20:22 usb-GENERIC_USB_Mass_Storage-0:0 -> ../../sdb**
lrwxrwxrwx 1 root root  9 sep 23 18:38 usb-Kingston_DT_101_G2_00142238268CEA5136160000-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 sep 23 20:22 wwn-0x5000cca68cdc6faf -> ../../sda
lrwxrwxrwx 1 root root 10 sep 23 18:38 wwn-0x5000cca68cdc6faf-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 sep 23 18:38 wwn-0x5000cca68cdc6faf-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 sep 23 18:38 wwn-0x5000cca68cdc6faf-part3 -> ../../sda3

---

### Post by oldfred on 2014-09-23
Neither parted or fdisk command shows sdb, so it did not mount. But your ls command is showing the usb as sdb? And that shows no partitions. Not sure then if not partitioned or just error on mount in first place?

And it is normal for fdisk to not show gpt partitions correctly on sda.

---

### Post by rzvann-u on 2014-09-23
Indeed, my last **ls** shows the usb as sdb. Now I am confused.
I plugged in another linux machine (elementary OS) and I run the same commands. They show exactly the same things. So, I guess it is not partitioned.

---

### Post by oldfred on 2014-09-23
What does this show. It should end with 55 aa as the end of the MBR.

 sudo dd if=/dev/sda bs=512 count=1 | hexdump -C

```
000001b0  cd 10 ac 3c 00 75 f4 c3  51 fa 51 fa 00 00 [COLOR=#ff0000]80[/COLOR] 01  |...<.u..Q.Q.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 0c ce df 06 00 fe  |......?.........|
000001d0  ff ff 83 fe ff ff c1 e4  50 09 00 a6 50 09 00 00  |........P...P...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001f0  ff ff 0b fe ff ff 4b ce  df 06 76 16 71 02 [COLOR=#ff0000]55 aa[/COLOR]  |......K...v.q.U.|

```

The 80 at 01be says my sda1 is bootable. and the 55 aa at end show it is a MBR with correct end.

[http://thestarman.pcministry.com/asm/mbr/PartTables.htm#mbr](http://thestarman.pcministry.com/asm/mbr/PartTables.htm#mbr)

---

### Post by rzvann-u on 2014-09-23
[B]sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C 
[/B]returns something I saw before

dd: failed to open &#8216;/dev/sdb&#8217;: No medium found

Any suggestions?

---

### Post by oldfred on 2014-09-23
Your ls by id showed it. But it still then is not correctly shown in device listings?

But this did show two flash drives, both sdb?
> **lrwxrwxrwx 1 root root  9 sep 23 20:22 usb-GENERIC_USB_Mass_Storage-0:0 -> ../../sdb**
lrwxrwxrwx 1 root root  9 sep 23 18:38 usb-Kingston_DT_101_G2_00142238268CEA5136160000-0:0 -> ../../sdb


Does this show it?
 sudo blkid -c /dev/null -o list

---

### Post by rzvann-u on 2014-09-23
device                    fs_type    label       mount point                   UUID
--------------------------------------------------------------------------------------------------------------------
/dev/sda1                 vfat                   /boot/efi                     C011-07AD
/dev/sda2                 ext4                   /                             51853be7-0277-4765-adfe-c355cb174d5b
/dev/sda3                 swap                   <swap>                        6cf43950-debe-4656-82b0-de5bb7159bc8

The Generic USB is the broken one and the second one is another USB drive that I have, but the second one was unplugged when the command was given.

---

### Post by oldfred on 2014-09-23
Without getting it mounted so we can work with it, then it is not possible to do anything.
I would see if your Windows system that you orginally used will mount it and copy your data.

Then see if you can partition it with Windows.

---

### Post by rzvann-u on 2014-09-24
Thank you for your reply and for your interest. I will try today to plug into a Windows machine and try to see if it mounts.

---

### Post by sudodus on 2014-09-24
So

```
sudo ls -l /dev/disk/by-id
```

can find the pendrive as **/dev/sdb** but dd does not recognize it. Maybe if you try a disk repair tool, ***ddrescue*** with the option **-d** it might work.

Install it with

```
sudo apt-get install gddrescue
```

Read the info pages very carefully

```
info ddrescue
```

```

`-d'
`--direct'
     Use direct disc access to read the input file, bypassing the kernel
     cache. (Open the file with the O_DIRECT flag). Use it only on
     devices or partitions, not on regular files. Sector size must be
     correctly set for this to work. Not all systems support this.

     If your system does not support direct disc access, ddrescue will
     warn you. If the sector size is not correctly set, all reads will
     result in errors, and no data will be rescued.

```

and ***chapter 7. Direct Disc Access*** of the info pages.

If ddrescue works (can see and read/write to/from the pendrive as /dev/sdb, then I suggest that you overwrite the first megabyte (maybe more) and try again with gparted. ***Maybe*** something confusing can be removed that way and the pendrive will work again.

---

### Post by oldfred on 2014-09-24
You had both flash drives showing as sdb??
I might try one more time by unplugging it and replugging it.
Since you cannot correctly unmount it, just to be safe I might shut down system. And if you have trouble shutting down as it cannot umount it correctly use REISUB.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

