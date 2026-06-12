---
title: "Hang on starting network 686-smp"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by Quirky on 2005-12-23
I have a mobile pentium 4 with hyper threading installed in my laptop. With the 686 kernel everything works fine. I installed the linux-686-smp kernel and, without the pcmcia network card plugged in, everything works as expected. I plug in the network card and run `sudo /etc/init.d/networking restart' and the machine hangs.

Has anyone had similar experience? What can I do to try and track down the cause of this?

---

### Post by 23meg on 2005-12-23
Take a look in your kernel log for errors reported when the crash happens.

---

### Post by Quirky on 2005-12-24
I would, but the whole PC hangs. I can't do a thing. 

Is there a way to save a log to a different file before restarting networking?

EDIT: I guess that the lack of replies means that this is a genuine bug. [http://bugzilla.ubuntu.com/show_bug.cgi?id=21485](http://bugzilla.ubuntu.com/show_bug.cgi?id=21485)

EDIT2: It was a bug - The rt2500 driver is not compatible with SMP. Sadly this driver is pretty much deprecated in favour of rt2x00, which is still in the beta stages, but is going to support SMP kernels. Phew! Perhaps for Dappy Duck then..

---

### Post by ned.b on 2006-01-25
Aha - that explains it!

Thanks for the info Quirky!

---

