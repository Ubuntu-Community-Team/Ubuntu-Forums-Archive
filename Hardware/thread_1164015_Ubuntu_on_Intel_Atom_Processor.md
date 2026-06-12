---
title: "Ubuntu on Intel Atom Processor"
date: 2009-05-19
forum: Hardware
---

### Post by Chebyshev on 2009-05-19
I recently built a small computer for myself based on an Intel Atom dual-core processor. It has 2GB of RAM and runs off a 30GB SSD (OCZ Vertex).

I put 9.04 on it and I've been disappointed with the performance, particularly in Firefox. I do a lot of Django development and this page: [http://docs.djangoproject.com/en/dev/ref/models/fields/#ref-models-fields]("http://docs.djangoproject.com/en/dev/ref/models/fields/#ref-models-fields") eats 25% of the CPU (System Monitor seems to think I have 4 cores for some reason) constantly and makes Firefox almost unusable.

I know there is a Netbook remix of 9.04 that is meant for EEE PCs and the like, but I'm not interested in the different interface meant for small screens. Are there optimizations for the Intel Atom processor that I should look into? Is it just slow? Why does System Monitor think I have 4 cores?

---

### Post by SushiR on 2009-05-19
> **Chebyshev said:**
> Why does System Monitor think I have 4 cores?

The Atom works with hyperthreading...

---

### Post by snowpine on 2009-05-19
Ubuntu Netbook Remix will not boost your performance. (All it is is a different GUI.)

There is an lpia port of Ubuntu specifically designed for the Atom. I was very disappointed with it, but your mileage may vary: [http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)

Personally, when Firefox drags on my Atom-based netbook (Dell Mini 9) I try a different browser such as Opera. The Atom is a low power, low price chip, but it should get the job done. :)

---

