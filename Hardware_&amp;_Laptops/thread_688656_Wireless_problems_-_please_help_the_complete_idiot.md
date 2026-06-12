---
title: "Wireless problems - please help the complete idiot!!"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by myddewji13 on 2008-02-05
ok...as per title i am the complete idiot... this is the problem im having...the wireless on my laptop isnt working (seems like a common problem)...but after talking on the phone with hp... they're telling me that i dont have a broadcom problem but rather an intel problem....as per this thread 
[http://ubuntuforums.org/showthread.php?t=686036]("http://ubuntuforums.org/showthread.php?t=686036")

anyway...some help would be extremely appreciated as this internet issue is the only thing thats keeping me from getting rid of windows completely...

---

### Post by odiseo77 on 2008-02-05
I can't be of much help since I don't use a broadcom or a intel card, but first of all, we need to know which card you're using. In a terminal, type:

```
lspci
sudo lshw -C network
```

and post the outputs here, so other people with more experience with these cards can help you.

---

### Post by myddewji13 on 2008-02-05
this is what i get

```
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:43:92:2a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=172.16.4.105 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
```

---

### Post by pytheas22 on 2008-02-05
I wouldn't trust what some HP support guy tells you unless you're sure that he specifically supports Linux (which I don't think HP or hardly anyone else does to end-users); otherwise he probably has no idea what he's doing outside of XP.

You have a Broadcom wireless card, chipset bcm4310.  Thanks to the hard reverse-engineering work of some programmers (and no thanks to Broadcom, which has steadfastly refused to cooperate with open-source), there is a Broadcom Linux driver which however requires non-free firmware to work.  Ubuntu for legal and philosophical reasons doesn't ship with the firmware, but it's easy to install.  Do this in a terminal:

```
sudo apt-get install bcm43xx-fwcutter
```

it should ask you something about automatically fetching the firmware; tell it yes.

If all goes as it should, the firwmare will be extracted and installed, and a simple reboot should have your wireless working.

If things don't go as planned, post and I'll try to walk you through it.

---

### Post by pytheas22 on 2008-02-05
if the above steps don't work, see the how-to here [http://ubuntuforums.org/showthread.php?t=434946](http://ubuntuforums.org/showthread.php?t=434946) for a tutorial specifically for your version of the Broadcom card...but you can still ask questions here if that doesn't work for you.

---

### Post by myddewji13 on 2008-02-05
ok...trying it out now...ran into one problem

```
wget ftp://lwfinger.dynalias.org/patches/bcm43xx-softmac-sa.tar.bz2
```
doesnt work...i dont think the file is hosted there anymore...any ideas where to get another copy?... im currently searching on google with no luck

---

### Post by myddewji13 on 2008-02-05
ok...no luckk....help whenever u can...thank u..

---

### Post by pytheas22 on 2008-02-05
Did you try it using the directions I gave you before following the how to?  Were you asked at any point if it should fetch firmware automatically?

You shouldn't actually need to download the driver...doing so and compiling it would give you the latest version, but you should already have a relatively recent version built into the Linux kernel that will work once it has the non-free firmware to plug into.  You could probably skip steps 3 and 4 of that tutorial and it would be fine.  It does look like that site is gone for good.

---

### Post by myddewji13 on 2008-02-05
THANKS a lot...i managed to get the wireless working using ndiswrapper... the problem was the driver...when u do a search for broadcom 4310 on the forums theres a link to a dell driver...they tell u to look in the drivers_us folder...and it workd!!!...finally its been a week...im soooo happy...now just the headphone issue (speakers not turning off when headphones plugged in) to deal with and then im uninstalling vista....GO UBUNTU!!!!YEA

---

### Post by myddewji13 on 2008-02-06
....ok...edit that..i sort of have it working...i have to reinstall the driver evertime i restart...anyway to make ndiswrapper work permenantly?

---

### Post by myddewji13 on 2008-02-06
nvm...got it fixed...just searched 'enable ndiswrapper on startup' in forums

---

