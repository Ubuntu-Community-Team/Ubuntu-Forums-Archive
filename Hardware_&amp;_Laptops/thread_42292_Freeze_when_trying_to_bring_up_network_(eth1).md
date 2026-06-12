---
title: "Freeze when trying to bring up network (eth1)"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by pb7804 on 2005-06-16
**Hello guys!**

Could someone help me to find a reason of freeze when I'm trying to up second network interface?

I have two NICs in my system, one from nVidia embedded into ASUS A7N8X-X motherboard (eth0) and another one from SMC - it's not very new but working PCI board based on Intel DEC chip (eth1). 

Here it is, from dmesg:

```
[SIZE=3]de2104x PCI Ethernet driver v0.7 (Mar 17, 2004)
eth1: 21041 at 0xe0afc000, 00:80:48:e8:7a:ed, [COLOR=DarkRed]**IRQ 17**[/COLOR][/SIZE]
```

And it's module seems to be loaded:

[SIZE=3]```
~$ lsmod |grep de2104x
de2104x                19840  0
```[/SIZE]


When I just installed Ubuntu Hoary everything worked fine, I disabled eth1 and did various things including installing some packages. Now I decided to get eth1 up and - BOOM! - I got system locked up completely.  ](*,)  I've tried to up eth1 from console using ifconfig and got the same freeze and kernel panic message "not syncing: Fatal exception in interrupt" and some traceback. I feel It's something about resource conflict, IRQ maybe, or it's an ACPI issue, but I'm completely unsure about it. 

ls /proc/irq gives me this:

[SIZE=1]**0  1  10  11  12  13  14  15  16  18  19  2  20  21  22  3  4  5  6  7  8  9**[/SIZE]

IRQ 17 is missing? It must be assigned to eth1 ...  :confused: 

Just guessing it's a consequence of kernel updates. As far as I remember there was a couple of updates since I installed Hoary on my PC.

Please, someone recommend the way how to find what's causing it. I'll appreciate any ideas.

Below is some outputs and parts of logs you may find useful. Tried to make it as short and compact as possible.

```
[SIZE=3]$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:07.0 Multimedia controller: Philips Semiconductors SAA7134 (rev 01)
0000:01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:01:08.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
[COLOR=DarkRed]**0000:01:09.0 Ethernet controller: Digital Equipment Corporation DECchip 21041 [Tulip Pass 3] (rev 11)**
[/COLOR]0000:01:0a.0 SCSI storage controller: LSI Logic / Symbios Logic 53c860 (rev 02)
0000:02:00.0 VGA compatible controller: ATI Technologies Inc R300 AD [Radeon 9500 Pro]
0000:02:00.1 Display controller: ATI Technologies Inc R300 AD [Radeon 9500 Pro] (Secondary)
[/SIZE]
```

And fragment of syslog:

