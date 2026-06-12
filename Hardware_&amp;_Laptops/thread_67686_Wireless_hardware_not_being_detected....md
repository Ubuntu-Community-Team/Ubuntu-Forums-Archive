---
title: "Wireless hardware not being detected..."
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by KageKeeper on 2005-09-21
Hi all...

I know there are lots of people that have issues with wireless and laptops..

I did search, but could not find anything that I was looking for.

I have a Compaq Presario V4000 laptop. It uses a Broadcom for wireles. It is integrated. I got the bcmwl5 inf and sys files from my windows install before I wiped and put Ubuntu on it.

My wireless light was on  initially when I first installed. 

I went through the various How To's for installing ndiswrapper. Everything seems ok there.

When I enter:

```
ndiswrapper -l
``` 

It tells me the driver is installed, but does not say the hardware is present and my wireless light is off.

So, I am baffled as to why it appears as if my wireless adapter is not even being detected.

Any thoughts?

I appreciate it!

---

### Post by moephan on 2005-09-25
I'm no expert, but I'm wondering if perhaps the ndiswrapper is not loaded. If you go to System > Administration > Network settings, there should be an entry called "Wireless connection." If it's not in there, close the Network settings applets and try:

sudo modprobe ndiswrapper

Your wireless light should come on at this point. However, you may still not be able to connect. In this case, start the Network settings applet again and you should see Wireless connection in there at this point. Select it and click the Properties button. Check the checkbox for "This device is conifigured." Select your wireless access point in the "Network name" drop down and enter a WEP key if required. Set the "Configuration" drop down to DHCP. Click OK. You may need to Deactivate and Reactivate the connection before it works.

HTH.

Cheers, Rick

---

### Post by KageKeeper on 2005-09-25
[QUOTE=moephan]I'm no expert, but I'm wondering if perhaps the ndiswrapper is not loaded. If you go to System > Administration > Network settings, there should be an entry called "Wireless connection." If it's not in there, close the Network settings applets and try:

sudo modprobe ndiswrapper

Your wireless light should come on at this point. However, you may still not be able to connect. In this case, start the Network settings applet again and you should see Wireless connection in there at this point. Select it and click the Properties button. Check the checkbox for "This device is conifigured." Select your wireless access point in the "Network name" drop down and enter a WEP key if required. Set the "Configuration" drop down to DHCP. Click OK. You may need to Deactivate and Reactivate the connection before it works.

HTH.

Cheers, Rick[/QUOTE]

Thanks, but I have done that. modprobing ndiswrapper does indeed load it, but did not help in the detection of my hardware.

Thanks again. :)

---

### Post by towsonu2003 on 2005-10-09
Did you try the driver files (the same name) from the windows install CD? You will have to go to a friend with windows or use vine (or WINE?) in linux to unpack the .exe file (I think it was under swsetup/wlan/) in the install CD. 
If 
ndiswrapper -l 
does not say that hardware is present, then I am pretty sure you have the wrong driver file loaded. 
You could also download one from the ndiswrapper site. (See their page on how to find the appropriate driver files).

---

### Post by knappen on 2005-10-09
I second that. You probably have the wrong drivers.

Download the drivers for windows xp and install them with ndiswrapper.

ndiswrapper -i /path to drivers .inf file

---

### Post by skirkpatrick on 2005-10-09
The light doesn't necessarily come on.  On my HP laptop, the wifi LED is always on when it is enabled but on my son's Acer, the light flashes during wifi activity but off otherwise.

---

### Post by knappen on 2005-10-09
Some cards have both a Link and an Activity led. Perhaps you ony have an Activity led...

---

### Post by skirkpatrick on 2005-10-09
On my son's Acer, it only has one LED.  Under Windows, it is on all the time but only shows activity under Linux.

---

