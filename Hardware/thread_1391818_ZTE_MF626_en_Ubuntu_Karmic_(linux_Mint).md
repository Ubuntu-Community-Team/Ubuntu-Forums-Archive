---
title: "ZTE MF626 en Ubuntu Karmic (linux Mint)"
date: 2010-01-27
forum: Hardware
---

### Post by JuanitoMint on 2010-01-27
Hola amigos, estoy intentando conectar el modem mf626 de claro en el ubuntu pero sin exito. :(
lo que hice:
envié el comando AT+ZCDRUN=8 (para no tener que utilizar usbswitch ) esto deshablilita el autorun del usb como un cd y lo deja en modo:modem
para volverlo al estado anterior AT+ZCDRUN=9 (esto funciona en varios modelos, asi que si quieren pueden probar esto antes de toda la zanata del usbswitch)

El network manager lo detecta correctamente, puedo crear la conexion Mobile BroadBand con los parametros que corresponde pero al intentar conectar, hace la animación de conectando y al los pocos segundos me pone: GSM network disconnected

Alguna sugerencia ? alguien que lo haya hecho andar?

---

### Post by JuanitoMint on 2010-02-02
agrego el contenido de los logs


juan@juan-laptop ~ $ tail /var/log/messages

Feb  2 11:08:57 juan-laptop sudo: pam_sm_authenticate: Called

Feb  2 11:08:57 juan-laptop sudo: pam_sm_authenticate: username = [juan]

Feb  2 11:09:48 juan-laptop pppd[2646]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.

Feb  2 11:09:48 juan-laptop pppd[2646]: pppd 2.4.5 started by root, uid 0

Feb  2 11:09:48 juan-laptop pppd[2646]: Using interface ppp0

Feb  2 11:09:48 juan-laptop pppd[2646]: Connect: ppp0 <--> /dev/ttyUSB2

Feb  2 11:09:48 juan-laptop pppd[2646]: PAP authentication succeeded

Feb  2 11:09:51 juan-laptop pppd[2646]: Modem hangup

Feb  2 11:09:51 juan-laptop pppd[2646]: Connection terminated.

Feb  2 11:09:52 juan-laptop pppd[2646]: Exit.




tail /var/log/debug

Feb  2 11:34:49 juan-laptop pppd[2991]: sent [PAP AuthReq id=0x1 user="clarogprs" password=""]

Feb  2 11:34:49 juan-laptop pppd[2991]: rcvd [LCP DiscReq id=0xb magic=0x12d1771]

Feb  2 11:34:49 juan-laptop pppd[2991]: rcvd [PAP AuthAck id=0x1 ""]

Feb  2 11:34:49 juan-laptop pppd[2991]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]

Feb  2 11:34:50 juan-laptop pppd[2991]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]

Feb  2 11:34:50 juan-laptop pppd[2991]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]

Feb  2 11:34:51 juan-laptop pppd[2991]: rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]

Feb  2 11:34:51 juan-laptop pppd[2991]: sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]

Feb  2 11:34:54 juan-laptop NetworkManager: <debug> [1265121294.001081] ensure_killed(): waiting for ppp pid 2991 to exit

Feb  2 11:34:54 juan-laptop NetworkManager: <debug> [1265121294.001191] ensure_killed(): ppp pid 2991 cleaned up

---

### Post by JuanitoMint on 2010-02-03
Bien al fin consegui hacer andar el servicio de claro en mi ubuntu karmic (linux mint helena)
En vez de hacer toda la movida le USB switch, lo pongo y lo ejecto y ahi detecta el modem o como alternativa deshabilito el autorun:

una vez en modo modem (espero que termine la inicializacion hasta tener la luz azul) me conecto con GtkTerm y le mando AT+ZCDRUN=8 (ahi se desactiva el arranque para volverlo a normal AT+ZCDRUN+9)
ponerlo sin el autorun tiene ventajas para linux pero en windows no aparece más para instalar, elijan uds lo que más les convenga (yo lo tengo deshabilitado)

No puedo conectarlo desde el network manager, pero lo hago conectandome con wvdial a través de la interfaz gráfica GNOME PPP (podria ser kppp que también usa wvdial)
el primer problema que se presenta es que nuestro usuario no es parte del grupo **dip** y por lo tanto no puede discar asi que en la consola escribimos:

sudo usermod -a -G dip <nombreUsuario>

(reemplazar por tu nombre)

ahora tenemos que reiniciar la session en el gnome (o el que sea) ctrl+alt+backspace o desde el menu: logout

