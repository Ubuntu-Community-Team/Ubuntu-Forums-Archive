---
title: "Faulty RAM, Memtest86+ &amp; BadRAM"
date: 2012-01-02
forum: Hardware
---

### Post by Dry Lips on 2012-01-02
Hi! 

 A little time ago I got some computer equipment that I'm trying to put to some good use. Unfortunately the RAM I got (Crucial BallistiX Tracer 2X2GB DDR2 800mhz (total 4GB)) apparently is faulty. After a couple of kernel panics, I've had enough and ran Memtest86+.
 

 However, I need some help in order to interpret the results... This is what I've got after testing it for nearly three hours on one computer.
 

```
Memory: 4095M
CHIPSET: AMD K8 IMC (ECC : Disabled)

401 MHz (DDR803) CAS: 5-5-5-18 / DDR2 (128bits)


WallTime   Cached  RsvdMem   MemMap   Cache   ECC  Test   Pass  Errors  ECC Errs
--------   ------  -------   ------   ------  ---  ----   ----  ------  --------
 2:51:20   4095M      136K    e820       on   off   Std      1      24         0


Tst  Pass  Failing Address            Good      Bad     Err-bits  Count Chan
---  ----  ----------------------   --------  --------  --------  ----- ----
4       0  000646b3fb4 - 1606.6MB   a9ee0402  a9ae0402  00400000      1
5       1  000606b4330 - 1542.7MB   00400000  00000000  00400000     11
5       1  000646b4310 - 1606.7MB   00400000  00000000  00400000     12
6       1  000646b3fb4 - 1606.6MB   f7ffffff  00000000  00400000     13

``` When I tried move the memory to another computer, I got different results. Is this perhaps because the modules were inserted in a different order, than during the memtest with the first computer? Is there any way to tell which module that is faulty (if it is one and not both.)

Here are the second results (after approx. an hour and a half of testing on another computer.)

```

Tst  Pass  Failing Address            Good      Bad     Err-bits  Count Chan
---  ----  ----------------------   --------  --------  --------  ----- ----
2       0  0003b94c04c - 953.2MB    ffffffff  ffbfffff  00400000      1
5       0  0003b94c148 - 953.2MB    00400000  00000000  00400000      2
5       0  0003f94c148 -1017.2MB    00400000  00000000  00400000      3 
7       0  0003b94c04c - 953.2MB    c944cc57  c944cc57  00400000      4
5       1  00008b4c328 - 139.2MB    ffefffff  ffffffff  00100000      7
5       1  0000cb4c308 - 203.2MB    ffefffff  ffffffff  00100000      8
5       1  0003b94c648 - 953.2MB    00400000  00000000  00400000      9
5       1  0003f94c628 -1017.2MB    00400000  00000000  00400000     10
8       1  0003b94co4c - 953.2MB    62f24cbb  62b24cbb  00400000     11

```Finally I wanted to know if anyone of you have used the BadRAM settings in Grub2? [https://help.ubuntu.com/community/BadRAM](https://help.ubuntu.com/community/BadRAM)
 

 How would I block out the faulty part based on the information in the second memtest above? I read the link I posted above, and I get the general idea, but I'm not sure how to do it in practice...  
 

 Any help would be much appreciated!

---

### Post by Dry Lips on 2012-01-03
bump

---

### Post by efflandt on 2012-01-04
Sometimes RAM just is not compatible with a chipset.  When I first got an early Athlon64 in 2004, some RAM I got was glitching WinXP or Linux and memtest85+ showed errors.  But OCZ exchanged it for RAM they guaranteed would work, and it did. Years later when I upgraded again, I had no trouble with PNY RAM.  By then RAM was likely compatible with more types of hardware.

Someone at work had an early Pentium4 (2 GHz I think) and it would occasionally blue screen with Crucial RAM.  When that PC was being retired, I checked it with memtest86+ and got errors (no errors with its original RAM).  But I put that Crucial RAM in a different 2.8 GHz PC, dual channel with RAM of slightly different speed, it got no errors at all, and is still being used today.

Have you tried testing one stick at a time?

---

### Post by Dry Lips on 2012-01-07
> **efflandt said:**
> Sometimes RAM just is not compatible with a chipset.  When I first got an early Athlon64 in 2004, some RAM I got was glitching WinXP or Linux and memtest85+ showed errors.  But OCZ exchanged it for RAM they guaranteed would work, and it did. Years later when I upgraded again, I had no trouble with PNY RAM.  By then RAM was likely compatible with more types of hardware.

Someone at work had an early Pentium4 (2 GHz I think) and it would occasionally blue screen with Crucial RAM.  When that PC was being retired, I checked it with memtest86+ and got errors (no errors with its original RAM).  But I put that Crucial RAM in a different 2.8 GHz PC, dual channel with RAM of slightly different speed, it got no errors at all, and is still being used today.

Have you tried testing one stick at a time?

Hi and thanks for taking the time to answer this thread. It's probably not a question of incomparability, since I tested it on two different machines. And finally I also got around to testing one stick at the time. It turns out that one stick if fine, but the other is faulty.

If I'm lucky, I might get that stick replaced by the vendor, but if not I'd like to hear from people who have used the BadRAM settings in Grub2... [https://help.ubuntu.com/community/BadRAM](https://help.ubuntu.com/community/BadRAM)

---

