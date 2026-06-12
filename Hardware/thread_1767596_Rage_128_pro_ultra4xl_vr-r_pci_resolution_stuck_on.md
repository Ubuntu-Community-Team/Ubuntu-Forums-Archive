---
title: "Rage 128 pro ultra4xl vr-r pci resolution stuck on 800x600"
date: 2011-05-25
forum: Hardware
---

### Post by jcer93705 on 2011-05-25
Hi guys this video card Rage 128 pro ultra4xl vr-r pci resolution stuck on 800x600. I actually sticking linux into this customer system because I'm tired of them bringing me with virus and stuff. But I have a problem that it's stuck on that low resolution. What can I do about it?

---

### Post by dandnsmith on 2011-05-26
I expect you're on the default driver module, and that this is what limits you.
Check out lsmod, and look for things like r128.
You could try the ATI drivers, but be prepared to find that they don't support your chosen version of Ubuntu (which you haven't told us about).
I changed to a 9200/9250 PCI card so I could use DVI to the monitor to hand - a great improvement.

---

### Post by jcer93705 on 2011-05-26
> **dandnsmith said:**
> I expect you're on the default driver module, and that this is what limits you.
Check out lsmod, and look for things like r128.
You could try the ATI drivers, but be prepared to find that they don't support your chosen version of Ubuntu (which you haven't told us about).
I changed to a 9200/9250 PCI card so I could use DVI to the monitor to hand - a great improvement.

Sorry I'm using kubuntu 11.04 32bit which I upgraded from kubuntu 10.10. I got out of it stock with 1024 x 1024? Something like that. Computer is very laggy I need to upgrade it but might end up telling her to upgrade the system with for sure a new case, motherboard combo and stuff.

---

