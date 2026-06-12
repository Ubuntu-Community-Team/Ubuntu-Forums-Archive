---
title: "Attempting to get YUNO-VFD serial display to work"
date: 2015-04-24
forum: Hardware
---

### Post by rohan! on 2015-04-24
Hi,

I'm having some problems figuring out how to get a Serial VFD working on Ubuntu 14.04.

The VFD is part of an Aures point of sale unit. The specs say it's a YUNO-VFD.

I've not had much success in searching for information regarding this display online, though I think that it is manufactured by Aures.

So, firstly, I'm presuming that I need to load a driver, though as it's an uncommon display I'm not sure that there will be drivers... is there a generic driver for serial VFDs??

Secondly, I've tried to see which device it is in my /dev folder using dmesg and setserial (outputs below), but there are 5 different serial TTYs... how do I know which one refers to the display?

```

$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    1.630314] 00:02: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.651110] 00:03: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
[    1.671896] 00:04: ttyS2 at I/O 0x3e8 (irq = 5, base_baud = 115200) is a 16550A
[    1.692722] 00:05: ttyS3 at I/O 0x2e8 (irq = 10, base_baud = 115200) is a 16550A
[    1.713561] 00:06: ttyS4 at I/O 0x2d8 (irq = 6, base_baud = 115200) is a 16550A
[    1.734392] 00:07: ttyS5 at I/O 0x2d0 (irq = 11, base_baud = 115200) is a 16550A

```

```

$ setserial -g /dev/ttyS[0-5]
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: 16550A, Port: 0x03e8, IRQ: 5
/dev/ttyS3, UART: 16550A, Port: 0x02e8, IRQ: 10
/dev/ttyS4, UART: 16550A, Port: 0x02d8, IRQ: 6
/dev/ttyS5, UART: 16550A, Port: 0x02d0, IRQ: 11

```

I'm really struggling here. Any input would be greatly appreciated.

---

