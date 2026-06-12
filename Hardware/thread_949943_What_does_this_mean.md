---
title: "What does this mean?"
date: 2008-10-16
forum: Hardware
---

### Post by Ralex1098 on 2008-10-16
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

```

Why doesn't it say that I have 2 nVidia 7800GT cards? I noticed that other for other peoples' xorg files, Ubuntu tells them.

Just curious.

---

### Post by ajgreeny on 2008-10-16
I think it depends on the version of ubuntu you are running and which xorg it has, and also whether or not you have installed proprietary drivers for your graphics card.  The new xorg in hardy shows similar on mine, though it doesn't even say what card I have simply

Section "Device"
    Identifier    "Configured Video Device"
EndSection

in my xorg.conf, with an ati card running with the open source driver.

If everything works, don't worry about it.

---

### Post by Ralex1098 on 2008-10-16
Hey thanks. I'm just anxious to learn everything there is to know about the Linux/Ubuntu environment

---

