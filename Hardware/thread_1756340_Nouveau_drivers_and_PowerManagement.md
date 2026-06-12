---
title: "Nouveau drivers and PowerManagement"
date: 2011-05-12
forum: Hardware
---

### Post by lviggiani on 2011-05-12
Hi everybody,
according to [this]("http://nouveau.freedesktop.org/wiki/PowerManagement") the nouveau driver should have power-management and GPU clock rescaling capabilities (something like powermizer).
I'm using nouveau driver on my laptop with GeForce 8400M and the driver seems working fine including 3D support. However, xsensors reports a GPU temperature around 85°C compared to the proprietary drivers keeping the GPU around 70°C with powermizer set to "adaptive". This makes me believe that nouveau is currently keeping the GPU at its maximum performance level, thus not actually rescaling clock on actual usage.
I've tried googling around but I couldn't find neither any information about how to set nouveau driver to and adaptive policy nor if that is currently possible.
Has someone more precise information about this topic?
Thanks in advance, Luca.

---

### Post by lviggiani on 2011-05-23
Well,
after chatting with a nouveau developer and exchanging some log files I discovered the following:
- Power Management in nouveau is not implemented yet. They are still reverse engineering the thing and still trying to understand how it works.
- Thus there is no "PowerMizer" like feature yet in the nouveau drivers
- There is a way to manually change GPU / Memory clock but it is still too dangerous to try at the moment as it might burn your hardware out.

---

