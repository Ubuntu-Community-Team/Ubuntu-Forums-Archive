---
title: "[SOLVED] GRUB - Incorrect screen resolution after installing a new graphics card"
date: 2020-03-27
forum: Hardware
---

### Post by lcs_europe on 2020-03-27
Good evening to everybody

I installed a new graphics card. Since then, the screen resolution at GRUB is no longer correct.

**Soft- und Hardware**
[LIST]
[*]OS: Ubuntu 19.10 (5.3.0-42-generic #32-Ubuntu SMP x86_64 x86_64 x86_64 GNU/Linux). The graphics drivers for the card installed: [FONT=courier new]sudo apt install nvidia-driver-435[/FONT]
[*]PC: Gigabyte GA-H110M-DS2 (rev. 1.0), Intel Core i7-7700 (3.6 GHz), 32 GB RAM, **Palit GeForce 1050 Ti KalmX**
[*]MONITOR: Apple StudioDisplay 27"
[/LIST]
I made the following adjustments to the GRUB configuration:
[LIST]
[*][FONT=courier new]GRUB_GFXMODE="2560x1440x24"[/FONT]
[*][FONT=courier new]GRUB_GFXPAYLOAD_LINUX="2560x1440x24"[/FONT]
[*][FONT=Courier New]sudo grub-mkconfig -o /boot/grub/grub.cfg[/FONT] and [FONT=Courier New]sudo update-grub[/FONT]
[/LIST]
I added [FONT=Courier New]FRAMEBUFFER=y[/FONT] to the [FONT=Courier New]/etc/initramfs-tools/conf.d/splash[/FONT] and did [FONT=Courier New]sudo update-initramfs -u[/FONT].

The splash screen (plymouth) is also displayed in the wrong screen resolution.

Who has a tip on how I can solve the "problems"?

Thank you in advance for your appreciated help and stay healthy, Laszlo

---

### Post by lcs_europe on 2020-03-29
Hi there. Problem solved. I have choose the wrong resolution in the [FONT=Courier New]grub.cfg[/FONT]. I replaced the font and size in the GRUB-Theme too.

---

### Post by mörgæs on 2020-03-31
Thanks for an attempt at marking the thread solved. Better though to use Thread Tools.

---

