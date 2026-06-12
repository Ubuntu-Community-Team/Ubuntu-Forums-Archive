---
title: "Dual cores"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by Xzenome on 2007-02-22
I have an Intel dual core processor (I'm not sure which) and it is x86 **not** x86_64. Anyway I noticed when I was running BOINC earlier that it only counted one processor (but I know it is dual core). Does Ubuntu x86 not use both processors or something. How can I rectify this? No one seemed to know on IRC.

---

### Post by mikewhatever on 2007-02-22
6.06 and 6.10 versions work with dual cores. You can get a desktop CD and try it.

---

### Post by Xzenome on 2007-02-22
> **mikewhatever said:**
> 6.06 and 6.10 versions work with dual cores. You can get a desktop CD and try it.

I am using Ubuntu 6.10 now.

---

### Post by MystaMax on 2007-02-22
Type ```
uname -a 
``` at the terminal and see if it says anything about SMP. In ubuntu, theres also a system monitor which shows CPU usage for both cores. Its on the system panel menu, I believe under Administration. Correct me if I'm wrong guys. I'm on a windows box at work now :( .

---

### Post by mikewhatever on 2007-02-22
Yes, the system monitor is in System->Administation->System Monitore and it should show two CPUs.

---

### Post by Xzenome on 2007-02-23
From uname -a
```
michael@Xenon:~$ uname -a
Linux Xenon 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux
```

Also System Monitor only shows one CPU.

So how can I fix this?

---

### Post by Rui Pais on 2007-02-23
try
```
sudo aptitude install linux-image-generic
```
and reboot to your new kernel. (should be 2.6.17-11-generic)

---

