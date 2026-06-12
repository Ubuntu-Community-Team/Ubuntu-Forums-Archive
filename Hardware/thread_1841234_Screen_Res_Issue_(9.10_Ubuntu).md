---
title: "Screen Res Issue (9.10 Ubuntu)"
date: 2011-09-09
forum: Hardware
---

### Post by mrunowich on 2011-09-09
Friend gave me a Pavilion N5425 With Ubuntu 9.10 installed. I have two issues currently but on this thread, I am looking for some help with fixing the screen resolution Max. In terminal, typing in xrandr, the max allowed is 800x600, however the laptop's hardware allows for 1024x768. I have spent quite some time researching answers and tried several different codes in terminal to try and solve this problem with no luck.
 
If you have any info that could help- i'd really appreciate it.

---

### Post by realzippy on 2011-09-09
Isn't that a Trident CyberBlade graphics?
If so, bad luck.
Please show output from

```
lspci |grep VGA
```

Please also attach your 
/var/log/Xorg.0.log 
file...

---

### Post by mrunowich on 2011-09-10
> **realzippy said:**
> Isn't that a Trident CyberBlade graphics?
If so, bad luck.
Please show output from

```
lspci |grep VGA
```

Please also attach your 
/var/log/Xorg.0.log 
file...

10-4, it is a Trident Cyberblade-
LSPCI lgrep VGA returns with sets of different codes to enter in in order to view different sets of informations about the graphics system for Trident.

Xorg.O.log returns with returns with quite a bit of info about the Trident Cyberblade and information pertaining to screen resolution but no options to change the settings for max screen res.

---

### Post by realzippy on 2011-09-10
Can you attach the log file?

Have you ever tried to use a xorg.conf file?

Eg:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        Horizsync 30.0-60.0
        VertRefresh 50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by mörgæs on 2011-09-10
Before going further, I would test Lubuntu and Xubuntu 11.04 in a live boot and install the one that works better. 

9.10 is a dead-end: 
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by realzippy on 2011-09-10
Why not simply upgrade to 10.04 LTS ?

---

### Post by mörgæs on 2011-09-10
Because it is an old computer and it would benefit from something lighter than a regular Ubuntu.

---

