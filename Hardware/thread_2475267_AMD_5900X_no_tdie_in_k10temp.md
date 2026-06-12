---
title: "AMD 5900X no tdie in k10temp"
date: 2022-05-20
forum: Hardware
---

### Post by clauder2 on 2022-05-20
Hi,

I just did upgrade to 22.04 from 21.04 and now sensors does not report the die temperature (tdie) of my AMD 5900X. Here is the output from sensors:
k10temp-pci-00c3
Adapter: PCI adapter
Tctl:         +51.9°C  
Tccd1:        +36.0°C  
Tccd2:        +35.0°C  

For what it's worth, the MB is an Aorus Pro AC (B550).

The kernel is 5.15.0-30-generic

Is something broken in 22.04?

---

### Post by TheFu on 2022-05-20
The kernel was undergoing lots of AMD updates, specifically for sensor data.
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.15-HWMON](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.15-HWMON)  that link mentions that a new driver is needed, so that would be something to validate.

I've always had less than great sensor data on my Ryzen systems.  I'm not running 22.04.  We're just now looking to migrate to 20.04. Stability is very important.

Now that AMD has 30% of the CPU market, perhaps we'll be treated like 2nd class citizens?

---

### Post by Yellow Pasque on 2022-05-22
> **TheFu said:**
> The kernel was undergoing lots of AMD updates, specifically for sensor data.
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.15-HWMON](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.15-HWMON)  that link mentions that a new driver is needed, so that would be something to validate.

The driver is included in the 5.15 kernel. You missed the important line in the article: "fixed up the driver to no longer display Tdie temperatures if there is no difference from the Tctl temperature."

---

### Post by TheFu on 2022-05-24
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.19-HWMON](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.19-HWMON) v5.19 kernels get more support for AMD Ryzen sensors, at least for 570 motherboards.  Sadly, I have twin 450 motherboards.

---

### Post by Yellow Pasque on 2022-05-24
> **TheFu said:**
> [https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.19-HWMON](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.19-HWMON) v5.19 kernels get more support for AMD Ryzen sensors, at least for 570 motherboards.  Sadly, I have twin 450 motherboards.

Okay, but I'm not sure what that has to do with the OP's question.
Let me clarify: Nothing is broken in 22.04 with the 5.15.x kernel. Not seeing Tdie is expected on CPU's that don't use an offset for Tctl. Or, for a more technical explanation: [https://www.hwinfo.com/forum/threads/cpu-temp-sensors-explanation.5597/#post-20914](https://www.hwinfo.com/forum/threads/cpu-temp-sensors-explanation.5597/#post-20914)

---

### Post by TheFu on 2022-05-24
It is related to Ryzen and sensors, which will likely draw other lurkers.  A little deeper sharing of information sources doesn't hurt, does it?

---

