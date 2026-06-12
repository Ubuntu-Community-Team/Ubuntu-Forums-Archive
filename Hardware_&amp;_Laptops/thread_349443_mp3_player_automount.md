---
title: "mp3 player automount"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by klittzzer on 2007-01-30
Can anyone help?

I have a 'SigmaTel' 2 GiB USB mass storage mp3 player and a '...' 64 MiB USB flash drive. Both of these devices work ok in Ubuntu Edgy but will only mount if I boot my computer with them plugged in. If I plug either of them in when Ubuntu Edgy is running, they do not mount. 

Is there a way that I can tell Edgy to automount these devices while it is running? I mean, if I plug them before I switch on my notebook so that they are being recognised by Edgy, can I then add them to the mounted devices list or something like that? Even if I can run a command in the terminal to mount them it has got to be better than having to shut down my system and re boot every time I want to read or write to them (that is reminiscent of Windows, surely Ubuntu is above all of that?).
 

cheers

klittzzer

I have just booted my notebook with my mp3 player plugged in. It has been recognised and 'fstab' =

klittzzer@notebook:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3911    31415076   83  Linux
/dev/hda2            3912        9599    45688860   83  Linux
/dev/hda3            9600        9729     1044225   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sda: 2091 MB, 2091384832 bytes
77 heads, 38 sectors/track, 349 cylinders
Units = cylinders of 2926 * 2048 = 5992448 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         349     2042272    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 38) logical=(0, 1, 1)


Is there any way I can make that permanent?

As I have said, if I plug the device in while Ubuntu is running nothing happens, it just will not mount it unless from boot.

Please help

---

### Post by klittzzer on 2007-01-30
I have just spent hours trying to find a solution to this problem. It can't be hardware related because if it was the USB removable device wouldn't get picked up like it does when I plug it in before boot. I can't find any answers to this problem as it is generally thought that if I plug a device in to one of the USB ports on my laptop it will automatically mount and I will get an icon in /etc/media/ and on my desktp. 
As it stands, none of the USB devices I have and none of the ones I have tried that a mate of mine gave me to try will hotplug. is that it? Is there absolutely no way that any USB device will be picked up by Ubuntu unless I turn off my computer and reboot with the device plugged in while the computer is switched off?
I have been asking about this for a while now and just got told off for assuming it was the software. 
Surely there must be a way in which an OS such as Ubuntu can cope with reading USB devices that are plugged in while it is running. I have 'hal' and have reinstalled it around a dozen times and I have installed ivman.
Nothing works. is there any software which will enable the hot plugging of removable USB drives that I am missing?

I don't really expect a reply cos everyone seems to think that these devices will automagically be detected. Even though it has never happened.

---

