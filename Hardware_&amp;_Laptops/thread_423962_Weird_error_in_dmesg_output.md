---
title: "Weird error in dmesg output"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by jalefkowit on 2007-04-26
Does anyone know what this error in the output of dmesg means?

```
APIC error on CPU0: 01(01)
```

My dmesg output is literally clogged with it, but there doesn't seem to be any adverse effects; everything on my system is (by all outward appearances) working fine. But any errors with the CPU make me very, very nervous, and I'd rather figure them out before they pile up and my CPU dies rather than after :)  But Googling for the error doesn't return anything useful.

So with that in mind, anybody have a clue what this means?

(For reference, the CPU is an AMD Athlon 2400+, in an Abit KX7-333 motherboard. Yes, I know it's time I bought a new computer. so you don't need to remind me :) )

---

### Post by earobinson on 2007-04-26
[http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller](http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller)

---

### Post by jalefkowit on 2007-04-26
I have no idea what I'm supposed to do with that Wikipedia page.  It has a one-sentence explanation of what an APIC is, but not what the error I'm seeing means, or what I should do about it, if anything...

---

### Post by earobinson on 2007-04-26
A Programmable Interrupt Controller (PIC) is a device which allows priority levels to be assigned to its interrupt outputs. When the device has multiple interrupt outputs to assert, it will assert them in the order of their relative priority. Common modes of a PIC include hard priorities, rotating priorities, and cascading priorities. PICs often allow the cascading of their outputs to inputs between each other.

Your computer is having an error. I would not worry much about this unless you notice other bugs. Since If your program interupt controler dident work your computer would not be able to multy task and since you can I assume that its working (just maybe not fully)

[http://en.wikipedia.org/wiki/Programmable_Interrupt_Controller](http://en.wikipedia.org/wiki/Programmable_Interrupt_Controller)

---

### Post by jalefkowit on 2007-04-26
OK, that's helpful -- thanks!  I had been treating it as a low-priority issue, sounds like that's the appropriate course...

---

### Post by earobinson on 2007-04-26
yup. you could run hwdb-gui fomr the terminal and make a note of it when you submit your hw profile.

---

