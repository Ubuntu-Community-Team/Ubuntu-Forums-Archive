---
title: "Kernel panic - not syncing: No init found.  Try passing init= option to kernel."
date: 2008-08-22
forum: General Help
---

### Post by ranjithmrk on 2008-08-22
hi

I compiled my kernel and mounted my filesystem(ext2). After loading the kernal and file systems images into board and started the booting the following error is comming.

................................................................................................................

Warning: unable to open an initial console.

Kernel panic - not syncing: No init found. Try passing init= 

option to kernel.

................................................................................................................

I looked at my filesystem and it contained /dev/console.Please help me.



Regards

kumar



the following data is displayed in the console.

U-Boot 1.1.5 (Dec 14 2006 - 16:11:00)



DRAM: 64 MB

NAND: NAND device: Manufacturer ID: 0xec, Chip ID: 0xda (<NULL> NAND 256MiB 3,3

V 8-bit)

256 MiB

DataFlash:AT45DB642

Nb pages: 8192

Page Size: 1056

Size= 8650752 bytes

Logical address: 0xC0000000

Area 0: C0000000 to C0003FFF (RO)

Area 1: C0004000 to C0007FFF

Area 2: C0008000 to C0037FFF (RO)

Area 3: C0038000 to C083FFFF

In: serial

Out: serial

Err: serial

DM9161A PHY Detected

No link

MAC: error during RMII initialization

Hit any key to stop autoboot: 0

## Booting image at 21400000 ...

Image Name: M9X_OS

Image Type: ARM Linux Kernel Image (gzip compressed)

Data Size: 1174826 Bytes = 1.1 MB

Load Address: 20008000

Entry Point: 20008000

Verifying Checksum ... OK

Uncompressing Kernel Image ... OK



Starting kernel ...



Linux version 2.6.20.11 (root@localhost.localdomain) (gcc version 4.1.1) #1 Mon

Jul 7 10:52:05 IST 2008

CPU: ARM926EJ-S [41069265] revision 5 (ARMv5TEJ), cr=00053177

Machine: Atmel AT91SAM9263-EK

Ignoring unrecognised tag 0x54410008

Memory policy: ECC disabled, Data cache writeback

Clocks: CPU 199 MHz, master 99 MHz, main 16.367 MHz

CPU0: D VIVT write-back cache

CPU0: I cache: 16384 bytes, associativity 4, 32 byte lines, 128 sets

CPU0: D cache: 16384 bytes, associativity 4, 32 byte lines, 128 sets

Built 1 zonelists. Total pages: 16256

Kernel command line: mem=64M console=ttyS0,115200 initrd=0x21100000,3145728 root

=/dev/ram0 rw

AT91: 160 gpio irqs in 5 banks

PID hash table entries: 256 (order: 8, 1024 bytes)

Console: colour dummy device 80x30

Dentry cache hash table entries: 8192 (order: 3, 32768 bytes)

Inode-cache hash table entries: 4096 (order: 2, 16384 bytes)

Memory: 64MB = 64MB total

Memory: 59312KB available (2148K code, 231K data, 100K init)

Mount-cache hash table entries: 512

CPU: Testing write buffer coherency: ok

NET: Registered protocol family 16

SCSI subsystem initialized

usbcore: registered new interface driver usbfs

usbcore: registered new interface driver hub

usbcore: registered new device driver usb

NET: Registered protocol family 2

IP route cache hash table entries: 1024 (order: 0, 4096 bytes)

TCP established hash table entries: 2048 (order: 1, 8192 bytes)

TCP bind hash table entries: 1024 (order: 0, 4096 bytes)

TCP: Hash tables configured (established 2048 bind 1024)

TCP reno registered

checking if image is initramfs...it isn't (no cpio magic); looks like an initrd

Freeing initrd memory: 3072K

NetWinder Floating Point Emulator V0.97 (double precision)

JFFS2 version 2.2. (NAND) (C) 2001-2006 Red Hat, Inc.

io scheduler noop registered

io scheduler anticipatory registered (default)

atmel_usart.0: ttyS0 at MMIO 0xfeffee00 (irq = 1) is a ATMEL_SERIAL

atmel_usart.1: ttyS1 at MMIO 0xfff8c000 (irq = 7) is a ATMEL_SERIAL

RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize

loop: loaded (max 8 devices)

NAND device: Manufacturer ID: 0xec, Chip ID: 0xda (Samsung NAND 256MiB 3,3V 8-bi

t)

Scanning device for bad blocks

Creating 2 MTD partitions on "NAND 256MiB 3,3V 8-bit":

0x00000000-0x04000000 : "Partition 1"

0x04000000-0x10000000 : "Partition 2"

atmel_spi atmel_spi.0: Atmel SPI Controller at 0xfffa4000 (irq 14)

mtd_dataflash spi0.0: AT45DB642x (8448 KBytes)

usbmon: debugfs is not available

at91_ohci at91_ohci: AT91 OHCI

at91_ohci at91_ohci: new USB bus registered, assigned bus number 1

at91_ohci at91_ohci: irq 29, io mem 0x00a00000

usb usb1: configuration #1 chosen from 1 choice

hub 1-0:1.0: USB hub found

hub 1-0:1.0: 2 ports detected

Initializing USB Mass Storage driver...

usbcore: registered new interface driver usb-storage

USB Mass Storage support registered.

udc: at91_udc version 3 May 2006

mice: PS/2 mouse device common for all mice

ads7846 spi0.3: touchscreen, irq 31

input: ADS784x Touchscreen as /class/input/input0

i2c /dev entries driver

TCP cubic registered

NET: Registered protocol family 1

NET: Registered protocol family 17

RAMDISK: Compressed image found at block 0

VFS: Mounted root (ext2 filesystem).

Freeing init memory: 100K

Warning: unable to open an initial console.

Kernel panic - not syncing: No init found. Try passing init= option to kernel.

---

