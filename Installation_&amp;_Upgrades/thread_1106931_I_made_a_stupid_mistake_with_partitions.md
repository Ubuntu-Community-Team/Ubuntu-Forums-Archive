---
title: "I made a stupid mistake with partitions"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by Flexico on 2009-03-26
OK, I started with a Windows XP installation and installed Ubuntu next to it for dual-booting, and it worked fine, but after a time I decided I didn't want Ubuntu on that drive anymore, so I deleted the Ubuntu partition and expanded the Windows partition to fill the drive. Now when I try to boot from it, it tries to use GRUB but returns Error 22.

How can I restore the Windows OS without losing my files?

---

### Post by Zimmer on 2009-03-26
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Read down a fair way to either using the Windows XP Recovery Console , or just below it, how to use ms-sys program to restore the MBR.

Sorry, got to dash....
Regards

---

### Post by Deathray on 2009-03-26
Sorry! We don't support uninstalling Ubuntu, especially if you are planning on using Windows :b. Just kidding here is a simple guide that I am sure will fix your problem :) Don't hesitate to reply if you need help.
[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm]("http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm")

---

### Post by Flexico on 2009-03-26
> **Zimmer said:**
> [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Read down a fair way to either using the Windows XP Recovery Console , or just below it, how to use ms-sys program to restore the MBR.

Sorry, got to dash....
Regards

Thanks! I ran Ubuntu from my disk I burned from the iso image, but when I run the installer command, it at first appears to be working, then says,
"E: Couldn't find package ms-sys".

I tried to run ms-sys, but it says it's an unknown command (ie, didn't install). Heh...now what? Do I need to run Ubuntu from an actual hard drive?

===============================
> **Deathray said:**
> Sorry! We don't support uninstalling Ubuntu, especially if you are planning on using Windows :b. Just kidding here is a simple guide that I am sure will fix your problem :) Don't hesitate to reply if you need help.
[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm]("http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm")

Ha ha ha, I'm not totally getting rid of Ubuntu, I plan to run it from an 8Gig flash drive, with the hard drive purely Windows, simply because it's becoming a hassle. :\ (I'm trying to do too much, doubtless.)

I'll try this if the thing the other guy said doesn't work. ;)

---

### Post by Zimmer on 2009-03-26
If you read Herman's page carefully you will note you must boot the live CD for Ubuntu (not install it!)  open the Terminal app
and run the command

sudo apt-get install ms-sys

Before you run ms-sys, you will probably want to check first and see which hard disk is which, so you can work on the right MBR, run
 'sudo fdisk -lu' for that,
sudo fdisk -lu
From the output from the above command, you should be able to tell which of your hard drives are  called '/dev/sda', and which one is '/dev/sdb' and so on.

sudo ms-sys -m  /dev/sda

Where: /dev/sda is the MBR of the hard drive you want to boot Windows from again.

---

### Post by Flexico on 2009-03-26
> **Zimmer said:**
> If you read Herman's page carefully you will note you must boot the live CD for Ubuntu (not install it!)

I am running the OS from the CD, but when I execute the said command "sudo apt-get install ms-sys" (I tried it several times), it says it "couldn't find package ms-sys".

---

### Post by aadipotter on 2009-03-27
> **Flexico said:**
> OK, I started with a Windows XP installation and installed Ubuntu next to it for dual-booting, and it worked fine, but after a time I decided I didn't want Ubuntu on that drive anymore, so I deleted the Ubuntu partition and expanded the Windows partition to fill the drive. Now when I try to boot from it, it tries to use GRUB but returns Error 22.

How can I restore the Windows OS without losing my files?

I too hv the same problem.
Now, i installed 8.04 by booting from cd and then installing it.
Everything worked fine until I tried to mount the CD/DVD volume and it said "Could not mount the volume".

Next, I restarted the system and tried to access Win XP and it gave a stop error with a blue screen, saying windows could not be opened.

Any suggestions?

---

### Post by Rainbow Road on 2009-03-27
I have had to replace my grub with the windows MBR a few times due to removing Ubuntu (although on a separate hard drive). Every time I boot from Windows XP disk, and select R to use recovery console. You need to select your windows drive and then type fixmbr

Hopefully when it reboots it should go straight into Windows.

---

### Post by Flexico on 2009-04-05
Thanks much, this has been helpful, I got it working. :)

---

