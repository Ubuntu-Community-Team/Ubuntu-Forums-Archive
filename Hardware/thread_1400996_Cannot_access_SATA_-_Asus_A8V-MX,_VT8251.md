---
title: "Cannot access SATA - Asus A8V-MX, VT8251"
date: 2010-02-07
forum: Hardware
---

### Post by zenon222 on 2010-02-07
I am running an ASUS A8V-MX which has a VIA VT8251 SATA / AHCI controller.  Linux cannot find either of the drives in Karmic.  

I have tried the kernel switch pci=nomsi by editing the /boot/grub/grub.cfg

```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bb1cd0ab-7955-48bc-bfac-4bf56970ec28
    linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=bb1cd0ab-7955-48bc-bfac-4bf56970ec28 ro  splash vga=795 pci=NOMSI   quiet splash
    initrd    /boot/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bb1cd0ab-7955-48bc-bfac-4bf56970ec28
    linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=bb1cd0ab-7955-48bc-bfac-4bf56970ec28 ro single  splash vga=795 pci=NOMSI
    initrd    /boot/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/10_linux ###
```As best I can tell from the screen dump below (I filtered out all that was not VT82xx specific) linux is finding the the controller and recognizing that it's a SATA controller, but yet I still cannot find my drives in gaprted.

Here is my output from lspci -v

```
zenon@zenon-ubuntu:~$ lspci -v
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000cfff
    Memory behind bridge: ff500000-ff5fffff
    Prefetchable memory behind bridge: 7ff00000-bfefffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
    Flags: bus master, medium devsel, latency 64, IRQ 26
    I/O ports at ec00 [size=8]
    I/O ports at e880 [size=4]
    I/O ports at e800 [size=8]
    I/O ports at e480 [size=4]
    I/O ports at e400 [size=16]
    Memory at ff6ffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
    Subsystem: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
    Flags: bus master, medium devsel, latency 32
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at fc00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 20
    I/O ports at e080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 22
    I/O ports at e000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 23
    I/O ports at d880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
    Subsystem: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
    Flags: medium devsel
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
    Subsystem: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
    Flags: bus master, medium devsel, latency 128
    Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 64, IRQ 23
    I/O ports at d400 [size=256]
    Memory at ff6ff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
    Kernel modules: shpchp

00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Kernel modules: shpchp

02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
```

---

### Post by zenon222 on 2010-02-09
This is a common issue, can anyone help me out?

---

### Post by combatwombat_nz on 2010-02-16
I just had the same issue whilst installing KahelOS on this board. Use the following grub parameters at the end of the grub boot line for installation:

pc=nomsi

---

### Post by zenon222 on 2010-02-17
I tried pci=nomsi to no avail.

I just ended up disabling the onboard an plugged in a PCI SATA controller.

---

### Post by sinurge on 2010-02-25
> **zenon222 said:**
> I tried pci=nomsi to no avail.

I just ended up disabling the onboard an plugged in a PCI SATA controller.
can you make that all lower case as pci=nomsi, am not sure abt this but i used to have the same problem, on mine when i edited it put it all in lower case. just a try

If you are using gparted live cd then when you boot as well you have to give these boot params else it will not show ur hard drives.

---

### Post by zenon222 on 2010-02-26
SOB!  I bet that's it!

THANK YOU!

---

### Post by |{urse on 2010-02-26
I had that problem on a similar board, I had to set it to IDE in the bios for some odd reason. That still confuses me to this day.

---

