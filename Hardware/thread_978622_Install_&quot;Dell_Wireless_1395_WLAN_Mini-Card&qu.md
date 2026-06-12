---
title: "Install &quot;Dell Wireless 1395 WLAN Mini-Card&quot; in Ubuntu"
date: 2008-11-11
forum: Hardware
---

### Post by J0ny on 2008-11-11
Hi, a few days ago I purchased a Dell Inspiron 1525 that came with Win Vista, immediately put ubuntu.

Was everything ok, except by the Wi-Fi (in win works), I found that it's not recognized. Search in Internet and find in ubuntu forum that i must to use the ndiswrapper to install win drivers. So I went to the Dell site, was downloaded the drivers for the plate and follow the instructions to post [here]("http://ubuntuforums.org/showthread.php?p=6045569#post6045569") (last post)

Now it would seem that I recognized wi-fi card (at least to pull  sudo lshw-C network, they list that) but do not know how to connect to Wi-Fi.

I understand I have to go to "manual network configuration" and there I would have to appear "wireless network" or something like that, but does not.

There is something I am doing wrong? I am missing something?

 	
Please excuse my English

Thank

---

### Post by J0ny on 2008-11-11
Please help me!!!!!!!!

---

### Post by rakihirou on 2008-11-16
you have to set the wireless connection.
use the network-manager or wicd to set if you're using WPA password etc.
the WPA2 is working on 8.10 only. I mean for inspiron 1525.

---

### Post by J0ny on 2008-11-19
The interface does not appear anywhere.

I do iwconfig and I get everything with "no wireless extensions".

Yesterday I upgrade to version 8.10.

---

### Post by kevinorin on 2009-02-19
Hey, I have the same adapter, did you ever find a fix? I am looking into solutions now.

Regards,

Kevin W
[www.kevinorin.com](www.kevinorin.com)

---

### Post by duanedesign on 2010-01-27
It looks like you need to use the ndiswrapper and the windows driver. This post walks through it.

[http://ubuntuforums.org/showthread.php?t=960628](http://ubuntuforums.org/showthread.php?t=960628)

---

### Post by ediazp on 2010-05-07
I have the same problem. I am on a Dell 1721 with the 1395 wireles card I did everithig I have found o the interet, and finally I see the wirelless ligth working., but I canot see any network, if I do iwconfig i get:

lo        no wireless extensions.

eth0      no wireless extensions.


Then if I do:
 ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4315) present (alternate driver: ssb)


So, the driver seems to be there but I cannot hit the internet! HELP PLEAAASE

Cheers,
Esteban

---

### Post by efflandt on 2010-05-08
If **sudo lspci -v** shows it as BCM 4312 (or 4311) you should not need ndiswrapper.  If you can temporarily connect to a wired network, that is easiest.  Otherwise you will need to insert your Ubuntu install CD, go to System > Adminstration > Synaptic, and check the box to add the CD to the repository.  Exit Synaptic.

Then go to System > Administration > Hardware Drivers, and activate Broadcom STA (not sure if you will need to reboot).  Then you should be able to configure it from System > Preferences > Network Connections > Wireless (although, in ifconfig -a it will appear to be eth instead of wlan).

If you added the install CD to the Synaptic repository, you can then go back to Synaptic and uncheck it.

---

