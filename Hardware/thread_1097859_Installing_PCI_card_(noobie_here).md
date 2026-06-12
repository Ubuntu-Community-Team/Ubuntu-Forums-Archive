---
title: "Installing PCI card (noobie here)"
date: 2009-03-16
forum: Hardware
---

### Post by ronaldo07 on 2009-03-16
Hi guys

I am very new to linux world. I am trying to install PCI data acquisition card on to my PC.

I am running Ubuntu 8.10 (installed few days back)

Here are the instruction for installing ( got it from manufacture)

> Installing Advantech DAQ Device Linux Driver

This Advantech DAQ Device Linux Driver Package is developed for Linux kernel version 2.6.x (for PCI and USB), and kernel version 2.4.x (only for PCI). The driver supports four platforms: Red Hat Enterprise Linux 4, Fedora Core 6, Debian 4.0 and Red Hat Linux 9.

&#12288;

Read this document carefully, as it explains how to install the device driver, how to develop with this toolkit and what to do if anything goes wrong.
INSTALLING :

 

Note: If the driver was installed before, please remove it from the system firstly.

For Red Hat Enterprise Linux 4, Fedora Core 6, and Red Hat Linux 9, please type the following commands:

#rpm -e advdaq

For Debian 4.0, please type the following commands:

#dpkg -r advdaq

 
1. Get the driver package according your platform. Type the following commands:

For Red Hat Enterprise Linux 4, Fedora Core 6, and Red Hat Linux 9:

#rpm -ivh advdaq-<version>.<platform>.i386.rpm

For Debian 4.0:

#dpkg -i advdaq_<version>_i386.deb

2. To install the driver modules and make device files, please type:

#insmod /usr/src/Advantech/DAQ-<version>/modules/advdrv_core.ko
#insmod /usr/src/Advantech/DAQ-<version>/modules/which_device_driver_you_want_to_insmod.ko
  

When I run > #insmod /usr/src/Advantech/DAQ-<version>/modules/advdrv_core.ko

I get error
> insmod: error inserting '/usr/src/Advantech/DAQ-1.03.0001/modules/advdrv_core.ko': -1 Invalid module format

I noticed one thing that manufacture has not mentioned Ubuntu in installation manual. but only Debian, Fedora, Red hat

Does it mean it will not work on Ubuntu ??
What do I need to do to make it work on my Ubuntu system ?

I really don't want to install another Operating system :(

---

### Post by cariboo on 2009-03-16
You may want to go to the devices Manaufacturers web site and see if there a newer drivers.

Jim

---

### Post by ronaldo07 on 2009-03-16
This is the most recent Driver.

Do you think I can use Debian driver for Ubuntu ??
Because I thought Ubuntu is based on Debian

---

### Post by ronaldo07 on 2009-03-17
Is it not possible  ?
I can't believe that I am not able to get any solution for it.

No offense but using new hardware in Ubuntu sucks

---

### Post by mrtomservo on 2009-03-17
Generally speaking i've had no problems installing Debian specific software on Ubuntu.  Usually an "Invalid module format" means it was compiled for an different kernel than you're using.  Could you provide the part number for the pci card you're using?  

I don't see why you can't get this working with Ubuntu.  Worst case scenario you might have to compile the drivers from source, provided the company would provide you with the source that is.  You may have to contact them and explain the situation.

But post the PCI card model number and i'll see what I can find.

---

### Post by ronaldo07 on 2009-03-17
Thanks for your reply
I am trying to install PCI-1751 (Advantech)

This is the url to download driver

[http://support.advantech.com.tw/support/DownloadSRDetail.aspx?SR_ID=GF-1HXN7](http://support.advantech.com.tw/support/DownloadSRDetail.aspx?SR_ID=GF-1HXN7)

I will call manufacture again. May be this time I get nicer person who can send me source code :D
But I won't count on it.

---

### Post by mrtomservo on 2009-03-17
No problem, companies that DO offer linux drivers.. in my experience about 50 percent of the time they won't work right without tweaking.  I blame the companies, and not the distro.  :)  

I'm working on it now, I'm running 8.04 and not 8.10 but I get the same error as you about the invalid modules format.  Gonna do some digging and see what the deal is. :)

Well, it looks like there's two solutions.  The best solution would be to compile from source, if the source can be found.  The second best solution would be to try and install an older kernel to match what it was compiled for. (trying to figure that one out still)

According to one of their message boards they generally frown on giving out the source code unless you bought 1000+ items.  Debian 4.0 is pretty darned old.  From what I can tell the latest kernel for Debian Etch 4.0 is 2.6.18.  So that seems to basically line up with Ubuntu 6.06, which has 2.6.15.  It would seem that while the manufacturer's website says it supports kernel 2.6.* that it might indeed be 2.6.18 or lower, making it incompatible with Ubuntu versions higher than 6.06.  That's pretty dated driver support if you ask me.  

So here's what i've found, there might be something you can do with these drivers as your part is listed: [http://www.comedi.org/doc/x1781.html]("http://www.comedi.org/doc/x1781.html")

Here's the link to the forum where I got the lack of source code availability info: [http://www.adamforum.com/viewthread.php?tid=389]("http://www.adamforum.com/viewthread.php?tid=389")

Sorry I don't have better news.  Realistically if you don't want to spent a very long time playing with it, you'll probably have to install Debian 4.0 Etch.  Don't know if you're familiar with it, but it's pretty similar to Ubuntu.  A lot less hardware support than Ubuntu in my experience though.  Ironic, really.  

Have you considered dual booting?  Maybe an Ubuntu/Debian setup?

---

### Post by ronaldo07 on 2009-03-17
Thanks alot for doing all this research for me.
I really appreciate it.

Yeah I think Debian is the way to go for me.
I am not familiar with Ubuntu that much, so switching won't change anything for me. I need to learn Debian instead Ubuntu :))

Thanks for all your help.

---

