---
title: "Video problems with Intel 830m on Acer Travelmate 620"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by hankwang on 2008-04-06
Hi, 

I installed Ubuntu Gutsy on an old Acer Travelmate 620 (Intel Pentium Mobile 1 GHz, 512 MB, intel i830m video) and almost everything runs fine, except suspend/resume. Suspending the laptop is fine, but after resume, often the screen is messed up, only displaying a couple of 1x1 cm blocks of pixels with colors vaguely resembling what was originally on the desktop.

Switching to a text-mode virtual console also produces junk (it switches to 40x20 character mode). Control-alt-Backspace restarts the X server with a login screen, but after login the desktop does not appear (the task bar is drawed, but the login prompt does not disappear and we can't do anything meaningful). The only way out of it seems to be rebooting.

By the way, during reboot, the screen stays black rather than showing the ubuntu logo with a progress bar. This did not happen with the installation dvd.

Apparently, something is wrong with the video driver. Does anybody know the magic setting to fix this? I did not find anything useful in 'man intel', and it would be a pity if my girlfriend switches back to Windows (it's her laptop) ;-). Here is some background data:

From xorg.conf:
```
Section "Device"
	Identifier	"Intel Corporation 82830 CGC [Chipset Graphics Controller]"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection
```

And  some snippets from Xorg.0.log:

```
X Window System Version 1.3.0
Release Date: 19 April 2007 
Build Date: 18 January 2008
(II) intel(0): Integrated Graphics Chipset: Intel(R) 830M
(--) intel(0): Chipset: "i830"
(--) intel(0): Linear framebuffer at 0x98000000
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output LVDS using initial mode 1024x768
(II) intel(0): Monitoring connected displays enabled
```

---

