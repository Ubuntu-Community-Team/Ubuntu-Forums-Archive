---
title: "MPX-6864 Capture card kernel panic"
date: 2014-02-13
forum: Hardware
---

### Post by nevixa2 on 2014-02-13
Hello,

I ordered a MPX-6864 and I’m trying to install it on Ubuntu. When looking at  the specs, it should work on Linux 3.2 kernel. On higher kernels (I tried 3.8,  3.9, 3.12) the driver does not compile, but on the 3.2 kernel the driver does  compile. When I load the driver on the 3.2 kernel, the complete system freezes.  I tried Ubuntu 12.04 and Ubuntu 10.04 with all sorts of kernels. 

I checked the logfiles and the only reference I could find to the card was:

```
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   10.910830] tw686x driver version 0.1.1 loaded
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   10.910833] tw686x driver dma_mode=1, debug=0
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   10.910867] tw686x 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   10.910881] tw686x[0]: subsystem: 0000:0000
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.046305] tw686x[0]: registered device video 0 [v4l2]
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.046337] tw686x[0]: registered device video 1 [v4l2]
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.046363] tw686x[0]: registered device video 2 [v4l2]
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.046387] tw686x[0]: registered device video 3 [v4l2]
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.046411] tw686x[0]: registered device video 4 [v4l2]
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.047488] tw686x[0]: registered device video 5 [v4l2]
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.048526] tw686x[0]: registered device video 6 [v4l2]
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.049560] tw686x[0]: registered device video 7 [v4l2]
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.051742] tw686x[0]: tw686x_setup() Failed to create audio adapters 7
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.051752] tw686x[0]: found  at 0000:01:00.0, bus: 1, rev: 1, irq: 16, latency: 0, mmio: 0xf0000000
syslog.1:Jan 31 08:56:21 bcr013 kernel: [   11.051759] tw686x 0000:01:00.0: setting latency timer to 64
```

  
I also made a picture of the kernel panic screen: [IMG]http://studiodiip.eu/ubuntucrash.jpg[/IMG]


 Of course the people at Commell said that in their system it works fine on Ubuntu 12.04 with kernel 3.2. Can someone help me with figuring this out? What logfiles should I look into, etc? I'm running a clean install of Ubuntu 12.04 with kernel 3.2.0.58.

Thank you very much!

---

### Post by nevixa2 on 2014-02-17
Even a hint of how to debug such errors would be great!
Thank you

---

### Post by nevixa2 on 2014-02-17
Maybe some more info on a crash. I also followed all steps for IRQ debugging, without any success.

[IMG]http://studiodiip.eu/DSC_1219.JPG[/IMG]

---

### Post by antonglu on 2014-03-29
Have you fix it? I have the same problem with 6864.

---

