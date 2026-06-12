---
title: "Feisty on Sony XG500"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by Rsolo57 on 2007-09-11
Hello Ubuntu Forums,

First time Ubuntu user here. Just recently installed Feisty Fawn on my laptop, Sony XG500. I have everything but the PCMCIA slots working. I have the driver for my PCMCIA wireless adapter, Trendnet TEW-421pc, installed. The card doesn't power on. I've tried both PCMCIA slots on the laptop and one on the docking station. When I use dual boot and go into the old Window XP partition the card powers on and works. Do I need to look at the PCMCIA driver? Any and all help is appreciated. I've done numerous searches on google and various forums but haven't found a solution.

-R

---

### Post by Rsolo57 on 2007-09-12
Solution:

-Re-installed Ubuntu.
-Downloaded all updates.
-Downloaded these files to /home/user/ directory: note: (user=login name)
   1.

      [WWW] [http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)
   2.

      [WWW] [http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)
   3.

      [WWW] [http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk)

-Installed using command line in the numerical order

1.) sudo dpkg -i ndiswrapper-common_*.deb
2.) sudo dpkg -i ndiswrapper-utils*.deb
3.) sudo dpkg -i --force-depends ndisgtk_*.deb
  
-Downloaded device driver from Manufacture website.
-Followed exact instructions for ndiswrapper.

The problem was, I was unable to point ndiswrapper to the driver location. ie. sudo ndiswrapper -i ~/user/drivers/windows xp/ devicedrivername.inf, probably because I'm a little sketchy on directory navagation. To fix this I used cd to change to the directory that had my device driver. and ran: sudo ndiswrapper -i devicedrivername.inf and bingo!! ndiswrapper -l shows device present and driver installed, reboot and all is well. 

One thing I didn't know was you had to have all other files associated with the INF file. My driver came with a .cat and .sys file and without those ndiswrapper kept saying invalid driver. Just make sure you have the other files in the same directory as the INF file and ndiswrapper will pull everything it needs. Most of the 
How To's I've seen lack the simplest details for the newbie (albeit my solution lacks a lot as well)  that is in all of us. Anyway thanks for the great forums and the endless amount of information!

-R

---

