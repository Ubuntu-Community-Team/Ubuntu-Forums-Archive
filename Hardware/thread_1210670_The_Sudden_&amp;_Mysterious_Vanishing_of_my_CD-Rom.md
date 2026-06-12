---
title: "The Sudden &amp; Mysterious Vanishing of my CD-Rom"
date: 2009-07-11
forum: Hardware
---

### Post by Kevide on 2009-07-11
Hello, everyone.

I've spent the last two days searching for similar issues, but have so far not found anything too helpful to my problem. Two days ago, my CD-Rom disappeared from Places/Computer. I was briefly able to get it back yesterday, after rechecking the BIOS. (Booted from live CD, burned an .ISO image, etc.) Only to find it gone again this morning.

I am running Ubuntu 9.04 Jaunty.

Here is the output from “gedit /etc/fstab”

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3e026514-d510-4d7a-adce-20ea4ddaa4d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b45c3a9e-7735-4024-a000-ae796115cc2f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

From “gedit /etc/mstab”

```
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-13-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/kevin/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=kevin 0 0
```

And “lshw”

```

 description: Computer

    width: 32 bits

  *-core

       description: Motherboard

       physical id: 0

     *-memory

          description: System memory

          physical id: 0

          size: 970MiB

     *-cpu

          product: Mobile Intel(R) Pentium(R) 4 CPU 2.80GHz

          vendor: Intel Corp.

          physical id: 1

          bus info: cpu@0

          version: 15.4.1

          serial: 0000-0F41-0000-0000-0000-0000

          size: 18EHz

          width: 32 bits

          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl est tm2 cid xtpr

          configuration: id=0

        *-logicalcpu:0

             description: Logical CPU

             physical id: 0.1

             width: 32 bits

             capabilities: logical

        *-logicalcpu:1

             description: Logical CPU

             physical id: 0.2

             width: 32 bits

             capabilities: logical

     *-pci

          description: Host bridge

          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller

          vendor: Intel Corporation

          physical id: 100

          bus info: pci@0000:00:00.0

          version: 02

          width: 32 bits

          clock: 33MHz

          configuration: driver=agpgart-intel module=intel_agp

        *-system:0 UNCLAIMED

             description: System peripheral

             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller

             vendor: Intel Corporation

             physical id: 0.1

             bus info: pci@0000:00:00.1

             version: 02

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: latency=0

        *-system:1 UNCLAIMED

             description: System peripheral

             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller

             vendor: Intel Corporation

             physical id: 0.3

             bus info: pci@0000:00:00.3

             version: 02

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: latency=0

        *-display:0 UNCLAIMED

             description: VGA compatible controller

             product: 82852/855GM Integrated Graphics Device

             vendor: Intel Corporation

             physical id: 2

             bus info: pci@0000:00:02.0

             version: 02

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: latency=0

        *-display:1 UNCLAIMED

             description: Display controller

             product: 82852/855GM Integrated Graphics Device

             vendor: Intel Corporation

             physical id: 2.1

             bus info: pci@0000:00:02.1

             version: 02

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: latency=0

        *-usb:0

             description: USB Controller

             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1

             vendor: Intel Corporation

             physical id: 1d

             bus info: pci@0000:00:1d.0

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

        *-usb:1

             description: USB Controller

             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2

             vendor: Intel Corporation

             physical id: 1d.1

             bus info: pci@0000:00:1d.1

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

        *-usb:2

             description: USB Controller

             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3

             vendor: Intel Corporation

             physical id: 1d.2

             bus info: pci@0000:00:1d.2

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master

             configuration: driver=uhci_hcd latency=0 module=uhci_hcd

        *-usb:3

             description: USB Controller

             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller

             vendor: Intel Corporation

             physical id: 1d.7

             bus info: pci@0000:00:1d.7

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: driver=ehci_hcd latency=0 module=ehci_hcd

        *-pci

             description: PCI bridge

             product: 82801 Mobile PCI Bridge

             vendor: Intel Corporation

             physical id: 1e

             bus info: pci@0000:00:1e.0

             version: 83

             width: 32 bits

             clock: 33MHz

             capabilities: pci bus_master

           *-firewire

                description: FireWire (IEEE 1394)

                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

                vendor: Texas Instruments

                physical id: 4

                bus info: pci@0000:01:04.0

                version: 00

                width: 32 bits

                clock: 33MHz

                capabilities: bus_master cap_list

                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394

           *-pcmcia

                description: CardBus bridge

                product: PCI1510 PC card Cardbus Controller

                vendor: Texas Instruments

                physical id: 5

                bus info: pci@0000:01:05.0

                version: 00

                width: 32 bits

                clock: 33MHz

                capabilities: pcmcia bus_master cap_list

                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket

           *-network:0

                description: Ethernet interface

                product: BCM4401 100Base-T

                vendor: Broadcom Corporation

                physical id: 6

                bus info: pci@0000:01:06.0

                logical name: eth0

                version: 01

                serial: 00:03:25:21:9e:3b

                width: 32 bits

                clock: 33MHz

                capabilities: bus_master cap_list ethernet physical

                configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

           *-network:1

                description: Network controller

                product: BCM4306 802.11b/g Wireless LAN Controller

                vendor: Broadcom Corporation

                physical id: 9

                bus info: pci@0000:01:09.0

                version: 03

                width: 32 bits

                clock: 33MHz

                capabilities: bus_master

                configuration: driver=b43-pci-bridge latency=64 module=ssb

        *-isa

             description: ISA bridge

             product: 82801DBM (ICH4-M) LPC Interface Bridge

             vendor: Intel Corporation

             physical id: 1f

             bus info: pci@0000:00:1f.0

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: isa bus_master

             configuration: latency=0

        *-ide

             description: IDE interface

             product: 82801DBM (ICH4-M) IDE Controller

             vendor: Intel Corporation

             physical id: 1f.1

             bus info: pci@0000:00:1f.1

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: ide bus_master

             configuration: driver=ata_piix latency=0

        *-multimedia

             description: Multimedia audio controller

             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller

             vendor: Intel Corporation

             physical id: 1f.5

             bus info: pci@0000:00:1f.5

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

        *-communication UNCLAIMED

             description: Modem

             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller

             vendor: Intel Corporation

             physical id: 1f.6

             bus info: pci@0000:00:1f.6

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: cap_list

             configuration: latency=0

  *-network:0

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:90:4b:c6:16:6c

       capabilities: ethernet physical wireless

       configuration: broadcast=yes ip=192.168.0.11 multicast=yes wireless=IEEE 802.11bg

  *-network:1 DISABLED

       description: Ethernet interface

       physical id: 2

       logical name: vboxnet0

       serial: 00:76:62:6e:65:74

       capabilities: ethernet physical

       configuration: broadcast=yes multicast=yes

  *-network:2 DISABLED

       description: Ethernet interface

       physical id: 3

       logical name: pan0

       serial: 86:73:22:c8:0b:26

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```

