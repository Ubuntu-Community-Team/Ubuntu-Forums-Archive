---
title: "Problems Installing on Thinkpad T20"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by Topflite on 2006-07-19
I'm trying to install Ubuntu on an IBM Thinkpad T20 laptop.  I recently bought the laptop used, and the owner reported having problems getting several versions of Windows to work on it.  I'm trying to boot Ubuntu with the arguments:

boot=casper acpi=off noapic nolapic initrd=/casper/initrd.gz ram_size=262144 root=/dev/ram rw debug 

but the kernel always stops loading at the same point.  These are the last few startup messages I see:
[  118.658311] pnp: Device 00:0e acrivated.
[  118.658703] 00:0e: ttyS0 at I/O 0x3f8 (irq=4) is a 16550A
[  118.659226] PCI: Found IRQ 11 for device 0000:00:03.1
[  118.659289] PCI: Sharing IRQ 11 with 0000:00:03.0

If I try to boot with the additional boot parameter pci=off, it boots, but I obviously can't use any devices, which isn't very desirable.  

I speculate it's possibly a problem with PCI devices, since it boots when I use pci=off.  

Any suggestions for a fix?  Thanks!

---

### Post by Topflite on 2006-07-19
Also, Knoppix LiveCD starts with the default parameters and works on the system.  Several devices work in Knoppix, including USB and ethernet.  So it seems to me there should be some way to get Ubuntu to work, too.

---

### Post by Jaxilian on 2006-07-21
I run Ubuntu 6.06 on my T20 and I never had any problems with it. Check bios settings and turn off Power saving stuff. That might do it for ya.

- flodis

---

### Post by susa on 2006-07-21
install the latest IBM bios for the T20 and replace the memory sticks with new ram

---

### Post by aut2no on 2008-07-04
i know its been 2 yearssince this thread started, but im having the same problem and cant find the answer.  with an irqpoll it looks like it wants floppy fd0 that doesnt exist.  
i did get 'kernel panic' wich i thought was funny.  that was 'acpi=force irqpoll pci=off nofd0' ... all i could think of
i should add xubuntu 8 hardy heron

---

