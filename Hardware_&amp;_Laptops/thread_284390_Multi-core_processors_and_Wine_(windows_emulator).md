---
title: "Multi-core processors and Wine (windows emulator)"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by Amurko on 2006-10-25
If I get a new computer with a multicore processor, get the appropriate kernel to use the multicore features, and then try to play Windows games through Wine, will those games be able to use the multicore processor?  In other words, will Wine be able to use the multicore ability of the processor or will it only be able to access one core, thus not taking full advantage of the hardware?

---

### Post by Rhubarb on 2006-10-25
Yes, wine will work perfectly with multithreaded games / programs very well.
You don't need to do modify anything to make it so, it just supports multi-core processors off the mark - so long as you're running an SMP kernel.

I just tried the benchmarking option in 7-zip (windows version) in wine, then in windows.  The benchmark actually runs faster running in Ubuntu under wine than it does in windows xp (haven't tried testing it in vista yet).

(wine = Wine Is Not an Emulator)

---

