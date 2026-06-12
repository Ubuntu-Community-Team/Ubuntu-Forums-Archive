---
title: "Intel 845gv slow io"
date: 2008-12-31
forum: Hardware
---

### Post by Chronos6 on 2008-12-31
Hello There!

I've switched motherboard 3months ago, and the system seemed slow, but i thought it is becouse of the slower cpu, slower ram or something. 
Yesterday i bought a Corsair Voyager 8bg, what can write 13megabytes/sec, and i tried to copy stuff on it(small or huge files, doesent matter) it starts with 10 megs/sec, and decreases to 1,2megs. USB2.0 turned on, and would be slower when reading. I checked and the speed is flapping. once its 5megs, in the other second its 400k. Checked with iotop. When Firefox loading there is too much iowait going on. While copying the cpu is in use 5%, but full iowait is slowing the machine. I checked the Mobo chipset, but the problems solved since 2.4 kernels. Intel 845gv. asrock p4i45gv. Or is it? 
I have problems with the newest kernels(2.6.27, opened a bug at launchpad) and using 2.6.24-21. 
hdparm normal, but when copying anything to external hdd, usb stick or other partition it is hell slow. And i have HDIO_SET_DMA failed: Operation not permitted.

Any ideas? I hate that its hell slow. Runnung deluge and firefox at the same time equals with unusable system. But with 2ghz pentium4 processor and 512 megs of ram this shouldnt be a problem.

Thank you, hope somebody can help me.

---

### Post by moron on 2009-01-05
I can't comment on your other issues but the slow USB sounds like it might be this issue:

[https://bugs.launchpad.net/gvfs/+bug/197762](https://bugs.launchpad.net/gvfs/+bug/197762)

Cheers

---

