---
title: "Dylan ekoore tablet [Accelerometer and backlight problems]"
date: 2012-09-09
forum: Hardware
---

### Post by raffarti on 2012-09-09
Hi everyone,
I don't now if that's the right place for this, anyway...

I've managed to install ubuntu 12.04 and then upgrade it to 12.10 and kernel to 3.6rc5 (kernel upgrade only accomplished to kill my webcam, I don't mind it anyway) on a Dylan ekoore tablet (NOTE the ubuntu ekoore LiveCD2.2 iso provaided doesn't boot, but works enought on VirtualBOX to peek though it).
All basic stuff works pretty good, I've find out drivers for wifi and multitouch.

What doesn't works are the accelerometer and the backlight control.

I found no way to control backlight, and it turns off only a few seconds after screen lock.

Unfortunatly, I can't find out the model of the accelerometer, though in ekoore live cd 'adxl34x' is setted as native instead of module (NOTE live cd works also on other ekoore tablets).
An interesting fact is that an input is sent to /dev/input/event2 when you rotate the tablet of 90°, but actually event2 is detected as 'AT Translated Set 2 Keyboard' and it also works when volume up and down and enter button on the top of the tablet are pushed. That result on Alt+Ctrl+Shift+F12 pressed when rotating the tablet, the input on event2 is the same for any angle.

Here I report lsinput:
```
   $ sudo lsinput 
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43841
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event3
   bustype : BUS_USB
   vendor  : 0xeef
   product : 0x736d
   version : 528
   name    : "eGalax Inc. USB TouchController"
   phys    : "usb-0000:00:1d.1-2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS

/dev/input/event4
   bustype : BUS_VIRTUAL
   vendor  : 0xeef
   product : 0x20
   version : 1
   name    : "eGalaxTouch Virtual Device for M"
   bits ev : EV_SYN EV_KEY EV_ABS

/dev/input/event5
   bustype : BUS_VIRTUAL
   vendor  : 0xeef
   product : 0x10
   version : 1
   name    : "eGalaxTouch Virtual Device for S"
   bits ev : EV_SYN EV_KEY EV_ABS

```and lshw -businfo:
 ```
 $ sudo lshw -businfo -sanitize
Bus info          Device     Class       Description
====================================================
                             system      ViewPad 97i (AZ01-H01)
                             bus         AN02-H02
                             memory      64KiB BIOS
cpu@0                        processor   Intel(R) Atom(TM) CPU N550   @ 1.50GHz
                             memory      48KiB L1 cache
                             memory      1MiB L2 cache
                             memory      2GiB System Memory
                             memory      2GiB SODIMM DDR2 Synchronous 667 MHz (1,5 ns)
                             memory      DIMM [empty]
pci@0000:00:00.0             bridge      Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
pci@0000:00:02.0             display     Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
pci@0000:00:02.1             display     Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
pci@0000:00:1b.0             multimedia  N10/ICH 7 Family High Definition Audio Controller
pci@0000:00:1d.0             bus         N10/ICH 7 Family USB UHCI Controller #1
pci@0000:00:1d.1             bus         N10/ICH 7 Family USB UHCI Controller #2
pci@0000:00:1d.2             bus         N10/ICH 7 Family USB UHCI Controller #3
pci@0000:00:1d.3             bus         N10/ICH 7 Family USB UHCI Controller #4
pci@0000:00:1d.7             bus         N10/ICH 7 Family USB2 EHCI Controller
pci@0000:00:1e.0             bridge      82801 Mobile PCI Bridge
pci@0000:00:1f.0             bridge      NM10 Family LPC Controller
pci@0000:00:1f.2             storage     N10/ICH7 Family SATA Controller [IDE mode]
pci@0000:00:1f.3             bus         N10/ICH 7 Family SMBus Controller
                  scsi1      storage     
scsi@1:0.0.0      /dev/sda   disk        32GB KingSpec KSD-SMP
scsi@1:0.0.0,1    /dev/sda1  volume      27GiB EXT4 volume
scsi@1:0.0.0,2    /dev/sda2  volume      2035MiB Extended partition
                  /dev/sda5  volume      2035MiB Linux swap / Solaris partition
usb@1:8           scsi2      storage     
scsi@2:0.0.0      /dev/sdb   disk        31GB SCSI Disk
scsi@2:0.0.0,1    /dev/sdb1  volume      29GiB Windows FAT volume
usb@1:3           wlan0      network     Wireless interface
```Any help is welcome.


[EDIT]
New ekoore live CD version come out (3.0) an the accelerometer seems to turn out to be some rough g-sensor (it just swap screen of 90° anti-clockwise and back normal randomly at any angle).
Live CD backlight control doesn't works all the same of 12.10.

---

### Post by bensz on 2012-12-23
Hello,
I just bought a dylan tablet, but with ubuntu 12.04, touchpanel does'nt work. How did  you make it work?

Thank you

Benoit szczygiel

---

