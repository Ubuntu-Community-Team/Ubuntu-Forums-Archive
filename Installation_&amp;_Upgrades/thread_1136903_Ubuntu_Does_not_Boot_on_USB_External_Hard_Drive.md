---
title: "Ubuntu Does not Boot on USB External Hard Drive"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Seth92 on 2009-04-25
I recently installed the new Ubuntu 9.04 on my external hard drive.  I partitioned the drive so I would devote 100 Gigs to Ubuntu and 150 Gigs to NTFS for external storage for Windows Vista.  During installation, I partitioned the drive using the guided partitioner and chose to install the boot loader onto the external hard drive, sdb, as opposed to the internal hard drive.  The installation completed "successfully".  I did not realize by doing so the external USB Hard Drive would not boot.  I even went into GPartitioner and changed the boot from the NTFS to Linux ext3 with the LiveCD.  There is a yellow sign with an exclamation point in it to the right of my NTFS partition.  I changed the boot order in my bios to USB-HDD, CDROM, then Harddrive.

I do not wish to have a dual boot system.  I wish to have this external hard drive as a portable operating system and portable storage for any computer I wish to use it on.  

Any suggestions are welcome, and yes I am a noob to Linux.  I have installed successful dual-boot systems in the past with Ubuntu, but this is a much more difficult task.  (I'm not afraid to use the terminal and I can boot the LiveCD and the external hard drive is mounted)
:confused:

---

### Post by holyskeleton on 2009-04-25
i donno if you can just install the desktop edition as a portble edition. softwares usually have a portable edition and sometimes they are different from the standard packages. and an OS is likely to be like that.

---

### Post by Seth92 on 2009-04-25
I assumed if I installed the OS completely on the external hard drive all I had to do was change the boot order, because it would stand alone.

---

### Post by aikiwolfie on 2009-04-25
The last time I installed Linux to an external hard drive using the standard installation procedure I had to physically disable my internal hard discs first by unplugging them. After the installation is complete, switch off your PC and plug you hard drives in again.

If you do it that way the external drive should boot fine. You can then use the BIOS boot menu to boot from the external USB hard drive any time you feel like it. The best part is, the rest of your system remains unchanged.

---

### Post by Topsiho on 2009-04-25
See

[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)

Then find on [www.ubuntu.com](www.ubuntu.com) how to install 9.04 on a USB-stick, in order to install this on a netbook, such as the Acer Aspire One.
I used the command line method to do this, as this is very easy to do, if you follow the instructions EXACTLY...

That is: use your external USB harddisk as a live CD, with the difference that you can write on it.

Success :)

Topsiho

---

### Post by Topsiho on 2009-04-25
I think you should follow aikiwolfie's advice as he has actually done this :)

Topsiho

---

### Post by aikiwolfie on 2009-04-25
The Live USB option will work. But you'll be on a Live user session everytime you boot. I've never tried to create a new user in a live session. So I don't know if it works.

The method I mentioned above does work and in my opinion produces better results. But it's cumbersome. The Live USB option is a little more elegant. But your on a live user session with full privilages.

---

### Post by Seth92 on 2009-04-25
But, I have already installed the operating system on a 250 Gig hard drive.  150 Gigs as NTFS as external storage and 100 Gigs for Ubuntu.  How would I go about fixing it, seeing as Ubuntu already "successfully" installed on that partition.

---

### Post by Seth92 on 2009-04-25
But, I have already installed the operating system on a 250 Gig hard drive.  150 Gigs as NTFS as external storage and 100 Gigs for Ubuntu.  How would I go about fixing it, seeing as Ubuntu already "successfully" installed on that partition.

---

### Post by aikiwolfie on 2009-04-25
How far into the boot process do you get?

---

### Post by Seth92 on 2009-04-25
I have Vista on my internal drive and I know Ubuntu is installed onto the external drive because when I boot my live CD is see the OS files.  Even though my boot order is USB-HDD, CDROM, then Hard Drive, it boots Vista unless there is a bootable CD.  Therefore, it doesn't boot at all.

(P.S. I have AHCI enabled, if that plays an important role)

---

### Post by aikiwolfie on 2009-04-25
What you need to do is boot to the live CD and install GRUB to the USB hard drive. This link might help.

[http://www.freesoftwaremagazine.com/articles/grub_intro/]("http://www.freesoftwaremagazine.com/articles/grub_intro/")

---

### Post by meierfra. on 2009-04-25
Sound like a problems with your Bios. Make sure that booting from a USB drive is enabled in the bios.


To make sure that grub is configured correctly, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post  (use the code tags)

---

### Post by Seth92 on 2009-04-26
I made sure the boot order in my BIOS was correct, and indeed it was.  I will try to do the boot action script in a little while.

---

### Post by Seth92 on 2009-04-26
In addition to making sure that the boot order in my BIOS was correct, I also would like to note that GRUB is installed into the grub folder of the boot folder (/boot/grub).  All of the necessary files seem to be there.

---

### Post by aikiwolfie on 2009-04-26
The fact that grub is installed doesn't mean it's configured properly. I've been through this issue my self. The only way I could get this to work was to disconnect my internal hard drives and do the installation as I said before.

I understand you've installed it once already. But sometimes the only way to fix something is to redo it.

I'm all out of ideas on this so good luck.

---

### Post by Seth92 on 2009-04-26
Thanks, that worked.  I guess that is just an issue with the new 9.04.

---

### Post by KI4CLZ on 2009-04-26
> **Topsiho said:**
> See

[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)

Then find on [www.ubuntu.com](www.ubuntu.com) how to install 9.04 on a USB-stick,...

Topsiho

Where do I find this information... specifically... The ubuntu site has it's own learning curve and is a chore to get any specific answers, if at all...

a walk thru would be nice...

Thanks, 
Frustrated in 'Bama

---

### Post by TBerk on 2009-04-28
> **KI4CLZ said:**
> Where do I find this information... specifically... The ubuntu site has it's own learning curve and is a chore to get any specific answers, if at all...

a walk thru would be nice...

Thanks, 
Frustrated in 'Bama

OK, lets try this because I'm interested also...

From the Wiki entry:
> 
[Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_(operating_system)") (can be installed directly to a flash drive or USB external Hard Drive manually or using tools like [usb-creator]("http://en.wikipedia.org/wiki/Usb-creator"), [UNetbootin]("http://en.wikipedia.org/wiki/UNetbootin"), or [cd2usb]("http://en.wikipedia.org/wiki/Cd2usb"))


Hey, wait, lookee here:

[HOW TO make a USB Disc with Ubuntu LiveCD and Super Grub Disc in it]("http://ubuntuforums.org/showthread.php?t=575406")

The question may remain, does it make a difference between a USB based flash drive vs a USB based IDE, etc Hard Drive though.

I hope this furthers an answer along.


TBerk

---

