---
title: "IBM thinkpad T30 suspend to RAM wireless reset"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by hil on 2005-11-24
My wireless is reset everytime I suspend to RAM. I had to re-configure my wireless by doing
```
ifconfig eth0 192.168.1.130
route add default gw 192.168.1.1
```
Suspending to RAM does not reset my ethernet on eth1. I wonder if that is the way it should be. Does anyone have the wireless settings unchanged after resuming from a suspend?

---

### Post by spiderbatdad on 2005-11-27
Hi. I've been playing with Ubuntu 5.10 on my T-30 for several days nows. I know nothing about programming or configuring applications...or anything else for that matter. However, my wireless connection has not been reset by the os. I'm not sure what you mean when you say suspend to RAM. I'm having an issue at boot-up where Ubuntu hangs during boot at "configuring system networks," or something like that. If I wait about 30 sec. and hit enter, it indicates "ok" then moves along and loads. I'm loving this OS and learning a lot as a result of it's open sourse nature. Did you install Ubuntu by letting it partition your disk along side an existing version of windows xp?
Maybe xp had a registry problem you weren't aware of around you wireless card.:confused:

---

### Post by hil on 2005-12-02
The "configuring system networks" hangs because it is running dhclient to determine the IP of the laptop. You can set it to a fix IP address it avoid running dhclient. You probably did not have ethernet cable connected or a router which listened to DHCP requests to cause the 30 seconds hang there.
I am returning my Windows Xp professional to the place of purchase but I did install another Windows XP (academic version) before I install Ubuntu. GRUB can do dual boot but you have to install GRUB on the MBR (Master Boot Record) which is the default in ubuntu installation.
I meant suspend to RAM in terms of Fn key+F4. It works for me after I did everything in [http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html]("http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html")
I'm not sure if it can work without installing necessary packages mention in the link.

---

### Post by hil on 2006-08-04
This issue is solved on ubuntu 6.06. I did not have to install any special packages to use the sleep function. Simply enable the suspend function in power management in gnome is enough. After the system wakes up, it restores the wireless settings and reconnects to the access point.

---

