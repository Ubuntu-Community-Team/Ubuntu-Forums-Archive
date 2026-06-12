---
title: "Printer Problem"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by DJDANG on 2008-01-10
:)Hello everyone, I've installed a xerox 3116 on my ubuntu pc, but whenever I print I receive an error in the printing, it says:

```

INTERNAL ERROR - Insufficient Memory

         POSITION : 0x1aa7 (6823)

         SYSTEM : eHeapImage

         LINE : 285212736

         VERSION : QPDL 1.22 12-29-2004

```

I installed the driver just as the manual said, but it always comes out with the error.
If anyone knows how to fix this problem, please post the instructions:)
:confused::confused::confused:

Thanks in advance:popcorn:

---

### Post by Sef on 2008-01-11
What are your system specs?  How much swap do you have?

---

### Post by DJDANG on 2008-01-11
How do I check how much swap I have?

---

### Post by Sef on 2008-01-11
> How do I check how much swap I have?

How big a swap partition did you make when installing Ubuntu?

---

### Post by DJDANG on 2008-01-11
:(I really dont remember, but I'll reinstall ubuntu so I can put some more space in the swap, I didn't think about that before:lolflag:. I'll tell u if I solved the problem:popcorn:

---

### Post by RainMaker1492 on 2008-03-11
I have the same exact problem with the same printer (xerox Phaser 3116)

I also tried downloading the linux drivers from Xerox but with not any luck.

did the changing of the SWAP size worked for you?

---

### Post by RainMaker1492 on 2008-03-11
Never mind.
I was able to fix it.

I changed the driver in "Printer Configuration" to "Generic GDI Printer Foomatic/gdi".
working fine so far.

---

