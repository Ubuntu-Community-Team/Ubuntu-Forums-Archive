---
title: "&quot;hardware drivers&quot; stops recognizing my nvidia"
date: 2009-09-16
forum: Hardware
---

### Post by ivanhelguera on 2009-09-16
Hello, 
I messed up my system badly (including attempting at some point a 'manual' install of nvidia 185 drivers by running  NVIDIA-Linux-x86-185.18.36-pkg1.run) and I have problems. Nvidia drivers do not work, and are not recognized. 
```
dpkg-reconfigure  xserver-xorg
```
gives no information whatsover abou the driver to use. My actual, sorry xorg.conf:  
```
m@ih-Phenom:~$ cat /etc/X11/xorg.conf
#commented part removed


Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
any ideas how to purge the remains of the old drivers and make the system see & use the nvidia drivers? (nothing else gives proper resolution - it's a an integrated 8300)
I'd be most grateful for any help.

---

### Post by freackout on 2009-09-16
> **ivanhelguera said:**
> Hello, 
I messed up my system badly (including attempting at some point a 'manual' install of nvidia 185 drivers by running  NVIDIA-Linux-x86-185.18.36-pkg1.run) and I have problems. Nvidia drivers do not work, and are not recognized. 
```
dpkg-reconfigure  xserver-xorg
```
gives no information whatsover abou the driver to use. My actual, sorry xorg.conf:  
```
m@ih-Phenom:~$ cat /etc/X11/xorg.conf
#commented part removed


Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
any ideas how to purge the remains of the old drivers and make the system see & use the nvidia drivers? (nothing else gives proper resolution - it's a an integrated 8300)
I'd be most grateful for any help.

have you tried envyng its rather good.

---

