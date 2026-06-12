---
title: "Ubuntu 17.10: [Firmware Bug]: TSC_DEADLINE"
date: 2017-10-20
forum: Hardware
---

### Post by dorko20 on 2017-10-20
Hello guys, 
I've installed the newest Ubuntu 17.10 and I am getting this error during boot:
```
[Firmware Bug]: TSC_DEADLINE disabled due to Errata; please update microcode to version: 0x25 (or later)
```
The systems boots up without any other problem, everything seems to be working OK. The system is fully updated.
I am wondering why is this error showing. My notebook model is Lenovo ThinkPad 450s and has the latest drivers installed.

My CPU model is:
```
Intel(R) Core(TM) i5-5300U CPU @ 2.30GHz (family: 0x6, model: 0x3d, stepping: 0x4)
```

I am running this system under the latest VMware Player 14.0.0 build-6661328 (Windows 7 64-Bit). 
Under this VM, Intel VT-x/EPT is enabled.


Please see dmesg log attached.

---

### Post by dorko20 on 2017-10-20
seems like this is a bug:
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724650](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1724650)

---

