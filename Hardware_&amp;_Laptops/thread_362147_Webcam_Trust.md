---
title: "Webcam Trust"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by Marian.nr on 2007-02-15
Hello

I have WebCam Trust 120 spacecam and installed kubuntu 6.10 edgy, kernel 2.6.17-11-generic.

I had download driver for my webcam >> SPCA5XX
gspcav1-20070110

instaled with instructions from this forum
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/ ......./spca5xx*
sudo make install
sudo modprobe spca5xx

i was tryed it with 
sudo make CC=gcc-3.4

but same result

Command LSUSB wrote:

Bus 005 Device 008: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc.
Bus 005 Device 004: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 009: ID 06a5:d800 Divio Chicony TwinkleCam
Bus 001 Device 001: ID 0000:0000

Command "DMESG |grep VID*" wrote:

[17179569.184000] BIOS-provided physical RAM map:
[17179570.296000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.992000] ACPI: Core revision 20060707
[17179571.240000] Boot video device is 0000:00:02.0
[17179571.312000] pnp: PnP ACPI: found 11 devices
[17179571.312000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.312000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.712000] isapnp: No Plug & Play device found
[17179571.740000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.744000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[17179571.744000] mice: PS/2 mouse device common for all mice
[17179571.744000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.908000] ACPI: Transitioning device [C248] to D3
[17179572.908000] ACPI: Transitioning device [C248] to D3
[17179572.908000] ACPI: Transitioning device [C249] to D3
[17179572.908000] ACPI: Transitioning device [C249] to D3
[17179572.908000] ACPI: Transitioning device [C24A] to D3
[17179572.908000] ACPI: Transitioning device [C24A] to D3
[17179572.908000] ACPI: Transitioning device [C24B] to D3
[17179572.908000] ACPI: Transitioning device [C24B] to D3
[17179573.264000] ICH6: chipset revision 3
[17179574.140000] Uniform CD-ROM driver Revision: 3.20
[17179574.372000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.476000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.580000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179574.684000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179574.716000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179574.788000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179574.788000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.240000] usb 1-1: device not accepting address 2, error -71
[17179575.848000] usb 5-2: new high speed USB device using ehci_hcd and address 3
[17179576.324000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[17179576.676000] usb 5-2.1: new high speed USB device using ehci_hcd and address 4
[17179576.968000] usb 5-2.3: new low speed USB device using ehci_hcd and address 5
[17179577.268000] usb 5-2.4: new low speed USB device using ehci_hcd and address 6
[17179587.936000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179587.936000] usb-storage: device found at 4
[17179587.936000] usb-storage: waiting for device to settle before scanning
[17179587.964000] input: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:1d.7-2.4
[17179588.856000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179589.860000] lp: driver loaded but no devices found
[17179590.016000] Linux video capture interface: v1.00
[17179592.936000] usb-storage: device scan complete
[17179592.940000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179593.080000] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[17179593.084000] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[17179595.472000] wmi_add device=dff53400
[17179595.520000] ACPI: Video Device [C055] (multi-head: yes  rom: no  post: no)
[17179607.472000] Bluetooth: HCI device and connection manager initialized
[17179940.548000] usb 5-2.1: new high speed USB device using ehci_hcd and address 7
[17179940.640000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179940.640000] usb-storage: device found at 7
[17179940.640000] usb-storage: waiting for device to settle before scanning
[17179945.640000] usb-storage: device scan complete
[17179945.640000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179945.648000] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[17179945.652000] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[17180010.488000] drivers/media/video/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered

Command LSMOD wrote:
...
Module                 Size  Used by
spca5xx               637648  0
sn9c102                 94092  0
v4l2_common         17280  1 sn9c102
videodev                10752  2 spca5xx,sn9c102
video                     17540  0
usbhid                    45152  0
ehci_hcd                34696  0
uhci_hcd                24968  0
usbcore               134912  6 spca5xx,sn9c102,usbhid,ehci_hcd,uhci_hcd
...

If disconnect and connect webcam:

Disconnect

[17181773.024000] usb 1-1: USB disconnect, address 5

Connect and write command DMESG:

[17181780.824000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[17181780.972000] usb 1-1: configuration #1 chosen from 1 choice

Thank's for all answer...

---

### Post by Marian.nr on 2007-02-16
I uninstall spca5xx and gspca.
I install only gspcav1 for new kernel.

And the same result :(

Any help ?

---

### Post by kuddo on 2007-09-05
Where did u get you`re driver ? Because the Trust Company told me in my mail that they dont give suport and drivers for linux OS...and never will...

---

