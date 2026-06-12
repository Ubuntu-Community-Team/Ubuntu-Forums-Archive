---
title: "DEC 2000t USB Digital TV box not working."
date: 2005-02-17
forum: Hardware &amp; Laptops
---

### Post by kobeyu on 2005-02-17
Hi,

> kobe@kimiko:~ $ cat /etc/issue
Ubuntu 5.04 "Hoary Hedgehog" Development Branch 

I'm trying to get my DEC2000t working. It uses the ttusb_dec driver.
> 
kobe@kimiko:~ $ lsmod |grep ttusb
ttusb_dec              22344  0
dvb_core               84008  1 ttusb_dec
ttusbdecfe              4288  1 ttusb_dec
usbcore               119864  6 usb_storage,ttusb_dec,ehci_hcd,usbhid,uhci_hcd
firmware_class         10752  2 ttusb_dec,bttv
crc32                   4672  6 via_rhine,ttusb_dec,dvb_core,8139too,8139cp,fbcon

However, when I plug it in (or at boot time), logs say: (Note: I've doctored the /etc/hotplug/firmware.agent script to add a few debug messages)

> 
Feb 17 09:45:27 kimiko default.hotplug[12570]: arguments (usb) env (SUBSYSTEM=usb OLDPWD=/ DEVPATH=/devices/pci0000:00/0000:00:10.1/usb2/2-1 PATH=/bin:/sbin:/usr/sbin:/usr/bin ACTION=add PWD=/etc/hotplug UDEV_LOG=1 MANAGED_EVENT=1 SHLVL=1 HOME=/ PHYSDEVDRIVER=usb DEBUG=yes PHYSDEVBUS=usb SEQNUM=1426 _=/usr/bin/env)
Feb 17 09:45:27 kimiko default.hotplug[12570]: invoke /etc/hotplug/usb.agent ()
Feb 17 09:45:37 kimiko default.hotplug[12590]: arguments (firmware) env (PHYSDEVPATH=/devices/pci0000:00/0000:00:10.1/usb2/2-1 SUBSYSTEM=firmware OLDPWD=/ DEVPATH=/class/firmware/2-1 FIRMWARE=dvb-ttusb-dec-2000t.fw PATH=/bin:/sbin:/usr/sbin:/usr/bin
ACTION=remove PWD=/etc/hotplug UDEV_LOG=1 MANAGED_EVENT=1 SHLVL=1 HOME=/ PHYSDEVDRIVER=usb DEBUG=yes PHYSDEVBUS=usb SEQNUM=1429 _=/usr/bin/env)
Feb 17 09:45:37 kimiko default.hotplug[12590]: invoke /etc/hotplug/firmware.agent ()
Feb 17 09:45:37 kimiko firmware.agent[12590]: Loaded functions
Feb 17 09:45:37 kimiko firmware.agent[12590]: Set directories: /lib/hotplug/firmware /usr/local/lib/hotplug/firmware /usr/lib/hotplug/firmware
Feb 17 09:45:37 kimiko firmware.agent[12590]: Set SYSFS: /sys and VERSION: 2.6.10-3-k7-smp
Feb 17 09:45:37 kimiko firmware.agent[12590]: ACTION is 'remove'
Feb 17 09:45:37 kimiko kernel:  [autoremove_wake_function+0/87] autoremove_wake_function+0x0/0x57
Feb 17 09:45:37 kimiko kernel:  [ret_from_fork+6/20] ret_from_fork+0x6/0x14
Feb 17 09:45:37 kimiko kernel:  [autoremove_wake_function+0/87] autoremove_wake_function+0x0/0x57
Feb 17 09:45:37 kimiko kernel:  [pg0+545708406/1069851648] hub_thread+0x0/0x110 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [kernel_thread_helper+5/11] kernel_thread_helper+0x5/0xb
Feb 17 09:45:37 kimiko kernel: usb 2-1: USB disconnect, address 5
Feb 17 09:45:37 kimiko kernel: usb 2-1: new full speed USB device using uhci_hcd and address 6
Feb 17 09:45:37 kimiko kernel: ttusb_dec: no version info in Firmware
Feb 17 09:45:37 kimiko kernel: usb_unlink_urb() is deprecated for synchronous unlinks.  Use usb_kill_urb() instead.
Feb 17 09:45:37 kimiko kernel: Badness in usb_unlink_urb at drivers/usb/core/urb.c:457
Feb 17 09:45:37 kimiko kernel:  [pg0+545717227/1069851648] usb_unlink_urb+0x99/0x9b [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545903968/1069851648] ttusb_dec_exit_usb+0x30/0x59 [ttusb_dec]
Feb 17 09:45:37 kimiko kernel:  [pg0+545904393/1069851648] ttusb_dec_probe+0x98/0x214 [ttusb_dec]
Feb 17 09:45:37 kimiko kernel:  [sysfs_add_file+88/121] sysfs_add_file+0x58/0x79
Feb 17 09:45:37 kimiko kernel:  [pg0+545693813/1069851648] usb_probe_interface+0x6f/0x88 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [driver_probe_device+47/110] driver_probe_device+0x2f/0x6e
Feb 17 09:45:37 kimiko kernel:  [device_attach+65/150] device_attach+0x41/0x96
Feb 17 09:45:37 kimiko kernel:  [kobject_get+26/36] kobject_get+0x1a/0x24
Feb 17 09:45:37 kimiko kernel:  [bus_add_device+92/173] bus_add_device+0x5c/0xad
Feb 17 09:45:37 kimiko kernel:  [device_pm_add+93/153] device_pm_add+0x5d/0x99
Feb 17 09:45:37 kimiko kernel:  [device_add+199/343] device_add+0xc7/0x157
Feb 17 09:45:37 kimiko kernel:  [pg0+545723529/1069851648] usb_set_configuration+0x2f7/0x45e [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545703294/1069851648] usb_new_device+0xb4/0x16d [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545707050/1069851648] hub_port_connect_change+0x213/0x3f1 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545708117/1069851648] hub_events+0x24d/0x36e [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545708459/1069851648] hub_thread+0x35/0x110 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [autoremove_wake_function+0/87] autoremove_wake_function+0x0/0x57
Feb 17 09:45:37 kimiko kernel:  [ret_from_fork+6/20] ret_from_fork+0x6/0x14
Feb 17 09:45:37 kimiko kernel:  [autoremove_wake_function+0/87] autoremove_wake_function+0x0/0x57
Feb 17 09:45:37 kimiko kernel:  [pg0+545708406/1069851648] hub_thread+0x0/0x110 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [kernel_thread_helper+5/11] kernel_thread_helper+0x5/0xb
Feb 17 09:45:37 kimiko kernel: usb_unlink_urb() is deprecated for synchronous unlinks.  Use usb_kill_urb() instead.
Feb 17 09:45:37 kimiko kernel: Badness in usb_unlink_urb at drivers/usb/core/urb.c:457
Feb 17 09:45:37 kimiko kernel:  [pg0+545717227/1069851648] usb_unlink_urb+0x99/0x9b [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545903968/1069851648] ttusb_dec_exit_usb+0x30/0x59 [ttusb_dec]
Feb 17 09:45:37 kimiko kernel:  [pg0+545904393/1069851648] ttusb_dec_probe+0x98/0x214 [ttusb_dec]
Feb 17 09:45:37 kimiko kernel:  [sysfs_add_file+88/121] sysfs_add_file+0x58/0x79
Feb 17 09:45:37 kimiko kernel:  [pg0+545693813/1069851648] usb_probe_interface+0x6f/0x88 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [driver_probe_device+47/110] driver_probe_device+0x2f/0x6e
Feb 17 09:45:37 kimiko kernel:  [device_attach+65/150] device_attach+0x41/0x96
Feb 17 09:45:37 kimiko kernel:  [kobject_get+26/36] kobject_get+0x1a/0x24
Feb 17 09:45:37 kimiko kernel:  [bus_add_device+92/173] bus_add_device+0x5c/0xad
Feb 17 09:45:37 kimiko kernel:  [device_pm_add+93/153] device_pm_add+0x5d/0x99
Feb 17 09:45:37 kimiko kernel:  [device_add+199/343] device_add+0xc7/0x157
Feb 17 09:45:37 kimiko kernel:  [pg0+545723529/1069851648] usb_set_configuration+0x2f7/0x45e [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545703294/1069851648] usb_new_device+0xb4/0x16d [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545707050/1069851648] hub_port_connect_change+0x213/0x3f1 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545708117/1069851648] hub_events+0x24d/0x36e [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545708459/1069851648] hub_thread+0x35/0x110 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [autoremove_wake_function+0/87] autoremove_wake_function+0x0/0x57
Feb 17 09:45:37 kimiko kernel:  [ret_from_fork+6/20] ret_from_fork+0x6/0x14
Feb 17 09:45:37 kimiko kernel:  [autoremove_wake_function+0/87] autoremove_wake_function+0x0/0x57
Feb 17 09:45:37 kimiko kernel:  [pg0+545708406/1069851648] hub_thread+0x0/0x110 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [kernel_thread_helper+5/11] kernel_thread_helper+0x5/0xb
Feb 17 09:45:37 kimiko kernel: usb_unlink_urb() is deprecated for synchronous unlinks.  Use usb_kill_urb() instead.
Feb 17 09:45:37 kimiko kernel: Badness in usb_unlink_urb at drivers/usb/core/urb.c:457
Feb 17 09:45:37 kimiko kernel:  [pg0+545717227/1069851648] usb_unlink_urb+0x99/0x9b [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545903968/1069851648] ttusb_dec_exit_usb+0x30/0x59 [ttusb_dec]
Feb 17 09:45:37 kimiko kernel:  [pg0+545904393/1069851648] ttusb_dec_probe+0x98/0x214 [ttusb_dec]
Feb 17 09:45:37 kimiko kernel:  [sysfs_add_file+88/121] sysfs_add_file+0x58/0x79
Feb 17 09:45:37 kimiko kernel:  [pg0+545693813/1069851648] usb_probe_interface+0x6f/0x88 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [driver_probe_device+47/110] driver_probe_device+0x2f/0x6e
Feb 17 09:45:37 kimiko kernel:  [device_attach+65/150] device_attach+0x41/0x96
Feb 17 09:45:37 kimiko kernel:  [kobject_get+26/36] kobject_get+0x1a/0x24
Feb 17 09:45:37 kimiko kernel:  [bus_add_device+92/173] bus_add_device+0x5c/0xad
Feb 17 09:45:37 kimiko kernel:  [device_pm_add+93/153] device_pm_add+0x5d/0x99
Feb 17 09:45:37 kimiko kernel:  [device_add+199/343] device_add+0xc7/0x157
Feb 17 09:45:37 kimiko kernel:  [pg0+545723529/1069851648] usb_set_configuration+0x2f7/0x45e [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545703294/1069851648] usb_new_device+0xb4/0x16d [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545707050/1069851648] hub_port_connect_change+0x213/0x3f1 [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545708117/1069851648] hub_events+0x24d/0x36e [usbcore]
Feb 17 09:45:37 kimiko kernel:  [pg0+545708459/1069851648] hub_thread+0x35/0x110 [usbcore]
Feb 17 09:45:38 kimiko kernel:  [autoremove_wake_function+0/87] autoremove_wake_function+0x0/0x57
Feb 17 09:45:38 kimiko kernel:  [ret_from_fork+6/20] ret_from_fork+0x6/0x14
Feb 17 09:45:38 kimiko kernel:  [autoremove_wake_function+0/87] autoremove_wake_function+0x0/0x57
Feb 17 09:45:38 kimiko kernel:  [pg0+545708406/1069851648] hub_thread+0x0/0x110 [usbcore]
Feb 17 09:45:38 kimiko kernel:  [kernel_thread_helper+5/11] kernel_thread_helper+0x5/0xb
Feb 17 09:45:38 kimiko kernel: usb_unlink_urb() is deprecated for synchronous unlinks.  Use usb_kill_urb() instead.
Feb 17 09:45:38 kimiko kernel: Badness in usb_unlink_urb at drivers/usb/core/urb.c:457
Feb 17 09:45:38 kimiko kernel:  [pg0+545717227/1069851648] usb_unlink_urb+0x99/0x9b [usbcore]
Feb 17 09:45:38 kimiko kernel:  [pg0+545903968/1069851648] ttusb_dec_exit_usb+0x30/0x59 [ttusb_dec]
Feb 17 09:45:38 kimiko kernel:  [pg0+545904393/1069851648] ttusb_dec_probe+0x98/0x214 [ttusb_dec]
Feb 17 09:45:38 kimiko kernel:  [sysfs_add_file+88/121] sysfs_add_file+0x58/0x79
Feb 17 09:45:38 kimiko kernel:  [pg0+545693813/1069851648] usb_probe_interface+0x6f/0x88 [usbcore]
Feb 17 09:45:38 kimiko kernel:  [driver_probe_device+47/110] driver_probe_device+0x2f/0x6e
Feb 17 09:45:38 kimiko kernel:  [device_attach+65/150] device_attach+0x41/0x96
Feb 17 09:45:38 kimiko kernel:  [kobject_get+26/36] kobject_get+0x1a/0x24
Feb 17 09:45:38 kimiko kernel:  [bus_add_device+92/173] bus_add_device+0x5c/0xad
Feb 17 09:45:38 kimiko kernel:  [device_pm_add+93/153] device_pm_add+0x5d/0x99
Feb 17 09:45:38 kimiko kernel:  [device_add+199/343] device_add+0xc7/0x157
Feb 17 09:45:38 kimiko default.hotplug[12611]: arguments (usb) env (SUBSYSTEM=usb OLDPWD=/ DEVPATH=/devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0 PATH=/bin:/sbin:/usr/sbin:/usr/bin ACTION=add PWD=/etc/hotplug UDEV_LOG=1 MANAGED_EVENT=1 SHLVL=1 HOME=/ DEVICE=/proc/bus/usb/002/006 INTERFACE=0/0/0 PRODUCT=b48/1008/100 TYPE=0/0/0 DEBUG=yes PHYSDEVBUS=usb SEQNUM=1427 _=/usr/:bin/env)
Feb 17 09:45:38 kimiko default.hotplug[12611]: invoke /etc/hotplug/usb.agent ()
Feb 17 09:45:38 kimiko usb.agent[12611]: Setup ttusb_dec for USB product b48/1008/100
Feb 17 09:45:38 kimiko usb.agent[12611]:      ttusb_dec: already loaded
Feb 17 09:45:38 kimiko default.hotplug[12651]: arguments (firmware) env (PHYSDEVPATH=/devices/pci0000:00/0000:00:10.1/usb2/2-1 SUBSYSTEM=firmware OLDPWD=/ DEVPATH=/class/firmware/2-1 FIRMWARE=dvb-ttusb-dec-2000t.fw PATH=/bin:/sbin:/usr/sbin:/usr/bin
ACTION=add PWD=/etc/hotplug UDEV_LOG=1 MANAGED_EVENT=1 SHLVL=1 HOME=/ PHYSDEVDRIVER=usb DEBUG=yes PHYSDEVBUS=usb SEQNUM=1428
_=/usr/bin/env)
Feb 17 09:45:38 kimiko default.hotplug[12651]: invoke /etc/hotplug/firmware.agent ()
Feb 17 09:45:38 kimiko firmware.agent[12651]: Loaded functions
Feb 17 09:45:38 kimiko firmware.agent[12651]: Set directories: /lib/hotplug/firmware /usr/local/lib/hotplug/firmware /usr/lib/hotplug/firmware
Feb 17 09:45:38 kimiko firmware.agent[12651]: Set SYSFS: /sys and VERSION: 2.6.10-3-k7-smp
Feb 17 09:45:38 kimiko firmware.agent[12651]: ACTION is 'add'
Feb 17 09:45:38 kimiko firmware.agent[12651]: Adding firmware
Feb 17 09:45:39 kimiko firmware.agent[12651]: Looking in /lib/hotplug/firmware for dvb-ttusb-dec-2000t.fw with Version 2.6.10-3-k7-smp
Feb 17 09:45:39 kimiko firmware.agent[12651]: Found versionless file



