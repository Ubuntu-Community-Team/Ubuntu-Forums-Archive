---
title: "Screen Brightness Control"
date: 2009-10-08
forum: Hardware
---

### Post by jeggen on 2009-10-08
I am having a problem getting Ubuntu to manage my screen brightness.  It seems to change if I come out of standby without being plugged in but I can't change it dynamically.  I have tried adding the noapic option in my boot line in menu.lst but that didn't help.  I am not sure what to do next for troubleshooting.  I am using a HP/Compaq 8501w.

---

### Post by jeggen on 2009-10-15
I am still looking for some help on this issues.  Any suggestions on where/how to start troubleshooting?

---

### Post by imwithid on 2009-10-22
I've been having the same problem but using my desktop. The monitor is much too bright. I can control the brightness through Windows using the Intel driver (DG965OT motherboard - on-board video card). It is able to directly control the back lighting on the monitor.

I've been looking to resolve this problem for almost two years. Good luck. There seems to be no progress on this topic. Rather than focus on only laptops, there should be a more general control system for LCD monitors of all types.

You may want to be more specific as to the version of Ubuntu you are using as well as a breakdown of your hardware.

Type in your terminal:

```


$ lshw -businfo


```

---

