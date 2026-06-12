---
title: "B43 stop working in hardy (Fatal DMA error)"
date: 2008-07-13
forum: Hardware
---

### Post by santiagozky on 2008-07-13
Today for some reason my wireless card stop working. I'm using the b43 driver.

card ( dell inspiron 1501 ):
 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

I'm getting this:

[PHP]
[   42.630239] b43-phy0: Broadcom 4311 WLAN found
[   42.670432] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
[   42.670444] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   42.697220] phy0: Selected rate control algorithm 'simple'
[   43.305360] NET: Registered protocol family 10
[   43.305591] lo: Disabled Privacy Extensions
[   43.306754] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   44.041957] udev: renamed network interface wlan0 to eth0
[   44.220238] loop: module loaded
[   44.292968] lp: driver loaded but no devices found
[   44.553064] Adding 498004k swap on /dev/sda3.  Priority:-1 extents:1 across:498004k
[   45.176587] EXT3 FS on sda2, internal journal
[   45.911130] kjournald starting.  Commit interval 5 seconds
[   45.911472] EXT3 FS on sda4, internal journal
[   45.911476] EXT3-fs: mounted filesystem with ordered data mode.
[   46.711302] ip_tables: (C) 2000-2006 Netfilter Core Team
[   51.180052] No dock devices found.
[   51.574356] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[   51.574391] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xe
[   51.574394] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x10
[   51.574397] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x18
[   54.728701] apm: BIOS not found.
[   56.527919] NET: Registered protocol family 4
[  128.194265] Marking TSC unstable due to: cpufreq changes.
[  128.204413] Time: hpet clocksource has been installed.
[  128.557727] Clocksource tsc unstable (delta = -202072828 ns)
[   67.993546] input: b43-phy0 as /devices/virtual/input/input9
[   68.378442] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   61.915093] b43-phy0 debug: Chip initialized
[   61.915557] b43-phy0 debug: 32-bit DMA initialized
[   61.936562] Registered led device: b43-phy0:tx
[   61.937240] Registered led device: b43-phy0:rx
[   61.937402] Registered led device: b43-phy0:radio
[   61.937435] b43-phy0 debug: Wireless interface started
[   61.974786] b43-phy0: Radio hardware status changed to DISABLED
[   61.975860] b43-phy0 debug: Adding Interface type 2
[   61.976169] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  146.759533] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 19
[   68.702166] [fglrx] GART Table is not in FRAME_BUFFER range 
[   68.702176] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   68.702179] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   68.926231] [fglrx] interrupt source 20008000 successfully enabled
[   68.926239] [fglrx] enable ID = 0x00000004
[   68.926561] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  172.180598] hda-intel: Invalid position buffer, using LPIB read method instead.
[  304.483286] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[  304.483298] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[  304.492994] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[  304.493002] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[  530.547980] b43-phy0: Radio hardware status changed to ENABLED
[  540.246670] NET: Registered protocol family 17
[  541.447388] b43-phy0 debug: Using hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
[  541.459257] eth0: Initial auth_alg=0
[  541.459268] eth0: authenticate with AP 00:1e:c7:3d:ab:e1
[  541.462530] eth0: RX authentication from 00:1e:c7:3d:ab:e1 (alg=0 transaction=2 status=0)
[  541.462538] eth0: authenticated
[  541.462544] eth0: associate with AP 00:1e:c7:3d:ab:e1
[  541.466513] eth0: RX AssocResp from 00:1e:c7:3d:ab:e1 (capab=0x431 status=0 aid=1)
[  541.466520] eth0: associated
[  541.466528] eth0: switched to short barker preamble (BSSID=00:1e:c7:3d:ab:e1)
[  541.466887] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  541.670462] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  541.670481] b43-phy0: Controller RESET (DMA error) ...
[  541.671355] b43-phy0 debug: Wireless interface stopped
[  541.674176] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 2/64
[  541.674740] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[  541.682476] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[  541.690446] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[  541.698431] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[  541.706429] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 2/128
[  541.714430] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[  541.825367] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  543.326462] b43-phy0 debug: Chip initialized
[  543.327244] b43-phy0 debug: 32-bit DMA initialized
[  543.349860] Registered led device: b43-phy0:tx
[  543.350394] Registered led device: b43-phy0:rx
[  543.350701] Registered led device: b43-phy0:radio
[  543.350747] b43-phy0 debug: Wireless interface started
[  543.350755] b43-phy0: Controller restarted
[  547.465635] eth0: No ProbeResp from current AP 00:1e:c7:3d:ab:e1 - assume out of range
[  548.357472] b43-phy0 debug: Disabling hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
[  548.357740] b43-phy0 debug: Using hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
[  548.358877] eth0: Initial auth_alg=0
[  548.358888] eth0: authenticate with AP 00:1e:c7:3d:ab:e1
[  548.557453] eth0: authenticate with AP 00:1e:c7:3d:ab:e1
[  548.757611] eth0: authenticate with AP 00:1e:c7:3d:ab:e1
[  548.957472] eth0: authentication with AP 00:1e:c7:3d:ab:e1 timed out
[  552.400932] eth0: no IPv6 routers present
[  558.372104] b43-phy0 debug: Disabling hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
[  568.437640] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[  568.437652] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[  568.447674] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[  568.447682] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[  641.405946] b43-phy0: Radio hardware status changed to DISABLED
[  641.505859] b43-phy0: Radio turned on by software
[  641.505873] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[  650.802915] b43-phy0: Radio hardware status changed to ENABLED
[  663.801176] b43-phy0: Radio hardware status changed to DISABLED
[  664.501074] b43-phy0: Radio turned on by software
[  664.501087] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[  668.800528] b43-phy0: Radio hardware status changed to ENABLED
[  697.467077] b43-phy0 debug: Using hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
[  697.467248] eth0: Initial auth_alg=0
[  697.467255] eth0: authenticate with AP 00:1e:c7:3d:ab:e1
[  697.667090] eth0: authenticate with AP 00:1e:c7:3d:ab:e1
[  697.867029] eth0: authenticate with AP 00:1e:c7:3d:ab:e1
[  698.067003] eth0: authentication with AP 00:1e:c7:3d:ab:e1 timed out
[  829.875139] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[  829.875151] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[  829.884939] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[  829.884946] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[  897.576652] b44: eth1: Link is up at 100 Mbps, full duplex.
[  897.576663] b44: eth1: Flow control is off for TX and off for RX.
[  897.577796] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  908.238973] eth1: no IPv6 routers present
[  936.841570] APIC error on CPU0: 00(40)
[  952.308233] b43-phy0 debug: Disabling hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
[  952.308246] b43-phy0 debug: Removing Interface type 2
[  952.368531] b43-phy0 debug: Wireless interface stopped
[  952.369131] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 0/64
[  952.448213] b43-phy0 ERROR: DMA RX reset timed out
[  952.448291] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[  952.456208] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[  952.464190] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[  952.472203] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[  952.480200] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 128/128
[  952.644170] b43-phy0 ERROR: DMA TX reset timed out
[  952.644271] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[/PHP]

