---
title: "Help!  Updated System Today And Lost Network Card!"
date: 2008-10-15
forum: General Help
---

### Post by jacoulter on 2008-10-15
Hi,

I ran updates today for 8.0.4 64-bit (including the latest linux kernel) and after the mandatory restart my NIC has dissappeared.  When I run ifconfig all it reports is the lo loopback device.  How do I get Ubuntu to find and configure my NIC?

TIA,

Jim

---

### Post by samwisgg on 2008-10-15
Jim,

you're not the first one ... Simply go back to your previous linux kernel (sorry but it's the only solution for now). See this thread :

[http://ubuntuforums.org/showthread.php?t=948434]("http://ubuntuforums.org/showthread.php?t=948434")

---

### Post by Yellow Pasque on 2008-10-15
Is your NIC still showing with lshw and lspci? Does lshw show a driver loaded for your card?
```
sudo lshw -C network
sudo update-pciids
lspci | grep Ethernet
```

If your card is still functional, look at the interfaces and make sure eth0 is defined:
```
cat /etc/network/interfaces
```

---

### Post by jacoulter on 2008-10-15
Thanks - I forgot I had to load a new driver for the r8168 NIC driver in the previous kernal and had to rerun the switchmod script from [http://www.jamesonwilliams.com/hardy-r8168.htm](http://www.jamesonwilliams.com/hardy-r8168.htm).  The new kernal version wiped out the the driver change - I reran the script and everything works fine now - thanks for your help!

---

