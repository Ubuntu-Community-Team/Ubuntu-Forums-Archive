---
title: "ACPI sleep vs wireless card; logs attached"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by LazyBoy on 2005-05-01
Greetings all,

I'm using Hoary on a Thinkpad T23.  ACPI sleep works unless my PCMCIA wireless card in. 
Here are the logs from a failed sleep with the wireless card and the wired lan connected.

```

May  1 11:09:18 localhost postfix/master[6828]: reload configuration
May  1 11:09:18 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.1
May  1 11:09:18 localhost dhclient: Copyright 2004 Internet Systems Consortium.
May  1 11:09:18 localhost dhclient: All rights reserved.
May  1 11:09:18 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
May  1 11:09:18 localhost dhclient:
May  1 11:09:18 localhost dhclient: sit0: unknown hardware address type 776
May  1 11:09:18 localhost dhclient: sit0: unknown hardware address type 776
May  1 11:09:18 localhost dhclient: Listening on LPF/eth0/00:d0:59:bf:f8:a3
May  1 11:09:18 localhost dhclient: Sending on   LPF/eth0/00:d0:59:bf:f8:a3
May  1 11:09:18 localhost dhclient: Sending on   Socket/fallback
May  1 11:09:18 localhost dhclient: DHCPRELEASE on eth0 to 192.168.12.13 port 67May  1 11:09:18 localhost postfix/master[6828]: reload configuration
May  1 11:09:19 localhost postfix/master[6828]: reload configuration
May  1 11:09:19 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.1
May  1 11:09:19 localhost dhclient: Copyright 2004 Internet Systems Consortium.
May  1 11:09:19 localhost dhclient: All rights reserved.
May  1 11:09:19 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
May  1 11:09:19 localhost dhclient:
May  1 11:09:19 localhost dhclient: sit0: unknown hardware address type 776
May  1 11:09:19 localhost dhclient: sit0: unknown hardware address type 776
May  1 11:09:19 localhost dhclient: Listening on LPF/wlan0/00:80:c8:b5:93:04
May  1 11:09:19 localhost dhclient: Sending on   LPF/wlan0/00:80:c8:b5:93:04
May  1 11:09:19 localhost dhclient: Sending on   Socket/fallback
May  1 11:09:19 localhost dhclient: DHCPRELEASE on wlan0 to 192.168.12.13 port 67
May  1 11:09:19 localhost kernel: FIXME: most likely needs refinement, first implementation version only...
May  1 11:09:19 localhost kernel: get_mask 0x00000000, set_mask 0x00000040
May  1 11:09:19 localhost kernel: setting RXconfig to 2050:0fdd
May  1 11:09:19 localhost kernel: get_mask 0x00000000, set_mask 0x00000000 - after update
May  1 11:09:19 localhost kernel: FIXME: most likely needs refinement, first implementation version only...
May  1 11:09:19 localhost kernel: get_mask 0x00000000, set_mask 0x00000040
May  1 11:09:19 localhost kernel: setting RXconfig to 2050:0fdd
May  1 11:09:19 localhost kernel: get_mask 0x00000000, set_mask 0x00000000 - after update
May  1 11:09:19 localhost kernel: acx_set_status: Setting status = 0 (STARTED)
May  1 11:09:19 localhost kernel: module count --
May  1 11:09:19 localhost kernel: removing /proc entry driver/acx_wlan0_phy
May  1 11:09:19 localhost kernel: removing /proc entry driver/acx_wlan0_eeprom
May  1 11:09:19 localhost kernel: removing /proc entry driver/acx_wlan0_diag
May  1 11:09:19 localhost kernel: removing /proc entry driver/acx_wlan0
May  1 11:09:19 localhost kernel: switching off power LED to save power :-)
May  1 11:09:19 localhost kernel: Removing device wlan0!
May  1 11:09:29 localhost kernel: unregister_netdevice: waiting for wlan0 to become free. Usage count = 1
May  1 11:10:09 localhost last message repeated 4 times
May  1 11:11:10 localhost last message repeated 6 times
May  1 11:12:11 localhost last message repeated 6 times

```
And here are the logs from successful suspend and resume with only the wired lan.

