---
title: "Intel 8260 wireless adapter unclaimed on 20.10 groovy kernel 5.8.0-26-generic"
date: 2020-11-10
forum: Hardware
---

### Post by vakulenchuk on 2020-11-10
After updating to groovy, and then the kernel was updated at some point now I have to boot into 5.8.0-25-generic to use my wireless.  Below is the output of lshw -C network on both.
Is this a bug in the latest kernel missing the correct firmware?  Or somehow it cannot claim the interface with the latest firmware?
There seems to have been some work done on the linux-firmware package in the past month [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/diff/?id=346057dbe7c7595748e61b8a5b962e5c7316924b](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/diff/?id=346057dbe7c7595748e61b8a5b962e5c7316924b)
I can't be certain if this is where the issue is though.  Anything else that can be done or checked? 

The firmware seems to be present
```
/lib/firmware$ ll iwlwifi-8*
-rw-r--r-- 1 root root 1745176 Oct 28 13:51 iwlwifi-8000C-13.ucode
-rw-r--r-- 1 root root 2351636 Oct 28 13:51 iwlwifi-8000C-16.ucode
-rw-r--r-- 1 root root 2394060 Oct 28 13:51 iwlwifi-8000C-21.ucode
-rw-r--r-- 1 root root 2120860 Oct 28 13:51 iwlwifi-8000C-22.ucode
-rw-r--r-- 1 root root 2227284 Oct 28 13:51 iwlwifi-8000C-27.ucode
-rw-r--r-- 1 root root 2310116 Oct 28 13:51 iwlwifi-8000C-31.ucode
-rw-r--r-- 1 root root 2448976 Oct 28 13:51 iwlwifi-8000C-34.ucode
**-rw-r--r-- 1 root root 2401100 Oct 28 13:51 iwlwifi-8000C-36.ucode**
-rw-r--r-- 1 root root 2389968 Oct 28 13:51 iwlwifi-8265-21.ucode
-rw-r--r-- 1 root root 1811984 Oct 28 13:51 iwlwifi-8265-22.ucode
-rw-r--r-- 1 root root 2234528 Oct 28 13:51 iwlwifi-8265-27.ucode
-rw-r--r-- 1 root root 2307104 Oct 28 13:51 iwlwifi-8265-31.ucode
-rw-r--r-- 1 root root 2440780 Oct 28 13:51 iwlwifi-8265-34.ucode
-rw-r--r-- 1 root root 2409984 Oct 28 13:51 iwlwifi-8265-36.ucode

```



5.8.0-25-generic
```
$ sudo lshw -C network
  *-network                 
       description: Wireless interface
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 3a
       serial: 00:c2:c6:bc:22:58
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-25-generic firmware=36.79ff3ccf.0 8000C-36.ucode ip=192.168.50.229 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:133 memory:df100000-df101fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: eno1
       version: 21
       serial: b8:ae:ed:ea:91:9e
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:124 memory:df200000-df21ffff
```

5.8.0-26-generic
```
$ sudo lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:df100000-df101fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: eno1
       version: 21
       serial: b8:ae:ed:ea:91:9e
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:126 memory:df200000-df21ffff
```

---

### Post by vakulenchuk on 2020-11-12
I had crossposted this and it was answered here [https://askubuntu.com/questions/1291313/intel-8260-wireless-adapter-unclaimed-on-20-10-groovy-kernel-5-8-0-26-generic#1291822](https://askubuntu.com/questions/1291313/intel-8260-wireless-adapter-unclaimed-on-20-10-groovy-kernel-5-8-0-26-generic#1291822)

---