and in dmesg:

> ttusb_dec: no version info in Firmware
ttusb_dec_boot_dsp: Firmware (dvb-ttusb-dec-2000t.fw) unavailable.
usb_unlink_urb() is deprecated for synchronous unlinks.  Use usb_kill_urb() instead.
Badness in usb_unlink_urb at drivers/usb/core/urb.c:457
 [<e0c23beb>] usb_unlink_urb+0x99/0x9b [usbcore]
 [<e0c51560>] ttusb_dec_exit_usb+0x30/0x59 [ttusb_dec]
 [<e0c51709>] ttusb_dec_probe+0x98/0x214 [ttusb_dec]
 [<c0193dc9>] sysfs_add_file+0x58/0x79
 [<e0c1e075>] usb_probe_interface+0x6f/0x88 [usbcore]
 [<c020ec63>] driver_probe_device+0x2f/0x6e
 [<c020ece3>] device_attach+0x41/0x96
 [<c01b4951>] kobject_get+0x1a/0x24
 [<c020ef9d>] bus_add_device+0x5c/0xad
 [<c02119ec>] device_pm_add+0x5d/0x99
 [<c020de23>] device_add+0xc7/0x157
 [<e0c25489>] usb_set_configuration+0x2f7/0x45e [usbcore]
 [<e0c2057e>] usb_new_device+0xb4/0x16d [usbcore]
 [<e0c2142a>] hub_port_connect_change+0x213/0x3f1 [usbcore]
 [<e0c21855>] hub_events+0x24d/0x36e [usbcore]
 [<e0c219ab>] hub_thread+0x35/0x110 [usbcore]
 [<c012fa7a>] autoremove_wake_function+0x0/0x57
 [<c0102e56>] ret_from_fork+0x6/0x14
 [<c012fa7a>] autoremove_wake_function+0x0/0x57
 [<e0c21976>] hub_thread+0x0/0x110 [usbcore]
 [<c0101295>] kernel_thread_helper+0x5/0xb
