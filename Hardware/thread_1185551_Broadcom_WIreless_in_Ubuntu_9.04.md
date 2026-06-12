---
title: "Broadcom WIreless in Ubuntu 9.04"
date: 2009-06-12
forum: Hardware
---

### Post by sconnelly on 2009-06-12
I recently installed Ubuntu 9.04 on my Dell Inspiron 1505 laptop.  This laptop has a Broadcom 4311 wireless card.  I have never been able to get this card to work.  I tried ndiswrapper and fwcutter.  After installing Ubuntu 9.04 I tried System->Administration->Hardware Drivers and got:

Broadcom B43 wireless driver 
Broadcom STA wireless driver

with the B43 light green and "activated" and "currently in use".
Since the wireless wasn't working, I thought I would try the STA wireless driver.  I deactivated the B43 driver and activated the STA driver.  I thought both drivers would still be available, but the B43 driver didn't appear in the list after rebooting. I think I could reinstall the B43 driver by using 'modprobe'.  Does anyone know which of these drivers gives me the best route to a working wireless card?

---

