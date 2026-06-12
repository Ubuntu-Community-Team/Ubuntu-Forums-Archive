---
title: "HP dv6000 usb port issue"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by jgriffinpark on 2008-03-02
Hello, I have the 64-bit version of Ubuntu 7.10 running on my dv6405us laptop. I finally got the wireless card working, and now I'm only worried about the usb port problem, which is:

If the usb device (mouse, printer) is plugged in while the system boots, it will work, but once the system is loaded, the usb ports won't respond. If I unplug any of the working usb cables and try to reinsert them, they won't respond. I couldn't find any answers to this...does anyone know what to do? Sorry, I'm very new to this stuff.

---

### Post by Ayuthia on 2008-03-03
By any chance are you using noapic or noapic nolapic as your boot parameters?  If so, in dmesg there is most likely a message that nobody cared about one of your IRQ.  That should be the message that disabled your USB ports.

If that is the case, you might try noapic noirqdebug and see if that solves your problem.  There is a dv9000 series thread somewhere that lists other options that you could try if this does not work.  Unfortunately, I do not have a link to it right now because it used to be a sticky in the Hardware & Laptops section, but they removed the stickies.

---

### Post by jgriffinpark on 2008-03-03
THANK YOU!!!! I edited the grub menu file to include noirqdebug, and now I have a fully operational system! Thanks again!

---

