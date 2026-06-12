---
title: "Scanner UMAX Astra 5450"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by Profik123 on 2007-08-30
Does anyone know, how to solve this problem?

I start the xsane, scanner is recognized, but the lamp doesn't turn on. It normally starts the scanning, but the picture is completely black. 
[Here]("http://www.sane-project.org/man/sane-plustek.5.html") I saw, that my scanner is supported (actually the 5400 model, but that's quite same).

```

sane-find-scanner

found USB scanner (vendor=0x1606 [UMAX], product=0x0160 [USB SCANNER], chip=LM9832/3) at libusb:001:003

```

```

scanimage -L

device `plustek:libusb:001:003' is a UMAX 5400 USB flatbed scanner

```

Thx for your answer.

Sry of my bad english, I am from Czech republic

---

