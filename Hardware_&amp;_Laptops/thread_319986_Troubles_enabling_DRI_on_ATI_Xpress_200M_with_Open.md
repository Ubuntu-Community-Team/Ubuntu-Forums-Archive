---
title: "Troubles enabling DRI on ATI Xpress 200M with Open source radeon driver"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by ralf57 on 2006-12-16
Hi all,
i'm trying to enable direct rendering on my HP DV5135EU laptop equipped with a ATI Xpress 200M PCI card and Ubuntu Edgy

the "lspci" command outputs this
```

01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

```

I've followed the guide on the wiki
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

and my current xorg.conf (only relevant sections) file contains this

```

.....
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
........
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"XAANoOffscreenPixmaps"	"1"
EndSection
............
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option          "AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection


``` 

It seems correctly configured but

```
glxinfo | grep "direct rendering"
```
returns
```
direct rendering: No
```:( 

either with only Sideport or Sideport+UMA memory enabled

I'm afraid that my card is not supported by the open source driver,
but before giving up i have to be 100% assured of it.
Any ideas?
Is there any detailed and updated list of ati cards currently supported by the open driver?
Thanks in advance.

---

### Post by tjohn on 2006-12-16
> **ralf57 said:**
> 
I've followed the guide on the wiki
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


I found that note in the wiki 

_2D acceleration only_
Xpress 200M Northbridge integrated gpus


Greez Tobias

---

### Post by ralf57 on 2006-12-16
> **tjohn said:**
> I found that note in the wiki 
_2D acceleration only_
Xpress 200M Northbridge integrated gpus


I had already noted that.
Btw, my card is not an integrated gpu but a dedicated card (128MB+128MB)
on PCI bus, instead.
I still haven't found a comprensive list of supported chipsets/cards....:???:

Updated: i've just found two lines in Xorg.0.log file stating that:

```

(II) RADEON(0): Direct rendering broken on XPRESS 200 and 200M

```
and 
```

(WW) RADEON(0): Direct rendering disabled

```

so it seems that nothing's left to be done but praying for this chipset to be supported in the next versions of the driver.
I hope this will save some headaches to other users

---

### Post by tjohn on 2006-12-18
I have got the same problem with my Radeon Xpress 200 M...
I have tried many ways to install the driver. At the end I left it at all.
I hope the next kernel will support by Card.

---

### Post by d-E-a-D on 2006-12-19
People, good news, just follow this link: [http://ubuntuforums.org/showthread.php?t=321766&highlight=200m](http://ubuntuforums.org/showthread.php?t=321766&highlight=200m)

And you will get your 200M full working!

Cumps

---

### Post by ralf57 on 2006-12-20
> **d-E-a-D said:**
> People, good news, just follow this link: [http://ubuntuforums.org/showthread.php?t=321766&highlight=200m](http://ubuntuforums.org/showthread.php?t=321766&highlight=200m)

And you will get your 200M full working!

Cumps

Thank you d-E-a-D for your instructions,
but my complains were referred to the open source driver not ATI's one.
The problem with Xpress 200M card is currently that:
1) with open source (radeon) driver  (which supports AIGLX) you won't have 3D at all
2) with ATI's proprietary driver (fglrx) you can have full 3D performances but no support for AIGLX

The only way to set-up a 3D-Desktop (Compiz or Beryl) is to go with fglrx/XGL.
The worst option, imho, since XGL is not integrated into X and fgrlx driver is proprietary software.

---

### Post by d-E-a-D on 2006-12-21
I know ralf57, but you can't use open source drivers, at least for now, with 200M because it reports a problem when using it's memory. (sideport or uma or anything else)

So, all we have to do is wait until amd/ati get AIGLX working with proprietary drivers.

Cumps

---

