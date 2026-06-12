---
title: "Wifi Help"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by pruett57 on 2005-04-07
Okay, well....i need help with getting and setting up my wifi.

I have an IBM TP R40, with the Cisco Aironet Wireless card (350).
I've downloaded the driver/utilities from Cisco and ran the script (after getting the correct libraries). 

I've tried to piece together things from other threads with ndiswrapper and kismet.


The problem is that Cisco's install help isn't much of a help and the nor are the how to's for ndiswrapper or kismet.

I'm trying here and want this to work!

Any help would be grateful!

Thank you,
jp

---

### Post by kermy on 2005-04-08
Have you tried the windows ndis driver with ndiswrapper? Does it load or what error do you get?

---

### Post by pruett57 on 2005-04-08
Nope, I haven't tried the windows driver but I did try the linux drivers from cisco.
I wasn't sure which driver to use (2k, xp, nt, 98, etc.) for ndis or really where to get it. 

Thanks

---

### Post by kermy on 2005-04-08
I think you should use the XP or 2000 driver, but ndis might be just ndis.. :)

---

### Post by pruett57 on 2005-04-08
okay, so I think it is up and running but don't have the best way to test it at the moment.

Are they some good commands I need to know?
Any good program that would allow me to just connect to wifi access points automagicly?

I've just downloaded airsnort, ifplugd, netapplet, prismstumbler and waproamd but could only get airsnort to work but it didn' find anything..

Thanks again,


jp

---

### Post by kermy on 2005-04-09
Using the command iwlist I can get a list of found access points:
[INDENT]sudo iwlist wlan0 scan[/INDENT]
It depends on wether you have no security, WEP or WPA how you should go further from this point. WEP and no security can be configured from /etc/network/interfaces (man interfaces), but WPA needs another program: wpa_supplicant (apt-get install wpasupplicant) I think you can search the forums here for more info.

Good luck!

---

### Post by uberlinux on 2005-04-15
I think we should have a cisco forum, considering that many people and business use cisco internetworking infrastructure and cisco dosent support anything. I think that there is a real need

---

