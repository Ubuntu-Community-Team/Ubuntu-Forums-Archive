---
title: "Stuck at 640X480 resolution SIS 315pro video problem"
date: 2017-07-07
forum: Hardware
---

### Post by mimuwhen on 2017-07-07
Hello everyone,

I have this machine which I installed Lubuntu on, everything went well after a couple of issues but once the installation finished and I booted up the machine, my display would only work at 680X480 resolution.  When I boot in recovery mode and during the installation process however, the display works at full resolution and everything is well.  Everything has been updated.  The video card is an SIS 315 pro as profiled here.  [https://h-node.org/videocards/view/en/645/Silicon-Integrated-Systems--SiS--315PRO-PCI-AGP-VGA-Display-Adapter](https://h-node.org/videocards/view/en/645/Silicon-Integrated-Systems--SiS--315PRO-PCI-AGP-VGA-Display-Adapter)

Here is the machine's specifications.  Other than this everything seems to be fine so far, can't figure it out and it's driving me a bit crazy.

```
computer
    descripción: Equipo de escritorio
    producto: MS-6712
    fabricante: MSI
    versión: 1.0
    serie: [REMOVED]
    anchura: 32 bits
    capacidades: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuración: chassis=desktop cpus=1
  *-core
       descripción: Placa base
       producto: MS-6712
       fabricante: MSI
       id físico: 0
       versión: 1.0
       serie: [REMOVED]
     *-firmware
          descripción: BIOS
          fabricante: American Megatrends Inc.
          id físico: 0
          versión: Version 07.00T
          date: 04/02/01
          tamaño: 64KiB
          capacidad: 192KiB
          capacidades: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          descripción: CPU
          producto: AMD Athlon(tm) XP
          fabricante: Advanced Micro Devices [AMD]
          id físico: 4
          información del bus: cpu@0
          versión: 6.10.0
          ranura: Socket-A
          tamaño: 1150MHz
          capacidad: 3GHz
          anchura: 32 bits
          reloj: 100MHz
          capacidades: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow eagerfpu 3dnowprefetch vmmcall
        *-cache:0
             descripción: L1 caché
             id físico: 5
             ranura: Internal Cache
             tamaño: 128KiB
             capacidad: 1MiB
             capacidades: synchronous internal write-back unified
             configuración: level=1
        *-cache:1
             descripción: L2 caché
             id físico: 6
             ranura: Internal Cache
             tamaño: 512KiB
             capacidad: 1MiB
             capacidades: synchronous internal write-back unified
             configuración: level=2
     *-memory
          descripción: Memoria de sistema
          id físico: 1
          tamaño: 1506MiB
     *-pci
          descripción: Host bridge
          producto: VT8377 [KT400/KT600 AGP] Host Bridge
          fabricante: VIA Technologies, Inc.
          id físico: 100
          información del bus: pci@0000:00:00.0
          versión: 80
          anchura: 32 bits
          reloj: 66MHz
          configuración: driver=agpgart-via latency=8
          recursos: irq:0 memoria:e0000000-e7ffffff
        *-pci
             descripción: PCI bridge
             producto: VT8237/VX700 PCI Bridge
             fabricante: VIA Technologies, Inc.
             id físico: 1
             información del bus: pci@0000:00:01.0
             versión: 00
             anchura: 32 bits
             reloj: 66MHz
             capacidades: pci pm normal_decode bus_master cap_list
        *-display NO RECLAMADO
             descripción: VGA compatible controller
             producto: 315PRO PCI/AGP VGA Display Adapter
             fabricante: Silicon Integrated Systems [SiS]
             id físico: 5
             información del bus: pci@0000:00:05.0
             versión: 00
             anchura: 32 bits
             reloj: 66MHz
             capacidades: pm vga_controller bus_master cap_list
             configuración: latency=39 maxlatency=16 mingnt=3
             recursos: memoria:c0000000-cfffffff memoria:dffc0000-dfffffff ioport:ec00(size=128) memoria:c0000-dffff
        *-communication
             descripción: Communication controller
             producto: PCI 1 port parallel adapter
             fabricante: MosChip Semiconductor Technology Ltd.
             id físico: 7
             información del bus: pci@0000:00:07.0
             versión: 01
             anchura: 32 bits
             reloj: 33MHz
             configuración: driver=parport_pc latency=32
             recursos: irq:18 ioport:e800(size=8) ioport:e400(size=8) ioport:e000(size=8) ioport:dc00(size=8) ioport:d800(size=8) ioport:d400(size=16)
        *-usb:0
             descripción: USB controller
             producto: VT82xx/62xx UHCI USB 1.1 Controller
             fabricante: VIA Technologies, Inc.
             id físico: 10
             información del bus: pci@0000:00:10.0
             versión: 80
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=32
             recursos: irq:21 ioport:c800(size=32)
           *-usbhost
                producto: UHCI Host Controller
                fabricante: Linux 4.8.0-56-generic uhci_hcd
                id físico: 1
                información del bus: usb@2
                nombre lógico: usb2
                versión: 4.08
                capacidades: usb-1.10
                configuración: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             descripción: USB controller
             producto: VT82xx/62xx UHCI USB 1.1 Controller
             fabricante: VIA Technologies, Inc.
             id físico: 10.1
             información del bus: pci@0000:00:10.1
             versión: 80
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=32
             recursos: irq:21 ioport:cc00(size=32)
           *-usbhost
                producto: UHCI Host Controller
                fabricante: Linux 4.8.0-56-generic uhci_hcd
                id físico: 1
                información del bus: usb@3
                nombre lógico: usb3
                versión: 4.08
                capacidades: usb-1.10
                configuración: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             descripción: USB controller
             producto: VT82xx/62xx UHCI USB 1.1 Controller
             fabricante: VIA Technologies, Inc.
             id físico: 10.2
             información del bus: pci@0000:00:10.2
             versión: 80
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm uhci bus_master cap_list
             configuración: driver=uhci_hcd latency=32
             recursos: irq:21 ioport:d000(size=32)
           *-usbhost
                producto: UHCI Host Controller
                fabricante: Linux 4.8.0-56-generic uhci_hcd
                id físico: 1
                información del bus: usb@4
                nombre lógico: usb4
                versión: 4.08
                capacidades: usb-1.10
                configuración: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   descripción: Ratón
                   producto: USB Optical Mouse
                   fabricante: Logitech
                   id físico: 1
                   información del bus: usb@4:1
                   versión: 43.01
                   capacidades: usb-2.00
                   configuración: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:3
             descripción: USB controller
             producto: USB 2.0
             fabricante: VIA Technologies, Inc.
             id físico: 10.3
             información del bus: pci@0000:00:10.3
             versión: 82
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm ehci bus_master cap_list
             configuración: driver=ehci-pci latency=32
             recursos: irq:21 memoria:dffaff00-dffaffff
           *-usbhost
                producto: EHCI Host Controller
                fabricante: Linux 4.8.0-56-generic ehci_hcd
                id físico: 1
                información del bus: usb@1
                nombre lógico: usb1
                versión: 4.08
                capacidades: usb-2.00
                configuración: driver=hub slots=6 speed=480Mbit/s
        *-isa
             descripción: ISA bridge
             producto: VT8235 ISA Bridge
             fabricante: VIA Technologies, Inc.
             id físico: 11
             información del bus: pci@0000:00:11.0
             versión: 00
             anchura: 32 bits
             reloj: 33MHz
             capacidades: isa pm bus_master cap_list
             configuración: latency=0
        *-ide
             descripción: IDE interface
             producto: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             fabricante: VIA Technologies, Inc.
             id físico: 11.1
             información del bus: pci@0000:00:11.1
             versión: 06
             anchura: 32 bits
             reloj: 33MHz
             capacidades: ide pm bus_master cap_list
             configuración: driver=pata_via latency=32
             recursos: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
        *-multimedia
             descripción: Multimedia audio controller
             producto: VT8233/A/8235/8237 AC97 Audio Controller
             fabricante: VIA Technologies, Inc.
             id físico: 11.5
             información del bus: pci@0000:00:11.5
             versión: 50
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm cap_list
             configuración: driver=snd_via82xx latency=0
             recursos: irq:22 ioport:c400(size=256)
        *-network
             descripción: Ethernet interface
             producto: VT6102/VT6103 [Rhine-II]
             fabricante: VIA Technologies, Inc.
             id físico: 12
             información del bus: pci@0000:00:12.0
             nombre lógico: enp0s18
             versión: 74
             serie: [REMOVED]
             tamaño: 100Mbit/s
             capacidad: 100Mbit/s
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuración: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             recursos: irq:23 ioport:c000(size=256) memoria:dffafe00-dffafeff
     *-scsi:0
          id físico: 2
          nombre lógico: scsi0
          capacidades: emulated
        *-disk
             descripción: ATA Disk
             producto: ST340810A
             fabricante: Seagate
             id físico: 0.0.0
             información del bus: scsi@0:0.0.0
             nombre lógico: /dev/sda
             versión: 3.39
             serie: [REMOVED]
             tamaño: 37GiB (40GB)
             capacidades: partitioned partitioned:dos
             configuración: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=942abb48
           *-volume:0
                descripción: partición EXT4
                fabricante: Linux
                id físico: 1
                información del bus: scsi@0:0.0.0,1
                nombre lógico: /dev/sda1
                nombre lógico: /
                versión: 1.0
                serie: [REMOVED]
                tamaño: 35GiB
                capacidad: 35GiB
                capacidades: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuración: created=2017-06-27 01:36:27 filesystem=ext4 lastmountpoint=/ modified=2017-06-28 18:52:50 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-06-28 18:51:53 state=mounted
           *-volume:1
                descripción: Extended partition
                id físico: 2
                información del bus: scsi@0:0.0.0,2
                nombre lógico: /dev/sda2
                tamaño: 1534MiB
                capacidad: 1534MiB
                capacidades: primary extended partitioned partitioned:extended
              *-logicalvolume
                   descripción: Linux swap / Solaris partition
                   id físico: 5
                   nombre lógico: /dev/sda5
                   capacidad: 1534MiB
                   capacidades: nofs
     *-scsi:1
          id físico: 3
          nombre lógico: scsi1
          capacidades: emulated
        *-cdrom:0
             descripción: DVD writer
             producto: DVD RW DW-Q28A
             fabricante: SONY
             id físico: 0.0.0
             información del bus: scsi@1:0.0.0
             nombre lógico: /dev/cdrom
             nombre lógico: /dev/dvd
             nombre lógico: /dev/dvdrw
             nombre lógico: /dev/sr0
             versión: KYS3
             capacidades: removable audio cd-r cd-rw dvd dvd-r
             configuración: ansiversion=5 status=nodisc
        *-cdrom:1
             descripción: CD-R/CD-RW writer
             id físico: 0.1.0
             información del bus: scsi@1:0.1.0
             nombre lógico: /dev/cdrw
             nombre lógico: /dev/sr1
             capacidades: audio cd-r cd-rw
             configuración: status=nodisc
```

---

### Post by Yellow Pasque on 2017-07-07
Usually 640x480 means fbdev driver is being loaded. You should be able to get a better resolution with generic vesa driver. Make an /etc/X11/xorg.conf file with a text editor. Copy/paste the block of text below:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Log out or restart.

---

### Post by oldfred on 2017-07-07
Recovery mode uses nomodeset.

If you boot to grub and add nomodeset do you then get full resolution.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Do not upgrade to a new Ubuntu.

 The stock kernel of Ubuntu 17.04 is doing away with Direct Rendering Manager (DRM) support for a number of ancient graphics processors.
3Dfx Banshee/Voodoo3+, ATI Rage 128, Matrox G200/G400, SIS, VIA, and Savage hardware
This was done because they expose insecure APIs to user-space. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276)

