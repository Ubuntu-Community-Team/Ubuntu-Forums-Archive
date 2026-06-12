---
title: "Logitech 961310-0403 QuickCam?"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by drews_blunted on 2005-06-07
Alright so ive been looking at this cool webcam and im woundering if it will work well in linux? Does anyone know how well logitech webcams work in linux?

Logitech 961310-0403 QuickCam Orbit 1.3MP Effective Pixels USB2.0 Interface WebCam - Retail 

[http://www.newegg.com/Product/Product.asp?item=N82E16830108112](http://www.newegg.com/Product/Product.asp?item=N82E16830108112)

---

### Post by Gouchi on 2005-06-07
It seems ok  ;-) 

Check [this](http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC)

to try your webcam :

```
gst-launch-0.8 v4lsrc ! xvimagesink 
or 
gst-launch-0.8 v4l2src ! xvimagesink

```

Otherwise, lauch gnomemeeting.

---

### Post by drews_blunted on 2005-06-09
Ok, i have just plugged in the webcam! the red light is on so i know its atleast getting power! the command you gave me simply brought up a green screen with some fuzz, i do not think ubuntu has magicaly detected it and done everything for me! Is there a easy way to get a webcam working such as this one? and if so what do you do to go about setting up a wecam!

---

### Post by drews_blunted on 2005-06-09
a quick listing of my usb ports showed this!
I have a logitech usb gamepad also, so im assuming linux knows both devices are there.

Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:c216 Logitech, Inc.
Bus 002 Device 003: ID 046d:08b5 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by drews_blunted on 2005-06-09
Ok, some search on google has lead me to a program called OrbitCam its suposed to work with my quickcam orbit and philips webcams. The program didnt bring me up and liv video feeds or anything to let me know how to or even if my cam is working but it did detect the cam and give me this information.

**Device Capabilites**
Name:Logitech QuickCam Orbit
Type:1
Channels:1
Audio Channels:0
Max Width:640
Min Width:160
Max Height:480
Min Height:120
**Device Picture**
Brightness:31744
Hue:65535
Colour:32768
Contrast:32768
Whiteness:49152
Depth:24
Palette:15
Palette: YUV 4:2:0 Planar
**Device Window**
x,y:(0,0)
Width,Height:(160,120)
**Device Memory**
Size:921600
Frames:2
Frame[0]:(nil)
Frame[1]:0x70800

---

### Post by Gouchi on 2005-06-10
And Gnomemeeting works ?

If not try to see if webcam modules are loaded :

```
lsmod | grep pwc
``` 

and check output from dmesg when you plug the webcam.

```
dmesg
``` 