nos volvemos a loguear y abrimos GNOME PPP
le ponemos estos datos: (abajo están las pantallas)

username: clarogprs
password: clarogprs999
(recordar password)
phone number: *99#
en setup 
DEVICE /dev/ttyUSB2

wait for dialtone (un check) destildar

podemos poner los DNS a mano porque a veces no los levanta
vamos a setup ->networking y le ponemos: 
MANUAL DNS

DNS1 170.51.255.167
DNS2 170.51.255.166
[IMG]http://www.webexperts.com.ar/ubuntu/modem.png[/IMG]

[IMG]http://www.webexperts.com.ar/ubuntu/networking.png[/IMG]

[IMG]http://www.webexperts.com.ar/ubuntu/options.png[/IMG]

Espero les sirva a los que están con problemas
lo del network manager supongo lo resolverán luego (yo no veo logs detallados de lo que pasa)

---

### Post by atari130xe on 2010-02-04
Gracias! estoy posteando desde Ubuntu con la conexion de Claro, funciona PERFECTAMENTE! :D

---

### Post by atari130xe on 2010-02-05
Nuevamente yo... el tema es que intento hacer funcionar el modem en Ubuntu 9.04 (en la pc de un amigo) y el problema reside en que no reconoce los puertos ttyUSB0, ttyUSB1, etc. dice que no existe, alguien sabe como modificar esto? Solamente muestra los puertos ttyS0, S1, S2 y S3.
Gracias!

```
emiliano@emiliano-desktop:~$ lsusb
[COLOR="Blue"]Bus 001 Device 013: ID 19d2:2000[/COLOR]  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
emiliano@emiliano-desktop:~$
```


