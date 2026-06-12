---
title: "Help recovering data from an USB stick"
date: 2022-03-22
forum: Hardware
---

### Post by felipe-vfs on 2022-03-22
Hello, everyone.

In the past past few days, my USB stick files disappeared. What confuses me is that both the "Files" program and GParted says that the storage is still being occupied, but I can't access seem to find a way to get to them.

USB Stick properties, as seen on "Files": [https://i.imgur.com/cMLhY8Z.png](https://i.imgur.com/cMLhY8Z.png)
GParted information: [https://i.imgur.com/zF9abYN.png](https://i.imgur.com/zF9abYN.png)

I've tried checking the USB with fdisk, and the information is discrepant from GParted:
[HTML]
Disk /dev/sdb: 29.78 GiB, 31954305024 bytes, 62410752 sectors
Disk model: Rainbow Line    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5a718157
[/HTML]
[IMG]https://imgur.com/a/HV7dTHe[/IMG]

I've tried using dmesg to get some more information and here's what I found out about the USB:

[HTML]
[ 8397.723841] usb 1-3: new high-speed USB device number 23 using xhci_hcd
[ 8397.880234] usb 1-3: New USB device found, idVendor=058f, idProduct=6387, bcdDevice= 1.00
[ 8397.880247] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 8397.880250] usb 1-3: Product: Intenso Rainbow Line
[ 8397.880253] usb 1-3: Manufacturer: Alcor
[ 8397.880256] usb 1-3: SerialNumber: 12345678
[ 8397.882701] usb-storage 1-3:1.0: USB Mass Storage device detected
[ 8397.885327] scsi host2: usb-storage 1-3:1.0
[ 8398.895952] scsi 2:0:0:0: Direct-Access     Intenso  Rainbow Line     8.07 PQ: 0 ANSI: 4
[ 8398.897086] sd 2:0:0:0: [sdb] 62410752 512-byte logical blocks: (32.0 GB/29.8 GiB)
[ 8398.897768] sd 2:0:0:0: [sdb] Write Protect is off
[ 8398.897772] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 8398.898437] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 8398.899370] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 8398.922007]  sdb: sdb1
[ 8398.935868] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 8399.919818] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[/HTML]

Does anyone have any suggestions as how I should recover this data? I've tried using testdisk to create an img of it, but mounting it didn't work either. Any help would be appreciated, this data is really important to me.
[IMG]https://imgur.com/a/HV7dTHe[/IMG]

---

### Post by Autodave on 2022-03-22
The only thing that I have EVER had that helped me was to refrigerate the drive....even freeze it in the freezer.  When good and cold, pull it out and immediately into the PC.  Have a means ready to copy the data should it be available.  IF this works, it will quickly stop as the drive warms up.

This is a looooong shot.....but I did have it work one time.

---

### Post by guiverc on 2022-03-22
> **felipe-vfs said:**
> What confuses me is that both the "Files" program and GParted says that the storage is still being occupied, but I can't access seem to find a way to get to them.


What you're seeing with those sort of enquiries is just *metadata *about the data, ie. details from the partition table or directories, which will be stored in a different location to where the actual data is stored. You'll get the same response if there is actual data there, or no data still exists as they're showing only what *should be there*, not what is there (*ie. showing results with the assumption that  no logical or physical errors/problems exist*).

---

### Post by tea for one on 2022-03-23
```
[ 8399.919818] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
```
Did you try to run fsck?

---

### Post by rsteinmetz70112 on 2022-03-25
Is it a fat file system? If so you may want to try Windows and run chkdsk.

---

### Post by felipe-vfs on 2022-04-14
Hello, everyone. Sorry for the delay, I didn't have the to check the USB.

As suggested in the dmesg log, I tried running the fsck as the following:

[IMG]https://i.imgur.com/6Fjfk4U.png[/IMG]
[IMG]https://imgur.com/6Fjfk4U[/IMG]

[IMG]https://imgur.com/6C13OFx[/IMG]
I cancelled the operation, unmounted the driver, but got the same error message. After some googling, I found some suggestions that I should try running fsck using the -a flag. And so I did:

[IMG]https://i.imgur.com/6C13OFx.png[/IMG]
[IMG]https://imgur.com/6C13OFx[/IMG]

It's been sitting like this for something like two hours. The laptop it's running on isn't the fatest, but I feel it's taking too long. Is that normal? If not, is it safe to cancel the operation and maybe try to start it in a different way? I'm desperate thinking these memories of my wife and I might have beenn lost. :-(

I've made an image using testdisk and was able to recover a few things, but most of them are in strange folders named in a strange way, making it quite hard to search through them. I would like to return the drive to its original functionality. Any help would be greatly appreciated.

---

