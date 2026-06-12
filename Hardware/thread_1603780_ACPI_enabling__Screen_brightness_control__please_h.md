---
title: "ACPI enabling ? Screen brightness control ? please help"
date: 2010-10-23
forum: Hardware
---

### Post by AlexZaim on 2010-10-23
Hello, i have a toshiba T135 laptop. 
The problem is that the brightness keys don't work anymore in 10.10. They worked fine in 10.04 with "nomodeset acpi_backlight=vendor" but now this line only makes my computer to boot in a terminal.

In my packages i have one called **toshset**, which is from toshiba and this is the description: "Toshset is a command-line tool to allow access to much of the Toshiba laptop hardware interface developed by Jonathan Buzzard". And when i start it from a command line it outputs:
"*required kernel toshiba support not enabled.*"

Other notes:
there is another package in the repo that is called **fnfxd** and this is the describtion:
"[I]fnfx enables owners of Toshiba laptops to change the LCD brightness,
control, the internal fan and use the special keys on their keyboard
(Fn-x combinations, hot-keys). The internal functions will give the
possibility to map the Fn-Keys to functions like volume up/down, mute,
suspend to disk, suspend to ram and switch LCD/CRT/TV-out. These
functions heavily depend on the system and/or kernel configuration.
You will need at least a kernel (v2.4.x, v2.5.x, v2.6.x) with ACPI and
Toshiba support (CONFIG_ACPI and CONFIG_ACPI_TOSHIBA).[/I]"

But it doesn't change anything after i install it (and reboot). 

I think the problem lies in acpi kernel enabling. Does anyone know how can i do it?

PS: adding "acpi=on" in /etc/default/grub doesn't help. It may work on fedora and other related distribution but for some strange reason it didn't worked for me on ubuntu.

---

### Post by AlexZaim on 2010-10-23
bump

---

### Post by AlexZaim on 2010-10-25
bump

---

