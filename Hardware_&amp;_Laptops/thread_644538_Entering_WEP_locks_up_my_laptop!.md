---
title: "Entering WEP locks up my laptop!"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by bipolarpenguin on 2007-12-19
I am using a Gateway MT3422 Laptop.  It uses the Real Tek 8185 wifi card.  There have been other posts about it not being detected or functioning properly but this is a lot different.

Everything is detected and running fine.  However if I manually configure or pick my network up as soon as I enter my WEP and press <enter>the entire machine locks up.  This happens every time.  I have done 2 clean installs just to be safe.  

Does anyone have any suggestions?


Thanks

---

### Post by naja on 2007-12-19
Hi 
I have the same chipset in my PCMICA-Card. I am using Ndiswrapper thoug there is an opensource-driver but it didnt work,i ll maybe compile the newest driver later,but for now ndiswrapper is doing the job.
First Blacklist the rtl Driver by adding this lines to /etc/modprobe.d/blacklist:
# Bad r8180 linux driver
blacklist r8180
blacklist rt73usb

I dont remember why is the second driver is blacklisted.
then search for ndiswrapper in Synaptic and install all 3 pakages,there are something like that:
Ndiswrapper common
ndiswrapper util
ndisgtk

Then you can start Windowsdrivermanager -ndisgtk- from Adminsitration-menu.Choose your driver (I use Winxp driver)

even after getting the ndiswrapper to work,i couldnt use the card as i wanted,so ive installed wicd
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
be WARNED it will remove some networkmanger -cant remeber which one-
after that reboot and start wicd,it will choose wext as driver (ndiswrapper) and you will see available networks.you can configure your network there.Once you do this,you dont have to launch wicd to connect each time you start your system,because it has already a daemon that starts at boot time.

I hope it would help

---

