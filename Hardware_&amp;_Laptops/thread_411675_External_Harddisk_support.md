---
title: "External Harddisk support"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by Nickosss on 2007-04-17
Help me please...

I'm running Xubuntu 6.10 Edgy since yesterday.
I'm gonna use this computer only for music (I'm a DJ in my spare time).

My problem is that all my music is on an external harddisk. I would like to copie the music
to my internal harddisk, but xubuntu doesn't recognize my harddisk...

when I connect it to my PC it starts to run but it isn't getting on speed.

How can I make my harddisk compatible????

- extra info
   - my external harddisk is from my old dell laptop
   - when i connect it to windows and i look it up in my device manager it is named: HTS54802 0M9AT00 USB Device

---

### Post by kidders on 2007-04-17
Hi there and welcome,

Perhaps if I describe what's *meant* to happen, that might help you identify what's going wrong for you.

_**dmesg**_
Take a look at the output of **dmesg**, before and after plugging in your device. You should see something like the following get added to the output...

```
usb 2-7: new high speed USB device using ehci_hcd and address 5
usb 2-7: configuration #1 chosen from 1 choice
Initializing USB Mass Storage driver...
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 4:0:0:0: Direct-Access     USB 2.0  MobileDisk N4HY  1.00 PQ: 0 ANSI: 2
SCSI device sdc: 253952 512-byte hdwr sectors (130 MB)
sdc: Write Protect is off
sdc: Mode Sense: 03 00 00 00
sdc: assuming drive cache: write through
SCSI device sdc: 253952 512-byte hdwr sectors (130 MB)
sdc: Write Protect is off
sdc: Mode Sense: 03 00 00 00
sdc: assuming drive cache: write through
sdc: sdc1 sdc2
sd 4:0:0:0: Attached scsi removable disk sdc
```This example describes the addition of a new storage device (called /dev/sdc) with two disk partitions (called /dev/sdc1 and /dev/sdc2).

_**The /dev filesystem**_
Now that you know where to look, you can check that everything is okay.
```
kidders@x2:~$ ls -l /dev/sdc*
brw-rw---- 1 root plugdev 8, 32 2007-04-17 14:44 /dev/sdc
brw-rw---- 1 root plugdev 8, 33 2007-04-17 14:44 /dev/sdc1
brw-rw---- 1 root plugdev 8, 34 2007-04-17 14:44 /dev/sdc2
kidders@x2:~$ groups
kidders adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin
```[LIST]
[*]The 'b' in "brw-rw----" means that the new devices are "block" devices, which is sensible.
[*]The second "rw" means that, provided I am a member of the user group called "plugdev", I have read/write access to the new devices. (Only of limited importance.)
[*]The output of the **groups** command shows that I am.[/LIST]_**Mounting filesystems**_
Now, you can check whether Xubuntu automatically mounted any filesystems for you.
```
kidders@x2:~$ mount | grep sdc
/dev/sdc2 on /media/UID type hfsplus (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/STUFF type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
```This means that two filesystems were recognised ... a HFS+ (Apple) one and a FAT (Microsoft) one ... and it shows how to access them.

If no filesystems were mounted for you, you may have automatic mounting switched off, or there may be a problem. To check, you can try mounting it/them manually.

```
sudo mkdir /media/usbdisk
sudo mount /dev/sdc1 !$
```If all goes well, there should be no output from either command, Xubuntu should automatically detect your filesystem type, and it should now be accessible at /media/usbdisk.


If you try working through my example, and post your results, that should help identify what sort of problem you're having. Unless there is something very strange about your USB disk, it really should work!

---

