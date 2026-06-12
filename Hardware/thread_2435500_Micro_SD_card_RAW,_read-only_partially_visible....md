---
title: "Micro SD card RAW, read-only partially visible..."
date: 2020-01-21
forum: Hardware
---

### Post by miladost on 2020-01-21
Hello I have a micro SD card that is giving me problems. It won't show up when in my file manager but it does show in lsusb. After trying alot of things I know that the card became RAW file system is read-only and has no partition table. 


The card is legit it's a lexar 32gb 633x bought directly from Amazon (no third-party) I have barely used it and it was working fine until I tried some things. 

The problems began when I used Rufus 2.18 on winXP to put Ubuntu 19 server on the micro SD. After it asked to format the card  there was some error and then it didn't show up anymore. So I put it in a separate Ubuntu machine where it did show up fine. yet the Ubuntu machine does not have a native SD card reader so I had to resort to put it different cheap China gadgets like cameras and stuff. Why more than one? Because it was only recognized on some combinations of gadget+cable and when it was recognized it was stuttering (disconnecting and reconnecting after a few seconds). So I plugging and unplugging the card alot. After a while it became like I mentioned before. So what can I do to save this totally legit card?

---

### Post by CelticWarrior on 2020-01-22
From the description the card is likely to be busted now.

In order to avoid such problems in the future please use proper hardware.

---

### Post by tea for one on 2020-01-22
Yes, it sounds like the card may be unhealthy.

However, if you wish to experiment to see if all is not lost, then I suggest you have a look at the following utilities.

[B]gparted 
gnome-disks 
mkusb[/B]

Please be careful when using partitioning and formatting tools, it is easy to make a mistake especially if you are in a hurry.

---

### Post by miladost on 2020-01-22
> **tea for one said:**
> Yes, it sounds like the card may be unhealthy.

However, if you wish to experiment to see if all is not lost, then I suggest you have a look at the following utilities.

[B]gparted 
gnome-disks 
mkusb[/B]

Please be careful when using partitioning and formatting tools, it is easy to make a mistake especially if you are in a hurry.

I tried gparted on another machine now it recognizes the card. I can't format it. The only option it gives is "New" which gives me a message that I should add a new partition table. So I used gparted option to do that but after its finished there is no change. I tried the add partition table process 3 times...

---

### Post by Autodave on 2020-01-22
Does it show a partition now?  If so, you need to now format it.  If it does not show a partition, then I believe it is time for a new card.

---

### Post by tea for one on 2020-01-22
> **miladost said:**
> I tried gparted on another machine now it recognizes the card. I can't format it. The only option it gives is "New" which gives me a message that I should add a new partition table. So I used gparted option to do that but after its finished there is no change. I tried the add partition table process 3 times...

I have experienced seemingly dead SD cards in the past and, sometimes, if the partition table is created in **gparted**, there is a reluctance for **gparted** to allow the formation of a partition. 

I have no idea why this occurs.

However, I have used **gparted** to create the partition table and then **gnome-disks** to prepare and format the partition.

Also, sometimes an **msdos** partition table will work and sometimes a **gpt** table - there does not seem to be a surefire route.............

I think that you will have to **carefully** jump around between the utilities until the SD card is working.

Good luck

---

### Post by miladost on 2020-01-22
> **Autodave said:**
> Does it show a partition now?  If so, you need to now format it.  If it does not show a partition, then I believe it is time for a new card.
It does not. The option to format in gparted is gray. I'm trying gnome-disks now.


> **tea for one said:**
> I have experienced seemingly dead SD cards in the past and, sometimes, if the partition table is created in **gparted**, there is a reluctance for **gparted** to allow the formation of a partition. 

I have no idea why this occurs.

However, I have used **gparted** to create the partition table and then **gnome-disks** to prepare and format the partition.

Also, sometimes an **msdos** partition table will work and sometimes a **gpt** table - there does not seem to be a surefire route.............

I think that you will have to **carefully** jump around between the utilities until the SD card is working.

Good luck
Okay I tried gnome-disks and it does seem to format I'll be trying slow format with zeros and the MBR option tomorrow (because the estimate is 10 hours to format)

---

### Post by tea for one on 2020-01-22
> **miladost said:**
> It does not. The option to format in gparted is gray. I'm trying gnome-disks now.



Okay I tried gnome-disks and it does seem to format I'll be trying slow format with zeros and the MBR option tomorrow (because the estimate is 10 hours to format)

MBR option? - do you mean **msdos** option for the partition table?

I wouldn't wait 10 hours for a format, why don't you quickly format in FAT32 and see if you can save a file?

Then you will quickly know if your card is alive or dead?

---

### Post by miladost on 2020-01-22
> **tea for one said:**
> MBR option? - do you mean **msdos** option for the partition table?

I wouldn't wait 10 hours for a format, why don't you quickly format in FAT32 and see if you can save a file?

Then you will quickly know if your card is alive or dead?
Using gnome-disks. The format function only gives me 3 options
-MBR/DOS partitioning scheme
-Gpt
-And no partitioning scheme

And quick or slow (with zeros) format

I already tried quick format with both MBR/DOS and gpt and it did nothing.

Edit: if you mean what I did in gparted, I selected MSDOS for the partition table but after it finishes there is no change whatsoever (to my knowledge) also gparted option to format is still greyed out after that.

---

### Post by CelticWarrior on 2020-01-22
With Gparted, after creating a new partition table, you need to select the unallocated space and actually create a partition. Then you can format it (or not).

But, again, all you're doing is very likely a waste of time. Slow format should not be used in flash memory because it wears it out even more and, in your case, the absurd estimation of 10 hours is a major red flag. It will failed way before that time though.

---

