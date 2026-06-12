---
title: "Hard Drive Advice"
date: 2012-12-24
forum: Hardware
---

### Post by suddentwigs on 2012-12-24
Good morning. I am running Ubuntu Studio 10.04 Lucid Lynx. I am about to invest in a new external hard drive to cope with my ever increasing collection of data, and I wonder if somebody can enlighten me about filesystems. I understand that the FAT systems are not great and can lead to problems with data preservation etc. Is Ext4 the optimum choice of filesystem? I have my eye on this: 
 
[http://www.ebuyer.com/384256-seagate-3tb-expansion-desktop-hard-drive-stbv3000200](http://www.ebuyer.com/384256-seagate-3tb-expansion-desktop-hard-drive-stbv3000200)
 
Is it likely I'll be able to format it with a useful filesystem without losing a lot of space? If not, can somebody suggest an alternative? Many thanks.

---

### Post by Grenage on 2012-12-24
Use eSATA if it's available on your PC.

EXT4 is a good choice, unless you're planning on connecting the drive to a Windows machine - in which case you should consider NTFS.  You can change the reserved block % on EXT4 so you don't need to lose 5%.

---

### Post by rnerwein on 2012-12-24
> **Grenage said:**
> Use eSATA if it's available on your PC.

EXT4 is a good choice, unless you're planning on connecting the drive to a Windows machine - in which case you should consider NTFS.  You can change the reserved block % on EXT4 so you don't need to lose 5%.
hi
by the way: tune2fs is the command to change the reserved block count
cheers :P

---

### Post by suddentwigs on 2012-12-24
Is eSATA preferable to USB 3.0? I thought USB 3.0 was the fastest connection these days. Broadly speaking, is it possible to format any drive with any filesystem? I am not planning to connect this drive to a windows PC at any point.

---

### Post by Grenage on 2012-12-24
Sorry, I missed that is was USB3; do you have a PC with USB3 ports?

I find eSATA to be more reliable, and while I haven't tried a large amount of USB3 devices for bulk data transfer, I didn't see anything that topped eSATA.  In theory it's faster, and I suspect that performance will improve.

I also find USB storage on Ubuntu to be a bit flaky; I'd have less reservations if using it on a Windows machine.

---

### Post by fdrake on 2012-12-24
> **suddentwigs said:**
>  is it possible to format any drive with any filesystem?

yes. you may want to start with gparted :[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

also check the man command for alternatives to gparted such as fdisk, parted,..



> Is eSATA preferable to USB 3.0? I thought USB 3.0 was the fastest connection these days.
it looks like there are different opinions about it... [http://www.itworld.com/hardware/98987/usb-30-vs-esata-is-faster-better](http://www.itworld.com/hardware/98987/usb-30-vs-esata-is-faster-better)
i'd prefer usb since i am sure you'll be moving the ext hd around with other comp.

---

### Post by dannyboy79 on 2012-12-24
yes, you can format it to any filesystem you want using gparted. i would also second eSata but if you don't have eSata ports, then usb3.0 of course. i have my external disk as ext4 and all is well. fat32 is the most compatible with Win, OS X, and Linux BUT there's a max file size of 4GB and I am not sure if there's a max hard drive size (2TB or 3TB etc). If you never intend to hook it up to anything other then Linux, then ext4 is a great choice

---

### Post by suddentwigs on 2012-12-24
Yes, I have 2 USB 3.0 ports. I also have 1 eSATA socket free. In what way do you find USB storage flaky on Ubuntu? I've never had a problem myself. I'm more concerned about picking the right drive and formatting it to Ext4, as I use my computer for audio work and have just learned that FAT can corrupt files and shouldn't be used to store delicate project files.

---

### Post by Grenage on 2012-12-24
FAT isn't journaled.

I find USB flaky on speed detection with some systems; it's better than it was.  Be it USB3 for portability, or uSATA, you should be fine with either - although I have not used USB3 on any Linux systems.

---

### Post by dannyboy79 on 2012-12-24
> **suddentwigs said:**
> Yes, I have 2 USB 3.0 ports. I also have 1 eSATA socket free. In what way do you find USB storage flaky on Ubuntu? I've never had a problem myself. I'm more concerned about picking the right drive and formatting it to Ext4, as I use my computer for audio work and have just learned that FAT can corrupt files and shouldn't be used to store delicate project files.
fat (fat32) has no more corruption possibility then any other filesystem AFAIK. It's been around forever which would lead me to believe it's very stable but does have it's limitations.

---

### Post by kurt18947 on 2012-12-24
> **Grenage said:**
> FAT isn't journaled.

I find USB flaky on speed detection with some systems; it's better than it was.  Be it USB3 for portability, or uSATA, you should be fine with either - although I have not used USB3 on any Linux systems.

It seems there is quite a lot of variability in USB chipsets.  I had one notebook HD enclosure that was advertised as USB 2.0.   It was   s  l  o  w.  When I looked at it with disk tools, the connection speed showed up as 1.2 Mb./sec (I think) aka USB 1.  I put the same hard drive in a different enclosure (Vantec) and the displayed speed was 480 Mb./sec.  Actual throughput was less but still better than the no-name enclosure.

---

