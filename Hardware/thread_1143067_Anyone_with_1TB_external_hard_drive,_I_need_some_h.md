---
title: "Anyone with 1TB external hard drive, I need some help..."
date: 2009-04-29
forum: Hardware
---

### Post by legolas_w on 2009-04-29
Hi
Thank you for reading my post.
I am looking to buy a 1TB external hard drive and I want to know which model and brand is compatible with ubuntu and whether the following things are doable with an external hard drive or not.

- Can I partition the external hard drive into several partition?
- If yes, Is it possible to have encrypted partition which somehow asks for some sort of key before let a user use it?
- Does these hard disks designed to be used rarely or I can attach it to my computer permanently?

Thanks.

---

### Post by Peasantoid on 2009-04-29
"Compatible" with Ubuntu?

If the manufacturer had any sense whatsoever, the device should definitely not require drivers.

1) Yes, of course.
2) Don't know.
3) Yes, you can attach it permanently. My current one has been going strong for ages.

---

### Post by legolas_w on 2009-04-29
Peasantoid,

Can I ask what model and brand is your disk?

Thanks.

---

### Post by keith.newell on 2009-04-29
This would be more of a personal preference, but I would recommend any drive that Western Digital makes.  For some reason I have just had a run of bad luck with Seagates.  Once again, just my personal opinion.  Hope this helps.  :)

---

### Post by coffeecat on 2009-04-29
> **keith.newell said:**
> For some reason I have just had a run of bad luck with Seagates.

Any USB drive should just work. However, I've come across a few threads about Seagate USB drives not working with Linux, where they work just fine with Windows. There may very well be something odd with the Seagate firmware that conflicts with the Linux USB driver. So, yet another reason not to go for Seagate. :roll: Or Maxtor either, whom Seagate bought out in 2006.

---

### Post by pparks1 on 2009-04-29
I've been very happy with Western Digital external drives as well.   I've got 3.5" versions and 2.5" versions and all have worked just fine for me.

As far as encrypting the drive goes, you certainly can encrypt the whole filesystem on a partition.  Look at something like truecrypt.org for this.

---

### Post by Peasantoid on 2009-05-01
> **legolas_w said:**
> Peasantoid,

Can I ask what model and brand is your disk?

Thanks.
Sorry I couldn't respond sooner, I was dead. :)

It's a LaCie 300GB "designed by Neil Poulton" disk. Basically a shiny black box with a blue strip light that shines onto the table.

---

### Post by brandon88tube on 2009-05-01
I have a Western Digital Caviar Black 1TB. I would have to recommend buying a normal hard drive and buying an enclosure for it. In my opinion you get exactly what you want and I think its cheaper.

---

### Post by eric stockman on 2009-05-06
I myself  bought a Lacie 1 TB & this drive seems to be pre-partioned in a non-dos way  ( MAC? ) .
To straighten things up ( whereby You will lose the pre-installed Windows & Mac software ( linux users dont need them anyway ) you can use dd to overwrite the mbr-sector on that ext.drive where its partition table lives.
Suppose your new external Usb-drive is /dev/sdc 
To be sure You can save its current mbr sector with:
 sudo dd  if=/dev/sdc  of=lacie.mbr  count=1  bs=512 
this will copy the first 512 bytes into a file lacie.mbr ( give it a name to your liking )

Now overwite the mbr-sector with the one on your hard-drive :
 sudo dd  if=/dev/sda  of=/dev/sdc  count=1  bs=512 
Be **carefull** here dont swap the input file (if) with the output(of ) 
( change sda into hda if needed by your hardware ) 
Now start up gparted and You will be able to partition the external drive to Your liking.

---

### Post by coffeecat on 2009-05-06
> **eric stockman said:**
> 

..... 


Now start up gparted and You will be able to partition the external drive to Your liking.

There's an easier way. :wink: Simply start up Gparted, go to Device -> Create Partition Table and create an msdos partition table (which is the default). Now you can create your partitions.

---

### Post by inspired on 2009-05-06
> **legolas_w said:**
> Peasantoid,

Can I ask what model and brand is your disk?

Thanks.
I have two 1TB Drivestation disks from Buffalo. Works great. One is USB 2.0 only, and the other is dual firewire and USB.

Both work fine, straight out of the box.
In this moment the firewire connection has crapped out... but that's an issue with Ubuntu on my laptop having a problem, which I am in the process of resolving. For some days it worked fine on FW.

I also had a bad run with Seagate. Had a 500 GB pocket drive. It died after two weeks. Got it replaced... the next one died after about 5 weeks... and I was using a different laptop by the time I got that drive... so it was not my system corrupting it.

Jonathan

---

