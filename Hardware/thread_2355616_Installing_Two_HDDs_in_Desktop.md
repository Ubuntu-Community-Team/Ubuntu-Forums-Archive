---
title: "Installing Two HDDs in Desktop"
date: 2017-03-14
forum: Hardware
---

### Post by shane_faulkinbury2 on 2017-03-14
Yesterday I purchased a Seagate Barracuda.  I want to install it in my desktop witch already has an HDD installed.  What I would like to do is have my Ubuntu 16.04.1 installed on one and have my Documents, Downloads, and Videos installed installed on the other.

What I'm wondering is how I would go about this?  My desktop is an three year old HP witch only has one power connector for an HDD, but has three slots for HDDs.  Oh yeah, it's an IDE and not a SATA.  What do I need to purchase to get this working?

---

### Post by TheFu on 2017-03-14
If you desktop uses SATA, then you need a SATA HDD and power connections.

Most people would place their complete HOME on the new disk.  Please explain what you think needs to happen.  There are lots of how-tos for adding more storage to Linux systems. Those are all fine. Just be certain to use ext4 as the format. You could use any Linux file system, but ext4 is usually the best all-round answer.

Also, if you've used LVM or encryption, let us know how you did that. There are multiple ways.

---

### Post by oldfred on 2017-03-14
If HP is only 3 years old that really should be SATA not IDE.
When I built my system in 2006, the new SATA drives cost about $10 more then IDE, but only a year or two later they were they same cost. Then then only started selling IDE drives for compatibility with older systems.

       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

---

### Post by shane_faulkinbury2 on 2017-03-14
Well I'll have to look after I get off this computer, but it looks a lot like the PATA.  It was brand new three years ago so you might be right about it not being IDE.  I thought IDE and SATA were the only two kinds. :lolflag:

---

### Post by shane_faulkinbury2 on 2017-03-15
Well it actually looks like a SATA so I guess I'll have to purchase something like this with a usb hook up.       [HTML]https://www.newegg.com/Product/Product.aspx?Item=N82E16817349010&cm_re=SATA_hard_drive_enclosure_kit-_-17-349-010-_-Product[/HTML]

---

### Post by shane_faulkinbury2 on 2017-03-15
I just got this one.  I hope it works!  [https://www.newegg.com/Product/Product.aspx?Item=N82E16817182155](https://www.newegg.com/Product/Product.aspx?Item=N82E16817182155)

---

### Post by shane_faulkinbury2 on 2017-03-22
I found out you can't install Windows 10 on a flash drive or external HDD so it looks like I'm done trying that.  So I guess I'll install Xbuntu, Mint or some other distro.  Maybe I'll go ahead and try Ubuntu Server to put my website on it, get rid of Godaddy and save $20 a month!  If anybody comes up with a way of installing Windows 10 on an external let me know.  :D

---