usb_unlink_urb() is deprecated for synchronous unlinks.  Use usb_kill_urb() instead.
Badness in usb_unlink_urb at drivers/usb/core/urb.c:457
 [<e0c23beb>] usb_unlink_urb+0x99/0x9b [usbcore]
 [<e0c51560>] ttusb_dec_exit_usb+0x30/0x59 [ttusb_dec]
 [<e0c51709>] ttusb_dec_probe+0x98/0x214 [ttusb_dec]
 [<c0193dc9>] sysfs_add_file+0x58/0x79
 [<e0c1e075>] usb_probe_interface+0x6f/0x88 [usbcore]
 [<c020ec63>] driver_probe_device+0x2f/0x6e
 [<c020ece3>] device_attach+0x41/0x96
 [<c01b4951>] kobject_get+0x1a/0x24
 [<c020ef9d>] bus_add_device+0x5c/0xad
 [<c02119ec>] device_pm_add+0x5d/0x99
 [<c020de23>] device_add+0xc7/0x157
[<e0c25489>] usb_set_configuration+0x2f7/0x45e [usbcore]
 [<e0c2057e>] usb_new_device+0xb4/0x16d [usbcore]
 [<e0c2142a>] hub_port_connect_change+0x213/0x3f1 [usbcore]
 [<e0c21855>] hub_events+0x24d/0x36e [usbcore]
 [<e0c219ab>] hub_thread+0x35/0x110 [usbcore]
 [<c012fa7a>] autoremove_wake_function+0x0/0x57
 [<c0102e56>] ret_from_fork+0x6/0x14
 [<c012fa7a>] autoremove_wake_function+0x0/0x57
 [<e0c21976>] hub_thread+0x0/0x110 [usbcore]
 [<c0101295>] kernel_thread_helper+0x5/0xb
