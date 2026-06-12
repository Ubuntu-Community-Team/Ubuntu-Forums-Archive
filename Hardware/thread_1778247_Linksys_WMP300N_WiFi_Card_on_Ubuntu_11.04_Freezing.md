---
title: "Linksys WMP300N WiFi Card on Ubuntu 11.04 Freezing/Can't Install via NDISWrapper"
date: 2011-06-08
forum: Hardware
---

### Post by akira7799 on 2011-06-08
Hello All, 

I've just installed Ubuntu 11.04 on my system.  I quit Windows cold-turkey and am new to Ubuntu.  I noticed that my Linksys WMP300N WiFi Card was given Broadcom drivers during install.  This caused the system to become unresponsive (freeze) after a few minutes of light network traffic.

I did some research and learned that I could use NDISWrapper to install the Windows version of the requisite driver.   I'm not sure what happened, but the install didn't work.  

Under the Wireless Networks section of the Connections drop-down menu I now have the error "device not ready (firmware missing).  

I can only connect (to the internet) now via hard-line ethernet cord.  

Can anyone point me in a direction of getting the WiFi card installed correctly?  Has anyone dealt with this problem in the past?  

Please let me know what steps I need to take in order to get this 35 foot ethernet cord unplugged from my computer.

Thanks, 
Dave

---

### Post by akira7799 on 2011-06-14
Hey All,

I just wanted to let everyone know that I was able to fix the driver stability issue with my Linksys WMP300N on Ubuntu 11.04 Natty 64 bit.   Just to let everyone know, my WMP300N is at PCI Bus address: 04:08.0 with device ID 14E4:4329.

I needed to blacklist the following drivers:
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist wl

Then I rebooted.

I then installed ndiswrapper and the "ORIGINAL" BCMWL5 drivers.  I'm going to try and attach them for anyone else who'll need em in the future.

Ubuntu recognized the new ones immediately.  

Hope it helps someone in the future,
Dave

---

### Post by eye_try_very_hard on 2011-09-21
Sorry to resurrect this, but I'm having problems with the same card and can't find a way to get it to work.  I even went from 64 to 32 to try to simplify things and still no dice.  It says it installs and the device is there but there's no wlan entry and obviously no connection. I've tried 3 different drivers through ndiswrapper all to no avail.  All help greatly appreciated!

---

