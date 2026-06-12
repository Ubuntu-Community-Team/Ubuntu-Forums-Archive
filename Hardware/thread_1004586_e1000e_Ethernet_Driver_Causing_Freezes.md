---
title: "e1000e Ethernet Driver Causing Freezes"
date: 2008-12-07
forum: Hardware
---

### Post by BeigeGenius on 2008-12-07
System freezes seem to only occur when the laptop is connected via Ethernet.
Freezes tend to occur when connected to the internet via ethernet and then changing power source shortly before or during a file download (ubuntu iso from kent mirror), watching a LAN TV stream using VLC or transfering files accross the network. When tested using the wireless device no freezes occurred.

Freezes did not occur whilst using the e1000 driver in 7.10

Ethernet Device information:

Intel Corporation 82573L Gigabit Ethernet Controller

59: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.fDJwwtOIb5B
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "e1000e"
  Driver Modules: "e1000e"
  Device File: eth0
  HW Address: 00:15:b7:aa:72:5e
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (Ethernet controller)

syslog extract before crash, thought to be just the log of changing power source and not the actual reason for the crash.

Dec 7 15:11:37 JustAComp kernel: [ 65.948734] CPU0 attaching NULL sched-domain.
Dec 7 15:11:37 JustAComp kernel: [ 65.948747] CPU1 attaching NULL sched-domain.
Dec 7 15:11:37 JustAComp kernel: [ 65.960135] CPU0 attaching sched-domain:
Dec 7 15:11:37 JustAComp kernel: [ 65.960143] domain 0: span 0-1 level MC
Dec 7 15:11:37 JustAComp kernel: [ 65.960146] groups: 0 1
Dec 7 15:11:37 JustAComp kernel: [ 65.960152] CPU1 attaching sched-domain:
Dec 7 15:11:37 JustAComp kernel: [ 65.960155] domain 0: span 0-1 level MC
Dec 7 15:11:37 JustAComp kernel: [ 65.960157] groups: 1 0
Dec 7 15:12:28 JustAComp kernel: [ 117.542150] CPU0 attaching NULL sched-domain.
Dec 7 15:12:28 JustAComp kernel: [ 117.542168] CPU1 attaching NULL sched-domain.
Dec 7 15:12:29 JustAComp kernel: [ 117.569134] CPU0 attaching sched-domain:
Dec 7 15:12:29 JustAComp kernel: [ 117.569146] domain 0: span 0-1 level MC
Dec 7 15:12:29 JustAComp kernel: [ 117.569152] groups: 0 1
Dec 7 15:12:29 JustAComp kernel: [ 117.569161] domain 1: span 0-1 level CPU
Dec 7 15:12:29 JustAComp kernel: [ 117.569166] groups: 0-1
Dec 7 15:12:29 JustAComp kernel: [ 117.569175] CPU1 attaching sched-domain:
Dec 7 15:12:29 JustAComp kernel: [ 117.569179] domain 0: span 0-1 level MC
Dec 7 15:12:29 JustAComp kernel: [ 117.569184] groups: 1 0
Dec 7 15:12:29 JustAComp kernel: [ 117.569191] domain 1: span 0-1 level CPU
Dec 7 15:12:29 JustAComp kernel: [ 117.569196] groups: 0-1

Would it be possible to revert back to driver e1000 and does using the new driver e1000e risk damaging my ethernet card similar to the bug experienced by users during intrepid alpha?

---

### Post by BeigeGenius on 2008-12-09
Bump

Would it be possible to use the previous e1000 driver used in 7.10 as the latest seems to cause freezes when changing power source?

---

