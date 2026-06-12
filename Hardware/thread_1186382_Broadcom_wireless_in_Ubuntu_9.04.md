---
title: "Broadcom wireless in Ubuntu 9.04"
date: 2009-06-13
forum: Hardware
---

### Post by sconnelly on 2009-06-13
I recently installed Ubuntu 9.04 on my Dell Inspiron 1505 laptop.  I am having a problem getting my Broadcom 4311 wireless card to work.  Immediately after installation:

System -> Administration -> Hardware Drivers showed

   Broadcom B43 wireless driver 
   Broadcom STA wireless driver

with the B43 light green and "activated" and "currently in use".
Since the wireless wasn't working, I thought I would try the STA wireless driver.  I deactivated the B43 driver and activated the STA driver.  I thought both drivers would still be available, but the B43 driver didn't appear in the list after rebooting.  I think I can restore the B43 driver using 'modprobe', but I don't know which driver to use.  Does anyone have any suggestions?

---

