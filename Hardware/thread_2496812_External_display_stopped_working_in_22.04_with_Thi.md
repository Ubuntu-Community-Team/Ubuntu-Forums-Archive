---
title: "External display stopped working in 22.04 with ThinkPad Carbon X1 gen 11 usb-"
date: 2024-04-13
forum: Hardware
---

### Post by thayer-t on 2024-04-13
[COLOR=#0C0D0E][FONT=-apple-system]My thinkpad carbon x1 gen 11 had been working for about 3 weeks without problems connecting to my Philips 27" 4K external monitor over usb-c / thunderbolt cable (or an older Samsung 4K). It's running ubuntu 22.04 jammy with X11 from x.org (not wayland, but I've tried both)[/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system]Now the kernel doesn't see the external display, although it can get power through it and see the display's usb hub and attached devices (according to dmesg).[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]It's fairly new and I've been updating the system software, so I suspect a firmware or software update has broken this.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Notes:[/FONT][/COLOR]

[LIST]
[*]I hear a sound when plugging in then an immediately "disconnect" sound. In syslog I see usb hub being detected but nothing explicitly about "display" or "graphics" or "video"
[*]the cable and display work well with a macbook, and had been working with my laptop previously.
[*]I've tested with both the laptops usb-c ports
[*]xrandr doesn't see the external display either
[*]About graphics: Mesa Intel® Graphics (RPL-U)
[*]About hardware: Lenovo ThinkPad X1 Carbon Gen 11
[*]OS: Ubuntu 22.04.4 LTS
[*]Kernel: 6.5.0-1019-oem
[*]Kernel details: #20-Ubuntu SMP PREEMPT_DYNAMIC Mon Mar 18 17:38:55 UTC 2024
[*]plugging in a native hdmi to hdmi cable works on my Philips but not my Samsung 27" where it's flakey and pops in and out.
[*]current firmware is UEFI BIOS 2024-01-25 N3XET50W (1.25), and the software updater reports I'm up-to-date
[*]Tested with X11org and Wayland X11
[/LIST]
[COLOR=#0C0D0E][FONT=-apple-system]What's the right way to debug this? Best next step? Should I compile my own kernel?
Should I try to reach Canonical (ubuntu), Lenovo (kernel is oem), or someone else?[/FONT][/COLOR]

---

### Post by thayer-t on 2024-10-12
Was working for 6 months after updating OS and switching to Wayland. But a recent update and reboot caused it to fail again. So disappointing...

---

