---
title: "Keyboard suddenly not working in Hardy Intrepid"
date: 2008-11-13
forum: Hardware
---

### Post by craftomaniac on 2008-11-13
Hello everyone. I have been using Ubuntu since the release of Hardy and it has been superb and great so far. I recently upgraded to Intrepid which was better but with another quite serious but bearable problem.

Now, suddenly, the support for external keyboards and mice has broken.

It was working the last time I booted up Ubuntu. While I was in that boot, Ubuntu installed a kernel update to 2.6.27-8 and I installed blender as well.

Now, all I have to type and navigate with is my touchpad and my laptop keyboard. My external Apple Aluminium Keyboard, Logitech V550 mouse, and my older (took it out just to try) Logitech V500 mouse all don't work anymore.

Curiously, lsusb shows that Linux is still detecting these input devices, just not using them.

Bus 007 Device 004: ID 05ac:0220 Apple, Inc. Aluminum Keyboard
Bus 007 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 064e:a101 Suyin Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 147e:2016  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 004 Device 002: ID 046d:c526 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I am running Ubuntu 8.10 Intrepid with 2.6.27-8 kernel

I don't think the problem is with my USB ports as they have been working fine, and still work fine in Windows, and any removable USB thumbdrives, hard disks, etc. I plug in still work as per normal. Just that my keyboard and my mice do not work anymore within Ubuntu (they still work at GRUB and BIOS and so on).

I have booted into the original 2.6.27-7 kernel, reconfigured xorg.conf, uninstalled blender, restarted countless times, tried multiple combinations of USB ports all to no avail.

What should I do?

---

