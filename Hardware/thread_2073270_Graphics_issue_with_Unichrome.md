---
title: "Graphics issue with Unichrome"
date: 2012-10-19
forum: Hardware
---

### Post by Maximumbob_uk on 2012-10-19
Hi,

I have been trying to refurb an old netbook for my son.  I have wiped it clean and installed ubuntu 11.10 32 bit onto it.

It has:
Via C7-M 1600MHz CPU
Via Tech. CX700/VX700 [S3 Unichrome Pro] (rev 03)

It was VERY difficult to get it up and running as often the graphics were completely bugged.

I have updated it and managed to get it running by putting in an xorg.conf

```
Section "Monitor"
	Identifier	"Configured Monitor"
        Driver          "vesa"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Whilst the graphics issue is resolved (as in visible and not a garbled screen) there remain some massive bugs.  

1) The size of the desktop exceeds the size of the screen.  I can see the envelope in the top right, but not the date etc.

2) I am unable to change the resolution of the desktop.

I downloaded xresprobe and used the command ddcprobe.

This told me:
```
vbe: VESA 3.0 detected.
oem: VIA CX700
vendor: ?
product:
memory: 65536kb
mode: 640x480x256
mode: 640x480x64k
mode: 800x600x256
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1600x1200x256
mode: 1600x1200x64k
edid:
edidfail
```

SO, is there some kind soul who can help put me on the right path as regards some way to make the desktop fit the screen?

I assume it may require some specific settings within the xorg.conf, but I have hit my skill ceiling!!!

I would really like this fixed... otherwise I may have to give him his raspberry pi birthday pressie early!!!!

---

### Post by 2F4U on 2012-10-19
Any special reason for using 11.10? Its support will end in April 2013:

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

If you can, I would rather suggest to try 12.04. Considering the hardware, Xubuntu 12.04 may be more appropriate than Ubuntu 12.04.

---

### Post by Maximumbob_uk on 2012-10-19
ok... i'll give it a whirl and let you know how i get on

---

### Post by Maximumbob_uk on 2012-10-19
i just found this blog about installing linux on a machine identical to mine!!!

in one specific part he talks about frambuffer exceeding screen size.  Can anyone translate this for me???

[http://archwebbook.blogspot.co.uk/2008/09/gnome-progress.html](http://archwebbook.blogspot.co.uk/2008/09/gnome-progress.html)

i think that may solve my problem

edit:  i tried xubuntu and it didnt get past the loading screen :-/

---

