---
title: "Usbmem detected yesterday, but not today /dev/sda# gone missing"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by red_Marvin on 2006-04-04
I'm using a Sandisk Cruzer Micro 512MB to transfer firles between two computers.

Until today that is, Now it fails to automount, and it doesn't show up on the
computer:/// window. I can not mount it by cli either. On the other computer,
a server install, I mount it with *sudo mount -t vfat /dev/sda1 /media/usbdisk*
But also this fails, and /dev/sda1 doesn't exist at all.

During a conversation with dabaR in #ubuntu I did the following tests:
sudo fdisk -l
sudo fdisk -l /dev/sda
dmesg
ls /dev

I have't done anything unusual to the computer... ](*,) 

```
root@HERCULES:/home/leo# sudo fdisk -l
Disk /dev/hda: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början            Block    Id  System
/dev/hda1   *           1       19269   154778211   83  Linux
/dev/hda2           19270       19457     1510110    5  Utökad
/dev/hda5           19270       19457     1510078+  82  Linux växling / Solaris

Disk /dev/hdb: 80,0 GB, 80026361856 byte
255 huvuden, 63 sektorer/spår, 9729 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hdb1   *           1           1        8001   83  Linux
/dev/hdb2               2        9729    78140160   83  Linux


root@HERCULES:/home/leo# sudo fdisk -l /dev/sda 

<nothing>

root@HERCULES:/home/leo# dmesg
] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[dfffa800-dfffafff]  Max Packet=[2048]
[4294698.601000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0005ce0046151b7d]
[4294699.307000] Real Time Clock Driver v1.12
[4294699.397000] input: PC Speaker
[4294699.562000] Floppy drive(s): fd0 is 1.44M
[4294699.577000] FDC 0 is a post-1991 82077
[4294701.689000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[4294701.699000] NET: Registered protocol family 17
[4294703.022000] NET: Registered protocol family 10
[4294703.022000] Disabled Privacy Extensions on device c02eb280(lo)
[4294703.022000] IPv6 over IPv4 tunneling driver
[4294704.475000] ACPI: Power Button (FF) [PWRF]
[4294704.475000] ACPI: Power Button (CM) [PWRB]
[4294704.568000] ibm_acpi: ec object not found
[4294711.084000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294711.090000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294711.090000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294711.090000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294711.103000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294711.103000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294711.103000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294711.103000] [fglrx] AGP detected, AgpState   = 0x1f004e09 (hardware caps of chipset)
[4294711.103000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294711.103000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[4294711.103000] agpgart: SiS delay workaround: giving bridge time to recover.
[4294711.114000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[4294711.114000] [fglrx] AGP enabled,  AgpCommand = 0x1f004301 (selected caps)
[4294711.124000] [fglrx] free  AGP = 54800384
[4294711.124000] [fglrx] max   AGP = 54800384
[4294711.124000] [fglrx] free  LFB = 122679296
[4294711.124000] [fglrx] max   LFB = 122679296
[4294711.124000] [fglrx] free  Inv = 0
[4294711.124000] [fglrx] max   Inv = 0
[4294711.124000] [fglrx] total Inv = 0
[4294711.124000] [fglrx] total TIM = 0
[4294711.124000] [fglrx] total FB  = 0
[4294711.124000] [fglrx] total AGP = 16384
[4294713.098000] eth0: no IPv6 routers present
[4294713.747000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294713.747000] apm: overridden by ACPI.
[4294716.575000] Bluetooth: Core ver 2.7
[4294716.575000] NET: Registered protocol family 31
[4294716.575000] Bluetooth: HCI device and connection manager initialized
[4294716.575000] Bluetooth: HCI socket layer initialized
[4294716.622000] Bluetooth: L2CAP ver 2.7
[4294716.622000] Bluetooth: L2CAP socket layer initialized
[4294716.674000] Bluetooth: RFCOMM ver 1.5
[4294716.674000] Bluetooth: RFCOMM socket layer initialized
[4294716.674000] Bluetooth: RFCOMM TTY layer initialized
[4294872.793000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294872.793000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294872.887000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294872.887000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294873.002000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294873.002000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294873.088000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294873.088000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294873.203000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294873.203000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294873.285000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294873.285000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294873.416000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294873.416000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294873.482000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294873.482000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294873.679000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294873.679000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294873.753000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294873.753000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294874.536000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294874.536000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294875.542000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294875.542000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294893.779000] usb 4-1: new high speed USB device using ehci_hcd and address 3
[4295034.584000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295034.584000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295035.639000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295035.639000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295275.860000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295275.860000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295276.008000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295276.008000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295277.452000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295277.452000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295277.543000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295277.543000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295337.675000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295337.675000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295339.131000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295339.131000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295353.113000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295353.113000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295353.203000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295353.203000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295568.010000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295568.010000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295568.146000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295568.146000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295569.220000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295569.220000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295569.323000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295569.323000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295574.201000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295574.201000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295575.461000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295575.461000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295584.749000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295584.749000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295584.868000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295584.868000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295595.063000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295595.063000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295595.178000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295595.178000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295665.039000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295665.039000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295665.146000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295665.146000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295675.033000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295675.033000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295675.148000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295675.148000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295759.667000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295759.667000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295759.761000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295759.761000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295759.950000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295759.950000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295760.049000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295760.049000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295796.644000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295796.644000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295796.767000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295796.767000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295798.474000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295798.474000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295798.552000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295798.552000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295801.346000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295801.346000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295801.454000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295801.454000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295837.549000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295837.549000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295837.664000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295837.664000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296027.170000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296027.170000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296027.285000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296027.285000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296050.255000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296050.255000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296050.346000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296050.346000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296150.147000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296150.147000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296150.266000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296150.266000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296150.652000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296150.652000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296150.755000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296150.755000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296206.645000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296206.645000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296206.752000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296206.752000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296206.903000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296206.903000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296207.018000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296207.018000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296207.478000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296207.478000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296207.572000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296207.572000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296209.340000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296209.340000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296209.480000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296209.480000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296221.800000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296221.800000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296221.907000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296221.907000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296222.042000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296222.042000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296222.116000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296222.116000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296222.379000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296222.379000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296222.465000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296222.465000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296222.699000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296222.699000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296222.789000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296222.789000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296223.380000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296223.380000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296223.503000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296223.503000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.


root@HERCULES:/home/leo# ls /dev
acpi
adsp
agpgart
audio
cdrom
cdrom1
cdrw
console
core
dmmidi1
dri
dsp
dvd
evms
fb0
fd
fd0
full
hda
hda1
hda2
hda5
hdb
hdb1
hdb2
hdc
hdd
hpet
initctl
input
kmem
kmsg
log
loop
lp0
lvm
MAKEDEV
mapper
md0
md1
md10
md11
md12
md13
md14
md15
md16
md17
md18
md19
md2
md20
md21
md22
md23
md24
md3
md4
md5
md6
md7
md8
md9
mem
midi1
mixer
mixer1
net
null
port
ppp
psaux
ptmx
pts
ptya0
ptya1
ptya2
ptya3
ptya4
ptya5
ptya6
ptya7
ptya8
ptya9
ptyaa
ptyab
ptyac
ptyad
ptyae
ptyaf
ptyb0
ptyb1
ptyb2
ptyb3
ptyb4
ptyb5
ptyb6
ptyb7
ptyb8
ptyb9
ptyba
ptybb
ptybc
ptybd
ptybe
ptybf
ptyc0
ptyc1
ptyc2
ptyc3
ptyc4
ptyc5
ptyc6
ptyc7
ptyc8
ptyc9
ptyca
ptycb
ptycc
ptycd
ptyce
ptycf
ptyd0
ptyd1
ptyd2
ptyd3
ptyd4
ptyd5
ptyd6
ptyd7
ptyd8
ptyd9
ptyda
ptydb
ptydc
ptydd
ptyde
ptydf
ptye0
ptye1
ptye2
ptye3
ptye4
ptye5
ptye6
ptye7
ptye8
ptye9
ptyea
ptyeb
ptyec
ptyed
ptyee
ptyef
ptyp0
ptyp1
ptyp2
ptyp3
ptyp4
ptyp5
ptyp6
ptyp7
ptyp8
ptyp9
ptypa
ptypb
ptypc
ptypd
ptype
ptypf
ptyq0
ptyq1
ptyq2
ptyq3
ptyq4
ptyq5
ptyq6
ptyq7
ptyq8
ptyq9
ptyqa
ptyqb
ptyqc
ptyqd
ptyqe
ptyqf
ptyr0
ptyr1
ptyr2
ptyr3
ptyr4
ptyr5
ptyr6
ptyr7
ptyr8
ptyr9
ptyra
ptyrb
ptyrc
ptyrd
ptyre
ptyrf
ptys0
ptys1
ptys2
ptys3
ptys4
ptys5
ptys6
ptys7
ptys8
ptys9
ptysa
ptysb
ptysc
ptysd
ptyse
ptysf
ptyt0
ptyt1
ptyt2
ptyt3
ptyt4
ptyt5
ptyt6
ptyt7
ptyt8
ptyt9
ptyta
ptytb
ptytc
ptytd
ptyte
ptytf
ptyu0
ptyu1
ptyu2
ptyu3
ptyu4
ptyu5
ptyu6
ptyu7
ptyu8
ptyu9
ptyua
ptyub
ptyuc
ptyud
ptyue
ptyuf
ptyv0
ptyw0
ptyv1
ptyw1
ptyv2
ptyw2
ptyv3
ptyw3
ptyv4
ptyw4
ptyv5
ptyw5
ptyv6
ptyw6
ptyv7
ptyw7
ptyv8
ptyw8
ptyv9
ptyw9
ptyva
ptywa
ptyvb
ptywb
ptyvc
ptywc
ptyvd
ptywd
ptyve
ptywe
ptyvf
ptywf
ptyx0
ptyx1
ptyx2
ptyx3
ptyx4
ptyx5
ptyx6
ptyx7
ptyx8
ptyx9
ptyxa
ptyxb
ptyxc
ptyxd
ptyxe
ptyxf
ptyy0
ptyy1
ptyy2
ptyy3
ptyy4
ptyy5
ptyy6
ptyy7
ptyy8
ptyy9
ptyya
ptyyb
ptyyc
ptyyd
ptyye
ptyyf
ptyz0
ptyz1
ptyz2
ptyz3
ptyz4
ptyz5
ptyz6
ptyz7
ptyz8
ptyz9
ptyza
ptyzb
ptyzc
ptyzd
ptyze
ptyzf
ram0
ram1
ram10
ram11
ram12
ram13
ram14
ram15
ram2
ram3
ram4
ram5
ram6
ram7
ram8
ram9
random
rtc
shm
snd
sndstat
stderr
stdin
stdout
tty
tty0
tty1
tty10
tty11
tty12
tty13
tty14
tty15
tty16
tty17
tty18
tty19
tty2
tty20
tty21
tty22
tty23
tty24
tty25
tty26
tty27
tty28
tty29
tty3
tty30
tty31
tty32
tty33
tty34
tty35
tty36
tty37
tty38
tty39
tty4
tty40
tty41
tty42
tty43
tty44
tty45
tty46
tty47
tty48
tty49
tty5
tty50
tty51
tty52
tty53
tty54
tty55
tty56
tty57
tty58
tty59
tty6
tty60
tty61
tty62
tty63
tty7
tty8
tty9
ttya0
ttya1
ttya2
ttya3
ttya4
ttya5
ttya6
ttya7
ttya8
ttya9
ttyaa
ttyab
ttyac
ttyad
ttyae
ttyaf
ttyb0
ttyb1
ttyb2
ttyb3
ttyb4
ttyb5
ttyb6
ttyb7
ttyb8
ttyb9
ttyba
ttybb
ttybc
ttybd
ttybe
ttybf
ttyc0
ttyc1
ttyc2
ttyc3
ttyc4
ttyc5
ttyc6
ttyc7
ttyc8
ttyc9
ttyca
ttycb
ttycc
ttycd
ttyce
ttycf
ttyd0
ttyd1
ttyd2
ttyd3
ttyd4
ttyd5
ttyd6
ttyd7
ttyd8
ttyd9
ttyda
ttydb
ttydc
ttydd
ttyde
ttydf
ttye0
ttye1
ttye2
ttye3
ttye4
ttye5
ttye6
ttye7
ttye8
ttye9
ttyea
ttyeb
ttyec
ttyed
ttyee
ttyef
ttyp0
ttyp1
ttyp2
ttyp3
ttyp4
ttyp5
ttyp6
ttyp7
ttyp8
ttyp9
ttypa
ttypb
ttypc
ttypd
ttype
ttypf
ttyq0
ttyq1
ttyq2
ttyq3
ttyq4
ttyq5
ttyq6
ttyq7
ttyq8
ttyq9
ttyqa
ttyqb
ttyqc
ttyqd
ttyqe
ttyqf
ttyr0
ttyr1
ttyr2
ttyr3
ttyr4
ttyr5
ttyr6
ttyr7
ttyr8
ttyr9
ttyra
ttyrb
ttyrc
ttyrd
ttyre
ttyrf
ttys0
ttyS0
ttys1
ttyS1
ttyS10
ttyS11
ttyS12
ttyS13
ttyS14
ttyS15
ttyS16
ttyS17
ttyS18
ttyS19
ttys2
ttyS2
ttyS20
ttyS21
ttyS22
ttyS23
ttyS24
ttyS25
ttyS26
ttyS27
ttyS28
ttyS29
ttys3
ttyS3
ttyS30
ttyS31
ttyS32
ttyS33
ttyS34
ttyS35
ttyS36
ttyS37
ttyS38
ttyS39
ttys4
ttyS4
ttyS40
ttyS41
ttyS42
ttyS43
ttyS44
ttyS45
ttyS46
ttyS47
ttyS48
ttyS49
ttys5
ttyS5
ttyS50
ttyS51
ttyS52
ttyS53
ttys6
ttyS6
ttys7
ttyS7
ttys8
ttyS8
ttys9
ttyS9
ttysa
ttysb
ttysc
ttysd
ttyse
ttysf
ttyt0
ttyt1
ttyt2
ttyt3
ttyt4
ttyt5
ttyt6
ttyt7
ttyt8
ttyt9
ttyta
ttytb
ttytc
ttytd
ttyte
ttytf
ttyu0
ttyu1
ttyu2
ttyu3
ttyu4
ttyu5
ttyu6
ttyu7
ttyu8
ttyu9
ttyua
ttyub
ttyuc
ttyud
ttyue
ttyuf
ttyv0
ttyw0
ttyv1
ttyw1
ttyv2
ttyw2
ttyv3
ttyw3
ttyv4
ttyw4
ttyv5
ttyw5
ttyv6
ttyw6
ttyv7
ttyw7
ttyv8
ttyw8
ttyv9
ttyw9
ttyva
ttywa
ttyvb
ttywb
ttyvc
ttywc
ttyvd
ttywd
ttyve
ttywe
ttyvf
ttywf
ttyx0
ttyx1
ttyx2
ttyx3
ttyx4
ttyx5
ttyx6
ttyx7
ttyx8
ttyx9
ttyxa
ttyxb
ttyxc
ttyxd
ttyxe
ttyxf
ttyy0
ttyy1
ttyy2
ttyy3
ttyy4
ttyy5
ttyy6
ttyy7
ttyy8
ttyy9
ttyya
ttyyb
ttyyc
ttyyd
ttyye
ttyyf
ttyz0
ttyz1
ttyz2
ttyz3
ttyz4
ttyz5
ttyz6
ttyz7
ttyz8
ttyz9
ttyza
ttyzb
ttyzc
ttyzd
ttyze
ttyzf
urandom
usplash_fifo
vcs
vcs1
vcs2
vcs3
vcs4
vcs5
vcs6
vcs7
vcsa
vcsa1
vcsa2
vcsa3
vcsa4
vcsa5
vcsa6
vcsa7
xconsole
zero

```

---

### Post by red_Marvin on 2006-04-11
I'm bumping this in hope that somebody who might have the answer, missed
the thread before will see it now. I will not do it again.
Sorry.

Anyway, my dad said something about "supermount" or somesuch that might
be useful to look into, but otherwise I see no solution but reinstalling.:-k

---

