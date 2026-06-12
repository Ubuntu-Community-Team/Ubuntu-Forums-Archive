---
title: "Compaq Presario R3000 Wireless Issue"
date: 2009-05-17
forum: Hardware
---

### Post by twst123 on 2009-05-17
I am new to Ubuntu and have version 9.04 installed on an old Compaq Presario R3000.  How can I enable the wireless card? 

I read through many posts on this issue, but none were able to fix my problem.  Any help appreciated.

```

*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:04:47:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:59:a3:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 72:13:e6:31:35:04
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by krozar on 2009-06-11
I'm also having trouble getting wireless to work on my R3120 laptop since upgrading to 9.04.  Worked fine in 8.10.

---

### Post by DannyD.Fl on 2009-06-19
Please help! I'm also having the same problem....

---

### Post by DannyD.Fl on 2009-06-19
All right I got my light on (have not checked a wireless connection yet, but this is the first time the light is ever on, so here goes nothing....

Run System, Administratio/ Update Manager

Do all the updates that are recomended. The computer will restart.

Then go to system/administration/hardware drivers and activate the broadcom and the video card software.

restart the system and wireless shoud work

---

### Post by Abdul99 on 2009-07-19
[DannyD.Fl]("http://ubuntuforums.org/member.php?u=859221") I did what you said but my system is up-to-date and I still cannot get the wireless work. I have just converted to Ubuntu from Vista, first time it worked fine but when I reformatted my laptop with ubuntu again, it stopped working. Also, the hardware drivers section doesnt show any proprietary hardwares, it says 'No proprietary hardwares....'. Can someone please help???

---

