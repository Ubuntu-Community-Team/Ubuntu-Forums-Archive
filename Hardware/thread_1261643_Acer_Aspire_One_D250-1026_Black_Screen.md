---
title: "Acer Aspire One D250-1026 Black Screen"
date: 2009-09-09
forum: Hardware
---

### Post by Dipper on 2009-09-09
I'm running the following:

Kubuntu 8.10
Kernel 2.6.27-generic
BIOS version 1.03

The screen flickers intermittently and at some point goes black (as if going into sleep mode), requiring reboot.  The backlight is on, so this is not a hardware issue.  The laptop is brand new, purchased at Wal-Mart.

Here is my xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
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

There is little information about this type of problem when I try google.  With other models, upgrading the bios is recommended.  However, in my case, I believe 1.03 is the latest bios.

This is driving me crazy.  I can't return the unit because I deleted the 6 GB recovery partition when I installed Ubuntu.  So I really need to try to fix this.  Any help would be appreciated.

---

### Post by Dipper on 2009-09-09
bump

---

### Post by Dipper on 2009-09-09
bump

---

### Post by Antonio Tavares on 2009-10-28
Hello.
I regret to say that this as started to happen exactly as Dipper told on my ACER ASPIRE ONE AOA 110-Aw.
My xorg.conf is similar, but it has a subsection "Display" on section "Secreen" so I can connect my Aspire to several external screens and to force it to use native resolution of 1024x600 (instead of 800x600 as it sudenly was using).
The problem is that after a normal boot, I may be working for a while and then the screen starts to flicker randomly. Then it crashes black (with light on). Sometimes I can get a text terminal, by pressing CTRL-ALT-F4 for example. Other times that does not work. Right now I tryed another thing. I closed the computer (to make it go to sleep) and when I turned it on, it was working again.
I suggest you try that for now.
I'm going to wait 1 day more for Ubuntu 9.10 and do a distro update. Maybe it solves this bug.

---

