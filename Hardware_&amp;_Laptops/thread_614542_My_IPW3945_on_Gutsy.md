---
title: "My IPW3945 on Gutsy"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by jolger on 2007-11-16
Hi there, i have a bit of a problem, when i try to modprobe ipw3945
i first of all get a module not found:

```

jolger@jolger-laptop:~$ sudo modprobe ipw3945
[sudo] password for jolger:
FATAL: Module ipw3945 not found.
2007-11-17 09:16:28: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
jolger@jolger-laptop:~$ 

```

If i however do an lspci, i can see the network card, the problem here is, that it says:
```

jolger@jolger-laptop:~$ lspci | grep PRO
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
jolger@jolger-laptop:~$ 

```
Note: The pci device displays as "Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)" and not "Intel PRO/Wireless 3945ABG Network Connection"

If anyone has any ideas to how i could resolve this problem, i'd be deeply gratefull :)

Also note: i am running Gutsy, it worked fine on Feisty, so i suppose there is something different in the way Gutsy detects hardware OR the restricted-modules just aren't built properly on my machine........ :P

Running:
Zepto ZNote 2425W
CPU: Intel Core¹ Duo 1.8GHz
Mobo: Unknown
Ram: 1GB
Ethernet:   Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
Wifi: Described above
GFX: Nvidia GeForce Go 7600

---

### Post by jolger on 2007-11-16
Bump, i'd love to see a solution to this, IF there is one that is...

/Jolger - AkA TP

---

### Post by narselon on 2007-11-16
I too have this problem. Wifi was running fine on gutsy until a mess where my graphics settings died on me when trying to fix the hibernate issues. I've so far fixed nearly everything but somehow the wifi disappeared somewhere along the way. The light indicator does not respond when I press fn+F2. The driver appears in the restricted drivers manager, but won't go "in use."  I downloaded a few of the others but they require either the ieee or the iwifi subsystem which then requires something with the kernel which they never make clear. I've seen a few people suggest booting into the generic kernel, which seems to bring back wifi but I can't access the desktop due to crashing or whitescreening due to compiz.

---

### Post by jolger on 2007-11-17
Works in the Generic Kernel for me o.o
Thanks ^.^

/Jolger AkA TP

---

