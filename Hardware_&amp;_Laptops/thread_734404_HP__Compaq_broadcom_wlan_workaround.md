---
title: "HP / Compaq broadcom wlan workaround"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by sir4taye on 2008-03-24
Presario f730us, amd64x2, Ubuntu 8.04
broadcom 4311, nvidia 6200

This will get your wireless working in 7.10 or less. I'm still working on the 8.04 workaround)
everything inbetween # signs (without the #signs themselves) needs to be typed into a terminal screen (under applications then accessories then terminal -this is the command line, somewhat like dos)

1)you must uninstall ndiswrapper & bcm43xx-fwcutter 

#sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9#
#sudo apt-get remove bcm43xx-fwcutter# 

2)Add bcm43xx to the /etc/modprobe.d/blacklist file (b43 if you're using 8.04)

#sudo gedit /etc/modprobe.d/blacklist#
a text editor will activate add thes 2 lines "blacklist bcm43xx" (without the "")
3)Reboot
#sudo reboot#

Download driver for BCM94311MCG wlan mini-PCI here:
http://www.stosha.net/WLANBroadcom.tar.gz or
http://stosha.stylet-software.com/WLANBroadcom.tar.gz

#cd ~/Desktop#

#tar -xzvf WLANBroadcom.tar.gz#

4)move the folder WLANBroadcom to your home directory

#mv WLANBroadcom/ /home/(yourusername)/#

5)Install ndiswrapper from source :

#sudo apt-get update#
#sudo apt-get install build-essential#
#sudo apt-get install linux-headers-`uname -r`#
#sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build#
#mkdir -p ~/bcm43xx/ndiswrapper#
#cd ~/bcm43xx/ndiswrapper#
#sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?modtime=1193538074&big_mirror=0#
#tar -xvzf ndiswrapper-1.49.tar.gz#
#cd ndiswrapper-1.49#
#make distclean#
#make#
#sudo make install#

6)Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper

#cd /home/yourname/WLANBroadcom/#

#sudo ndiswrapper -i bcmwl5.inf#

#ndiswrapper -l#

#sudo gedit /etc/modules#
an editor will activate add this line "ndiswrapper" (without "")

#sudo modprobe ndiswrapper#

#sudo ndiswrapper -m#

7)Reboot
#sudo reboot#

---

### Post by FALSEFLAG on 2008-03-26
my soon to be eliminated vista has a bcmwl6.inf, I wonder if subbing that for bcmwl5.inf would be good, bad, better, worse, indifferent?

---

### Post by FALSEFLAG on 2008-03-26
I'll totally try this in 804 if you send me a working torrent link to BSG-razor :-) its a cointoss risk against a reinstall but I'm fully committed to heron now so let see how many BC cards we can get online? 
Deal or no Deal?

---

