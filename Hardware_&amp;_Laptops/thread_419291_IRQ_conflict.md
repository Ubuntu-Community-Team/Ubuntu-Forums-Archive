---
title: "IRQ conflict"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by M@her on 2007-04-22
HI everybody, I'm using Kubuntu 6.06 LTS kernel 2.6.15-28-686, and I've got a strange problem, every dozen of hours (sometimes less, somteimes a lot more), my usb ports disappear...I had the same problem with Mandriva 2007 and it's optimized kernel...:confused: 

I noticed that this problem disappear when I use the default i386 kernel.

I checked out my messages and found that :

**[17179579.312000] uhci_hcd 0000:00:1d.2: irq 169, io base 0x0000d400**

and 

[B][17179619.512000] serial8250: too much work for irq169
[17179619.524000] serial8250: too much work for irq169
[17179619.528000] serial8250: too much work for irq169
[17179619.536000] serial8250: too much work for irq169
[17179619.540000] serial8250: too much work for irq169
[17179619.544000] serial8250: too much work for irq169
[17179619.548000] serial8250: too much work for irq169
[17179619.552000] serial8250: too much work for irq169
[17179619.560000] serial8250: too much work for irq169[/B]

So I guess it's an IRQ conflict, and this is the source of the conflict :

**IO-APIC-level  libata, uhci_hcd:usb3**

Libata !

Notice that my motherboard possesses a RAID controller (I'm not using it anyway) and is configured in Legacy Mode so hard drives uses the traditional 15 IRQs.

I've got 4 native USB ports on the MB, 2 in the front of the CU, and 2 others in the bottom (plugged in the MB); everytime the mysterious bug occured, only 4 ports are shown by **lsusb** command, the native ones when there's nothing plugged in the other ones (but always 4), they are of course unusable...

The only solution is to reebot the machine, which is something that shouldn't happen with Linux...

I would be very grateful if you help me to solve that.

Thank you.

---

### Post by M@her on 2007-09-17
Problem solved.

It was due to a disposition that I choosed on my motherboard to manage Pata + Sata (I have 3 CD/DVD devices). It causes a problem of virtual IRQ conflict.

To solve that I found a strange solution. I pass the irqpoll parameter to the kernel while booting (I get the same error anyway), and just after the boot finish, I reboot again without that option...and it works...for the session...

---

