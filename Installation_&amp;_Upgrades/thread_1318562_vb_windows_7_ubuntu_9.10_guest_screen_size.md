---
title: "vb windows 7 ubuntu 9.10 guest screen size"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by broekskw on 2009-11-07
ok have windows 7 64bit running as a host and trying to get ubuntu 9.10 64-bit as a guest, did a fresh install but can not get my screen size on the ubuntu anything bigger then 800x600. my xorg.conf file is empty and when i try to select my screen display under system preference display i get an error "it appears that your graphics driver does not support the necessary extensions to use this tool. do you want to use your graphics driver vendors tool instead. if i select yes another error screen comes up " there was a problem initializing catalyst control center linux edition. no ati graphics driver is installed;

this is a guest inside of vb, do i have to install the graphic driver?? under ubuntu software center i have installed
1.ati binary x.org driver
2. ati catalyst control center

what gives

thanks
:lolflag:

---

### Post by Yvan300 on 2009-11-07
You have to use the virtual box guest additions iso to install a driver.

---

### Post by broekskw on 2009-11-07
ok followed a guide on the guest additions with no luck,
can not find out what the problem is

---

### Post by Yvan300 on 2009-11-08
What was the problem, were you able to install the guest additions and if so then switch to full screen mode and see if the resolution changes.

---

### Post by Scunizi on 2009-11-08
If you didn't, then install the guest additions from terminal.. mount the iso for guest additions in the gui then open the terminal and "cd /media/cdrom0"  .. from there sudo ./<64 bit version of guest additions file> .. then restart the guest.. you should now be able to ctrl+f for full screen (crtl+f to revert to windowed mode).

---

