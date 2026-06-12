---
title: "Any way to dual-boot XP and Ubuntu Netbook Remix?"
date: 2008-12-07
forum: Hardware
---

### Post by CycleGeek on 2008-12-07
Folks:

I was very pleased running Gutsy on my old Inspiron 700m.  When it gave up the ghost a few weeks ago I took the opportunity to get an Acer Aspire One - the ZG5 with 160GB HDD and 6-cell battery. 

I'd like to dual boot the Ubuntu Netbook Remix on this machine - the only problem is that the USB image I found here 

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

has no option to set up a dual-boot.

I tried doing a vanilla Hardy install to repartition the drive.  It put in a GRUB screen that allowed me to pick the OS, but when I did the UNR install off my USB drive, I didn't see my Windows partition and GRUB is gone.

Once I get my recovery disks - is there a quick way to set up a dual-boot between XP and Ubuntu Netbook?

Thanks so much in advance!

---

### Post by JediJazz on 2009-04-23
Hi there this is my first post but I hope it helps.

Ok Its a bit of a pain to get the Netbook Remix to work with additional OS's but its something i had to do.

I do like chilling out with the remix but every now and again I may need Windows or my ubuntu Ibex  box for something...

This is what i done last time...

The installer for Netbook remix wipes the whole hard drive.

I installed the NETBOOK Remix First.

Then use Gparted on a USB stick and Resize that partition and created and additional 6 partitions.


I then installed Windows, and then Ubuntu Ibex Last and that picked up on all the different partitions to create my grub. 

Its may not be the best solution for you but it doe what i needed . I hope it helps. 

JediJazz

---

### Post by beanhead on 2009-04-23
I have an aspire one and installed it to usb with the usb image writer program. Using the 9.04 image it was very easy give it a try ! It dual boots just fine. Of course I killed windows as soon as I tested it ! Way better ! Linux rules !

---

### Post by HankB on 2009-04-23
> **CycleGeek said:**
> 
Once I get my recovery disks - is there a quick way to set up a dual-boot between XP and Ubuntu Netbook?
The installer for the 8.10 version of UNR blithely overwrites your drive. The one used for Jaunty is like a normal install that allows you to select partitions and such. It should be no problem to set up a dual boot install with that.

-hank

---

### Post by caulktel on 2009-04-25
I also installed it last night on my AAO 8.9. I already had Window XP on it. I love UNR 9.04 on it now, but it wont boot XP anymore. It shows up in the Grub menu and I can see my files from Linux side but it just sits there saying "starting up" or something like that. Any ideas?

---

