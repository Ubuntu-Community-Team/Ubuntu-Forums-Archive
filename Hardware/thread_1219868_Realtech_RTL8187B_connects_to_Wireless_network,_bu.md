---
title: "Realtech RTL8187B connects to Wireless network, but I cant browse the Internet"
date: 2009-07-22
forum: Hardware
---

### Post by Tommii on 2009-07-22
Hi!

I just installed the Ubuntu 9.04 on an Fujitsu-Siemens Amilo Pi3525. lsusb shows that I have a **Realtek RTL8187B** in it. I found here some threads about Ndiswrapper, but I don`t think it is the solution. 
The notebook is able to connect to wireless networks, right now it`s also connected. However, _**I cannot browse the internet, even if it is connected to a wireless network**_. 
I found [this site]("http://briancantin.blogspot.com/2007/11/hacking-rtl8187b-on-linux.html"), downloaded rtl8187b-modified-jadams-2-1-2008.tar.gz and tried to run ./makedrv but without success. Anyway I don`t know if I need this or the Ndiswrapper if I am able to connect to wireless networks. 

Could you help me with this problem? Thanks a lot.

---

### Post by bryonak on 2009-07-22
Realtek is fairly standard and should be supported by default.
However if it's a new chip it still might have glitches...


Could you post the terminal output of ```
iwconfig
``````
sudo dhclient
```and```
ping google.com
```


Also some mainboards have the problem of not initialising the wifi card properly on reboots, which means you have to turn the machine off completely. It's a rare error case, but I saw it just 2 weeks ago on a PC dualbooting Ubuntu and Windows.

---

### Post by user 123 on 2009-08-04
I have had many problems with the driver for the rtl8187b. However if you install the linux-backports-modules package in synaptic or from the terminal it completely solves it.

# For Ubuntu 8.10 Intrepid users:
sudo apt-get install linux-backports-modules-intrepid

# For Ubuntu 9.04 Jaunty users:
sudo apt-get install linux-backports-modules-jaunty

You may have to check you have all of the correct repositories enabled, in the case backports.

---

### Post by leodp on 2009-08-04
Hi, I have a different ralink (RA2500) wireless card.
Mine has the same problem. Looks like it is not correctly picking up the transmission rate.

try something like:
sudo iwconfig wlan0 rate 54M

Where instead of 54M you use the rate of your router.
Infos on the bug here, if I an right:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515)
Leodp

---

### Post by Tommii on 2009-10-06
Thank you for your help and sorry I haven`t been here for a long time. I finally solved the problem with ndiswrapper and a XP driver after what I set the wlan rate to 11M.

Thanks.

---

