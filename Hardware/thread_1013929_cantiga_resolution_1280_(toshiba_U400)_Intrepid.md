---
title: "cantiga resolution 1280 (toshiba U400) Intrepid"
date: 2008-12-17
forum: Hardware
---

### Post by Cannaregio on 2008-12-17
Dunnow why is it too hard to integrate the most recent intel cards, however I got a good resolution with the vesa driver, after various finetuning attempts.

Somehow I managed to have those previously hard to obtain 1280:800 resolution on my Toshiba laptop.

I modified the xorg.conf as follows:

changed one line of the previous old snippet
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection

```
where did that [COLOR="#0000ff"]2048[/COLOR] came from, beats me.
I substituted it anyway with
```
	SubSection "Display"
		Virtual	1280 800
	EndSubSection

```

This seems to have done the trick. Previosuly I was confined to the 1024/768 settings.
Here how my Monitor section of xorg.conf was and is:

```
Section "Monitor"
	Identifier      "Configured Monitor"
	Vendorname      "Generic LCD Display"
	Modelname       "LCD Panel 1280x800"
	Horizsync       31.5-48.0
	Vertrefresh     56.0 - 65.0
	modeline  "1280x800@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma   1.0
EndSection

```

Note the "[COLOR="Blue"]modeline 1280x800@60[/COLOR]" first

For completeness I add also my Section "device" here
```
Section "Device"
	Identifier  "Card0"
	Driver      "vesa"
	VendorName  "Intel Corporation"
	BoardName   "Cantiga Integrated Graphics Controller (Q45)"
	Option      "MonitorLayout" "LVDS"
	BusID       "PCI:0:2:0"
EndSection

```

So it is now still running with the vesa driver, BUT at least and for the first time with a correct resolution.

Fact is that when I rebooted after the changes above I discovered that I finally managed to broke free from the ugly 1024x768 settings... and I am still using the kernel  2.6.27-10-generic in Intrepid.

Compiz seems to work fine.

But Glxgears gives low frames:
2537 frames in 5.0 seconds = 506.842 FPS
2460 frames in 5.0 seconds = 490.647 FPS
2520 frames in 5.0 seconds = 502.200 FPS


Good luck to those that were stuck in a lower resolution.

---

### Post by Olnex on 2008-12-29
But the problem is, if you use "vesa" instead of "intell", will some features be unusable as "vesa" is more generic than "intel"?
I have same laptop(U400/H00) and I have the same problem: sometimes screen resolution becomes 1024x768 when resumes from suspend, I tried to install Hardy instead, however, it can't even get into desktop, everything is messed up on the screen.
Finally I installed OpenSuse 11.1, only minor problems remain(multimedia key), suspend works(hibernate seems not work sometime), and the mic works too which is important to me because I have to use skype.

---

### Post by guido_damico on 2009-02-07
I was having the same issue with my new Sony Vaio FW190EDH with GMA 4700MHD and the most recent official Ubuntu drivers I am up to 1600x900.

All I needed to do was to install them when the software update signalled me they were available and then let them detect the video card.

Hope this helps.

---

