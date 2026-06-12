---
title: "Unable to verify with LUKS and consequently cannot startup Ubuntu anymore"
date: 2016-11-20
forum: Hardware
---

### Post by Josquin69 on 2016-11-20
After the last system update in which I got both a new kernel and an updated NVIDIA driver I cannot verify with LUKS anymore. I now can only boot up the system via a workaround involving the rescue option.

Previously I also got the LUKS key entry field only after a cold boot, and it would not let me type anything in it. After that I always did a warm boot with CTRL-ALT-DEL and did not get the LUKS entry field, but a blank purple screen. I was able to enter the LUKS password then by blind typing it and hitting ENTER. Then the system continued its boot. I also did not have virtual consoles using the proprietary driver.

After the last kernel update and latest NVIDIA driver update I also can not blind type the password anymore and I now can only log in by booting to the rescue mode, typing the LUKS password in text mode and choosing resume boot (twice!) after that.

Current system info: DELL Precision M4600 with Kernel 4.4.0-47 and latest NVIDIA driver for my Quadro 2000M

[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]System:    Host: josquin-Precision-M4600 Kernel: 4.4.0-47-generic x86_64 (64 bit gcc: 5.4.0)[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]Desktop: Cinnamon 3.2.1 (Gtk 3.18.9-1ubuntu3.1) dm: lightdm Distro: Ubuntu 16.04 xenial[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]Machine: System: Dell (portable) product: Precision M4600 v: 01 Chassis: type: 9[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]Mobo: Dell model: 08V9YG v: A00 Bios: Dell v: A16 date: 12/26/2013[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]CPU: Quad core Intel Core i7-2760QM (-HT-MCP-) cache: 6144 KB[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 19156[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]clock speeds: min/max: 800/3500 MHz 1: 807 MHz 2: 980 MHz 3: 801 MHz 4: 1140 MHz 5: 847 MHz[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]6: 823 MHz 7: 1378 MHz 8: 847 MHz[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]Graphics: Card: NVIDIA GF106GLM [Quadro 2000M] bus-ID: 01:00.0 chip-ID: 10de:0dda[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]Display Server: X.Org 1.18.4 drivers: nvidia (unloaded: fbdev,vesa,nouveau)[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]Resolution: 1920x1080@59.91hz[/TD]
[/TR]
[TR]
[TD="class: blob-num js-line-number, align: right"][/TD]
[TD="class: blob-code blob-code-inner js-file-line"]GLX Renderer: Quadro 2000M/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 367.57 Direct Rendering: Yes[/TD]
[/TR]
[/TABLE]
[/TD]
[TD="class: blob-code blob-code-inner js-file-line"][/TD]
[/TR]
[/TABLE]


Choosing the Nouveau open source driver did give me an unacceptable resolution of 1024x768 and redshift complained about missing Gamma or something. Option which I additionally could explore is using the NVIDIA legacy or 340.x driver.

I can by hopping via the rescue mode and resume boot option get into the system again and even got my virtual consoles back when running NVIDIA, but any help would be greatly appreciated. I understand that removing LUKS is possible, but very dangerous. I do not want to reinstall.

Kind regards,
Josquin Hoens

---

