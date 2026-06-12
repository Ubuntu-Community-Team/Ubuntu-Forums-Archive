---
title: "Make Ubuntu re-detect hardware"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by rogier.de.groot on 2008-02-28
I've just installed Ubuntu (server variant) on a hard disk, then swapped that disk to another system, which doesn't have a cd-rom drive; hence the rather clumsy install method. Anyway, I think Ubuntu isn't recognizing the hardware properly now - eth0 won't work (eth1 works though). Eth0 being the on-board nic in the motherboard. How do I make Ubuntu redetect my hardware?

---

### Post by overdrank on 2008-02-28
> **rogier.de.groot said:**
> I've just installed Ubuntu (server variant) on a hard disk, then swapped that disk to another system, which doesn't have a cd-rom drive; hence the rather clumsy install method. Anyway, I think Ubuntu isn't recognizing the hardware properly now - eth0 won't work (eth1 works though). Eth0 being the on-board nic in the motherboard. How do I make Ubuntu redetect my hardware?

HI and in my experience it has detected the change on the first boot. Have you check to make sure the onboard nic is enabled in bios and was it working prior?

---

### Post by Yellow Pasque on 2008-02-28
Run some commands for us if possible
```
sudo update-pciids
lspci | grep Ethernet
cat /etc/network/interfaces
sudo ethtool eth0
sudo ifconfig
```

---

### Post by rogier.de.groot on 2008-02-29
Yes the nic is enabled and used to work fine on win2k - that was before eth1 was added though.
lspci show two 3Com nics but none of the other commands helps.
Isn't there something like "sudo dpkg-reconfigure hardware" ? I think the entries in /etc/modprobe.conf are wrong since the hardware switch.

---

### Post by rogier.de.groot on 2008-02-29
Some additional info: both cards are 3C509 (B and C), but the driver loaded (seen in lsmod) is "3c59x". I tried loading the "3c509" driver, but it didn't detect any nics (dmesg and tail /var/log/messages didn't show anything).

---

### Post by phil_elson on 2008-05-31
Almost exactly the same problem. Did you come across a solution?

Again eth0 not detected but eth1 is.


I have now fixed this problem thanks to the following thread:

[http://ubuntuforums.org/showthread.php?t=255018](http://ubuntuforums.org/showthread.php?t=255018)

---

