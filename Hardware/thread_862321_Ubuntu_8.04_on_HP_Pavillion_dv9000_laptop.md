---
title: "Ubuntu 8.04 on HP Pavillion dv9000 laptop"
date: 2008-07-17
forum: Hardware
---

### Post by fiprojects on 2008-07-17
Folks,
I've tried this for seven months but am unfortunately leaving Ubuntu Linux as a desktop environment - I'm a Unix/Linux techie and think its great server side - I am more used to the RedHat directory structure but not totally lost with Ubuntu and can do most of the work that I need to do.  From a desktop point of view though the sheer amount of effort for me to get things going is annoying the pants of me.  I'm amazed for instance that something as simple as Mozilla Firefox installs but does not marry itself to my java installation that I have to tweak under the bonnet to make it work.  I've tried different Java installations - I would have thought something as basic as this would be plug and play from Sypatics or whatever but alas not. I hate having to depend on VMware and XP just so I can do my online banking (which needs java).  Email/Web and OpenOffice are my day to day tools - as is DreamweaverMX which I have tried with CrossOver and instead went for vmware/XP setup.

The purpose of this post is not to curse though - sorry if it appears that way - It is to assist other more patient people as I have drivers and their respective URLs for those that might depend on ndiswrapper to get things like wifi working on a laptop similar to mine.

My laptop was bought in Canada and HP recognise it as as dv9618ca (17inch monitor, two hard disks 120Gb a piece, using AMD Turion64x2 and Nvidia graphics card, 2Gbyte of RAM - I did engage HP for support about XP drivers - amazingly, XP is not supported on it (forcing you to stick with Vista) but they did help and say unofficially such drivers are available as follows - Ubuntu installed fine on my machine with the exception of the wifi which I got working using ndiswrapper.

Drivers are:

MS Universal Audio Architecture (UAA) Bus Driver for High Definition Audio (sp33867)
[ftp://ftp.hp.com/pub/softpaq/sp33501-34000/sp33867.exe](ftp://ftp.hp.com/pub/softpaq/sp33501-34000/sp33867.exe)

Kane: Here is the link for Conexant High Definition Audio Driver :
[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34200.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34200.exe)

Kane: Here is the link for NVIDIA GeForce Series Video Driver :
[ftp://ftp.hp.com/pub/softpaq/sp33501-34000/sp33537.exe](ftp://ftp.hp.com/pub/softpaq/sp33501-34000/sp33537.exe)

Here is the link for Synaptics Touchpad driver :
[ftp://ftp.hp.com/pub/softpaq/sp35001-35500/sp35444.exe](ftp://ftp.hp.com/pub/softpaq/sp35001-35500/sp35444.exe)

Here is the link for Conexant HDAUDIO Soft Data Fax Modem with SmartCP Driver : [ftp://ftp.hp.com/pub/softpaq/sp33501-34000/sp33742.exe](ftp://ftp.hp.com/pub/softpaq/sp33501-34000/sp33742.exe)

Kane: Here is the link for Broadcom Wireless LAN Driver :
[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)

Kane: Integrated 10/100BASE-T Ethernet LAN driver for AMD dv9000 :
[ftp://ftp.hp.com/pub/softpaq/sp28501-29000/sp28817.exe](ftp://ftp.hp.com/pub/softpaq/sp28501-29000/sp28817.exe)

Cheers / Best of luck to you all...

---

### Post by rhlapathy on 2008-08-08
I have the same laptop and have been looking to putting Ubuntu on it.

Did you have to format both partitions or did you just format one and install from the cd?

---

### Post by kaffka on 2008-08-19
You can install it on any hard drive i think, but i would strongly suggest you to start by resizing a partition with Vista.

Ubuntu is not so space eating, starting with a partition of 30 gig will give you more than you need, beside you will need 2 more partition, 1 for GRUB and 1 for swap memory.

Now Ubuntu can read/write on NTFS, so it's great.

But you need to use the Alternate installation CD

in any case good luck, there is a lot of information regarding Ubuntu/Kubuntu on DV9000

---

