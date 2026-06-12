---
title: "Ubuntu on 8GB Flashdrive to use as both installer and liveCD"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by enduser000 on 2009-02-19
Hello,
     I've been running ubuntu as my main for some time now and the time has come to spread it around.  After seeing the compiz/beryl cube and animations a few of my friends would like to install ubuntu.  So I have been running around trying to install it, or preparing them to.
     My issue is this: I would like to have a liveCD of ubuntu on my flashdrive, to show people, and to work on other computers.  But, I would also (more importantly) would like to have an updated liveCD that can install ubuntu.
     So I have a few questions...
1. If you use System->Administration->Create a USB startup disk to install ubuntu on someones computer, will it install the updates/apps/settings (like themes or wallpaper) you currently have on the disk? or at least the updates?

2. Can you install multiple distributions of ubuntu or even other OS's on one stick? It would be great to be able to use different distributions and cool to be able to install them as different people need or like different things.

3. Is there a problem with installing on an 8GB flashdrive? I poked around a bit beforehand and found some users were having issues with it, though some weren't ([http://ubuntuforums.org/showthread.php?t=968243&highlight=USB+startup+disk&page=3](http://ubuntuforums.org/showthread.php?t=968243&highlight=USB+startup+disk&page=3)).

4. Can you install ubuntu from a regular installation? (ie, I install ubuntu/kubuntu/xubuntu on my flashdrive and then try to install on other peoples machines).  This would be good (though probably not realistic) because I am much more familiar with the regular install and configuration of ubuntu and it's deravites (especially when using GRUB).

     Any help or suggestions are appreciated.  Thanks for taking the time to read this lenghty post and I hope to hear from you soon.

enduser

---

### Post by bryanl on 2009-02-19
use [remasterysy](http://www.remastersys.klikit-linux.com/) with the isotostick script or [unetbootin](http://unetbootin.sourceforge.net/) to set up the iso on your stick.

First thing is to install all the updates and packages you want in your 'distribution' and then use remastersys to create a bootable iso image of that setup. You can either burn the iso to a DVD or to a USB drive and go from there

---

### Post by enduser000 on 2009-02-19
Thanks for the reply,
     So if I get this image working (it's been failing on updating the kernel then won't boot using "Make a USB startup disk" in ubuntu) and install all this stuff, then restore it to the USB drive, along with others (same thing for those), would I be able to put grub on it and have multiple custom "liveCD"s that will install as well? What about persistence?  Anyways I'll give it a shot when I have some time, thanks again,

enduser

EDIT: read the remastersys page, it's pretty cool.  I'll get on that soon. Thanks,

enduser

---