The machine is a Gateway 7324GZ, Pentium 4 machine. Running Jaunty Jackalope, Ubuntu 9.04, updated last shortly before this began. 

If anyone can help me solve this mystery, I would be greatly appreciative. 

Best.

---

### Post by Kevide on 2009-07-11
Also, the following terminal commands were attempted:
```
mount /dev/cdrom
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab
 
```

```

mount /dev/scd0

mount: special device /dev/scd0 does not exist 
```

```

mount /media/cdrom0

mount: special device /dev/scd0 does not exist
 
```

```

mount /dev/scd0/media/cdrom0

mount: can't find /dev/scd0/media/cdrom0 in /etc/fstab or /etc/mtab
 
```

---

### Post by earthpigg on 2009-07-12
does the problem persist when booting from a live cd?

what about when booting from a thumb drive, both with and without a cd inserted in the drive?

hardware failure is a possibility, trying to rule that out.

cd drives are _not_ either broken or not-broken... i myself have experienced a cd drive that was* kind of sort of* broken.

---

### Post by Kevide on 2009-07-12
I am having trouble booting into the live cd. This occured yesterday as well but I was able to get the live cd up over the next several consecutive reboots, though not any longer. Have not tried the thumb yet.

---

### Post by darco on 2009-07-12
Did you update your kernel? If so, .31.2 is having issues w/optic drives...

darco

---

### Post by Kevide on 2009-07-12
Possibly. I ran update manager a day or so before this began. My comand may I use to determine what version of the kernel I'm running?

---

### Post by darco on 2009-07-12
```
uname -r
```

I doubt you have it then...its not in the repos yet and you would have  gone out of your way to d/l it

darco

---

### Post by earthpigg on 2009-07-12
> **Kevide said:**
> I am having trouble booting into the live cd. This occured yesterday as well but I was able to get the live cd up over the next several consecutive reboots, though not any longer.

im sorry to say, but this is sounding increasingly like a hardware failure.

if you dont want to risk wasting money on a new cd drive, you could borrow a buddies (or another computer sitting around your house), switch it out for yours, and see if that suddenly resolves everything - that would tell you that your cd drive is indeed busted.... well, on its deathbed anyways.




the thing to remember about switching hardware components around: if the plug fits, it is probably designed to fit and whatever it is will probably work perfectly. :popcorn:

---

### Post by Kevide on 2009-07-12
@ Darco. Still running 2.6.28-13-generic, thank you for the code.

@ Earthpig, I'll have to try that later today. Thanks. I'll report back soon-like.

Also, I've heard that Brasero can cause harm to cdroms. Is this a known issue, or paranoia

---

### Post by Kevide on 2009-07-13
Turns out replacing the drive was not neccessary. The boot order in my BIOS had previously been:
1:cd/DVD
2:HDD
3:FDD

I changed this to:
1:FDD
2:cd/DVD
3:HDD

And it worked. My CDROM is back an functional. 

Eathpigg, darco, thank you both for advice and your patience.

---

