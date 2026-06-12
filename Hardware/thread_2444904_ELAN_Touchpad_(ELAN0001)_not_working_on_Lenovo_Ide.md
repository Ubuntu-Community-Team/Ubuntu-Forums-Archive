---
title: "ELAN Touchpad (ELAN0001) not working on Lenovo Ideapad 5 15 (AMD4600u/Ryzen5)"
date: 2020-06-05
forum: Hardware
---

### Post by jopof on 2020-06-05
Hi all,

i recently installed Ubuntu 20.04 on my new Lenovo Ideapad 5 15 (AMD).
Now, i cannot get the touchpad working. Everythings works smoothly on Win10. I already tried several things like instaling packages, recompiling the kernel (updating mainstream and making sure i2c is supported).

**uname -r:**
Linux 5.7.0-050700-generic #202005312130 SMP Mon Jun 1 01:33:12 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

**lspci:**
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Renoir IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe GPP Bridge
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe GPP Bridge
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 51)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 7
01:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a)
02:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Renoir (rev ce)
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1637
03:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
03:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir USB 3.1
03:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir USB 3.1
03:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 01)
03:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
04:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 81)
04:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 81)


**dmesg (why is the touchpad shown as touchscreen (i don't have one)?):**
[    0.593826] i2c /dev entries driver
[    0.597751] elants_i2c i2c-ELAN0001:00: supply vcc33 not found, using dummy regulator
[    0.597765] elants_i2c i2c-ELAN0001:00: supply vccio not found, using dummy regulator
[    0.598190] elants_i2c i2c-ELAN0001:00: elants_i2c_send failed (77 77 77 77): -121
[    0.598214] elants_i2c i2c-ELAN0001:00: software reset failed: -121
[    0.598553] elants_i2c i2c-ELAN0001:00: elants_i2c_send failed (77 77 77 77): -121
[    0.598573] elants_i2c i2c-ELAN0001:00: software reset failed: -121
[    0.598900] elants_i2c i2c-ELAN0001:00: elants_i2c_send failed (77 77 77 77): -121
[    0.598921] elants_i2c i2c-ELAN0001:00: software reset failed: -121
[    0.599243] elants_i2c i2c-ELAN0001:00: elants_i2c_send failed (4d 61 69 6e): -121
[    0.599264] elants_i2c i2c-ELAN0001:00: boot failed: -121
[    0.656710] elants_i2c i2c-ELAN0001:00: invalid 'hello' packet: 00 00 ff ff
[    1.627998] elants_i2c i2c-ELAN0001:00: Failed to read fw id: -121
[    1.628163] input: Elan *Touchscreen* as /devices/platform/AMDI0010:01/i2c-1/i2c-ELAN0001:00/input/input4




[B]xinput:
[/B]&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M705                               id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech K750                               id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C             id=9    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Logitech K750                               id=14    [slave  keyboard (3)]

[B]
acpidump | grep -C3 ELAN:[/B]
    91E0: 70 0D 43 52 51 30 33 35 30 00 5F 48 49 44 A0 17  p.CRQ0350._HID..
    91F0: 93 54 50 54 59 0A 05 70 0D 46 54 43 53 31 30 30  .TPTY..p.FTCS100
    9200: 33 00 5F 48 49 44 A0 17 93 54 50 54 59 0A 01 70  3._HID...TPTY..p
    9210: 0D 45 4C 41 4E 30 30 30 31 00 5F 48 49 44 A0 17  .**ELAN0001**._HID..
    9220: 93 54 50 54 59 0A 02 70 0D 53 59 4E 41 30 30 30  .TPTY..p.SYNA000
    9230: 31 00 5F 48 49 44 A4 00 14 49 06 5F 44 53 4D 0C  1._HID...I._DSM.
    9240: A0 4C 05 93 68 11 13 0A 10 F7 F6 DF 3C 67 42 55  .L..h.......<gBU


**Whenever i swipe over the touchpad, these kind of events occur:**
[  170.805570] elants_i2c i2c-ELAN0001:00: unknown packet 0e 00 04 03
[  170.812010] elants_i2c i2c-ELAN0001:00: unknown packet 0e 00 04 03
[  170.818804] elants_i2c i2c-ELAN0001:00: unknown packet 0e 00 04 03
[  170.826209] elants_i2c i2c-ELAN0001:00: unknown packet 0e 00 04 03
[  170.832958] elants_i2c i2c-ELAN0001:00: unknown packet 0e 00 04 03
[  170.839848] elants_i2c i2c-ELAN0001:00: unknown packet 0e 00 04 03
[  170.847425] elants_i2c i2c-ELAN0001:00: unknown packet 0e 00 04 03
[  170.854092] elants_i2c i2c-ELAN0001:00: unknown packet 0e 00 04 01

**cat /sys/bus/i2c/devices/*/name:**
Synopsys DesignWare I2C adapter
Synopsys DesignWare I2C adapter
SMBus PIIX4 adapter port 0 at 0b00
SMBus PIIX4 adapter port 2 at 0b00
AMDGPU DM i2c hw bus 0
AMDGPU DM i2c hw bus 1
AMDGPU DM i2c hw bus 2
AMDGPU DM aux hw bus 0
AMDGPU DM aux hw bus 2
ELAN0001:00

**/proc/bus/input/devices (again shown as touchscreen):**
I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="Elan Touchscreen"
P: Phys=
S: Sysfs=/devices/platform/AMDI0010:01/i2c-1/i2c-ELAN0001:00/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=2
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=6e1800001000003

**ls -l /sys/dev/*/*/device/driver:**
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/10:224/device/driver -> ../../../../bus/acpi/drivers/tpm_crb
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/180:0/device/driver -> ../../../../../../../bus/usb/drivers/usbhid
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/189:0/driver -> ../../../../../bus/usb/drivers/usb
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/189:128/driver -> ../../../../../bus/usb/drivers/usb
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/189:1/driver -> ../../../../../../bus/usb/drivers/usb
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/189:256/driver -> ../../../../../bus/usb/drivers/usb
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/189:257/driver -> ../../../../../../bus/usb/drivers/usb
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/189:258/driver -> ../../../../../../bus/usb/drivers/usb
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/189:384/driver -> ../../../../../bus/usb/drivers/usb
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/226:0/device/driver -> ../../../../bus/pci/drivers/amdgpu
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/226:128/device/driver -> ../../../../bus/pci/drivers/amdgpu
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/239:0/device/driver -> ../../../../bus/pci/drivers/nvme
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/240:0/device/driver -> ../../../../../../../../bus/hid/drivers/logitech-djreceiver
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/240:1/device/driver -> ../../../../../../../../../bus/hid/drivers/logitech-hidpp-device
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/240:2/device/driver -> ../../../../../../../../../bus/hid/drivers/logitech-hidpp-device
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/248:0/device/driver -> ../../../bus/pnp/drivers/rtc_cmos
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/253:65536/device/driver -> ../../../../bus/acpi/drivers/tpm_crb
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/29:0/device/driver -> ../../../../bus/pci/drivers/amdgpu
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:64/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:65/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:66/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:67/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:68/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:69/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:70/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:71/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:72/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:73/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:74/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:75/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:76/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:77/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:78/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:79/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:80/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:81/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:82/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:83/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:84/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:85/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:86/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:87/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:88/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:89/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:90/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:91/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:92/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:93/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:94/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/4:95/device/driver -> ../../../bus/platform/drivers/serial8250
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/81:0/device/driver -> ../../../../../../../bus/usb/drivers/uvcvideo
lrwxrwxrwx 1 root root 0 Jun  6 01:16 /sys/dev/char/81:1/device/driver -> ../../../../../../../bus/usb/drivers/uvcvideo



Any help is appreciated.

Thanks and regards.

---

### Post by jopof on 2020-06-06
Update:
What i have found so far is, that probably must have something to do with the kernel. Actually the touchpad is being recognized correctly by another distro (live cd, kernel 5.5). There the touchpad is not mistaken as touchscreen.

Rushing through lsmod tells me that something may be missing or the hardware is not connected (and thus initialized/recognized) correctly?
[COLOR=#000000]i2c_designware_platform 16384 0[/COLOR]
[COLOR=#000000]i2c_designware_core 24576 1 i2c_designware_platform[/COLOR]

dmesg | grep ELA
[    1.376653] i2c_hid i2c-ELAN0001:00: i2c-ELAN0001:00 supply vdd not found, using dummy regulator
[    1.376666] i2c_hid i2c-ELAN0001:00: i2c-ELAN0001:00 supply vddl not found, using dummy regulator
[    1.417107] input: ELAN0001:00 04F3:3140 Mouse as /devices/platform/AMDI0010:01/i2c-1/i2c-ELAN0001:00/0018:04F3:3140.0001/input/input5
[    1.417146] input: ELAN0001:00 04F3:3140 Touchpad as /devices/platform/AMDI0010:01/i2c-1/i2c-ELAN0001:00/0018:04F3:3140.0001/input/input6
[    1.417180] hid-generic 0018:04F3:3140.0001: input,hidraw0: I2C HID v1.00 Mouse [ELAN0001:00 04F3:3140] on i2c-ELAN0001:00
[    6.927738] input: ELAN0001:00 04F3:3140 Mouse as /devices/platform/AMDI0010:01/i2c-1/i2c-ELAN0001:00/0018:04F3:3140.0001/input/input9
[    6.927894] input: ELAN0001:00 04F3:3140 Touchpad as /devices/platform/AMDI0010:01/i2c-1/i2c-ELAN0001:00/0018:04F3:3140.0001/input/input10
[    6.928007] hid-multitouch 0018:04F3:3140.0001: input,hidraw0: I2C HID v1.00 Mouse [ELAN0001:00 04F3:3140] on i2c-ELAN0001:00


xinput
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; ELAN0001:00 04F3:3140 Touchpad            id=11   [slave  pointer  (2)]
&#9116;   &#8627; ELAN0001:00 04F3:3140 Mouse               id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C           id=9    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                     id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]


input devices
I: Bus=0018 Vendor=04f3 Product=3140 Version=0100
N: Name="ELAN0001:00 04F3:3140 Mouse"
P: Phys=i2c-ELAN0001:00
S: Sysfs=/devices/platform/AMDI0010:01/i2c-1/i2c-ELAN0001:00/0018:04F3:3140.0001/input/input9
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=0
B: EV=17
B: KEY=30000 0 0 0 0
B: REL=1943
B: MSC=10


I: Bus=0018 Vendor=04f3 Product=3140 Version=0100
N: Name="ELAN0001:00 04F3:3140 Touchpad"
P: Phys=i2c-ELAN0001:00
S: Sysfs=/devices/platform/AMDI0010:01/i2c-1/i2c-ELAN0001:00/0018:04F3:3140.0001/input/input10
U: Uniq=
H: Handlers=mouse1 event8 
B: PROP=5
B: EV=1b
B: KEY=e520 10000 0 0 0 0
B: ABS=2e0800000000003
B: MSC=20


acpidump | grep -C3 ELAN
    91E0: 70 0D 43 52 51 30 33 35 30 00 5F 48 49 44 A0 17  p.CRQ0350._HID..
    91F0: 93 54 50 54 59 0A 05 70 0D 46 54 43 53 31 30 30  .TPTY..p.FTCS100
    9200: 33 00 5F 48 49 44 A0 17 93 54 50 54 59 0A 01 70  3._HID...TPTY..p
    9210: 0D 45 4C 41 4E 30 30 30 31 00 5F 48 49 44 A0 17  .ELAN0001._HID..
    9220: 93 54 50 54 59 0A 02 70 0D 53 59 4E 41 30 30 30  .TPTY..p.SYNA000
    9230: 31 00 5F 48 49 44 A4 00 14 49 06 5F 44 53 4D 0C  1._HID...I._DSM.
    9240: A0 4C 05 93 68 11 13 0A 10 F7 F6 DF 3C 67 42 55  .L..h.......<gBU


cat /sys/bus/i2c/devices/*/name
Synopsys DesignWare I2C adapter
Synopsys DesignWare I2C adapter
SMBus PIIX4 adapter port 0 at 0b00
SMBus PIIX4 adapter port 2 at 0b00
ELAN0001:00


lsmod | grep i2c
i2c_algo_bit           16384  1 amdgpu
i2c_piix4              28672  0
i2c_hid                32768  0
hid                   147456  3 i2c_hid,hid_multitouch,hid_generic
i2c_designware_platform    16384  0
i2c_designware_core    24576  1 i2c_designware_platform




rfkill
ID TYPE      DEVICE                 SOFT      HARD
 0 wlan      ideapad_wlan      unblocked unblocked
 1 bluetooth ideapad_bluetooth   blocked unblocked
 2 bluetooth hci0                blocked unblocked
 3 wlan      phy0              unblocked unblocked

---

### Post by ludovic50750 on 2020-06-11
Hi
I have the same problem than you, and probably the same touchpad !
You said that another distro worked live ? 
Can you tell me which one ? 
I could have a look at both kernels compilation parameters and see what's different !

Regards

---

