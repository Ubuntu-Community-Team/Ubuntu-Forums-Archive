---
title: "lockups on GA-Z87X-UD5H  both with 13.04 and 13.10 final beta"
date: 2013-10-08
forum: Hardware
---

### Post by tnttrx on 2013-10-08
hello.

currently I'm testing new configuration which includes 

- Gigabyte GA-Z87X-UD5H with BIOS F7
- Intel i5-4570
- 4 x DDR3 Kingston HyperX 1600MHz
- a lot of WD RED 3TB

whenever I put a pressure on storage system, dmesg starts filling with errors and eventually I get the hard lockup of whole machine. sometims it takes 10 minutes, sometimes couple of hours.

memtest86+ is passed many times without any errors.
I have tried ubuntu 13.04 with kernel 3.8 and ubuntu 13.10 final beta with kernel 3.11 (3.11.0-11-generic).
I have tried different hard drives (all of them are WD RED 3TB).
I have tried to stress only Intel integrated SATA controler and to stress only Marvell SATA controller.

each time I get errors similar to this in dmesg:
[http://pastebin.com/raw.php?i=TcFJ0YG3](http://pastebin.com/raw.php?i=TcFJ0YG3)

and when it eventually gets completely stuck, content of my monitor is similar to this:
[http://www.imagebam.com/image/52ddab280362713](http://www.imagebam.com/image/52ddab280362713)
[http://www.imagebam.com/image/d40b83280362714](http://www.imagebam.com/image/d40b83280362714)
[http://www.imagebam.com/image/3bc874280362715](http://www.imagebam.com/image/3bc874280362715)

as I am not really skilled in this kernel dumps decoding, could you please point me in right direction: what to try with the machine itself or where to fill in the bug report?

thx.

---

### Post by tnttrx on 2013-10-08
one more dmesg block:

[http://pastebin.com/raw.php?i=D8LXRLzi](http://pastebin.com/raw.php?i=D8LXRLzi)

---

### Post by tnttrx on 2013-10-16
board replaced with another one (exactly the same model) and I still have the same problem. :(

---

