---
title: "Wrong cpu detection?!"
date: 2009-10-26
forum: Hardware
---

### Post by Blacklightbulb on 2009-10-26
I have recently built another system and I've got everything right but for 1 issue. The BIOS detected the wrong CPU and it shows as a single core instead of a Dual Core.

Motherboard:
Asus M4N78 SE
Processor:
AMD Athlon64 X2 7850 Kuma

The BIOS detects the CPU as an Athlon64 3200+ Othello instead! The CPU is also detected wrong by UBUNTU  ```
cat /proc/cpuinfo/
``` and also by CPUZ on windows partition.

I have already tried clearing the CMOS //correctly
I have flashed the BIOS to the latest version and still same issue.
The Motherboard FULLY supports the processor without issues.


Any help is appreciated.

---

### Post by Yellow Pasque on 2009-10-26
> The Motherboard FULLY supports the processor without issues.
> The BIOS detects the CPU as an Athlon64 3200+ Othello instead!
Those two statements contradict each other. The mobo may claim to support the CPU, but if it doesn't detect properly with the latest BIOS, does it really support it? :\
If the BIOS can't detect the CPU correctly, then the OS probably won't either. 

Basically, you need to write to the mobo manufacturer and get support from them.

---

### Post by TenPlus1 on 2009-10-26
If the motherboard isnt even detecting your processor correctly then you'll have to wait for a bios update that fixes the problem...

So long as your processor works that's the main thing, as for dual-core, try 32-bit and 64-bit versions of Ubuntu to see if a specific version picks up the two instead of one...

---

### Post by Blacklightbulb on 2009-10-26
> **Temüjin said:**
> Those two statements contradict each other. **The mobo may claim to support the CPU, but if it doesn't detect properly with the latest BIOS, does it really support it? :\**
If the BIOS can't detect the CPU correctly, then the OS probably won't either. 

Basically, you need to write to the mobo manufacturer and get support from them.

Not really. Other people have got the same identical components working without issues.
What I want to know is how can I get the BIOS to redetect my CPU. You know when it says 1 CPU detected. What I tried since now doesn't work.

---

### Post by Yellow Pasque on 2009-10-26
Has the CPU ever detected properly (in any board)? I guess it could be a problem with the CPU rather than the mobo.

---

### Post by Blacklightbulb on 2009-10-26
> **Temüjin said:**
> Has the CPU ever detected properly (in any board)? I guess it could be a problem with the CPU rather than the mobo.

Yes.

---

