---
title: "Serial8250: Too much work for IRQ11"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by Jerrac on 2005-04-18
I just reinstalled ubuntu, and as it was installing it gave me this message a lot. It would just fill up the screen.

Serial8250: Too much work for IRQ11

What does that mean?

---

### Post by Jerrac on 2005-04-18
Heh, I just ran dmesg and get this:
```

david@reia:~$ dmesg
 too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
serial8250: too much work for irq11
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
ACPI: PCI interrupt 0000:01:05.0[A] -> GSI 10 (level, low) -> IRQ 10
[drm] Initialized radeon 1.14.0 20050125 on minor 0: ATI Technologies Inc Radeon IGP 340M
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
david@reia:~$


```

---

### Post by glass-half-full on 2005-05-27
I am getting the same thing on an IBM Thinkpad R40e...... LIVE CD works fine but full 5.04 install hits this brick wall.

---

### Post by Phanatic on 2005-10-11
my workaround for this was to set different IRQs for the PCI devices in BIOS (the most suitable was setting half the devices to 10, the others to 11). now i get hardly any such errors (if i get one, the computer will continue after ca. 30 sec idle)

---

### Post by TheNewGuy on 2006-04-26
I have this same issue in dapper when I run the kernel with the irqpoll option. I'm glad there's some sort of fix for this but my laptop doesn't allow irq changes.

---

### Post by akaihola on 2006-12-13
Same problem here with a Fujitsu-Siemens Amilo A on Edgy. The BIOS doesn't offer any IRQ options. Switching on the Canon inkjet printer connected to the USB always hangs the computer immediately, and otherwise in hangs randomly.

---

### Post by MrUmunhum on 2007-09-07
On my laptop, I get the same message.
I found that by killing the ppp session on ttyS0, the problem goes away.
Now I just need the find where this ppp session is started?
Where is inittab?

---

