---
title: "4 CPUs?"
date: 2012-03-19
forum: Hardware
---

### Post by EricG1793 on 2012-03-19
I have a dual-core Core i3 on my laptop, and System Monitor gives usage statistics for 4 different "CPUs". I'm assuming that the 4 CPUs the OS recognizes are actually the cores in the processor, and the 4 "CPUs" are due to the hyperthreading, which I understand creates a virtual core for every physical core. Is this correct?

Is there a reason why different CPUs receive different usage rates at a given time? 1 and 3 seem to be the most active while the system idles, followed by 2 and 4.

---

### Post by Manyette on 2012-03-19
Yes you are correct.  Each physical core is equipped with the Hyperthreading to simulate a second core. My I7 shows 8 processors, which really means there are 4 cores, each with Hyperthreading. Little software currently support 4 cores, but some Linux software really does exercise all 4 plus the HT as well.

---

