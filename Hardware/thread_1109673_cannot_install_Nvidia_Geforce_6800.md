---
title: "cannot install Nvidia Geforce 6800"
date: 2009-03-29
forum: Hardware
---

### Post by zolek78 on 2009-03-29
i'm using Kubuntu 8.10 at the moment. I've got my laptop (Vaio SZ) installed with Kubuntu for 2 months now. I installed Nvidia driver once before and it went smoothly. Last week, I've got a graphic problem so I have to reinstall the driver. However, I keep receiving Low Resolution problem message instead of log-in screen and I have to reconfigure the driver...

This is my xorg.conf file

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I tried to install nvidia driver manually, using envy or hardware manager...but nothing seems to work

---

### Post by |{urse on 2009-03-29
have you ran 

nvidia-xconfig

?

---

### Post by zolek78 on 2009-03-29
matter of fact. I think i did

this is the output

```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver line.


ERROR: Unable to write to directory '/etc/X11'.

```

---

### Post by zolek78 on 2009-03-29
nevermind, I upgraded gcc 4.3 and everything went smoothly again...thanks for your help!

---

