---
title: "e1000e / Intel 82579LM issue"
date: 2024-02-09
forum: Hardware
---

### Post by slc66 on 2024-02-09
Hi all,

I have an issue with an 82579LM Gigabit Network on Ubuntu 23.10 : No network

The computer is an Dell OptiPlex 7010 

Any idea ?

```

uname -a
Linux desktop-slc 6.5.0-17-generic #17-Ubuntu SMP PREEMPT_DYNAMIC Thu Jan 11 14:01:59 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

```

```

sudo lshw -class net
  *-network NON-RÉCLAMÉ     
       description: Ethernet controller
       produit: 82579LM Gigabit Network Connection (Lewisville)
       fabricant: Intel Corporation
       identifiant matériel: 19
       information bus: pci@0000:00:19.0
       version: 04
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm msi cap_list
       configuration : latency=0
       ressources : mémoire:f7c00000-f7c1ffff mémoire:f7c39000-f7c39fff portE/S:f080(taille=32)
  *-network
       description: Interface réseau sans fil
       identifiant matériel: 4
       information bus: usb@1:1.3
       nom logique: wlx60e3271fd17c
       numéro de série: 60:e3:27:1f:d1:7c
       fonctionnalités: ethernet physical wireless
       configuration : broadcast=yes driver=rtl8xxxu driverversion=6.5.0-17-generic firmware=N/A ip=192.168.0.9 link=yes multicast=yes wireless=IEEE 802.11

```

```

sudo journalctl --boot --dmesg -g e1000e
févr. 09 17:43:59 desktop-slc kernel: e1000e: Intel(R) PRO/1000 Network Driver
févr. 09 17:43:59 desktop-slc kernel: e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
févr. 09 17:43:59 desktop-slc kernel: e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
févr. 09 17:43:59 desktop-slc kernel: e1000e: probe of 0000:00:19.0 failed with error -3

```

```

sudo dmesg | grep 0000:00:19.0
[    0.183591] pci 0000:00:19.0: [8086:1502] type 00 class 0x020000
[    0.183605] pci 0000:00:19.0: reg 0x10: [mem 0xf7c00000-0xf7c1ffff]
[    0.183614] pci 0000:00:19.0: reg 0x14: [mem 0xf7c39000-0xf7c39fff]
[    0.183622] pci 0000:00:19.0: reg 0x18: [io  0xf080-0xf09f]
[    0.183680] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.598818] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.620355] e1000e: probe of 0000:00:19.0 failed with error -3
[  474.936841] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[  475.954889] e1000e: probe of 0000:00:19.0 failed with error -3
[ 1225.981307] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[ 1227.002905] e1000e: probe of 0000:00:19.0 failed with error -3

```

---

### Post by SeijiSensei on 2024-02-09
Does this problem occur on 22.04LTS? You can boot from an installation medium and choose "Try Ubuntu" to see.

---

### Post by slc66 on 2024-02-19
Hi, there,
very sorry for this very late return. I need to change my notification email address.

Yes, this card has always worked very well.

It's only with Ubuntu 23.10 installed that it doesn't work anymore. The LiveUSB 23.10 allowed the installation.

I don't understand this.

---

### Post by Yellow Pasque on 2024-02-19
I see some reports that igb module is interfering and/or that reinserting e1000e moduie might work, so you can try:
```
sudo modprobe -v -r igb e1000e
sudo modprobe -v e1000e
```

---

### Post by slc66 on 2024-02-21
it doesn't work any better

> 
[761255.300655] e1000e: Intel(R) PRO/1000 Network Driver
[761255.300659] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[761255.300865] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[761256.318569] e1000e: probe of 0000:00:19.0 failed with error -3


---

### Post by mb4e on 2024-08-17
Same problem here, solved by reseating the CMOS battery.

---

### Post by cma42 on 2024-10-09
Just adding a breadcrumb here for future troubleshooters:  I had this issue too, it was resolved by issuing a "reboot" command from the command line.  Using reboot from the menu may have worked as well.  If you use "shutdown", the interface does not come back up.  It seems to have something to do with power management possibly in the firmware.  It seems to be OS-independent--I found posts from Windows users having this issue, and I had this problem on the same computer over a year ago running Ubuntu 20.04 (then it started working after I took it to my office to troubleshoot it further, but I never figured out why).  I updated it with a fresh install to 24.04 a few months ago and it's been running almost daily first on 20.04 and now on 24.04 without further issue until today.  The location's power was out over the weekend for several hours, so maybe that had something to do with it reverting to being "unclaimed".

---

### Post by slc66 on 2024-10-11
Please note:

If I reboot the PC, the card is recognized and gets an IP address.

The problem persists with a cold boot.

---

