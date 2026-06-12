---
title: "Need Network Lan Software for HP C795 EE"
date: 2008-10-05
forum: Hardware
---

### Post by bluebirday on 2008-10-05
Need Network Lan Software for Laptop HP C795 EE
I am using ubuntu 8.04.1

Network Adaptor in Vista as follows

Atheros AR5007 802.11b/g WiFi Adaptor
Realtek RTL8139/810x Family Fast Ethernet NIC

Thanks

---

### Post by pytheas22 on 2008-10-05
Please try following the instructions in the first post of [this thread]("http://ubuntuforums.org/showthread.php?t=798485"), which will install the latest madwifi drivers.  They should support your card.  If you run the script successfully but your wireless still doesn't work after a reboot, please post the output of the following commands in Ubuntu:
```

lsmod | grep ath
lshw -C Network
lspci -nn | grep -i atheros
dmesg | grep ath
sudo iwlist scan
```

---

### Post by bluebirday on 2008-10-05
Thank you for your help
The wireless network does not work and I got a message that my
adaptor is restricted from the manufacturer.

Regards

---

### Post by pytheas22 on 2008-10-05
Please post the output of the following commands so that we can figure out why it's not working:
```

lsmod | grep ath
lshw -C Network
lspci -nn | grep -i atheros
dmesg | grep ath
sudo iwlist scan
```

Also, if you go to System>Administration>Hardware Drivers, you should see a box that you can check to enable the use of your wireless card.  Make sure it is checked.  Does the wireless work then?

---

