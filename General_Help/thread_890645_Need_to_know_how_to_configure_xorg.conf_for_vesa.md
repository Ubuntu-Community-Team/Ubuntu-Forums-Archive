---
title: "Need to know how to configure xorg.conf for vesa"
date: 2008-08-15
forum: General Help
---

### Post by wandalalakers on 2008-08-15
I have a very old AMD K62/300 pc with 262mb and a Cirrus Logic XXXX video card.  I'm at another location so I can tell what the exact model of the video card.  When this pc boots up, the screen is echoed or everything is seeing double.  When selecting 8 bit in the xorg.conf file it looks fine but the colors are blah.  I've installed damn small and puppy on this same exact pc so I know it supports 800x600 16 bit.  I'll provide more info when I can get to the pc.  In the meantime, is there anyway to tell xorg.conf to use Xvesa 800x600 at 16 bit?  I'm using a verrrrry old version of ubuntu.  I install 5.04 on this pc for a 10 year old.

---

### Post by kerry_s on 2008-08-15
```
Section "Device"
	Identifier	"?"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection
```

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"?"
	Monitor		"?"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"800x600"
	EndSubSection
EndSection
```


also i think it's better if you go with debian etch instead:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso)

use> install vga=788 <to install debian. it should run fine with xfce4, but you can always go lighter if you want to.

---

### Post by wandalalakers on 2008-08-15
Doh!
I meant to tell you that I tried the "vesa" option this morning and put Identifier "Generic Video Card" and I forgot what happened.  I'll install Debian this afternoon.  Thx for responding!  I've been playing around with puppy and damn small on this same pc but nothing beats ubuntu.  I'm sure I can get debian going.  Thx again!

---

