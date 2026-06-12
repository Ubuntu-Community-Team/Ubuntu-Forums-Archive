---
title: "Long boot time.  Gave up waiting for root device.  10.04"
date: 2010-07-25
forum: Hardware
---

### Post by chriswillmorris on 2010-07-25
I have an Acer Aspire 1810TZ laptop with Windows 7 on it.  I decided to dual boot w/ Ubuntu 10.04 32-bit Lucid Lynx.  I was initially getting this issue

```

gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the righ device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/bf2ed1f9.... does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

but this usually doesn't happen anymore because I changed the rootdelay option in the Grub file to 90 (previously, it wasn't waiting long enough).

However, it now can take over 4 minutes to boot and I have a sneaking suspicion that this can be fixed (it shouldn't take that long, right?).

I looked on other forums to see what information people provided to help solve this problem, so here's some information you might need to help fix this:

List of hardware devices with 
lshw
```
                                                                     
                                                                     
                                                                     
                                             
chris-laptop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2956MiB
     *-cpu
          product: Genuine Intel(R) CPU           U4100  @ 1.30GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1300MHz
          capacity: 1300MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:27 memory:d0000000-d03fffff memory:c0000000-cfffffff(prefetchable) ioport:30d0(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d2400000-d24fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:30a0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:d4504c00-d4504fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:d4500000-d4503fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:d3500000-d44fffff ioport:d0400000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8131 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: c0
                serial: 00:26:9e:4e:91:c7
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 multicast=yes
                resources: irq:29 memory:d3500000-d353ffff ioport:2000(size=128)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:d2500000-d34fffff ioport:d1400000(size=16777216)
           *-network
                description: Wireless interface
                product: WiFi Link 1000 Series
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 00:1e:64:0e:5f:34
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.1.4 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:28 memory:d2500000-d2501fff
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:3080(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3060(size=32)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3040(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d4504800-d4504bff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:30c8(size=8) ioport:30dc(size=4) ioport:30c0(size=8) ioport:30d8(size=4) ioport:3020(size=32) memory:d4504000-d45047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d4505000-d45050ff ioport:3000(size=32)
```


cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c48b8f67-2794-4964-b0fe-c0841763c15d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1dadc84d-813d-4e22-b175-32b07cda2ca2 none            swap    sw              0       0
```


sudo blkid -c /dev/null:
```
/dev/sda1: LABEL="PQSERVICE" UUID="2AAA81A0AA816961" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="246E82DE6E82A85E" TYPE="ntfs" 
/dev/sda3: LABEL="Acer" UUID="CE0884CD0884B64D" TYPE="ntfs" 
/dev/sda5: UUID="c48b8f67-2794-4964-b0fe-c0841763c15d" TYPE="ext4" 
/dev/sda6: UUID="1dadc84d-813d-4e22-b175-32b07cda2ca2" TYPE="swap" 
```


some sort of boot info retrieved from a boot info script:
```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    25,167,871    25,165,824  27 Hidden HPFS/NTFS
/dev/sda2    *     25,167,872    25,372,671       204,800   7 HPFS/NTFS
/dev/sda3          25,372,672   357,814,051   332,441,380   7 HPFS/NTFS
/dev/sda4         357,814,270   625,141,759   267,327,490   5 Extended
/dev/sda5         357,814,272   614,199,295   256,385,024  83 Linux
/dev/sda6         614,201,344   625,141,759    10,940,416  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2AAA81A0AA816961                       ntfs       PQSERVICE                     
/dev/sda2        246E82DE6E82A85E                       ntfs       SYSTEM RESERVED               
/dev/sda3        CE0884CD0884B64D                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c48b8f67-2794-4964-b0fe-c0841763c15d   ext4                                     
/dev/sda6        1dadc84d-813d-4e22-b175-32b07cda2ca2   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c48b8f67-2794-4964-b0fe-c0841763c15d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c48b8f67-2794-4964-b0fe-c0841763c15d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c48b8f67-2794-4964-b0fe-c0841763c15d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c48b8f67-2794-4964-b0fe-c0841763c15d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c48b8f67-2794-4964-b0fe-c0841763c15d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c48b8f67-2794-4964-b0fe-c0841763c15d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c48b8f67-2794-4964-b0fe-c0841763c15d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c48b8f67-2794-4964-b0fe-c0841763c15d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2aaa81a0aa816961
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 246e82de6e82a85e
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c48b8f67-2794-4964-b0fe-c0841763c15d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1dadc84d-813d-4e22-b175-32b07cda2ca2 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 249.9GB: boot/grub/core.img
 277.9GB: boot/grub/grub.cfg
 249.9GB: boot/initrd.img-2.6.32-21-generic
 249.9GB: boot/vmlinuz-2.6.32-21-generic
 249.9GB: initrd.img
 249.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  00 00 00 ff ff ff ff 10  eb 53 00 22 05 93 19 01  |.........S."....|
00000010  00 00 00 6c 9b 57 00 64  c7 c5 d2 22 45 9c 4a d6  |...l.W.d..."E.J.|
00000020  35 85 06 e1 d0 a7 33 00  00 00 00 01 00 00 00 ff  |5.....3.........|
00000030  ff ff ff 40 eb 53 00 22  05 93 19 01 00 00 00 98  |...@.S."........|
00000040  9b 57 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |.W..............|
00000050  00 00 00 00 00 00 00 cf  7e 3f 11 16 1c b7 57 14  |........~?....W.|
00000060  5e 35 df 59 25 5c 70 df  54 43 00 00 00 00 00 34  |^5.Y%\p.TC.....4|
00000070  00 00 00 35 00 00 00 01  00 00 00 c4 9b 57 00 22  |...5.........W."|
00000080  05 93 19 36 00 00 00 0c  9c 57 00 01 00 00 00 d4  |...6.....W......|
00000090  9b 57 00 00 00 00 00 9a  e2 68 8e 10 46 63 d1 c2  |.W.......h..Fc..|
000000a0  ff 22 e9 22 8d 4c 53 00  00 00 00 00 00 00 00 70  |.".".LS........p|
000000b0  eb 53 00 01 00 00 00 78  eb 53 00 00 00 00 00 80  |.S.....x.S......|
000000c0  eb 53 00 03 00 00 00 88  eb 53 00 00 00 00 00 90  |.S.......S......|
000000d0  eb 53 00 05 00 00 00 09  b3 99 58 6b 7e fd c5 69  |.S........Xk~..i|
000000e0  65 70 69 24 37 5b 4b a8  eb 53 00 00 00 00 00 b0  |epi$7[K..S......|
000000f0  eb 53 00 09 00 00 00 b8  eb 53 00 00 00 00 00 c0  |.S.......S......|
00000100  eb 53 00 0b 00 00 00 c8  eb 53 00 00 00 00 00 d0  |.S.......S......|
00000110  eb 53 00 0d 00 00 00 ae  90 fd 91 f3 48 07 9b d3  |.S..........H...|
00000120  e3 7b 62 59 a6 c5 1d e8  eb 53 00 00 00 00 00 f0  |.{bY.....S......|
00000130  eb 53 00 11 00 00 00 f8  eb 53 00 00 00 00 00 00  |.S.......S......|
00000140  ec 53 00 13 00 00 00 08  ec 53 00 00 00 00 00 10  |.S.......S......|
00000150  ec 53 00 15 00 00 00 6f  c5 73 8d 8c 7f 66 d3 5d  |.S.....o.s...f.]|
00000160  99 14 32 68 c9 3c 1e 28  ec 53 00 00 00 00 00 30  |..2h.<.(.S.....0|
00000170  ec 53 00 19 00 00 00 38  ec 53 00 00 00 00 00 40  |.S.....8.S.....@|
00000180  ec 53 00 1b 00 00 00 48  ec 53 00 00 00 00 00 50  |.S.....H.S.....P|
00000190  ec 53 00 1d 00 00 00 d4  ae 8d 77 87 f6 1a 46 7b  |.S........w...F{|
000001a0  8c 23 d4 27 22 21 9a 68  ec 53 00 00 00 00 00 70  |.#.'"!.h.S.....p|
000001b0  ec 53 00 21 00 00 00 78  ec 53 00 00 00 00 00 fe  |.S.!...x.S......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 20 48 0f 00 fe  |........... H...|
000001d0  ff ff 05 fe ff ff 02 20  48 0f 00 f8 a6 00 00 00  |....... H.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```


I am new to Ubuntu and would greatly appreciate anyone's help.  If I can't fix the long boot time, I might try out a previous version.

---