usb_unlink_urb() is deprecated for synchronous unlinks.  Use usb_kill_urb() instead.
Badness in usb_unlink_urb at drivers/usb/core/urb.c:457
 [<e0c23beb>] usb_unlink_urb+0x99/0x9b [usbcore]
 [<e0c51560>] ttusb_dec_exit_usb+0x30/0x59 [ttusb_dec]
 [<e0c51709>] ttusb_dec_probe+0x98/0x214 [ttusb_dec]
 [<c0193dc9>] sysfs_add_file+0x58/0x79
 [<e0c1e075>] usb_probe_interface+0x6f/0x88 [usbcore]
 [<c020ec63>] driver_probe_device+0x2f/0x6e
 [<c020ece3>] device_attach+0x41/0x96
 [<c01b4951>] kobject_get+0x1a/0x24
 [<c020ef9d>] bus_add_device+0x5c/0xad
 [<c02119ec>] device_pm_add+0x5d/0x99
 [<c020de23>] device_add+0xc7/0x157
 [<e0c25489>] usb_set_configuration+0x2f7/0x45e [usbcore]
 [<e0c2057e>] usb_new_device+0xb4/0x16d [usbcore]
 [<e0c2142a>] hub_port_connect_change+0x213/0x3f1 [usbcore]
 [<e0c21855>] hub_events+0x24d/0x36e [usbcore]
 [<e0c219ab>] hub_thread+0x35/0x110 [usbcore]
 [<c012fa7a>] autoremove_wake_function+0x0/0x57
 [<c0102e56>] ret_from_fork+0x6/0x14
 [<c012fa7a>] autoremove_wake_function+0x0/0x57
 [<e0c21976>] hub_thread+0x0/0x110 [usbcore]
 [<c0101295>] kernel_thread_helper+0x5/0xb
