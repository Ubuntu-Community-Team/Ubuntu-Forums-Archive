---
title: "Dropped connections with ipw2200"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by Arthemys on 2005-05-19
I have an Intel 2200 series wireless card that does work with Ubuntu, however the card sometimes stops working entirely and I need to reboot in order to get it to work again. Or sometimes it won't associate to certain APs randomly, that only moments earlier, worked fine.

I believe there is a new version of this driver out, however I'd like to compare the version that I have installed now (which I'm not sure how to obtain) and see if this is a common problem with my version / card model.

Thanks!

---

### Post by luca_linux on 2005-05-19
Type this at console to see you current version:
```
dmesg | grep ipw
```
Anyway, I think you'd better update ipw2200 driver to the latest available, if it isn't, as well as the firmware.
Here's a howto if you need: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by Arthemys on 2005-05-19
> 
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: ipw-2.3-boot.fw load failed: Reason -2
ipw2200: Unable to load firmware: 0xFFFFFFFE
ipw2200: failed to register network device
ipw2200: probe of 0000:02:02.0 failed with error -5


That's what I get now when I boot.

Should I back the driver itself down one version because that version of the FW isn't on their site?

---

### Post by luca_linux on 2005-05-19
I've just updated the ipw2200 driver from 1.0.3 to 1.0.4. I've just followed my howto.
Are you sure you have downloaded the latest firmware and placed all the files included in the archive in /usr/lib/hotplug/firmware and removed the old ones?

---

### Post by Arthemys on 2005-05-19
I brought it down to 1.0.3 and it's happy now, but from what the error message sounds like, is that it's looking for a newer version of the firmware. Newer than 2.2

---

### Post by luca_linux on 2005-05-19
In fact you have to install the latest firmware that is 2.3.

---

### Post by Arthemys on 2005-05-19
I only saw 2.2 on their site, did I miss it?

---

### Post by luca_linux on 2005-05-19
Go here: [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)
Or directly here: [http://ipw2200.sourceforge.net/firmware.php?fid=5](http://ipw2200.sourceforge.net/firmware.php?fid=5)

---

### Post by Arthemys on 2005-05-19
I -swear- that wasn't there a few hours ago. :-?

Oh well, is there a great need to go up to 1.0.4 from 1.0.3?

---

### Post by luca_linux on 2005-05-19
Yes, if you often use the suspend functions of you laptop: in fact there've been many fixes, especially about the power managemente stuff.
Anyway it's always a good thing to updating the drivers.
For example also the AP scanning has been improved.

---

### Post by Arthemys on 2005-05-19
I probably should have just read the changelog. Thanks! :)

---

### Post by ewinslow on 2005-06-25
I see this thread hasn't been active, but I'm seeing this behavior after coming out of hibernation. I just upgraded the firmware to 2.3 and the driver to 1.0.4, but that hasn't solved it. I'm getting the same exact error messages that Arthemys posted earlier in this thread.

Upon reboot everything loads fine, but eth1 is down and out after hibernation.

---

### Post by yang on 2005-06-26
Arthemys, did upgrading both the driver and firmware end up fixing the problem for you? (I'm guessing from your final post that it did.) How do I find out which version of the firmware I have?

Also, is there any chance that such updates can be done via apt or some other easy-to-use update system (instead of manually following the HOWTO and having a zillion things not go according to the HOWTO and losing all my hair :)? This relates to [http://ubuntuforums.org/showthread.php?t=43891&highlight=ipw2200](http://ubuntuforums.org/showthread.php?t=43891&highlight=ipw2200).

I ask these questions because I'm interested in knowing whether I should bother trying to go through the hassle of updating the driver. I think I am having the exact same problem. After some amount of time, my wireless card simply stops working (fails to associate with the network it was just using). My attempts to remove/readd the module (modprobe -r ipw2200; modprobe ipw2200) don't work either.

---

### Post by damotor on 2005-06-27
Hi.
I'm having same problem with a fujitsu-siemens m 1425 and a ipw2200, my parameters are:
iwconfig eth1 essid pc channel 6 mode Ad-Hoc key off

And there, while I'm serving a webpage or wathever, connection drops.

dmesg | grep ipw2200 returns:
ipw2200: Intel (R) PRO/Wireless 2200/2915 Network Driver, 1.0.4
ipw2200: Copyright (c) 2003.2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Firmware error detected. Restarting.
ipw2200: Firmware error detected. Restarting.
ipw2200: failed to ASSOCIATE command

It's quite weird because both pc's are quite near and when I made ping, at the beggining all are transmited ok, but after some seconds, they're lost, then appear messages like "Destination Host Unreachable" and there the packets are transmited ok for a while.

---

