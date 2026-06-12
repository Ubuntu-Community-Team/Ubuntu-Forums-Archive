---
title: "HP zv6131 BCM4318 drops config intermittently"
date: 2010-03-29
forum: Hardware
---

### Post by SaudiZeus on 2010-03-29
After installing 9.10 on my HP zv6131, and then installing the b43-fwcutter, I was finally able to get my Broadcom wireless working reliably, or so it seemed.  Later, after applying the 274 updates the update manager recommended, I could get the card working after initial boot, but anywhere from 1 to 6 hours later, it would suddenly stop and, while the network manager still reported the connection active, iwconfig would show that it had lost all of the wireless settings (i.e., SSID, encryption settings, etc.).  

Enabling and disabling the device with the wireless button had no effect, nor did either ifup/ifdown wlan0 or ifconfig wlan0 up/down.  The only action that got the wireless working again was a reboot, and then only until it decided to drop again.

/var/log/messages showed nothing, but /var/log/debug showed a series of disassociations, followed by new associations, that occurred over a several-minute period just preceding the drops.  The last entry reported that it had disassociated due to a local choice.  What that choice was is a mystery, as no one was using the laptop at the time.

I've had a devil of a time finally getting this chip to work, and I am frustrated that it is again dropping out.  Any assistance or guidance would be much appreciated!

---

