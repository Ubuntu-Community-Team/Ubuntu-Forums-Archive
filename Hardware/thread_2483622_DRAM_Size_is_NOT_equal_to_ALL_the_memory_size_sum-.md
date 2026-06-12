---
title: "DRAM Size is NOT equal to ALL the memory size sum-up in BIOS"
date: 2023-02-04
forum: Hardware
---

### Post by jiapei100 on 2023-02-04
Hi, all:

I've installed **4 memories** which sum up to **128G**. However, in **BIOS**, **Current DRAM Size** shows **ONLY 98304MB**, ```
cat /proc/meminfo
``` the same **98304MB**.
Can anybody help please?

[ATTACH=CONFIG]291710[/ATTACH]

---

### Post by TheFu on 2023-02-05
Is some RAM being used by the iGPU?

---

### Post by Yellow Pasque on 2023-02-06
What motherboard? Any chance we can see output of:
```
free -h
sudo dmidecode -t mem
```

---

### Post by jiapei100 on 2023-02-07
> **Yellow Pasque said:**
> What motherboard? Any chance we can see output of:
```
free -h
sudo dmidecode -t mem
```

Great .... Thank you very much...
I finally realized the 4th memory was NOT accurately plugged in its slot. After a simple re-insertion, everything is Okay now... Thank you ...

---

### Post by TheFu on 2023-02-07
Please use the Thread Tools button to mark this thread as "SOLVED" to help others out.

---

