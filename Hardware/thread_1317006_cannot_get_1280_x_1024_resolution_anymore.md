---
title: "cannot get 1280 x 1024 resolution anymore"
date: 2009-11-06
forum: Hardware
---

### Post by profeta81 on 2009-11-06
hi all

I have a toshiba satellite A-100 and an external leovo f-417 17''.

After clean install ubuntu 9.10 I could plug external screen and get 1280 x 1024 resolution on external screen and 1280*800 on laptop video. After giving a presentation using a video projector, the maximum resolution for the external screen has become 1024*768.

is it possible to revert to the previous configuration somehow? I tryed sudo dpkg-reconfigure xserver-xorg but that didn work...

thanks!
Lorenzo

---

### Post by freackout on 2009-11-07
> **profeta81 said:**
> hi all

I have a toshiba satellite A-100 and an external leovo f-417 17''.

After clean install ubuntu 9.10 I could plug external screen and get 1280 x 1024 resolution on external screen and 1280*800 on laptop video. After giving a presentation using a video projector, the maximum resolution for the external screen has become 1024*768.

is it possible to revert to the previous configuration somehow? I tryed sudo dpkg-reconfigure xserver-xorg but that didn work...

thanks!
Lorenzo
sudo su gedit /etc/X11/xorg.conf
then ctrl/at/backspace to restart gdm

---

### Post by profeta81 on 2009-11-07
> **freackout said:**
> sudo su gedit /etc/X11/xorg.conf
then ctrl/at/backspace to restart gdm

hi, thanks for the reply,

if i gedit the document what should I add or remove? all the configuration is automatic, the content of /etc/X11/xorg.conf is:

> 


Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2640 800
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection



the autoconfiguration did work correctly (I could use the 1280 x 1024 resolution). Now for some reasons id doesn't work anymore and the highest resolution for the 17'' monitor is 1024*768...

---

### Post by profeta81 on 2009-11-07
Ok, I've been messing around a bit, and found in the /etc/X11 directory a previous xorg.conf.20091106143152 backup file (I guess was created when I plugged in the videoprojector maybe). I backed up the current xorg.conf (the one which was giving me the wrong resolution) file and renamed the older backup, restarted gdm and now I can get the correct resolution. The only difference between the two files is:

> 
lorenzo@lorenzo-laptop > diff /etc/X11/xorg.conf /etc/X11/xorg.conf_wrongres 
6c6
< 		Virtual	2560 1024
---
> 		Virtual	2640 800


thanks anyway for the help!

---

