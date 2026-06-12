---
title: "nVidia GeForce 7150M / HP dv9000 series laptop - screen blurry"
date: 2008-10-22
forum: Hardware
---

### Post by PaulATL on 2008-10-22
Hi all,

I have an HP DV9000 series laptop with an AMD 64 processor, 17 inch screen, and nVidia 7150M graphics processor.  I've been running fine on Ubuntu 8.04 for months, thanks to envyNG.  However, with the latest kernel update. 2.6.24-21, my envyNG-installed nVidia driver stopped working (laptop went into low graphics mode), and I had to re-run envyNG.  Now, my screen resolution is correct, but it is a little blurry--not horrible, but I know if I were to use it for hours, I'd have eyestrain.

Does anyone know how I can fix this?

Current nVidia driver version: 173.14.12

Thanks!
  Paul

---

### Post by PaulATL on 2008-10-22
Never mind - found my own answer!

By going to System -> Administration -> NVIDIA X Server Settings and changing the screen resolution to its native 1440x900, all is now well.

If anyone else runs into this problem, hopefully this will help.

--Paul

---

