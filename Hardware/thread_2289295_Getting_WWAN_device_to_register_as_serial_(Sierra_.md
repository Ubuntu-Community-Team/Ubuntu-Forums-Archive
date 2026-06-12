---
title: "Getting WWAN device to register as serial (Sierra Gobi 3000 / MC8355)"
date: 2015-08-03
forum: Hardware
---

### Post by Paul_Jewell on 2015-08-03
Hello all, 

My thinkpad (x220 tablet) came with a Sierra Gobi 3000 / MC8355 WWAN device and I have been milling around google for a few weeks on and off trying to get the gps functionality to work. The card is registered in lsusb but most guides tell me I need to get a serial device to connect to. (/dev/ttyUSB, /dev/ttyUSB0x) I am unable to figure out how to get this device to show up. I post the log below (/var/log/syslog), it does not look like a critical error but possibly it could help. Please let me know what other output or information I should post!

```

Aug  2 17:52:18 paul-ThinkPad-X220-Tablet kernel: [44832.367276] video LNXVIDEO:00: Restoring backlight state
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet avahi-daemon[738]: Withdrawing workstation service for wwan0.
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet kernel: [44832.374503] usb 2-1.1: New USB device found, idVendor=0bda, idProduct=8187
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet kernel: [44832.374560] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet kernel: [44832.374570] usb 2-1.1: Product: RTL8187_Wireless
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet kernel: [44832.374578] usb 2-1.1: Manufacturer: Manufacturer_Realtek_RTL8187_
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet kernel: [44832.374585] usb 2-1.1: SerialNumber: 00C0CA65C092
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet kernel: [44832.376704] usb 2-1.4: USB disconnect, device number 11
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet kernel: [44832.377005] cdc_mbim 2-1.4:2.5 wwan0: unregister 'cdc_mbim' usb-0000:00:1d.0-1.4, CDC MBIM
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet ModemManager[22687]: <info>  (net/wwan0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet NetworkManager[22693]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:2.5/net/wwan0, iface: wwan0)
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet mtp-probe: checking bus 2, device 12: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet mtp-probe: bus: 2, device: 12 was not an MTP device
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet ModemManager[22687]: [/dev/cdc-wdm0] unexpected port hangup!
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet ModemManager[22687]: <info>  (usbmisc/cdc-wdm0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet kernel: [44832.478644] psmouse serio1: synaptics: queried max coordinates: x [..5472], y [..4448]
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet NetworkManager[22693]: <info> wake requested (sleeping: yes  enabled: yes)
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet NetworkManager[22693]: <info> waking up and re-enabling...
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet NetworkManager[22693]: <info> WWAN now enabled by management service
Aug  2 17:52:18 paul-ThinkPad-X220-Tablet NetworkManager[22693]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
```

Thank you for reading.

---

### Post by Paul_Jewell on 2015-08-04
Actually I think that I found where the issue is, but I don't know much about writing drivers so I can't say how best to fix it. I get the error "unknown number of interfaces" as shown below. As seen in the source ([http://lxr.free-electrons.com/source/drivers/usb/serial/qcserial.c](http://lxr.free-electrons.com/source/drivers/usb/serial/qcserial.c)), the device should only have 3 or 4 interfaces, but for some reason mine has 5, even though the device is listed as being supported in that driver file. I have tried updating to a mainline kernel temporarily as some suggested that there are updates in the driver files, but this has not worked either. 

```
Aug  3 23:03:06 paul-ThinkPad-X220-Tablet kernel: [   49.898443] usbserial: USB Serial deregistering driver Qualcomm USB modemAug  3 23:03:06 paul-ThinkPad-X220-Tablet kernel: [   49.898469] usbcore: deregistering interface driver qcserial
Aug  3 23:03:13 paul-ThinkPad-X220-Tablet kernel: [   56.623753] usbcore: registered new interface driver qcserial
Aug  3 23:03:13 paul-ThinkPad-X220-Tablet kernel: [   56.623766] usbserial: USB Serial support registered for Qualcomm USB modem
Aug  3 23:03:13 paul-ThinkPad-X220-Tablet kernel: [   56.687173] usb 2-1.4: unknown number of interfaces: 5
Aug  3 23:03:13 paul-ThinkPad-X220-Tablet kernel: [   56.687196] usb 2-1.4: unknown number of interfaces: 5
Aug  3 23:03:13 paul-ThinkPad-X220-Tablet kernel: [   56.687204] usb 2-1.4: unknown number of interfaces: 5

```

Does anyone know if there is another driver which would support 5 interfaces, or if there is a good place to submit this bug report to? I don't think I should mess wiht the driver myself, as I am not really sure what I am doing!

Thanks for reading.

---

### Post by tgalati4 on 2015-08-04
The module (driver) that you are trying to run handles up to Gobi 2000.  You have a Gobi 3000.

>  25 /* standard device layouts supported by this driver */
 26 enum qcserial_layouts {
 27         QCSERIAL_G2K = 0,       /*** Gobi 2000** */
 28         QCSERIAL_G1K = 1,       /* Gobi 1000 */
 29         QCSERIAL_SWI = 2,       /* Sierra Wireless */
 30         QCSERIAL_HWI = 3,       /* Huawei */


You can send an email to the developers (somebody at Qualcomm), or try writing some code to recognize your Gobi 3000 and treat it as a 2000 and see if it works.

> tgalati4@Mint17 ~ $ modinfo qcserial
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/usb/serial/qcserial.ko
license:        GPL v2
description:    Qualcomm USB Serial driver
**author:         Qualcomm Inc**


---

### Post by Paul_Jewell on 2015-08-04
The gobi 3000 is listed on line 131 of the file I linked to. ([http://lxr.free-electrons.com/source/drivers/usb/serial/qcserial.c](http://lxr.free-electrons.com/source/drivers/usb/serial/qcserial.c)) Are these devices "recognized" but just not supported yet? It just seems strange to list them at all. If you think it won't break anything major if I mess with this driver, so you know what the best way is to build/make this file in ubuntu?

---

