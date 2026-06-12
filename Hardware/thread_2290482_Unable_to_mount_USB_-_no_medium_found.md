---
title: "Unable to mount USB - no medium found"
date: 2015-08-12
forum: Hardware
---

### Post by Randyman99 on 2015-08-12
I have a new HP USB 3.0 128 GB thumbdrive. It came with some preinstalled stuff that would only run on Windows or Mac, so I went into XP and totally muffed it up so it's unreadable. Back in Xubuntu, it doesn't mount. I figure I could wipe it and start over, but can't get to that point. Gparted doesn't see it. I issue the following commands with results:

```
sudo blkid | grep sd
```

and it just displays my current installed hard drives (3) and partitions (24), which I won't bore you with here. The USB drive is not listed.

I unplug the USB drive and plug it in again, and issue the command:

```
dmesg

................
[  970.159524] usb 1-5: USB disconnect, device number 3
[ 1010.004110] usb 1-5: new high-speed USB device number 4 using ehci-pci
[ 1010.137252] usb 1-5: New USB device found, idVendor=03f0, idProduct=da07
[ 1010.137261] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1010.137264] usb 1-5: Product: x702w
[ 1010.137267] usb 1-5: Manufacturer: HP
[ 1010.137270] usb 1-5: SerialNumber: 2304501274
[ 1010.139410] usb-storage 1-5:1.0: USB Mass Storage device detected
[ 1010.139756] scsi7 : usb-storage 1-5:1.0
[ 1011.136677] scsi 7:0:0:0: Direct-Access     hp       NAND Flash       1.00 PQ: 0 ANSI: 6
[ 1011.139319] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 1011.145325] sd 7:0:0:0: [sdd] Attached SCSI removable disk

```

That tells me that the system recognizes the thumb drive, and attaches it as sdd. 
Okay, so lets say it doesn't have a partition on it, and I need to create one. As Gparted won't see it, maybe I can use fdisk. I issue the command:

```
sudo fdisk /dev/sddfdisk: unable to open /dev/sdd: No medium found

```

So fdisk doesn't see it. I can issue the command

```
ls -l /dev/sdd
brw-rw---- 1 root disk 8, 48 12.08.2015 09:13 /dev/sdd

```

So at some level the system is able to see the USB drive on /dev/sdd, but if fdisk won't see it, I don't know what to do.

---

### Post by ajgreeny on 2015-08-12
I have no idea what you mean by [COLOR="#0000FF"]"so I went into XP and totally muffed it up so it's unreadable."[/COLOR] but I wonder if you formatted it in XP, and whether XP is able to or defaults to creating dynamic partitions which are invisible to Linux.

Tell us a bit more if you can about what you have actually done to the disk, and what the "stuff" on it was before you did whatever it was.

---

### Post by Randyman99 on 2015-08-12
Thank you, ajgreeny, for your quick response. I was trying to save you from trudging through details that were not on message. The thumb drive would not read in the thumb drive originally in Ubuntu. Then I noticed on the package that it required Windows or Mac. I figured it had some security or other type of software that restricted access to the drive. I figured I could blast it away and reformat it. I rebooted into my antique version of XP, and sure enough, there it was. I used Avanquest Partition Commander, and was able to access the drive. I decided to delete the one FAT32 partition. I clicked accept, that action completed OK. Then I wanted to create one FAT32 partition of 20 GB, and an ext3 partition (Partition Commander didn't allow ext4 as a choice) of 50 GB, and leave the rest unformatted for now. Before I clicked accept, I changed my mind about some parameter on the ext4 partition. I wasn't able to change it, so I deleted it and then recreated it the way I wanted. I thought Partition Commander would remove the first creation and deletion from stack of actions to complete, but when I clicked accept, I saw that it was creating the FAT32, creating the ext4, deleting the ext4, and then recreating the ext4. Well, color me impatient, I didn't want to sit through all that, I let it finish creating the FAT32 partition, and then when it started on the first ext4 partition, I hit cancel, thinking I could redo it more quickly by recreating the ext4 partition by itself. I guess Partition Commander has some bugs in it, because then I couldn't read the drive at all in XP, Partition Commander or no. I also tried Partition Commander boot disk, but that wasn't able to see it either. I figured Ubuntu/Xubuntu might be able to save me, so I rebooted back into that. That's what got me to where I am now.

---

### Post by sudodus on 2015-08-13
> **Randyman99 said:**
> ... I can issue the command

```
ls -l /dev/sdd
brw-rw---- 1 root disk 8, 48 12.08.2015 09:13 /dev/sdd

```

So at some level the system is able to see the USB drive on /dev/sdd, but if fdisk won't see it, I don't know what to do.

When ***ls*** can see the thumbdrive, I think ***mkusb*** can see it too, and if you let it wipe the first megabyte, the bad things confusing gparted and other tools should be gone. See this link

[mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

After that it should work to create partitions with gparted.

---

### Post by Randyman99 on 2015-08-13
Thank you, Sudodus, That looks like a good thing to try. I tried plugging the USB into another computer, and the ls command didn't work there. I plugged it back into the first computer again, and now wasn't able to detect it their either. I figured I had a faulty USB, and as it was less than a week old, I took it back to the store, and exchanged it for another of the same make and model. With this new one, Gparted was able to read it just fine. I was able to delete the factory partition and create one of my own, and am able to write to it now just fine.

I like your suggestion, though, and think it would have allowed me to recover, if in fact the problem with the USB had been strictly software. It's possible I might have had a bad first sector from the get-go, but I don't know that it wasn't a hardware problem, either, perhaps a loose connection inside the USB. I will bookmark this page for reference in case I need to recover a USB in the future, and mark this thread as solved.

---

### Post by sudodus on 2015-08-13
I'm glad you found a solution :-)

Yes, that it seems to be a hardware problem or a problem with software 'behind or below' what we can touch with our tools.

---

