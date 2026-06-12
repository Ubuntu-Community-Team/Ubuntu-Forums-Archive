---
title: "Question regarding rtl_fm and specific USB port connections"
date: 2018-01-19
forum: Hardware
---

### Post by francistransitron2 on 2018-01-19
Hi,

I am planning to use 2 RTL-SDR dongles on a single computer. The thing  is, they will be operating on 2 different frequencies, and so different  antennas will be used. 

I would like one instance of rtl_fm or gnuradio to open set to  "frequency 1" and connect to a specific USB port. Then the other  instance on "frequency 2" to another USB port.

I know that in Linux, USB ports are defined at a kernel level as such:
"The name given to this device by the kernel (KERNELS=="1-4.5")  indicates that this device is plugged into the fifth port of a hub  connected to port four on bus 1"

The computer I am using has no hub, and only one bus. It has 4 ports. So I would like to use 1-3.1 and 1-4.1 for example.

Can someone help me for this?

Thank you

---

