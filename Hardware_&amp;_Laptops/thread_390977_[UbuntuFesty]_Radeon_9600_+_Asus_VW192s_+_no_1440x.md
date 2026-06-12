---
title: "[Ubuntu:Festy] Radeon 9600 + Asus VW192s + no 1440x900"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by derbouka on 2007-03-22
Hi!

I bought an Asus VW192s, but I can't put to work the 1440x900 resolution :(

I've followed the "[X11 Configuration- 5.4.3.2 Adding a Widescreen Flatpanel to the Mix]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html")" and now I've the "1280x960", but I can't put to work the 1440x900..

So, my "/var/log/Xorg.0.log" has this info:
```
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 106.0 MHz   Image Size:  410 x 256 mm
(II) RADEON(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) RADEON(0): Serial No: 71LV002700
(II) RADEON(0): Ranges: V min: 50  V max: 75 Hz, H min: 30  H max: 82 kHz, PixClock max 210 MHz
(II) RADEON(0): Monitor name: ASUS VW192Sÿÿ
```
and so, I've put the Monitor section on "/etc/X11/xorg.conf" like this:
```
Section "Monitor"
	Identifier	"ASUS VW192Sÿ"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-75
	Modeline	"1440x900"  106.0  1440 1520 1672 1094  900 903 909 934
EndSection
```
and my screen section like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"ASUS VW192Sÿ"
	DefaultDepth	24

	...

	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

But when I got to "System>Preferences>Screen Resolution" It doesn't apear the "1440x900" :\

Can anyone help me?
PS: Ive already used the command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by vespo on 2007-03-23
Hi

Make a backup copy of your xorg.conf. Then, in the Display section, try removing all modes except "1440x900". This will force X to start with the right resolution. After editing xorg.conf don't run dpkg-reconfigure because it could revert to a wrong xorg.conf.
To restart X, just hit Ctrl+Alt+Del. If you're stuck in console mode, type "startx". If it fails, revert to the previous backed-up xorg.conf

---

### Post by derbouka on 2007-03-23
Hello!

Yes, it's working.. :)

Basically, I've only removed the modeline from the monitor section and put the "1965x1027" and now it's working.. 
Well it's strange but it's working lol :)

Thanks!

---

### Post by Sir_Yaro on 2007-08-10
thank u for config

---

