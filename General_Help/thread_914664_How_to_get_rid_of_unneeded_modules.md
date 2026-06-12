---
title: "How to get rid of unneeded modules?"
date: 2008-09-09
forum: General Help
---

### Post by TPJ on 2008-09-09
Hello.

I'm trying to prevent my system from loading some kernel modules (at the boot time) I don't need. I have already blacklisted many modules (like irda, gameport, floppy etc.) in my /etc/modprobe.d/blacklist file, I have commented out many rules in my udev configuration, I have turned off the hal daemon, and some modules are no longer loaded, but the rest still is. Here are some lines from my dmesg:

(...)
[   41.279382] Yenta: CardBus bridge found at 0000:00:0a.0 [1043:1504]
[   41.408546] Yenta: ISA IRQ mask 0x0498, PCI irq 11
[   41.408616] Socket status: 30000006
[   41.504484] Yenta: CardBus bridge found at 0000:00:0a.1 [1043:1504]
[   41.572314] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   41.632476] Yenta: ISA IRQ mask 0x0498, PCI irq 5
[   41.632550] Socket status: 30000006
(...)
[   43.288649] input: Power Button (FF) as /devices/virtual/input/input4
[   43.299683] ACPI: Power Button (FF) [PWRF]
[   43.300353] input: Sleep Button (CM) as /devices/virtual/input/input5
[   43.311624] ACPI: Sleep Button (CM) [SLPB]
[   43.312277] input: Power Button (CM) as /devices/virtual/input/input6
[   43.327608] ACPI: Power Button (CM) [PWRB]
(...)
[   50.497754] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2294kHz
[   50.665394] irda_init()

The problem is I don't need support for Power/Sleep buttons, gameport and irda. I also think I don't need this Yenta stuff. How can I prevent my Ubuntu from loading all of these unneeded modules?

---

### Post by cariboo on 2008-09-09
Why do you need to disable those modules, remember linux is not windows. Unloading the modules, just because you don't need them will not enhance the performance of your computer.

Jim

---

### Post by TPJ on 2008-09-10
**cariboo907**, believe me, I do realize that Linux is not Windows. If Linux was the same as Windows, I would have never used it, since I don't like the way Windows works. I haven't worked on Windows for years.

I don't like the idea of loading unneeded kernel modules, so I simply want to get rid of them. The question is how can I achieve this goal, if blacklisting them doesn't help?

And one more thing: I don't want to *unload* them, I want to *prevent* them from being loaded during the boot process.

Edit: fixed a typo.

---

### Post by lavinog on 2008-10-08
I think some items maybe compiled into the kernel.
You would need to recompile the kernel if blacklisting them doesn't work.
[http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

---

