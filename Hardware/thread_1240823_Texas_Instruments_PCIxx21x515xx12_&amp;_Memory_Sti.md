---
title: "Texas Instruments PCIxx21/x515/xx12 &amp; Memory Stick"
date: 2009-08-15
forum: Hardware
---

### Post by ladaja on 2009-08-15
Hello, I have a laptop with this Card Reader "Texas Instruments PCIxx21/x515/xx12", the one I have read should work with Memory Stick cards, but when I plug in a ms card, nothing happend. I'd like to know if there exists any solution to this or why is this happening.
Extra information:
daniel@daniel-laptop:~$ dmesg 
   in -> [  745.545043] tifm_core: MemoryStick card detected in socket 0:0
   out -> [  797.807184] tifm0 : demand removing card from socket 0:0

daniel@daniel-laptop:~$ lspci  (all texas instruments computer has)
08:00.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:00.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:00.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:00.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


I have also tried to load manually the modules: tifm_7xx1, tifm_sd and tifm_core, but once loaded, the behavior is the same.

I hope you can help. Thank you very much for all.

---

### Post by ladaja on 2009-08-15
Please, I need your help and I'm sure it is a common issue.

---

### Post by ladaja on 2009-08-24
nobody can help me? nobody have a ms or xd card? pleeeease

---

### Post by sakundiak on 2009-09-29
Bump as i am having trouble with this as well

---

### Post by sakundiak on 2009-09-29
bump

---

### Post by sakundiak on 2009-10-01
Can someone please help out with this or at least tell me its impossible and only works with windows.

---

