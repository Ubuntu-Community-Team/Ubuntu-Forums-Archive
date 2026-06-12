---
title: "Iriver IFP-780 not showing up on file tree"
date: 2022-02-21
forum: Hardware
---

### Post by Joe_Linux on 2022-02-21
I have a Iriver IFP-780 audio codec player (yes I know it's old). It does not show up on the file tree (mount). The firmware version on the device is 1.25
Here is the result of lsusb 
```
joe@joe-X555LAB:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 13d3:3501 IMC Networks 
Bus 001 Device 002: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
joe@joe-X555LAB:~$ 
```
Thankyou

---

### Post by Holger_Gehrke on 2022-02-21
The player isn't on the list. The only one of the devices on your list I wasn't sure about is "ID 13d3:3501" and that is bluetooth according to an online USB ID list. The manual for the player I found online says it's one of these old devices that takes an AA battery and needs to be switched on to be visible on the bus. It also mentions using a proprietary piece of software - iRiver Media Manager - to put music on the player and to update it's firmware.

Another thing I saw online was mention of an updated firmware version 1.85 which seems to make the device capable of acting as a storage device.

Holger

---

