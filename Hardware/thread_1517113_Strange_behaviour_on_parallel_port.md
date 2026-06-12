---
title: "Strange behaviour on parallel port"
date: 2010-06-24
forum: Hardware
---

### Post by Fibonacci on 2010-06-24
I'm trying to directly output data to the parallel port on Ubuntu.
I know the control pins are on port 0x037a, and the sixth bit counting from the right on that port controls the direction (in/out) of the data pins, 1 being in and 0 being out.
Say I run outb(0x00,0x37a). Then I can indeed output data on the data pins, so the sixth control bit should be a 0.
Next I run inb(0x037a), and get the value 0xe0 - the direction bit is set to 1, when I explicitly had set it to 0 before. Perhaps I was wrong with what I assumed each value would mean? I, then, write exactly the same value I got to the port I got it from, that is, run outb(0xe0,0x37a), and now I cannot output anything on the data bits. Surely they are set as inputs now.
Re-running outb(0x00,0x37a) will set them again as outputs, but the result of inb(0x037a) is still 0xe0.

Is there any way to prevent that from happening? At least make inb give me the same value I put on outb?

---

