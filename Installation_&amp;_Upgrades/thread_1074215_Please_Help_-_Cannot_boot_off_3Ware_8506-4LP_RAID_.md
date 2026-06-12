---
title: "Please Help - Cannot boot off 3Ware 8506-4LP RAID Controller"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by rasta_caleb on 2009-02-19
Hello,

A while back, I bought one of these: 
[http://www.surpluscomputers.com/348232/rackable-systems-dual-xeon-3.0ghz.html](http://www.surpluscomputers.com/348232/rackable-systems-dual-xeon-3.0ghz.html)

The system works great, but recently I have tried installing Ubuntu Server 8.10, but I can't get it to boot properly.

Here is what I did:
1. Reset the BIOS (Phoenix BIOS) on the machine to default config
2. Formatted the drives, created two RAID 1 (mirrored) Arrays.  The first is comprised of drives 0 & 1, and the second drives 2 & 3.

I installed Ubuntu 8.10 using UNetBootin (gave it the ISO i downloaded) via a USB stick, also seemed to work great; it discovered the hardware, set up the network, and apparently installed a bunch of great stuff like LAMP, Tomcat, and SAMBA services.

Now, after successfully installing all that, my server boots and sits there with a blinking cursor.

The Phoenix BIOS seems to think there are no hard drives present.

My friends are telling me to use FreeBSD, we used that a ton at yahoo where I used to work so I am somewhat familiar with it, but I have been reading up on ubuntu for the past few weeks and i'm very impressed.  I really want to get this to work. 

Please, help :-)

Thank you in advance.

---

### Post by dean123 on 2009-02-19
It is possible that your system bios tried to boot from the
second raid unit. Some bioses scan in reverse order. You can confirm my theory by deleting the second raid unit, 
non-bootable unit if you will.

Some system bios settings will allow you to change the boot order of add-in bootable cards and scsi. Check yours. Good luck.

---

### Post by tekkitan on 2009-07-13
I am having this same problem, different 3ware card though. I only have one array though, 2 hard drives in RAID1. My BIOS sees the 3ware card and it is set to boot first. Still I get the blinking cursor though. Seems to work with FreeBSD and Windows, so I am sad :(  I am trying to build a nice Ubuntu 9.04 desktop.

---

### Post by tekkitan on 2009-07-15
anyone?

---

### Post by stuffthatspins on 2010-12-10
I'm having the same problem. Different 3Ware card.

I used the 3Ware bios to setup a RAID 10 unit. Installed ubuntu server 10.x lts on the RAID unit.

When I try to boot the system is hangs with a flashing cursor... 

I've set the Phoenix bios to default settings. I've made sure the boot order for HD has the 3Ware card in it. I've moved the drives to the second controller card. nothing. nada...

Not sure where to go from here.

Phoenix server bios 3 rel. 3.1
3Ware bios RAID controller 9500s escalade

Thanks!

---

