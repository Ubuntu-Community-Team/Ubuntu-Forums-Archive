---
title: "Dell Inspiron 1420 Laptop"
date: 2009-02-17
forum: Hardware
---

### Post by igneousquill on 2009-02-17
I'm currently running Ubuntu 8.10 on my desktop, and I may be acquiring a Dell Inspiron 1420 Laptop in the next few days.  It currently has Windows on it, but I'd rather use a Linux distro.  Does anyone know if I'd have any problem with Ubuntu on this particular model?  If there's a list of compatible laptops somewhere, I'd appreciate the link.

---

### Post by nixscripter on 2009-02-17
There is a general list of supported hardware here: [https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

Speaking as a Dell Inspiron 1420n user, who bought it with Linux pre-installed, I found several things somewhat problematic after upgrading from their base system of 7.04 (Fiesty).

1. Wireless works -- sort of. You will have to change from the ip1495 (or whatever it is) to the iwl3495 driver to avoid all sorts of strange connection problems. The latter requires proprietary firmware, unfortunately.

2. The built-in modem with proprietary drivers doesn't work, at least not for me. Worse than that, if you try to upgrade your kernel too far, your sound card (which the modem is wired into, it's a soft modem) will not work either.

3. Direct support for the intel graphics card (with the open source i910 driver) is somewhat sketchy. 3D games (e.g. under Wine) crash, but Compiz and simple applications work. Oh, and the external monitor works, but the S-Video output doesn't.

4. I've had a little trouble with sleep and hibernation, but haven't investigated either lately.

I am someone who is willing to live with a few minor defects, several of which I probably caused. ;-) Just wanting to warn you.

---

