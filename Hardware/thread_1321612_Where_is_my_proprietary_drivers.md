---
title: "Where is my proprietary drivers?"
date: 2009-11-10
forum: Hardware
---

### Post by oktay_y2003 on 2009-11-10
I had 9.04 on my HP Pavilion DV6570, everything worked fine until I decided to install 9.10. I installed a fresh setup and now I can't use my broadcom wireless, when I go to Hardware drivers to enable proprietary drivers there is nothing to activate, no wireless driver, no graphic driver!
Therefor I use wired connection to internet, but every time I restart the system I have to unplug the cable and plug it again so that the connection be established.
I am disappointed with this Koala!

---

### Post by CyberWind on 2009-11-10
Look at the kernel version currently loaded in your system. Apparently, you now use the kernel from the previous version of ubuntu. Editing menu.lst file should helps you.

---

### Post by tonafernandez on 2009-11-10
i have something similar of a problem, was running Jaunty and after i did a CLEAN install after formatting the drive im stuck with no propietary drivers, i have a workaround after downloading the drivers from broadcom, but i have to rmmod an ssd driver then insmod the wl.ko driver by broadcom, still have not figured out how to do this on startup so any help will be appreciated
here is the link
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by tonafernandez on 2009-11-10
From thread
[http://ubuntuforums.org/showthread.php?t=1280375](http://ubuntuforums.org/showthread.php?t=1280375)

it looks simple enough 
sudo apt-get install bcmwl-kernel-source and dkms packages
you can do this from synaptics as well

i will try later @ home

---

### Post by oktay_y2003 on 2009-11-10
Thank for helps!
It is srange that using Koala as live cd the drivers are available, but after installation, the driver list is empty. It is worth mentioning that during installation I get a crash report about some program, I can't remember the name right now!
I'll try to install packages using synaptic or terminal anyway. I hope it works!

---

### Post by oktay_y2003 on 2009-11-11
I used synaptic and installed bcmwl package, and now wireless is working! Strange that after installing wireless driver, I can now see the graphic proprietary driver in hardware drivers list!

---

### Post by Topher88 on 2009-11-11
> **tonafernandez said:**
> From thread
[http://ubuntuforums.org/showthread.php?t=1280375](http://ubuntuforums.org/showthread.php?t=1280375)

it looks simple enough 
sudo apt-get install bcmwl-kernel-source and dkms packages
you can do this from synaptics as well

i will try later @ home

You rock!  I had the exact same problem as the OP, and this seems to have done the trick!  Thanks!

---

