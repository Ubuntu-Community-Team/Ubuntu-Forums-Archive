---
title: "How to go about ATI drivers with HD3650"
date: 2010-12-15
forum: Hardware
---

### Post by hinge on 2010-12-15
Hi

Just got a lenovo W500 with a radeon HD 3650 chipset. Hopefully it is a great machine....
The thing is I have never had a machine with an ATI  adaptor in it, I've always had nvidia.

What is the recommended way of installing a decent driver?
Which driver "distribution" should I use?
the fglrx form the repo or the downloadable one from ati?

I have tried both and none of the work - I end up in the console...

Is there a good howto. I have googled but came up blank...
I'm running Ubuntu 10.10

---

### Post by hinge on 2010-12-16
I tried following the manual installation on:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

I get a blank screen. Log and config below....

What to do?


```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

```
[     9.725] ukiOpenDevice: open result is 11, (OK)
[     9.725] ukiOpenByBusid: ukiOpenMinor returns 11
[     9.725] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     9.725] (==) fglrx(0): NoAccel = NO
[     9.725] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[     9.725] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 3650" (Chipset = 0x9591)
[     9.725] (--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x2126)
[     9.725] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[     9.725] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[     9.725] (--) fglrx(0): MMIO registers at 0xbfff0000
[     9.725] (--) fglrx(0): I/O port at 0x00002000
[     9.725] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     9.747] (II) fglrx(0): Battery is used
[     9.770] (II) fglrx(0): Detected: Switchable-graphics system with a non-AMD chipset
[     9.770] (EE) fglrx(0): Please disable switchable-graphics feature and configure the discrete card as the default adapter
[     9.770] (EE) fglrx(0): GetBIOSParameter failed
[     9.770] (EE) fglrx(0): PreInitAdapter failed
[     9.770] (EE) fglrx(0): PreInit failed
[     9.770] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === end
[     9.811] (II) UnloadModule: "fglrx"
[     9.811] (II) UnloadModule: "fglrxdrm"
[     9.811] (II) UnloadModule: "fglrxdrm"
[     9.811] (EE) Screen(s) found, but none have a usable configuration.
[     9.811] 
Fatal server error:
[     9.811] no screens found
[     9.811] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[     9.811] Please also check the log file at "/var/log/Xorg.5.log" for additional information.
[     9.811] 
[     9.823]  ddxSigGiveUp: Closing log

```

---

### Post by gradinaruvasile on 2010-12-16
> [     9.770][COLOR="Red"] (II) fglrx(0): Detected: Switchable-graphics system with a non-AMD chipset
[     9.770] (EE) fglrx(0): Please disable switchable-graphics feature and configure the discrete card as the default adapter[/COLOR]

Your laptop has 2 video adapters - one Intel and one Ati.
The idea supposedly is that the Intel is used until more power needed, then the Ati is powered on. Although this might sound interesting, one cant help to wonder that a single video card with good power management isnt a better option... I have read somewhere that this switcheroo stuff is only needed because Intel wants to have its adapter there no matter what (it is done with the newer nvidias too with the "Optimus" platform - and that is worse because the nvidia adapter can be used only on some models, most of them can only use the Intel under Linux).

There is an issue with this: this switcheroo works only in Windows. But this particular laptop has a Bios switch that forces the use of the desired adapter at boot.
So, go in the BIOS, find that option, switch to the Ati card then it should work (i have seen  a w500 working well with the fglrx driver).

PS. Make sure you have the right PCI ID for the card in xorg.conf.

---

### Post by hinge on 2010-12-16
Hi 

Thanks for the explanation - like you say, I don't know if it makes sense...

I fixed it!!

Funny though - the error message in xorg.conf  told me to do this:

"Please disable switchable-graphics feature and configure the discrete card as the default adapter"

---

### Post by ubuntuforums on 2011-02-22
I have the same issue, I want to do exactly as that error message says "disable switchable-graphics feature and configure the discrete card as the default adapter". Unfortunately my HP BIOS is handicaped and is lacking the setting to do so. How did you fix it? I suppose your BIOS contained that setting?

---

### Post by cyberey66 on 2011-02-23
> **ubuntuforums said:**
> I have the same issue, I want to do exactly as that error message says "disable switchable-graphics feature and configure the discrete card as the default adapter". Unfortunately my HP BIOS is handicaped and is lacking the setting to do so. How did you fix it? I suppose your BIOS contained that setting?

If you can't disable switchable graphics, as far as I know you cannot use fglrx drivers.  You should be able to use the integrated graphics, also as far as I know, the discrete graphics will still be enabled and consuming power.

With switcheroo, you may be able to dig through the code and write a script to disable the integrated video during boot.

One of the main issues is that both fglrx and xorg's intel drivers use different open GL libraries and overwrite each other.  But if you can somehow disable the intel graphics during boot, I believe it should work.  I don't know much about what the hybrid setting in the bios actually does though.

---

### Post by ubuntuforums on 2011-02-27
> **cyberey66 said:**
> If you can't disable switchable graphics, as far as I know you cannot use fglrx drivers.  You should be able to use the integrated graphics, also as far as I know, the discrete graphics will still be enabled and consuming power.

With switcheroo, you may be able to dig through the code and write a script to disable the integrated video during boot.

One of the main issues is that both fglrx and xorg's intel drivers use different open GL libraries and overwrite each other.  But if you can somehow disable the intel graphics during boot, I believe it should work.  I don't know much about what the hybrid setting in the bios actually does though.
Thanks for the info. I'm currently trying to find a way to disable the intel graphics. If I'm lucky it can be disabled or blacklisted through a bios mod.

---

