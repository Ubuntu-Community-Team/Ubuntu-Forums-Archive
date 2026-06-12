---
title: "Help a newbee with basic instalation issues please"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by zblip2 on 2009-08-31
Hi

I would very much like to run ubuntu on my computer but lack the basic skills to install it.

Here are the difficulties I encounter:

I downloaded the CD (which won't fit on a CD obviously so why call it this way) kit (french version) from the french ubuntu site. I recieved a 4.5G compressed file. When I click on it it opens a ''winrar'' application. I uncompressed this file onto my hard drive and it created a 9G kit (which by the way will not fit on ONE instalation DVD). So I just burned a DVD with the 4.5G compressed file. This dvd doesn't work as a boot up disk probably cause the files are compressed.

Here are the questions I ask:

Must I burn TWO DVDs using the 9G uncompressed kit?

If this is the case, WHY doesn't the ubuntu site tell us right off the bat that we nead two DVDs?

Did I do something wrong while downloading?

And finally, why isn't there a simple basic step by step tutorial for ordinary people. Man! I cant understand why the Ubuntu people, after creating such a neat program, didn't take one hour to write a simple stupid 4 step installation guide for people who don't know sh!t about fancy computer vocabulary.... The hour spent writing this guide would multiply by 10 the number of ubuntu users, and would divide by ten the number of lost folks like me seeking advice.

Thanks for your help.

---

### Post by jerrrys on 2009-08-31
The english version of ubuntu fits on one cd and installs with ease,  may want to forget your french version if you find it too confusing...

---

### Post by Topsiho on 2009-08-31
I am not sure what you downloaded, and from what site. Might be a DVD with ALL Ubuntu files, which is quite unnecessary ... and might have to be dumped within a really short time when files on it get obsolete.

You should download the LiveCD from the official Ubuntu download site (and from nowhere else, you can there choose a mirror near you):

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

This is the CD that is used by every Ubuntu user in the world. American, Dutch, French, and so on. And just fits on a CD of 700 MB.

During the install you are asked what language you want to use, and some more questions (keyboard, timezone, names, password to use, partitioning, and questions I forgot).

And when the install is nearly complete the necessary files for your language are downloaded and installed. Voilà :)..

Topsiho

---

### Post by presence1960 on 2009-08-31
[http://www.ubuntu.com/products/whatisubuntu](http://www.ubuntu.com/products/whatisubuntu)

this is **_The Official Ubuntu site_**

---

### Post by stumbleUpon on 2009-08-31
The official installation guide

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

See these links for step-by-step instructions with pictures

[http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml)

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04)

you can find many more such links on google.

---

### Post by Swagman on 2009-09-01
You don't uncompress an ISO either.

Using a burning programme.. Probably NERO in your case .. or IMG burn..

Select create IMAGE... Don't just burn a file onto the cd.

Bobs your Mothers Brother.

---

### Post by anujpathania on 2009-09-01
Try this -

1. Download Ubuntu CD Image (<700MB) (English) from here - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download).

2. Burn it (Try ImgBurn) or mount it (Try Daemon Tools).

3. Click Install Inside Windows (using WUBI), also you can always dual boot but that is complicated procedure which I don't recommend for newcomers.

4. You can always add French translation package later after installation.

---

### Post by karamu on 2009-09-01
Welcome to Ubuntu- a smart move!

As previous posters have noted, you can simply download the standard English version and chose to add French support once you have installed the OS (your English is obviously good enough to navigate the installer program). The live CD image is the correct size to burn onto a CD.

Be sure that you are burning the image file (ISO) and not simply copying the ISO onto a blank disc- most CD burning software will have this as an option.

---

### Post by presence1960 on 2009-09-01
> **anujpathania said:**
> Try this -



3. Click Install Inside Windows (using WUBI), also you can always dual boot but that is complicated procedure which I don't recommend for newcomers.


That is absolutely not true. There are many guides and how to's to set up a dual boot. here are a few:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[https://help.ubuntu.com/9.04/switching/installing.htm](https://help.ubuntu.com/9.04/switching/installing.htm)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Wubi is not meant to be a permanent solution. it is meant to be a trial or test drive to see if one likes Ubuntu without having to partition your hard disk. See these for more info:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

Quote from the latter link:
Wubi (Windows-based Ubuntu Installer) is an official Windows-based free software installer for Ubuntu.

Wubi was born as an independent project and as such versions 7.04 and 7.10 were unofficial releases.[2] Since 8.04 the code has been merged within Ubuntu and since 8.04 alpha 5, Wubi can also be found in the Ubuntu Live CD.[1]

[COLOR="Red"]The goal of the project is to assist a Windows user unacquainted with Linux in trying Ubuntu[/COLOR] without risking any loss of information due to disk formatting or partitioning.[2] Wubi can also uninstall Ubuntu from within Windows.

It is not a virtual machine, but rather, it creates a stand-alone installation within a loopmounted device, also known as a disk image, like Topologilinux does. It is not a Linux distribution of its own, but rather an installer for Ubuntu.[1]

Users interested in directly installing to a dedicated partition, like a standard Ubuntu install does, without needing a CD should use UNetbootin instead.[3]

While Wubi does not install Ubuntu directly to its own partition (which the developers consider a feature) this can also be accomplished by using LVPM, the Loopmounted Virtual Partition Manager, to transfer the Wubi-generated Ubuntu installation to a dedicated real partition, including a bootable USB keydrive.[1] [COLOR="Red"]The advantage of this setup is that users can test the operating system and install the drivers before they install it to a dedicated partition (and avoid booting and functioning risks).[/COLOR]

Wubi adds an entry to the Windows boot menu which allows the user to run Linux. Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), as opposed to being installed within its own partition. This file is seen by Linux as a real hard disk. [1] Wubi also creates a swap file in the Windows file system (c:\ubuntu\disks\swap.disk), in addition to the memory of the host machine. This file is seen by Ubuntu as additional RAM.[1]

Note the text in red!

---

### Post by leorolla on 2009-11-10
Try Wubi, and see if you get what you want...

If you give up before your hardware etc will be configured, you can uninstall it easier and cleaner than you uninstall any W application.

If you see that your life is better with Ubuntu, then you can play with backup, super grup, partition, format etc. but at that point you won't give up anymore.

One year ago I gave up trying to make Ubuntu and my hardware be friends of each other. Now I am back, it took me already many many hours but worths. Recent Ubuntu plays well with your hardware.

This 4BG thing is crazy:

Download a ISO file like ubuntu-9.10-i386.iso or something like that with less than 700MB.

Download Daemon Tools Lite, mount the ISO and it will open as if it were a CD.

Ne t'inquetes pas à cause de la langue, pendant l'instalation on va te demander la langue, tu mets français et ça va marcher nickel.

---

