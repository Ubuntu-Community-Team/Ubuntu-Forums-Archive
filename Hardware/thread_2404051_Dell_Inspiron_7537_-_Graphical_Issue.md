---
title: "Dell Inspiron 7537 - Graphical Issue"
date: 2018-10-19
forum: Hardware
---

### Post by apatran on 2018-10-19
Hello Everyone,

I'll start with the problem: 

My laptop seems to have the same graphical issue with nearly every distro of linux i've tried. Periodically along the very bottom edge of the screen I get some sort of white artifacting. It's not a solid line of artifacts, more like a broken up line of several artifacts. It is not constant, it appears and disappears. Along with this issue, when the screen is left idle, the brightness will *almost* imperceptibly oscillate between increasing and decreasing by a very small value, maybe like 2-3% every second. It's just enough to drive me insane. These brightness  changes though are not registered by the system, as far as the OS is concerned, the brightness has always been at max.


The frequency of these issues:


white artifacts: can happen randomly regardless of input, but seems to happen with 100% consistency when moving the mouse from an idle state. Tends to happen much less if the mouse is actively moving around the screen.

Brightness oscillation: Only occurs when the screen is idle. After no longer touching the mouse, takes maybe 3-4 seconds for the oscillation to begin.


None of these issues occur in Windows, the BIOS, grub or tty. They only begin after loading into the OS


Hardware specs:

- Dell Inspiron 7537 Laptop
- 16GB RAM
- Core i7 4510u - Intel® HD Graphics 4400
- G-Force GT 750m


I've tried several distro's thinking it might be distro specific, here's the list:

- Ubuntu 16, 18
- Debian stable
- OpenSUSE
- Manjaro
- Arch Linux


Interestingly enough, Linux Mint actually works. It's the only distro I've found that actually does not have any issues and I've been desperately trying to figure out why.


I'm currently operating in Ubuntu 18.04 to try and see if I can find a fix for the issue for atleast the Debian family of distro's

Things I've tried: 

- Nvidia 390 drivers
- Performance only mode (Prefer nvidia card over Intel)
- Power saving mode (Prefer Intel over nvidia)
- Disable any sort of automatic brightness adjustments in Ubuntu power settings (BIOS unfortunately does not give me the ability to disable adaptive brightness)
- Kernel parameters: acpi_backlight=video || acpi_backlight=vendor || acpi_backlight=native
- Different display managers: SDDM, LightDM, GDM
- Sacrificing a goat to the dark lord
- Different kernel versions 4.13, 4.15, 4.16, 4.17 in Ubuntu
- Flashed laptop with latest BIOS

Nothing has yielded any results. I haven't been able to find any solutions online. This is either not a common problem or a laptop people don't commonly try to use with linux. I managed to find this ONE post: [https://forum.antergos.com/topic/5294/screen-brightness-flicker-when-moving-the-mouse](https://forum.antergos.com/topic/5294/screen-brightness-flicker-when-moving-the-mouse), from someone who seems to have had the same issue as me, but it's two years old and unsolved. 

If anyone needs more hardware details, or general details please let me know. If anyone has any ideas it would be greatly appreciated

---

### Post by apatran on 2018-10-21
If anyone's interested I managed to fix it! Using the nomodeset kernal parameter seems to solve the issue. I didn't think it would based on the description on what nomodeset does, but it works!

---

### Post by hrsetrdr on 2018-10-22
Glad you solved it, I was going to suggest using an earlier driver, but good to know "nomodeset" fixed it.

---

### Post by apatran on 2018-10-22
I didn't like the idea of using nomodeset for the rest of my Linux days because as I understand it that would mean I would be using basic Linux drivers for my video instead of Intel and Nvidia, which is non optimal.

I did some further debugging and the row of flickering pixels is actually being caused by the Intel i915 driver somehow. I found a string of i915 parameters that actually fixes the issue. I'll do some further investigation and figure out exactly which of those parameters is the linchpin that's fixing the flicker. I'll post it here for archival purposes, in case any other poor soul wastes months on such a silly problem.

---

### Post by apatran on 2018-10-23
In case anyone ever comes searching. I solved this i915 flicker issue by the following:

1. Create a file in /etc/modprobe.d/ called i9815.conf
2. paste this line into it "options i915 enable_psr=1"
3. in console update-initramfs -u
4. reboot. 

The Arch Linux wiki actually suggests disabling psr and that did nothing for me. I never thought enabling it would be the solution. I hope someone else with an older intel chip finds this useful.

---

