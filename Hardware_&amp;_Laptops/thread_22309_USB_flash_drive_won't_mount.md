---
title: "USB flash drive won't mount"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by drummer on 2005-03-26
Hi all, i'm having problems mounting my usb flash drive. I have added it to fstab:
```
/dev/sdb     /media/thumb     auto     rw,users,noauto     0     0
```but when i try to mount, it says /dev/sdb does not exist. This is true (i checked in /dev) but it's been there on other installs of linux (Hoary array6, warty, debian..).

Where else can i mount the drive to or how can i get sdb into /dev?

I also get this output in dmesg when the drive is plugged in:
```
ehci_hcd 0000:00:02.2: port 1 reset error -110
hub 3-0:1.0: hub_port_status failed (err = -32)
```
Thanks and Happy Easter

---

### Post by soul_rebel on 2005-03-29
Have you tryed just plugging the drive in when the boot has finished?

do you have another scsi disk? sdb comes after sda, so if you don't have another scsi disk the usb drive will show as sda.

---

### Post by drummer on 2005-03-29
[QUOTE=soul_rebel]Have you tryed just plugging the drive in when the boot has finished?

do you have another scsi disk? sdb comes after sda, so if you don't have another scsi disk the usb drive will show as sda.[/QUOTE]
 yes, i tried all that.. and my sata showed as sda, which all worked fine, i just didn't know where sdb had gone. I've reinstalled though now with the 32 bit rather than the 64 bit hoary and all is working sweetly.. 

Thanks very much for your reply though.

---

### Post by Plank117 on 2005-03-29
I have had this same problem, I added a usb drive to fstab in the same manner that
drummer did, and when I tried to mount the thing I got a message stating that /dev/sda does not exist. What gives? Don't get me wrong, I've just started using linux and so far its been nothing but positive except for this. I'm using hoary 5.04 on an Averatec C3500. Have I done something wrong here, have I sinned against god, or is it foreigners?

---

### Post by Whiffle on 2005-03-29
I didn't add anything to my fstab to get my nikon camera to work.  I just plug it in, and gnome-volume-manager takes care of the rest.  It pops up on the desktop and nautilus as sda.  

any output in dmesg, Plank?

---

### Post by chz on 2005-03-29
in the warty release my thumbdrive popped out as sdb as well...but for sum reason now when i stick it in it's titled as the thumbdrive name...(ie "/media/LEXAR MEDIA"). maybe something happened with your kernel compile? i had an issue with this too before, but i reinstalled warty, then upgraded to hoary, and everything worked after that (had sound, printer, application problems installing from the hoary-preview cd.) so unless this is a fresh install of hoary you have, maybe reinstalling would maybe benefit. if you've been upgrading for awhile and have the system the way you like it, then hopefully somebody out there has a solution.

---

### Post by Plank117 on 2005-03-30
I haven't checked dmesg, or heard of it, where is it? I've checked in /etc and in /dev, and I was unable to locate this "dmesg." However, I figured out what the problem with the "/dev/sda cannot be found" message was. I added sda to fstab as /sda instead of /dev/sda, I changed the mount point to /media/thumb like drummer did, but all this did is further enlighten me of the extent of this problem. Whenever I try to mount my flash drive I get the message "/media/thumb does not exist," which only leads to the conclusion that ubuntu can't even see my usb ports. I checked in the device manager and it saw my usb controllers but I still have this problem. I checked in /proc/bus/usb and there is nothing there. Can someone help me out? I just set up a dual boot on my computer and I would really like to get going with ubuntu becuase so far it has gone great.

---

### Post by soul_rebel on 2005-03-31
dmesg is just a command that prints out kernel messages. Plug the drive and after a while type dmesg in a xterm, you will get some info, and you will know how the drive is called (maybe your sata controller has 2 channels, so it uses sda and sdb, than usb drive is sdc).

---

### Post by drummer on 2005-03-31
[QUOTE=Plank117]I haven't checked dmesg, or heard of it, where is it? I've checked in /etc and in /dev, and I was unable to locate this "dmesg." However, I figured out what the problem with the "/dev/sda cannot be found" message was. I added sda to fstab as /sda instead of /dev/sda, I changed the mount point to /media/thumb like drummer did, but all this did is further enlighten me of the extent of this problem. Whenever I try to mount my flash drive I get the message "/media/thumb does not exist," which only leads to the conclusion that ubuntu can't even see my usb ports. I checked in the device manager and it saw my usb controllers but I still have this problem. I checked in /proc/bus/usb and there is nothing there. Can someone help me out? I just set up a dual boot on my computer and I would really like to get going with ubuntu becuase so far it has gone great.[/QUOTE]
 Plank117, /media/thumb is a folder i created..
