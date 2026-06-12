---
title: "Ubuntu won't boot from USB Drive."
date: 2008-11-30
forum: General Help
---

### Post by Scythe X10 on 2008-11-30
Hey, I'm very new to Linux and I wanted to give it a try. Since I will be learning soon in my college course I will be taking why not give it a head start. Well I wanted to install it on a USB flash drive. I looked it up and came across Ubuntu, and found out you can install it on a flash drive. So I burn the LiveCD and boot it, All goes well, I install Ubuntu using the USB boot maker application provided with the Ubuntu live cd.. All goes well and it tells me everything was done properly. So I turn on my computer, boot from the USB flash drive and i get a black screen with a big B on the top left and that's it. Can't type nothing or anything.

The Flash drive I'm using is a Scandisk Cruzer Micro 8GB thumb drive. I checked the Ubuntu .ISO with that MD5SUM app, all matched. Disk was verified.

Machine - HP M8400F

AMD Phenom 9600 2.3 quad
Nvidia 8500GT 256MB GPU
3GB ram

Any other info needed I will provide.

I'm very interested in Linux mainly because of the fact that you have control over so much, and using Ubuntu via the CD was a very nice experience and I hope to be using it soon. If it comes down to it I will install Ubuntu on my second HDD or make a dual boot if possible. But I would very much like to get the flash drive method working.

Thanks in advance.

---

### Post by Scythe X10 on 2008-11-30
Alright well I'm going to reformat that USB drive with the FAT32 file system using Windows and then try reinstalling Ubuntu on it using the Ubuntu Live Cd applicated USB boot creator or whatever the name is. This time i will choose 2GB with that slider for documents and what not. I did a little research and it seems that if you use over 2GB with the slider it becomes a pile of junk filled errors. Hopefully this will work. I'm actually off right now so I'll post back within 6-8 hours. If you have any insight to this issue please share :)

---

### Post by C.S.Cameron on 2008-11-30
I've had best luck with large flash drives letting UNetbootin format and install, erasing the files, then installing with usb-creator to get a persistent install.

---

### Post by SVWander on 2008-11-30
> **C.S.Cameron said:**
> I've had best luck with large flash drives letting UNetbootin format and install, erasing the files, then installing with usb-creator to get a persistent install.

Does the USB-Creator allow the user to actually install Ubuntu on the USB drive? In other words can it become a complete installation where you can save files (to the USB drive) have bookmarks saved and etc? 

Tim

---

### Post by Scythe X10 on 2008-11-30
> **C.S.Cameron said:**
> I've had best luck with large flash drives letting UNetbootin format and install, erasing the files, then installing with usb-creator to get a persistent install.

I'm going to try this. By erasing the files, Do you mean just straight up deleting ( windows ) or using another method?

---

### Post by SVWander on 2008-12-01
> **Scythe X10 said:**
> I'm going to try this. By erasing the files, Do you mean just straight up deleting ( windows ) or using another method?

Hi Sorry I butted in on your post. You are using an Ubuntu CD Live to install Ubuntu into a USB drive OR or you trying to install the CD Live on a USB drive? I am trying to do the former and not having much luck. Doing the latter should be very easy if you are using the newest version of Ubuntu. Find Create a USB Startup Disk in the systems menu. Actually I am using Kubuntu so I am not sure exactly where it is. But if you look you will find it. I created a startup USB disk in less than 30 minutes using a 4G memory stick. I rebooted hit F12 selected to boot from my USB port and it booted into a Live session.

However, that isn't what I wanted to do. I wanted to be able to use the USB drive to save settings and such. So far I haven't been able to figure that one out. There is, however a place where I have seen something like that advertised. So I believe it is possible.

Let me know if that solves your problem. 

Tim

---

### Post by Scythe X10 on 2008-12-01
I'm trying to make a Ubuntu OS USB. So I can boot into the OS using that flash drive from any computer capable of booting from a USB flash drive. I'm just having so much trouble actually doing it. I can never start the OS from the flash drive on any computer. It always comes up with a black screen with a "B" and does nothing. If someone can provide a step by step guide on how to do this please do. I followed various ones with the same result. My computer is not at fault because it won't boot from any machine.

Edit - It's also possible I'm doing something wrong. I'm very new to this whole thing. I've never had ANY prior experience with creating a Bootable OS from a flash drive. ( besides a Win98DOS ) But I'm using the USB Start creator to try and make it. I REALLY want to get this working because Linux seems like a very nice OS, Very secure, stable and best of all I have control over so much as well as having programs that i really want that don't run on anything but Linux. So I'm really, really wanting to get this done. Also, that USB creator only makes a Install live CD!? Most of the guides i read said it will install a fully bootable Ubuntu?

