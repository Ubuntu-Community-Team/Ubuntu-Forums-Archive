---
title: "Need some help with next step in ubuntu!!!"
date: 2008-08-09
forum: Hardware
---

### Post by tankandre on 2008-08-09
I have a compaq presario v6000 which unfortunately runs vista premium sp1. After endless crashes and bsods, I looked and found Ubuntu. Ubuntu looks very promising, so i decided to give it a try through a live cd (hardy heron). But then I found out that my Broadcom 802.11 b/g Wlan would not let me use ubuntu through the live cd. I copied the error and went to the linux wireless drivers website, but I realized all the instructions were within ubuntu itself (using linux commands). I want to know what step should I take next. **Can I install ubuntu even though my wireless driver didn't work with the live cd?** I assume it will install properly, and that i will have to fix wireless later. But I might be wrong. I also read that Nvidia might cause some trouble.
I have Nvidia GeForce Go 6150. If it were for me, i would delete vista and switch to ubuntu right away. But I share this computer, and so it wouldn't be fair for me to decide which os to run. So dual booting is want i want to do. Wubi, I thought, will be my best bet, but will it display the same error message the live cd showed? "b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Dr...devicefirmware](http://linuxwireless.org/en/users/Dr...devicefirmware) and download the correct firmware (version 4)

How different is wubi from the real ubuntu experience? i just want to dual boot safely so that i can finally get rid of vista once everyone gets used to ubuntu. I also want to check if i should use a 32 bit or 64 bit ubuntu. My vista is a 32 bit os, but i have an AMD turion 64 mobile technology with 2.00 ghz. Thanx for reading through all of this.

---

### Post by dragonboss on 2008-08-09
I don't really know about wubi cos i havent tried it yet but you can install ubuntu without the wireless driver and later use lan or manually download the files and install it yourself or alternatively use your windows drivers with ndiswrapper but the "b43" means u have a broadcom 43xx wireless card (notoriously troublesome in ubuntu) but it comes with some drivers in the repository.

This post might help:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

Try this for the graphics card :
[http://ubuntuforums.org/showthread.php?t=880787&highlight=Nvidia+GeForce+6150](http://ubuntuforums.org/showthread.php?t=880787&highlight=Nvidia+GeForce+6150)

---

### Post by ThaRabbit on 2008-08-09
For the wireless card, please check here: (ndiswrapper method, this worked for me)
[http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

Option 2 for your wireless card to work could be this: (potentially less stable)
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

If you're using a WEP key and can't connect to your wireless via the network manager, please check here: (this is for after you get the ndiswrapper to work ;) )
[http://ubuntuforums.org/showthread.php?t=884996](http://ubuntuforums.org/showthread.php?t=884996)

Seeing as how you're using an AMD 64 bit, I believe you have to install some win32 libraries before you try the ndiswrapper method, the first link I gave you should epxlain everything.

Now, concerning this:
> Wubi, I thought, will be my best bet, but will it display the same error message the live cd showed? "b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Dr...devicefirmware](http://linuxwireless.org/en/users/Dr...devicefirmware) and download the correct firmware (version 4)

That error is caused due to a part of the wireless driver (automatically selected by ubuntu for you card) missing. Again, please check teh first link in my reply, it will clarify :)

Not to be complete:
You can safely use the dual boot option if you are familiar with drive partitioning. If you are not, I urge you to either create a question thread about dual boot and how to set it up. Or at least read into the topic using google. It WILL cause data loss if you do it wrong. As a beginner, wubi might be your best option for now.

---

### Post by tankandre on 2008-08-09
thx tharabbit and dragonboss. So basically, i use wubi to download ubuntu, and then from there download the appropriate drivers to enable my wlan. I just wanna be sure that i won't get any errors while i do that. Wubi partitions your hardrive automatically right?

---

### Post by kspncr on 2008-08-10
I believe wubi installs Ubuntu inside of Windows so there is no need to partition your hard drive. I haven't tried wubi myself, so I'm not 100% sure, but I think that's right.

---

### Post by ThaRabbit on 2008-08-10
There are some known limitations when using wubi. Please check the wubi subforums for more informations:
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

and the Wubi FAQ:
[http://ubuntuforums.org/showthread.php?t=396526](http://ubuntuforums.org/showthread.php?t=396526)

Now if you have partition software (not the ubuntu CD one, but paragorn partition manager for instance) and are feeling adventurous I would suggest to:

1. Shrink the windows partition (create at least 12 Gb of space)
2. Create and "extended" partition (as in, not primary)
3. Create a swap partition inside the extended partition (around your ram size)
4. Create an ext3 partition inside the extended partition (the rest of the free space)
5. apply changes.

Note that software like paragon partition manager is vista safe and will change your partitions without data loss.

Now boot from the ubuntu cd, choose install. 

When you get to the partitioning part, choose manual.

set the ext3 partition as "mount point /" leave the NTFS partition alone! Now install.

You will have a dual boot system with windows and ubuntu. Please note that you will have to update your MBR when you remove ubuntu again.

---

