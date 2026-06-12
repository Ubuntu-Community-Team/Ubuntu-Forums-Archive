---
title: "Any Toshiba owners out there?"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by ThrobbingBrain66 on 2006-07-28
Is there a Toshiba owner out there that has managed to re/compile a kernel with the toshiba and toshiba_acpi modules?  I've compiled a new kernel with all the toshiba support, but then my wifi doesnt work and quite frankly, configuring ndiswrapper confuses me.

---

### Post by marios88 on 2006-07-29
I am a hapy toshiba owner with 6.06 everything worked out of the box with my tecra A2 i just had to choose the keyboard layout,

As for wifi it just works....


```
lsmod | grep toshiba_acpi
toshiba_acpi           10940  0

```

---

### Post by ThrobbingBrain66 on 2006-07-29
Mine currently works too...I just don't get the greatest battery life because toshiba_acpi support isnt included by default (on my kernel anyway).  So when I try to compile a new kernel to get the toshiba_acpi, I lose my wifi.

I don't know...maybe it is enabled in the default kernel as a module.  If that's the case, I don't know how to active modules.  Any ideas?

---

### Post by Gtaylor on 2006-07-29
See my Tecra A4 wiki page for details on restoring your wireless. Even if you're not using an A4, this should do the trick:

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA4)

Look under "Restoring USB/Network"

---

### Post by ThrobbingBrain66 on 2006-07-29
Thanks!!  I'll give that a try the next time I have a moment to compile a kernel.  Just to make sure I have those instructions clear, I am to add the pci=noacpi and irqpoll to the menu.lst, correct?

---

### Post by Gtaylor on 2006-07-29
You don't need to recompile the kernel.

You can add the flags by hilighting your kernel in the GRUB menu and editing it via the menu. I think the key to hit is 'e'.

---

### Post by MrBbDD_OK on 2006-07-29
I have a Portege PII 366 and a D-Link wireless card. Install found everything and had it working before the first reboot. I have an atheros chip so it's using ath_pci; this is the first distro that has it included with no extra work. For ndiswrapper, it's really simple. You get the WinXP drivers for your card and copy them to an appropriate folder on /home/user (wherever) cd to that directory, and run ndiswrapper. It will list all its options, one of which is install the driver (-i?), which is the .inf file. Once loaded, enter ifconfig to see what it's been named (ath0, wlan0, etc.) then iwconfig (ath0, wlan0, whichever) to set it up.

Britt Dickson

---

### Post by ThrobbingBrain66 on 2006-07-29
> **Gtaylor said:**
> You don't need to recompile the kernel.

You can add the flags by hilighting your kernel in the GRUB menu and editing it via the menu. I think the key to hit is 'e'.

I know I don't have to recompile a kernel just to add those two options to the boot menu, but I DO need to recompile a kernel to add the toshiba_acpi support.

---

### Post by shooterae5 on 2006-07-30
[FONT="Comic Sans MS"][SIZE="2"]I have 6.06 running on a [COLOR="DarkRed"]Satellite M35X-S149[/COLOR]. 

I had problems with power management when I first installed. 
It was a BIOS update from Toshiba that fixed it. 

The only issue that is remaining is WEP keys will not work. 

I'm a big advocate of Ubuntu Linux and try to get everyone to try it.[/SIZE][/FONT]

---

