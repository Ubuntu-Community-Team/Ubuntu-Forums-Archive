---
title: "HP laptop shut down when viewing web videos"
date: 2009-09-09
forum: Hardware
---

### Post by Sue-Ann on 2009-09-09
I have recently installed Ubuntu 9.04 on my (not so new) HP pavilion ze5500 laptop. Everything is running fine, except when I try to watch web videos from websites such as Greatstufftv.com and alluc.org after about 15mins of watching the computer hibernates/shuts down. I thought I just needed to modify the power management and screen saver but I did that and it still shuts down...help!!

---

### Post by sergiom99 on 2009-09-09
What about overheating?
You can monitor temperature with lm-sensors:
1) ```
$ sudo apt-get install lm-sensors
```
2) ```
$ sudo sensors-detect
```
3) ```
$ sensors
[I]acpitz-virtual-0
Adapter: Virtual device
temp1:       +30.0°C  (crit = +95.0°C)
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +27.0°C
Core0 Temp:  +24.0°C
Core1 Temp:  +33.0°C
Core1 Temp:  +31.0°C
[/I]
```

And I would start by compiling my own DSDT file. Its easy and it helped a lot in mine: 
[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

You can also post your laptop specs to see if the help anyone.

---

### Post by Sue-Ann on 2009-09-09
Thanks alot

---

