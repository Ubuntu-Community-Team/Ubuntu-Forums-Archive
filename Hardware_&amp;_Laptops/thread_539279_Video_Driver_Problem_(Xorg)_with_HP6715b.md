---
title: "Video Driver Problem (Xorg) with HP6715b"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by woody22075 on 2007-08-31
I am experiencing some issues getting Ubuntu 7.04 installed on my hp 6715b.  I searched around and used the following to get gdm to run during the installer:

sudo -s
killall gdm
apt-get install xorg-driver-fglrx
depmod -a
aticonfig --initial
gdm start

it worked for the installer.  When Ubuntu boots up, I try the same procedure.  However, when i try the "apt-get" line, I get the response, "E: Couldn't find package xorg-driver-fglrx".  Additionally, there is a repeating error "bcm43xx:Error:Microcode "bcm43xx_microcode5.fw""

I'm new to linux, so there is probably a rather simple step I am missing.  How should I proceed?

---

### Post by antm88 on 2007-08-31
I've just bought that exact laptop (setting it up yesterday) and had the same problem as you. Basically you need to be connected to the internet so that ubuntu can download the graphics driver. So if you have an ethernet cable then plug it into the laptop (the wireless doesn't work - that's what the other 43xx message is telling you) and retry those steps.
If you want more info then ask.
Setting up the wireless card in ubuntu is the next step and I'm having no luck with that :(
Ant

---

### Post by woody22075 on 2007-08-31
antm88,

Thanks for the response.  I was able to download the driver during the installation, but afterwards when I try to boot Ubuntu, it gives me the "couldnt find package xorg-driver-fglrx" and does not attempt to contact the online repository.

Did you successfully contact the online repository twice?  

woody

---

### Post by antm88 on 2007-09-06
yeah you do the exact same thing when you're loading up ubuntu for the first time. after you've done that it is set up and it works normally.
check that it is able to connect to the internet at all. have you set up dhcp properly?
ant

---

### Post by woody22075 on 2007-09-06
I thought the dhcp would be autoconfigured.  Am I missing something?

---

### Post by antm88 on 2007-09-06
Did you change any internet settings whatsoever while it was installing?
Did you change anything about the hardware setup after it was installed?
Are you able to log in as root with the 'sudo -s' command?
I just followed the steps twice and it worked.
Try pinging your router's IP by typing 'ping 10.0.0.52' (where you put your router's IP in instead of 10.0.0.52)

If all else fails I can try and help you do it manually but I'm a bit of a noob

---

### Post by antm88 on 2007-09-06
I've just reinstalled ubuntu on the laptop so I was faced with all those problems again. The problem seems to be that it can't gain internet access. The way I solved it was by setting up a DHCP server on my router. That way the laptop could connect without having to set any config up (that would be hard to do in rescue mode). Once the DHCP server was working, I booted the laptop up in rescue mode, followed the instructions you posted and it was able to connect to the internet and it worked.
Incidentally I have spent ages trying to get the wireless networking set up, followed all kinds of different guides etc. with no luck, but I have just found one guide that is very easy to follow and works flawlessly. So to save you a lot of time: [link]("http://ubuntuforums.org/showthread.php?t=405990")

---

