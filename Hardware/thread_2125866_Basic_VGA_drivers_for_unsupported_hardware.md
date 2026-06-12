---
title: "Basic VGA drivers for unsupported hardware"
date: 2013-03-15
forum: Hardware
---

### Post by cbillson on 2013-03-15
I have a requirement to run ubuntu on the Acer Revo L80, this uses an onboard VGA chipset (Intel HD) which i believe is currently unsupported.

I only need CLI access so dont need anything advanced at all for graphics, however currently on a basic install it is not possible to get any output other than flashing screen (box functions via SSH however!)

is there any way i can tweak / fudge the install to use anything to give me the most basic of text output?

Cheers
Chris

---

### Post by albandy on 2013-03-15
Try creating this xorg.conf file:
```

Section "Device"
	Identifier	"Generic device"
	Driver "vesa"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Generic device"
	DefaultDepth    24
    	SubSection     "Display"
        	Depth       24
        	Modes      "1024x768" "800x600"
    	EndSubSection
EndSection

```

---

### Post by schragge on 2013-03-15
Try booting into text console
```
echo manual | sudo tee /etc/init/lightdm.override
```

---

