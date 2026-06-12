---
title: "USB Hard Drive problem"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by gw90se on 2005-03-28
I know this has been addressed before, but I was unable to locate a solution.

My usb external hard drive won't show up. My usb pen drive and usb compact flash do. Below is the message log from when I plug in the usb hard drive. Any ideas wher I can start? FYI, I did load Hoary, briefly and it showed back up, but when I went back to Warty it doesn't. I sure would like this to work, since I use it for back-ups.

I did notice where it keeps calling it a SCSI device, but's it's a 60GB IDE drive in an external bay.

```
Mar 28 18:21:59 localhost kernel: usb 1-2.4: new full speed USB device using address 10
Mar 28 18:21:59 localhost kernel: usb 1-2.4: not running at top speed; connect to a high speed hub
Mar 28 18:21:59 localhost kernel: scsi7 : SCSI emulation for USB Mass Storage devices
Mar 28 18:21:59 localhost kernel:   Vendor: Genesys   Model: USB to IDE Disk   Rev: 0033
Mar 28 18:21:59 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Mar 28 18:21:59 localhost kernel: SCSI device sda: 117231408 512-byte hdwr sectors (60022 MB)
Mar 28 18:22:00 localhost kernel: sda: test WP failed, assume Write Enabled
Mar 28 18:22:00 localhost kernel:  /dev/scsi/host7/bus0/target0/lun0: p1
Mar 28 18:22:00 localhost kernel: Attached scsi removable disk sda at scsi7, channel 0, id 0, lun 0
Mar 28 18:22:00 localhost scsi.agent[6384]: disk at /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2.4/1-2.4:1.0/host7/7:0:0:0
Mar 28 18:22:04 localhost kernel: VFS: Can't find a valid FAT filesystem on dev sda1.
Mar 28 18:22:04 localhost kernel: UDF-fs: No VRS found
Mar 28 18:22:04 localhost kernel: Unable to identify CD-ROM format.
Mar 28 18:22:04 localhost kernel: HFS+-fs: unable to find HFS+ superblock
Mar 28 18:22:04 localhost kernel: VFS: Can't find a HFS filesystem on dev sda1.
Mar 28 18:22:04 localhost kernel: VFS: Can't find ext2 filesystem on dev sda1.
Mar 28 18:22:04 localhost kernel: ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1
Mar 28 18:22:04 localhost kernel: XFS: bad magic number
Mar 28 18:22:04 localhost kernel: XFS: SB validate failed
```

---

### Post by mercurus on 2005-03-28
Hi

The kernel recognises IDE devices connected through USB ports as SCSI (for hotplug support ??). It looks to me from the log as though the device has been recognised, and Ubuntu has even tried to mount the device with a variety of filesystems unsuccessfully.

Is there a filesystem on the HDD yet ? If so, which one ?
If you need to create one you could use sudo fdisk /dev/sda1 and then format each partition according to your needs. Otherwise, if there is a valid filesystem on there, you'll have to edit /etc/fstab to make sure it is attempting to mount the correct type of filesystem, with the appropriate options.

Cheers
mercurus

---

### Post by gw90se on 2005-03-29
I origionally formated this hard drive from Windows, where I started using it as a back up drive. (It's a 60GB hard drive) As I said in the origional post. I had briefly loaded Hoary, and it showed right up on the desktop as soon as it was plugged in. I was able to see contents, too. I dropped Hoary and went back to Warty because of a couple of problems that I was also having in Hoary. I'll wait for the final release then try that again.

---

### Post by lorap on 2005-03-30
first of all try to mount it in this way:
i.create a directory,say "usb" in your home directory:
sudo mkdir /home/YourUserName/usb
ii.mount it this way(if you use warty):
sudo mount /dev/sr0 /home/YourUserName/usb -t vfat -o umask=000
p.s.:
if you're running hoary,i think you should change sr0 to sda0,but i'm not sure.
to be sure open /dev directory and then plug in/out the usb-hard drive to see what drives appear/disappear.
have a nice day!
pavel.

---

