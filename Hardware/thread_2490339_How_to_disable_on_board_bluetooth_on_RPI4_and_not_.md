---
title: "How to disable on board bluetooth on RPI4 and not the bluetooth usb"
date: 2023-08-30
forum: Hardware
---

### Post by shufflekees on 2023-08-30
Hello,
I searched the internet for a solution, but couldn't find a suitable one. I blocked the UART (ttyAMA0) and tried other suggestions, both the on board and the usb BT are disabled then. How can I disable the on board BT and have the usb BT enabled. I use a metal box and the bluetooth is weak.
Thanks in advance
Kees

---

### Post by #&amp;thj^% on 2023-08-30
While using the RPI4, can you show us this please:
```
less /boot/overlays/README
```
I need to see that file
and also show:
```
rfkill list all
```

---

### Post by shufflekees on 2023-09-02
Hello,
kees@kees-desktop:~$ sudo su
[sudo] password for kees: 
root@kees-desktop:/home/kees# less /boot/overlays/README
/boot/overlays/README: No such file or directory
root@kees-desktop:/home/kees# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci1: Bluetooth
    Soft blocked: no
    Hard blocked: no

When I (soft) block hci1 hci0 doesnt  work eather.

---

