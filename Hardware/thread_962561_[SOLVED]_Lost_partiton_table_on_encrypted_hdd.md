---
title: "[SOLVED] Lost partiton table on encrypted hdd"
date: 2008-10-29
forum: Hardware
---

### Post by jdavis72 on 2008-10-29
I have left my desktop running for a few weeks without rebooting, during which I have installed all updates (even when it said I should reboot). This morning I rebooted to to find my partition table gone and the hdd not bootable. Running a live cd and then gparted showed the entire drive unallocated. Then running ```
testdisk
``` showed an incorrect (previous) table layout. The way my sys should be is: I installed Ubuntu 8.04 with a fully encrypted drive (save for 200MB for /boot). Unfortunately, I was in the middle of resetting my external hdd, so I have no backup. How can I get my data back from my desktop? Thanks in advance!

Jeremy

---

### Post by JMorg on 2008-10-29
Well, it seems as long as your issue only lies in an unallocated partition table then your data should be able to be backup up. The method I would use is to either run a bootable disc or pull your hdd and place it into an enclosure to turn it into an external drive and plug it into a machine that is running in a linux environment so you can see the data. From there you "Should" be able to pull the data and back up important files that are necessary. Afterwards reinstall linux and I would recommend making:  /(root), /home, /var, /bin  : partitions in case of os corruption in the future for possible easier data recovery.

---

### Post by jdavis72 on 2008-10-29
> **JMorg said:**
> Well, it seems as long as your issue only lies in an unallocated partition table then your data should be able to be backup up. The method I would use is to either run a bootable disc or pull your hdd and place it into an enclosure to turn it into an external drive and plug it into a machine that is running in a linux environment so you can see the data. From there you "Should" be able to pull the data and back up important files that are necessary. Afterwards reinstall linux and I would recommend making:  /(root), /home, /var, /bin  : partitions in case of os corruption in the future for possible easier data recovery.
But how do I do this with an encrypted drive? If it was not encrypted, I understand how to do it. But, except 200MB for /boot, the entire drive is encrypted (with one partiton for /, and the other for swap). Thanks in advance!

Jeremy

---

### Post by JMorg on 2008-10-29
Hmm that brings up a good point as far as the encryption goes. I will do some research and see what I can come up with. I have previously heard mixed reviews on whether data encryption is recoverable or not if incremental data backups are not performed. I will do my best to see what I can come up with for ya. 

In the meantime, mind if I ask whether or not this is your home personal PC? because If so I am curious why you used data encryption :). Password encryption is now stored in /etc/shadow and password cracking is not nearly as possible as it once was, but I am all ears!

---

### Post by jdavis72 on 2008-10-29
> **JMorg said:**
> Hmm that brings up a good point as far as the encryption goes. I will do some research and see what I can come up with. I have previously heard mixed reviews on whether data encryption is recoverable or not if incremental data backups are not performed. I will do my best to see what I can come up with for ya. 

In the meantime, mind if I ask whether or not this is your home personal PC? because If so I am curious why you used data encryption :). Password encryption is now stored in /etc/shadow and password cracking is not nearly as possible as it once was, but I am all ears!
Yes, this is my home pc. Long story short, I live in a bad neighborhood, and am always afraid of a break-in. This desktop has all of my personal and former business financial data, plus lots of other personal data (pics, vids, etc.). Thus, if anyone steals this computer, I know they'll never get to the data, or any other info from swap, etc. that I don't know about. That's also why I have an external hdd that is used exclusively as an encrypted backup (it's stored in a safe). However, I was in the middle of writing random data to the external hdd and prepairing it for encryption before I did a new rsync, when I rebooted the desktop. I don't think the data is corrupted, just that the partition table is gone (how, I don't know). Booting into a live cd with gparted, all I see is one big unallocated disk. No /boot partition (which should be readable) or anything. Before I rebooted, the os was working fine. I never received any error messages. The only thing I can say is, is that it has been up for a few weeks, all while I have been installing updates to it (at some point, it required me to reboot, but I never did before installing more updates).

---

### Post by JMorg on 2008-10-29
Ok, here we go. You may have already read this article but [HTML]https://help.ubuntu.com/community/DataRecovery[/HTML] may help you out if you haven't. In particular I found this portion to be a great possibility, because it will pull the data on the drive (I don't see why it wouldn't even if the data is encrypted because it seems like a brute way to grab the data from beginning to end). 

