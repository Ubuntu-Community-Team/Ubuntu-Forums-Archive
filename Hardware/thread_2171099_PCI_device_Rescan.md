---
title: "PCI device Rescan"
date: 2013-08-29
forum: Hardware
---

### Post by larry10 on 2013-08-29
Hi,

I try to rescan my PCIe device on Ubuntu 13.04, I use : sudo echo 1 > /sys/bus/pci/rescan

and system would show : bash /sys/bus/pci/rescan: Permission denied

How should I fix it ?

or, do I have other way to rescan my PCI device ?


Thanks !

---

### Post by djbuijs on 2014-02-25
This worked for me:
sudo chmod 777 [COLOR=#000000]/sys/bus/pci/rescan
[/COLOR]
That said, my PC rebooted when I tried [COLOR=#000000]sudo echo 1 > /sys/bus/pci/rescan[/COLOR]

---

### Post by Yellow Pasque on 2014-02-26
[https://blogs.oracle.com/joshis/entry/sudo_echo_does_not_work](https://blogs.oracle.com/joshis/entry/sudo_echo_does_not_work)

---

