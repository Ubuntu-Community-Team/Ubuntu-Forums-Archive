---
title: "Dual Booting Xubuntu and XP the right way"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by johngreaver on 2009-01-22
Ok I'm still a LINUX noob but here my question i want to make sure i get this right. I have been running ubuntu with the gnome GUI.I find gnome to be kinda slow with my setup so Idownloaded xubunut and i LOVE xfce it works great. so here my question Im going to install xubuntu overmy current ubuntu i usually do manual partition i create 3 partitions a 50mb /boot ext a 2gb swap and the rest for my instal ext3. Is this the best way, when dual booting with xp i only have an 80gb hdd and i split it 50/50. i was also wondering is it best to locate my swap file at the begening or end of the partition i have heard you get better performance putting it at the begening. well anyways i just want to make sure this is the best way to go about it any help woul dbe awesome

Gateway Mx6441 laptop
80gb hdd
512mb ram
1.8ghx amd turinx64

---

### Post by louieb on 2009-01-22
Don't think the location of the swap partition is going to make much difference (if any)  that you would see. Like you I've  heard the fastest access is to sectors at the beginning of the drive.

Unless you need a /boot partition (using encryption or LVM or you get GRUB error 18)  don't think I'd use one.   Instead I create a 10GB / (root) partition, a swap partition and use the balance to create a /home partition. 

My laptop has a 40GB drive. This is how I have it sliced up. 
[IMG]http://louboldt.com/part_t30laptop.png[/IMG]
  

Doesn't sound like your that new. Manual partitioning scares most noobs.

---

### Post by Mark Phelps on 2009-01-22
You don't need to download XUbuntu -- you already have it. To quote from the Xubuntu info "Xubuntu is a version of Ubuntu that uses XFCE instead of GNOME as a desktop."

Just change your desktop from Ubuntu to Xubuntu. Install the package xubuntu-desktop, then on the reboot, select Xfce as the desktop manager and you're set to go.

---

### Post by zvacet on 2009-01-23
@ **johngreaver**

As **Mark Phelps** allready said there is no need for fresh install of Xubuntu.All you need to do is install xubuntu-desktop.If you want xfce and remove gnome read [this.]("http://psychocats.s465.sureserver.com/ubuntu/purexfce")

---

### Post by johngreaver on 2009-01-23
@louieb 

I took your advice man it owrks great as for manual partitioning i am a linux noob but im an ace on windows and i have used a lot of linux based partitioning tools , and i downloaded and installed a fresh xubuntu because i had too much bs on my ubuntu gnome install i tried downloading the xfce enviorment and didnt like the way it it installed over gonome when i switched sessions........on another note im getting ready to buy a new lappy my bidget is about 650 bucks what hardware would you guys recomend to run ubuntu or any linux distro in general the best because now i right now i have an ati xpress 200m intergraded card with 64mb and even with the proprietary drivers its buggy as hell im all ears i really want to learn linux so far my expeirence has been top notch but i want to be completly micro$oft free

---

