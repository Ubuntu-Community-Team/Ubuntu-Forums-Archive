---
title: "nvidia driver -- how to enable fastwrites &amp; SBA?"
date: 2004-11-27
forum: Hardware &amp; Laptops
---

### Post by negativ on 2004-11-27
I don't even know if it will make that much difference, but how can I enable AGP Fast Writes and Side Band Addressing?  It sure sounds spiffy.

I'm on Hoary.

---

### Post by stodge on 2004-11-27
Does your hardware (graphics card and motherboard) support them?

---

### Post by negativ on 2004-11-27
> 
$ cat /proc/driver/nvidia/agp/host-bridge
Host Bridge:     VIA Technologies, Inc. VT8363/8365 [KT133/KM133]
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000217:0x00000104


$ cat /proc/driver/nvidia/agp/card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000217:0x1f000104


yep.

---

### Post by negativ on 2004-12-18
(Ibump)

Still interested in a solution to this, if anyone has it...

---

### Post by Botsinge on 2004-12-18
Just add it as arguments when you load the nvidia module. I have this line in my /etc/modules

```
nvidia NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1
```

---

