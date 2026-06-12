---
title: "finding out motherboard and ram"
date: 2009-11-30
forum: Hardware
---

### Post by CastorTroyXXIV on 2009-11-30
hi, is there a program to tell me what kind of motherboard i have? and ram i have? i was gonna buy a graphics card and some more ram. is there a program i can use to find this information? thanks.

---

### Post by sisco311 on 2009-11-30
[hardinfo]("apt://hardinfo") (apturl link, click the link to install it) is a GUI application that displays information about your hardware.

Go to Applications -> System Tools -> System Profiler and Benchmark to run it.

informations about the motherboard are under *Devices -> DMI* and
informations about the RAM are under *Devices -> Memory* 

Or you could use the:
```
sudo lshw -class bus
```
and
```
sudo  lshw -class memory
```
commands in a terminal.

Or you could create a html file with the system info on the Desktop:
```
sudo lshw -html > ~/Desktop/sysinfo.html
```

Open it with your favorite web browser.

---

