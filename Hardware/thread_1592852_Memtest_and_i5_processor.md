---
title: "Memtest and i5 processor"
date: 2010-10-11
forum: Hardware
---

### Post by gizmobay on 2010-10-11
I purchased all the components to build a new home built system. I purchased a Raidmax new power supply. The power supply was faulty and I've cooked two motherboards and my RAM. I'm also concerned it cooked my i5 processor. The i5 video didn't work and the computer didn't boot until I added a separate PCIe card. I ran memtest on my 4GB of RAM and now I'm getting fail errors. My question does memtest test only the motherboard RAM or does it test the processor RAM. Also, does the i5 on video needed to be setup in the BIOS or does it work automatically or could this also mean my i5 is toast to.

---

### Post by cascade9 on 2010-10-11
Memtest will use a iny bit of CPU power, but it doesnt really test the CPU. 

If your having issues with the i5 GPU on a new motherboard, its likely you've cooked the GPU part of the chip at least, possibly more. Sorry :(

---

### Post by gizmobay on 2010-10-14
I unplug the computer after running memtest when it failed. I go out of town come back plug comp back in and now memtest passes the RAM. I don't understand as I didn't touch the inside at all.

---

### Post by cascade9 on 2010-10-14
'Dirty' power can make memtest fail.

---

