---
title: "Sharp Aquos LCDTV"
date: 2009-04-21
forum: Hardware
---

### Post by zefiriss01 on 2009-04-21
hi, i use Sharp Aquos LCD TV for monitor, i use ordinary vga cabel, and have like this:

- pc turn on, motherboard manufacture pic show up fine, tv said 800x600 60Hz
- entering boot loader, still ok, tv said 720x400 70Hz
- entering ubuntu progress bar, still ok, tv said 640x480 60Hz
- then suddenly blank, first tv said 720x400 70Hz, then -- (no data), then there's note at center screen said "Not compatible with this signal"

so, why not compatible?
and how to solve it?
i assume it resolution or refresh rate problem, i wonder if there's script which i can write so ubuntu will jump to spesific resolution and refresh rate at booting so it can enter the system.

---

### Post by zefiriss01 on 2009-04-21
hi again,
i try with my laptop, and it has same problem, just when it goes blank, it move to my laptop screen, i mean like transferred to my laptop screen, and ubuntu can enter smoothly.

---

### Post by zefiriss01 on 2009-04-22
!!!!!
I found the problem, it work well with openSUSE 11.1, it on monitor chose, I don't know why ubuntu can't detect, my monitor detected as VESA in openSUSE.

now, how can i enter the GUI, anyone know how to change monitor from command line (I only can enter ubuntu from recovery command line)?

---

### Post by zefiriss01 on 2009-04-27
using xubuntu 9.04 now, and needs some tricks to make graphic works.

1. installing xubuntu on safemode
2. change xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"

# 1360x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 84.72 MHz
Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"


DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1360x768_60.00" 
EndSubSection

EndSection
```

done, but it really takes whole day to configure xorg.conf

I answer my own question :cry:, well, see the good side, now i know more about xorg.conf O:)

---

