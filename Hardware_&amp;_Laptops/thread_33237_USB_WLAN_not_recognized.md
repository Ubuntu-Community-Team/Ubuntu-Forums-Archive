---
title: "USB WLAN not recognized"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by chewbacca810 on 2005-05-10
I bought 2 cheap usb wlan sticks and I am having trouble even getting them working.  First, when I plug the stick in, and unplug it, this is all I get:

```
usb 5-2: USB disconnect, address 4
usb 5-2: new high speed USB device using ehci_hcd and address 5
``` 

But, in the device manager, it shows up as "802.11g WLAN and Pen Drive".  Here's output of /proc/bus/usb/devices:

```
T:  Bus=05 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=148f ProdID=9020 Rev= 0.01
S:  Manufacturer=Ralink
S:  Product=802.11g WLAN + Pen Drive
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=300mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
``` 

I downloaded rt2500 source, compiled, and installed it okay, but sudo modprobe rt2500 doesn't do anything.  Anyway to get these things working?  Is it possible to edit something with hotplug to get it to load the rt2500 driver?  Any info would help.

thanks!

---

### Post by richbayliss on 2005-05-10
Hi,

I have a USB wireless adaptor. It is based on the Prism2_usb module. I recommend the NDISWrapper module - it is by far easier to setup.

STEPS:
1) sudo apt-get install ndiswrapper-utils   (i think thats the pkg)
2) Download the WindowsXP drivers from web/CD
3) Goto the folder, on HDD, where drivers are stored (I made a /usr/drivers/wifi folder for them)
4) Look for a .INF file, this should be the WindowsXP driver.
5) ndiswrapper -i foobar.inf  -- Encapsulates the driver
6) plug in the adaptor
7) modprobe ndiswrapper
8) iwconfig wlan0 -- should say something
9) iwconfig wlan0 essid JoeBloggs mode Ad-Hoc

This *should* give you an adhoc wifi network called "JoeBloggs". Then you need to use ifconfig/dhcp to set an IP.

Hope this is of use,

Rich

---

### Post by chewbacca810 on 2005-05-10
I just tried ndiswrapper (I tried before I went to sleep with no luck, but I never modprobe'd ndiswraper).  Anyways, the usb driver gets loaded okay, but still no driver for the usb stick:

```
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
``` 

Why isn't a driver loading for this?  I also tried adding my own .usermap in /etc/hotplug/usb:

```
rt2500  0x0003  0x148f  0x9020  0x0000  0x0000  0x00    0x00    0x00    0xff    0xff    0xff    0x00000000
``` 

Now, /var/log/messages gives me:

```
May 10 08:28:27 deimos kernel: usb 5-2: new high speed USB device using ehci_hc
$May 10 08:28:27 deimos usb.agent[9757]:      rt2500: loaded successfully
``` 

but, it still doesn't see the stick as anything.  Does this mean that this stick is completely unsupported, or is there a way to get the drivers to recognize the device still (maybe editing the code of the rt2500?) ?

---

### Post by chewbacca810 on 2005-05-10
Alright, I kept screwing around with ndiswrapper and I finally found out that for some reason, the conf file in /etc/ndiswrapper/rt2500 wasn't named right.  It was supposed to be 148f:9020.conf (the vendor and product id), but it was 148f:1234 (or something) renaming the file worked great.  BUT, it takes about 7-10 minutes for the driver to load, it just keeps reseting the usb device ( over 700 times ).  Anyone know a fix to this? 

thanks

---

