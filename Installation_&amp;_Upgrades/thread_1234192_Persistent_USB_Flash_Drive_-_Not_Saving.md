---
title: "Persistent USB Flash Drive - Not Saving"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by zebraneo on 2009-08-07
I am trying to create a Persistent USB Flash drive - flash drive 8GB, and it's not saving the information. Can someone tell me what I did wrong.



default persist
label persist
  menu label ^Run Ubuntu Persistently saving changes back to USB
 kernel /casper/vmlinuz
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

label live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

label live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
  append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
label check
  menu label ^Check disc for defects
  kernel /casper/vmlinuz
  append  noprompt boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80

---

### Post by Mighty_Joe on 2009-08-07
Why don't you use the Live CD USB Creator?  It's way easier than rolling your own.  
[Here's another option]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/")
[This post]("http://ubuntuforums.org/showthread.php?t=1193680") contains all the ways to run Ubuntu from a USB flash drive, including my preference, a full install.

---

### Post by zebraneo on 2009-08-07
Live CD USB Creator, and it doesn't save

---

### Post by randcoop on 2009-08-08
You'll need a casper-rw file in order for persistent to work.  Simply telling it to happen in the boot config isn't sufficient.  It will try to save changes, but has no where to save them without the casper-rw.  

Creating a casper-rw is not an easy thing, but you can download pre-created ones.  First you'll need to determine how big you want it to be.

---

