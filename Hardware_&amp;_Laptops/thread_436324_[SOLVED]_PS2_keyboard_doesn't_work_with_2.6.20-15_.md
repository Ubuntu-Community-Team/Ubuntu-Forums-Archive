---
title: "[SOLVED] PS/2 keyboard doesn't work with 2.6.20-15 kernel"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by Bukran on 2007-05-07
Hello everybody.

I did upgrade recently from Ubuntu 6.10 (Edgy) to Ubuntu 7.04 (Feisty) with the Update Manager. First I installed every update of Edgy, as it's recommended on [www.ubuntu.com](www.ubuntu.com). With the upgrade came a new version of the kernel: 2.6.20-15-generic and I'm afraid we've lost backwards compatibility when trying to fix things for USB keyboards.

I have an old PS/2 keyboard and a wireless USB mouse. The keyboard works perfectly in GRUB but I lose it in the splash logon screen, there's no response at all. I've tried a couple of the possible solutions found on the Internet...

Adding 'acpi=off nolapic' to the GRUB boot line apparently solved the problem, as I could type, but after that the computer didn't power off after shutdown (I had to turn it off manually). Something to do with ACPI, I'm afraid ;)

Disabling USB support on the BIOS setup just made me lose the mouse too (my also old motherboard doesn't distinguish between keyboard USB support and mouse USB support).

There's no problem when I boot with previous kernel 2.6.17-11-generic so I assume it's a bug/missconfiguration in the new one. I have a K7 motherboard, AMD Duron 700 MHz, 384 MB RAM.

Thanks beforehand.

---

### Post by kushko on 2007-05-08
I think I have the same problem.

I just installed 7.04 for the first time and only my keypad and caps lock keys work with my PS2 (Dell) keyboard at the splash screen. I also tried a PS2 Compaq keyboard I have and it didn't work either. It works fine if I go into the recovery mode on bootup though.

The funny thing about my problem was that anytime I hit a key the screen resolution would change (any key).

Kevin
P4 1.6GHz
ABit BL7 MB
Radeon 7000
768MB RAM

---

### Post by no_martini_no on 2007-07-01
Hi.
I have a motherboard VIA VT8371 x86 family...
I'm sure there is a problem with ACPI support. My keyboard is also disabled when loading ubuntu feisty.
 Here I have some lines from the kernel loader immediately after it loaded the kernel modules etc.:

```

 *loading kernel modules...
 *loading manual drivers...                    // my keyboard is now disabled
 [28.912000] ACPI:PCI Interrupt 0000:00:07.5[C] -> link [LNKC] -> GSI 10 (level, low) -> IRQ10
 [29.460000] ACPI:PCI Interrupt 0000:00:09.0[A] -> link [LNKB] -> GSI 12 (level, low) -> IRQ12

```

I'm asking myself why the new 2.6.20-15 kernel has no ACPI  support for older motherboards, because in dapper I didn't notice any of these problems with ACPI...
I also noticed that two adapters are sharing the same IRQ (in this case the 10th and 12th), but I think it doesn't matter.

any help?

---

### Post by harr986 on 2007-07-01
I upgraded to ubuntu 7.04 about two weeks ago. Having the same problem. PS/2 keyboard with Logitech MX700 usb wireless mouse. When booting 2.6.20.15 (even recovery mode) from Grub I can not type anything on the logon screen. I can still boot 2.6.17.11, thank goodness.
    My system is a Iwill K7R266-plus motherboard, a 1.4gh AMD cpu, and 768mb 133 sdram. I haven't seen anything yet that looks like a solution.

---

### Post by IntuitiveNipple on 2007-07-02
Have you checked the boot log in the sessions where the keyboard has failed?

Once you've restarted in a good kernel check the log of the previous boot (/var/log/dmesg.0), you should see something like this:
```
$ grep -E 'i8042|serio:|input:|PS/2' /var/log/dmesg.0
[    1.180432] mice: PS/2 mouse device common for all mice
[    1.181029] input: Macintosh mouse button emulation as /class/input/input0
[    1.181291] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.186444] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.190700] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.190702] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.190704] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.190706] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.190708] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.394069] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.088000] input: PS/2 Mouse as /class/input/input2
[   16.112000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3

```

---

### Post by Bukran on 2007-07-25
I've finally managed to get the keyboard working. I haven't spent much time trying to figure out what do the following options exactly mean but one can imagine out of their name:

```
acpi=force irqpoll
```

By adding these two options to the boot line in /boot/grub/menu.lst my old PS/2 keyboard works and switching and power off are also ok. I must say as well that by this time I'm now running 2.6.20-16-generic kernel version but I don't think that matters at all, as the first time I booted the new version there was the same problem. ;)

---

