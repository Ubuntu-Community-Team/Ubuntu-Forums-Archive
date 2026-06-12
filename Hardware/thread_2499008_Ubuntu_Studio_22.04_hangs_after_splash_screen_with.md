---
title: "Ubuntu Studio 22.04 hangs after splash screen with AMD RX 7600 XT at blinking cursor"
date: 2024-07-07
forum: Hardware
---

### Post by robertwk on 2024-07-07
I changed the video card in my system from an Nvidia card to this AMD GPU, and at first I just tried swapping the card in, which produced the same result.

I've tried installing the official AMDGPU drivers from AMD, and that hasn't resulted in any success.

I can hit alt-F2 and get into terminal mode no problem, but otherwise it just hangs and won't enter the windowing system.

I did an inxi -G and saw that it loads: ati, fbdev, modesetting,radeon,vesa but unloaded:amdgpu, but also gpu:amdgpu.

I have no idea how to fix this and I've tried everything to the extent of my knowledge.

If anyone has any ideas, I'd appreciate it.

---

### Post by QIII on 2024-07-07
Have you uninstalled the NVIDIA driver?

---

### Post by robertwk on 2024-07-08
Yes, did that. It still hangs, sometimes with [FONT=courier new][OK] Finished terminate Plymouth boot screen[COLOR=#0C0D0E].[/COLOR][/FONT]

---

### Post by robertwk on 2024-07-08
I was still having problems so I did an uninstall of the amdgpu driver, and also added "nomodeset" to the grub boot script, and it brought me into x11 fine, but as of now there is no driver loaded. What would be the best way to move forward? I can't keep adding 'nomodeset' manually to the boot script every time and also having a 1024x768 stretched out display.

How can I get the correct driver installed?

I am on Ubuntu 22.04.4 LTS with 6.2.0-1018-Lowlatency

---

### Post by robertwk on 2024-07-09
The solution was to install mesa drivers and kill the old x.conf file, because x was still trying to load in nvidia drivers. Problem solved.

---

