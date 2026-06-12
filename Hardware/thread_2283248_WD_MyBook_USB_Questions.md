---
title: "WD MyBook USB Questions"
date: 2015-06-20
forum: Hardware
---

### Post by bilkay on 2015-06-20
I have a WB MyBook 1TB SATA/USB external drive that I have been using on my Scientific Atlanta cable DVR connected via SATA. Researching the drive before I bought it, I read in one of the reviews that the SA box formatted the drive as Linux ext. I disconnected the drive from the cable box and tried to connect via usb to my laptop. It did not mount and got the following in /var/log/syslog (I'm not sure what's relevant):

```
Jun 20 07:29:12 Laptop kernel: [ 5652.900071] usb 2-1: new high-speed USB device number 4 using ehci_hcd
Jun 20 07:29:12 Laptop kernel: [ 5653.034155] scsi9 : usb-storage 2-1:1.0
Jun 20 07:29:12 Laptop mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1"
Jun 20 07:29:12 Laptop mtp-probe: bus: 2, device: 4 was not an MTP device
Jun 20 07:29:13 Laptop kernel: [ 5654.032925] scsi 9:0:0:0: Direct-Access     WD       My Book AV 1020  1010 PQ: 0 ANSI: 4
Jun 20 07:29:13 Laptop kernel: [ 5654.035438] sd 9:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jun 20 07:29:13 Laptop kernel: [ 5654.035762] sd 9:0:0:0: Attached scsi generic sg2 type 0
Jun 20 07:29:13 Laptop kernel: [ 5654.036032] sd 9:0:0:0: [sdb] Write Protect is off
Jun 20 07:29:13 Laptop kernel: [ 5654.036039] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
Jun 20 07:29:13 Laptop kernel: [ 5654.037514] sd 9:0:0:0: [sdb] No Caching mode page found
Jun 20 07:29:13 Laptop kernel: [ 5654.037522] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun 20 07:29:13 Laptop kernel: [ 5654.040469] sd 9:0:0:0: [sdb] No Caching mode page found
Jun 20 07:29:13 Laptop kernel: [ 5654.040477] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun 20 07:29:13 Laptop kernel: [ 5654.050689]  sdb: unknown partition table
Jun 20 07:29:13 Laptop kernel: [ 5654.052997] sd 9:0:0:0: [sdb] No Caching mode page found
Jun 20 07:29:13 Laptop kernel: [ 5654.053005] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Jun 20 07:29:13 Laptop kernel: [ 5654.053011] sd 9:0:0:0: [sdb] Attached SCSI disk
```

Questions:

1. To format the drive, what device do I use?
2. If I format it, will I be able to use it later with the cable box?

If anyone's had experience with this situation, I'd really appreciate the help.

---

### Post by sudodus on 2015-06-20
0. Decide how you want the drive formatted! How are you going to use it? With Windows, Linux, MacOS, one or two or all of them? Will you only store data, or do you want to boot from it?

1. It is probably straight-forward to create new partition(s) and file system(s) with ***gparted***. Boot from an Ubuntu install DVD/USB drive, and select it gparted from dash. It is also possible to install gparted into an installed Ubuntu system.

If you cannot identify the MyBook drive from gparted, you can run the following command from a terminal window:

```
sudo lsblk -fm
```

(Make the window wide to see the output better.)

---

### Post by bilkay on 2015-06-20
I ran: 

```
$ sudo fdisk /dev/sdb
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xf7545b04.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): p

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf7545b04

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): 
```

It looks like the person who said SA formats as Linux ext was blowing smoke.

---

### Post by sudodus on 2015-06-20
But fdisk is an old program. parted and lsblk might find things that fdisk cannot find. On the other hand, if you want to format it, you can use gparted directly, as long as the device is recognized (and this is the case). Or must you run in command line mode?

Do you know how you want to format the drive: to create a partition table, create partition(s) and file system(s)? In that case, just go ahead. Otherwise please describe what you want, and you will get relevant advice :-)

---

### Post by bilkay on 2015-06-20
I'm really more interested in question #2. I've found that /dev/sdb gets me to the disk where I can partition it, format, etc. I don't need the disk on to be on the cable box right now, but I might in the future, and I'd rather not do something irreversible. I was hoping on the off-chance that someone had already tried the same thing. If not, I'll just go ahead and maybe help someone in the future.

I find it very strange that the disk has no partition yet the cable box could read it and write to it. When I first installed it, the cable box went through a format procedure, so if I can get it back to the out-of-the-box (unformatted) condition, the cable box should be able to handle it. Any thoughts on that?

---

### Post by sudodus on 2015-06-20
I think there is a format, maybe a very special format created for the cable box, maybe a newer format or disk mapping, that is not recognized by fdisk (because fdisk is old, and not updated for all new partition tables, maps and file systems.

If it could be formatted by the cable box company's tool when it was new, it is very likely that it can be done again (but I cannot be 100% sure). So if it were my disk, I would re-partition and re-format it and use it for linux. Other people might re-format it for Windows. And if I would like to use it again for the cable box, I would re-format it with that company's tool.

Edit: And it is possible to remove all traces of formatting, for example overwriting with zeros at a low level. See this link

[https://help.ubuntu.com/community/mkusb#Wipe_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_whole_device)

---

### Post by bilkay on 2015-06-24
Update: I created one partition (sdb1) on the drive and formatted it ext4. All is well. Then I re-connected it to the cable box and rebooted that. It asked to format the disk and I allowed it. Available recording space indicated it was seeing the added disk. Then I shut down the cable box, re-connected the disk to the PC and ran fdisk. It showed that the partition I had added was no longer there. With fdisk, I again created one partition (sdb1) and then reformatted ext4. Everything seems OK to this point. The only real change I could see was the blkid changed.

One curiosity is that while I had the disk on the cable box, I made a short recording. With the disk removed, the recording was still there and playable. The cable manual says recordings should go onto the disk with the most available space. That one didn't seem to but I'm not going to investigate that further.

---

