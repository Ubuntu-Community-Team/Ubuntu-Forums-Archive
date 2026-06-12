---
title: "Install Fails with Averatec 6200 Series, works with LiveCD"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by Michael_Valentine on 2005-04-08
The LiveCD portion works when I select the special boot parameters at the prompt "livecd vga=771 noapic nolapic", I select the sis video card during this process as well and everything is ok at this point, but when I try to install I have to use the same parameters "linux vga=771 noapic nolapic" to start the install which runs thru all it routines successfully until it is finished.  At this point I end up with a cursor in the upper left corner and a black screen.  I have tried adding the "xdriver=sis" boot parameter as well as "xdriver=vesa", "xdriver=sis noapic nolapic" and a host of others either leaving me with a completely black screen or the one with the cursor in the corner.  Any ideas?

---

### Post by Michael_Valentine on 2005-04-10
Fixed the problem, edited the xorg.conf file from recovery mode and set the video driver to sis.   :-)

---

### Post by jamesrw on 2005-06-22
I am thinking about buying an Averatec 6240 and running Ubuntu. How smooth was your installation? I am not an experienced user... do you think you could tell me what you did to get things running? What are some things that don't work and need time to fix?

---

### Post by Jleviaguirre on 2005-11-12
By this time you probably already bought your laptop. Anyway, I have an Averatec with dual boot (yes, Windows is a nessesary ill) four partitions:

1 ntfs
2 swap
3 linux
4 fat32 (to share amont winnt and linux)

It works fine the installation. I did the noapic nolapic to install and everything is great except for the wifi. I am sure there is a way to make it work.

---

### Post by fezzik on 2006-09-14
Were you able to get the Daper installation to work?

---

