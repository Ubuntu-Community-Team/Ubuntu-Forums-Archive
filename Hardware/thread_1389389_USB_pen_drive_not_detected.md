---
title: "USB pen drive not detected"
date: 2010-01-24
forum: Hardware
---

### Post by Hombal on 2010-01-24
I have a Transcend 2 GB hard disk. It is not getting detected after some days. It is getting detected by the lsusb command. Following is the output:

Bus 004 Device 004: ID 058f:1234 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Device 004 is the one.

The output dmseg | tail :

[ 2636.736935] usb 4-1: USB disconnect, address 3
[ 2646.450182] usb 4-2: new high speed USB device using ehci_hcd and address 4
[ 2646.584176] usb 4-2: configuration #1 chosen from 1 choice
[ 2646.606067] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2646.606941] usb-storage: device found at 4
[ 2646.606949] usb-storage: waiting for device to settle before scanning
[ 2647.256192] usb-storage: device scan complete
[ 2647.256934] scsi 6:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
[ 2647.260155] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 2647.260243] sd 6:0:0:0: Attached scsi generic sg2 type 0

But there is no drive detected. No pop-up.. :confused:
Any help is greatly appreciated :)

---

### Post by Hombal on 2010-01-25
Still no reply!!:confused::confused:

---

### Post by raktarok on 2010-02-01
Don't know if you have solved this, but what is the output of command sudo fdisk -l ?

---

### Post by Hombal on 2010-02-01
Here is the output.. No the problem is not solved yet :(

[FONT=Courier New]pramod@pramod-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d004cff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11170    89716298+   7  HPFS/NTFS
/dev/sda2           13781       14593     6530422+   7  HPFS/NTFS
/dev/sda3           11171       11294      996030   82  Linux swap / Solaris
/dev/sda4           11295       13780    19968795   83  Linux

Partition table entries are not in disk order[/FONT]

---

### Post by raktarok on 2010-02-01
fdisk is not detecting your drive. What about the output of this, after you plugin the drive?

```
ls /dev/sdb*

```

Also, can you see the drive in gparted partition manager? Look at the upper right corner to change the disks.
```
sudo apt-get install gparted
```

Also, have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1395515](http://ubuntuforums.org/showthread.php?t=1395515)

---

### Post by Hombal on 2010-02-02
When I enter ls /dev/sdb* I see the entry. But the same is not visible in gparted.

[FONT=Courier New]pramod@pramod-laptop:~$ ls /dev/sdb*
/dev/sdb
pramod@pramod-laptop:~$ sudo gparted
======================
libparted : 1.7.1
======================[/FONT]


But when the device is inserted I see some mention of sdb related entry. is there a problem with the device or ubuntu

---

### Post by raktarok on 2010-02-02
Ok, try this now:

sudo fdisk /dev/sdb

If all goes well, you should be dropped to a fdisk prompt. There, press p to view the partition table. Post the output here. 

If this does not work, try formatting the drive from a computer where it works. Then see if the pendrive is now detected in ubuntu.

Good luck!

---

### Post by eddier on 2010-02-02
Pop it into a windows system and reformat it to fat32.

I had the same problem and this did the trick--why Partition magic doesn't see it had me baffled also!

eddie

---

### Post by usererror on 2010-02-03
so what do we do if we don't have access to a windows computer?  I have to sansa mp3 players, both are the same model, and both play files just fine.

One will auto mount, the other does not.  

lsusb sees the device, but fdisk does not. any ideas?

---

### Post by rajeshgheware on 2010-08-15
I face the same issue. See below:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614351](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614351)
- Rajesh Gheware

---

