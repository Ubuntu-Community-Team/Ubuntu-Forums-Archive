---
title: "Latitude i8k kernel module"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by Verbunk on 2007-03-03
Hi Guys, 

      Small problem, 

          I have a latitude C840 which just had a video card upgrade, For some reason the system BIOS reports the machine as a Precision M50 and the i8k driver won't load anymore. Any tips on how I can get it working?

---

### Post by StephenSchaeffer on 2007-03-13
You might try adding:

i8k force=1

to your /etc/modules file. You can also 'sudo modprobe i8k force=1', but you'll have to do that every time you boot.

I don't know why the 'force' flag is needed, but I know it is on my machine. (Dell Inspiron e1705)

Good luck!

---

