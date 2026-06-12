---
title: "Problem with wireless on HP dv6500"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by karl_kashofer on 2008-03-04
Hi !

I have a problem with ndiswrapper and/or the windows driver for my wlan card. I compiled ndiswrapper 1.52 and downloaded sp34152.exe which seems to be the right driver for this card:
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
```
according to this site: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-dfa35a08da26002d337e79d528efb0c4ed5a127f](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-dfa35a08da26002d337e79d528efb0c4ed5a127f)

This enables wlan but its very flaky. Sometimes it does not work at all, sometimes it works but you have to connect twice to get it working from knetworkmanager and sometimes it works fine.

The main problem seems to be that sometimes the ndiswrapper fails to load the windows driver for the card. This is my syslog:
```

Mar  3 21:58:09 beka-laptop kernel: [   41.134758] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Mar  3 21:58:09 beka-laptop kernel: [   41.234822] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
Mar  3 21:58:09 beka-laptop kernel: [   41.236528] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Mar  3 21:58:09 beka-laptop kernel: [   41.237844] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 16
Mar  3 21:58:09 beka-laptop kernel: [   41.237855] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 16 (level, low) -> IRQ 16
Mar  3 21:58:09 beka-laptop kernel: [   41.237897] PCI: Setting latency timer of device 0000:03:00.0 to 64
Mar  3 21:58:09 beka-laptop kernel: [   41.245031] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138D, count: 1, return_address: ffffffff88aab48e
Mar  3 21:58:09 beka-laptop kernel: [   41.245148] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x110
Mar  3 21:58:09 beka-laptop kernel: [   41.245243] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
Mar  3 21:58:09 beka-laptop kernel: [   41.245247] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
Mar  3 21:58:09 beka-laptop kernel: [   41.245256] ndiswrapper (mp_halt:259): device ffff810071aab780 is not initialized - not halting
Mar  3 21:58:09 beka-laptop kernel: [   41.245263] ndiswrapper: device eth%%d removed
Mar  3 21:58:09 beka-laptop kernel: [   41.245272] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Mar  3 21:58:09 beka-laptop kernel: [   41.245281] ndiswrapper: probe of 0000:03:00.0 failed with error -22
Mar  3 21:58:09 beka-laptop kernel: [   41.247588] usbcore: registered new interface driver ndiswrapper

```

If this happens during boot no network interface is created. Additionally its then impossible to unload/load ndiswrapper as sudo modprobe -r ndiswrapper just hangs.

System: 
HP dv6500eu AMD Turion Kubuntu 7.10 64bit

Would anyone know what to do ?
Thanks,
Karl

This is how it looks when it works, nothing changed, just rebooted multiple times:
```

Mar  3 21:59:35 beka-laptop kernel: [   37.512724] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Mar  3 21:59:35 beka-laptop kernel: [   37.614049] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
Mar  3 21:59:35 beka-laptop kernel: [   37.615748] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Mar  3 21:59:35 beka-laptop kernel: [   37.616346] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 16
Mar  3 21:59:35 beka-laptop kernel: [   37.616356] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 16 (level, low) -> IRQ 16
Mar  3 21:59:35 beka-laptop kernel: [   37.616387] PCI: Setting latency timer of device 0000:03:00.0 to 64
Mar  3 21:59:35 beka-laptop kernel: [   37.624374] ndiswrapper: using IRQ 16
Mar  3 21:59:35 beka-laptop kernel: [   37.975617] wlan0: ethernet device 00:1a:73:a3:a6:53 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x5
01, vendor: 'NDIS Network Adapter', 14E4:4312.5.conf
Mar  3 21:59:35 beka-laptop kernel: [   37.975657] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Mar  3 21:59:35 beka-laptop kernel: [   37.977849] usbcore: registered new interface driver ndiswrapper

```

---

