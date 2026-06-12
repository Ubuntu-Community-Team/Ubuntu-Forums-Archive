---
title: "megaraid2 support?"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by Scott Robinson on 2005-03-25
I'm attempting to install Ubuntu on to a Dell server using Perc 4e. However, only the megaraid driver is included in the installation media.

Is there any way to either download the megaraid2 driver, or generate an installation CD including the megaraid2 driver?

---

### Post by alastair on 2005-03-25
According to Christoph Hellwig (kernel developer) there is NO megaraid2 driver in Linux kernel 2.6 :

[http://lists.debian.org/debian-kernel/2004/12/msg00244.html](http://lists.debian.org/debian-kernel/2004/12/msg00244.html)

There does appear to be confusion generated around what driver supports which cards. This might be especially true for Dell rebranded parts (where you might need a more exact description).

Are you sure the "megaraid" module does not work for you? Perhaps ask on the Dell poweredge list :

[http://lists.us.dell.com/pipermail/linux-poweredge/](http://lists.us.dell.com/pipermail/linux-poweredge/)

---

### Post by Scott Robinson on 2005-03-25
I was confused. megaraid2 is a 2.4-ism. They've been split up in 2.6.

I've found and posted on an already existing bug in Ubuntu Bugzilla. Hopefully I can figure something out there.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=7759](https://bugzilla.ubuntu.com/show_bug.cgi?id=7759)

---

