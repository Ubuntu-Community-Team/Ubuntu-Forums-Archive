---
title: "[SOLVED] Front usb ports on Dell Optiplex gx240"
date: 2008-12-31
forum: Hardware
---

### Post by ginlorax on 2008-12-31
My front usb ports are not working under Gutsy.  I can plug in a thumb drive, and see it via lsusb, but it does not auto-mount, nor can I seem to access it.  I found several old threads that note [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=459444"), but no solution.

I noticed that the host controller for the front panel (I think) shares the same irq as the NIC ( 18 ).  On a hunch that it might be an IRQ conflict, I added a noapic option in my grub menu.lst.  After rebooting, when I plugged in the thumb drive it recognized it immediately.  /proc/interrupts show that both host controllers are now on 9.

Any advice on how to proceed?

Thanks!

---

### Post by ginlorax on 2009-01-04
I tried turning off the onboard ethernet in BIOS and added an old pci NIC card I had lying around.  Both USB controllers now had their own IRQ, but I still had the same problem.

I upgraded to Hardy and now the front USB ports are working.  Problem solved.

---