usb_unlink_urb() is deprecated for synchronous unlinks.  Use usb_kill_urb() instead.
Badness in usb_unlink_urb at drivers/usb/core/urb.c:457
 [<e0c23beb>] usb_unlink_urb+0x99/0x9b [usbcore]
 [<e0c51560>] ttusb_dec_exit_usb+0x30/0x59 [ttusb_dec]
 [<e0c51709>] ttusb_dec_probe+0x98/0x214 [ttusb_dec]
 [<c0193dc9>] sysfs_add_file+0x58/0x79
 [<e0c1e075>] usb_probe_interface+0x6f/0x88 [usbcore]
 [<c020ec63>] driver_probe_device+0x2f/0x6e
 [<c020ece3>] device_attach+0x41/0x96
 [<c01b4951>] kobject_get+0x1a/0x24
 [<c020ef9d>] bus_add_device+0x5c/0xad
 [<c02119ec>] device_pm_add+0x5d/0x99
 [<c020de23>] device_add+0xc7/0x157
 [<e0c25489>] usb_set_configuration+0x2f7/0x45e [usbcore]
 [<e0c2057e>] usb_new_device+0xb4/0x16d [usbcore]
 [<e0c2142a>] hub_port_connect_change+0x213/0x3f1 [usbcore]
 [<e0c21855>] hub_events+0x24d/0x36e [usbcore]
 [<e0c219ab>] hub_thread+0x35/0x110 [usbcore]
 [<c012fa7a>] autoremove_wake_function+0x0/0x57
 [<c0102e56>] ret_from_fork+0x6/0x14
 [<c012fa7a>] autoremove_wake_function+0x0/0x57
 [<e0c21976>] hub_thread+0x0/0x110 [usbcore]
 [<c0101295>] kernel_thread_helper+0x5/0xb


Critical of which (I think) is the "ttusb_dec_boot_dsp: Firmware (dvb-ttusb-dec-2000t.fw) unavailable." line near the top of dmesg (hence the debug in firmware.agent) 
I can't figure out whats going on here. (needless to say, the device doesn't work -- even if I create the /dev/dvb nodes for it, it doesn't work.

I've attached my firmware.agent for completeness.
Any ideas?
Thanks,

Kobeyu.

---

### Post by kobeyu on 2005-02-17
Oh, and needless to say,
> 
kobe@kimiko:/etc/hotplug $ ls /lib/hotplug/firmware/dvb*
/lib/hotplug/firmware/dvb-ttusb-dec-2000t.fw
/lib/hotplug/firmware/dvb-ttusb-dec-2540t.fw
/lib/hotplug/firmware/dvb-ttusb-dec-3000s.fw


Kobeyu.

---

### Post by jo.pettitt on 2005-09-29
I've got mione to load the firmware and MythTV can see the card but I can't get it to tune in any channels yet. Have you managed to get yours working yet?

---

### Post by easyease on 2006-03-21
ive just ordered a usb freeview box off ebay......judging by your problems looks like ill be resorting to using it in windows to. #sigh#

---

