---
title: "DWL-G122 Rev D1 in Ubuntu 10.04"
date: 2010-09-12
forum: Hardware
---

### Post by tuibguy on 2010-09-12
Fresh install of 9.10 upgraded to 10.04 Ubuntu Lucid Linux

According to [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") USB adapter issue solved since release of 8.10. Ran lsusb and this displays

Bus 001 Device 002: ID 07d1:3b01 D-Link System AirPlus G DWL-G122 Wireless Adapter

and wireless networks not found.  able to find network with a laptop running 

What am I missing?

---

### Post by Magic_Spehar on 2010-10-16
Hi Tuibgy,

Try the following solution (already posted here by Tarzan). It worked for me with my G122 adapter when I had Ubuntu 10.04.

Be careful though not to upgrade your system to 10.10 because the default kernel doesn't work with the G122 adapter (you need to change your grub then so the kernel used is the former version and then it also works).

1. Download Linux driver for RT3070USB from [http://www.ralinktech.com/](http://www.ralinktech.com/) (Software -> Linux)

2. Unpack the tar & bz2 source package, be careful to don't leave spaces in the extracted directory name, open a terminal and go to contents' directory

3.
Code:
cp RT2870STACard.dat RT3070STACard.dat
cp RT2870STA.dat RT3070STA.dat
cp common/rt2870.bin common/rt3070.bin
sudo make
sudo make install
4. Add to /etc/modprobe.d/blacklist.conf
Code:
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta
5. Make a new dir and copy a RT2870 file in it:
Code:
sudo mkdir /etc/Wireless/RT2870STA
sudo cp /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
6. Add RT3070STA in /etc/modules

7. Restart the system

---