---

### Post by SVWander on 2008-12-01
> **Scythe X10 said:**
> I'm trying to make a Ubuntu OS USB. So I can boot into the OS using that flash drive from any computer capable of booting from a USB flash drive. I'm just having so much trouble actually doing it. I can never start the OS from the flash drive on any computer. It always comes up with a black screen with a "B" and does nothing. If someone can provide a step by step guide on how to do this please do. I followed various ones with the same result. My computer is not at fault because it won't boot from any machine.

Edit - It's also possible I'm doing something wrong. I'm very new to this whole thing. I've never had ANY prior experience with creating a Bootable OS from a flash drive. ( besides a Win98DOS ) But I'm using the USB Start creator to try and make it. I REALLY want to get this working because Linux seems like a very nice OS, Very secure, stable and best of all I have control over so much as well as having programs that i really want that don't run on anything but Linux. So I'm really, really wanting to get this done. Also, that USB creator only makes a Install live CD!? Most of the guides i read said it will install a fully bootable Ubuntu?

I have installed the latest version of Ubuntu in a Corsair USB drive. I have used two methods. One is using the method you have already mentioned. The other is using UNetbootin, Universal Netboot Installer. It is available from SourceForge.net. It will it all for you. But I did have a problem with UNetbootin "seeing" my USB drive. I had to select it from the drop down menu. That can be somewhat dangerous. Be sure you are installing it to the right drive! In Ubuntu using the terminal run fdisk -l. It will list the drives on your machine.

I will say using the last method the computer ran slowly. Using the other USB startup drive seems to have been a little faster. I still am having trouble figuring out how to save my settings and bookmarks.

Here is another link to a Ubuntuforum question on this subject. [http://ubuntuforums.org/showthread.php?t=964572&highlight=usb+drive+installs](http://ubuntuforums.org/showthread.php?t=964572&highlight=usb+drive+installs)
It gives a lot of information that might be helpful to you. 

Good luck! And have fun . . . 

Tim

ps Have you downloaded ubuntu to your desktop? I found that much easier than trying to run it from my CD-ROM. tm

---

### Post by odzx on 2008-12-02
Same problem here. I've already tried unetbooting and got the same results.
I tried to reformat the usb drive using gparted, formating it to fat32 and adding the boot flag... did not do the trick. still getting the black screen saying the disk is not bootable.
ones I have rebooted from the HD and open the usb drive with nautilus, it says "the media contains software" and offers to open the autorun prompt, as if it is a regular LiveCD.:confused:

p.sI also tried booting a different computer with the drive... same result.](*,)

---

### Post by Scythe X10 on 2008-12-05
Still having the same issue. Any insights please? Still very interested in Ubuntu.

---

### Post by Scythe X10 on 2008-12-07
Come on, Really? Know one knows the answer this this issue?

---

### Post by odzx on 2008-12-08
> **Scythe X10 said:**
> Come on, Really? Know one knows the answer this this issue?

did you try unetbootin?
I got my usb flash drive to work by running using unetbootin first and then erasing everything from the drive and running the ubuntu tool again.
I can still run it though only one computer in the house. the other one will not boot.

---

### Post by Scythe X10 on 2008-12-08
Yes I tried that. Both of my computers won't boot off of it. I just gave up and put my regular stuff on it. But if anyone has a sure fire way of getting this to work please share.

---

### Post by ugm6hr on 2008-12-08
I gather you're trying to get a persistent USB install (rather than a LiveUSB).

This has an option: [http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

It also links to screenshots detailing how to use the USB creator.

---

### Post by Scythe X10 on 2008-12-10
> **ugm6hr said:**
> I gather you're trying to get a persistent USB install (rather than a LiveUSB).

This has an option: [http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

It also links to screenshots detailing how to use the USB creator.

I may be out of line, because of my lack of knowledge on this subject But I thought the built in USB creator did the same thing.

From the linked page - "Please Note: A very nice USB Installer is now included on the Ubuntu 8.10 CD, Please use this > [USB Ubuntu 8.10 Flash drive installer]("http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/") instead!"

---

### Post by ultratek on 2008-12-11
make the drive an unallocated space and let ubuntu format it as logical and not primary

---

