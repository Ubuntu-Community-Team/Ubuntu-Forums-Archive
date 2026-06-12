---
title: "madwifi not working after last days upgrade - 8.04.3"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by lkraemer on 2009-09-03
Compaq CQ50-139NR running Ubuntu 8.04.3 LTS using Atheros AR242x. 

My madwifi drivers will not install after the updates from the last
two days.  The module ath_pci does not install.

Here are the error messages and Kernel info.

larry@ubuntu:~$ uname -r
2.6.24-24-generic

larry@ubuntu:~$ uname -a
Linux ubuntu 2.6.24-24-generic #1 SMP Tue Aug 18 17:04:53 UTC 2009 i686 GNU/Linux

larry@ubuntu:~$dmesg tail
[   37.439203] loop: module loaded
[   37.526304] lp: driver loaded but no devices found
[   37.581158] ath_hal: module license 'Proprietary' taints kernel.
[   37.582784] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   37.873986] ath_pci: disagrees about version of symbol _ath_hal_attach
[   37.873991] ath_pci: Unknown symbol _ath_hal_attach
[   37.874097] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[   37.874099] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   37.874523] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[   37.874525] ath_pci: Unknown symbol ath_hal_computetxtime
[   37.874795] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[   37.874797] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   37.874990] ath_pci: Unknown symbol _ath_hal_detach
[   37.875599] ath_pci: Unknown symbol ath_hal_print_decoded_register
[   37.876191] ath_pci: disagrees about version of symbol ath_hal_init_channels
[   37.876192] ath_pci: Unknown symbol ath_hal_init_channels
[   37.876447] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[   37.876449] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[   37.919694] Adding 6658932k swap on /dev/sda4.  Priority:-1 extents:1 across:6658932k
[   38.555242] EXT3 FS on sda3, internal journal
[   39.720578] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.179698] No dock devices found.
[   41.757090] apm: BIOS not found.
[   41.852012] ppdev: user-space parallel port driver
[   42.107757] audit(1251992244.761:2): type=1502 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5145 profile="/usr/sbin/cupsd" namespace="default"
[   43.377151] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   43.377158] vboxdrv: Successfully done.
[   43.377162] vboxdrv: Found 2 processor cores.
[   43.377236] vboxdrv: fAsync=0 offMin=0x3e4 offMax=0x20ac
[   43.377305] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   43.377309] vboxdrv: Successfully loaded version 3.0.4 (interface 0x000e0000).
[   45.152790] r8169: eth0: link down
[   45.290971] Bluetooth: Core ver 2.11
[   45.291286] NET: Registered protocol family 31
[   45.291291] Bluetooth: HCI device and connection manager initialized
[   45.291296] Bluetooth: HCI socket layer initialized
[   45.349157] Bluetooth: L2CAP ver 2.9
[   45.349164] Bluetooth: L2CAP socket layer initialized
[   45.484884] Bluetooth: RFCOMM socket layer initialized
[   45.484900] Bluetooth: RFCOMM TTY layer initialized
[   45.484903] Bluetooth: RFCOMM ver 1.8
[   49.131045] [drm] Initialized drm 1.1.0 20060810
[   49.162560] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 21
[   49.162574] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   49.162681] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   50.246528] set status page addr 0x03f7f000
[   66.070597] NET: Registered protocol family 10
[   66.071023] lo: Disabled Privacy Extensions
[   66.071700] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   75.759011] CPU0 attaching NULL sched-domain.
[   75.759023] CPU1 attaching NULL sched-domain.
[   75.790283] CPU0 attaching sched-domain:
[   75.790292]  domain 0: span 03
[   75.790295]   groups: 01 02
[   75.790301] CPU1 attaching sched-domain:
[   75.790304]  domain 0: span 03
[   75.790307]   groups: 02 01
[   89.889684] usb 7-1: new low speed USB device using uhci_hcd and address 2
[   90.065806] usb 7-1: configuration #1 chosen from 1 choice
[   90.246750] usbcore: registered new interface driver hiddev
[   90.260896] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input8
[   90.297492] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
[   90.297523] usbcore: registered new interface driver usbhid
[   90.297530] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  300.175887] r8169: eth0: link down
[  300.179375] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  319.793654] usb 7-1: USB disconnect, address 2
[  851.546017] ath_pci: disagrees about version of symbol _ath_hal_attach
[  851.546026] ath_pci: Unknown symbol _ath_hal_attach
[  851.546252] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  851.546256] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  851.547147] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  851.547151] ath_pci: Unknown symbol ath_hal_computetxtime
[  851.547734] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  851.547739] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  851.548140] ath_pci: Unknown symbol _ath_hal_detach
[  851.549470] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  851.550784] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  851.550791] ath_pci: Unknown symbol ath_hal_init_channels
[  851.551355] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  851.551360] ath_pci: Unknown symbol ath_hal_getwirelessmodes

Typically I use the following to get everything back operational.
```

cd ~/madwifi_ar5007
cd madwifi-hal-0.10.5.6-r4068-20090705
make clean
make
sudo make install
sudo modprobe ath_pci
sudo /etc/init.d/networking restart

```

Any help would be appreciated.

lkraemer

---

### Post by stlsaint on 2009-09-03
i too had this same issue with a acer aspire notebook. but i was unable to find a fix so basically im replying to keep the thead alive without it fading to the back. there are many articles on how to fix the issue thru google but i have had no success...i ended up installin a seperate distro on that system.

---

### Post by lkraemer on 2009-09-03
I posted at [https://answers.launchpad.net/ubuntu/+question/81819](https://answers.launchpad.net/ubuntu/+question/81819)
and got this reply .........which worked GREAT!....

Please try the solution from forumuser Ilove2023 at the following location:
[http://www.uluga.ubuntuforums.org/showthread.php?p=5196946](http://www.uluga.ubuntuforums.org/showthread.php?p=5196946)

On my computer, I can see the madwifi-unload script under madwifi-trunk-r4031-20090529/scripts

On your pc, the madwifi-unload script should be in ~/madwifi_ar5007/madwifi-hal-0.10.5.6-r4068-20090705/scripts

After running the madwifi-unload script, you can proceed with your usual commands (make clean , make, .....)

Or you could try this alternative madwifi reinstallation script:

[http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

THANKS!.

lkraemer

---