> GNU Parted

Run Parted from the command line to recover your partition.

When changing the partition table on your hard drive, you must ensure that no partition on the disk is mounted. This includes swap space. The easiest way to accomplish this is to run the live cd. Parted is installed on the base Ubuntu system. Once at the desktop, open a terminal and run_:

sudo swapoff -a

Next run parted and tell it to use the device in question. For example, if your /dev/sda drive is the drive from which you want to recover, run:

sudo parted /dev/sda

Then, use the rescue option:

rescue START END

where Start is the area of the disk where you believe the partition began and END is it's end. If parted finds a potential partition, it will ask you if you want to add it to the partition table. 


The article later states that recovery can be performed by remounting that image that you pulled. I would assume that mounting an encrypted drive would work as long as you hold the entirety of the drive due to the nature of encryption/decryption. Therefore the decryption keys would transfer over on the image of the data allowing for the encryption to be broken for you to see all of your data.

I am curious if this works out so be sure to let me know if you don't mind!

---

### Post by JMorg on 2008-10-29
> **jdavis72 said:**
> Yes, this is my home pc. Long story short, I live in a bad neighborhood, and am always afraid of a break-in. This desktop has all of my personal and former business financial data, plus lots of other personal data (pics, vids, etc.). Thus, if anyone steals this computer, I know they'll never get to the data, or any other info from swap, etc. that I don't know about. That's also why I have an external hdd that is used exclusively as an encrypted backup (it's stored in a safe). However, I was in the middle of writing random data to the external hdd and prepairing it for encryption before I did a new rsync, when I rebooted the desktop. I don't think the data is corrupted, just that the partition table is gone (how, I don't know). Booting into a live cd with gparted, all I see is one big unallocated disk. No /boot partition (which should be readable) or anything. Before I rebooted, the os was working fine. I never received any error messages. The only thing I can say is, is that it has been up for a few weeks, all while I have been installing updates to it (at some point, it required me to reboot, but I never did before installing more updates).

Ah I see, well I completely understand now! I would, however, recommend that instead of running as an entire encrypted drive, that within the OS you create an encrypted virtual drive. For example a program known as "Truecrypt" will allow you to create a "virtual drive" and you can even set the type of encryption and key so that you have to mount the drive and decrypt it each time you want to access the data. It may seem redundant, but in a case like you're in now it could come in handy because backing up the information is as easy as backing up the unmounted file (Shows up as an individual file before mounted).

---

### Post by jdavis72 on 2008-10-29
> **JMorg said:**
> Ok, here we go. You may have already read this article but [HTML]https://help.ubuntu.com/community/DataRecovery[/HTML] may help you out if you haven't. In particular I found this portion to be a great possibility, because it will pull the data on the drive (I don't see why it wouldn't even if the data is encrypted because it seems like a brute way to grab the data from beginning to end). 




The article later states that recovery can be performed by remounting that image that you pulled. I would assume that mounting an encrypted drive would work as long as you hold the entirety of the drive due to the nature of encryption/decryption. Therefore the decryption keys would transfer over on the image of the data allowing for the encryption to be broken for you to see all of your data.

I am curious if this works out so be sure to let me know if you don't mind!

Thanks for the help. I understand how I can copy the entire drive to another disk. But my problem is how to get into it and decrypt it. I don't know what sectors, etc. the partitions reside on, much less how I would edit that info for a partition table. Testdisk and gpart have returned incorrect data (it sees where vista was installed, along with the old swap partition, however, I since then reformatted, and installed Ubuntu 8.04 as the only os, using the alt disc, and encrypting the entire drive.). I'm afraid I'm out of luck. Without a way to actually de-crypt the data, I'm screwed. I wish I knew what happened in the first place. Thanks anyway.

Jeremy

---

### Post by jdavis72 on 2009-01-03
Sorry I haven't posted to this in a while. This problem came up as I was moving to a new city, and job. I actually solved it in November. Basically what I did was purchase a new 500GB internal SATA hdd, swapped it out with my old one, reinstalled Ubuntu exactly as before, then copied the MBR layout, reinstalled the old drive and using a live cd, wrote the new MBR layout to the old drive. That fixed it to where I could then mount the old drive, and get to my data.

How I lost my original layout, I don't know. I never messed with grub before that. Anyway, that fixed it. Thanks for your help anyway. It's much appreciated.

Jeremy

---

