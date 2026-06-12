---
title: "Ubuntu 16.04 64-bit and Intel i7-4770 K processor with Haswell graphics"
date: 2016-05-12
forum: Hardware
---

### Post by cigtoxdoc on 2016-05-12
What are the correct drivers, programs, etc., for use with the i7-4770K and Ubuntu 16.04 64-bit.  Something has gotten lost on upgrade from 15.10 to 16.04.

Thank you,

John

---

### Post by Jonathan_Goodwin on 2016-05-13
Having recently been googling on that subject (as I have a Haswell-based laptop) and struggling with my own 16.04 LTS upgrade ..

My understanding is that the Intel Haswell GPU uses a Mesa-based video driver which Intel engineers contribute to. It is built into Ubuntu, including 16.04, something I can at least attest to on my machine. OpenGL support is still horribly backlevel (3.3), but much better support (4.0+) is expected very soon in an updated driver.

IIRC, the Intel web site offers downloads of their graphics driver, updated on a quarterly basis.

That is as much as I know, if that is helpful.

---

### Post by Bucky Ball on 2016-05-13
*Thread moved to **Hardware**.*

---

### Post by Linuxisfast on 2016-05-13
If you wish to stay current with MESA add oibaf ppa at [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) they are well tested with their own thread at Phoronix and work well.

---