### Post by datakid on 2007-01-31
ok, this maybe annoying, but where you posted fstab, you should post mtab (when one of your devices is plugged in and working.

fstab = file system table ("# /etc/fstab: static file system information." from the file)
mtab = mounted file system table

hence, the mtab can be equally as interesting.

try comparing the two?

Also, I notice that you have said above "fstab=" and then run the fdisk command.

fdisk is the partition manager - that's not showing you anything meaningful (in this situation).

What you want when you say fstab is the file /etc/fstab (and when I say mtab, I mean /etc/mtab)

ie, I would type this to look at them:

datakid@boxen:~$ less /etc/mtab
datakid@boxen:~$ less /etc/fstab

what the OS finds in fstab is the file systems it know's about.
what it finds in mtab are the mount drives.

eg, my mtab:


/dev/sda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
/dev/sda3 /media/sda3 ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdb3 /media/ipod hfsplus rw,nosuid,nodev,uid=1000,gid=1000 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=datakid 0 0


note that there is an ipod mounted? (second last line)

I'm having trouble with it at the moment - I can tell what the problem is (see here: [http://www.ubuntuforums.org/showthread.php?t=349705](http://www.ubuntuforums.org/showthread.php?t=349705) ) by using dmesg

datakid@boxen:~$dmesg

When you use these tools, you may find more information to "search on" or post here, that may help us help you :D

---

### Post by klittzzer on 2007-01-31
Thanks for your time and answer. And thanks for not digging me out. That is what got me at it when I last tried to get help to sort out this problem. I was told it was my hardware, and that I shouldn't blame the software. I wouldn't see the mp3 player or flash drive mounted if it was hardware.

Anyway. I have had a look at dmesg  a load of times and will post it from when I boot with the device plugged and it being mounted and when I try to hot plug it. I hadn't read anything about the 'mtab' file though. All of the how2s and other stuff I have looked at, and I have been looking for a while now, just seem to mention 'fstab' and adding drives to that. At the moment, with nothing plugged, it is just showing me my / ,/home, and swap partitions I think. I will do the same and post that with and without the player. I will explain when I post it.

Is there any way that I can do something with this IVMAN utility? I have read posts here and there which seem to say that installing and configuring it has solved problems similar to this. Unfortunately, I am yet to read anything in the way of a coherent guide explaining how to configuring IVMAN, they have just said that it works.

I will post the outputs next.
Thanks again for your time

Hold on, I have just tried to 'eject' the device and get this error message saying:  "UNABLE TO EJECT MEDIA" (below that)" Show more details" (below that) "ERROR:Device /dev/sda1/ was not mounted by you" (and under that) "Eject: unmount of '/media/MP3' failed".  That is a new one????

Ok outputs of dmesg, /etc/mtab/, /etc/fstab/, and lsusb when I try to hotplug the device are-

dmesg




Ok DATAKID,

here are the outputs of /etc/mtab, etc/fstab, and dmesg while the mp3 player is mounted as a result of my plugging it in to USB port2 on my laptop before I switched the computer on and thus booted up with it in-that's the only way I can get it mounted and readable/writable. And to add to my problem, the music that is on the player is not showing in Ubuntu any more. I can see the sysem files but no music and it still doesn't hot plug or automount.
I must add that my cd/dvd+-rw drive works perfectly (that last line of dmesg has never appeared before?) and I can read any data or music cd and film dvd no problem and they always automount.

Ok dmesg with player mounted from boot=

[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bfef000 (usable)
[17179569.184000]  BIOS-e820: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 447MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 114671
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110575 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e6010
[17179569.184000] ACPI: RSDT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1bffc3c0
[17179569.184000] ACPI: FADT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1bfffb10
[17179569.184000] ACPI: MADT (v001 INSYDE APIC_000 0x30303030 0000 0x00010200) @ 0x1bfffba0
[17179569.184000] ACPI: DSDT (v001 MTC___ 8650____ 0x00001000 INTL 0x02002036) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1592.410 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.240000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.240000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.256000] Memory: 444776k/458684k available (1910k kernel code, 13388k reserved, 1069k data, 308k init, 0k highmem)
[17179569.256000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.336000] Calibrating delay using timer specific routine.. 3188.80 BogoMIPS (lpj=6377603)
[17179569.336000] Security Framework v1.0.0 initialized
[17179569.336000] SELinux:  Disabled at boot.
[17179569.336000] Mount-cache hash table entries: 512
[17179569.336000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.336000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.336000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.336000] CPU: L2 cache: 1024K
[17179569.336000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.336000] Checking 'hlt' instruction... OK.
[17179569.352000] SMP alternatives: switching to UP code
[17179569.352000] Freeing SMP alternatives: 16k freed
[17179569.352000] checking if image is initramfs... it is
[17179569.944000] Freeing initrd memory: 5623k freed
[17179569.944000] ACPI: Core revision 20060707
[17179569.944000] ACPI: Looking for DSDT ... not found!
[17179569.988000] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
[17179569.988000] Total of 1 processors activated (3188.80 BogoMIPS).
[17179569.988000] ENABLING IO-APIC IRQs
[17179569.988000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.132000] Brought up 1 CPUs
[17179570.132000] migration_cost=0
[17179570.132000] NET: Registered protocol family 16
[17179570.132000] EISA bus registered
[17179570.132000] ACPI: bus type pci registered
[17179570.132000] PCI: PCI BIOS revision 2.10 entry at 0xe9c04, last bus=1
[17179570.132000] PCI: Using configuration type 1
[17179570.132000] Setting up standard PCI resources
[17179570.132000] ACPI: Interpreter enabled
[17179570.132000] ACPI: Using IOAPIC for interrupt routing
[17179570.136000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.136000] PCI: Probing PCI hardware (bus 00)
[17179570.136000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.136000] PCI quirk: region 1000-107f claimed by vt8235 PM
[17179570.136000] PCI quirk: region 1400-140f claimed by vt8235 SMB
[17179570.136000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179570.136000] Boot video device is 0000:01:00.0
[17179570.136000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.152000] ACPI: Embedded Controller [EC0] (gpe 1) interrupt mode.
[17179570.152000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[17179570.152000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 14 15)
[17179570.152000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[17179570.156000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 14 15)
[17179570.156000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11
[17179570.156000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
[17179570.156000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179570.156000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179570.156000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179570.156000] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0
[17179570.156000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.156000] pnp: PnP ACPI init
[17179570.160000] pnp: PnP ACPI: found 9 devices
[17179570.160000] PnPBIOS: Disabled by ACPI PNP
[17179570.160000] PCI: Using ACPI for IRQ routing
[17179570.160000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.164000] pnp: 00:07: ioport range 0x330-0x331 has been reserved
[17179570.164000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179570.164000] pnp: 00:07: ioport range 0x1000-0x107f could not be reserved
[17179570.164000] pnp: 00:07: ioport range 0x1400-0x140f has been reserved
[17179570.164000] PCI: Bridge: 0000:00:01.0
[17179570.164000]   IO window: c000-dfff
[17179570.164000]   MEM window: c0000000-cfffffff
[17179570.164000]   PREFETCH window: 90000000-9fffffff
[17179570.164000] PCI: Bus 2, cardbus bridge: 0000:00:09.0
[17179570.164000]   IO window: 00001800-000018ff
[17179570.164000]   IO window: 00001c00-00001cff
[17179570.164000]   PREFETCH window: 20000000-21ffffff
[17179570.164000]   MEM window: 22000000-23ffffff
[17179570.164000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.164000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.164000] NET: Registered protocol family 2
[17179570.204000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.204000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.204000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.204000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.204000] TCP reno registered
[17179570.204000] audit: initializing netlink socket (disabled)
[17179570.204000] audit(1170239930.204:1): initialized
[17179570.204000] VFS: Disk quotas dquot_6.5.1
[17179570.204000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.204000] Initializing Cryptographic API
[17179570.204000] io scheduler noop registered
[17179570.204000] io scheduler anticipatory registered
[17179570.204000] io scheduler deadline registered
[17179570.204000] io scheduler cfq registered (default)
[17179570.204000] isapnp: Scanning for PnP cards...
[17179570.560000] isapnp: No Plug & Play device found
[17179570.592000] Real Time Clock Driver v1.12ac
[17179570.592000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.592000] mice: PS/2 mouse device common for all mice
[17179570.592000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.592000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.592000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.592000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.608000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179570.612000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179570.612000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179570.612000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179570.616000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179570.616000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.616000] EISA: Probing bus 0 at eisa.0
[17179570.616000] Cannot allocate resource for EISA slot 1
[17179570.616000] EISA: Detected 0 cards.
[17179570.620000] TCP bic registered
[17179570.620000] NET: Registered protocol family 1
[17179570.620000] NET: Registered protocol family 8
[17179570.620000] NET: Registered protocol family 20
[17179570.620000] Using IPI No-Shortcut mode
[17179570.620000] ACPI: (supports S0 S1 S3 S4 S5)
[17179570.620000] Freeing unused kernel memory: 308k freed
[17179570.644000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.740000] Capability LSM initialized
[17179571.772000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179571.772000] ACPI: Processor [CPU0] (supports 16 throttling states)
[17179572.076000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179572.076000] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[17179572.076000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[17179572.076000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179572.076000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 177
[17179572.076000] PCI: Via IRQ fixup for 0000:00:11.1, from 0 to 1
[17179572.076000] VP_IDE: chipset revision 6
[17179572.076000] VP_IDE: not 100% native mode: will probe irqs later
[17179572.076000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179572.076000]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[17179572.076000]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
[17179572.076000] Probing IDE interface ide0...
[17179572.492000] hda: WDC WD800VE-07HDT0, ATA DISK drive
[17179573.164000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.216000] Probing IDE interface ide1...
[17179574.080000] hdc: PHILIPS DVD+/-RW SDVD8431, ATAPI CD/DVD-ROM drive
[17179574.752000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.756000] hda: max request size: 128KiB
[17179574.764000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179574.764000] hda: cache flushes supported
[17179574.764000]  hda: hda1 hda2 hda3
[17179574.868000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.868000] Uniform CD-ROM driver Revision: 3.20
[17179575.264000] usbcore: registered new driver usbfs
[17179575.264000] usbcore: registered new driver hub
[17179575.268000] USB Universal Host Controller Interface driver v3.0
[17179575.268000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179575.268000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179575.268000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179575.268000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179575.268000] ACPI: Invalid IRQ link routing entry
[17179575.268000] ACPI: Unable to derive IRQ for device 0000:00:10.0
[17179575.268000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI - using IRQ 11
[17179575.268000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179575.268000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179575.268000] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[17179575.272000] usb usb1: configuration #1 chosen from 1 choice
[17179575.272000] hub 1-0:1.0: USB hub found
[17179575.272000] hub 1-0:1.0: 2 ports detected
[17179575.376000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179575.376000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179575.376000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179575.376000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179575.376000] ACPI: Invalid IRQ link routing entry
[17179575.376000] ACPI: Unable to derive IRQ for device 0000:00:10.1
[17179575.376000] ACPI: PCI Interrupt 0000:00:10.1[B]: no GSI - using IRQ 7
[17179575.376000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179575.376000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179575.376000] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[17179575.376000] usb usb2: configuration #1 chosen from 1 choice
[17179575.376000] hub 2-0:1.0: USB hub found
[17179575.376000] hub 2-0:1.0: 2 ports detected
[17179575.480000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179575.480000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179575.480000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179575.480000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179575.480000] ACPI: Invalid IRQ link routing entry
[17179575.480000] ACPI: Unable to derive IRQ for device 0000:00:10.2
[17179575.480000] ACPI: PCI Interrupt 0000:00:10.2[C]: no GSI - using IRQ 5
[17179575.480000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179575.480000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179575.480000] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[17179575.480000] usb usb3: configuration #1 chosen from 1 choice
[17179575.480000] hub 3-0:1.0: USB hub found
[17179575.480000] hub 3-0:1.0: 2 ports detected
[17179575.584000] PCI: Enabling device 0000:00:10.3 (0000 -> 0002)
[17179575.584000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179575.584000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179575.584000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179575.584000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179575.584000] ACPI: Invalid IRQ link routing entry
[17179575.584000] ACPI: Unable to derive IRQ for device 0000:00:10.3
[17179575.584000] ACPI: PCI Interrupt 0000:00:10.3[D]: no GSI - using IRQ 10
[17179575.584000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179575.584000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179575.584000] ehci_hcd 0000:00:10.3: irq 10, io mem 0x24011000
[17179575.584000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.584000] usb usb4: configuration #1 chosen from 1 choice
[17179575.584000] hub 4-0:1.0: USB hub found
[17179575.584000] hub 4-0:1.0: 6 ports detected
[17179575.720000] Attempting manual resume
[17179575.784000] kjournald starting.  Commit interval 5 seconds
[17179575.784000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.728000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179580.268000] usb 2-1: configuration #1 chosen from 1 choice
[17179585.796000] ath_hal: module license 'Proprietary' taints kernel.
[17179585.796000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179585.796000] irda_init()
[17179585.796000] NET: Registered protocol family 23
[17179585.904000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179585.908000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.928000] input: PC Speaker as /class/input/input1
[17179586.192000] wlan: 0.8.4.2 (0.9.2.1)
[17179586.192000] ath_rate_sample: 1.2 (0.9.2.1)
[17179586.196000] ath_pci: 0.9.4.5 (0.9.2.1)
[17179586.196000] PCI: Enabling device 0000:00:06.0 (0000 -> 0002)
[17179586.196000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 185
[17179586.780000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179586.780000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179586.780000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17179586.780000] wifi0: mac 7.8 phy 4.5 radio 5.6
[17179586.780000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17179586.780000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17179586.780000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17179586.780000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17179586.780000] wifi0: Use hw queue 8 for CAB traffic
[17179586.780000] wifi0: Use hw queue 9 for beacons
[17179586.784000] wifi0: Atheros 5212: mem=0x24000000, irq=185
[17179586.796000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.800000] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[17179586.808000] agpgart: AGP aperture is 128M @ 0xa0000000
[17179586.948000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179586.948000] Yenta: CardBus bridge found at 0000:00:09.0 [1734:10ab]
[17179586.948000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179586.948000] Yenta: Routing CardBus interrupts to PCI
[17179586.948000] Yenta TI: socket 0000:00:09.0, mfunc 0x01001002, devctl 0x44
[17179586.980000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[17179587.036000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179587.080000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179587.132000] ts: Compaq touchscreen protocol output
[17179587.180000] Yenta: ISA IRQ mask 0x0000, PCI irq 169
[17179587.180000] Socket status: 30000006
[17179587.184000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 11, using IRQ 23
[17179587.184000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[17179587.184000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKB] -> GSI 23 (level, low) -> IRQ 193
[17179587.184000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 1
[17179587.188000] eth0: VIA Rhine II at 0x1e200, 00:40:d0:8d:27:ed, IRQ 193.
[17179587.188000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 41e1.
[17179587.592000] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[17179587.592000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 5, using IRQ 22
[17179587.592000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179587.592000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179587.592000] PCI: Via IRQ fixup for 0000:00:11.6, from 5 to 9
[17179587.596000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179587.616000] usbcore: registered new driver libusual
[17179587.856000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179587.872000] SCSI subsystem initialized
[17179587.884000] Initializing USB Mass Storage driver...
[17179587.884000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179587.884000] usbcore: registered new driver usb-storage
[17179587.884000] USB Mass Storage support registered.
[17179587.884000] usb-storage: device found at 2
[17179587.884000] usb-storage: waiting for device to settle before scanning
[17179588.104000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179588.104000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 9
[17179588.104000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179588.216000] cs: IO port probe 0x100-0x3af: clean.
[17179588.220000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179588.220000] cs: IO port probe 0x820-0x8ff: clean.
[17179588.220000] cs: IO port probe 0xc00-0xcf7: clean.
[17179588.220000] cs: IO port probe 0xa00-0xaff: clean.
[17179588.496000] NET: Registered protocol family 17
[17179588.880000] lp: driver loaded but no devices found
[17179588.904000] Adding 1044216k swap on /dev/disk/by-uuid/d0b153c3-ecf8-473a-a25e-56314832e9e2.  Priority:-1 extents:1 across:1044216k
[17179589.000000] EXT3 FS on hda1, internal journal
[17179589.176000] kjournald starting.  Commit interval 5 seconds
[17179589.184000] EXT3 FS on hda2, internal journal
[17179589.184000] EXT3-fs: mounted filesystem with ordered data mode.
[17179590.864000] NET: Registered protocol family 10
[17179590.864000] lo: Disabled Privacy Extensions
[17179590.864000] IPv6 over IPv4 tunneling driver
[17179593.120000] usb-storage: device scan complete
[17179593.784000] ACPI: AC Adapter [AC] (on-line)
[17179593.828000] ACPI: Battery Slot [BAT0] (battery absent)
[17179593.852000] ACPI: Power Button (FF) [PWRF]
[17179593.852000] ACPI: Lid Switch [LID]
[17179593.852000] ACPI: Sleep Button (CM) [SBTN]
[17179593.852000] ACPI: Power Button (CM) [PBTN]
[17179593.876000]   Vendor: Generic   Model: MP3 Player        Rev: 0100
[17179593.876000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17179594.020000] ibm_acpi: ec object not found
[17179594.060000] pcc_acpi: loading...
[17179594.172000] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[17179595.136000] SCSI device sda: 1021184 2048-byte hdwr sectors (2091 MB)
[17179595.892000] sda: Write Protect is off
[17179595.892000] sda: Mode Sense: 3e 00 00 00
[17179595.892000] sda: assuming drive cache: write through
[17179597.196000] [drm] Initialized drm 1.0.1 20051102
[17179597.788000] apm: BIOS not found.
[17179597.860000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 209
[17179597.860000] PCI: Via IRQ fixup for 0000:01:00.0, from 11 to 1
[17179597.860000] [drm] Initialized via 2.7.4 20051116 on minor 0
[17179597.884000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179597.884000] agpgart: Device is in legacy mode, falling back to 2.x
[17179597.884000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17179597.884000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[17179598.164000] SCSI device sda: 1021184 2048-byte hdwr sectors (2091 MB)
[17179598.920000] sda: Write Protect is off
[17179598.920000] sda: Mode Sense: 3e 00 00 00
[17179598.920000] sda: assuming drive cache: write through
[17179598.920000]  sda: sda1
[17179600.180000] sd 0:0:0:0: Attached scsi removable disk sda
[17179600.204000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179601.068000] ath0: no IPv6 routers present
[17179601.744000] eth0: no IPv6 routers present
[17179602.072000] Bluetooth: Core ver 2.8
[17179602.072000] NET: Registered protocol family 31
[17179602.072000] Bluetooth: HCI device and connection manager initialized
[17179602.072000] Bluetooth: HCI socket layer initialized
[17179602.096000] Bluetooth: L2CAP ver 2.8
[17179602.096000] Bluetooth: L2CAP socket layer initialized
[17179602.144000] Bluetooth: RFCOMM socket layer initialized
[17179602.144000] Bluetooth: RFCOMM TTY layer initialized
[17179602.144000] Bluetooth: RFCOMM ver 1.7
[17179644.024000] UDF-fs: No partition found (1)
[17179710.552000] Unable to identify CD-ROM format.


Any good? 

Next is the output of 'less /etc/mtab/

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
/dev/hda2 /home ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/MP3 vfat rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=109,g
id=46,umask=007 0 0

I can see the mp3 player ok. I thought I would be able to as I have an icon on my desktop and in /media/. Oh yeah, I also managed to rename the player yesterday with the use of 'mtools' so it is working to a certain extent. Having to reboot everytime I want to see the player or flash drive is annoynung for sure, and now I can't see the contents of the drives.

Next is the output rom 'less /etc/fstab' for what it is worth

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=515a6a56-72ff-4eab-83b9-6341d94becd2 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda2
UUID=d80b5144-3f86-4382-80ae-239e28c201fc /home           ext3    defaults      
  0       2
# /dev/hda3
UUID=d0b153c3-ecf8-473a-a25e-56314832e9e2 none            swap    sw            
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


here is the output of 'lsusb' while the player is mounted

klittzzer@notebook:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 066f:821c SigmaTel, Inc. 
Bus 002 Device 001: ID 0000:0000  

there it is plugged in to USB 2.

Ok, I will now 'eject' the device and post the same outputs as above after plugging the player in while Ubuntu is running.

Please bear with me datakid, I know the post is gonna be long but you are the only person who has taken interest in helping me out with this. I really do appreciate the help geezer.

---

### Post by klittzzer on 2007-01-31
OK Datakid,

I have just plugged in my mp3 player while Ubuntu is up and running. As usual, it doesn't look like it is being recognised or mounted as I have no icon on either my desktop or in /media/

The output of 'dmesg'=

[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bfef000 (usable)
[17179569.184000]  BIOS-e820: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 447MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 114671
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110575 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e6010
[17179569.184000] ACPI: RSDT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1bffc3c0
[17179569.184000] ACPI: FADT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1bfffb10
[17179569.184000] ACPI: MADT (v001 INSYDE APIC_000 0x30303030 0000 0x00010200) @ 0x1bfffba0
[17179569.184000] ACPI: DSDT (v001 MTC___ 8650____ 0x00001000 INTL 0x02002036) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1592.369 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.216000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.216000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.232000] Memory: 444776k/458684k available (1910k kernel code, 13388k reserved, 1069k data, 308k init, 0k highmem)
[17179570.232000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.312000] Calibrating delay using timer specific routine.. 3188.80 BogoMIPS (lpj=6377618)
[17179570.312000] Security Framework v1.0.0 initialized
[17179570.312000] SELinux:  Disabled at boot.
[17179570.312000] Mount-cache hash table entries: 512
[17179570.312000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.312000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.312000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.312000] CPU: L2 cache: 1024K
[17179570.312000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179570.312000] Checking 'hlt' instruction... OK.
[17179570.328000] SMP alternatives: switching to UP code
[17179570.328000] Freeing SMP alternatives: 16k freed
[17179570.328000] checking if image is initramfs... it is
[17179570.920000] Freeing initrd memory: 5623k freed
[17179570.920000] ACPI: Core revision 20060707
[17179570.920000] ACPI: Looking for DSDT ... not found!
[17179570.968000] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
[17179570.968000] Total of 1 processors activated (3188.80 BogoMIPS).
[17179570.968000] ENABLING IO-APIC IRQs
[17179570.968000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.112000] Brought up 1 CPUs
[17179571.112000] migration_cost=0
[17179571.112000] NET: Registered protocol family 16
[17179571.112000] EISA bus registered
[17179571.112000] ACPI: bus type pci registered
[17179571.112000] PCI: PCI BIOS revision 2.10 entry at 0xe9c04, last bus=1
[17179571.112000] PCI: Using configuration type 1
[17179571.112000] Setting up standard PCI resources
[17179571.116000] ACPI: Interpreter enabled
[17179571.116000] ACPI: Using IOAPIC for interrupt routing
[17179571.116000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.116000] PCI: Probing PCI hardware (bus 00)
[17179571.116000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.116000] PCI quirk: region 1000-107f claimed by vt8235 PM
[17179571.116000] PCI quirk: region 1400-140f claimed by vt8235 SMB
[17179571.116000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179571.116000] Boot video device is 0000:01:00.0
[17179571.116000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.132000] ACPI: Embedded Controller [EC0] (gpe 1) interrupt mode.
[17179571.132000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[17179571.132000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 14 15)
[17179571.132000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[17179571.136000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 14 15)
[17179571.136000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179571.136000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179571.136000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179571.136000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179571.136000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179571.136000] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11
[17179571.136000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
[17179571.136000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179571.136000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179571.136000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179571.136000] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0
[17179571.136000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.136000] pnp: PnP ACPI init
[17179571.140000] pnp: PnP ACPI: found 9 devices
[17179571.140000] PnPBIOS: Disabled by ACPI PNP
[17179571.140000] PCI: Using ACPI for IRQ routing
[17179571.140000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.144000] pnp: 00:07: ioport range 0x330-0x331 has been reserved
[17179571.144000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179571.144000] pnp: 00:07: ioport range 0x1000-0x107f could not be reserved
[17179571.144000] pnp: 00:07: ioport range 0x1400-0x140f has been reserved
[17179571.144000] PCI: Bridge: 0000:00:01.0
[17179571.144000]   IO window: c000-dfff
[17179571.144000]   MEM window: c0000000-cfffffff
[17179571.144000]   PREFETCH window: 90000000-9fffffff
[17179571.144000] PCI: Bus 2, cardbus bridge: 0000:00:09.0
[17179571.144000]   IO window: 00001800-000018ff
[17179571.144000]   IO window: 00001c00-00001cff
[17179571.144000]   PREFETCH window: 20000000-21ffffff
[17179571.144000]   MEM window: 22000000-23ffffff
[17179571.144000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.144000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179571.144000] NET: Registered protocol family 2
[17179571.184000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.184000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179571.184000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179571.184000] TCP: Hash tables configured (established 16384 bind 8192)
[17179571.184000] TCP reno registered
[17179571.184000] audit: initializing netlink socket (disabled)
[17179571.184000] audit(1170243958.184:1): initialized
[17179571.184000] VFS: Disk quotas dquot_6.5.1
[17179571.184000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.184000] Initializing Cryptographic API
[17179571.184000] io scheduler noop registered
[17179571.184000] io scheduler anticipatory registered
[17179571.184000] io scheduler deadline registered
[17179571.184000] io scheduler cfq registered (default)
[17179571.184000] isapnp: Scanning for PnP cards...
[17179571.540000] isapnp: No Plug & Play device found
[17179571.572000] Real Time Clock Driver v1.12ac
[17179571.572000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.572000] mice: PS/2 mouse device common for all mice
[17179571.572000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.576000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.576000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.576000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.588000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.592000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.596000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.596000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.596000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.596000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.600000] EISA: Probing bus 0 at eisa.0
[17179571.600000] Cannot allocate resource for EISA slot 1
[17179571.600000] EISA: Detected 0 cards.
[17179571.600000] TCP bic registered
[17179571.600000] NET: Registered protocol family 1
[17179571.600000] NET: Registered protocol family 8
[17179571.600000] NET: Registered protocol family 20
[17179571.600000] Using IPI No-Shortcut mode
[17179571.600000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.600000] Freeing unused kernel memory: 308k freed
[17179571.628000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.740000] Capability LSM initialized
[17179572.772000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179572.772000] ACPI: Processor [CPU0] (supports 16 throttling states)
[17179573.084000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179573.084000] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[17179573.084000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[17179573.084000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179573.084000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 177
[17179573.084000] PCI: Via IRQ fixup for 0000:00:11.1, from 0 to 1
[17179573.084000] VP_IDE: chipset revision 6
[17179573.084000] VP_IDE: not 100% native mode: will probe irqs later
[17179573.084000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179573.084000]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[17179573.084000]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
[17179573.084000] Probing IDE interface ide0...
[17179573.500000] hda: WDC WD800VE-07HDT0, ATA DISK drive
[17179574.172000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.216000] Probing IDE interface ide1...
[17179575.080000] hdc: PHILIPS DVD+/-RW SDVD8431, ATAPI CD/DVD-ROM drive
[17179575.752000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.756000] hda: max request size: 128KiB
[17179575.764000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179575.764000] hda: cache flushes supported
[17179575.764000]  hda: hda1 hda2 hda3
[17179575.856000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.856000] Uniform CD-ROM driver Revision: 3.20
[17179576.228000] usbcore: registered new driver usbfs
[17179576.228000] usbcore: registered new driver hub
[17179576.232000] USB Universal Host Controller Interface driver v3.0
[17179576.232000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179576.232000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179576.232000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179576.232000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179576.232000] ACPI: Invalid IRQ link routing entry
[17179576.232000] ACPI: Unable to derive IRQ for device 0000:00:10.0
[17179576.232000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI - using IRQ 11
[17179576.232000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179576.232000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179576.232000] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[17179576.236000] usb usb1: configuration #1 chosen from 1 choice
[17179576.236000] hub 1-0:1.0: USB hub found
[17179576.236000] hub 1-0:1.0: 2 ports detected
[17179576.340000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179576.340000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179576.340000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179576.340000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179576.340000] ACPI: Invalid IRQ link routing entry
[17179576.340000] ACPI: Unable to derive IRQ for device 0000:00:10.1
[17179576.340000] ACPI: PCI Interrupt 0000:00:10.1[B]: no GSI - using IRQ 7
[17179576.340000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179576.340000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179576.340000] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[17179576.340000] usb usb2: configuration #1 chosen from 1 choice
[17179576.340000] hub 2-0:1.0: USB hub found
[17179576.340000] hub 2-0:1.0: 2 ports detected
[17179576.444000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179576.444000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179576.444000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179576.444000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179576.444000] ACPI: Invalid IRQ link routing entry
[17179576.444000] ACPI: Unable to derive IRQ for device 0000:00:10.2
[17179576.444000] ACPI: PCI Interrupt 0000:00:10.2[C]: no GSI - using IRQ 5
[17179576.444000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179576.444000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179576.444000] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[17179576.444000] usb usb3: configuration #1 chosen from 1 choice
[17179576.444000] hub 3-0:1.0: USB hub found
[17179576.444000] hub 3-0:1.0: 2 ports detected
[17179576.548000] PCI: Enabling device 0000:00:10.3 (0000 -> 0002)
[17179576.548000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179576.548000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179576.548000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179576.548000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179576.548000] ACPI: Invalid IRQ link routing entry
[17179576.548000] ACPI: Unable to derive IRQ for device 0000:00:10.3
[17179576.548000] ACPI: PCI Interrupt 0000:00:10.3[D]: no GSI - using IRQ 10
[17179576.548000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179576.548000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179576.548000] ehci_hcd 0000:00:10.3: irq 10, io mem 0x24011000
[17179576.548000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.548000] usb usb4: configuration #1 chosen from 1 choice
[17179576.548000] hub 4-0:1.0: USB hub found
[17179576.548000] hub 4-0:1.0: 6 ports detected
[17179576.684000] Attempting manual resume
[17179576.752000] kjournald starting.  Commit interval 5 seconds
[17179576.752000] EXT3-fs: mounted filesystem with ordered data mode.
[17179586.236000] input: PC Speaker as /class/input/input1
[17179586.392000] irda_init()
[17179586.392000] NET: Registered protocol family 23
[17179586.568000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.576000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.992000] ath_hal: module license 'Proprietary' taints kernel.
[17179586.992000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179587.064000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179587.064000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 11, using IRQ 23
[17179587.064000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[17179587.064000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKB] -> GSI 23 (level, low) -> IRQ 185
[17179587.064000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 9
[17179587.068000] eth0: VIA Rhine II at 0x1e200, 00:40:d0:8d:27:ed, IRQ 185.
[17179587.068000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 41e1.
[17179587.204000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.232000] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[17179587.240000] agpgart: AGP aperture is 128M @ 0xa0000000
[17179587.276000] wlan: 0.8.4.2 (0.9.2.1)
[17179587.440000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179587.440000] Yenta: CardBus bridge found at 0000:00:09.0 [1734:10ab]
[17179587.440000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179587.440000] Yenta: Routing CardBus interrupts to PCI
[17179587.440000] Yenta TI: socket 0000:00:09.0, mfunc 0x01001002, devctl 0x44
[17179587.500000] ath_rate_sample: 1.2 (0.9.2.1)
[17179587.508000] ath_pci: 0.9.4.5 (0.9.2.1)
[17179587.544000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179587.672000] Yenta: ISA IRQ mask 0x0000, PCI irq 169
[17179587.672000] Socket status: 30000006
[17179587.676000] PCI: Enabling device 0000:00:06.0 (0000 -> 0002)
[17179587.676000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 193
[17179588.256000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179588.256000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179588.256000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17179588.256000] wifi0: mac 7.8 phy 4.5 radio 5.6
[17179588.256000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17179588.256000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17179588.256000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17179588.256000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17179588.256000] wifi0: Use hw queue 8 for CAB traffic
[17179588.256000] wifi0: Use hw queue 9 for beacons
[17179588.364000] wifi0: Atheros 5212: mem=0x24000000, irq=193
[17179588.364000] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[17179588.364000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 5, using IRQ 22
[17179588.364000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179588.364000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179588.364000] PCI: Via IRQ fixup for 0000:00:11.6, from 5 to 9
[17179588.368000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179588.572000] NET: Registered protocol family 17
[17179588.724000] cs: IO port probe 0x100-0x3af: clean.
[17179588.728000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179588.728000] cs: IO port probe 0x820-0x8ff: clean.
[17179588.728000] cs: IO port probe 0xc00-0xcf7: clean.
[17179588.732000] cs: IO port probe 0xa00-0xaff: clean.
[17179588.808000] NET: Registered protocol family 10
[17179588.808000] lo: Disabled Privacy Extensions
[17179588.808000] IPv6 over IPv4 tunneling driver
[17179588.876000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179588.876000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 9
[17179588.876000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179588.992000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[17179589.048000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179589.064000] ts: Compaq touchscreen protocol output
[17179589.732000] lp: driver loaded but no devices found
[17179589.756000] Adding 1044216k swap on /dev/disk/by-uuid/d0b153c3-ecf8-473a-a25e-56314832e9e2.  Priority:-1 extents:1 across:1044216k
[17179589.840000] EXT3 FS on hda1, internal journal
[17179590.028000] kjournald starting.  Commit interval 5 seconds
[17179590.036000] EXT3 FS on hda2, internal journal
[17179590.036000] EXT3-fs: mounted filesystem with ordered data mode.
[17179594.456000] ACPI: AC Adapter [AC] (on-line)
[17179594.496000] ACPI: Battery Slot [BAT0] (battery absent)
[17179594.516000] ACPI: Power Button (FF) [PWRF]
[17179594.516000] ACPI: Lid Switch [LID]
[17179594.516000] ACPI: Sleep Button (CM) [SBTN]
[17179594.516000] ACPI: Power Button (CM) [PBTN]
[17179594.648000] ibm_acpi: ec object not found
[17179594.692000] pcc_acpi: loading...
[17179594.796000] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[17179597.480000] [drm] Initialized drm 1.0.1 20051102
[17179597.992000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 209
[17179597.992000] PCI: Via IRQ fixup for 0000:01:00.0, from 11 to 1
[17179597.992000] [drm] Initialized via 2.7.4 20051116 on minor 0
[17179598.028000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179598.028000] agpgart: Device is in legacy mode, falling back to 2.x
[17179598.028000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17179598.028000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[17179598.248000] apm: BIOS not found.
[17179599.196000] eth0: no IPv6 routers present
[17179599.404000] ath0: no IPv6 routers present
[17179602.268000] Bluetooth: Core ver 2.8
[17179602.268000] NET: Registered protocol family 31
[17179602.268000] Bluetooth: HCI device and connection manager initialized
[17179602.268000] Bluetooth: HCI socket layer initialized
[17179602.296000] Bluetooth: L2CAP ver 2.8
[17179602.296000] Bluetooth: L2CAP socket layer initialized
[17179602.340000] Bluetooth: RFCOMM socket layer initialized
[17179602.340000] Bluetooth: RFCOMM TTY layer initialized
[17179602.340000] Bluetooth: RFCOMM ver 1.7

see anything?

the output of 'less /etc/mtab/' =

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
/dev/hda2 /home ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

I can't see the device there?

The output of 'less /etc/fstab' =

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=515a6a56-72ff-4eab-83b9-6341d94becd2 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda2
UUID=d80b5144-3f86-4382-80ae-239e28c201fc /home           ext3    defaults      
  0       2
# /dev/hda3
UUID=d0b153c3-ecf8-473a-a25e-56314832e9e2 none            swap    sw            
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


and the output of 'lsusb' =

klittzzer@notebook:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

And as you can see? The mp3 player just isn't being recognised. Believe me I have spent a lot of time trying to sort this out. It just seems like Ubuntu doesn't support the automounting of usb devices. None of the devices I have tried hotplug or automount. I seem to be pretty much alone in this dilemma and as a result of that I have had no luck at all in these or any other forums or support sites. It is assumed that automount works. Gnome Volume Manager has all the requisite boxes ticked. There is a command in system/preferences/sessions/Start Up Programs which says "gnome-volume-manager --sm-disable" Has that anything to do with it? I have disabled it but the problem remains and I have entered "gnome-volume-manager" as a command in that box but it didn't make any difference.
I rckon it has something to do with permissions and my not having them. I may be wrong though?

Please try to help me datakid or anyone else. It is letting a good OS down. I don't want to go back to Windows because of this. 

thanks again

klittzzer

---

### Post by datakid on 2007-01-31
no hassles mate.

Hey, i'm off to bed cos it's late here in Oz, and my linux knowledge is two beans outta 5 ;), but I reckon between the two of us, we can get it done cobber - stick in there, we'll get it done.

---

### Post by klittzzer on 2007-02-01
Sorry I have been a while replying datakid, I have been out and about in London.

I have just spent a while searching for some answers to my little problem but have only found the same stuff I have already tried. I don't seem to be having much joy in this forum as oinly yourself has replied to my post. Perhaps the problem I have can't be solved and Ubuntu doesn't have the facility to hotplug devices such as the ones I have. It seems a little over the top to say that but I have not been able to hotplug anything while Ubuntu is up and running. I have a Logitech cordless USB mouse which is sold by the million probably and Ubuntu Edgy claims to be able to operate with this device seamlessly. When I plug it in, however, it just doesn't work. Ubuntu will only recognise it if I boot up with it plugged and even then it is limited to being only able to 'left, centre, and right click' the cursor moves very sporadically and thus the device is pretty much rendered useless. I have followed some config guides ([http://www.ubuntuforums.org/showthread.php?t=348115&highlight=Mouse+on+laptop](http://www.ubuntuforums.org/showthread.php?t=348115&highlight=Mouse+on+laptop)) for the device but have had no joy whatsoever. I also have a 'Logitech' game joypad, again that is sold worldwide by the million probably, which just doesn't get detected by Gnome, Nautilus, Ubuntu, or whatever best describes the part of my OS that doesn't work as it is purported to. 
That is the frustrating bit. According to the documentation here [https://help.ubuntu.com/community/UsbFlashDrives](https://help.ubuntu.com/community/UsbFlashDrives)
(I have tried the fixes at the end of the page) my devices should 'just work'. When I plug my flash drive or mp3 player (I don't need to tell you they are the same thing really) and try-

'sudo mount /dev/sda1 /mnt'

and/or

'sudo mount /dev/sda1 /media/mp3/ -t vfat

-in a terminal, I get the reply, 'Special Device doesn't exist' or something along those lines.
If I enter the above in a terminal with a device mounted from boot, it causes major instability in the entire desktop environment and results in the complete disabling of my using any USB device, even from boot. There are major conflicts as a result.

I have tried, I think, almost all of the walkthroughs in the Ubuntu Community docs to no avail.

Is it my Kernel? Or is it inherent with Ubuntu? Surely those claims that Ubuntu will automount or hotplug USB devices are true? I seem to be pretty much alone in this problem and, apart from yourself datakid, I have had absolutely no support in the issue. Are there any forums other than this which may be helpful to me? Gnome-Volume-Manager just doesn't seem to work on my laptop. I have reinstalled it and all that but no joy.

Do you or anyone else reckon I could get my computer fully functional with another distribution? I am not knocking Ubuntu, Gnome seems to be the problem (I had Gnome & KDE when I first installed Ubuntu Edgy and the problem remained the same in KDE) so if I get Suse and use gnome will I be in the same boat?

I can't understand why this problem is apparently unsolvable? Any help out there??????

nice one

klittzzer

---

