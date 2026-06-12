---
title: "blutooth problem 12.04"
date: 2012-07-11
forum: Hardware
---

### Post by sree88 on 2012-07-11
ubuntu 12.04 bluetooth problem wifi is working

$lsmod | grep
bluetooth 180104 14 bnep,rfcomm,btusb,fwload



$hciconfig
hci0:  Type:BR/EDR Bus:USB
BD Address:00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
DOWN
RX bytes:0 acl:0 sco:0 events:0 errors:0
TX bytes:6 acl:0 sco:0 commands:2 errors:0


$hciconfig hci0 up
Can't init device hci0: onnection timed out(110)


 $dmesg  | grep blue
 $

$bluetoothd
$

laptop : sony vaio vpceh18
linux ubuntu 3.2.0-26-generic

---

