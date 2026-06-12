---
title: "Network Manager cannot connect to Wifi"
date: 2012-04-29
forum: Hardware
---

### Post by bruno.braga on 2012-04-29
Guys,

I've tons of threads about this topic, but sadly, none has answered the question. There are some hotspots I could never connect, because of this error, but I never really bother digging too much into it. Recently, after adding another wifi router at home, I can't connect my machine if running Ubuntu (macosX is just fine). Any other device (iPhone, etc) also connects without any problems. 

The issue, from the network-manager logs in syslog shows repeatedly the same over and over:

```

Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> Activation (wlan0) starting connection 'myeesid'
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> Activation (wlan0/wireless): access point 'myeesid' has security, but secrets are required.
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 29 16:29:54 mac17 NetworkManager[12566]: <warn> No agents were available for this request.
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Apr 29 16:29:54 mac17 NetworkManager[12566]: <warn> Activation (wlan0) failed for access point (myeesid)
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> Marking connection 'myeesid' invalid.
Apr 29 16:29:54 mac17 NetworkManager[12566]: <warn> Activation (wlan0) failed.
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 29 16:29:54 mac17 NetworkManager[12566]: <info> (wlan0): deactivating device (reason 'none') [0]


```

Anyone knows what could this be? I read about issues with network-manager, with linux kernel, and that those were fixed, but here I am...

I tried so many different approaches that I am even a bit lost right now... Has anyone really solved this thing? 

My specs:
```

$ uname -a
Linux mac17 3.2.0-20-generic #33-Ubuntu SMP Tue Mar 27 16:42:26 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

$ lshw
...
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:20 ioport:6000(size=4096) memory:bba00000-bbafffff ioport:90200000(size=2097152)
           *-network
                description: Wireless interface
                product: BCM43224 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 10:9a:dd:ae:e1:6a
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-20-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:17 memory:bba00000-bba03fff
...


$ hwinfo --network
...
45: None 00.0: 1070a WLAN
  [Created at net.124]
  Unique ID: AYEt.QXn1l67RSa1
  Parent ID: y9sn.R3TanyWUNhC
  SysFS ID: /class/net/wlan0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  Hardware Class: network interface
  Model: "WLAN network interface"
  Driver: "brcmsmac"
  Driver Modules: "brcmsmac"
  Device File: wlan0
  HW Address: 10:9a:dd:ae:e1:6a
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (Network controller)


```

I haven't downgraded the kernel, neither disabled the network-manager, because I want to use it. If there is no other way...

Thanks in advance,

---

