---
title: "Bluetooth not recognized - Intel  7620 PCI Wi-Fi/Bluetooth on Toshiba Laptop"
date: 2024-03-02
forum: Hardware
---

### Post by BeachNerd on 2024-03-02
Hi:  I'm relatively new to Ubuntu.  I recently resurrected an old Toshiba Portege R830 by installing Ubuntu (Ubuntu 22.04.4 LTS).  Laptop works great, including dual band Wi-Fi, but Bluetooth capability of the Intel 7260HMW AN PCI card (combined Wi-Fi/Bluetooth) is not detected, i.e. Bluetooth doesn't show up in the hardware profile, even though the 7620 does.  There are no external switches to turn Wi-Fi or Bluetooth on or off.   I know BT works as I tested it in Windows before converting to Ubuntu.   I've done a lot of searching and Bluetooth seem to be a bit of a  problem, especially with the 7620.  I couldn't find any solutions that works for me.  I'm using a USB Bluetooth dongle for now but would prefer to jetison the dongle.  Just wondering if anyone has any suggestions including other PCI cards that would work.  Thanks for any advice.

---

### Post by jeremy31 on 2024-03-02
What shows in results from terminal for ```
lsusb
```
I remember issues trying to find wifi/BT combos that would work in my old Toshibas, likely made 14 years ago

---

### Post by BeachNerd on 2024-03-02
> **jeremy31 said:**
> What shows in results from terminal for ```
lsusb
```


I'll post when the laptop is back up.  I downgraded to Ubuntu 12.x (because I happened to have that bootable disk laying around so I installed it) and the Bluetooth works so, presumably, not a hardware issue.  Currently upgrading back to 22.

---

### Post by BeachNerd on 2024-03-03
> **jeremy31 said:**
> What shows in results from terminal for ```
lsusb
```


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:58f5 Realtek Semiconductor Corp. 2SF001
Bus 001 Device 004: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2024-03-03
You could try resetting the BIOS to defaults and see if the results for lsusb change

---

### Post by BeachNerd on 2024-03-03
I notice the Intel Wi-Fi card doesn't appear in the bios at all - which seems a bit weird  (maybe less weird and more about my lack of understanding how BIOS works) since the WiFi card works (except for Bluetooth

---

### Post by BeachNerd on 2024-03-07
Sadly, resetting the BIOS settings to default doesn't change behavior.

---

