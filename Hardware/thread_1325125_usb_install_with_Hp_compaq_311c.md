---
title: "usb install with Hp compaq 311c?"
date: 2009-11-13
forum: Hardware
---

### Post by drew45 on 2009-11-13
Hi all :),
I've just received a  compaq 311C notebook and cannot install ubuntu netbook remix 9.10.  I get a blank screen on both try install or install options.
Reading the forums I see others have had difficulty with usb install. I've tried 9.04 as well with the same results. 
any help troubleshooting greatly appreciated.

W.

---

### Post by drew45 on 2009-11-15
Hi,  I'm getting the message can not mount /dev/loop1 on /cow

any help troubleshooting please?

W.

---

### Post by davidryderuk on 2009-11-15
Have you tried using usb-creator again and not leaving any storage space for your documents? I think the option you want will be:

"Discard on shutdown, unless you save them elsewhere"

> 

Just to flag up that this issue may also apply to UNR 9.10 beta:

I make a bootable SD card of ubuntu-9.10-beta-netbook-remix.iso with usb-creator
- with persistence I have the same (initramfs) error: mounting /dev/loop1 on /cow failed
- with no persistence it boots fine

I'm afraid I didn't investigate much at the time (just went ahead without persistence) and only subsequently spotted this bug report. When I have spare media I'll try to recreate this and see if PATH=$PATH:/filesystem.squashfs/usr/bin gets around it as above.


[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/365853](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/365853)

---

### Post by gzarkadas on 2010-04-01
The 'discard' option worked for me (with a Packard Bell dot m notebook) - the 'keep files' one always threw me in busybox. I had an 8 GB flash drive, so I instructed gparted to make 2 partitions: one 800 MB for the iso image and the other with the rest space. Formatted both partitions to FAT-32 and set flags 'boot,lba' for first, 'lba' for second. That way I have a working boot disk + space to save files in one usb flash.:p

---

