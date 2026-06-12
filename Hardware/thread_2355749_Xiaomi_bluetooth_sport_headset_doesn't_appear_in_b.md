---
title: "Xiaomi bluetooth sport headset doesn't appear in bluetooth device list"
date: 2017-03-16
forum: Hardware
---

### Post by torq072 on 2017-03-16
I'm trying to connect Xiaomi bluetooth sport headset to my Laptop( ASUS K56CM) on Ubuntu 16.04, but my laptop even doesn't see it in available bluetooth devices

What i've already tried to solve this issue:

-I had install blueman, but nothing changed my headset is still not recognizing.
-I've tried solution from this [thread]("http://askubuntu.com/questions/775523/after-updating-to-16-04-bluetooth-audio-a2dp-mode-stopped-working") , but it didn't help me either.

Here is output of 
```
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
```
```
Linux torq07-K56CM 4.4.0-66-generic #87-Ubuntu SMP Fri Mar 3 15:29:05 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave AR9485 Wireless Network Adapter [1a3b:2c97]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
--
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:1587]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 13d3:5165 IMC Networks 
Bus 001 Device 003: ID 13d3:3362 IMC Networks Atheros AR3012 Bluetooth 4.0 Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    2.331249] usb 1-1.1: Product: Bluetooth USB Host Controller
[   19.382559] Bluetooth: Core ver 2.21
[   19.382585] Bluetooth: HCI device and connection manager initialized
[   19.382590] Bluetooth: HCI socket layer initialized
[   19.382594] Bluetooth: L2CAP socket layer initialized
[   19.382603] Bluetooth: SCO socket layer initialized
[   34.159760] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.159763] Bluetooth: BNEP filters: protocol multicast
[   34.159768] Bluetooth: BNEP socket layer initialized
[  103.674922] Bluetooth: RFCOMM TTY layer initialized
[  103.674932] Bluetooth: RFCOMM socket layer initialized
[  103.674940] Bluetooth: RFCOMM ver 1.11
[  485.208416] Bluetooth: hci0 urb ffff8800c3c85840 failed to resubmit (2)
[  641.984833] Bluetooth: hci0 urb ffff880073303d80 failed to resubmit (2)
[    0.265863] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    2.600196] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
bluetooth             520192  38 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel

```

Hope you guys can help me to connect this thing to my laptop.

P.S: Strange thing is that another  Bluetooth Xiaomi Speaker MDZ-15 DA is connecting from the box without any problems.

---

### Post by jeremy31 on 2017-03-16
You may have to do a complete shutdown and a cold boot and try again.  I am not sure what causes that strange error failed to resubmit

---

### Post by gdesilva on 2017-03-17
Just check that you have made your Xiaomi visible in Xiaomi -> Settings -> Bluetooth (ie. the phone bluetooth settings)

---

### Post by torq072 on 2017-03-18
> **gdesilva said:**
> Just check that you have made your Xiaomi visible in Xiaomi -> Settings -> Bluetooth (ie. the phone bluetooth settings)

How to do this? I don't have any interface in Xiaomi bluetooth sport  headset. Beside those headset is connecting to my iphone without any problems, so i think it is visible , but thanks for the idea, i will google it for sure, maybe there is really some sort of settings for this headset.

---

### Post by gdesilva on 2017-03-18
My apologies...I thought it was a Xiaomi handset (phone) - should have paid more attention to your post.

---

