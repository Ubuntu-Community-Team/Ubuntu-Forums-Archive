---
title: "Touchpad, headphone jack and suspend/resume problems with MSI A6400"
date: 2011-07-20
forum: Hardware
---

### Post by smay on 2011-07-20
Hi everyone,

I've done my first Ubuntu install dual-booting with Win7. 11.04 looks great but I've been working through some problems and trying to fix them.

Problem 1: no scrolling, gestures, or configuration for Sentelic touchpad. This appears to be a known issue with a bug report, and I can live without. However I swear the first couple of times I booted, the top left & right zone scrolling was working, and it's since disappeared! Maybe I'm imagining things. 

Problem 2: Headphone jack didn't work. This surprised me as I always thought this was a hardware switch. This was **solved** by following the [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") help article along with [this thread]("https://bbs.archlinux.org/viewtopic.php?id=103470") on the Arch Linux forums. I discovered the ALSA HDA codec was Conexant CX20585 and that changing the model in /etc/modprobe.d/alsa-base.conf with

```
options snd-hda-intel model=asus
```Problem 3: Suspend and resume don't work. Appears to [be a known issue with 11.04/2.6.38]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/748994").The hard drive is written to, screen goes blank (but backlight is still on) lights remain on, fan remains on, laptop goes unresponsive. Keyboard, mouse, power button, and Magic SyRq shortcuts do nothing.

Everything in /var/log/pm-suspend.log seems to be logged as a success.

I thought it might be that swap was smaller than physical memory. After repartitioning to increase swap size (and forgetting to update grub and much messing around with the bootloader) this is not the issue.

I will try upgrading the kernel to 2.6.39 and see if that does anything.

(Should I put this in the laptop compatibility/incompatibility thread? I had a look at those but it's really awkward to search. Is there a hardware wiki page somewhere?)

---