---

### Post by mimuwhen on 2017-08-04
Hello guys, 

I had to abandon this project because the computer was damaged.  Today I decided to start over, I changed out the motherboard with a different one.  Curiously enough I re-used the old hard drive and the new motherboard booted up fine with the old installation, even recognized the new processor and everything.  Because I thought this could lead to certain hardware issues, I decided to re-install lubuntu anyway.  I wasn't worried about the same issue happening again as I thought that was due to to the other graphics card, this motherboard now has an on board graphics chip.  However that was a mistake as after installing lubuntu on this motherboard i ended up with the SAME problem as the old motherboard.  I should have left it the way it was!

> **Temüjin said:**
> Usually 640x480 means fbdev driver is being loaded. You should be able to get a better resolution with generic vesa driver. Make an /etc/X11/xorg.conf file with a text editor. Copy/paste the block of text below:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Log out or restart.


I'm not sure if this solution applies to this new motherboard but I tried anyway but was not allowed to add the xorg.config file into the folder due to lack of permissions.  Tried to change the folder permissions with no success.  Am not sure how to get this done.  

> Recovery mode uses nomodeset.

If you boot to grub and add nomodeset do you then get full resolution.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Do not upgrade to a new Ubuntu.

 The stock kernel of Ubuntu 17.04 is doing away with Direct Rendering  Manager (DRM) support for a number of ancient graphics processors.
