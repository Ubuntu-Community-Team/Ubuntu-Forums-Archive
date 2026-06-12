---
title: "Windows disk not showing properly"
date: 2008-09-07
forum: Hardware
---

### Post by akczero on 2008-09-07
Hi all, 

I'm trying to recover my data from my laptop's vista disk. I'm running Ubuntu 8.04 desktop. I go into places>computer and attempt to mount the windows drive. Instead of 200 GB media or what have you, it just says "SCSI Drive" and will not mount or anything. What could be the problem here?

---

### Post by cdtech on 2008-09-07
Could you open a terminal and type:
```
sudo fdisk -l
```
This will show the drives and partitions. Maybe we can mount it through the command line to recover your data.

---

### Post by akczero on 2008-09-08
Okay this is what it says...

fdisk: invalid option -- 1

EDIT: oops it's a lowercase l, not a 1. Looks exactly the same!

This is what I get. 

Disk /dev/sda: 200.0 GB, 200049647616 bytes 
255 heads, 63 sectors/track, 24321 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xdc79474a 

Device: /dev/sda1 
Start: 1 
End: 913 
Blocks: 7331840 
Id: 27 
System: Unknown 

Partition 1 does not end on cylinder boundary. 
Device: /dev/sda2
Start: 913 
End: 24322 
Blocks: 188027096
Id: 7 
System: HPFS/NTFS

---

### Post by akczero on 2008-09-08
bump, help?

---

### Post by cdtech on 2008-09-08
You can just copy/paste the output from the terminal, it makes it easier to read. lol

Can you browse the SCSI drive listed within "places"?
Is this your primary drive? Does it have an OS on the primary partition?

---

### Post by NetpigsBang on 2008-09-08
**[[color=magenta]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=seagreen]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by akczero on 2008-09-08
Sorry about the typing - was using another computer to access the internet while I was fiddling with my laptop (the problem child). 

I haven't tried browsing the drive through "Places", but in Computer, the drive is titled "SCSI Drive" and gives me an error when I double click it (this error message won't tell me the info I need to mount the drive). 

Yes this is my primary drive on the machine (Sony VAIO VGN-FZ140E notebook) and yes Vista is on the primary partition.

---

