---
title: "System sometimes locks up when connecting to WLAN"
date: 2008-05-20
forum: Hardware
---

### Post by DaVince21 on 2008-05-20
Hello,

For some reason, my entire system likes to lock up in about a chance of 1 on 10 when I try to connect to a wireless network.

Basically, what happens is this:
- The system boots normally.
- NetworkManager is started and I'm asked to enter my keyring password.
- Either I'm connected to the network, or the system locks up as soon as it's *almost* connected.

This lockup is absolute when it happens. I can't do a thing with my laptop anymore, not even switch to the console, and I'll have to restart my PC.

I have an Atheros card and two proprietary drivers in my restricted drivers manager. I can't remember what card exactly it was because XUbuntu doesn't come with the useful hardware device information utility...:confused:

---

### Post by DaVince21 on 2008-05-21
Finally got a good hardware checker, seems I got a AR2413 802.11bg NIC.

---

### Post by quanumphaze on 2008-05-24
I have a similar problem with my Atheros 5005G chipset.

Background
This one works excelently well at home with standard WPA with pre-shared key. But when I take it to university, which uses EAP stuff, I have to kill Network Manager and use wpa_suplicant from the console to get any success in connecting.

The instant I press enter to start wpa_suplicant the system locks up in about 1/10 times and usually worse when I am getting less than optimal reception. I have been searching quite a bit and can't find an easy solution that doesn't involve compiling madwifi SVN (not any good guides anyway) or using ndiswrapper. All of which risk making things worse.

I just found this halfway through typing: [Easy MadWifi (Atheros WLAN) installation script]("http://ubuntuforums.org/showthread.php?t=798485")
______________________________________

PS: You could use 
```
sudo lshw -C network
and
lspci -v   #no sudo needed
```
to get the detailed information that can be easily posted for others to help with

---

