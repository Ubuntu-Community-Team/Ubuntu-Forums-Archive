---
title: "Left ctrl button not working!"
date: 2010-05-12
forum: Hardware
---

### Post by Drycola on 2010-05-12
Hi,

On my HP TX2500 I've got a weird keyboard problem: my left control button doesn't work! It is not a hardware problem since I've checked it on windows where it works properly!
I'm using **Ubuntu 10.04** and my laptop model is exactly **HP Pavilion tx2510us**

---

### Post by Drycola on 2010-05-12
Bump!

---

### Post by anglican on 2010-05-12
> **Drycola said:**
> Hi,

On my HP TX2500 I've got a weird keyboard problem: my left control button doesn't work! It is not a hardware problem since I've checked it on windows where it works properly!
I'm using **Ubuntu 10.04** and my laptop model is exactly **HP Pavilion tx2510us**
Is there something in your /etc/X11/xorg.conf file that uses that kry for some special purpose e.g. I have:

```
        Option          "XkbOptions"    "lv3:ralt_switch,compose:rctrl"
```to assign my right ctrl key as the "compose" key to access certain special characters.

H

---

### Post by Drycola on 2010-05-13
I've opened System->Preferences->Keyboard shortcut and tried to assign the left ctrl button to a function just to see if it works, I've found that it gives the signal "XF86MyComputer" !!!
So, what should I do to fix this??

---

### Post by Drycola on 2010-05-16
<bump>

---

### Post by anglican on 2010-05-17
> **Drycola said:**
> <bump>
Well what was in your /etc/X11/xorg.conf file?

H

---

### Post by chrishaum on 2010-06-01
I'm having a similar problem (none of the Ctrl keys works, nor does Caps Lock).  Here is my xorg.conf file:


Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2720 900
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Thanks!

---

