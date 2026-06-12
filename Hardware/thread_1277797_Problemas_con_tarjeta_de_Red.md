---
title: "Problemas con tarjeta de Red"
date: 2009-09-28
forum: Hardware
---

### Post by josecardenasvejar on 2009-09-28
Estimados: 
                  He detectado un problema que me tiene algo inquieto. Al encender mi pc, se iniciaba una conexión eth1, al reiniciarlo aparecía una conexión eth2 y así sucesivamente, ya voy en la 17. Tengo configurado todo con dhcp para navegar en mi casa y trabajo. pero trato de eliminar esa conexión y me aparece un mensaje que dice "message did not receive a reply (timeout by message bus ethernet)" y no se puede eliminar, aparece nuevamente, aunque haga click en los diferentes perfiles de conexión que tengo.

Ahora, desapareció el ícono de red del panel principal, solo puedo ingresar a través de sistema, preferencias.


Tengo esta inquietud, hace unos días no me aparecía esto

Agradezco muchísimo su ayuda

Saludos:confused:

---

### Post by moreback on 2009-09-29
mmmh... interesante tu problema, podrías indicarnos frente a qué hardware estamos tratando? Un** lspci -v **nos vendría bien para empezar. Lo otro es que te cerciores que estás usando sólo Network-Manager para conectarte y que no tienes nada (salvo la interfaz lo) en /etc/network/interfaces.

Saludos.

---

### Post by josecardenasvejar on 2009-09-29
Hola, muchas gracias por tu respuesta.

Al hacer lspci -v me aparece esto:

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at 3080 [size=64]
    I/O ports at 3040 [size=64]
    I/O ports at 3000 [size=64]
    Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    Memory at f6200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    Memory at f6486000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f6489000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
    Memory at f6487000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f6489400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: Device f03c:30cf
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at 30c0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    Memory behind bridge: f6100000-f61fffff
    Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2301
    I/O ports at 30f0 [size=8]
    I/O ports at 30e4 [size=4]
    I/O ports at 30e8 [size=8]
    I/O ports at 30e0 [size=4]
    I/O ports at 30d0 [size=16]
    Memory at f6484000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2300
    Memory at f6488000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 30f8 [size=8]
    Memory at f6489c00 (32-bit, non-prefetchable) [size=256]
    Memory at f6489800 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f2000000-f3ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f6000000-f60fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
    Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f4000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, medium devsel, latency 64, IRQ 5
    Memory at f6100000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, medium devsel, latency 64, IRQ 7
    Memory at f6100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f6100c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ricoh-mmc
    Kernel modules: ricoh_mmc

02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Hewlett-Packard Company Device 30cf
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f6101000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
    !!! Unknown header type 7f

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Hewlett-Packard Company Device 137b
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k_pci
    Kernel modules: ath_pci, ath5k



después, en interfaces me sale esto : 

auto lo
iface lo inet dhcp


un fuerte abrazo y muchas gracias!

---

### Post by moreback on 2009-09-30
Supongo que en la configuración del Network-Manager tienes en "Cableada" una sola conexión, no? debería ser algo como "Auto eth0".

Me gustaría ver también la salida al comando **ifconfig -a** y la del comando **ip route**

Saludos.

---

### Post by Patriciologico on 2009-10-02
Hola josecardenasvejar, tu thread ha sido movido. Por favor recuerda postear en el subforo adecuado. En ellos existe un sticky que te señala el tipo de consulta que contiene cada uno. Si tienes dudas no dudes en leer las normas:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Saludos.

---

