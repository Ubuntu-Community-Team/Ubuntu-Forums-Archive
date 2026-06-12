---
title: "Error 18 and hard disks"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by Dangerousdave26 on 2009-08-29
Ubuntu 9.04 Desktop addition
Dell Inspiron 1150 note book
1 GB Ram
320 GB Hard Drive (brand new)

I read the manual on the install burned the ISO to CD but must have had a CD failure in the burn. 

Next attempt was on DVD all went well there. 

I installed the system following all of the defaults. 

Used the whole drive as one partition plus the swap file partition of 2.9 BG.

I went to do the first reboot and got the "loading Grub" then "Error 18"

I did a quick google search and found an old archieved thread here that pointed out it may be caused by bios problems related to the hard drive. 

So off I go to Dell to check the Bios for the latest update. The last update for this device was A07 and that is the version I have. No problems there.

Then I checked the bios settings and I can not change anything related to the hard drive. I can see the drive and the BIOS is saying it is a 137GB drive. Nope its not its a 320 so that must be the problem. 

What is did was reload again this time I broke up the drive into 3 ext3 partitions and the swap file. 

1 x 120 GB ext3 Mount as /
1 x 120 GB ext3 Mount as /user
1 x 77 GB ext3 Mount as /home
1 x swap 3 GB (about)

That worked no more error 18 but was it the right way to fool the system?

How should I have partitioned this?

Odds are good its going to get blow out tomorrow and get 2 partitions plus the swap drive. 

Thanks for any help

---

### Post by rrplay on 2009-08-29
Did you check the hard drive in the bios after installing with your previous partitioning scheme?

anyhow 50GB is plenty for /
3GB is fine for swap
plenty of GB's left for /home

hope this helps

---

### Post by presence1960 on 2009-08-29
> **rrplay said:**
> Did you check the hard drive in the bios after installing with your previous partitioning scheme?

anyhow 50GB is plenty for /
3GB is fine for swap
plenty of GB's left for /home

hope this helps

If your hard disk is not being read correctly in the BIOS that can be a major problem. I would check with Dell to find a solution to the problem. I recall there being something you need to do when that happens, but right now I can't remember the procedure. Maybe someone else here knows. if not call DEll it is their machine.

P.S. I did some googling and a few hits suggested updating your BIOS as some older BIOS have a limit of 137 GB for hard disks. You can get an updated BIOS from Dell's site.

---

### Post by Dangerousdave26 on 2009-08-29
No I did not and that was a good question.

Looking at it again it still shows the primary Hard Drive : 137 GB.

Since I set it at about 120 that tells me it should be the limit on the hard drive size. 

Thats what I will do go 50 GB on the / the balance on the second parition and about 3 BG on the swap. 

Thanks

---

### Post by Bartender on 2009-08-29
Yeah, that's weird that BIOS is not picking up the specs on the new drive.  Does BIOS tell you anything else about the drive?  IIRC there's usually a line next to the capacity that identifies the drive - something like SG320G-1104553 or similar that will indicate the brand and capacity.
I'm wondering if there's something wrong with the new drive?  Some tiny flaw that's not letting it identify itself correctly?  It would be interesting to put that drive into another PC and see if it's picked up correctly...

---

### Post by louieb on 2009-08-29
The traditional way of dealing with grub error 18 is put /boot in its own partition located near the front of the drive.   1/2GB would be plenty of space for a /boot partition.  In your case if you made your 1st partition mount / (root) and kept its size under 130GB or so then you would not need a /boot partition. 

Also no need to separate /usr from / (root) combine them and give the partition  20GB or so and you should be fine. 

1GB for swap is fine unless you hibernate - then needs to be larger that the amount of ram installed  

> Looking at it again it still shows the primary Hard Drive : 137 GB.Just one thing:  in BIOS setup check the mode make sure its set to LBA (logical block addressing)  the 137GB limit usually occurs when mode is set to CHS or user. 

so what to do with the rest of the space? Some would say use it for /home. 

Others including myself make a small 5GB partition for /home all that really needs to be there is a bunch of small configuration files email by far being the largest.  Then with the rest of the drive use it for a data partition to store you music, photos, whatever.      

still others don't bother with a separate /home partition and just make their / (root) partition a little larger and use the rest for a data partition.   
This would be my 2nd choice.     

:confused: Hope I didn't confuse to much. But choices choices choices.

> Looking at it again it still shows the primary Hard Drive : 137 GB.

In BIOS setup check the mode - should be set to LBA (logical block addressing) It might be set to CHS or user - that would explain the 137GB limit too.

---

### Post by Dangerousdave26 on 2009-08-29
This bios seems to be locked down pretty hard. 

You can't change any thing on page 1 

This page contains all of the system information. 

Date and Time
Intel Celeron 2.60 GHz
Level 2 Cache 128KB
System Memory 1024 MB
Video Controller Intel 852GM/GME/GMV
Panel Type: 14" XGA
Audio Controller: Sigmatel 9750
Modem Controller: Broadcom Polaris
Primary Hard Drive: 137 GB (note when I put the original back in it reads the correct size as 30GB. It only shows 137 when the 320 GB is in place)
Modular Bay: CD-RW/DVD Combo

Of these values the only one I can change is the system date and time. 

Page 2 is the Boot order very simple 

Page 3 is Post Configuration, Wireless Configuration, and basic Devices Configuration

Page 4 is the battery setting

Page 5 is Power management basically it is just the display brightness when on battery or AC power. 

Page 6 System security Bios Passwords. 

For this test I put the old hard drive back in and it reads correctly @ 30 GB that tells me louieb is right on with his assessment that it is reading CHS or user. However there is no way to set it to LBA. 

So it looks like the easiest way to do it is something similar to what I have already done. 

But now I need to read louieb post a little closer and see if I can decipher it. 

Oh and Ubuntu does not have a problem seeing the total drive size. 

Thanks.

---

### Post by Dangerousdave26 on 2009-08-30
OK we can count this one as solved 

Thanks for everyone's help.

I did some extensive reading on partitioning and partition types then I settled on this set up.

sda1 ext2 512 MB /Boot
sda2 ext3 32 GB /
sda3 swap 3 GB 
sda5 ext3 82 GB /usr
sda6 ext3 20 GB /tmp
sda7 ext3 180 GB + /home

It may be flawed but I figured when the flaws show up I will learn from it.

Resources

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

[http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html)

[http://www.tldp.org/HOWTO/Partition/](http://www.tldp.org/HOWTO/Partition/)

---

### Post by louieb on 2009-08-30
As long as it works - right. cool You can now mark this as solved by clicking on thread tools (located near the top)

---

