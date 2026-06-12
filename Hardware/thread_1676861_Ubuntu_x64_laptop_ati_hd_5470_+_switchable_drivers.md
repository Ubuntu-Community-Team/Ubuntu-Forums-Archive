---
title: "Ubuntu x64 laptop ati hd 5470 + switchable drivers"
date: 2011-01-27
forum: Hardware
---

### Post by Filenotfoundx404 on 2011-01-27
Well i got a new laptop and decided to dual boot windows 7 x64 and  Ubuntu 10.10 x64. Been playing around with it and i really like Ubuntu.  But having trouble on what drivers to install and how to get switchable  graphics to work.

This is what i have:
Acer Aspire 5553G Laptop
Windows7x64 + Ubuntu 10.0 x64 dual boot
ATI Radeon HD 4200 Integrated + ATI Radeon HD 5470 dedicated

I installed the ati proprietary drivers via additional drivers program,  but from the looks of it, its an older version, v10.1 CCC. And it only  detects the internal 4200. It seems 11.1 is the most recent.

i came across [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx) about installing it and [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics) about switching graphics, but i have a few questions to make sure im doing everything correctly.

in the installing link above it says to do:
```
$ cd ~/; mkdir catalyst11.1; cd catalyst11.1/
$ wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-1-x86.x86_64.run]("http://www2.ati.com/drivers/linux/ati-driver-installer-")
$ chmod +x ati-driver-installer-11-1-x86.x86_64.run

```Well is that file for desktop or laptop, hd4xxx or hd5xxx? does it even matter or will that work for all of the above?
Also would i need both the hd 4xxx and hd5xxx drivers since I have 4200 integrated and 5470 dedicated?

Another thing, from doing it this way(via terminal), would there be any  differences then if you just went to the amd website, downloaded the  right version(ie mobile hd5xxx for linux64) and then just ran that? 



Next since i already have ati drivers and CCC installed, which command would be better to remove it? that page lists both:
```
$ sudo apt-get remove --purge xserver-xorg-video-radeon

```and
```
$ sudo sh /usr/share/ati/fglrx-uninstall.sh
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

```Which would get rid of everything for a cleaner install of newer  version? Or should/could i just go to additional drivers and under there  click remove to get rid of all of it?



And lastly about the switchable graphics, if the CCC doesnt have a built  in option for that (it does on windows7 version due to me having both  ati integrated and dedicated), and i have to use the switch scripts, how  will that affect windows when i run it after Ubuntu?
Like for example, i exit Ubuntu with the integrated graphics on, would  that mean when i log in windows it will be on integrated? or same thing  with dedicated.
Also what about using the script to shutdown with both turned on, what would happen then if i log into windows?

---

### Post by Filenotfoundx404 on 2011-01-28
Bump :3
<.<     >.>

---

### Post by Filenotfoundx404 on 2011-01-30
So no one knows or can elaborate on it?

---

### Post by xdominex on 2011-01-30
Hello, Filenotfoundx404.
I am having similar issues and hoped that the new ATI driver would solve the issue AND lend increased performance to my graphics card in Ubuntu. I don't have a solution, unfortunately, but I CAN tell you that the driver block vga switcheroo from loading, effectively disabling the ability to switch graphics cards. Also, I have the ATI install instructions which happen to have specific uninstall instructions as well. I have attached the document to this post.

---

### Post by zacharias-pt on 2011-03-06
i cant even install ubuntu. it just freazes screen like described here: [http://ubuntuforums.org/showthread.php?p=10528657#post10528657](http://ubuntuforums.org/showthread.php?p=10528657#post10528657)
any thoughts?

is it possible to have both gpu's working as fine as on Win7?
kudos

---

