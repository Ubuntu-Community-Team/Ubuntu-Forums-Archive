---
title: "unable to open an initial console"
date: 2008-08-22
forum: General Help
---

### Post by ranjithmrk on 2008-08-22
i am trying to mount a jffs2 filesystem. 
I enabled the mtd feature of the kernel in a way that it creates a 
bootloader and filesystem partition in mtd0 and mtd1. I have loaded the 
jffs2 image and copied it to a random address in the dataflash 0x40400000. 
When the kernel booted up.. it went on until it displayed :

*****************************************************************
Warning: unable to open an initial console.

Kernel panic - not syncing: No init found.  Try passing init= 
option to kernel.

*****************************************************************

I looked at my filesystem and it contained /dev/console. I do not know what 
the problem is.
Please help me.

Regards
Ranjith

Here is the console display:

Starting kernel ...

Uncompressing 
Linux......................................................................................... 
done, booting the kernel.
Linux version 2.6.15.4 (root at dhcp-938-1) (gcc version 4.1.0 20060304 
(TimeSys 4.1.0-3)) #23 PREEMPT Wed Nov 29 17:22:52 EST 2006
CPU: ARM926EJ-Sid(wb) [41069265] revision 5 (ARMv5TEJ)
Machine: ATMEL AT91SAM9260
Memory policy: ECC disabled, Data cache writeback
BUG: mapping for 0xfffa4000 at 0xfeda6000 overlaps vmalloc space
CPU0: D VIVT write-back cache
CPU0: I cache: 8192 bytes, associativity 4, 32 byte lines, 64 sets
CPU0: D cache: 8192 bytes, associativity 4, 32 byte lines, 64 sets
Built 1 zonelists
Kernel command line: console=ttyS0,115200n8 rw ip=off root=/dev/mtdblock1 
rootfstype=jffs2 init=linuxrc mem=32M
set_irq_chained_handler 2
set_irq_chained_handler 3
set_irq_chained_handler 4
AT91: 96 gpio irqs in 3 banks
PID hash table entries: 256 (order: 8, 4096 bytes)
Console: colour dummy device 80x30
Dentry cache hash table entries: 8192 (order: 3, 32768 bytes)
Inode-cache hash table entries: 4096 (order: 2, 16384 bytes)
Memory: 32MB = 32MB total
Memory: 29532KB available (2312K code, 429K data, 108K init)
Mount-cache hash table entries: 512
CPU: Testing write buffer coherency: ok
NET: Registered protocol family 16
SCSI subsystem initialized
usbcore: registered new driver usbfs
usbcore: registered new driver hub
NetWinder Floating Point Emulator V0.97 (double precision)
JFFS2 version 2.2. (NAND) (C) 2001-2003 Red Hat, Inc.
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
ttyS0 at MMIO 0xfffff200 (irq = 1) is a AT91_SERIAL
ttyS1 at MMIO 0xfffb0000 (irq = 6) is a AT91_SERIAL
ttyS2 at MMIO 0xfffb4000 (irq = 7) is a AT91_SERIAL
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
eth0: ATMEL MACB rev 1.12 at 0xfffc4000 irq 21
DataFlash Driver init<5>usbmon: debugfs is not available
usb-ohci usb-ohci.0: AT91SAM9260 OHCI
usb-ohci usb-ohci.0: new USB bus registered, assigned bus number 1
usb-ohci usb-ohci.0: irq 20, io mem 0x00500000
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
Initializing USB Mass Storage driver...
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
gpio_irq_unmask 101 fee01800
at91_udc version 8 March 2005
udc: at91_udc version 8 March 2005
usb0: Ethernet Gadget, version: May Day 2005
usb0: using at91_udc, OUT ep2 IN ep1 STATUS ep4
usb0: MAC c2:01:e6:99:21:62
usb0: HOST MAC 4a:25:fa:8e:cd:09
mice: PS/2 mouse device common for all mice
AT91 I2C TWI_CWGR 0006DCD8
spi spi.0: AT91 SPI Interface at 0xfffc8000 irq : 12
<7>spi_adapter spi-0: client [dataflash] attached to adapter
spi_adapter spi-0: Atmel AT45DB642 detected [spi0] (8650752 bytes)
Creating 2 MTD partitions on "Atmel AT45DB642":
0x00000000-0x00039c00 : "bootloader"
rfd_ftl: no RFD magic found in 'bootloader'
0x00039c00-0x00840000 : "filesystem"
spi spi.1: AT91 SPI Interface at 0xfffcc000 irq : 13
<7>spi_adapter spi-1: registered as adapter #1
NET: Registered protocol family 2
IP route cache hash table entries: 512 (order: -1, 2048 bytes)
TCP established hash table entries: 2048 (order: 1, 8192 bytes)
TCP bind hash table entries: 2048 (order: 1, 8192 bytes)
TCP: Hash tables configured (established 2048 bind 2048)
TCP reno registered
TCP bic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
VFS: Mounted root (jffs2 filesystem).
Freeing init memory: 108K
Warning: unable to open an initial console.
Kernel panic - not syncing: No init found.  Try passing init= option to 
kernel.

---