dmesg
```
[    0.622782] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[    0.623025] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.623271] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.623514] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 6 7 10 11 12)
[    0.623728] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.623936] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.624155] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.624379] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 *10 11 12)
[    0.624604] ACPI: WMI: Mapper loaded
[    0.624848] SCSI subsystem initialized
[    0.624904] libata version 3.00 loaded.
[    0.624962] usbcore: registered new interface driver usbfs
[    0.624983] usbcore: registered new interface driver hub
[    0.625022] usbcore: registered new device driver usb
[    0.625165] PCI: Using ACPI for IRQ routing
[    0.625306] Bluetooth: Core ver 2.13
[    0.625306] NET: Registered protocol family 31
[    0.625306] Bluetooth: HCI device and connection manager initialized
[    0.625306] Bluetooth: HCI socket layer initialized
[    0.625306] NET: Registered protocol family 8
[    0.625306] NET: Registered protocol family 20
[    0.625306] NetLabel: Initializing
[    0.625306] NetLabel:  domain hash size = 128
[    0.625306] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.625306] NetLabel:  unlabeled traffic allowed by default
[    0.625306] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0
[    0.625306] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.628087] AppArmor: AppArmor Filesystem Enabled
[    0.628101] pnp: PnP ACPI init
[    0.628101] ACPI: bus type pnp registered
[    0.632019] Switched to high resolution mode on CPU 0
[    0.634528] pnp: PnP ACPI: found 20 devices
[    0.634531] ACPI: ACPI bus type pnp unregistered
[    0.634536] PnPBIOS: Disabled by ACPI PNP
[    0.634549] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.634552] system 00:01: ioport range 0x500-0x50f has been reserved
[    0.634559] system 00:02: iomem range 0xfea00000-0xfea000ff has been reserved
[    0.634565] system 00:03: iomem range 0xf0001000-0xf0001fff has been reserved
[    0.634571] system 00:04: iomem range 0xf0002000-0xf0002fff has been reserved
[    0.634577] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.634580] system 00:05: ioport range 0x800-0x805 has been reserved
[    0.634583] system 00:05: ioport range 0x290-0x297 has been reserved
[    0.634585] system 00:05: ioport range 0x880-0x88f has been reserved
[    0.634596] system 00:10: iomem range 0xf0000000-0xf0000fff has been reserved
[    0.634601] system 00:11: iomem range 0xe0000000-0xefffffff has been reserved
[    0.634608] system 00:13: iomem range 0xf0000-0xfffff could not be reserved
[    0.634611] system 00:13: iomem range 0xfe800000-0xfe8000ff has been reserved
[    0.634614] system 00:13: iomem range 0xfea00000-0xfea000ff has been reserved
[    0.634617] system 00:13: iomem range 0x5bee0000-0x5befffff could not be reserved
[    0.634621] system 00:13: iomem range 0xffff0000-0xffffffff has been reserved
[    0.634624] system 00:13: iomem range 0x0-0x9ffff could not be reserved
[    0.634627] system 00:13: iomem range 0x100000-0x5bedffff could not be reserved
[    0.634630] system 00:13: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.634633] system 00:13: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.634636] system 00:13: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.669355] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.669359] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    0.669365] pci 0000:00:01.0:   MEM window: 0xfb000000-0xfcffffff
[    0.669370] pci 0000:00:01.0:   PREFETCH window: 0x000000f4000000-0x000000f7ffffff
[    0.669377] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.669381] pci 0000:00:02.0:   IO window: 0xa000-0xafff
[    0.669387] pci 0000:00:02.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.669391] pci 0000:00:02.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.669398] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.669402] pci 0000:00:03.0:   IO window: 0xc000-0xcfff
[    0.669408] pci 0000:00:03.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.669413] pci 0000:00:03.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.669421] pci 0000:00:13.1: PCI bridge, secondary bus 0000:04
[    0.669425] pci 0000:00:13.1:   IO window: 0x9000-0x9fff
[    0.669430] pci 0000:00:13.1:   MEM window: 0xfda00000-0xfdafffff
[    0.669435] pci 0000:00:13.1:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.669452] pci 0000:00:01.0: setting latency timer to 64
[    0.669468] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.669473] pci 0000:00:02.0: setting latency timer to 64
[    0.669482] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
[    0.669487] pci 0000:00:03.0: setting latency timer to 64
[    0.669495] pci 0000:00:13.1: setting latency timer to 64
[    0.669500] bus: 00 index 0 io port: [0x00-0xffff]
[    0.669502] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.669505] bus: 01 index 0 io port: [0xb000-0xbfff]
[    0.669507] bus: 01 index 1 mmio: [0xfb000000-0xfcffffff]
[    0.669510] bus: 01 index 2 mmio: [0xf4000000-0xf7ffffff]
[    0.669512] bus: 01 index 3 mmio: [0x0-0x0]
[    0.669515] bus: 02 index 0 io port: [0xa000-0xafff]
[    0.669517] bus: 02 index 1 mmio: [0xfdb00000-0xfdbfffff]
[    0.669519] bus: 02 index 2 mmio: [0xfde00000-0xfdefffff]
[    0.669522] bus: 02 index 3 mmio: [0x0-0x0]
[    0.669524] bus: 03 index 0 io port: [0xc000-0xcfff]
[    0.669526] bus: 03 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.669528] bus: 03 index 2 mmio: [0xfdc00000-0xfdcfffff]
[    0.669531] bus: 03 index 3 mmio: [0x0-0x0]
[    0.669533] bus: 04 index 0 io port: [0x9000-0x9fff]
[    0.669535] bus: 04 index 1 mmio: [0xfda00000-0xfdafffff]
[    0.669538] bus: 04 index 2 mmio: [0xfd900000-0xfd9fffff]
[    0.669540] bus: 04 index 3 io port: [0x00-0xffff]
[    0.669542] bus: 04 index 4 mmio: [0x000000-0xffffffff]
[    0.669545] bus: 80 index 0 io port: [0x00-0xffff]
[    0.669547] bus: 80 index 1 mmio: [0x000000-0xffffffff]
[    0.669561] NET: Registered protocol family 2
[    0.669699] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.669955] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.670844] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.671361] TCP: Hash tables configured (established 131072 bind 65536)
[    0.671366] TCP reno registered
[    0.671594] NET: Registered protocol family 1
[    0.671740] checking if image is initramfs... it is
[    1.418697] Freeing initrd memory: 7379k freed
[    1.418847] cpufreq: No nForce2 chipset.
[    1.419025] audit: initializing netlink socket (disabled)
[    1.419051] type=2000 audit(1265403055.416:1): initialized
[    1.427649] highmem bounce pool size: 64 pages
[    1.427656] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.429043] VFS: Disk quotas dquot_6.5.1
[    1.429107] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.429795] fuse init (API version 7.10)
[    1.429897] msgmni has been set to 1712
[    1.430107] alg: No test for stdrng (krng)
[    1.430125] io scheduler noop registered
[    1.430127] io scheduler anticipatory registered
[    1.430129] io scheduler deadline registered
[    1.430153] io scheduler cfq registered (default)
[    1.430173] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.430258] pci 0000:01:00.0: Boot video device
[    1.437505] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.437551] pcieport-driver 0000:00:02.0: found MSI capability
[    1.437592] pcieport-driver 0000:00:02.0: irq 2303 for MSI/MSI-X
[    1.437607] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.437625] pci_express 0000:00:02.0:pcie01: allocate port service
[    1.437638] pci_express 0000:00:02.0:pcie02: allocate port service
[    1.437651] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.437712] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.437760] pcieport-driver 0000:00:03.0: found MSI capability
[    1.437801] pcieport-driver 0000:00:03.0: irq 2302 for MSI/MSI-X
[    1.437818] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.437831] pci_express 0000:00:03.0:pcie01: allocate port service
[    1.437848] pci_express 0000:00:03.0:pcie02: allocate port service
[    1.437861] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.442009] aer 0000:00:02.0:pcie01: service driver aer loaded
[    1.446075] aer 0000:00:03.0:pcie01: service driver aer loaded
[    1.446090] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.446633] pciehp 0000:00:02.0:pcie02: HPC vendor_id 1106 device_id a327 ss_vid 0 ss_did 0
[    1.446672] pciehp 0000:00:02.0:pcie02: service driver pciehp loaded
[    1.447180] pciehp 0000:00:03.0:pcie02: HPC vendor_id 1106 device_id c327 ss_vid 0 ss_did 0
[    1.447212] pciehp 0000:00:03.0:pcie02: service driver pciehp loaded
[    1.447223] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.447366] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.447369] ACPI: Power Button (FF) [PWRF]
[    1.447415] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.447418] ACPI: Power Button (CM) [PWRB]
[    1.447462] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.447469] ACPI: Sleep Button (CM) [SLPB]
[    1.447530] fan PNP0C0B:00: registered as cooling_device0
[    1.447536] ACPI: Fan [FAN] (on)
[    1.448299] processor ACPI_CPU:00: registered as cooling_device1
[    1.453091] thermal LNXTHERM:01: registered as thermal_zone0
[    1.453482] ACPI: Thermal Zone [THRM] (33 C)
[    1.453537] isapnp: Scanning for PnP cards...
[    1.807463] isapnp: No Plug & Play device found
[    1.808800] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.808901] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.809452] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.810348] brd: module loaded
[    1.810691] loop: module loaded
[    1.810776] Fixed MDIO Bus: probed
[    1.810783] PPP generic driver version 2.4.2
[    1.810850] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.810890] Driver 'sd' needs updating - please use bus_type methods
[    1.810900] Driver 'sr' needs updating - please use bus_type methods
[    1.811038] sata_via 0000:00:0f.0: version 2.4
[    1.811064] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.811098] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.811212] scsi0 : sata_via
[    1.811349] scsi1 : sata_via
[    1.813255] ata1: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 21
[    1.813258] ata2: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 21
[    2.016009] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.223118] ata1.00: ATA-7: MAXTOR STM380215AS, 4.AAB, max UDMA/133
[    2.223121] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.289776] ata1.00: configured for UDMA/133
[    2.492016] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.502811] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM380215 4.AA PQ: 0 ANSI: 5
[    2.502930] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.502948] sd 0:0:0:0: [sda] Write Protect is off
[    2.502951] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.502978] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.503055] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.503072] sd 0:0:0:0: [sda] Write Protect is off
[    2.503074] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.503100] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.503106]  sda: sda1 sda2 sda3
[    2.543151] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.543207] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.543635] pata_via 0000:00:0f.1: version 0.3.3
[    2.543797] scsi2 : pata_via
[    2.543872] scsi3 : pata_via
[    2.545614] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[    2.545618] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[    2.708434] ata3.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.01, max UDMA/66
[    2.724325] ata3.00: configured for UDMA/66
[    2.881450] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.01 PQ: 0 ANSI: 5
[    2.885483] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.885488] Uniform CD-ROM driver Revision: 3.20
[    2.885615] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.885668] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.885831] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.885857] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    2.885883] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    2.885958] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    2.885996] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfdfff000
[    2.896014] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    2.896088] usb usb1: configuration #1 chosen from 1 choice
[    2.896120] hub 1-0:1.0: USB hub found
[    2.896128] hub 1-0:1.0: 8 ports detected
[    2.896244] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.896265] uhci_hcd: USB Universal Host Controller Interface driver
[    2.896311] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.896320] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.896374] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    2.896406] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000e000
[    2.896490] usb usb2: configuration #1 chosen from 1 choice
[    2.896519] hub 2-0:1.0: USB hub found
[    2.896526] hub 2-0:1.0: 2 ports detected
[    2.896622] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    2.896629] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.896677] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    2.896707] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000dc00
[    2.896783] usb usb3: configuration #1 chosen from 1 choice
[    2.896809] hub 3-0:1.0: USB hub found
[    2.896817] hub 3-0:1.0: 2 ports detected
[    2.896910] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    2.896916] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    2.896969] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    2.896991] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    2.897072] usb usb4: configuration #1 chosen from 1 choice
[    2.897106] hub 4-0:1.0: USB hub found
[    2.897114] hub 4-0:1.0: 2 ports detected
[    2.897212] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.897220] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    2.897287] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    2.897318] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000d400
[    2.897401] usb usb5: configuration #1 chosen from 1 choice
[    2.897434] hub 5-0:1.0: USB hub found
[    2.897444] hub 5-0:1.0: 2 ports detected
[    2.897616] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.897968] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.897976] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.898117] mice: PS/2 mouse device common for all mice
[    2.898291] rtc_cmos 00:08: RTC can wake from S4
[    2.898330] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.898368] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.898453] device-mapper: uevent: version 1.0.3
[    2.898584] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.898637] device-mapper: multipath: version 1.0.5 loaded
[    2.898640] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.898738] EISA: Probing bus 0 at eisa.0
[    2.898778] EISA: Detected 0 cards.
[    2.898815] cpuidle: using governor ladder
[    2.898817] cpuidle: using governor menu
[    2.899319] TCP cubic registered
[    2.899429] NET: Registered protocol family 10
[    2.899831] lo: Disabled Privacy Extensions
[    2.900153] NET: Registered protocol family 17
[    2.900180] Bluetooth: L2CAP ver 2.11
[    2.900182] Bluetooth: L2CAP socket layer initialized
[    2.900185] Bluetooth: SCO (Voice Link) ver 0.6
[    2.900187] Bluetooth: SCO socket layer initialized
[    2.900235] Bluetooth: RFCOMM socket layer initialized
[    2.900244] Bluetooth: RFCOMM TTY layer initialized
[    2.900246] Bluetooth: RFCOMM ver 1.10
[    2.900309] Using IPI No-Shortcut mode
[    2.900411] registered taskstats version 1
[    2.900544]   Magic number: 14:259:851
[    2.900643] rtc_cmos 00:08: setting system clock to 2010-02-05 20:50:57 UTC (1265403057)
[    2.900647] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.900649] EDD information not available.
[    2.900915] Freeing unused kernel memory: 532k freed
[    2.901035] Write protecting the kernel text: 4120k
[    2.901069] Write protecting the kernel read-only data: 1524k
[    2.930907] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.237144] Floppy drive(s): fd0 is 1.44M
[    3.256026] FDC 0 is a post-1991 82077
[    4.126876] PM: Starting manual resume from disk
[    4.126882] PM: Resume from partition 8:3
[    4.126884] PM: Checking hibernation image.
[    4.127072] PM: Resume from disk failed.
[    4.164435] EXT4-fs: barriers enabled
[    4.177031] kjournald2 starting.  Commit interval 5 seconds
[    4.177045] EXT4-fs: delayed allocation enabled
[    4.177047] EXT4-fs: file extents enabled
[    4.177158] EXT4-fs: mballoc enabled
[    4.177164] EXT4-fs: mounted filesystem with ordered data mode.
[    8.157145] udev: starting version 141
[    8.299067] Linux agpgart interface v0.103
[    8.349293] agpgart: Detected VIA P4M890 chipset
[    8.355205] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
[    8.388700] parport_pc 00:0d: reported by Plug and Play ACPI
[    8.388745] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.401318] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.832543] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    8.966880] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    8.994817] ppdev: user-space parallel port driver
[    9.264184] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.264372] HDA Intel 0000:80:01.0: setting latency timer to 64
[    9.264377] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
[    9.464144] lp0: using parport0 (interrupt-driven).
[    9.483516] psmouse serio1: ID: 10 00 64<6>Adding 996020k swap on /dev/sda3.  Priority:-1 extents:1 across:996020k
[   10.045767] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   10.140738] EXT4 FS on sda1, internal journal on sda1:8
[   10.994092] EXT4-fs: barriers enabled
[   11.009163] kjournald2 starting.  Commit interval 5 seconds
[   11.012211] EXT4 FS on sda2, internal journal on sda2:8
[   11.012215] EXT4-fs: delayed allocation enabled
[   11.012217] EXT4-fs: file extents enabled
[   11.016396] EXT4-fs: mballoc enabled
[   11.016403] EXT4-fs: mounted filesystem with ordered data mode.
[   11.251709] type=1505 audit(1265403065.847:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1973
[   11.310301] type=1505 audit(1265403065.907:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1977
[   11.310505] type=1505 audit(1265403065.907:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1977
[   11.310572] type=1505 audit(1265403065.907:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1977
[   11.310628] type=1505 audit(1265403065.907:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1977
[   11.474355] type=1505 audit(1265403066.071:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1982
[   11.474636] type=1505 audit(1265403066.071:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1982
[   11.510409] type=1505 audit(1265403066.107:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1986
[   15.725874] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.725877] Bluetooth: BNEP filters: protocol multicast
[   15.933476] Bridge firewalling registered
[   16.932273] [drm] Initialized drm 1.1.0 20060810
[   16.961092] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.961242] [drm] Initialized via 2.11.1 20070202 on minor 0
[   17.005115] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   17.005143] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   17.005257] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   21.845185] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   75.744015] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   75.989742] usb 4-2: configuration #2 chosen from 1 choice
[   76.070041] cdc_wdm: probe of 4-2:2.5 failed with error -22
[   76.070057] usbcore: registered new interface driver cdc_wdm
[   76.073665] cdc_acm 4-2:2.1: ttyACM0: USB ACM device
[   76.076422] usbcore: registered new interface driver cdc_acm
[   76.076428] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   76.784041] usb 4-2: USB disconnect, address 2
[   82.360027] usb 4-2: new full speed USB device using uhci_hcd and address 3
[   82.578121] usb 4-2: configuration #2 chosen from 1 choice
[   82.608746] cdc_acm 4-2:2.1: ttyACM0: USB ACM device
[   82.691617] cdc_wdm: probe of 4-2:2.5 failed with error -22
[  110.270373] PPP BSD Compression module registered
[  110.294841] PPP Deflate Compression module registered
[  878.336042] usb 4-2: USB disconnect, address 3
[  909.752020] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  909.923305] usb 1-5: configuration #1 chosen from 1 choice
[  909.958228] Initializing USB Mass Storage driver...
[  909.959389] usb-storage: device ignored
[  909.959443] usbcore: registered new interface driver usb-storage
[  909.959447] USB Mass Storage support registered.
[ 1054.568444] usb 1-5: USB disconnect, address 4
[ 1061.140019] usb 1-6: new high speed USB device using ehci_hcd and address 5
[ 1061.285328] usb 1-6: configuration #1 chosen from 1 choice
[ 1061.338394] usb-storage: device ignored
[ 1216.799530] mtrr: no MTRR for f4000000,4000000 found
[ 1218.091441] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[ 1218.091468] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[ 1218.091582] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[ 1219.010284] usb 1-6: USB disconnect, address 5
[ 1250.120019] usb 1-6: new high speed USB device using ehci_hcd and address 6
[ 1250.291048] usb 1-6: configuration #1 chosen from 1 choice
[ 1250.321551] usb-storage: device ignored
[ 2827.332275] usb 1-6: USB disconnect, address 6
[ 2872.488020] usb 1-3: new high speed USB device using ehci_hcd and address 7
[ 2872.659711] usb 1-3: configuration #1 chosen from 1 choice
[ 2872.690571] usb-storage: device ignored
[ 2949.430151] usb 1-3: USB disconnect, address 7
[ 2965.948014] usb 4-2: new full speed USB device using uhci_hcd and address 4
[ 2966.168126] usb 4-2: configuration #2 chosen from 1 choice
[ 2966.199772] cdc_acm 4-2:2.1: ttyACM0: USB ACM device
[ 2966.257121] cdc_wdm: probe of 4-2:2.5 failed with error -22
[ 3534.912045] usb 4-2: USB disconnect, address 4
[ 3551.792027] usb 1-5: new high speed USB device using ehci_hcd and address 9
[ 3551.963555] usb 1-5: configuration #1 chosen from 1 choice
[ 3551.995971] usb-storage: device ignored
[ 3629.007274] usb 1-5: USB disconnect, address 9
[ 3637.496026] usb 4-1: new full speed USB device using uhci_hcd and address 5
[ 3637.742637] usb 4-1: configuration #2 chosen from 1 choice
[ 3637.750989] cdc_acm 4-1:2.1: ttyACM0: USB ACM device
[ 3637.810123] cdc_wdm: probe of 4-1:2.5 failed with error -22
[ 4401.672043] usb 4-1: USB disconnect, address 5
[ 4413.548027] usb 1-6: new high speed USB device using ehci_hcd and address 11
[ 4413.719169] usb 1-6: configuration #1 chosen from 1 choice
[ 4413.751004] usb-storage: device ignored
[ 4501.403896] usb 1-6: USB disconnect, address 11
[ 4508.204027] usb 4-2: new full speed USB device using uhci_hcd and address 6
[ 4508.450185] usb 4-2: configuration #2 chosen from 1 choice
[ 4508.458816] cdc_acm 4-2:2.1: ttyACM0: USB ACM device
[ 4508.516253] cdc_wdm: probe of 4-2:2.5 failed with error -22
[ 5880.042308] usbcore: registered new interface driver usbserial
[ 5880.042325] USB Serial support registered for generic
[ 5880.042368] usbcore: registered new interface driver usbserial_generic
[ 5880.042370] usbserial: USB Serial Driver core
[ 6048.036429] usbcore: deregistering interface driver usb-storage
[10037.224074] usb 4-2: USB disconnect, address 6
[10050.588057] usb 1-6: new high speed USB device using ehci_hcd and address 13
[10050.763609] usb 1-6: configuration #1 chosen from 1 choice
[10050.777689] Initializing USB Mass Storage driver...
[10050.783776] ------------[ cut here ]------------
[10050.783780] WARNING: at /build/buildd/linux-2.6.28/fs/proc/generic.c:551 proc_register+0x10b/0x1e0()
[10050.783783] proc_dir_entry 'scsi/usb-storage' already registered
[10050.783786] Modules linked in: usb_storage(+) usbserial ppp_deflate zlib_deflate bsd_comp ppp_async crc_ccitt cdc_acm cdc_wdm binfmt_misc via drm bridge stp bnep video output input_polldev lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device ppdev psmouse pcspkr serio_raw snd soundcore snd_page_alloc i2c_viapro shpchp parport_pc parport via_agp agpgart floppy fbcon tileblit font bitblit softcursor [last unloaded: usb_storage]
[10050.783830] Pid: 8839, comm: modprobe Not tainted 2.6.28-17-generic #58-Ubuntu
[10050.783832] Call Trace:
[10050.783839]  [<c0139ba0>] warn_slowpath+0x60/0x80
[10050.783845]  [<c02c7202>] ? idr_get_empty_slot+0xe2/0x270
[10050.783849]  [<c02c749f>] ? ida_get_new_above+0x10f/0x1c0
[10050.783853]  [<c02c749f>] ? ida_get_new_above+0x10f/0x1c0
[10050.783856]  [<c02c767d>] ? idr_pre_get+0x3d/0x70
[10050.783860]  [<c01ffcdb>] proc_register+0x10b/0x1e0
[10050.783864]  [<c01fff83>] proc_mkdir_mode+0x33/0x50
[10050.783868]  [<c01fffaf>] proc_mkdir+0xf/0x20
[10050.783874]  [<c0371e06>] scsi_proc_hostdir_add+0x46/0x80
[10050.783878]  [<c0366038>] scsi_host_alloc+0x2b8/0x2d0
[10050.783882]  [<c0369a10>] ? scsi_error_handler+0x0/0x120
[10050.783894]  [<f7f911cd>] storage_probe+0x1d/0x820 [usb_storage]
[10050.783898]  [<c020c4f6>] ? sysfs_addrm_finish+0x36/0xf0
[10050.783902]  [<c020bca3>] ? sysfs_add_one+0x13/0x50
[10050.783905]  [<c020bd3b>] ? sysfs_addrm_start+0x5b/0xa0
[10050.783912]  [<c04ff22b>] ? mutex_lock+0xb/0x20
[10050.783916]  [<c03bc3e4>] ? usb_autopm_do_device+0x64/0xf0
[10050.783921]  [<c03bca32>] usb_probe_interface+0xa2/0x130
[10050.783925]  [<c020cb62>] ? sysfs_create_link+0x12/0x20
[10050.783931]  [<c034fed6>] really_probe+0xe6/0x180
[10050.783934]  [<c03bbe91>] ? usb_match_id+0x41/0x60
[10050.783939]  [<c034ffae>] driver_probe_device+0x3e/0x50
[10050.783942]  [<c0350049>] __driver_attach+0x89/0x90
[10050.783946]  [<c034f763>] bus_for_each_dev+0x53/0x80
[10050.783950]  [<c034fd09>] driver_attach+0x19/0x20
[10050.783953]  [<c034ffc0>] ? __driver_attach+0x0/0x90
[10050.783957]  [<c034f137>] bus_add_driver+0x1c7/0x240
[10050.783962]  [<c03501e9>] driver_register+0x69/0x140
[10050.783966]  [<c02c0020>] ? scsi_cmd_ioctl+0x370/0x410
[10050.783971]  [<c03bccfc>] usb_register_driver+0x7c/0x100
[10050.783975]  [<c020b740>] ? sysfs_ilookup_test+0x0/0x20
[10050.783982]  [<f7d12000>] ? usb_stor_init+0x0/0x43 [usb_storage]
[10050.783989]  [<f7d12000>] ? usb_stor_init+0x0/0x43 [usb_storage]
[10050.783996]  [<f7d12027>] usb_stor_init+0x27/0x43 [usb_storage]
[10050.784000]  [<c010111e>] _stext+0x2e/0x170
[10050.784023]  [<c020c4d5>] ? sysfs_addrm_finish+0x15/0xf0
[10050.784027]  [<c020bca3>] ? sysfs_add_one+0x13/0x50
[10050.784030]  [<c020bd1f>] ? sysfs_addrm_start+0x3f/0xa0
[10050.784035]  [<c01a938c>] ? __vunmap+0x9c/0xe0
[10050.784039]  [<c01a938c>] ? __vunmap+0x9c/0xe0
[10050.784045]  [<c01a9421>] ? vfree+0x21/0x30
[10050.784050]  [<c016416d>] ? load_module+0x103d/0x1050
[10050.784061]  [<c0164208>] sys_init_module+0x88/0x1b0
[10050.784064]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
[10050.784069]  [<c0500000>] ? account_scheduler_latency+0x170/0x210
[10050.784072] ---[ end trace a01a0ff5c05afc7f ]---
[COLOR="Blue"][10050.784078] usb-storage: device ignored
[10050.792370] usbcore: registered new interface driver usb-storage
[10050.792375] USB Mass Storage support registered.[/COLOR]
emiliano@emiliano-desktop:~$ 

```

