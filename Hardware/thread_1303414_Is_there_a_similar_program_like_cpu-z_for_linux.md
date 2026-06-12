---
title: "Is there a similar program like cpu-z for linux?"
date: 2009-10-28
forum: Hardware
---

### Post by Vigh on 2009-10-28
Is there a similar program like cpu-z for linux? Cheers Ant

---

### Post by amauk on 2009-10-28
lshw

full output
```
sudo lshw
```

short output
```
sudo lshw -short
```

---

### Post by albandy on 2009-10-28
CPU:
cat /proc/cpuinfo
Memory
cat /proc/meminfo

Devices:
PCI Devices (cards, chipset)
sudo lspci -v

Usb devices
sudo lsusb -v

---

### Post by Vigh on 2009-10-28
what about for monitoring temperatures of hardware?

---

### Post by albandy on 2009-10-28
> **Vigh said:**
> what about for monitoring temperatures of hardware?

install sensors-applet: sudo apt-get install sensors-applet

---

### Post by Malsasa on 2013-03-24
Use CPU-G for Linux! Close similiar with CPU-Z: [http://www.webupd8.org/2009/10/cpu-z-for-ubuntu-cpu-g.html](http://www.webupd8.org/2009/10/cpu-z-for-ubuntu-cpu-g.html).

---

### Post by QIII on 2013-03-24
Thank you for sharing.  Everyone’s questions are important and answers are valuable.

&#65279;If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

*Thread** closed.***

---

