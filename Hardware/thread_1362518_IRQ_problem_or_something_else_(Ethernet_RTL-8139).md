---
title: "IRQ problem or something else? (Ethernet RTL-8139)"
date: 2009-12-23
forum: Hardware
---

### Post by neur0 on 2009-12-23
Sometimes (completely at random as it seems) my network card stops working.
/etc/init.d/networking restart doesn't work, only reboot gets things back to normal.
Relevant Interrupts line looks like this:
```
17:     408275          0   IO-APIC-fasteoi   uhci_hcd:usb3, eth1
```
Relevant lshw is:
```
*-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 10
       serial: 00:30:84:9d:f5:ed
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.191.54 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:17 ioport:b800(size=256) memory:dbeff800-dbeff8ff

```

Colleagues working on the same machine on dual-booted windows aren't complaining so I believe its a software issue.
IP address is statically set.
 
This happens rarely (say once in 3 days on average) so I will be doing more tests when there is a problem.

Anyone have any ideas?

EDIT: This Ubuntu is 9.10

---

### Post by neur0 on 2010-03-19
I have an update:
I replaced the card (same model), but the problem is still there.
When it happens, I can ping my own address and the loopback address, but can't ping my default gateway.

I tried reloading the driver module (8139too) but after that, the interface is gone and networking restart or ifup doesn't help.

The problem always goes away after a restart, but comes back later.

Is there any way to bring the interface up after reloading the driver?

---

### Post by Dayofswords on 2010-03-19
[http://ubuntuforums.org/showthread.php?t=607953](http://ubuntuforums.org/showthread.php?t=607953)
[https://bugs.launchpad.net/ubuntu/+bug/162800](https://bugs.launchpad.net/ubuntu/+bug/162800)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156496](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156496)

i found these after a search, first remained unsolved

it does not look good..

---

