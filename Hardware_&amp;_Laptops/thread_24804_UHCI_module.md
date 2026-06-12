---
title: "UHCI module"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by hugos on 2005-04-08
Hi!
I've been trying to install the Speedtouch modem with the drivers of speedtouch.sourceforge.net
Everything went fine till I ran Speedtouch-start. When I run it, I get UHCI support.... KO.
I checked if I had the uhci module and no, there is no such module on my system.
How can I get this working, I mean if I have to install the module or not. If your answer is "yes, you do" please tell me if there is any way I can get the module without compiling the kernel.
My System is 5.04 and I made the "server" installation.

Cheers,
Hugo

---

### Post by p!=f on 2005-04-08
Please post your lspci and lsmod outputs here.

```

[~] > lsmod | grep uhci
uhci_hcd               29200  0
usbcore               103800  3 usbhid,uhci_hcd

```
You can also try...
```

sudo modprobe uhci_hcd

```

---

