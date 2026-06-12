---
title: "Touch pad issues / xorg.conf"
date: 2011-03-22
forum: Hardware
---

### Post by Sojurner on 2011-03-22
I have been searching for days on how to disable tap to click and enable edge scrolling on my Alps touchpad that is on my 
Acer Aspire G-7551G-5407

Everything i have found talks about finding it listed in the /etc/X11/xorg.conf, however i do not see anything in my xorg.conf file relating to a touchpad. 

I really need to get my touchpad working as it really is the only thing that is keeping me from using ubuntu full time. I would appreciate any help. If you need me to post something just give me the command i will post the results.

I am running Ubuntu 10.04LTS

I have installed gsynaptics and its runs, but none of the changes i make in gsynaptics seem to effect the touchpad at all. I tried using this because the touchpad tab in my mouse settings is there but when changing it, it does not affect the touchpad at all. 

My xorg.conf file
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

---

