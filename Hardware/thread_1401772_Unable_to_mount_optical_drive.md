---
title: "Unable to mount optical drive"
date: 2010-02-08
forum: Hardware
---

### Post by Theist17 on 2010-02-08
Hi all,

I'm having a slight issue. Every time I attempt to mount a CD in my Karmic install, I get the following error message:

mount: special device /dev/scd0 does not exist

Here's my output for /etc/fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=97829545-645e-4bcd-818d-ebbd0f5b451f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=34665239-5658-4c83-9663-2ed676b59e35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Here is my output for lshw -short:

```
H/W path             Device     Class       Description
=======================================================
                                system      Satellite M305D
/0                              bus         Satellite M305D
/0/0                            memory      109KiB BIOS
/0/4                            processor   AMD Turion(tm) X2 Ultra Dual-Core Mo
/0/4/5                          memory      64KiB L1 cache
/0/4/6                          memory      2MiB L2 cache
/0/e                            memory      4GiB System Memory
/0/e/0                          memory      2GiB DIMM DDR2 Synchronous
/0/e/1                          memory      2GiB DIMM DDR2 Synchronous
/0/100                          bridge      RS780 Host Bridge
/0/100/1                        bridge      Toshiba America Info Systems
/0/100/1/5                      display     RS780MC [Radeon HD 3100 Graphics]
/0/100/5                        bridge      RS780 PCI to PCI bridge (PCIE port 1
/0/100/5/0           eth0       network     88E8040T PCI-E Fast Ethernet Control
/0/100/7                        bridge      RS780 PCI to PCI bridge (PCIE port 3
/0/100/a                        bridge      RS780 PCI to PCI bridge (PCIE port 5
/0/100/a/0           wmaster0   network     AR5001 Wireless Network Adapter
/0/100/11            scsi0      storage     SB700/SB800 SATA Controller [AHCI mo
/0/100/11/0.0.0      /dev/sda   disk        250GB Hitachi HTS54252
/0/100/11/0.0.0/1    /dev/sda1  volume      179GiB EXT4 volume
/0/100/11/0.0.0/2    /dev/sda2  volume      100MiB Windows NTFS volume
/0/100/11/0.0.0/3    /dev/sda3  volume      44GiB Windows NTFS volume
/0/100/11/0.0.0/4    /dev/sda4  volume      9703MiB Extended partition
/0/100/11/0.0.0/4/5  /dev/sda5  volume      9703MiB Linux swap / Solaris partiti
/0/100/12                       bus         SB700/SB800 USB OHCI0 Controller
/0/100/12.1                     bus         SB700 USB OHCI1 Controller
/0/100/12.2                     bus         SB700/SB800 USB EHCI Controller
/0/100/13                       bus         SB700/SB800 USB OHCI0 Controller
/0/100/13.1                     bus         SB700 USB OHCI1 Controller
/0/100/13.2                     bus         SB700/SB800 USB EHCI Controller
/0/100/14                       bus         SBx00 SMBus Controller
/0/100/14.1                     storage     SB700/SB800 IDE Controller
/0/100/14.2                     multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                     bridge      SB700/SB800 LPC host controller
/0/100/14.4                     bridge      SBx00 PCI to PCI Bridge
/0/100/14.4/1                   bus         Firewire (IEEE 1394)
/0/100/14.4/1.2                 generic     Integrated MMC/SD Controller
/0/100/14.4/1.3                 storage     Integrated MS/xD Controller
/0/101                          bridge      Mobile K10 [Turion X2, Athlon X2, Se
/0/102                          bridge      Family 11h [Turion X2, Athlon X2, Se
/0/103                          bridge      Mobile K10 [Turion X2, Athlon X2, Se
/0/104                          bridge      Mobile K10 [Turion X2, Athlon X2, Se
/0/105                          bridge      Mobile K10 [Turion X2, Athlon X2, Se
/1                   vboxnet0   network     Ethernet interface

```

It's pretty annoying to not be able to burn or rip CDs and watch DVDs, so I'd appreciate your help very very much. 

Have a wonderful day!
Jordan

---

### Post by Theist17 on 2010-02-09
Just a quick note: I have yet to try booting from my Karmic LiveCD. Forgot to mention that.

---

### Post by Theist17 on 2010-02-10
UPDATE/bump:

My BIOS no longer recognizes the CD drive. I discovered this when attempting to boot from my Karmic LiveCD. 

This is bad news, guys and gals. I am in dire need of a way to fix this problem.

---

