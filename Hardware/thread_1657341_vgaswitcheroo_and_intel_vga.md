---
title: "vgaswitcheroo and intel vga"
date: 2011-01-01
forum: Hardware
---

### Post by vivivi on 2011-01-01
Hello.

i have Ubuntu 10.10, Intel Core i3 with video GeForce 310M and i want switch to Intel integrated card.

uname -a 2.6.35-24-generic #43~ppa1~loms~maverick-Ubuntu SMP Fri Dec 24 18:14:36 UTC 2010 x86_64 GNU/Linux

cat /proc/cpuinfo 
model name : Intel(R) Core(TM) i3 CPU M 350 @ 2.27GHz

lspci |grep VGA
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

Why i see only one VGA card?

And vga_switcheroo not works.

echo ON > /sys/kernel/debug/vgaswitcheroo/switch
bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory

I need some help. ):P

---

### Post by realzippy on 2011-01-01
Maybe you have a switch in your BIOS?

Can you install the nvidia driver without troubles?

---

### Post by vivivi on 2011-01-01
No i can't find this option in my Bios. Yes i can install nvidia drivers. My laptop is samsung r528. I checked dmesg | grep VGA 

2.671481] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    2.713787] [drm] Initialized drm 1.1.0 20060810
[    2.779360] nouveau 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.779375] nouveau 0000:02:00.0: setting latency timer to 64
[    2.785521] [drm] nouveau 0000:02:00.0: Detected an NV50 generation card (0x0a8a80a2)
[    2.803037] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PRAMIN
[    2.925351] [drm] nouveau 0000:02:00.0: ... appears to be valid
[    2.925358] [drm] nouveau 0000:02:00.0: BIT BIOS found
[    2.925364] [drm] nouveau 0000:02:00.0: Bios version 70.18.39.00
[    2.925368] [drm] nouveau 0000:02:00.0: Pointer to BIT loadval table invalid
[    2.925794] [drm] nouveau 0000:02:00.0: TMDS table version 2.0

Maybe you have idea?

I boot Fedora 14 from usb, it's same - i can't see intel VGA.

---

