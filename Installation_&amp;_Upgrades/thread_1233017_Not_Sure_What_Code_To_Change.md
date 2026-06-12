---
title: "Not Sure What Code To Change"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by zebraneo on 2009-08-06
I was told to change this but I am not sure exactly what I have to change Please tell me excatly what I have to do, this is the first time I am using Linux and changing a code, so please tell me what do 
This is the code that I have now:
[COLOR=DarkRed]

default persistent

label persistent

menu label ^Start ubuntu

kernel /casper/vmlinuz

append file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash perssistent --

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
  localboot 0x80[/COLOR]


and
this is what I was told to do!!!!!!!!!!!!!!


Make the drive persistent
By making the pen-drive installation persistent, you are modifying the installation to allow you to save changes. This will alter the Linux installation so that it does not assume that install media is unwritable. To do this, you must modify syslinux which was created to boot the drive.

   1.Boot your system from your host operating system (something other than off the pen-drive)
   2. Mount the pen-drive
   3.Edit text.cfg from within the syslinux folder by replacing the default live entry with:

default persistent

label persistent

menu label ^Start ubuntu

kernel /casper/vmlinuz

append file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash perssistent --

---

