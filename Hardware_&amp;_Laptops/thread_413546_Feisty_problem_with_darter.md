---
title: "Feisty problem with darter"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by Rotarychainsaw on 2007-04-19
I upgraded last night and everything went well except for one thing.

It seems like the hard drive is being put to sleep or something, and then it takes around 30 seconds for it to get going again to read anything. This causes some pretty large delays trying to open a program or menu or whatever. 

I have decided its the hard drive by watching the system monitor applet, the pale blue indicates the CPU is wating but not actually doing anything. Also, I watch the HD light on the computer and it doesn't do anything and as soon as it finally does blink, the program starts working.

Anyway, any ideas?

---

### Post by heimo on 2007-04-19
I'm not sure if this should work - but if the syntax is correct and it works (doesn't work with my SATA drive), it should disable power management. Replace sda with your hard disks device.
```
sudo hdparm -B255 /dev/sda
```

---

