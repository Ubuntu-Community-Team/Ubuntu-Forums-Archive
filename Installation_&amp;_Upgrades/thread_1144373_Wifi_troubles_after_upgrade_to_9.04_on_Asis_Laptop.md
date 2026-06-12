---
title: "Wifi troubles after upgrade to 9.04 on Asis Laptop"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Userbun on 2009-04-30
Hi!

I was using Ubuntu 8.10 on my Asus X80L laptop.
After upgrade I met some stranges with wifi:
1) It looks for the network for a very long time - much more than before.
2) It doesn't work well with it. It means it works well for 70 seconds then 30 seconds net doesn't work, then it works 70 secs again and so on. It's very strange, but I see it clearly with ping and other programs.

I tried to load with previouse kernel 2.6.27-11-generic #42-Ubuntu. Wifi works but video driverls not ok. Xorg eats all process time.

I like ubuntu but this feature doesn't let work with it. Is it possible to solve the problem?

# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:22:15:9e:5c:de
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.74 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:cc:43:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:79:37:0e:d8:04
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


$ uname -a
Linux e-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux


parts from dmesg:
...
[   12.209529] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   12.258766] cfg80211: World regulatory domain updated:
[   12.258770]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.258773]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.258776]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.258779]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.258781]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.258784]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.327966] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.328595] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   12.328606] iTCO_wdt: No card detected
[   12.336143] acpi device:20: registered as cooling_device2
[   12.336392] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1d/input/input7
[   12.339849] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   12.413669] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.933854] ath9k: 0.1
[   12.933907] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.933922] ath9k 0000:02:00.0: setting latency timer to 64
[   13.109274] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.109340] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.358125] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04711/0x0
[   13.371141] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.412342] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   13.451939] Registered led device: ath9k-phy0:radio
[   13.451960] Registered led device: ath9k-phy0:assoc
[   13.451978] Registered led device: ath9k-phy0:tx
[   13.452017] Registered led device: ath9k-phy0:rx
[   13.452567] phy0: Atheros 9280: mem=0xf7e40000, irq=17
[   13.613212] lp: driver loaded but no devices found
[   13.650678] ath_hal: module license 'Proprietary' taints kernel.
[   13.652091] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.678378] wlan: 0.9.4.1
[   13.699528] ath_pci: 0.9.4.1
...
[   28.700804] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.396751] wlan0: direct probe to AP 00:18:b0:ee:af:e0 try 1
[   29.593211] wlan0: direct probe to AP 00:18:b0:ee:af:e0 try 2
[   29.792197] wlan0: direct probe to AP 00:18:b0:ee:af:e0 try 3
[   29.992208] wlan0: direct probe to AP 00:18:b0:ee:af:e0 timed out
[   39.256300] eth0: no IPv6 routers present
[   74.304520] wlan0: direct probe to AP 00:18:b0:ee:af:e0 try 1
[   74.314901] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[   74.512194] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[   74.712139] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[   74.916054] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[   85.017581] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[   85.026267] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[   85.225129] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[   85.425303] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[   85.626655] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  101.576392] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  101.585300] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  101.784213] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  101.984204] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  102.184206] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  112.480623] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  112.489518] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  112.689752] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  112.888255] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  113.088259] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  123.168623] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  123.177539] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  123.376105] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  123.576171] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  123.776235] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  127.691144] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  127.888218] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  128.089631] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  128.288069] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  298.935755] ath_pci: driver unloaded
[  299.528966] wlan: driver unloaded
[  299.733836] ath_hal: driver unloaded
[  326.600531] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  326.609473] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  326.808219] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  327.008241] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  327.208244] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  343.224670] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  343.420115] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  343.621294] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  343.821197] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  353.928513] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  353.937312] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  354.140045] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  354.340211] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  354.540211] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  370.549456] wlan0: authenticate with AP 00:18:b0:ee:af:e1
[  370.558453] wlan0: authenticate with AP 00:18:b0:ee:af:e1
[  370.757040] wlan0: authenticate with AP 00:18:b0:ee:af:e1
[  370.957208] wlan0: authenticate with AP 00:18:b0:ee:af:e1
[  371.164052] wlan0: authentication with AP 00:18:b0:ee:af:e1 timed out
[  385.699882] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  385.896068] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  386.096225] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  386.296219] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  395.100565] wlan0: authenticate with AP 00:18:b0:ee:af:e1
[  395.109471] wlan0: authenticate with AP 00:18:b0:ee:af:e1
[  395.309055] wlan0: authenticate with AP 00:18:b0:ee:af:e1
[  395.508055] wlan0: authenticate with AP 00:18:b0:ee:af:e1
[  395.709556] wlan0: authentication with AP 00:18:b0:ee:af:e1 timed out
[  406.012550] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  406.021539] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  406.221050] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  406.421205] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  406.630363] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  416.929411] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  416.938226] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  417.136213] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  417.336083] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  417.536130] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  427.652473] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  427.661112] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  427.861230] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  428.061199] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  428.261192] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  438.584566] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  438.593391] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  438.792040] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  438.992218] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  439.192199] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out
[  455.199647] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 1
[  455.396045] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 2
[  455.596039] wlan0: direct probe to AP 00:18:b0:ee:af:e1 try 3
[  455.800044] wlan0: direct probe to AP 00:18:b0:ee:af:e1 timed out



Thanks in advance!

---

### Post by mlissner on 2009-11-13
Ditto here on 9.10. Atheros AR5211.

---