Try this [wiki](http://www.lavrsen.dk/twiki/bin/view/PWC/InstallationStandAloneModuleKernel2x6) , to update your module pwc if it's not work.

---

### Post by drews_blunted on 2005-06-12
lsmod | grep pwc

pwc                    78196  0
usbcore               107384  7 usbhid,snd_usb_audio,snd_usb_lib,pwc,ehci_hcd,uhci_hcd
videodev                9728  2 pwc,bttv


dmesg

*0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 13 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
audit: initializing netlink socket (disabled)
audit(1118424053.930:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 PS2K PS2M UAR2 UAR1 AC97 USB1 USB2 USB3 USB4 EHCI PWRB SLPB
ACPI: (supports S0 S1 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:0f.1
ACPI: PCI interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
    ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: WDC WD1200JB-00FUA0, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: SONY DVD-ROM DDU1611, ATAPI CD/DVD-ROM drive
hdd: SONY DVD RW DW-D26A, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 40X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Linux agpgart interface v0.100 (c) Dave Jones
ts: Compaq touchscreen protocol output
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
agpgart: Detected AGP bridge 0
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: AGP aperture is 64M @ 0xf8000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:00:07.0[A] -> GSI 16 (level, low) -> IRQ 16
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[f7a00000-f7a007ff]  Max Packet=[2048]
libata version 1.10 loaded.
sata_promise version 1.01
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 18
sata_promise PATA port found
ata1: SATA max UDMA/133 cmd 0xF8A94200 ctl 0xF8A94238 bmdma 0x0 irq 18
ata2: SATA max UDMA/133 cmd 0xF8A94280 ctl 0xF8A942B8 bmdma 0x0 irq 18
ata3: PATA max UDMA/133 cmd 0xF8A94300 ctl 0xF8A94338 bmdma 0x0 irq 18
ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
ata1: dev 0 ATA, max UDMA/133, 390721968 sectors: lba48
ata1: dev 0 configured for UDMA/133
scsi0 : sata_promise
ata2: no device found (phy stat 00000000)
scsi1 : sata_promise
ATA: abnormal status 0x8 on port 0xF8A9431C
ata3: disabling port
scsi2 : sata_promise
  Vendor: ATA       Model: ST3200822AS       Rev: 3.01
  Type:   Direct-Access                      ANSI SCSI revision: 05
Linux video capture interface: v1.00
SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: unknown partition table
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000a5669b]
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ 16
bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 16, latency: 64, mmio: 0xf2f00000
bttv0: detected: ATI TV Wonder/VE [card=64], PCI subsystem ID is 1002:0003
bttv0: using: ATI TV-Wonder VE [card=64,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
bttv0: using tuner=19
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
bttv0: i2c: checking for TDA9887 @ 0x86... not found
tuner: chip found at addr 0xc0 i2c-bus bt878 #0 [sw]
tuner: type set to 19 (Temic PAL* auto (4006 FN5)) by bt878 #0 [sw]
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: PLL: 28636363 => 35468950 .. ok
ACPI: PCI interrupt 0000:00:09.1[A] -> GSI 16 (level, low) -> IRQ 16
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
sk98lin: Asus mainboard with buggy VPD? Correcting data.
eth0: Yukon Gigabit Ethernet 10/100/1000Base-T Adapter
      PrefPort:A  RlmtMode:Check Link State
sata_via version 1.1
ACPI: PCI interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
sata_via(0000:00:0f.0): routed to hard irq line 4
ata4: SATA max UDMA/133 cmd 0xE800 ctl 0xE402 bmdma 0xD400 irq 20
ata5: SATA max UDMA/133 cmd 0xE000 ctl 0xD802 bmdma 0xD408 irq 20
ata4: no device found (phy stat 00000000)
scsi3 : sata_via
ata5: no device found (phy stat 00000000)
scsi4 : sata_via
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0xb400
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0xb800
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
uhci_hcd 0000:00:10.2: irq 21, io base 0xc000
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
uhci_hcd 0000:00:10.3: irq 21, io base 0xc400
uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 2-1: new full speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.4: irq 21, pci mem 0xf7f00000
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
NET: Registered protocol family 17
ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:11.5 to 64
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
usb 2-1: new full speed USB device using uhci_hcd and address 3
eth0: network connection up using port A
    speed:           10
    autonegotiation: yes
    duplex mode:     half
    flowctrl:        none
    irq moderation:  disabled
    scatter-gather:  enabled
pwc Philips webcam module version 10.0.6-unofficial loaded.
pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
pwc Trace options: 0x00a1
usb 2-2: new low speed USB device using uhci_hcd and address 4
pwc Logitech QuickCam Orbit/Sphere USB webcam detected.
pwc Registered as /dev/video1.
usbcore: registered new driver Philips webcam
usbcore: registered new driver snd-usb-audio
usbcore: registered new driver hiddev
input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:10.1-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
pwc Failed to set LED on/off time.
pwc set_video_mode(176x144 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.00.09e)
powernow-k8: BIOS error - no PSB
eth0: no IPv6 routers present
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
pwc set_video_mode(160x120 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
cdrom: This disc doesn't have any tracks I recognize!
usb 2-1: USB disconnect, address 3
usb 2-1: new full speed USB device using uhci_hcd and address 5
pwc Logitech QuickCam Orbit/Sphere USB webcam detected.
pwc Registered as /dev/video1.
cdrom: This disc doesn't have any tracks I recognize!
EXT2-fs warning (device sda): ext2_fill_super: mounting ext3 filesystem as ext2

EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
pwc Failed to set LED on/off time.
pwc set_video_mode(176x144 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
pwc set_video_mode(160x120 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
pwc set_video_mode(160x120 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
pwc set_video_mode(160x120 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
pwc set_video_mode(160x120 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
pwc set_video_mode(160x120 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
pwc set_video_mode(160x120 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
pwc set_video_mode(160x120 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
pwc set_video_mode(160x120 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
pwc set_video_mode(160x120 @ 10, palette 15).
pwc decode_size = 1.
pwc Using alternate setting 1.
bttv0: timeout: drop=69 irq=11610/10888453, risc=1dad502c, bits: HSYNC OFLOW FDSR
bttv0: reset, reinitialize
bttv0: PLL: 28636363 => 35468950 . ok
cdrom: This disc doesn't have any tracks I recognize!
ibm_acpi: ec object not found

---

### Post by Gouchi on 2005-06-12
it seems to be ok.

Your dev node  is **/dev/video1**, so try with GnomeMeeting with /dev/video1.

or with Gstreamer Launch :
```
gst-launch-0.8 v4lsrc device=/dev/video1 ! xvimagesink 
or
gst-launch-0.8 v4l2src device=/dev/video1 ! xvimagesink 

``` 

Before it didn't work because you have a TV Card using /dev/video0.

---

