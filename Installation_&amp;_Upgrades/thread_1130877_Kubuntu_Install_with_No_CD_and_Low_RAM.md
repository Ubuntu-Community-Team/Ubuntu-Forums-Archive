---
title: "Kubuntu Install with No CD and Low RAM"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by JeremyWorst on 2009-04-20
Does anybody have any suggestions for installing Kubuntu on a laptop that won't boot from CD and only has 128 MB RAM?  It's an old Toshiba laptop and the CD drive is connected via a PCMCIA card.  I've not been able to get it to boot from any bootable CD.  And Kubuntu's minimum RAM requirement for a normal install is greater than 128 MB.

Thanks!

Jeremy

---

### Post by Mark Phelps on 2009-04-20
If it DOES install, you won't be able to run KDE desktop -- so what is the point of installing Kubuntu?  Don't know if Xubuntu will even run with that little RAM.

You would do better to consider one of the minimal installs like DSL or Puppy Linux.  See the distrowatch.com page for links.

---

### Post by FaizanKazi on 2009-04-20
"Xubuntu releases:

    * 8.10, codename Intrepid Ibex (newest stable release).
    * 8.04.1, codename Hardy Heron, includes Long Term Support.

Minimum system requirements
You need 192 MB RAM to run the Live CD or 128 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time. To install Xubuntu, you need 1.5 GB of free space on your hard disk. Once installed, Xubuntu can run with starting from 192 (or even just 128) MB RAM, but it is strongly recommended to have at least 256 MB RAM. "

copied from: [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

xubuntu is fast and requires little system resources... just a note though... to make up for the very very low ram you might need to keep a good bit of swap space. a 2GB dedicated swap partition is strongly recommended. 

btw how in the world do you only have 128 mb of ram? youll probably be able to find an old stick of ram at some used computer parts shop for like 5 US dollars or so :) should run fine on 256 :) you could even run ubuntu!

you might wanna check out: [http://distrowatch.com/dwres.php?resource=major](http://distrowatch.com/dwres.php?resource=major)
seeing as you cant get ubuntu you might wanna check out some of its alternatives (listed at the bottom of the ubuntu section).

personally i thought openGeu seemed good, the enlightenment graphical desktop environment may not be KDE, but it might be better than the XFCE youll get with xubuntu (not sure about this :s) just try it out. nothing like experimentation!
[http://news.softpedia.com/news/First-Look-OpenGEU-8-10-107134.shtml](http://news.softpedia.com/news/First-Look-OpenGEU-8-10-107134.shtml)

Crunchbag linux (for low end systems) looks great!
[http://lwn.net/Articles/320950/](http://lwn.net/Articles/320950/)

heres a trick: buy yourself a neat 4gb to 8gb (preferably 8gb) flashdrive, and boot up off the xubuntu live cd (or your install) and create a bootable usb drive using the "iso" file (System >> "system settings??" >> Create a bootable USB flash disk). you boot up off the USB drive, try your distro, and if you like it, install it! if you dont, move onto the next one in 15~20 mins (time it takes to install to the usb drive)!!
have fun!!!

---

### Post by tamas305 on 2009-04-20
> **Mark Phelps said:**
> If it DOES install, you won't be able to run KDE desktop -- so what is the point of installing Kubuntu?  Don't know if Xubuntu will even run with that little RAM.

You would do better to consider one of the minimal installs like DSL or Puppy Linux.  See the distrowatch.com page for links.

I agree Puppy Linux works well on underpowered computers. I prefer the customiability of Arch Linux

---

### Post by JeremyWorst on 2009-04-23
Thanks for all the responses.  I should correct that I'd like to install Xubuntu, not Kubuntu, on the laptop.  I did have Xubuntu on it a while back which I installed by removing the HD and putting it into another laptop with an integrated CD drive and 512MB RAM, installing Xubuntu and then moving the HD back into the Toshiba.  Had some video issues, but worked right well otherwise.  As I recall DL'ing updates went smoothly until a new version was released and then it wanted 192MB RAM to install, not 128MB.  And 'back in the day', 128MB was a LOT of RAM for a PII laptop!
Jeremy

---

### Post by FaizanKazi on 2009-04-23
thats absolutely true... it was a lot of ram! see if you can get an extra stick and i assure you youll get it really dirt cheap :)
i wish any of my old pcs had survived... i could use a server/test machine. i killed em all by over clocking and sold the remaining components :s

try not to install it on a separate machine and then put the hard drive back. if you grab the "alternate install" cd you can install it easily. or you could just do a text mode install. its really not that bad! :)

EDIT: oh and if its easy, you could actually swap the memory between the machines just for the install. double check they are compatible types (pc 100 and ddr are not compatible) and the p2 motherboard supports the 512 sticks memory speed (100 or 133 mhz are the common speeds, but your old p2 motherboard may or may not support 133).

> **JeremyWorst said:**
> Thanks for all the responses.  I should correct that I'd like to install Xubuntu, not Kubuntu, on the laptop.  I did have Xubuntu on it a while back which I installed by removing the HD and putting it into another laptop with an integrated CD drive and 512MB RAM, installing Xubuntu and then moving the HD back into the Toshiba.  Had some video issues, but worked right well otherwise.  As I recall DL'ing updates went smoothly until a new version was released and then it wanted 192MB RAM to install, not 128MB.  And 'back in the day', 128MB was a LOT of RAM for a PII laptop!
Jeremy

---

