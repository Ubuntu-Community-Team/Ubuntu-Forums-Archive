---
title: "Broadcom Wireless"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by StandardBlueCaboose on 2007-04-11
I've been trying to get the wireless working on my mother's laptop. I told her that Linux is better than Windows Vista. But, alas, the wireless did not work, along with a host of other problems. I've managed to work out the other problems on my own, however, every attempt I make at setting up the wireless has failed. 

Her laptop has a "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)" wireless card. 

I was wondering if somebody could not only point me to a forum that can help me, but also tell me how to clear what I have done with ndiswrapper so far, so I can start over.

Thank you

---

### Post by rustybronco on 2007-04-11
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

haven't tried it YET, tomorrow I will though.

---

### Post by jputman01 on 2007-04-11
i believe to remove any ndiswrapper that you have done before you can use 

```
sudo rmmod ndiswrapper
sudo aptitude purge ^ndis~n
```

---

### Post by jputman01 on 2007-04-11
also, you can check here and see if you are using the correct driver: [ndiswrapper list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")
there are a couple listed for the card you have so you may need to try some different ones.

i'm not sure what version of ubuntu you are using or any of your other hardware specs but these are the exact steps I used to get my broadcom 4311 card to work on my hp laptop, you will need to replace my driver (bcmwl5.inf) with your driver, i got mine off of the hp website. I wrote this up for myself in case I ever had to do it again...maybe it will help you!

**Get Correct Driver:**
Create directory for drive to be installed- bcm4311
Get correct SoftPaq from HP- sp33008.exe
Place sp33008.exe in the bcm4311 folder
Run:
	```
sudo apt-get install cabextract
```
Go to the bcm4311 directory and run:
	```
sudo cabextract sp33008.exe
```
Verify that the bcmwl5.inf and .sys are now in the folder bcm4311

**Remove the 43xx driver:**
Run:
	```
sudo rmmod bcm43xx
echo &#8220;blacklist bcm43xx&#8221; | sudo tee &#8211;a /etc/modprobe.d/blacklist
```
	or ```
sudo gedit /etc/modprobe.d/blacklist [and add bcm43xx to list]
```

**Remove any old version of ndiswrappper:**
Run:
	```
sudo rmmod ndiswrapper
sudo aptitude purge ^ndis~n
```

**Build and install ndiswrapper:**
Run:
```
sudo aptitude install build-essential linux-headers-`uname -r`
cd /tmp && wget http://umn.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.39.tar.gz && tar zxvf ndiswrapper-1.39.tar.gz && cd ndiswrapper-1.39 && make && sudo make install
```

**Install driver into ndiswrapper:**
	```
sudo ndiswrapper &#8211;I bcmwl5.inf
```

**Make sure it works:**
	```
ndiswrapper &#8211;l
```
**Alias the device:**
	```
sudo ndiswrapper &#8211;m
```
**Load the kernel module:**
	```
sudo modprobe ndiswrapper
```

**Comment out all interfaces except lo device (add # symbol in front of all other entries)**
	```
sudo gedit /etc/network/interfaces
```

**Make sure ndiswrapper loads automatically at boot:**
	```
Echo &#8220;ndiswrapper&#8221; | sudo tee &#8211;a /etc/modules
```
	or ```
sudo gedit /etc/modules [and add ndiswrapper to the list of modules]
```

LIGHT SHOULD BE ON!!


hope this helps you, just replace all my references to 4311 and bcmwl5.inf with your card number and driver!!

---

