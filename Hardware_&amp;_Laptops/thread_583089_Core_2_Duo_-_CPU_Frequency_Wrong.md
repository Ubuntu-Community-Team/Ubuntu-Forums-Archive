---
title: "Core 2 Duo - CPU Frequency Wrong"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by RamonBianco on 2007-10-20
I have a Gigabyte 965P motherboard and an Intel e4300, overclocked to [COLOR="Green"]**2.7 GHz**[/COLOR] - FSB 338 and **[COLOR="Magenta"]multiplier 8[/COLOR]**.  The BIOS boot screen confirms the [COLOR="Green"]**2700 MHz**[/COLOR].

I have disabled SpeedStep to have a constant CPU frequency - I want the most BOINCage I can get.  My forum search only seems to get results related to FSB-frequency issues with SpeedStepping / frequency scaling.

In Feisty Fawn, the standard Ubuntu sources for CPU frequency on this PC all have it as [COLOR="Blue"]**3042 MHz**[/COLOR] instead of [COLOR="Green"]**2700**[/COLOR] - /proc/cpuinfo, sysinfo, etc.

If I change the [COLOR="Magenta"]**multiplier to 9**[/COLOR] and the FSB to 300, the values are reported correctly.  But I prefer the higher FSB for performance.

[SIZE="4"][COLOR="Magenta"]It appears that Ubuntu is not reading the actual multiplier from the BIOS, but the default CPU multiplier, which is 9 for an e4300[/COLOR][/SIZE] - 9*338=[COLOR="Blue"]**3042**[/COLOR].

Does anyone know if this has been fixed in Gutsy Gibbon, or if there is a work-around?

[CENTER]:?:[/CENTER]

---

### Post by RamonBianco on 2007-10-22
.

---

### Post by RamonBianco on 2007-10-25
Interestingly, lshw has it right:

> [FONT=courier][COLOR="DarkGreen"]@GBubuntu:~$ sudo lshw -class cpu
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.15.2
       serial: 0000-06F2-0000-0000-0000-0000
       slot: Socket 775
       **_size: 2704MHz_**
       capacity: 4GHz
       width: 64 bits
       _**clock: 338MHz**_[/COLOR][/FONT]

(except for calling the CPU speed "size" and the FSB "clock" [COLOR="Plum"][well, that one's not too bad][/COLOR].)
So why can't Feisty get it right in /proc/cpuinfo and sysinfo?  Can Gutzy?

---

### Post by 444 on 2007-10-25
This is a kernel issue.

It is pretty easy to install only the Gutsy kernel in Feisty, so it appears as an option in GRUB, Then you can try it and see.

If that still doesn't do it, then you'd have to modify the kernel somehow (and recompile), which can be a hassle.

---

### Post by RamonBianco on 2007-10-26
Thanks, 444.

I don't want to risk breaking anything by installing the Gusty kernel, much less doing the full "upgrade", if I can't even verify that Gutsy would fix this relatively minor issue.

I hope someone can confirm or deny whether this misbehavior has continued in Gutsy.

---

