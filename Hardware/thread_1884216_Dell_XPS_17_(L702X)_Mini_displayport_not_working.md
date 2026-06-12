---
title: "Dell XPS 17 (L702X) Mini displayport not working"
date: 2011-11-20
forum: Hardware
---

### Post by dtbaker on 2011-11-20
Hello,

I have a mini displayport on this dell laptop, connected to a DVI adapter ( [http://ritmotech.com.au/satotech/images/IMG_0028.JPG](http://ritmotech.com.au/satotech/images/IMG_0028.JPG) ) connected to an external monitor. 

DVI works on this monitor when plugged into another computer, but I cannot get the mini displayport to work.

I've searched high and low and everybody says "It just works when using the mini displayport". The ubuntu "displays" setting area doesn't find a second screen, neither does the laptop keyboard shortcut.

Is there anything I can do to find out if my ubuntu install knows about the mini displayport?


```
$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF108 [GeForce GT 555M] (rev a1)
```

```
$ cat /etc/X11/xorg.conf

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection
```

Ironhide is installed to get some nvidia gizmos working, however this mini displayport is apparently not related to the nvidia card, only the intel one.

Any ideas? Should something appear in dmesg when plugging into a mini displayport?

Cheers,
Dave

---

