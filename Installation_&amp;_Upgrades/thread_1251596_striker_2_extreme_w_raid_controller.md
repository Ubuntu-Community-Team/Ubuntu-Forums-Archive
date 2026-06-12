---
title: "striker 2 extreme w/ raid controller"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by wimcolgate on 2009-08-27
Hi,

I have a ASUS striker 2 extreme based system. It currently has 3 1TB drives configured as:

sata0: stand alone drive, 200MB bootsec + remainder is "perma files" (files that can be accessed by whatever OS I boot).
sata1/sata2: RAID0 using the built in nvidia raid controller -- this is where I have chosen to install my OSes. Currently I have a Vista and Win7RC1 OS install, (800MB total) with a previous vista install that is 400MB, but is now an empty partition. The remainder of the raid disks is empty.

When I try to install Ubuntu 9.04, It gives me the option of installing on my sata0 drive, or sata1 or sata2 -- but it does not seem to realize that my sata1/sata2 is a RAID set, and that there are some partitions available inside this RAID set to install on. Basically the installer sees sata1 and sata2 as completely empty drives.

Has anyone inastalled Ubuntu on a striker 2 extreme RAID enabled enabled drive?

Any help would be appreciated.

Thanks,

Wim

---

### Post by stlsaint on 2009-08-27
how are you trying to install ubuntu...via wubi..or livecd?

---

### Post by wimcolgate on 2009-08-28
downloaded the .iso to CD and booted the CD. I tried running gparted from the live CD after I aborted the installation -- and gparted also doesn't seem to see the RAID set -- just the individual and separate disks.

---

### Post by wimcolgate on 2009-08-29
Has anyone been able to use the onboard RAID controller to host their Ubuntu installation?

---

### Post by wimcolgate on 2009-08-31
It seems I am not alone in this. I found another poster in another forum that describes the same problem: 

[http://serverfault.com/questions/11834/onboard-raid-and-ubuntu-install-why-does-it-see-separate-disks](http://serverfault.com/questions/11834/onboard-raid-and-ubuntu-install-why-does-it-see-separate-disks)

I interpret this to mean that Ubuntu doesn't fully support the Asus Striker 2 extreme motherboard. By fully I mean the onboard Nvidia Raid chipset.

I also found this: 

[http://www.nvnews.net/vbulletin/showthread.php?t=100739&highlight=ubuntu+raid](http://www.nvnews.net/vbulletin/showthread.php?t=100739&highlight=ubuntu+raid)

It seems that Nvidia doesn't even supply linux drivers for its chipset either!

Is there anyone in Ubuntu-land that could confirm my interpretation? What's the likelyhood of a driver showing up one day? Since my RAID set contains all my various windows installations, I cannot, at this point simply break the RAID set to install Ubuntu :(

Wim

---

### Post by wimcolgate on 2009-09-05
After doing a little more reading ... is it possible to use mdadm to access/manipulate the RAID0 set (i.e. SW RAID) -- that was initially set up using the on-board NVIDIA raid controller? Since Ubuntu sees the disks independently, I'm assuming access to the drives actually (can) bypass the nvidia chipset? 

If this path can work, does anyone have a suggestion on how to set up the installation to use mdadm?

Does anyone see any downside to this? (like maybe incompatible implementations of RAID?)

Thanks,

Wim

---

