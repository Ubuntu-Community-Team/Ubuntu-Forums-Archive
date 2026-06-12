---
title: "Possibility of hardware hack on Ubuntu machines?"
date: 2013-10-27
forum: Hardware
---

### Post by NoBugs! on 2013-10-27
Possibility of hardware hack on Ubuntu machines?

According to this article, some British researchers found remote backdoor functionality on some computers:
[http://m.afr.com/p/technology/spy_agencies_ban_lenovo_pcs_on_security_HVgcKTHp4bIA4ulCPqC7SL](http://m.afr.com/p/technology/spy_agencies_ban_lenovo_pcs_on_security_HVgcKTHp4bIA4ulCPqC7SL)

I wonder if there is any third-party verification of this? Considering that Intel vPro and other features could allow access even when a computer is powered off, who is checking that circuitry doesn't have some sort of keylogger or remote backdoor that could activate vPro or other functionality for hackers?

---

### Post by TheFu on 2013-10-27
It is impossible to verify every piece of hardware used everywhere in the world.
Anything left alone for more than a few seconds is susceptible to being modified, especially portable devices.
Any equipment that is connected to any computer should be provided by trusted vendors, not necessarily the lowest price vendor.

Google "rubber ducky usb" to get an idea.

---

### Post by NoBugs! on 2013-10-27
So it emulates a keyboard, and types stuff?

Don't worry I'm sure Apple will invent a computer with no usb drives so they don't have this vulnerability :)

---

### Post by TheFu on 2013-10-28
> **NoBugs! said:**
> So it emulates a keyboard, and types stuff?

Don't worry I'm sure Apple will invent a computer with no usb drives so they don't have this vulnerability :)

But it will still have displayport - with provides DMA access ... a HUGE vulnerability - up there with Firewire.  Direct memory access is probably the worst security idea ... ever.  Lets attackers read the encryption keys stored in RAM for people who use encrypted storage it completely defeats the purpose.  PCMCIA slots on laptops or PCI-minibus does the same things.  

I'd rather have USB ports than any of those things. With USB, I can disable it.  I don't know how to disable DisplayPort and still have an external screen, do you?

---