It is wierd because if I try to unload the b43 module one time I get a segmentation fault and if I try again nothings happens and I have to do ctrl+c to get the prompt back.

Im using 2.6.24-19-generic for 32 bits.

I have already tried to change the firmware, which I got from  [http://omattos.com/broadcom/](http://omattos.com/broadcom/)

any ideas of what could be wrong?

---

### Post by Aziza Tullia on 2008-10-17
so, did you ever figure out the problem that you posed in this post?

well, check this out:

i ALSO have a Dell Inspiron 1501, and I am ALSO working in Hardy. 

Since I have updated my system (didn't do a clean install to Ubuntu 8.04), i have been unable to connect to any wireless networks. 

Here's the kernal log since boot until the most obvious error occurs:

```

Oct 17 18:51:16 jessjuju kernel: [  125.340850] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
Oct 17 18:51:16 jessjuju kernel: [  125.354966] Bluetooth: Core ver 2.11
Oct 17 18:51:16 jessjuju kernel: [  125.356141] NET: Registered protocol family 31
Oct 17 18:51:16 jessjuju kernel: [  125.356149] Bluetooth: HCI device and connection manager initialized
Oct 17 18:51:16 jessjuju kernel: [  125.356158] Bluetooth: HCI socket layer initialized
Oct 17 18:51:16 jessjuju kernel: [  125.465657] Bluetooth: L2CAP ver 2.9
Oct 17 18:51:16 jessjuju kernel: [  125.465667] Bluetooth: L2CAP socket layer initialized
Oct 17 18:51:16 jessjuju kernel: [  125.646100] Bluetooth: RFCOMM socket layer initialized
Oct 17 18:51:16 jessjuju kernel: [  125.646132] Bluetooth: RFCOMM TTY layer initialized
Oct 17 18:51:16 jessjuju kernel: [  125.646137] Bluetooth: RFCOMM ver 1.8
Oct 17 18:51:17 jessjuju kernel: [   57.162227] b43-phy0 debug: Chip initialized
Oct 17 18:51:17 jessjuju kernel: [   57.162698] b43-phy0 debug: 32-bit DMA initialized
Oct 17 18:51:17 jessjuju kernel: [   57.182231] Registered led device: b43-phy0:tx
Oct 17 18:51:17 jessjuju kernel: [   57.182251] Registered led device: b43-phy0:rx
Oct 17 18:51:17 jessjuju kernel: [   57.182269] Registered led device: b43-phy0:radio
Oct 17 18:51:17 jessjuju kernel: [   57.182301] b43-phy0 debug: Wireless interface started
Oct 17 18:51:17 jessjuju kernel: [   57.182306] b43-phy0 debug: Adding Interface type 2
Oct 17 18:51:17 jessjuju kernel: [   57.184158] ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct 17 18:51:18 jessjuju kernel: [  130.555104] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 19
Oct 17 18:51:20 jessjuju kernel: [   59.539264] [fglrx] GART Table is not in FRAME_BUFFER range 
Oct 17 18:51:20 jessjuju kernel: [   59.539276] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Oct 17 18:51:20 jessjuju kernel: [   59.539279] [fglrx] Reserve Block - 1 offset =  0X7ff5000 length = 0Xb000
Oct 17 18:51:21 jessjuju kernel: [   59.734803] [fglrx] interrupt source 20008000 successfully enabled
Oct 17 18:51:21 jessjuju kernel: [   59.734810] [fglrx] enable ID = 0x00000004
Oct 17 18:51:21 jessjuju kernel: [   59.735272] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Oct 17 18:51:30 jessjuju kernel: [   64.834013] hda-intel: Invalid position buffer, using LPIB read method instead.
Oct 17 18:52:22 jessjuju kernel: [  221.854379] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
Oct 17 18:52:22 jessjuju kernel: [  221.854399] b43-phy0: Controller RESET (DMA error) ...
Oct 17 18:52:22 jessjuju kernel: [  221.855387] b43-phy0 debug: Wireless interface stopped
Oct 17 18:52:22 jessjuju kernel: [  221.855620] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 2/64
Oct 17 18:52:22 jessjuju kernel: [  221.855702] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
Oct 17 18:52:22 jessjuju kernel: [  221.862363] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
Oct 17 18:52:22 jessjuju kernel: [  221.870384] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
Oct 17 18:52:22 jessjuju kernel: [  221.878341] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
Oct 17 18:52:22 jessjuju kernel: [  221.886340] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 2/128
Oct 17 18:52:22 jessjuju kernel: [  221.894348] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
Oct 17 18:52:22 jessjuju kernel: [  222.005290] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
Oct 17 18:52:23 jessjuju kernel: [   99.570236] b43-phy0 debug: Chip initialized
Oct 17 18:52:23 jessjuju kernel: [   99.570733] b43-phy0 debug: 32-bit DMA initialized
Oct 17 18:52:23 jessjuju kernel: [   99.593062] Registered led device: b43-phy0:tx
Oct 17 18:52:23 jessjuju kernel: [   99.593385] Registered led device: b43-phy0:rx
Oct 17 18:52:23 jessjuju kernel: [   99.593606] Registered led device: b43-phy0:radio
Oct 17 18:52:23 jessjuju kernel: [   99.593639] b43-phy0 debug: Wireless interface started
Oct 17 18:52:23 jessjuju kernel: [   99.593643] b43-phy0: Controller restarted
Oct 17 18:53:15 jessjuju kernel: [  296.121885] NET: Registered protocol family 17
Oct 17 18:59:06 jessjuju kernel: [  698.003918] b44: eth0: Link is up at 100 Mbps, full duplex.
Oct 17 18:59:06 jessjuju kernel: [  698.003928] b44: eth0: Flow control is off for TX and off for RX.
Oct 17 18:59:06 jessjuju kernel: [  698.007463] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 17 18:59:16 jessjuju kernel: [  710.069127] eth0: no IPv6 routers present

```


Have you got any ideas? 
(Any further information available with a simple request :)

Thanks!

p.s. I have not tried the firmware suggested in your post from [http://omattos.com/broadcom/](http://omattos.com/broadcom/)

p.p.s. This is my kernel version: 2.6.24-21-generic

---

