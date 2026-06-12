---
title: "USB controllers not working"
date: 2006-09-17
forum: Hardware &amp; Laptops
---

### Post by commodore on 2006-09-17
I got a USB mouse from my friend (haven't payed for it yet), because I have a crappy mouse :S. I plugged it in and hoped it will work. It didn't and later I noticed that the light inside it doesn't even turn on. So I think the problem is in the USB controller but it doesn't work in any of the USB ports. To I have to open my box and check for hardware problems?

---

### Post by commodore on 2006-09-17
Bump

---

### Post by commodore on 2006-09-18
BUMP

No ideas at all :P?

---

### Post by commodore on 2006-09-22
It has to be a driver problem because the controller works on Windows with the drivers from the manuafacturer's website. My motherboard is Biostar M7VIP.

---

### Post by christhemonkey on 2006-09-22
If you plug it in, could you supply the output of:
```
dmesg | tail 
```

and
```
cat /var/log/syslog 
```

---

### Post by commodore on 2006-09-23
No change in that.

---

### Post by IanW on 2006-09-23
Check USB is turned on in the BIOS?

---

### Post by commodore on 2006-09-24
Yes it is. There are different options, I chose "All enabled".

---

### Post by mgmiller on 2006-10-02
Try disabling legacy USB support in BIOS.

---