---

### Post by ceci.c on 2010-02-12
> **JuanitoMint said:**
> Bien al fin consegui hacer andar el servicio de claro en mi ubuntu karmic (linux mint helena)
En vez de hacer toda la movida le USB switch, lo pongo y lo ejecto y ahi detecta el modem o como alternativa deshabilito el autorun:

una vez en modo modem (espero que termine la inicializacion hasta tener la luz azul) me conecto con GtkTerm y le mando AT+ZCDRUN=8 (ahi se desactiva el arranque para volverlo a normal AT+ZCDRUN+9)
ponerlo sin el autorun tiene ventajas para linux pero en windows no aparece más para instalar, elijan uds lo que más les convenga (yo lo tengo deshabilitado)

No puedo conectarlo desde el network manager, pero lo hago conectandome con wvdial a través de la interfaz gráfica GNOME PPP (podria ser kppp que también usa wvdial)
el primer problema que se presenta es que nuestro usuario no es parte del grupo **dip** y por lo tanto no puede discar asi que en la consola escribimos:

sudo usermod -a -G dip <nombreUsuario>

(reemplazar por tu nombre)

ahora tenemos que reiniciar la session en el gnome (o el que sea) ctrl+alt+backspace o desde el menu: logout

nos volvemos a loguear y abrimos GNOME PPP
le ponemos estos datos: (abajo están las pantallas)

username: clarogprs
password: clarogprs999
(recordar password)
phone number: *99#
en setup 
DEVICE /dev/ttyUSB2

wait for dialtone (un check) destildar

podemos poner los DNS a mano porque a veces no los levanta
vamos a setup ->networking y le ponemos: 
MANUAL DNS

DNS1 170.51.255.167
DNS2 170.51.255.166
(...)
Espero les sirva a los que están con problemas
lo del network manager supongo lo resolverán luego (yo no veo logs detallados de lo que pasa)

Esto sirve para Xubuntu Karmic koala? Tengo el mismo problema con ese modem pero no tengo el gnome ppp ni el wvdial porque no está incluido...

Saludos y gracias ^^!

---

### Post by JuanitoMint on 2010-06-01
si te sirve para cualquier karmic el tema es que te vas a tener que instalar el gtkterm y el gnome-ppp para poder hacerlo andar porque no anda (por lo menos a mi) con el network manager

---

