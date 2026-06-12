---
title: "Eager to install 9.04"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by leveliv on 2009-08-19
Alright here's the big deal...I want to install ubuntu. But!

I have no installation disc and no way of getting one. I do how however have two extra computers on my network. Can I install it from .iso with like a virtual drive via network? 

The computer I am installing it on has windows XP as well...and I have some data like my WoW install and some accounting programs that I need to keep and cannot delete. How can I keep them but still have ubuntu..leave them in their own partition? 

The computers specs are pretty old but here they are: 
P4 1.3ghz 
512ram
Radeon AGP 6800 
40GB Harddrive
AC97 Sound

Thats it thats all ..I was also looking at gOS cause its based on 8.04LTS and is most likely stripped down for netbooks. and isn't as bulky as 9.04. 

oh and both the computers on my network are running either XP or Vista.

---

### Post by Copernicus1234 on 2009-08-19
Install it with [Wubi]("http://wubi-installer.org/"), that way you can run it without messing with your Window system until you are ready to move over completely.

And yes, if you have access to the other computers through the network, you can mount the ubuntu iso file on one of those computers, using daemon tools or similar, and install it with Wubi from Windows.

---

### Post by raymondh on 2009-08-19
see if a network install for 9.04 suits your needs/circumstances.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

For alternative distros, you may want to consider Xubuntu or Crunchbang.  I use crunchbang as well as gOS.

---

### Post by leveliv on 2009-08-19
I have Crunchbang on the DL right now. but now I am confused as to how I can keep  some files untouched..while installing linux.  there is about 3 gb of space left on the drive right now..maybe if I delete up to...15 or so I can just make another partition? Does anyone know how much XP takes up just for XP itself?

---

### Post by datacw on 2009-08-19
ok heres another thought

get the 9.04 cd or .iso and go into system -administrator usb start up disk maker and the rest is self explanatory:lolflag:

---

### Post by raymondh on 2009-08-19
> **leveliv said:**
> I have Crunchbang on the DL right now. but now I am confused as to how I can keep  some files untouched..while installing linux.  there is about 3 gb of space left on the drive right now..maybe if I delete up to...15 or so I can just make another partition? Does anyone know how much XP takes up just for XP itself?

When dealing with the HD, there are no guarantees except ... make sure you have a back-up of your valuable, irreplaceable files.

When setting up a dual boot configuration, just make sure you recognize which partition is windows and NOT touch it.  Also, realize that some OEM installs have a OEM-configured recovery partition.  Don't mess with that as well unless you have an original installation disc (or have an image of that partition elsewhere).

The forum and google ought to give you results/How-to's regarding dual-boot.  Here's the [installation guide]("https://help.ubuntu.com/community/Installation") for Ubuntu 9.04, as an example. 

My XP resides is a 20GB partition ... sans personal data, music, pics, videos ... just system and apps.  So far, I've used about 8GB of it.

You can create the partition prior to installation.  If so and during installation, you have to direct the install to that partition and mount root (/) and swap, as well as others thru the MANUAL option.  

In ubiquity (Ubuntu), there is also an automated option that allows you to install Ubuntu in the "largest continous free space"...

...or another option (GUIDED RESIZE) that allows you to use a slider to set partition sizings and ubiquity does the rest.  This guided resize is for those that have not created a partition beforehand nor, have an existing unallocated space.
 
Post back if you need clarifications.

---

### Post by leveliv on 2009-08-19
yeah I know about the partitioning. I have been using Ubuntu for about...4-5 years now. I will probably just go for the install on continuous amount of space. is there a minimum amount of free space?

---

### Post by leveliv on 2009-08-19
> ok heres another thought

get the 9.04 cd or .iso and go into system -administrator usb start up disk maker and the rest is self explanatory

how would I do that when I havent got it installed anywhere? or a live CD

---

### Post by raymondh on 2009-08-19
> **leveliv said:**
> yeah I know about the partitioning. I have been using Ubuntu for about...4-5 years now. I will probably just go for the install on continuous amount of space. is there a minimum amount of free space?

root, for me, is 20GB.  So far I have used 8GB (coincidentaly same as XP's). 15GB seems to be a good number for root.  Swap is at 2GB. I use a either a separate /home or a /data.

On another matter .... what is the vintage of your BIOS and laptop?  If you have a cylinder limit, try to keep the install within or risk an error 18.

---

