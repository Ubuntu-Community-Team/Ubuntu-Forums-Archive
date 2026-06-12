---
title: "Wifi Card"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by vef on 2005-10-29
I am running Ubuntu 5.10 and it works good but my onboard wifi device don’t work.

My notebook Packard bell easynote g1320 has a agere/lucent card.
I try to wrap the driver with ndiswrapper several times but I get the follow messege:

```
$ndiswrapper -i wlagsall.inf
Installing wlagsall
no vendor

$ndiswrapper -l
Installed ndis drivers:
wlagsall        invalid driver!
```

I did a google search but didn’t found a solution. 

Specifications of my notebook:
```
$lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5830 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5838
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5835
0000:02:04.0 Network controller: Lucent Microelectronics: Unknown device ab34
0000:02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

How can help to get this wifi card working in ubuntu linux

---

