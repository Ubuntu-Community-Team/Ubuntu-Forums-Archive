---
title: "USB Storage Failed to bind enclosure -19"
date: 2014-03-28
forum: Hardware
---

### Post by nibal on 2014-03-28
I have Ubuntu x64 13.10. I run custom kernel 3.13.6 because of my network card. I also have an external USB WD 3 TB "My Book". And that's where problems begin.
Whenever I boot into the default 13.10 kernel, it is recognized and mounted fine. Whenever I boot in my 3.13.6 custom kernel, I see it as an usb device but the scsi driver cannot mount it:

```

ses 71:0:0:1: Failed to bind enclosure -19

```

I have checked both kernels' configuration as well as the lsmod output and cannot get anywhere :-(

The custom kernel is necessary if i want to have network.
Any ideas, how to get also my USB storage working?

TIA

---

### Post by nibal on 2014-03-28
[QUOTE}
I have checked both kernels' configuration as well as the lsmod output and cannot get anywhere :-(

The custom kernel is necessary if i want to have network.
Any ideas, how to get also my USB storage working?

TIA[/QUOTE]

I should have suspected that something is wrong with the kernel, when I couldn't find anything suspicious in the configuration.
That was a 3.13.6 llt kernel. Maybe the llt or the 3.13.6 kernel had the problem. I downloaded the sources for the default 13.10
 kernel, 3.11.0.12, as a 3.11.0.orig + 3.11.0.12.diff. Funny thing when i patched it and built it it came out as 3.11.3. But it was
in the packages under sources for the linux-image-3.11.0.12-generic. Go figure ;-)

Anyway, this new kernel supports both my network card and the USB storage. :)

---

