---
title: "Vgaswitchero choosing ATI before loading x, is it possible?"
date: 2011-02-17
forum: Hardware
---

### Post by cacaloco on 2011-02-17
Well, i'm one of those unfortunate people with a HP-dvX-XXXX with the infamous switching graphics capability.

I know that i can change the current graphics adapter without rebooting (even though it needs an xsession restart), using the vga_switcheroo module, and i usually do so from a nice piece of software called Ubuntu Control Center (ucc)

My system, in a more particular case, is one bundled with an Intel Graphics Adapter (from the Core i5) and an ATI Radeon 4550. HP only provides an extremely crippled BIOS, actually worth for nothing (they should REALLY remove the press F2 stuff because you can't really change anything inside the BIOS).


My current problem is:

The system always boots with the Intel Adapter, and i can't install ATI proprietary drivers (X won't start if i do so).

When i use vga_switchero i have to use it the ATI adapter with the nice, but much less competent than the Catalyst, fglxr driver.

What i want to know is: **Is there a way to change my current VGA with vga_Switchero before x starts for the first time?**

And if there is, **could i possibly have the up-to-date Catalyst driver installed and taking control over X?**

That would be awesome.:p

---

### Post by cacaloco on 2011-02-18
No one?

I will ready my installation disc to recover from x-failure and will try to test some of this myself.

---

### Post by cacaloco on 2011-02-22
Well, even tough noone replied it, i've made quite some progress.

Created a shell script calling vga_switcheroo before loading X-common in rcS (/etc/init.d/vga-boot-switch.sh being linked by S69vga-boot-switch)

The contents of the shell script are nothing special

```
#! /bin/sh

echo ON > /sys/kernel/debug/vgaswitcheroo/switch 
#turns on "the other" board, the one not currently in use.

echo DIS > /sys/kernel/debug/vgaswitcheroo/switch  
#asks to switch to the dedicated board immediately

echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
#turns off the other board

```

This does not work 100% of the times, sometimes it will still start x with the intel driver. This seems to be related to wich graphics are on, off and currently running when i shutdown the computer. Don't know if Vga_switcheroo cannot define wich is the Discrete Graphics (it seems it can define it looking at dmesg) but sometimes the script won't run (don't know why).

No work has been done about the catalyst driver yet. I want to be 100% sure of how to always start with the radeon before diving into that.

---

