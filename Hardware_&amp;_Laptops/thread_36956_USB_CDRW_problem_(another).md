---
title: "USB CDRW problem (another)"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by makisupa123 on 2005-05-25
I've migrated my laptop over to Hoary from W2k.  Everything is going pretty well considering I'm a complete linux newb (using ndiswrapper to get my nic working was "interesting" but rewarding).  Here current problem -- a fairly generic ATAPI cdRW drive.  It worked, once (with k3b), but I don't know why Ubuntu refused to mount it -- automatically or manually.  Running K3b showed me what /dev it was assigned (scd0).  I added the relevant entry into my fstab:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
#/dev/sr0       /media/cdrecorder   udf,iso9660 rw,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/scd0       /media/cdrecorder   udf,iso9660 rw,user,noauto  0       0

I commented out the /dev/sro line for testing.  That is where I thought it should be.  the following is (what I think) the relevent portion from Dmesg:

uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using uhci_hcd and address 2
usb 1-1: unable to read config index 0 descriptor/start
usb 1-1: can't read configurations, error -75
usb 1-1: new full speed USB device using uhci_hcd and address 3
usb 1-1: unable to read config index 0 descriptor/start
usb 1-1: can't read configurations, error -75

I want this to work so badly...this is the last thing that needs to work before I can completely rid M$ from my life.  PLEASE HELP!!

Thanks in advance,

Mak

---

