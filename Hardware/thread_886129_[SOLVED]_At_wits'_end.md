---
title: "[SOLVED] At wits' end :|"
date: 2008-08-10
forum: Hardware
---

### Post by windoze87 on 2008-08-10
ok, so i've tried just about everything i know to get my nvidia driver to work. Here's the lowdown- about a month ago i got a new hard drive and i decided to reinstall Ubuntu to the new one. Well, i did...and ever since, i have no hardware acceleration with my nvidia card. the restricted drivers module tells me that my nvidia card is indeed enabled, and "lspci | grep -i nvidia" in terminal gives me this output```
00:06.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

``` so im pretty sure the damn card still works. if i go into terminal and run "sudo nvidia-xconfig" it rewrites my entire xorg.conf file and i have to spend an average of 45 minutes writing my old xorg.conf file back to get a halfway decent resolution. speaking of xorg.conf, under "Section 'device'" i have this--```
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:0:6:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
``` which doesnt strike me as being right, seeing as i have a geforce fx card and not a geforce 4. even /var/log/Xorg.0.log tells me that it's finding the card...but...no hardware acceleration. What exactly am i doing wrong? I'll post whatever i need to so i can get an answer...please help :|

---

### Post by windoze87 on 2008-08-10
update-- well, nvidia-settings doesnt tell me to run nvidia-xconfig anymore. it displays all the correct info about my card, and -amazingly- ubuntu FINALLY detects my monitor for the first time, and sets the correct resolution. All i did was open a terminal and type ```
sudo apt-get remove nvidia-glx-new --purge
```, then i did autoclean, autoremove, and then installed EnvyNG and used the driver it supplies...and bam, it now appears my graphics card is displayed correctly. However, i don't know if i have hardware acceleration or not still since i don't get any Compiz effects, which was my main problem... any ideas?

---

### Post by windoze87 on 2008-08-10
nevermind....everything works now :| amazing how things in ubuntu just...start working lol

---

