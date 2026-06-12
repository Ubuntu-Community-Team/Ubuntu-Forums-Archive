---
title: "Boot from USB"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by skalra63 on 2009-09-04
Hey guys, just wondering if you could help. 

I have used the live cd (9.04) to install Ubuntu. I have used the install program to install it to a 4GB USB flash drive (also tried it on an 8GB). I have it formatted to ext2. When I try to boot from the USB it runs through about 11 seconds of the boot but then hangs on the following:

sd 2:0:0:0: [sda] Attached SCSI removable disk
sd 2:0:0:0: Attcahed scsi generic sg1 type 0

After this it seems to hang and then it comes up with BusyBox.

Anyone with any ideas on what the issue could be?

---

### Post by skalra63 on 2009-09-04
Ok, an update on this. It appears that the USB installation actually works. I was using Virtual Box to test it. when booting directly from the usb from my laptop (not virtual machine), Ubuntu loads, which to me indicates that the issue is either VirtualBox or the USBCD ISO I made from the following web page [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB).

Anyone able to assist? Basically I am trying to help someone use their laptop with a failed ide connector on the motherboard (whole board will need to be replaced). I was hoping that they could use Ubuntu and boot from USB but their laptop does not support booting from USB....which is why i need this cd to work.

Any help would be greatly apprehciated.

---

### Post by skalra63 on 2009-09-05
Anyone able to help?

---

