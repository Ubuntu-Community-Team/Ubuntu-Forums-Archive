---
title: "Hotkeys on toshiba laptop FNFX &amp; toshiba_acpi"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by Verplrke on 2007-04-07
Specs:
[LIST]
[*]Kubuntu 6.10 on a Toshiba Satellite A60
    [*]Pentium 4, 3Ghz
    [*]512 MB Ram
    [*]Ati radeon Mobility 7000 IGP
[*]Logitech MediaPlay Cordless Mouse
[/LIST]

After browsing the forum I found alot of information regarding how to setup my hotkeys but couldn't find a solution for the problems encountered:

Already installed FNFX, Toshset and Toshutils

Followed this [How-To](http://ubuntuforums.org/showthread.php?t=9962)
```

maarten@Maarten-SatA60:~$ sudo fnfxd
Password:
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or http://fnfx.sf.net/index.php?section=doc#kernel.

maarten@Maarten-SatA60:~$ 
```

Found somewhere that I needed to test this:
```
maarten@Maarten-SatA60:~$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.17-11-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device

```
And added "CONFIG_ACPI_TOSHIBA=y" in .config in /usr/src/linux-headers-2.6.17-11/  but still giving the same problems ...

---

### Post by Verplrke on 2007-04-09
I should check the ACPI-section of my kernel or recompile it with the support included, but don't know how to do that ...

---

### Post by dmizer on 2007-04-10
yeah ... toshset and toshutils are for much older machines than you have.  that's why the module won't load.  these tools were developed for a specific release of the toshiba bios from back in the 700mhz pIII days.

i don't know where to point you because i don't have a toshiba with the newer bios, but i can definitely say that this is not your answer.

---

### Post by pingpongboss on 2007-04-11
I also have a problem with the hotkeys on my toshiba laptop. Using key-testing programs, I found out that the "media keys" and the "Fn" key wasnt being detected at all. I've also tried a bunch of hotkey configurating programs specifically for toshiba laptops and have run into problems with everything. Has anyone gotten the Fn + Fx keys to work on a toshiba?

---

### Post by dmizer on 2007-04-11
last i checked, toshiba was still using a proprietary bios.  this makes it next to impossible to get all the fn and fx buttons working.  if you have any working at all, you're a good deal ahead of most people.

keep at it, and document your findings well, there's no doubt that a guide is needed.

---

### Post by pingpongboss on 2007-04-11
> **dmizer said:**
> last i checked, toshiba was still using a proprietary bios.  this makes it next to impossible to get all the fn and fx buttons working.  if you have any working at all, you're a good deal ahead of most people.

keep at it, and document your findings well, there's no doubt that a guide is needed.

ahh i see what's going on there. I guess no amount of software could fix that.

---

