---
title: "D-Link Wireless USB Adapter problem"
date: 2010-10-13
forum: Hardware
---

### Post by Aleksandar_B on 2010-10-13
I recently got D-Link DWL-G122 Wireless USB adapter and wanted to use it to connect to my router through Ubuntu 10.04. I use it in dual-boot with Windows 7 and the wireless adapter works without a problem there, but not in Ubuntu.

After searching the web I have found that this is a common adapter and that support for it exists/has existed but not sure does that mean out-of-the-box support or does it require some adjustments.

After connecting the adapter through USB interface the network notification areas shows that the adapter is recognized (pic_1.png), but it doesn't show any networks, just for comparison i have tried to use it on Windows and it shows and connects to my network. 

I'm new to Linux in general so I have no idea how to solve this, so I would appreciate any help.

---

### Post by Magic_Spehar on 2010-10-14
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

### Post by Aleksandar_B on 2010-10-14
Thanks, worked like a charm.

---