```
sudo mkdir /media/thumb
``` but after my reinstall usb drives automounted like they should. another problem [here](http://ubuntuforums.org/showthread.php?t=21465) may or may not be related.. if so, hopefully it'll be fixed in the final release of hoary next week.

---

### Post by kaltsi on 2005-04-01
I used the acpi=off in the kernel line and I had this problem. I don't use this option and  my USB flash drive is mounted automatically when I plug in it. But my computer doesn't turn off when I shut down it.

---

### Post by darkoptix on 2005-04-02
umm, this may sound stupid, but try to format the disk, that fixed my problem of mounting issues. However those errors don't sound like a partition problem. 

Are you sure the usb ports are working correctly?
Maybe test them out with some other devices...

---

### Post by mckemie on 2005-09-18
It looks like this problem may not have been resolved?

I have the same problem:
Jump drive does not automount and device /dev/sda1 does not exist.

I poked around and found sda1 under /.dev.  I know not why.  But, the jump drive does mount using that device. Can someone explain this situation to me?

---

### Post by TheAreopagite on 2005-09-20
](*,) I'm having a similar problem. When I try to mount my usb flash drive, I get the error message 'can't read superblock'.

I've read the USB flash memory HOWTO. The usb port is working fine. When I plug the stick in it is immediately picked up and appears in /dev as sda and sda1. The stick itself works fine in a laptop running windows. I've run out of ideas. Any suggestions gratefully received.

If it helps, I have this in /proc/bus/usb/devices:

:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 13 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0ea0 ProdID=6828 Rev= 1.10
S:  Manufacturer=USB     
S:  Product=Flash Disk      
S:  SerialNumber=70417CD640E0071B
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

and this in /proc/scsi/scsi:

Attached devices:
Host: scsi13 Channel: 00 Id: 00 Lun: 00
  Vendor: OTi      Model: UStorage         Rev: 1.89
  Type:   Direct-Access                    ANSI SCSI revision: 02

---

### Post by mckemie on 2005-09-20
I'm not sure, but I think "superblocks" may be associated with filesystems other than vfat and your flash memory is likely vfat.  Are you attempting to mount a vfat filesystem or something else?

---

### Post by TheAreopagite on 2005-09-21
<Mckemie wrote: I'm not sure, but I think "superblocks" may be associated with filesystems other than vfat and your flash memory is likely vfat. Are you attempting to mount a vfat filesystem or something else?>
 
The stick is certainly vfat, and as it's used for my wife to transfer documents between her windows box at work and my linux box at home, it needs to stay that way.
 
All I know about superblocks is what is written in the MAN page for mount:
[size=2][/size] 
[size=2]*If no -t option is given, or if the auto type is specified, the superblock is probed for the filesystem type (adfs, bfs, cramfs, ext, ext2, ext3, hfs, hpfs, iso9660, jfs, minix, ntfs, qnx4, reiserfs, romfs, udf, ufs, xfs, xfs, xiafs are supported). If this probe fails, mount will try to read the file /etc/filesystems, or, if that does not exist, /proc/filesystems. All of the filesystem types listed there will be tried, except for those that are labeled "nodev" (e.g., devpts, roc and nfs). If /etc/filesystems ends in a line with a single * only, mount will read /proc/filesystems afterwards.*[/size]
[size=2][/size] 
[size=2]I don't have /etc/filesystems, but I do have /proc/filesystems and it does list vfat, so I can't see why the stick won't mount. I did specify the filesystem type with the -t option, so mount shouldn't need to probe the superblock, and if did try to probe it and fail, then it should be successful once it has tried all the filesystem types in /proc/filesystems.[/size]
[size=2][/size] 
[size=2]Incidentally, device manager is able to identify the stick as vfat (fat12) and even read the size. I don't know much about windows filesystems (or linux ones either!) but I thought vfat was also called fat32, not fat12. Could that be where the problem lies?
[/size]

---

### Post by Paulo Wageck on 2005-09-23
google about "unusual_devs.h", EFI partition support in Kernel (must disable), recompiling kernel, and so... 

I still coudnt get my usb sd card reader working....

cheers

drpaulo.com

---

### Post by TheAreopagite on 2005-10-02
:D  Whatever it was, installing breezy fixed it. USB now works fine.

---

