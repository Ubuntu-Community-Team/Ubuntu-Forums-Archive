---
title: "ATi Radeon Mobility 9100 Help with Compiz"
date: 2008-09-23
forum: General Help
---

### Post by SKooT1027 on 2008-09-23
I just switched over to ubuntu yesterday.  I have been running Windows for years, but tried to recover a partition with linux.  Long story short, I was unable to, and decided to stick with linux.

I'm having lots of trouble with my video card, and this seems to be a common problem.  I have a Toshiba Satellite A75 (S1253) Laptop which I installed Ubuntu Heron onto.

I followed all kinds of how to's for installing the video drivers, and have not had much luck.  I was finally last night able to change the Compiz settings from None to the other two options, but my computer lagged down heavily.  Also, I don't think the video drivers are properly installed, but rather part way there (enough to enable Compiz).

Has anyone figured out the easiest way to get the Mobility 9100 (or 9000) to function and install properly?

---

### Post by Kevbert on 2008-09-23
I'm using compiz on my laptop with an ATI Mobility Radeon 9000.  Compiz does use a lot of resources.  Here's the settings from my /etc/X11/xorg.conf file:
```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection
```

---

### Post by northern lights on 2008-09-23
Can you please post the output of```
sudo lshw -C display
```Thank you.

---

### Post by SKooT1027 on 2008-09-23
> **Kevbert said:**
> I'm using compiz on my laptop with an ATI Mobility Radeon 9000.  Compiz does use a lot of resources.  Here's the settings from my /etc/X11/xorg.conf file:
```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection
```

What drivers did you actually download, or did you only change the xorg file?

> **northern lights said:**
> Can you please post the output of```
sudo lshw -C display
```Thank you.

I'm at work right now, and didn't bring my laptop with me because I can't access internet through it while at work.  I'll have to run it when I get home tonight.

I do know off hand that when i ran fglrxinfo (right?) I often got some "Mesa" drivers and it didn't properly recognize my card, but at other times it would see it's a radeon 9000/9100

---

### Post by SKooT1027 on 2008-09-23
Also, is this just a problem with Ubuntu 8?  Like did the drivers work correctly on 7?  I haven't used linux in over 6 years, so I'm not familiar with the changes and compatibility.

---

### Post by northern lights on 2008-09-23
> **SKooT1027 said:**
> Also, is this just a problem with Ubuntu 8?  Like did the drivers work correctly on 7?  I haven't used linux in over 6 years, so I'm not familiar with the changes and compatibility.

This should not be an issue.

---

### Post by Kevbert on 2008-09-23
> **SKooT1027 said:**
> What drivers did you actually download, or did you only change the xorg file?


All I did was change the xorg.conf file as the driver came with the operating system.

---

