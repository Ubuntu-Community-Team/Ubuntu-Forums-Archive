---
title: "Stuck 800x600 res"
date: 2009-03-17
forum: Hardware
---

### Post by Vrekk on 2009-03-17
I install 8.10 on my laptop the other day and now I am a stuck in a 800x600 res. When I had 7.10 installed this was not an issue.
```
brett@brett-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
```
If that helps

---

### Post by overdrank on 2009-03-18
> **Vrekk said:**
> I install 8.10 on my laptop the other day and now I am a stuck in a 800x600 res. When I had 7.10 installed this was not an issue.
```
brett@brett-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
```
If that helps

You may try using xfix in the recovery mode. Recovery mode is usually the second choice from the grub when booting. You will be given 4 option and the last is xfix, after xfix is complete you should be given the option again and choose to boot normally.
You may also look at [X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by Vrekk on 2009-03-18
Xfix didnt work, and i dont know what you mean by the 2nd thing

---