### Post by tea for one on 2020-01-22
> **miladost said:**
> Using gnome-disks. The format function only gives me 3 options
-MBR/DOS partitioning scheme
-Gpt
-And no partitioning scheme

And quick or slow (with zeros) format

I already tried quick format with both MBR/DOS and gpt and it did nothing.

Edit: if you mean what I did in gparted, I selected MSDOS for the partition table but after it finishes there is no change whatsoever (to my knowledge) also gparted option to format is still greyed out after that.

Here is an internet guide for gnome-disks - any help?

[https://linuxhint.com/gnome_disk_utility/](https://linuxhint.com/gnome_disk_utility/)

It shows how to double-check the validity your partition table.

---

### Post by miladost on 2020-01-22
> **tea for one said:**
> Here is an internet guide for gnome-disks - any help?

[https://linuxhint.com/gnome_disk_utility/](https://linuxhint.com/gnome_disk_utility/)

It shows how to double-check the validity your partition table.

It just stays at unknown. No partition table whatsoever... I'm kinda losing hope :(

> **CelticWarrior said:**
> With Gparted, after creating a new partition table, you need to select the unallocated space and actually create a partition. Then you can format it (or not).

But, again, all you're doing is very likely a waste of time. Slow format should not be used in flash memory because it wears it out even more and, in your case, the absurd estimation of 10 hours is a major red flag. It will failed way before that time though.
I think you are right. I was just in disbelief that a legit card, barely used could break beyond repair so so easily.

---

### Post by tea for one on 2020-01-22
> **miladost said:**
> It just stays at unknown. No partition table whatsoever... I'm kinda losing hope :(


I think you are right. I was just in disbelief that a legit card, barely used could break beyond repair so so easily.

That's a pity, I thought that we were slowly making progress.

There are some other utilities but they do not have a GUI - only usable in the terminal.

Sometimes responses from the terminal give more indications when commands/processes fail.

I have only used them very occasionally because I find the flags/options/syntax are difficult to master (especially with drives, partitions and formatting).

---

### Post by CelticWarrior on 2020-01-22
> **tea for one said:**
> There are some other utilities but they do not have a GUI - only usable in the terminal.

Sometimes responses from the terminal give more indications when commands/processes fail.

There are indeed but I disagree regarding usefulness in this case. Data recovery tools like Testdisk/Photorec would be something to try in a last attempt to recover data. Not the case here.

Knowing that the OP is only trying to format the microSD, Disks, Gparted or any similar would do the job perfectly (the 10 hours to format is a symptom). Formatting via CLI would have surely give some specific errors like I/O errors.


Here's what I think happened:

> The problems began when I used Rufus 2.18 on winXP to put Ubuntu 19  server on the micro SD. After it asked to format the card  there was  some error and then it didn't show up anymore.

Probably nothing (physical) happened to the card. Whatever the Rufus' error it was it resulted in a broken partition table.
Rufus 3.8 (?) is the current version, why use 2.18?

Years ago I had a similar problem with some Rufus I was testing in a Windows 10 VM - Rufus errors out in the middle of the copy & corrupts the destination drive partition table. At that time I chalcked it up to some problem with the VM  or the USB passtrought but now I wonder if wasn't the same version. Not sure but it was a 2.something. Anyway, formatting to FAT32 again was painless, no other problem with the drive (and it could be burned perfectly in the host Ubuntu with any tool).

The dead of the card likely happened during this ordeal:

> I had to resort to put it different cheap China gadgets like cameras and  stuff. Why more than one? Because it was only recognized on some  combinations of gadget+cable and when it was recognized it was  stuttering (disconnecting and reconnecting after a few seconds). **So I  plugging and unplugging the card alot**.

Emphasis on the bold part. 

There's a chance that card was defective but very very low. I think how and whit what it was used fried it in the end.

This could have been prevented, probably. Just formatting it in the original computer that has a SD reader/writer should have been enough to recover it as a normal mass storage device. Of course, it can't be done from the File Explorer, only in Disk management.

---

### Post by miladost on 2020-01-23
> **CelticWarrior said:**
> 

Probably nothing (physical) happened to the card. Whatever the Rufus' error it was it resulted in a broken partition table.
Rufus 3.8 (?) is the current version, why use 2.18?



Rufus broke something, but if it was the partition table why was I still able to use the card on an Ubuntu machine?

I used 2.18 because that's the last version that supports winXP

---

### Post by tea for one on 2020-01-23
> **CelticWarrior said:**
>  Data recovery tools like Testdisk/Photorec would be something to try in a last attempt to recover data. Not the case here..

I wasn't really thinking about data recovery tools but something like **gdisk**, to see if an error message may appear and help with further investigation.

[https://www.rodsbooks.com/gdisk/walkthrough.html](https://www.rodsbooks.com/gdisk/walkthrough.html)

Having said that, working with partitions/formats in the terminal is not easy and it would depend on the comfort level of the OP.

---

### Post by miladost on 2020-01-23
I forgot to give this information to you guys in the OP. It probably doesn't matter but I'll just give all the details.The Ubuntu 19.10 server that I tried to put on the micro SD with Rufus 2.18 was the 64 bit ARM version. 

I tried windows disk part, disk Management but those tools didn't detect the SD. I used windows XP and Windows 10 also multiple versions of Ubuntu.  Chmodding the SD to 777 because it was read-only (no effect). Using the line 
```
sudo dd if=/dev/zero of=/dev/sdx bs=1M count=1 
``` with gparted like said in here.
[https://askubuntu.com/questions/1035671/sd-card-has-no-partition-table-and-has-no-file-system](https://askubuntu.com/questions/1035671/sd-card-has-no-partition-table-and-has-no-file-system)


I'll try gdisks later as last resort.

---

