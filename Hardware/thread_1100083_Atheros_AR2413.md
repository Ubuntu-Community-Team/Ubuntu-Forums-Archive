---
title: "Atheros AR2413"
date: 2009-03-18
forum: Hardware
---

### Post by DevinMcElheran on 2009-03-18
So I'm trying to fix my little brother's laptop up with Ubuntu, and I was wondering if there's firmware that I'd have to download separately and install or something? I get a driver in the "Hardware Drivers" utility, but it still isn't working. Any help is greatly appreciated, thanks.

---

### Post by pytheas22 on 2009-03-18
It might help to restart the computer after enabling the driver in 'Hardware Drivers'.  It might also work to run these commands:
```

sudo rmmod ath_pci
sudo modprobe ath_pci
```

If that doesn't do it, please post the output of these commands:
```

lsmod | grep ath
lshw -C Network
lspci -nn | grep -i atheros
uname -rm
```

---

