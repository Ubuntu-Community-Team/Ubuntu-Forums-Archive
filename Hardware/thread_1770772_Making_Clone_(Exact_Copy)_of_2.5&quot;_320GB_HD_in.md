---
title: "Making Clone (Exact Copy) of 2.5&quot; 320GB HD into a new partition in my 1TB 3.5&quot;"
date: 2011-05-29
forum: Hardware
---

### Post by just_ken_here on 2011-05-29
Hello

I have a laptop from 2008 which ran Vista on 320gb HD.
The Vista had been problematic since 2010 and finally came to DOOM failing to boot earlier this year-
I do not mind the Vista ended- but I would like to save my datas from it.

I could have just set new partition and installed Ubuntu, since it is able to traverse NTFS filesystem from my old Vista. Everything should have been solved with new OS.
But I suspect that the 320gb HD on the laptop is problem. Its failures destroys the Vista system somehow at sometime.
OR it may not - the Windows itself may become .... in middle age.

==================================================
So, I would like to get the whole 320gb from my laptop HD all transfered  (copied / backed up) to a new partition on my 1TB 3.5" HD that runs on my PC.

That way I can use the Ubuntu 10.10 on that 1TB drive to traverse over my old files from the 320GB Vista. Problem solved : I can toss or do experiment with the 2.5" drive

--------------------------------------------------
I may have idea on how to do this... But I would like to make sure that I am doing this Correctly <OR> if there is other more sophisticated & safer ways.

I am cautious since the 2.5" 320gb laptop drive seems instable. Like I said, I am suspicious of the drive-
Ubuntu LiveCD crashes often when running from my laptop while traversing the old NTFS filesystem. --> Thats why I put off with installing Ubuntu to rescue my laptop content.

My plan was to set aside new partition 320gb of NTFS on my 1TB 3.5" drive.
Then putting the laptop HD to an 2.5" enclosure -> hook it up via USB to my PC running Ubuntu on the 1TB drive.

From Ubuntu: just copy paste (all of the 320gb laptop drive to the new 320gb NTFS partition on my 1TB drive)

This should work right ?
(I just hope my laptop drive will not fail during the heavy read & transfer)


OR
Is there any other good or safer way ?

Thank you for all your good inputs & recommendations.

---

### Post by just_ken_here on 2011-05-29
**Hardware & Laptops**
(Problems with hardware & laptops not being detected or supported during or after install.)

-sorry
if it is in wrong section..:(. I guess I just read the title part.

Pls feel free to move it to elsewhere.. or let me know how to.

Sorry.

---

### Post by ILoveYorkies on 2011-05-31
> **just_ken_here said:**
> **Hardware & Laptops**
(Problems with hardware & laptops not being detected or supported during or after install.)

-sorry
if it is in wrong section..:(. I guess I just read the title part.

Pls feel free to move it to elsewhere.. or let me know how to.

Sorry.
[SIZE=2]Hi,
I wish I could help you more but I'm very new to Ubuntu and I'm running  with 11.04 but I could help better if you cleared something up for me. Do you want to access the clone of the  2.5 in. 320gb hard drive on the 1TB 3.5 in. drive that is installed in another computer that is already running Ubuntu 10.10 only but not dual booting with Windows Vista or Windows 7? If so, then I would only copy your user files like documents, photos, videos, music and scans to your computer from a scanner because if you clone the entire drive to the 3.5 and you try to access it from Ubuntu it might not work (it may even overwrite Ubuntu). an exact copy of the 320gb drive would contain the os (operating system in this case Vista) and the apps or programs installed which Ubuntu might have trouble with but it should be able to read all your user files. If you dual boot the computer that has the 3.5 in drive with Windows Vista or Windows 7 then you could do the exact cloning but be careful that the copy doesn't overwrite the os on the computer with the 3.5 in. disk. That's all the advice I can give you. Good Luck.
[/SIZE]

---

### Post by jerrrys on 2011-06-01
check out clonezilla.  been using it for a few years and a excellent tool for cloning.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by dandnsmith on 2011-06-01
just_ken_here:
don't know if youve done it yet, but I had a couple of thoughts

- HP installations usually have one or 2 extra partitions to do with restore functions, so you may not need 320 GB
- don't create the 320GB partition, just make sure there is spare space
- use clonezilla or gparted for the transfer and creation of new partition

- the failure may be the motherboard or RAM if the LiveCD is failing part way through traversing the files. You could consider trying a testing suite to determine where (use it to check the HDD as well

---

### Post by just_ken_here on 2011-10-10
Probably the HD was fine.
but it was just hacked all the time..

got now HD anyway.. but still hacked.

---

