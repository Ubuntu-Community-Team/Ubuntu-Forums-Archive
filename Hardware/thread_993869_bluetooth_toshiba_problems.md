---
title: "bluetooth toshiba problems"
date: 2008-11-26
forum: Hardware
---

### Post by vinsax on 2008-11-26
hello everybody,
i'm a brand new ubuntu user and on my toshiba u200 laptop I'm unable to let the bluetooth work properly. It seems to me that the system recognize it, but there is no bluetooth analyzer and utils working, as you can see from the following terminal output:

vincenzo@kazzavu:~$ sudo /etc/init.d/bluetooth start
[sudo] password for vincenzo: 
 * Starting bluetooth                                                    [ OK ] 
vincenzo@kazzavu:~$ sudo buez-utils
sudo: buez-utils: command not found
vincenzo@kazzavu:~$ dmesg |grep Bluetooth
[   23.127870] Bluetooth: Core ver 2.13
[   23.128572] Bluetooth: HCI device and connection manager initialized
[   23.128582] Bluetooth: HCI socket layer initialized
[   23.152842] Bluetooth: L2CAP ver 2.11
[   23.152851] Bluetooth: L2CAP socket layer initialized
[   23.197184] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.197193] Bluetooth: BNEP filters: protocol multicast
[   23.264555] Bluetooth: SCO (Voice Link) ver 0.6
[   23.264564] Bluetooth: SCO socket layer initialized
[   23.374721] Bluetooth: RFCOMM socket layer initialized
[   23.375012] Bluetooth: RFCOMM TTY layer initialized
[   23.375018] Bluetooth: RFCOMM ver 1.10

for sure I'm doing something wrong, so is anybody helping me? many thanks in advance, vincenzo.

---

### Post by binbash on 2008-11-26
it is bluez-utils not buez

---

### Post by vinsax on 2008-11-26
oh sorry, anyway it dosn't work the same:

vincenzo@kazzavu:~$ sudo bluez-utils
[sudo] password for vincenzo: 
sudo: bluez-utils: command not found
vincenzo@kazzavu:~$ 

any hint?

---

