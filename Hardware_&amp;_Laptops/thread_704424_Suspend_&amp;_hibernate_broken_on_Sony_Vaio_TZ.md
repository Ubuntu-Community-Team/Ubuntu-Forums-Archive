---
title: "Suspend &amp; hibernate broken on Sony Vaio TZ"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by JohnHughes on 2008-02-22
On a Sony Vaio TZ 31 (TZ31WN/B to be exact)

```
# cat /sys/power/state
mem disk
# echo mem >/sys/power/state
[ system hangs ]

```

More or less the same think with suspend to disk.

Anyone got any ideas?

---

### Post by vishketan on 2008-02-22
Hi!

I have a sony vaio VGN SZ483N/C and had quite some trouble getting suspend and hibernate to work on Ubuntu 7.10.

Here are some pointers which might help:

- you need the 2.6.24 kernel for suspend and hibernate to work reliably. The downside of compiling and installing your own kernel is that the wireless drivers and the sound drivers (alsa) don't work anymore ::mad: You need to compile them from source. Alternatively you can use the latest alpha releases of Hardy which have the latest kernel.

- Follow the tips at [https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend]("https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend")
in order to disable agp and use NvAGP instead (after this trick hibernate works on my machine with the default kernel but not suspend).

Let me know if that works for you.

vishy

[kernelcheck](http://kcheck.sourceforge.net/) is helpful if you want to compile your own kernel.

---

### Post by JohnHughes on 2008-02-25
I compiled 2.6.24.2 from kernel.org.

Stole a config from debian sid.

Sound & wifi worked out of the box.

Only thing not working at the moment (apart from docking station - see other thread) are the AV keys (eject &c).

---

### Post by vishketan on 2008-02-26
Suspend and resume work for me with Hardy alpha 5. But if I login, suspend, and logout then the screen becomes garbled. 

Did you make any changes to your acpi-defaults in order to get yours to work?


As for the AV keys I suggest that you post to the calling all Vaio owners thread with your dsdt so that it can be looked into.

vishy

---

