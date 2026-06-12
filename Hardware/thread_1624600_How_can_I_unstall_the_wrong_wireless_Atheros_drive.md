---
title: "How can I unstall the wrong wireless Atheros driver?"
date: 2010-11-17
forum: Hardware
---

### Post by pmueller on 2010-11-17
Hi,

How do I uninstall the installed wireless driver, Atheros 5001?  I am running Maverick or Ubuntu 10.10.  The version that I need for my wireless is Atheros 5007.  I have been running Ubuntu and Mint in previous version and this is the first time that I have had problems with the wireless install.  My computer is a Compaq CQ50-210US.

Any ideas are appreciated.

Paul

---

### Post by pmueller on 2010-11-19
Bump

---

### Post by coffeecat on 2010-11-19
As far as I am aware, both of those Atheros chipsets use the same ath5k driver. However, the ath5k driver is in constant development so you may see variation from one version of Ubuntu to the next. The ath5k driver is in the kernel so an older release of Ubuntu will use an older driver. What version of Ubuntu did the wireless work in and what version is it not working in? What exactly are the problems you are encountering?

---

### Post by scottmcarthur on 2010-11-19
[FONT=Arial]My cq50 is using the ath9k driver i believe.  I am not near my laptop right now, but I had a ton of problems under 10.10 and found that it was software locked for some reason.  I spent a week thinking it was a driver issue.  You might try this:

run [/FONT]```
rfkill  list
```[FONT=Courier New][FONT=Arial] [FONT=Verdana]to see if it is locked and if it is software locked like mine was, you can run [/FONT][/FONT][/FONT]```
rfkill unblock wlan
``` to unblock it.

Other than that, I would suggest checking out this wireless guide:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers)

---

### Post by pmueller on 2010-11-19
Hi.

I tried Scott's suggestion and it worked! Now I can see wireless networks in my area. 

When I ran in terminal:

rfkill  list

I got back:

0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

Running "rfkill unblock wlan" unblocked it right away.

For the record I used to run Mint Isadora and before that Ubuntu 7.04 through 9.10 on this laptop.

Thanks to all,

Paul

---

