---
title: "Graphics Driver Keeps Crashing"
date: 2017-06-15
forum: Hardware
---

### Post by snorty2 on 2017-06-15
Ubuntu 16.04 LTS Desktop

The computer runs great, except it freezes about once an hour. Below is a copy of the error. I've tried using the nvidia proprietary drivers (the last 4), but they are much worse. 

So my goal is to get the GTX 650 ti working with the Nouveau open-source driver. But here's what the log says after the computer freezes:

```
Jun 15 16:26:50 hostname kernel: [ 7175.736769] nouveau 0000:01:00.0: gr: TRAP ch 5 [003f8aa000 compiz[2059]]
Jun 15 16:26:50 hostname kernel: [ 7175.736776] nouveau 0000:01:00.0: gr: GPC0/TPC0/TEX: 80000041
Jun 15 16:26:50 hostname kernel: [ 7175.736782] nouveau 0000:01:00.0: gr: GPC1/TPC0/TEX: 80000041
Jun 15 16:26:50 hostname kernel: [ 7175.736787] nouveau 0000:01:00.0: gr: GPC2/TPC0/TEX: 80000041
Jun 15 16:26:50 hostname kernel: [ 7175.736791] nouveau 0000:01:00.0: gr: GPC2/TPC1/TEX: 80000041
Jun 15 16:26:50 hostname kernel: [ 7175.736804] nouveau 0000:01:00.0: fifo: read fault at 00023b7000 engine 00 [GR] client 01 [GPC0/T1_0] reason 02 [PTE] on channel 5 [003f8aa000 compiz[2059]]
Jun 15 16:26:50 hostname kernel: [ 7175.736805] nouveau 0000:01:00.0: fifo: gr engine fault on channel 5, recovering...
Jun 15 16:28:43 ...

```

---

### Post by gsahli on 2017-06-15
Can you try that graphics card in another computer? Do you have Windows also loaded to try? I suspect the card is failing.

---

### Post by efflandt on 2017-06-17
In spite of graphics cards being solid state and Nvidia chips being good,they can fail depending upon who makes the card. Who made your card?

I had a cheap Galaxy GT 430 that began failing shortly after its 1 year warranty expired. Eventually graphics would glitch during boot and according to logs the nvidia driver said the hardware was not responding. But I never had any trouble with EVGA GTX 550 Ti, MSI GTX 750 Ti, or current Asus GTX 1060.

Of course compiz has always occasionally had crash issues at times, but that does not seem to result in any graphics issues for me, it just generates crash reports. I probably do not even need compiz because I do not do anything fancy with the desktop.

---

### Post by snorty2 on 2017-06-19
I recently moved the 650gtx from a Windows PC to the Ubuntu box. It worked fine on that machine. 

Just in case, I moved the 650gtx over to another Ubuntu computer, and stress tested the gfx card for 24 hours. It passed with no problems.

---

### Post by Yellow Pasque on 2017-06-19
I would try a newer kernel (in other words, an updated nouveau module) to see if the bug has been fixed.
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11.6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.11.6/)

---

### Post by snorty2 on 2017-06-19
I added the PPA for Nouveau, removed/purged all nvidia and intel gpu drivers, and updated the Nouveau kernel. Now when it freezes I get this error:

```

Jun 19 16:00:56 hostname kernel: [ 2459.514559] nouveau 0000:01:00.0: fifo: SCHED_ERROR 0a [CTXSW_TIMEOUT]
Jun 19 16:00:56 hostname kernel: [ 2459.514563] nouveau 0000:01:00.0: fifo: gr engine fault on channel 2, recovering...

```

---

### Post by gsahli on 2017-06-20
Hmm, Still looking like graphics card failure (or nouveau problem with that model).

---

### Post by Yellow Pasque on 2017-06-20
Then you should probably report the bug:
[https://nouveau.freedesktop.org/wiki/HangDiagnosis/](https://nouveau.freedesktop.org/wiki/HangDiagnosis/)

---

