---
title: "Install problems"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by christhemonkey on 2006-06-06
I am trying to do a fresh install of Dapper with the live/install CD on my laptop.

The first time i booted up the live CD, everything was fine, so i selected install.  And went through and it then fell down on the partitioning.

So i switched it off, and went away and thought about it.


Next time i came back and did the partitioning before the installer (just deleted all partitions on hard drive, there was an extended partition left before for some reason)
Went through the installer, hour an a half later it fails, saying something about improper usage of modprobe.

So i switched off again, and came back later.

This time it takes about 2 hours to boot, and then when it does, never finishes loading GNOME.  Just sits there and reads the CD until about half an hour later, just being unresponsive.


This happens everytime i boot the liveCD.
My previous install of Breezy has been wiped off the harddrive.

I have tried booting with lots of different options; acpi=off noapic nolapic vga=771.  But the only one that seemed to help was the vga=771, which after seemingly forever dumped me to a command line after complaining X couldnt start.  So i edited xorg.conf, did a startx.  Was loading fine, but never finished.  Just stopped again.



The CD is a good burn, have installed on a couple of other PCs with it.  Have checked my RAM and the CDs integrity, both good.


Laptop has Pentium Celeron 600mhz with 128mb ram 10Gb hard drive.

Any help getting this to work greatly appreciated.


(sorry for the lengthy post! Really want to get Dapper working on this laptop)

((i would use an alternate CD, but this laptop was the only way of burning CDs!))

---

### Post by gatekeeper on 2006-06-06
The way I got round a similar problem was to install Breezy, replace sources /etc/apt/sources.list to the Dapper ones then:

sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade

Sad to say, but the Dapper installer doesn't seem to be rock solid yet. :-(

---

### Post by christhemonkey on 2006-06-07
Ok thanks for that, but this laptop doesnt have the internet.

What i did to install dapper,


First noticed that the live CD uses any available swap partitions,
then thought maybe i deleted a swap partition when i was doing partitioning.

So i did a server breezy install and created a 1GB swap partition.

Then went back and installed dapper,
it took over two hours in total from booting into dapper, to logging into it.
But now i have ubuntu Dapper Drake on my laptop, and i am happy :D

---

### Post by gatekeeper on 2006-06-07
Good to hear that you are up and running.  :-)

---

### Post by lavinog on 2006-06-09
[QUOTE=christhemonkey]

Then went back and installed dapper,
it took over two hours in total from booting into dapper, to logging into it.
But now i have ubuntu Dapper Drake on my laptop, and i am happy :D[/QUOTE]

I ran into a similar problem with xubuntu desktop cd. I found using the text mode install with the alternative install cd worked perfect and works much quicker for me.

---

