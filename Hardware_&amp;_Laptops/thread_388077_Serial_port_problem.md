---
title: "Serial port problem"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by Spectre5 on 2007-03-19
Hey, I need to "reset" my serial ports...is there a way to do this (like hotplug?)

I can use my serial port just fine, but if I go into hibernate and then return, it does not work.  If I reboot my computer, they work again no problem.  Is there a quicker way to get restart them besides rebooting my comp??

I am running xubuntu 6.10

Thanks,

Scott

---

### Post by randomdude on 2007-03-19
Does 

sudo /etc/init.d/setserial restart

do anything?

---

### Post by Spectre5 on 2007-03-19
> **randomdude said:**
> Does 

sudo /etc/init.d/setserial restart

do anything?

I get command not found...I looked in /etc/init.d/ and setserial is not there.

---

### Post by Spectre5 on 2007-03-19
I went and installed setserial....and it run nows...but doesn't fix the problem...any other ideas?

---

