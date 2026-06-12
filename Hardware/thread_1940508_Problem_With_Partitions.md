---
title: "Problem With Partitions"
date: 2012-03-13
forum: Hardware
---

### Post by Mir Rahmati on 2012-03-13
Hello Everyone

I am very new to Linux and I just installed the latest version of Ubuntu, I have deleted all my partitions and replaced my Windows operating System with Linux. I thought I can partition it after installing. 

I don't know how to partition my hard disk and separate a drive for my data. at the moment there is only one drive which is System. 

any ideas, please. 
Thank you very much

---

### Post by ahallubuntu on 2012-03-13
Out of curiosity, why do you want a separate partition for your date?  Some people do want this (having a separate /home partition for example) in case they want to upgrade Linux in the future or use different Linux versions with the same data.  (Or have Windows running as a dual-boot.)

To setup a separate partition now, you'll need to boot up your Ubuntu CD again and get into the "Try it" mode (not install).  Then start up Gparted.  If it's not installed, be online while you have the CD booted, then install it.  From a terminal:

sudo apt-get install gparted

To start it up:

sudo gparted

Then shrink your existing partition that "/" is mounted on by the amount you wish to have for data.  Then create a new partition in that free space, all in gparted.  Google for "gparted" info for more details on how to use it, but it's fairly easy.

To mount the new data partition on /home automatically you'd need to edit your /etc/fstab file and add the new partition there.

---

### Post by jerrrys on 2012-03-13
First you need to get to know gparted

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

How big are your HDD's?  Is one an external (usb)?

---

