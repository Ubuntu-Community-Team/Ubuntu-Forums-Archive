---
title: "Screen Resolution really lost plz help."
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by JustinJS on 2007-04-23
Ok when i go into system -> Preferances -> Screen Resolution i can pick 1024x768, 800x600, or 640x480 well i want 1440x900 on my laptop here is a print out from my /etc/X11/xorg.conf
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
```
Thank you

---

### Post by taurus on 2007-04-23
What kind of onboard graphic card do you have on that laptop?

```
lspci
```

---

### Post by garlik42 on 2007-04-23
look into 915resolution there are some howto's that should help you.

---

### Post by dannyboy79 on 2007-04-23
try to use dpkg

sudo dpkg-reconfigure xserver-xorg

(or is it .............xorg-xserver?)

---

### Post by JustinJS on 2007-04-23
tryed it no money :( and i belive it is a lspci

---

### Post by JustinJS on 2007-04-23
id what i was saying before about lspci im a lil slow today lol ahhh it is ```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by JustinJS on 2007-04-23
any other ideas would be great because i really have no idea how to fix it

---

### Post by JustinJS on 2007-04-23
ok i got it using the 915resolution i didnt get it at first but now im good thank u

---

