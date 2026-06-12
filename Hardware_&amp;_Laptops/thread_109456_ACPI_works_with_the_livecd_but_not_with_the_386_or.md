---
title: "ACPI works with the livecd but not with the 386 or 686 kernels when installed"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by siennalizard on 2005-12-28
Dear Ubuntuers,

I've recently noticed when using a Breezy livecd for recovery purposes that it boots perfectly happily and provides ACPI. I have not yet been able to get ACPI consitently working on my Clevo M121W laptop, and the APM system provides no features and segfaults.

I had really given up on ACPI: when I start the computer, it gives normally critical temerature warnings in the 1000's of degrees and shuts down. On the rare occasion it would boot, the fan would never run. I don't have any of these problems with the livecd, so it has given me hope! Is there any way I can use this kernel/configuration on my system? My make-kpkg custom 686 kernel won't do it either.

I was able to get the ipw2200 wireless card working by following tutorials and howtos I found (by downgrading my gcc as recommended). I cannot seem to get this to work with my custom kernel (compiled with gcc-4.0)

I had to use a custom kernel because the system tried to upgrade the default 686 kernel, and I got a kernel panic on reboot.

I'm happy to provide any details you need. Many thanks for any help you can provide!

J.

---

### Post by siennalizard on 2005-12-29
To solve the ACPI problem, simply (haha) recompile your kernel from sources WITHOUT the ACPI thermal.ko module, although you're warned not to do it. Contact me if you have problems with the recompile. Get the kernel sources with Synaptic and untar them (they're in /usr/src), then try something like this:

```

make-kpkg --initrd --revision=1 --append-to-version=custom kernel_image kernel_headers

```

Then install the resulting .debs in /usr/src. Ask me if you need help.

J.

More notes:

This gives you a booting, functioning system. I'm just worried about the temperature. The /proc/acpi/fan directory is empty, although all the thermal information is ok. The fan module is loaded, but doesn't create any files in that directory. The fan _never_comes on... Am I at risk of cooking my lappy? It's around 65 deg. C. at the moment, and it's not _really_ under load...

J.

---

