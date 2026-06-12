---
title: "Update - Wireless not work - madwifi hack - unable to boot into ubuntu"
date: 2008-10-15
forum: General Help
---

### Post by riodemes on 2008-10-15
Hello Everyone!

I'm not exactly why my problem is occurring, but I will do my best to explain.

Computer Specs:
Acer Extensa 5620Z Windows Vista with Ubuntu Hardy Partition
Intel T2370 Dual Core (1.73GHz)
2GB Ram
Wifi: I believe Wifi is via Atheros Hardware Layer (HAL) Hardware with Signal Up, not sure of specs.

Situation:
I updated today the system packages via update manager, and enabled them. I had previously had trouble with my wifi not working as it is not specifically supported and I use Madwifi to enable it. As usual, whenever I update some system files with the update manager, the wifi turns off, and I have to do a little Madwifi hack to enable it. It usually works but this time it didn't.

Here's the code I entered: 

tar xfz madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
make
sudo make install
sudo modprobe ath_pci
sudo reboot

which just installs the package I get from the madwifi databases, which I put into my homefolder and install. I'm not sure exactly what it does, but it gets my wifi to work, as it does not show up regularly on the Network Management applet.

What happens now: When I try to boot into Ubuntu 8.04 Hardy with linux kernel 2.6.24-21, it runs through everything but hangs after loading the networking wifi. I tried doing the system tools boot up and ran each one, but im not sure how to copy the code that my system spits out before it dies (if anyone knows just say and i can get it)

But when I boot into Ubuntu Hardy 2.6.29-19, everything works fine, and networking is alright. 

Quick Theories: 
1. I think my madwifi file is out of date and I need to install with a new one, but since I can't load into that kernel, because it stops when loading the networking hardware, I can't really change it without resorting to the command prompt (which I suck at)
2. I was thinking of trying this with the 2.6.29-19 kernel, but I don't want to risk having the same thing happen to this booter.

Any suggestions? I can provide details if needed. You people are all better versed with this stuff than I am haha. :lolflag:

Resources: Mad Wifi site: [http://madwifi.org/](http://madwifi.org/)

---

### Post by riodemes on 2008-10-17
bump

---

