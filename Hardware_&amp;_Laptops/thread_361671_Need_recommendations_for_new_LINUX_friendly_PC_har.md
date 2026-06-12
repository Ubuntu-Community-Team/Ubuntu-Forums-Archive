---
title: "Need recommendations for new LINUX friendly PC hardware"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by caffienda on 2007-02-14
I need some advice and opinions on putting together a new computer system.  I currently have 4 PC's and am wondering if using VMWare would be an ideal replacement for some of these PC's.?. I am just learning Linux, but am trying to migrate to it and use it 85-90% vs the 20-25% I use it now.  

I listed What I have now as far as PC's and equipment.  I'd like to consolidate as much as possible without spending a lot of $$.  I thought I would sell whatever I'm not going to use. 

I'm torn between starting a rackmount system or keeping the cases I have.  They are nice Thermaltake Tsunami3000's ($130 each).  I'm no noise fan, so I'd like to keep that in mind when choosing a CPU, MOBO and Video Card (but I guess there are always silent cooling options)

My thoughts were to keep one of the P4's as a HTPC. I love moves, music and pics, so this would be a good PC for this I guess.  When I buy movies, I copy them to the HD so I can view them w/o searching for the disk.  I'd love to be able to do this over the LAN!!

My budget for new MOBO, CPU, RAM, Video Card, RAID Controller, PSU and cooling is $1500 MAX.  I AM NOT A GAMER!!  I want a solid performer that can run a couple virtual OS's under something like VMWare.  I've been out of the hardware side so long, I'm not sure if I want to look at AMD or Intel. I have no preference.  I'm NO FAN of ATI!!! So, please let me hear your suggestions!  MUCHAS GRACIAS!!

Current PC's
**PC1**  XP Pro
-P4 2.53
4x512mb PC3200 RAM
ATI AIW 9600 (Dual 17" LCD Monitors connected)
Hauppauge PVR-150 PCI (USE THIS VERY OFTEN, AIW doesn't work for tuning)
2 16X DL DVD+-R/RW
4 Raptors, 2 74GB &  2 36GB 
4 SATA2 500Gb drives; 2 5000KS (16mb buff), 2 5000YS (Raid edition 2, 16mg buff) 
2 USB 250GB MyBooks


**PC2** Ubuntu 6.10 & VMWare Server
-P4 2.6
2x512 PC2700 RAM
Sapphire 9200 ATI based video card (17" LCD shared monitor on KVM switch)
4 WD 160GB PATA HD's
2 8x DL DVD+-R/RW

**PC 3 &4** 6.10 server
2 Dell P3 1Ghz,  Shared 17" LCD
-2x256 (512 total) RAM, 60Gb HD, 2 3COM Gigabit NIC's, 8x DL DVD+-R/RW
-128 RAM, 40Gb HD,  100Mbs NIC, DVD-ROM
           (I'm just playing around learning the server environment with these PC's.  I have a local web server on it, FTP server etc.  These are my first PC's I've really had SSH access to that isn't over a slow upstream of broadband.) 

I plan on expanding with more 5000KS's and 5000YS's in the future,

---

### Post by simonn on 2007-02-14
IMHO I think you approaching this from the wrong perspective.

Ask yourself what kind of software you want to run i.e. what you actually want to do with the PC(s).

As you are not a gamer I would be very surprised if you could not run **everything** you wanted on one linux box without VMware.

FWIW I have a Sempron 64 3000 with 1Gb RAM running Xubuntu. It can run slimserver, lighttpd running our "intranet" (slight exaggeration), record (or watch) two dvb-t streams (raw mpeg), while ripping a dvd to xvid (on a low nice level), browsing the web and doing some programming without it even flinching. Under 500mb RAM used (more like 350mb).

Home web/ftp servers require hardly any resources - I used to run one of a P133 with 64Mb - full on apache, most pages generated from xml using php etc.

As far as VMware goes, RAM is really the important thing. Again, as you are not going to be running games, I would budget for 512Mb RAM for WinXP and linux running gnome or KDE sessions, 256Gb for linux running XFCE sessions, 64-128Mb for linux without a GUI sessions.

---

