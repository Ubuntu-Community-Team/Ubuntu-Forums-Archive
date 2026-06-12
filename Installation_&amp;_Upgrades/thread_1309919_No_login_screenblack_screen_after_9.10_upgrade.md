---
title: "No login screen/black screen after 9.10 upgrade"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Nordavind on 2009-11-01
After the (new) loading screen, when I expect to see the login screen, the screen just goes black with a "working" (round circle) mouse pointer that I can move. It stays like this forever.

The same result appears when loading older version of the kernel from GRUB.

When logged into tty1 I can change to tty2-6, but not to any of the graphical ones.

Laptop: HP Pavilion ze5500
Processor: Genuine Intel(R) CPU 2.66GHz
RAM: 512MB
Graphics: RADEON IGP 345M
Max screen resolution: 1024x768
Soundcard 1: WDM-driver for ALi-sound accelerator (AC97 driver)
Soundcard 2: Unimodem half duplex sound unit

Any suggestions?

---

### Post by jwang on 2009-11-01
it seems to be X(gdm?) problem. Can you check /var/log/Xorg.0.log to see any errors?

---

### Post by Nordavind on 2009-11-02
I've checked the log now, and as far as I saw there were no errors there. I assume they'd start with (EE) as described in the beginning of the log.

---

### Post by Nordavind on 2009-11-02
Additional info.

When the screen is going black, I went to tty8, and there it hung right after checking the battery.

On the same screen, there is a warning about NAME="%k" is breaking some logic in kernel name, and that I should remove it from /etc/udev/rules.d/51-hso-udev.rules:124

Also, when loading an earlier kernel, the machine reports of an error with the soundcard, and that it is removing it. 


Don't know if any of this is related to the black screen, but I hope it can help getting me a solution.

---

### Post by Blenster on 2009-11-03
I have the same issue.  I'm relatively new to Ubuntu/linux so I will need a little help figuring out the debug process.  I appreciate the help and ideas!

---

### Post by Nordavind on 2009-11-09
Still don't get the login screen. With my limited knowledge of linux, I really need help with this. Is it X that's the problem, or is it maybe some check that needs to be done (but fails) before the login screen shows? A process that hangs?

While I don't expect anyone to have the solution based on this descriptions, I'm sure there are some suggestions to errorlogs or system settings I could check that possibly would help.

Thanks in advance :)

---

### Post by JCakeC on 2009-11-10
Nordavind,

happened exactly the same, but try booting with the newer kernel instead of the older. In my upgrade, GRUB wanted to load kernel 14, and the new Ubuntu installed the 16.
When loading, after BIOS screen press escape, select the newest kernel (there will be always one working, and most of th time it's the third option- I don't know why) once you boot, fix GRUB so it'll load the correct kernel by default.

---

### Post by Nordavind on 2009-11-19
I run a dual-boot system, so I always get the GRUB before loading the OS I want. I think it was that you meant by pressing Escape, right? Getting to the GRUB menu?

Anyhow, from there I can boot the following kernels:
2.6.31-14
2.6.28-16
2.6.27-14

The two newest give the same result, the last some other error before it halts.

---

### Post by Skinnybill on 2010-01-02
i have the same problem and would be interested in an answer :D

---

### Post by drpjkurian on 2010-01-02
Hi
Please check for broken packages by using broken filter in synaptic package manager.
You can enter into the OS through older kernel versions or recovery module

Dr Kurian

---

### Post by Nordavind on 2010-02-09
> **drpjkurian said:**
> Hi
Please check for broken packages by using broken filter in synaptic package manager.
You can enter into the OS through older kernel versions or recovery module

Dr Kurian

Not quite sure how to do that, so I just went intorecovery mode (stil can't get a GUI from that either) but I used the dpkg option to remove broken packages. It removed two things, one of the being the 2.6.28-16 kernel proprietary driver (or something). That kernel is no longer in the GRUB menu. Still no luck.

As I've mentioned before,I have an error about NAME="%k" is breaking some logic in kernel name, and that I should remove it from /etc/udev/rules.d/51-hso-udev.rules:124, so I commented out that line (Line reads KERNEL=="ttyHS[0-9]*", NAME="%k", GROUP="dialout", MODE="0660"). No change in the 2.6.31-14 kernel boot, but in the 2.6.27-14 one the load graphics is broken and in stead of halting with the thinking mouse pointer, it just ends on a black screen with a blinking marker.

Stll wondering if the soud could be the problem. The error is:
AC'97 access in not valid (0xfffffff) removing mixer.
ali mixer is creating 1 error.

Any thoughts? No net on the machine (won't connect the wireless).

---

### Post by johnrline on 2010-08-06
I had the same problem after upgrading. PulseAudio was failing to start during the boot-up sequence. I removed PulseAudio and now everything works for me. I doubt you have the exact same problem, but this might point you in the right direction.

---

