---
title: "best way to retrieve data"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by aaronp on 2009-04-07
Hi all,

I'm running Hardy Heron 8.04 and have 2 IDE hard drives, with 2 partitions each.
My motherboard blew up and I now have no way of accessing the data on my drives.

The PC was getting old so I decided to think of this as a good opportunity to buy a new one.

Problem - the new PC has only a SATA hard drive (preloaded with Vista and other MS bloatware) and no IDE slots on the m/b.

I was hoping to just open the case, plug in my two IDE drives and boot into Ubuntu like nothing ever happened but now it looks like I will have it do it a bit more round-a-bout than that!

Can anyone suggest the best options for getting my data and basically returning myself to where I was before the m/b died? 
I'm keen to keep using Ubuntu again and let the Vista gather dust but want to figure out the best way to go about this...
Also, keen to get use out of my two IDE drives as they are both reasonably new and I'd like the storage!!


I was thinking of getting an IDE HDD enclosure and plug it in via USB to effectively make my old drives external USB drives but because they are all formatted to ext3 will the enclosure be able to cope?

thanks in advance
Aaron

---

### Post by Partyboi2 on 2009-04-07
Another option could be to get a SATA to IDE converter.

---

### Post by pbpersson on 2009-04-07
I would just get [one of these]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4323593&CatId=508")

---

### Post by Didius Falco on 2009-04-07
Go with the SATA to IDE converters - much cheaper that way, you don't use up a slot unnecessarily and it'll keep your cables neater.

---

### Post by tgalati4 on 2009-04-07
Get a cheap usb enclosure and attempt to boot from usb drive.  Get a proper SATA drive for your new machine and install the latest distro.   Either way, you can dual-boot or just access the usb drive for your legacy data.

---

### Post by aaronp on 2009-04-07
thanks guys.
I think the PCI IDE card looks like the best optio. only about $25 too.

---

### Post by aaronp on 2009-04-09
ok guys, I'm back...

I bought an IDe 3.5 HDD enclosure. 
Now, when plugging it into the PC it doesn't seem to be recognised at all.

My external enclosure is a Vantec Nextar 3 and I've seen some psots saying it works fine with Ubuntu.

Here is the output of lsusb

```
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c054 Logitech, Inc. 
Bus 001 Device 002: ID 04f2:0760 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
```

This doesn't change, whether I have the external plugged in or not.

```
And this is fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e9be1ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda3            1531       11729    81923467+  83  Linux
/dev/sda4           11730       19059    58878225   83  Linux
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order
```

Again, makes no difference if the device is plugged in or not.

This is an almost completely fresh Hardy install so wondering if I am missing some drivers or something like that?
I would still expect that the USB device would at least be detected, even if it was not going to recognise it as a hard drive or mount it.

FYI the hard drive is 80gb formatted to ext3.

Any thoughts?

---

### Post by aaronp on 2009-04-09
All,

Sorry, disregard my previous post.
Seems I have no idea how to correctly plug in a USB cable.

Got that right and surprise, surprise my hard drives appaeard on the desktop instantly!!

thanks guys
Aaron

---

