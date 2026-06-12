---
title: "Failure to read or write on any CD or DVD"
date: 2008-08-07
forum: Hardware
---

### Post by promix89 on 2008-08-07
The only problem we have with a Ubuntu 8.04 and 8.04.1 but with 7.10 or 7.04 ... no
CD has no mistakes.
======================================================================
ionel@ionel-desktop:~$ lsb_release -rd
Description: Ubuntu 8.04.1
Release: 8.04
========================================================================
/var/log/kernel.log
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.673383] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.673401] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.673411] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.673423] end_request: I/O error, dev sr0, sector 72
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.673429] printk: 1 messages suppressed.
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.673435] Buffer I/O error on device sr0, logical block 18
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.673444] Buffer I/O error on device sr0, logical block 19
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684219] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684238] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684247] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684260] end_request: I/O error, dev sr0, sector 88
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684269] Buffer I/O error on device sr0, logical block 22
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684281] Buffer I/O error on device sr0, logical block 23
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684288] Buffer I/O error on device sr0, logical block 24
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684295] Buffer I/O error on device sr0, logical block 25
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684302] Buffer I/O error on device sr0, logical block 26
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684308] Buffer I/O error on device sr0, logical block 27
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684314] Buffer I/O error on device sr0, logical block 28
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.684320] Buffer I/O error on device sr0, logical block 29
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.728459] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.728479] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.728488] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:11 ionel-desktop kernel: [ 4953.728500] end_request: I/O error, dev sr0, sector 72
Aug 7 21:52:11 ionel-desktop kernel: [ 4954.220006] UDF-fs: No VRS found
Aug 7 21:52:12 ionel-desktop kernel: [ 4954.248395] ISO 9660 Extensions: Microsoft Joliet Level 3
Aug 7 21:52:12 ionel-desktop kernel: [ 4954.250369] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:12 ionel-desktop kernel: [ 4954.250383] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:12 ionel-desktop kernel: [ 4954.250393] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:12 ionel-desktop kernel: [ 4954.250405] end_request: I/O error, dev sr0, sector 116
Aug 7 21:52:12 ionel-desktop kernel: [ 4954.251836] ISOFS: unable to read i-node block
Aug 7 21:52:12 ionel-desktop kernel: [ 4954.251848] ISOFS: changing to secondary root
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.637641] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.637659] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.637668] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.637681] end_request: I/O error, dev sr0, sector 388
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.638575] ISOFS: unable to read i-node block
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.667074] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.667095] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.667105] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.667117] end_request: I/O error, dev sr0, sector 672
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.672552] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.672571] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.672581] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.672593] end_request: I/O error, dev sr0, sector 676
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.679431] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.679447] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.679457] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.679470] end_request: I/O error, dev sr0, sector 672
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.724878] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.724899] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.724940] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.724952] end_request: I/O error, dev sr0, sector 1064
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.804089] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.804108] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.804118] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:13 ionel-desktop kernel: [ 4955.804130] end_request: I/O error, dev sr0, sector 1064
Aug 7 21:52:54 ionel-desktop kernel: [ 4997.184501] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 21:52:54 ionel-desktop kernel: [ 4997.184519] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 21:52:54 ionel-desktop kernel: [ 4997.184529] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 21:52:54 ionel-desktop kernel: [ 4997.184542] end_request: I/O error, dev sr0, sector 1064
Aug 7 21:52:54 ionel-desktop kernel: [ 4997.184549] printk: 50 messages suppressed.
Aug 7 21:52:54 ionel-desktop kernel: [ 4997.184555] Buffer I/O error on device sr0, logical block 266
Aug 7 21:52:54 ionel-desktop kernel: [ 4997.184567] Buffer I/O error on device sr0, logical block 267
========================================================================
/var/log/syslog
Aug 7 22:50:26 ionel-desktop -- MARK --
Aug 7 22:56:36 ionel-desktop kernel: [ 8816.051841] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 22:56:36 ionel-desktop kernel: [ 8816.051860] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 22:56:36 ionel-desktop kernel: [ 8816.051870] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 22:56:36 ionel-desktop kernel: [ 8816.051882] end_request: I/O error, dev sr0, sector 1064
Aug 7 22:56:36 ionel-desktop kernel: [ 8816.051892] Buffer I/O error on device sr0, logical block 266
Aug 7 22:56:36 ionel-desktop kernel: [ 8816.051903] Buffer I/O error on device sr0, logical block 267
=======================================================================
/var/log/messages
Aug 7 22:50:26 ionel-desktop -- MARK --
Aug 7 22:56:36 ionel-desktop kernel: [ 8816.051841] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Aug 7 22:56:36 ionel-desktop kernel: [ 8816.051860] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current]
Aug 7 22:56:36 ionel-desktop kernel: [ 8816.051870] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Aug 7 22:56:36 ionel-desktop kernel: [ 8816.051882] end_request: I/O error, dev sr0, sector 1064
=======================================================================
ionel@ionel-desktop:~$ grep 'ide' /var/log/syslog
Aug 7 19:41:45 ionel-desktop kernel: [ 0.000000] BIOS-provided physical RAM map:
Aug 7 19:41:45 ionel-desktop kernel: [ 0.000000] ACPI: IRQ0 used by override.
Aug 7 19:41:45 ionel-desktop kernel: [ 0.000000] ACPI: IRQ2 used by override.
Aug 7 19:41:45 ionel-desktop kernel: [ 0.000000] ACPI: IRQ9 used by override.
Aug 7 19:41:45 ionel-desktop kernel: [ 22.296747] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000 00000000
Aug 7 19:41:45 ionel-desktop kernel: [ 24.752903] Boot video device is 0000:01:00.0
Aug 7 19:56:31 ionel-desktop kernel: [ 0.000000] BIOS-provided physical RAM map:
Aug 7 19:56:31 ionel-desktop kernel: [ 0.000000] ACPI: IRQ0 used by override.
Aug 7 19:56:31 ionel-desktop kernel: [ 0.000000] ACPI: IRQ2 used by override.
Aug 7 19:56:31 ionel-desktop kernel: [ 0.000000] ACPI: IRQ9 used by override.
Aug 7 19:56:31 ionel-desktop kernel: [ 16.463394] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000 00000000
Aug 7 19:56:32 ionel-desktop kernel: [ 18.919455] Boot video device is 0000:01:00.0
Aug 7 20:29:54 ionel-desktop kernel: [ 0.000000] BIOS-provided physical RAM map:
Aug 7 20:29:54 ionel-desktop kernel: [ 0.000000] ACPI: IRQ0 used by override.
Aug 7 20:29:54 ionel-desktop kernel: [ 0.000000] ACPI: IRQ2 used by override.
Aug 7 20:29:54 ionel-desktop kernel: [ 0.000000] ACPI: IRQ9 used by override.
Aug 7 20:29:54 ionel-desktop kernel: [ 15.899951] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000 00000000
Aug 7 20:29:54 ionel-desktop kernel: [ 18.355949] Boot video device is 0000:01:00.0
Aug 7 20:34:47 ionel-desktop kernel: [ 0.000000] BIOS-provided physical RAM map:
Aug 7 20:34:47 ionel-desktop kernel: [ 0.000000] ACPI: IRQ0 used by override.
Aug 7 20:34:47 ionel-desktop kernel: [ 0.000000] ACPI: IRQ2 used by override.
Aug 7 20:34:47 ionel-desktop kernel: [ 0.000000] ACPI: IRQ9 used by override.
Aug 7 20:34:47 ionel-desktop kernel: [ 15.235469] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000 00000000
Aug 7 20:34:47 ionel-desktop kernel: [ 17.692178] Boot video device is 0000:01:00.0
Aug 7 20:30:27 ionel-desktop kernel: [ 0.000000] BIOS-provided physical RAM map:
Aug 7 20:30:27 ionel-desktop kernel: [ 0.000000] ACPI: IRQ0 used by override.
Aug 7 20:30:27 ionel-desktop kernel: [ 0.000000] ACPI: IRQ2 used by override.
Aug 7 20:30:27 ionel-desktop kernel: [ 0.000000] ACPI: IRQ9 used by override.
Aug 7 20:30:27 ionel-desktop kernel: [ 16.109049] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000 00000000
Aug 7 20:30:27 ionel-desktop kernel: [ 18.565142] Boot video device is 0000:01:00.0

======================================================================
ionel@ionel-desktop:~$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DRW-1608P3S (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
========================================================================
ionel@ionel-desktop:~$ sudo lshw -C disk
[sudo] password for ionel:
  *-disk
       description: ATA Disk
       product: Maxtor 6Y120L0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y36C3PAE
       size: 114GiB (122GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000cb0ae
  *-cdrom
       description: DVD-RAM writer
       product: DRW-1608P3S
       vendor: ASUS
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 1.24
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted

---

### Post by mc4man on 2008-08-07
If you have an ide dvd drive then run ```
sudo hdparm -i /dev/scd0
```
if it shows the drive set to umda4 and considering this error
> [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
 I'd check to see if your using a 40 wire ide cable
Dvd drives that are set to udma4 need an 80 wire cable
some that are set to udma2 can also benefit (especially ones that are udma4 capable but have been 'soft' reset to udma2)

You can tell if it's a 40 wire just by looking, the individual wires are obvious, an 80 wire is almost smooth

---

