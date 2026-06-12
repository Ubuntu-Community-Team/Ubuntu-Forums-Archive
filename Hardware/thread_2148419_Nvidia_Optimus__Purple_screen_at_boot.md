---
title: "Nvidia Optimus / Purple screen at boot"
date: 2013-05-25
forum: Hardware
---

### Post by rowan_m on 2013-05-25
I have a ThinkPad T430 with an Nvidia NVS 5400M dual booting Raring and Windows 8.

If I boot directly into Ubuntu or reboot Ubuntu then the system boots with a purple screen directly after grub. It's still responsive in the background as I can reboot using Ctrl-Alt-Delete. If boot into Windows 8 and then reboot, the system boots into Ubuntu just fine.

I've tried a number of different options in grub: nomodeset, nox2apic, etc. and these don't seem to make a difference. I've also tried different combinations in the BIOS for discrete vs. integrated graphics and Optimus detection.

I assume there's something that Windows 8 is triggering in the card that's getting it in the right state to boot. Any ideas, similar experiences... or even a solution?

---