### Post by dino99 on 2015-04-24
here is an old updated howto; hopes it will help  [https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)
the ares support [http://www.aures-support.fr/UK/utilities/](http://www.aures-support.fr/UK/utilities/)  but 'yuno' is unknown, so lshw might help to identify the hardware.

[http://www.binarytides.com/linux-lshw-command/](http://www.binarytides.com/linux-lshw-command/)

---

### Post by rohan! on 2015-04-27
Hey,

Thanks for the quick response. I tried the howto, but didn't have any success: minicom says offline at the bottom, and the suggested alternative of using screen just gives me a blinking cursor. Neither method causes anything to happen on the serial display.

Below is the output of lshw. I've highlighted the part that seems relevant to me, where it says "serial" is unclaimed. Does this suggest I need a driver for the device?

```

$ lshw
ubuntu
    description: Hand Held Computer
    product: X72 (System SKUNumber)
    vendor: Quanta
    version: 03
    serial: QCQX01F50201QM
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=handheld family=BayTrail System sku=System SKUNumber uuid=00000000-0000-0000-0000-5403F50527F8
  *-core
       description: Motherboard
       product: X72
       vendor: Quanta
       physical id: 0
       version: 03
       serial: QCQX01F50201QM
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies Ltd.
          physical id: 0
          version: X72P-008
          date: 10/20/2014
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video pc98 acpi usb biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU  J1900  @ 1.99GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU  J1900  @ 1.99GHz
          slot: CPU 1
          size: 1333MHz
          capacity: 4GHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms cpufreq
          configuration: cores=4 enabledcores=4 threads=1
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back unified
     *-cache
          description: L1 cache
          physical id: 5
          slot: L1 Cache
          size: 24KiB
          capacity: 24KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: TS512MSK64W6H
             vendor: Transcend
             physical id: 0
             serial: 00101116
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM [empty]
             physical id: 1
             slot: DIMM1
     *-pci
          description: Host bridge
          product: ValleyView SSA-CUnit
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: ValleyView Gen7
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:107 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:2050(size=8)
        *-storage
             description: SATA controller
             product: ValleyView 6-Port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:104 ioport:2048(size=8) ioport:205c(size=4) ioport:2040(size=8) ioport:2058(size=4) ioport:2020(size=32) memory:d0814000-d08147ff
        *-usb
             description: USB controller
             product: ValleyView USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:103 memory:d0800000-d080ffff
        *-generic
             description: Encryption controller
             product: ValleyView SEC
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:106 memory:d0700000-d07fffff memory:d0600000-d06fffff
        *-multimedia
             description: Audio device
             product: ValleyView High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:108 memory:d0810000-d0813fff
        *-pci:0
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096)
        *-pci:1
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096)
        *-pci:2
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:1000(size=4096) memory:d0500000-d05fffff ioport:d0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: p2p1
                version: 18
                serial: 54:03:f5:05:27:f8
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-2_0.0.4 03/27/12 ip=192.133.1.28 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:105 ioport:1000(size=256) memory:d0500000-d0500fff memory:d0400000-d0403fff
        *-pci:3
             description: PCI bridge
             product: ValleyView PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:5000(size=4096)
        *-isa
             description: ISA bridge
             product: ValleyView Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
[B][COLOR="#FF0000"]        *-serial UNCLAIMED
             description: SMBus
             product: ValleyView SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:d0814800-d081481f ioport:2000(size=32)[/COLOR][/B]
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Techman SCSH01
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1.08
             serial: 15051001342
             size: 59GiB (64GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=4dbf8544-f8f0-46c4-aa7e-ab41bc43427e sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: a29d-8a76
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EFI partition
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot
                version: 1.0
                serial: aceb0561-6bed-47b3-9056-4785cb3ada2d
                size: 244MiB
                capabilities: extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2015-04-27 08:21:19 mount.fstype=ext2 mount.options=rw,relatime mounted=2015-04-27 08:21:19 state=mounted
           *-volume:2
                description: LVM Physical Volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: NbuL13-F3bO-Z6xn-mFa1-NEQx-5Rxv-cSnuTA
                size: 58GiB
                capabilities: multi lvm2
  *-battery
       product: Smart Battery
       vendor: Intel Corp.
       physical id: 1
       version: 2010
       serial: 1.0
       slot: Rear

```

Any more suggestions would be greatly appreciated.

---

### Post by dino99 on 2015-04-27
does not know what 'unclaimed' really mean here. That baytrail chipset got more support recently; maybe try the 3.19 kernel; you can downlad the 4 files (2 headers + 2 images) into an empty folder from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) , then do 'sudo dpkg -i *'

[https://www.happyassassin.net/2014/06/27/a-long-winded-and-probably-inaccurate-guide-to-the-kernel-development-process-particularly-regarding-baytrail/](https://www.happyassassin.net/2014/06/27/a-long-winded-and-probably-inaccurate-guide-to-the-kernel-development-process-particularly-regarding-baytrail/)

---

### Post by dino99 on 2015-04-27
does not know what 'unclaimed' really mean here. That baytrail chipset got more support recebtly; maybe try the 3.19 kernel; you can downlad the 4 files (2 headers + 2 images) into an empty folder from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) , then do 'sudo dpkg -i *'

[https://www.happyassassin.net/2014/06/27/a-long-winded-and-probably-inaccurate-guide-to-the-kernel-development-process-particularly-regarding-baytrail/](https://www.happyassassin.net/2014/06/27/a-long-winded-and-probably-inaccurate-guide-to-the-kernel-development-process-particularly-regarding-baytrail/)

you probably also try to update ids:
sudo update-pciids
sudo update usbids

---

### Post by rohan! on 2015-04-27
Thanks for the response again. 

I attempted to install 3.19 kernel but it caused lots of problems (no network, no keyboard...). So instead I tried to use the latest Ubuntu live version (which ships with 3.19). I still get that serial unclaimed issue though. Attempted to set up a getty task for serial devices and using screen to connect still doesn't work (the getty instance appears to crash when I connect the screen instance).

Not really sure where to go from here.

Thank you ever so much for the help so far.

---

### Post by dino99 on 2015-04-27
when searching about 'linux/ubuntu baytrail kernel driver' we can find some kernel's bugs and issue about acpi/sound. Also seen some users surprised by the lspci output, to be quite 'exotic' compared to what was usually expected (probably some specific hard chipset links that disturb the kernel) so its seems that either the kernel or the gallium driver still needs more work (or both)

---

### Post by dino99 on 2015-04-27
Also found that 'yuno' pdf (quite long to load) to says that the serial port is a usual RS232 one
[http://support.j2rs.com/Documents/TechnicalDocs/YUNO_User_Manual_V1.0%28EN%29.pdf](http://support.j2rs.com/Documents/TechnicalDocs/YUNO_User_Manual_V1.0%28EN%29.pdf)

[http://www.cyberciti.biz/faq/find-out-linux-serial-ports-with-setserial/](http://www.cyberciti.biz/faq/find-out-linux-serial-ports-with-setserial/)
[https://help.ubuntu.com/community/Minicom](https://help.ubuntu.com/community/Minicom)

---

### Post by rohan! on 2015-04-28
Ok. Not sure what I've changed, but am now getting some junk characters printed to the display (see attached), which I guess is an improvement. This happens when the getty instance launches for ttyS5 (can confirm but stopping and starting it from the commandline). Trying to connect minicom or screen to ttyS5 doesn't seem do anything. lshw still says that serial is unclaimed.

[IMG]https://pbs.twimg.com/media/CDqpYm_UkAA0ebz.jpg:large[/IMG]

Thanks again

---

### Post by rohan! on 2015-04-28
Yay! I got it working. Turns out that the baud rate needed to be set to 9600 as opposed to 115200.

```

$ cat /etc/init/ttyS5
# ttyS5 - getty
#
# This service maintains a getty on ttyS5 from the point the system is
# started until it is shut down again

start on stopped rc RUNLEVEL=[12345]
stop on runlevel [!12345]

respawn
[COLOR=#ff0000]**exec /sbin/agetty -h  ttyS5 9600 vt102**[/COLOR]

```

[IMG]https://pbs.twimg.com/media/CDq1TjXVIAAsN66.jpg:large[/IMG]

Thanks so so much for all the help :)

---

### Post by dino99 on 2015-04-28
as always the devil is hidden in the details :p

---

### Post by fbianco2 on 2015-05-03
Hey rohan!

Which kernel are you using now ?

(solved with 3.19, at least I see the VDF display)

---

