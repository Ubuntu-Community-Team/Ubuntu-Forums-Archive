---
title: "Partitions"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by bondmatt on 2009-06-19
I apologize for what may be a question regarding a very common topic but I worry about the consequences of making mistake.

I am planning to attempt to replace an existing installation of PCLinux with Ubuntu 8.04 LTS. PCLinux is dual booting with Vista using EasyBCD and GRUB for the bootloader.

My plan is to just put Ubuntu in where PCLinux was and still use GRUB/EasyBCD.

I am using a distro called CAELinux which is a common linux package (was PCLinux, switched to Ubuntu for 64bit) loaded with engineering software. I am keeping the PCLinux version on my 32bit laptop but I would like to switch the OS on the 64bit machine I own.

Can anyone give me even basic instructions on custom partitioning use the graphical Ubuntu installer? I plan to just have "/" and "swap" partitions. I really dont want to experiment with this.

Does anyone have any other advice for me?

Thanks in advance,
- Matthew Bondy

---

### Post by Sef on 2009-06-20
Read the [Illustrated Dual Boot]("http://members.iinet.net/%7Eherman546/index.html").

---

### Post by coffeecat on 2009-06-20
If the machine on which you've got PCLinuxOS and Vista has only / and swap partitions for PCLOS (as well as the Vista partition(s)), then the partitioning bit is quite straightforward. When you get to the partitioning stage in the installer, choose the 'manual' option rather than one of the 'guided' ones. Tell the installer to use the current / partition for / (you can also specify the filesystem you want), and it will pick the swap partition up automatically.

As far as grub/EasyBCD is concerned, I'm a little puzzled. I've no experience of EasyBCD, but a quick google tells me that you can set up Vista/Linux/otherOS multiboots with it using the Vista bootloader. Which tells me that you would use EasyBCD **or** grub, but not both. Or am I misunderstanding something?

Whatever - normally, the Ubuntu installer would simply replace and reinstall grub, autodetect the presence of Vista and set up a dual-boot Ubuntu/Vista menu for you. If you don't want grub stage 1 installed to the mbr, you can click on the 'advanced' button on the last screen just before the installer does its stuff (but after it has reformatted your / partition iirc). When you click on 'advanced', you can specify a partition for stage 1 instead of the MBR, or tell it not to install grub at all - again iirc.

Lastly, if you want to do some tinkering with your partitioning layout before you start the installer, go to System > Administration > Partition Editor in the live desktop for the Gparted partitioner. But don't try to resize the Vista C: partition with Gparted - [Not if you want to be able to boot into Vista again, that is]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/"). :(

---

### Post by -kg- on 2009-06-20
I agree totally with coffeecat.  If you're just replacing pclinux with Ubuntu, install it using the manual partitioning selection and mark the mount points of the existing partitions.  The installer will take care of the installation.

As far as the boot loader, I personally would just go with Ubuntu's GRUB installation.  It basically works the same way as BSD and will auto-detect any other OS that you have installed and include it in the boot menu, including Vista.

Of course, I never tried using GRUB to dual-boot Ubuntu with Windows 3.1, so if you're using that, ***you're on your own!*** :lolflag:

---

### Post by bondmatt on 2009-06-20
I should add that I am quite the linux novice. I went as far as the custom partition stage in the graphical installer and there was only a big blank area where the PCLinux / and swap partitions were.
 
How do I go about recreating those partitions? It seemed the only way was to set the size and pick the type of partition from a drag down box but something in the titles of that dialogue box concerned me.
 
I would prefer to pull out GRUB as an intermediate bootloader (which is how it was set up). However, Im not sure how to use EasyBCD to include safe modes, etc. for linux in the first bootloader. If I have to leave it as is (in terms of bootloader) I can accept that.
 
Thanks for the support,
- Matt Bondy

---

### Post by bondmatt on 2009-06-20
I thought the guide mentioned by sef would be one that I had already looked at but it was perfect. It covers the use of the graphical installer disk partitioner very thoroughly.


Thanks for the link to that,
- Matthew Bondy

---

