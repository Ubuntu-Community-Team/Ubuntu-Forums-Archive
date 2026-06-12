---
title: "Simple way to determine type of RAID on PC?"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2009-04-10
My Motherboard is a Gigabyte GA-7VAXP & the manual says it supports RAID-0 & RAID-1.
When I purchased my PC, the builder set it up as 2 HDDs = 1 massive HDD (2-120Gb = 240Gb) which I think is RAID-0. I didn't like that so they re-installed & there were 2 separate HDDs (c: & g: ) which I think is RAID-1. I have since added a 3rd HDD that is 200Gb.
How can I be sure which  one it is, as I need to know for Ubuntu Jaunty installation? Can anyone tell by my description?:confused: 
Thanks

---

### Post by cariboo on 2009-04-10
I would suggest you boot from the LiveCD and open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

the last letter is a lower case L. If you could paste the output in your next post it would be helpful. 

You can do the above using the LiveCD, if networking is working you can acess the forums using firefox.

Jim

---

### Post by GARoss on 2009-04-10
> **cariboo907 said:**
> I would suggest you boot from the LiveCD and open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

the last letter is a lower case L. If you could paste the output in your next post it would be helpful. 

You can do the above using the LiveCD, if networking is working you can acess the forums using firefox.

Jim
Thanks, Jim. Here it is;

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x303cb472

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb0c7ba6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e5c9c32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

George

---

### Post by cariboo on 2009-04-10
Unfortunately the output doesn't give what i was looking for, but, looking at your post again If your raid array's capacity is 120Gb then you are using raid1. As you said the origional setup was 240Gb which would indicate that it was raid0.

[list=1]
[*]raid0 = stripping, which is used more for speed than redundancy.
[*]raid1= mirroring for redundancy[/list]

Are planning to install Ubuntu on the 200Gb? If so it will show up as /dev/sdc in the partition editor.

Jim

---

### Post by GARoss on 2009-04-10
> **cariboo907 said:**
> Unfortunately the output doesn't give what i was looking for, but, looking at your post again If your raid array's capacity is 120Gb then you are using raid1. As you said the origional setup was 240Gb which would indicate that it was raid0.

[list=1]
[*]raid0 = stripping, which is used more for speed than redundancy.
[*]raid1= mirroring for redundancy[/list]

Are planning to install Ubuntu on the 200Gb? If so it will show up as /dev/sdc in the partition editor.

Jim

Just to clarify;
3 HDDs c: 120Gb, f: 120Gb & g: 200Gb. I can load data on each HDD independently.

When I got to the partition area with Alternate Install CD, it recognised all 3 HDDs.  

I have ample space on any of the the 3 HDDs. I assumed it would be on the old c: because of RAID. I thought RAID data was needed on both 120Gb HDDs. The 200Gb was added later & shouldn't be affected by RAID.
Can I just install it on my old g: (200Gb) without adding boot data to support RAID-1 (assuming it is RAID-1)? 
George

---

### Post by cariboo on 2009-04-10
IF you can add data to the 120Gb drives independantly, then you aren't using raid at all. If the 120Gb's were in an array you would only see them as a single 120Gb drive.

I have have a pair of 400Gb drives in a raid1 array on my server, this is the way they show up when I run df -h:

```
/dev/mapper/nvidia_ifdejefh1 370G  328G   24G  94% /home/storage
```

You can install Ubuntu on your 200Gb drive without having to do anything special. The only thing I would suggest, if you are running Vista is to use Vista's disk managment utility to resize the partion. If you are running XP run defrag on the partition at least twice before resizing it

Jim

---

### Post by GARoss on 2009-04-10
Thanks, Jim. 
There is something strange going on, though. Awhile back I tried to install on the 200Gb, g: by itself without the other 2 HDDs plugged in (I didn't want to accidentally delete anything). After the Live CD finished I couldn't boot to Ubuntu even with the HDD being plugged into where c: originally was. I put everything back together & deleted Ubuntu off g:. This gave me the impression that RAID had something to do with boot; that it shared data on both c & f drives (I don't recall trying c: without f: being plugged in to see if it worked by itself or not).
I'll give it a go & see what happens!
George

---

### Post by cariboo on 2009-04-10
Grub depends on the drive being where it was detected, If you installed Ubuntu on your third hard drive in Windows terms drive g:,Ubuntu sees the drive as the 3rd hard drive /dev/sdc. Ubuntu see drives, hard, cdrom, usb and other as a devices hence /dev and it now detects all drives as scsi hence /sd, c is the third hard drive. If you move the drive to a different connector the drive is no longer the third hard drive so grub can't find it and therefore will error out.

Good luck

Jim

---

### Post by GARoss on 2009-04-10
I'll give it a go. Thanks again, Jim!
George

---

### Post by GARoss on 2009-04-11
Okay, got it going on the 200Gb; with one glitch.
Used the standard CD to install & tried to manually set partition & this was the glitch. As it is 200Gb all I felt I needed was maybe 50Gb. So, I selected that HDD for 50Gb of ext4. It gave an error. After a few tries, I abandoned the install & when into XP to readup on it but also noticed the 200Gb HDD was not viewed in My Computer. 
I then tried to install again, but, this time with all 200Gb. To make a long story a little shorter, I couldn't split a portion for swap & ext4 manually; at least I didn't know how to do this in this menu. It was either 100% ext or 100% swap & in both cases it gave an error. So, back to the previous menu (see photo), selected the 200Gb & it installed successfully but with ext3 which I believe can be converted to ext4.
I've attached a photo of the menu that cause me so much confusion. After having install problems before it had me believing that it had a RAID-like function (sda & sdb both indicate XP is present) & Ubuntu would require a similar install. This was not the case.  
So, all is well with a dual boot Jaunty & XP!:guitar:
Thanks for all your help Jim!

---