```

May  1 11:48:11 localhost postfix/master[6789]: reload configuration
May  1 11:48:11 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.1
May  1 11:48:11 localhost dhclient: Copyright 2004 Internet Systems Consortium.
May  1 11:48:11 localhost dhclient: All rights reserved.
May  1 11:48:11 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
May  1 11:48:11 localhost dhclient:
May  1 11:48:11 localhost dhclient: sit0: unknown hardware address type 776
May  1 11:48:11 localhost dhclient: sit0: unknown hardware address type 776
May  1 11:48:11 localhost dhclient: Listening on LPF/eth0/00:d0:59:bf:f8:a3
May  1 11:48:11 localhost dhclient: Sending on   LPF/eth0/00:d0:59:bf:f8:a3
May  1 11:48:11 localhost dhclient: Sending on   Socket/fallback
May  1 11:48:11 localhost dhclient: DHCPRELEASE on eth0 to 192.168.12.13 port 67May  1 11:48:11 localhost postfix/master[6789]: reload configuration
May  1 11:48:11 localhost kernel: uhci_hcd 0000:00:1d.0: remove, state 1
May  1 11:48:11 localhost kernel: usb usb1: USB disconnect, address 1
May  1 11:48:11 localhost kernel: uhci_hcd 0000:00:1d.0: USB bus 1 deregistered
May  1 11:48:11 localhost kernel: uhci_hcd 0000:00:1d.1: remove, state 1
May  1 11:48:11 localhost kernel: usb usb2: USB disconnect, address 1
May  1 11:48:12 localhost kernel: uhci_hcd 0000:00:1d.1: USB bus 2 deregistered
May  1 11:48:12 localhost kernel: uhci_hcd 0000:00:1d.2: remove, state 1
May  1 11:48:12 localhost kernel: usb usb3: USB disconnect, address 1
May  1 11:48:12 localhost kernel: uhci_hcd 0000:00:1d.2: USB bus 3 deregistered
May  1 11:48:52 localhost kernel: Stopping tasks: ====================================================================================|
May  1 11:48:52 localhost kernel: Back to C!
May  1 11:48:52 localhost kernel: Warning: CPU frequency is 997500, cpufreq assumed 1000000 kHz.
May  1 11:48:52 localhost kernel: ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 11 (level, low) -> IRQ 11
May  1 11:48:52 localhost kernel: ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 11 (level, low) -> IRQ 11
May  1 11:48:52 localhost kernel: PCI: Setting latency timer of device 0000:00:1f.5 to 64
May  1 11:48:52 localhost kernel: Restarting tasks...VFS: busy inodes on changed media.
May  1 11:48:52 localhost kernel:  done
May  1 11:48:52 localhost udev[7984]: removing device node '/dev/vcsa12'
May  1 11:48:52 localhost udev[7990]: removing device node '/dev/vcs63'
May  1 11:48:52 localhost udev[7995]: removing device node '/dev/vcs12'
May  1 11:48:52 localhost udev[7998]: removing device node '/dev/vcsa63'
May  1 11:48:52 localhost kernel: e100: Intel(R) PRO/100 Network Driver, 3.2.3-k2-NAPI
May  1 11:48:52 localhost kernel: e100: Copyright(c) 1999-2004 Intel CorporationMay  1 11:48:52 localhost kernel: ACPI: PCI interrupt 0000:02:08.0[A] -> GSI 11 (level, low) -> IRQ 11
May  1 11:48:52 localhost kernel: e100: eth0: e100_probe: addr 0xc0200000, irq 11, MAC addr 00:D0:59:BF:F8:A3
May  1 11:48:53 localhost kernel: USB Universal Host Controller Interface driver v2.2
May  1 11:48:53 localhost kernel: ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 11 (level, low) -> IRQ 11
May  1 11:48:53 localhost kernel: uhci_hcd 0000:00:1d.0: Intel Corp. 82801CA/CAM USB (Hub #1)
May  1 11:48:53 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.0 to 64
May  1 11:48:53 localhost kernel: uhci_hcd 0000:00:1d.0: irq 11, io base 0x1800
May  1 11:48:53 localhost kernel: uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
May  1 11:48:53 localhost kernel: hub 1-0:1.0: USB hub found
May  1 11:48:53 localhost kernel: hub 1-0:1.0: 2 ports detected
May  1 11:48:53 localhost kernel: ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 11 (level, low) -> IRQ 11
May  1 11:48:53 localhost kernel: uhci_hcd 0000:00:1d.1: Intel Corp. 82801CA/CAM USB (Hub #2)
May  1 11:48:53 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.1 to 64
May  1 11:48:53 localhost kernel: uhci_hcd 0000:00:1d.1: irq 11, io base 0x1820
May  1 11:48:53 localhost kernel: uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
May  1 11:48:53 localhost kernel: hub 2-0:1.0: USB hub found
May  1 11:48:53 localhost kernel: hub 2-0:1.0: 2 ports detected
May  1 11:48:53 localhost kernel: ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 11 (level, low) -> IRQ 11
May  1 11:48:53 localhost kernel: uhci_hcd 0000:00:1d.2: Intel Corp. 82801CA/CAM USB (Hub #3)
May  1 11:48:53 localhost kernel: PCI: Setting latency timer of device 0000:00:1d.2 to 64
May  1 11:48:53 localhost kernel: uhci_hcd 0000:00:1d.2: irq 11, io base 0x1840
May  1 11:48:53 localhost kernel: uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
May  1 11:48:53 localhost kernel: hub 3-0:1.0: USB hub found
May  1 11:48:53 localhost kernel: hub 3-0:1.0: 2 ports detected
May  1 11:48:53 localhost postfix/master[6789]: reload configuration
May  1 11:48:53 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.1
May  1 11:48:53 localhost dhclient: Copyright 2004 Internet Systems Consortium.
May  1 11:48:53 localhost dhclient: All rights reserved.
May  1 11:48:53 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
May  1 11:48:53 localhost dhclient:
May  1 11:48:53 localhost dhclient: sit0: unknown hardware address type 776
May  1 11:48:53 localhost kernel: VFS: busy inodes on changed media.
May  1 11:48:53 localhost udev[8148]: creating device node '/dev/vcs12'
May  1 11:48:53 localhost udev[8236]: removing device node '/dev/vcsa12'
May  1 11:48:53 localhost udev[8307]: removing device node '/dev/vcs12'
May  1 11:48:53 localhost udev[8313]: creating device node '/dev/vcsa12'
May  1 11:48:53 localhost udev[8337]: creating device node '/dev/vcs12'
May  1 11:48:53 localhost usb.agent[8281]:      usbcore: already loaded
May  1 11:48:53 localhost udev[8349]: removing device node '/dev/vcsa12'
May  1 11:48:53 localhost udev[8361]: removing device node '/dev/vcs12'
May  1 11:48:53 localhost udev[8368]: creating device node '/dev/vcsa12'
May  1 11:48:54 localhost usb.agent[8272]:      usbcore: already loaded
May  1 11:48:54 localhost usb.agent[8252]:      usbcore: already loaded
May  1 11:48:54 localhost udev[8426]: removing device node '/dev/vcsa12'
May  1 11:48:55 localhost dhclient: sit0: unknown hardware address type 776
May  1 11:48:55 localhost dhclient: Bind socket to interface: No such device
May  1 11:48:55 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.1
May  1 11:48:55 localhost dhclient: Copyright 2004 Internet Systems Consortium.
May  1 11:48:55 localhost dhclient: All rights reserved.
May  1 11:48:55 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
May  1 11:48:55 localhost dhclient:
May  1 11:48:55 localhost dhclient: sit0: unknown hardware address type 776
May  1 11:48:55 localhost kernel: e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
May  1 11:48:55 localhost kernel: ACPI: Power Button (FF) [PWRF]
May  1 11:48:55 localhost kernel: ACPI: Lid Switch [LID]
May  1 11:48:55 localhost kernel: ACPI: Sleep Button (CM) [SLPB]
May  1 11:48:56 localhost dhclient: sit0: unknown hardware address type 776
May  1 11:48:56 localhost dhclient: Listening on LPF/eth0/00:d0:59:bf:f8:a3
May  1 11:48:56 localhost dhclient: Sending on   LPF/eth0/00:d0:59:bf:f8:a3
May  1 11:48:56 localhost dhclient: Sending on   Socket/fallback
May  1 11:48:56 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May  1 11:48:57 localhost dhclient: DHCPOFFER from 192.168.12.13
May  1 11:48:57 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
May  1 11:48:57 localhost dhclient: DHCPACK from 192.168.12.13
May  1 11:48:57 localhost dhclient: bound to 192.168.12.102 -- renewal in 238762 seconds.
May  1 11:48:57 localhost postfix/master[6789]: reload configuration
May  1 11:48:59 localhost udev[8539]: removing device node '/dev/vcs12'
May  1 11:48:59 localhost kernel: Warning: CPU frequency is 1000000, cpufreq assumed 997500 kHz.
May  1 11:49:05 localhost kernel: eth0: no IPv6 routers present
May  1 12:13:51 localhost -- MARK --
May  1 12:17:01 localhost /USR/SBIN/CRON[9201]: (root) CMD (   run-parts --report /etc/cron.hourly)

```
Any ideas?

Thanks,
LB

---

