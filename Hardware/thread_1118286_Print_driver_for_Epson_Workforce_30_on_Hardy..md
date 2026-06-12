---
title: "Print driver for Epson Workforce 30 on Hardy."
date: 2009-04-06
forum: Hardware
---

### Post by YenTheFirst on 2009-04-06
Hello, I'm using kubuntu 8.04 [hardy], and I'm trying to set up a printer. I have an Epson Workforce 30. When I set it up, it's not in the list of drivers.

Googling revealed that gutenprint 5.2.* had initial support for this printer. Hardy only has up to 5.0.2. I tried using the intrepid/jaunty repositories, and updated foomatic-db-gutenprint,ijsgutenprint,and libgutenprint2 to the 5.2.3 version, but there isn't a 5.2.3, cupsys-driver-gutenprint, instead it's cups-driver-gutenprint. attempting to install this proposes breaking my entire system, and basically upgrading me to intrepid.

While I didn't upgrade the cupsys-driver-gutenprint package, the other ones are updated. When I went to try to set up the printer again, it reported that "KDE is rebuilding the driver database", but the driver still wasn't in the list.

I'd prefer to stay on Hardy [with KDE 3.5] rather than upgrade my entire system. Is there any way to get the Epson Workforce 30 printing?

---

