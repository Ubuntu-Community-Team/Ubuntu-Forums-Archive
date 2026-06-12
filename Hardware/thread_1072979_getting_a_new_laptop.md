---
title: "getting a new laptop"
date: 2009-02-17
forum: Hardware
---

### Post by themuddaload on 2009-02-17
hey guys, its been a long time since ive been on the forums, but i came up with another question.

I plan to get a laptop for college. I will probably end up getting a Sony Vaio. a while back i seem to remember that there was a problem with ATI graphics cards not working with linux? all the graphics cards sony offers are ATI.

next question, is it possible to run a full gui, fancy distro (like Ubuntu [not like Damn Small Linux]) off of an external usb hard drive? I would like to still have the laptop be running windows, but i would like to have linux available because its freedom from viruses (parents got hit with malware twice in the last month, twas a pain in the butt). 

thanks guys.

- TML

---

### Post by Mizzou_Engineer on 2009-02-17
> **themuddaload said:**
> hey guys, its been a long time since ive been on the forums, but i came up with another question.

I plan to get a laptop for college. I will probably end up getting a Sony Vaio. a while back i seem to remember that there was a problem with ATI graphics cards not working with linux? all the graphics cards sony offers are ATI.

ATi cards mostly work fine under Linux now, ever since AMD bought ATi and put the spurs to the driver developers. I happily ran a desktop Radeon x1900GT until recently and replaced it with a Radeon HD 3850, which also runs very well. I would avoid Intel IGPs for the moment as the Intel IGP driver is a major work-in-progress. It has horrible 3D performance and often breaks suspend and hibernate, as I found out with my laptop and its GM45 IGP.

> next question, is it possible to run a full gui, fancy distro (like Ubuntu [not like Damn Small Linux]) off of an external usb hard drive? I would like to still have the laptop be running windows, but i would like to have linux available because its freedom from viruses (parents got hit with malware twice in the last month, twas a pain in the butt). 

thanks guys.

- TML

As long as you get a decently-fast USB stick, sure. Partition the drive, put a Ubuntu Live image on one partition and then put your /home on another.

---

### Post by themuddaload on 2009-02-18
> **Mizzou_Engineer said:**
> 
As long as you get a decently-fast USB stick, sure. Partition the drive, put a Ubuntu Live image on one partition and then put your /home on another.

So I just run the distro off of the iso image? I cant actually install it?

---

### Post by Mizzou_Engineer on 2009-02-18
> **themuddaload said:**
> So I just run the distro off of the iso image? I cant actually install it?

You could do that. I suggested using a live CD image as you need a far larger USB stick to do an actual install- 4-8 GB instead of 1 GB, the constant writes to a USB drive from a read-write installed OS will kill the drive far faster than the read-only live CD image, and a live CD puts much of the OS in RAM versus reading the OS from the USB drive. USB drives give you maybe 25 MB/sec throughput tops, so they're not all that fast but even slow RAM in a new laptop will be more than 10 GB/sec.

---

### Post by themuddaload on 2009-02-18
> **Mizzou_Engineer said:**
> You could do that. I suggested using a live CD image as you need a far larger **USB stick** to do an actual install- 4-8 GB instead of 1 GB, the constant writes to a USB drive from a read-write installed OS will kill the drive far faster than the read-only live CD image, and a live CD puts much of the OS in RAM versus reading the OS from the USB drive. USB drives give you maybe 25 MB/sec throughput tops, so they're not all that fast but even slow RAM in a new laptop will be more than 10 GB/sec.

I mean to put linux on an external hard drive, not a flash drive.

---

### Post by alexandari on 2009-02-18
Hi dude! I`m using ATI too,it`s fine :) (i`m not saying it`s great cuz i hate ATI). Maybe this is going to be a liiiitle out of topic:
so you`r saying about SONY laptops? Well,I cant tell you much about sony but...please hear what i`m saying...dont buy TOSHIBA laptops! I`m using a TOSHIBA Sattelite at the moment and it`s freaking burning my hands! both cores go 90 degrees when I`m playing WoW for example :( It`s overheating. The only advantage of that is making your own coffee on your laptop...or maybe eggs...you`r choice :)

---

### Post by stuffystuff200681 on 2009-08-03
if the computer has a esata (external sata) a full installation should work

got a hp pavillion and tried the esata boot before posting

RESULT: Much better than usb!!!:D 

you should switch up the roles too
esata= windows (make copy of drive with norton ghost or the like)
hdd= UBUNTU (much better to have ubuntu on top isn't it?)

all of this is just how i look at it; take what want and need.:P

---

