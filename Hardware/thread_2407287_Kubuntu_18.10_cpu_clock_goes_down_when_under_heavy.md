---
title: "Kubuntu 18.10 cpu clock goes down when under heavy workload"
date: 2018-12-02
forum: Hardware
---

### Post by 4techguns on 2018-12-02
When running resource-hungry applications or my Acer laptop is under heavy workload, the CPU clock goes down step-by-step to about 300 MHz depending on how heavy the workload is. Even when the hungry application closes, the clock limit just stays there and all I can do to fix it is a reboot. Anybody have a solution?

Computer Specs:
Intel Pentium N3710 @1.60 GHz (unexpectedly went to 2.56 GHz for all 4 cores)
4GB RAM
1 GB VRAM
Acer Aspire R3-131T

---

### Post by 4techguns on 2018-12-02
I finally found a solution by executing the following commands:
> sudo apt install linux-tools-generic
sudo cpupower frequency-set -d 2560000 -u 2560000
Output: 
Setting cpu: 0
Setting cpu: 1
Setting cpu: 2
Setting cpu: 3


---