3Dfx Banshee/Voodoo3+, ATI Rage 128, Matrox G200/G400, SIS, VIA, and Savage hardware
This was done because they expose insecure APIs to user-space. [https://bugs.launchpad.net/ubuntu/+s...x/+bug/1680276]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276")

Changing the setting at the grub menu using "e" makes it work but only during one boot.  By the next boot the setting is back where It was originally.  However I dont think that even that is fixing it.  I think the reason it goes back into full resolution when I edit the setting in grub is simply because I'm going into grub.  Everytime I go into grub and exit using ctrl-X or when I go into one of the advanced options, the computer boots at full resolution during one boot.  By the next boot it goes back to lo resolution. This is true even if I don't actually change the setting.  The simple act of me doing something in the grub menu makes it boot full resolution. 

> [SIZE=4]**How to permanently set kernel boot options on an installed OS (not wubi)**[/SIZE]

To permanently change the default kernel boot options, press ALT+F2 or   open a terminal from system > accessories > terminal. Type in the  following command:

     Code:
     gksudo gedit /etc/default/grub 
a text editor will open with the grub configuration file. Near the top of that file you will see something very similar to this:
     Code:
     GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
GRUB_CMDLINE_LINUX="" 
add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line, so for instance:

     Code:
     GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**
GRUB_CMDLINE_LINUX="" 
Save the file and exit gedit. If you have to add kernel options that contain quotation marks, add them as such:

     Code:
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=[COLOR=Red]\"[/COLOR]Linux[COLOR=Red]\"[/COLOR]" 
Now in the terminal, run the following command to update your grub configuration with the new default settings:
     Code:
     sudo update-grub 
Thats all.

I tried this method with no results.  No matter how I edit it, the problem still remains.

---

### Post by mimuwhen on 2017-08-06
Another thing I just discovered is that I can make it work by simply pressing ctrl-x at the main grub menu.  That's it, I dont even have to edit anything or select anything different.  Just press Ctrl-X at the grub screen and hit enter to let it boot and it will give me full resolution. I don't know if that offers up some type of clue.

---

