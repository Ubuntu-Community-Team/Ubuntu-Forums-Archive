---
title: "no ethernet cart after upgrade to ubuntu 10.04 on my asus eeepc 1005ha"
date: 2010-06-14
forum: Hardware
---

### Post by webdebbyjoss on 2010-06-14
Hi,

Ethernet card is gone on my Asus EeePC 1005HA and I can't detect it after upgrade to Ubuntu 10.04

Everything was OK on Ubuntu 9.10 :confused:

```
# ifconfig -a
```

shows only "lo" interface 
and there is no "eth0" just like it was before

anyway "eth0" is present from LiveCD boot and disappears only after system installation and operating during some time (in a 1-3 hours after clear install)

tried couple times to re-install system and have the same result


```
# lspci 
```

shows only 

Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

so only wireless network is available and works OK but no any wired controller available


```
# lshw -C Network
```

same here, only wireless network adapter available


Where is my Ethernet card? 
Can anyone suggest something to detect wired adapter and bring it up?


P.S. Noticed that my wired network interface is still available after clear install but disappears on couple next reboots. While experimenting with cleat install I've noticed that ethernet card disappeared after installing packages like "eeepc-acpi-utilites", "eeepc-tray". By removing that packages it doesn't allow to bring Ethernet card back again. Also I had an option that Ethernet card were available even after installing those packages so I don't think that it has a direct relation to this problem but anyway just a notice.

---

### Post by webdebbyjoss on 2010-06-15
Ok, the question is:

How can I detect hardware in Linux if 

```


# lspci

# lshw


```

shows nothing...?

---

