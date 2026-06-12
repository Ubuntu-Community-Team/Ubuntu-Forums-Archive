---
title: "usb cd-writer"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by daveb272 on 2007-12-19
I did the swap for 3 of my 4 of my pc's to ubuntu.  The only working cd-writers i have are a hp usb cd-writer 8200 and an even older iomega zip usb cd-rw 650.  i cant use cd/dvd creator, it tell's me to insert media, and kb3 is now telling me the same thing.  The splindle is new, and i doubt that 15 disk were bad.  I need to make a copy of a couple of iso's, and now i cant do it anymore, can anybody help?

---

### Post by fs3rp4 on 2007-12-19
Put the K3B information about the cd-writer.

---

### Post by bokkie on 2007-12-31
I have a similar problem, with HP 8200 USB CD-writer on an IBM Thinkpad A21e laptop that has no CD-writer.

I cannot mount it, because there seems to be no entry in /etc/fstab or /etc/mtab

The device seems to be recognized by the system, as seen from the output below:

$ cdrecord -scanbus
...
...
scsibus0:
        0,0,0     0) 'HP' 'CD-Writer+ 8200e' '0001' Removable Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     ......

However, when I try to write to it, I get the following:

$ cdrecord dev=0,0,0 driveropts=burnfree -v -data foobar.iso
...
cdrecord: Continuing in 5 seconds ...
...
After 5 seconds, the CD drive light flashes briefly, and then the following message appears:
...
Device type    : Removable Disk
Version        : 0
Response Format: 1
Vendor_info    : 'HP'
Identifikation : 'CD-Writer+ 8200e'
Revision       : '0001'
Device seems to be: Generic CCS Disk.
cdrecord: Sorry, no CD/DVD-Drive found on this target.

I assume this indicates that I have used the correct device information, but what is wrong?

---

