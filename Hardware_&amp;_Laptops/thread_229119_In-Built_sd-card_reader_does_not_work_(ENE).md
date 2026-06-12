---
title: "In-Built sd-card reader does not work (ENE)"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by tranceash on 2006-08-04
My built-in sd card reader does not work in ubuntu 6.0.6 kernel 2.6.15-26-386 
The ouput of lspci shows the hardware

0000:02:09.2 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller

But when insert the card it does not detect i checked the logs and dmesg no new messages.

Any particular module I have to load or compile.
Anybody knows about this issue?

---

### Post by chazmo on 2006-08-11
I seem to be having the exact same problem. I recently purchased an ACER 3100 series notebook and I've got everything working except the card reader. lspci shows

*FLASH memory: ENE Technology Inc: Unknown device 0551 (rev 01)*

I'll keep searching the forums/web to see if I can find an answer, but if anybody has a solution please post.

---

### Post by newen on 2006-08-25
I have not seen anybody who has got this working yet. Lspci recognizes it but this device seems currently unsupported, as it will ever be. (I sent a mail to ENE requesting Linux support a year ago, but I didn't get any reply). lspci -v gives this:

02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d0201c00 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>
02:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff01
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at d0202000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d0202400 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

Someone must develop a driver, as this company doesn't want to support Linux. For my next laptop (this one is almost 2 years old) I will check first the graphics card (either Intel with their open source drivers or Nvidia) and secondly that i doesn't come with such a device with so poor Linux support.

EDIT: it would be nice to mail the company masively asking at least for the datasheet of the CB710. Then, a driver for linux would be ony matter of work.

---

