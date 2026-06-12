---
title: "Broadcom bcm43228 disconnect/slow"
date: 2012-11-15
forum: Hardware
---

### Post by BramWillemsen on 2012-11-15
Hi,

My laptop (HP probook 6475b) has a Broadcom bcm43228 chip. The wireless does work, but it keeps disconnecting/slowing down all the time when I'm running Ubuntu. When working in Windows everything is faster and stable.

I installed the kernel source thingy, the STA driver, and tried a lot of the other suggestions a quick google brings up. Did anyone else experience similar connectivity problems? If someone has advice it would be greatly appreciated :) 

cheers,
Bram

I'm always on the same campus network. Could it be that I somehow badly configured this specific network in Ubuntu and that it is not a driver thing? I'm running Ubuntu 12.10 Btw

---

### Post by wildmanne39 on 2012-11-15
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by BramWillemsen on 2012-11-15
Thanks Wild Man,

I ran the script and attached the result here.

Bram

(P.S. I had to put it in an archive since the max text file size I could upload here was 19.5kb(

---

### Post by wildmanne39 on 2012-11-15
Hi, to attach the file click on the paperclip.
Thanks

---

### Post by BramWillemsen on 2012-11-16
I attached it yesterday :)

---

### Post by wildmanne39 on 2012-11-16
Hi, we are limited in what we can try because of the driver that you have to use with this card.

Please try:
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
```
Reboot

I believe the issue is because of the encryption being used and because there are so many networks in your area that network manager keeps trying to get to each one every few seconds.

Also the signal strength and quality  of link is not very good.
Thanks

---

### Post by BramWillemsen on 2012-11-16
Hi Wild Man,

I tried that before, but unfortunately those commands did not help. In windows my wireless network seems to be very fast. I can download with speeds between 1-10 Megabytes (not bits) per seconds in general and I have no connectivity problems at all. You say that it could be caused by there being too many networks. I don't think there are that many networks available actually, but there are many wireless routers for the university network placed everywhere. Could that cause the problem in Linux?

Since the drivers are proprietary I guess there is not much that can be done except hope that broadcom gives new drivers ? (I have not seen any open source alternatives). The wireless card works great in windows so the hardware is not faulty.

Thanks for your help so far btw :)

---

### Post by wildmanne39 on 2012-11-16
Hi, please see if this helps:

```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig eth1 power off
``` 
above exit0, then save gedit, close and reboot.
Thanks

---

