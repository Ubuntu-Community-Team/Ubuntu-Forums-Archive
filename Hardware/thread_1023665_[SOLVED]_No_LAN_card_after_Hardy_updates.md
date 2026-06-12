---
title: "[SOLVED] No LAN card after Hardy updates"
date: 2008-12-28
forum: Hardware
---

### Post by oygle on 2008-12-28
Have a 64-bit computer running Hardy. It hasn't been used for a while and there were 146 updates to apply. The updates went just fine, rebooted, and now no eth1.

There is no eth1, and there are no lights showing at the back of the computer where the LAN cable is plugged in.

I try a network restart and it says 'failed to bring up eth1'

The lspci command displays the network card as

> 
02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)


Oygle

---

### Post by shafi on 2008-12-28
> **oygle said:**
> Have a 64-bit computer running Hardy. It hasn't been used for a while and there were 146 updates to apply. The updates went just fine, rebooted, and now no eth1.

There is no eth1, and there are no lights showing at the back of the computer where the LAN cable is plugged in.

I try a network restart and it says 'failed to bring up eth1'

The lspci command displays the network card as



Oygle
Remember after the kernel upgrade always you need to introduce the installed drivers again to the upgraded kernel.
so you need to find the driver and install it again, after that you will get back the interface.

---

### Post by oygle on 2008-12-28
I found a thread at [http://ubuntuforums.org/showthread.php?t=770173&highlight=Attansic](http://ubuntuforums.org/showthread.php?t=770173&highlight=Attansic) , which is just for this particular (inboard) LAN card.

Oygle

---

### Post by albinootje on 2008-12-28
> **oygle said:**
> Have a 64-bit computer running Hardy. It hasn't been used for a while and there were 146 updates to apply. The updates went just fine, rebooted, and now no eth1. 

Try to boot from any of the older kernels from the grub-menu, and if you have internet through that, run this
```

sudo update-pciids
lspci | grep -i Attansic

```
to see whether your NIC gets recognised properly.

---

### Post by oygle on 2008-12-29
In this thread - [http://ubuntuforums.org/showthread.php?t=770173&page=7](http://ubuntuforums.org/showthread.php?t=770173&page=7) , I mentioned that after an upgrade to Intrepid, the LAN card is working again.

---

