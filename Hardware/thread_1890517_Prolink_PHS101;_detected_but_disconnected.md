---
title: "Prolink PHS101; detected but disconnected"
date: 2011-12-03
forum: Hardware
---

### Post by dirmansyah on 2011-12-03
Halo,
 

 My modem, Prolink PHS101, is detected by Xubuntu an Lubuntu. However, it is never connected to the network.
 Both OS keep on popping-up message saying that the device is disconnected.
 

 I have tried making new Mobile Broadband connection via Network Connections.
 The device was identified as "PROLINK WCDMA Technology MSM" (in the dropdown menu, under the label "Create a connection for this mobile broadband device").
 I use that one.
 

 I have tried 2 SIM cards. Both are failed on Prolink PHS101. However, on Nokia-E63 as the modem,  both SIM cards have been successfully connected to the network (internet)
 

 

 This is the result for the command “lsusb”.
 

 dl@dl-a1215p:~$ lsusb
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 002: ID 13d3:5702 IMC Networks
 Bus 001 Device 004: ID 19d2:0151 ONDA Communication S.p.A.
 dl@dl-a1215p:~$
 

 [additional info1]:
I have received an email from Prolink Support (support@fida.com). Mr.Tan (Technical Support) has kindly attached the procedure of setting the connection on Ubuntu. However, it was similar to what I had done without success.

----------

  [add2] 2011-12-05, 23.30 TZ:+7.
Printed on modem box:
P/N: HPA-PHS101M
Is there any user here using the same modem?
Oops, 63 views and no reply, so far.  zzz zzz zzz :)

----------

[add3] 2011-12-08, 04.50 TZ: +7
73 views, zero reply.
Some one has reported this as a bug.
The site url is: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/874987](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/874987)
with page-title: "PHS101 USB GSM HSDPA can't connect on ubuntu 11.10"

----------



 Thank you.
 DL
 .

---

### Post by dirmansyah on 2011-12-07
Some one has reported this as a bug.
The site url is: [https://bugs.launchpad.net/ubuntu/+s...er/+bug/874987]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/874987")
with page-title: "PHS101 USB GSM HSDPA can't connect on ubuntu 11.10"

---