```
[SIZE=2]
Jun 17 01:24:42 localhost kernel: ACPI: Looking for DSDT in initrd... not found!
Jun 17 01:24:42 localhost kernel: ENABLING IO-APIC IRQs
Jun 17 01:24:42 localhost kernel: ..TIMER: vector=0x31 pin1=0 pin2=-1
Jun 17 01:24:42 localhost kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Jun 17 01:24:42 localhost kernel: Freeing initrd memory: 4300k freed
Jun 17 01:24:42 localhost kernel: NET: Registered protocol family 16
Jun 17 01:24:42 localhost kernel: EISA bus registered
Jun 17 01:24:42 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfb4a0, last bus=2
Jun 17 01:24:42 localhost kernel: PCI: Using configuration type 1
Jun 17 01:24:42 localhost kernel: mtrr: v2.0 (20020519)
Jun 17 01:24:42 localhost kernel: ACPI: Subsystem revision 20050211
Jun 17 01:24:42 localhost kernel: ACPI: Interpreter enabled
Jun 17 01:24:42 localhost kernel: ACPI: Using IOAPIC for interrupt routing
Jun 17 01:24:42 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Jun 17 01:24:42 localhost kernel: PCI: Probing PCI hardware (bus 00)
Jun 17 01:24:42 localhost kernel: PCI: nForce2 C1 Halt Disconnect fixup
Jun 17 01:24:42 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

**[COLOR=DarkRed]Jun 17 01:24:42 localhost kernel: ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.[/COLOR]**

Jun 17 01:24:42 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 17 01:24:42 localhost kernel: pnp: PnP ACPI init
Jun 17 01:24:42 localhost kernel: pnp: PnP ACPI: found 12 devices
Jun 17 01:24:42 localhost kernel: PnPBIOS: Disabled by ACPI PNP
Jun 17 01:24:42 localhost kernel: PCI: Using ACPI for IRQ routing
Jun 17 01:24:42 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
Jun 17 01:24:42 localhost kernel: ** causes a device to stop working, it is probably because the
Jun 17 01:24:42 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
Jun 17 01:24:42 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
Jun 17 01:24:42 localhost kernel: ** behavior.  If this argument makes the device work again,
Jun 17 01:24:42 localhost kernel: ** please email the output of "lspci" to bjorn.helgaas@hp.com
Jun 17 01:24:42 localhost kernel: ** so I can fix the driver.

[B][COLOR=DarkRed]Jun 17 01:24:42 localhost kernel: de2104x PCI Ethernet driver v0.7 (Mar 17, 2004)
Jun 17 01:24:42 localhost kernel: ACPI: PCI Interrupt Link [APC2] enabled at **IRQ 17**
Jun 17 01:24:42 localhost kernel: ACPI: PCI interrupt 0000:01:09.0[A] -> **GSI 17 (level, high)** -> IRQ 17
Jun 17 01:24:42 localhost kernel: de0: SROM leaf offset 30, default media 10baseT auto
Jun 17 01:24:42 localhost kernel: de0:   media block #0: BNC
Jun 17 01:24:42 localhost kernel: de0:   media block #1: AUI
Jun 17 01:24:42 localhost kernel: de0:   media block #2: 10baseT-FD
Jun 17 01:24:42 localhost kernel: de0:   media block #3: 10baseT-HD
Jun 17 01:24:42 localhost kernel: eth1: 21041 at 0xe0afc000, 00:80:48:e8:7a:ed, IRQ 17[/COLOR][/B]
[/SIZE]
```

And finaly here is output of udevinfo:

```
[SIZE=3]$ udevinfo -p /sys/class/net/eth1 -a

udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at class device '/sys/class/net/eth1':
    SYSFS{addr_len}="6"
    SYSFS{address}="00:80:48:e8:7a:ed"
    SYSFS{broadcast}="ff:ff:ff:ff:ff:ff"
    SYSFS{features}="0x0"
    SYSFS{flags}="0x1002"
    SYSFS{ifindex}="3"
    SYSFS{iflink}="3"
    SYSFS{mtu}="1500"
    SYSFS{tx_queue_len}="1000"
    SYSFS{type}="1"

follow the class device's "device"
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:08.0/0000:01:09.0':
    BUS="pci"
    ID="0000:01:09.0"
    SYSFS{class}="0x020000"
    SYSFS{detach_state}="0"
    SYSFS{device}="0x0014"
    SYSFS{irq}="17"
    SYSFS{local_cpus}="1"
    SYSFS{subsystem_device}="0x0000"
    SYSFS{subsystem_vendor}="0x0000"
    SYSFS{vendor}="0x1011"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:08.0':
    BUS="pci"
    ID="0000:00:08.0"
    SYSFS{class}="0x060400"
    SYSFS{detach_state}="0"
    SYSFS{device}="0x006c"
    SYSFS{irq}="0"
    SYSFS{local_cpus}="1"
    SYSFS{subsystem_device}="0x0000"
    SYSFS{subsystem_vendor}="0x0000"
    SYSFS{vendor}="0x10de"

  looking at the device chain at '/sys/devices/pci0000:00':
    BUS=""
    ID="pci0000:00"
    SYSFS{detach_state}="0"[/SIZE]
```

Well, I'm out because I just dunno what to add.

---

