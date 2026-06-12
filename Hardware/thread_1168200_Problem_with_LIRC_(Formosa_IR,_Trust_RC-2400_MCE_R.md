---
title: "Problem with LIRC (Formosa IR, Trust RC-2400 MCE RC) &amp; Ubuntu 9.04 Jaunty"
date: 2009-05-23
forum: Hardware
---

### Post by elafos2008 on 2009-05-23
Hi,

after more than one day of trying I now decided to ask you in the forum for help... :(

I have installed Ubuntu 9.04 on my new Acer Revo R3600, which is intended to work as HTPC. Everything works just fine now, jsut the remote control seems impossible to get to work. I read all articles, tried nearly every hint/idea without success. 

The Formosa IR receiver is connected via USB and part of a set with the Trust RC-2400 MCE remote control. I installed LIRC (0.8.4a) and configured the device as Vista Media Center Remote. Also I loaded the modules "lirc_dev.ko" and "lirc_mceusb2.ko" into "/lib/modules/2.6.28-11-generic/misc" and also "/lib/modules/2.6.28-11-generic/ubuntu/media/lirc" (<-- here without suffix "-ko").

I tried both "old" (RC-5) and "new" (RC-6) version (but know that its RC-6), both with same bad result. The device is recognized when looking into "lsusb", but there seems to be no input assigned. May that be the problem (and if yes, what can I do?)?

When starting "irw" I get no response when pressing a button on my remote. Occasionally it seems to work for one time (once pressing the button) when I unplug and reconnect the IR-USB receiver ( I see a red response light on the IR receiver) and then it stops again - seems something crashes.

**irw**
000000037ff07be1 00 Up mceusb

Some more logs (I add as much as possible, hopefully you can find something and give me a hint.....) are listed below.

I would so much appreciate a reply from you, hopefully you experts can help a noob like me.. ;)

Have a good day!
[B]
lsusb[/B]
Bus 001 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 152e:2507 LG (HLDS) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 008: ID 147a:e017 Formosa Industrial Computing, Inc. 
Bus 002 Device 003: ID 046d:c058 Logitech, Inc. 
Bus 002 Device 002: ID 04f2:0402 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[B]ls -la /dev/input/by-id/
[/B]insgesamt 0
drwxr-xr-x 2 root root 100 2009-05-24 01:32 .
drwxr-xr-x 4 root root 280 2009-05-24 01:32 ..
lrwxrwxrwx 1 root root   9 2009-05-24 01:32 usb-Chicony_USB_Keyboard-event-kbd -> ../event3
lrwxrwxrwx 1 root root   9 2009-05-24 01:32 usb-Logitech_USB_Optical_Mouse-event-mouse -> ../event5
lrwxrwxrwx 1 root root   9 2009-05-24 01:32 usb-Logitech_USB_Optical_Mouse-mouse -> ../mouse1

**dmesg** (the interesting part only)

[   11.620983] udev: starting version 141
[   11.790073] lirc_dev: IR Remote Control driver registered, major 61 
[   11.795961] 
[   11.795969] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.51 $
[   11.795978] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   11.836727] usbcore: registered new interface driver hiddev
[   11.848259] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-1/2-1:1.0/input/input3
[   11.874450] generic-usb 0003:04F2:0402.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony USB Keyboard] on usb-0000:00:04.0-1/input0
[   11.901594] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-1/2-1:1.1/input/input4
[   11.928343] generic-usb 0003:04F2:0402.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Chicony USB Keyboard] on usb-0000:00:04.0-1/input1
[   11.935845] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb2/2-4/2-4:1.0/input/input5
[   11.965015] generic-usb 0003:046D:C058.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:04.0-4/input0
[   11.965080] usbcore: registered new interface driver usbhid
[   11.965201] usbhid: v2.6:USB HID core driver
[   12.176104] usb 2-6: reset low speed USB device using ohci_hcd and address 4
[   12.247045] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.473280] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   12.542482] lirc_dev: lirc_register_plugin: sample_rate: 0
[   12.548466] lirc_mceusb2[4]: Formosa21 SnowflakeEmulation on usb2:4
[   12.548573] usbcore: registered new interface driver lirc_mceusb2
[   12.548644] cfg80211: Calling CRDA to update world regulatory domain
[   12.885070] Linux agpgart interface v0.103
[   12.925604] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.925629] acer-wmi: No or unsupported WMI interface, unable to load
[   13.040259] cfg80211: World regulatory domain updated:
[   13.040268]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.040275]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.040280]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.040286]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.040291]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.040296]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.935090] nvidia: module license 'NVIDIA' taints kernel.
[   14.082742] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 19
[   14.082762] ath5k_pci 0000:05:00.0: PCI INT A -> Link[LN4A] -> GSI 19 (level, low) -> IRQ 19
[   14.082779] ath5k_pci 0000:05:00.0: setting latency timer to 64
[   14.083188] ath5k_pci 0000:05:00.0: registered as 'phy0'
[   14.130531] phy0: Selected rate control algorithm 'pid'
[   14.197092] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 22
[   14.197104] nvidia 0000:03:00.0: PCI INT A -> Link[SGRU] -> GSI 22 (level, low) -> IRQ 22
[   14.197117] nvidia 0000:03:00.0: setting latency timer to 64
[   14.197732] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.51  Thu Apr 16 19:02:15 PDT 2009
[   14.254642] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   14.293814] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   14.294818] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   14.294828] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   14.294921] HDA Intel 0000:00:08.0: setting latency timer to 64
[   14.684034] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   15.601883] lp: driver loaded but no devices found
[   15.763698] Adding 2104444k swap on /dev/sda7.  Priority:-1 extents:1 across:2104444k
[   16.340832] EXT3 FS on sda5, internal journal
[   17.433242] kjournald starting.  Commit interval 5 seconds
[   17.433508] EXT3 FS on sda6, internal journal
[   17.433518] EXT3-fs: mounted filesystem with ordered data mode.
[   17.895550] type=1505 audit(1243125252.847:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2133
[   18.006939] type=1505 audit(1243125252.959:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2137
[   18.007227] type=1505 audit(1243125252.959:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2137
[   18.007343] type=1505 audit(1243125252.959:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2137
[   18.007444] type=1505 audit(1243125252.959:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2137
[   18.323048] type=1505 audit(1243125253.275:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2142
[   18.323452] type=1505 audit(1243125253.275:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2142
[   18.387084] type=1505 audit(1243125253.339:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2146
[   20.453468] usbcore: registered new interface driver lirc_mceusb
[   20.454031] lirc_mceusb: USB Microsoft IR Transceiver Driver v0.2
[   23.668462] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.668469] Bluetooth: BNEP filters: protocol multicast
[   23.714477] Bridge firewalling registered
[   24.908813] ppdev: user-space parallel port driver

---

### Post by elafos2008 on 2009-05-24
...does no one have an idea? Can you maybe at least recommend an RC that works without any issues in Ubuntu 9.04 & LIRC (but also with Windows) and that can  be purchased in Germany??? I dont want to, but if its the last exit I´ll take it.

---

### Post by darklord on 2009-06-21
I also had problems with mine remote (for jaunty - ubuntu 9.04), which uses a similar receiver

, i found a partial fix for gnome-lirc-properties see message 4 in the below link, this resolve a known bug - hope this helps but i still have to setup gnome-lirc-properties after rebooting.

[http://ubuntuforums.org/showthread.p...30#post7492230](http://ubuntuforums.org/showthread.p...30#post7492230)

---

