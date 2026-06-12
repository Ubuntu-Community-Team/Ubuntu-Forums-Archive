---
title: "No LAN with Atheros L1"
date: 2011-08-08
forum: Hardware
---

### Post by pumrel on 2011-08-08
Hello, 
I am in a desperate need of help :( I am installing ubuntu on my friend's laptop which is an Asus F3E but I cannot make the ethernet card to work. It is an Atheros card.
```
03:00.0 Ethernet controller: Atheros Communications L1 Gigabit Ethernet (rev b0)
```Apparently, the driver module should already be built in the kernel but it doesn't seem to be working properly.
Lsmod showed the driver module loaded but with a 0 when in a Livecd.
Now I can' see it at all.
```
petra@petra-ntb:~$ modprobe alt1
FATAL: Module alt1 not found.

```How to make it work? I don't mind compiling it but I can't find where the source could be.
Moreover I was looking everywhere and I can't find any solution.

---

