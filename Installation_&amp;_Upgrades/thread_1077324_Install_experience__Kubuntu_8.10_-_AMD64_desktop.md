---
title: "Install experience:  Kubuntu 8.10 - AMD64 desktop"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by TomB19 on 2009-02-22
Newegg.ca put an AMD 9850 / Foxxconn A7DA-S combo on sale a couple of weeks ago for less than $200 and I couldn't resist.  They also had a great deal on Patriot 2GB SIMMs so I picked up 4 for a total of 8 GB.  I also picked up a Skythe mini-Ninja cooler.

I do quite a bit of panorama stitching with Hugin so the RAM and CPU will be put to good use.


The system:

AMD 9850
Foxxconn A7DA-S
4 x 2GB Patriot Viper (PVS24G6400LLK)
USB 2.0 media reader
no floppy
6 x Samsung 750 GB HDD (HD753LJ)
Lite-On LH-18A1P


The distribution:

I can't live without KDE and I can't live without Kubuntu.  Having tried an AMD64 flavor of Kubuntu previously, I had returned to i386 Kubuntu on my old dual core 2GB box.  The AMD64 version is generally fine but getting flash to work was not easy and it never did work quite right (it would play a few videos and then stop functionng) and Kdevelop 3.5.x didn't work properly out of the box.  Also, there is a bug with nVidea video support that causes it to not display checks in check boxes when they're selected without a refresh. The first two are probably packaging issues.  Kubuntu i386 works perfectly so I just carried on.

Having 8GB of RAM, I need an AMD64 distribution.  I'll report back on how it goes.


The install media (unetbootin):

Without a floppy drive, I wanted to install from USB stick.  This proved difficult.

unetbootin 3.04 - wouldn't make a bootable USB key from my .iso
unetbootin 3.13 - wouldn't make a bootable USB key from my .iso
unetbootin 3.13 - would make a bootable USB key if I let it download the .ISO but it selected the alternate net-install CD.


The install:

It went fairly well but there are problems with the Canadian APT mirror that cause it to go so slowly, it's pretty much broken sometimes.  I tried twice to use the Canadian mirror but had to switch to the US mirror to successfully install.

The alternate install worked fine but it asks a lot more questions than the GUI install.



The configuration:

Partitions -

/boot -> USB key
/ -> 6 drive mdadm RAID5

You can't boot directly to a RAID5 array and I didn't want a hard disk in the system for a small /boot partition so I thought I'd boot the kernel and initrd from a USB key.  It works slick.  There isn't much activity on the USB key so it doesn't slow the system down at all.  Further, it doesn't use the power and generate the heat of a hard disk.  I'm using a 1GB stick because that's the smallest I have but a smaller stick would be fine here.


The initial experience:

- The USB key shows up in the BIOS as a hard disk.  This needs to be kept in mind for the boot order.
- The binary ATI drivers are more buggy than the binary nVidea drivers.  Tabbed pages don't display the tabs properly.
- Lots of RAM is like cocaine for Hugin.  I've never seen it work this fast.  I think the RAM has more impact than the number of cores.


I'll report back after I've been running this system a few weeks.  So far, I'm extremely happy.

This community has been extremely helpful to me.  There is a great group of guys who hang out here and answer stupid beginner questions such as I've had in the past.  Thank you to all.  :)

---

