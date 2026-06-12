---
title: "Problema con Kodak c533"
date: 2008-12-14
forum: Hardware
---

### Post by Danikomdq on 2008-12-14
Hola: 
Como todo principiante, uno suele tener algunos problemas.
Tengo una Kodak c533 que al conectarla, si bien me la reconoce, aparece un aviso diciendo que no puede montarse la cámara.
Recibí el mismo error intentando abrirlo desde el F-Spot, como del menú *Lugares*, donde la cámara aparece listada.

Gracias

---

### Post by sajnox on 2008-12-14
Con la camara conectada ejecuta los siguientes comandos y copia la salida en la respuesta
```

sudo fdisk -l
lsusb
```

---

### Post by Danikomdq on 2008-12-14
> **sajnox said:**
> Con la camara conectada ejecuta los siguientes comandos y copia la salida en la respuesta
```

sudo fdisk -l
lsusb
```


Aparece esto:

daniel@daniel-desktop:~$ sudo fdisk -l

Disco /dev/sda: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x42ea42ea

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1572    12627058+   7  HPFS/NTFS
/dev/sda2            1573       10011    67786267+   5  Extendida
/dev/sda5            1573        9661    64974861   83  Linux
/dev/sda6            9662       10011     2811343+  82  Linux swap / Solaris
daniel@daniel-desktop:~$ lsusb

---

### Post by sajnox on 2008-12-14
Te falta la salida del comando lsusb

Estas seguro que la maquina estaba conectada y encendida cuando tiraste el comando sudo fdisk -l ??

---

### Post by Danikomdq on 2008-12-14
> **sajnox said:**
> Te falta la salida del comando lsusb

Estas seguro que la maquina estaba conectada y encendida cuando tiraste el comando sudo fdisk -l ??

Si estaba conectada y encendida

---

### Post by Danikomdq on 2008-12-15
Como les contaba me reconoce la cámara, ya que la misma aparece conectada, pero me dice que no puede ser montada. 
¿El problema no será que no me reconoce la tarjeta de memora? Es una SD Kingston.

---

### Post by Hei Ku on 2008-12-15
Podría ser la tarjeta SD, o quizas que esta camara no te monta la memoria como disco removible. Estas seguro que debería montarla? La probaste en otra maquina o SO?

---

### Post by Danikomdq on 2008-12-15
> **Hei Ku said:**
> Podría ser la tarjeta SD, o quizas que esta camara no te monta la memoria como disco removible. Estas seguro que debería montarla? La probaste en otra maquina o SO?

La maquina aparece listada y cuando quiero ingresar salta un mensaje de error que dice que no puede montarse, por supuesto las fotos no se visualizan.
Hasta hace un mes la misma compu estaba con Win XP y no tenia problemas.

---

### Post by sajnox on 2008-12-15
Tal vez haya que hacer uso de alguna opcion de montaje forzado para que lo haga por primera vez. (tal vez)

Cual es especificamente el mensaje de error que te tira y fijate si con windows la maquina sigue andando

---

### Post by mhoyos on 2008-12-15
buenas..

hay un "problema" de compatibilidad de las maquinas KODAK en cualquier linux.. es porque la camara "busca" su aplicacion en una pc con win, pero en nuestro caso, no existe y por ende, es listada pero no es reconocido el formato del montaje.

recomiendo utilizar un lector de tarjetas en este caso, y no conectar la camara directamente...

:)

salu2

---

### Post by Danikomdq on 2008-12-15
> **mhoyos said:**
> buenas..

hay un "problema" de compatibilidad de las maquinas KODAK en cualquier linux.. es porque la camara "busca" su aplicacion en una pc con win, pero en nuestro caso, no existe y por ende, es listada pero no es reconocido el formato del montaje.

recomiendo utilizar un lector de tarjetas en este caso, y no conectar la camara directamente...

:)

salu2

Gracias por la data. Veré que hago =D>=D>

Saludos

---

### Post by Martinius on 2008-12-15
Hola a todos, quería contarles que tengo el mismo problema que Danikomdq con una cámara Kodak C743 en Intrepid Ibex. Lo curioso es que no había tenido problemas de compatibilidad con las anteriores versiones de Ubuntu, por lo tanto el problema es nuevo.

---

### Post by Hei Ku on 2008-12-15
Pueden postear la salida del comando dmesg al conectar la camara?

---

### Post by Martinius on 2008-12-15
Esta es la salida del comando dmesg:

```
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e2c00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113519
[    0.000000] Kernel command line: root=UUID=2c463846-bb86-4513-9048-a2395ca37c41 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2799.950 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Memory: 440260k/458496k available (2572k kernel code, 17536k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xdc800000 - 0xff3fe000   ( 555 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdbfc0000   ( 447 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.90 BogoMIPS (lpj=11199800)
[    0.004040] Security Framework initialized
[    0.004049] SELinux:  Disabled at boot.
[    0.004074] AppArmor: AppArmor initialized
[    0.004090] Mount-cache hash table entries: 512
[    0.004317] Initializing cgroup subsys ns
[    0.004323] Initializing cgroup subsys cpuacct
[    0.004327] Initializing cgroup subsys memory
[    0.004353] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004357] CPU: L2 cache: 1024K
[    0.004361] CPU: Physical Processor ID: 0
[    0.004364] CPU: Processor Core ID: 0
[    0.004368] using mwait in idle threads.
[    0.004383] Checking 'hlt' instruction... OK.
[    0.022956] ACPI: Core revision 20080609
[    0.026219] ACPI: Checking initramfs for custom DSDT
[    0.375652] ENABLING IO-APIC IRQs
[    0.375976] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.415677] CPU0: Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.416026] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5600.43 BogoMIPS (lpj=11200872)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.500403] CPU1: Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.500425] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.504031] Measured 6284101208 cycles TSC warp between CPUs, turning off TSC clock.
[    0.504031] Marking TSC unstable due to check_tsc_sync_source failed
[    0.504047] Brought up 2 CPUs
[    0.504053] Total of 2 processors activated (11200.33 BogoMIPS).
[    0.504113] CPU0 attaching sched-domain:
[    0.504117]  domain 0: span 0-1 level CPU
[    0.504121]   groups: 0 1
[    0.504130] CPU1 attaching sched-domain:
[    0.504133]  domain 0: span 0-1 level CPU
[    0.504136]   groups: 1 0
[    0.504229] net_namespace: 840 bytes
[    0.504229] Booting paravirtualized kernel on bare hardware
[    0.504436] Time:  1:39:02  Date: 12/16/08
[    0.504486] NET: Registered protocol family 16
[    0.504526] EISA bus registered
[    0.504526] ACPI: bus type pci registered
[    0.504526] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[    0.504526] PCI: Using configuration type 1 for base access
[    0.509110] ACPI: EC: Look up EC in DSDT
[    0.526252] ACPI: Interpreter enabled
[    0.526257] ACPI: (supports S0 S1 S3 S4 S5)
[    0.526285] ACPI: Using IOAPIC for interrupt routing
[    0.544316] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.544316] PCI: 0000:00:00.0 reg 10 32bit mmio: [f8000000, fbffffff]
[    0.544447] pci 0000:00:01.0: supports D1
[    0.544493] PCI: 0000:00:09.0 reg 10 32bit mmio: [febffc00, febfffff]
[    0.544545] pci 0000:00:09.0: supports D1
[    0.544548] pci 0000:00:09.0: supports D2
[    0.544592] PCI: 0000:00:0f.0 reg 10 io port: [ec00, ec07]
[    0.544602] PCI: 0000:00:0f.0 reg 14 io port: [e880, e883]
[    0.544610] PCI: 0000:00:0f.0 reg 18 io port: [e800, e807]
[    0.544619] PCI: 0000:00:0f.0 reg 1c io port: [e480, e483]
[    0.544628] PCI: 0000:00:0f.0 reg 20 io port: [e400, e40f]
[    0.544636] PCI: 0000:00:0f.0 reg 24 io port: [e000, e0ff]
[    0.544725] PCI: 0000:00:0f.1 reg 20 io port: [fc00, fc0f]
[    0.544821] PCI: 0000:00:10.0 reg 20 io port: [dc00, dc1f]
[    0.544851] pci 0000:00:10.0: supports D1
[    0.544853] pci 0000:00:10.0: supports D2
[    0.544856] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544862] pci 0000:00:10.0: PME# disabled
[    0.544919] PCI: 0000:00:10.1 reg 20 io port: [d880, d89f]
[    0.544949] pci 0000:00:10.1: supports D1
[    0.544951] pci 0000:00:10.1: supports D2
[    0.544954] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544960] pci 0000:00:10.1: PME# disabled
[    0.545016] PCI: 0000:00:10.2 reg 20 io port: [d800, d81f]
[    0.545046] pci 0000:00:10.2: supports D1
[    0.545048] pci 0000:00:10.2: supports D2
[    0.545051] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545056] pci 0000:00:10.2: PME# disabled
[    0.545113] PCI: 0000:00:10.3 reg 20 io port: [d480, d49f]
[    0.545142] pci 0000:00:10.3: supports D1
[    0.545145] pci 0000:00:10.3: supports D2
[    0.545147] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545153] pci 0000:00:10.3: PME# disabled
[    0.545187] PCI: 0000:00:10.4 reg 10 32bit mmio: [febff800, febff8ff]
[    0.545239] pci 0000:00:10.4: supports D1
[    0.545241] pci 0000:00:10.4: supports D2
[    0.545244] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545249] pci 0000:00:10.4: PME# disabled
[    0.545333] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.545383] PCI: 0000:00:11.5 reg 10 io port: [d000, d0ff]
[    0.545437] pci 0000:00:11.5: supports D1
[    0.545439] pci 0000:00:11.5: supports D2
[    0.545474] PCI: 0000:00:11.6 reg 10 io port: [c800, c8ff]
[    0.545561] PCI: 0000:00:12.0 reg 10 io port: [c400, c4ff]
[    0.545570] PCI: 0000:00:12.0 reg 14 32bit mmio: [febff400, febff4ff]
[    0.545617] pci 0000:00:12.0: supports D1
[    0.545619] pci 0000:00:12.0: supports D2
[    0.545622] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545628] pci 0000:00:12.0: PME# disabled
[    0.545690] PCI: 0000:01:00.0 reg 10 32bit mmio: [f0000000, f3ffffff]
[    0.545698] PCI: 0000:01:00.0 reg 14 32bit mmio: [fd000000, fdffffff]
[    0.545724] PCI: 0000:01:00.0 reg 30 32bit mmio: [feaf0000, feafffff]
[    0.545742] pci 0000:01:00.0: supports D1
[    0.545744] pci 0000:01:00.0: supports D2
[    0.545790] PCI: bridge 0000:00:01.0 32bit mmio: [fca00000, feafffff]
[    0.545796] PCI: bridge 0000:00:01.0 32bit mmio pref: [eff00000, f7efffff]
[    0.545806] bus 00 -> node 0
[    0.545817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.546269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.564961] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.564961] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.564961] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.564961] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.565049] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.565256] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.568155] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.568361] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.568448] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 6C, should be 5F [20080609]
[    0.568448] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.568448] pnp: PnP ACPI init
[    0.568448] ACPI: bus type pnp registered
[    0.580862] pnp: PnP ACPI: found 14 devices
[    0.580862] ACPI: ACPI bus type pnp unregistered
[    0.580862] PnPBIOS: Disabled by ACPI PNP
[    0.580862] PCI: Using ACPI for IRQ routing
[    0.588047] NET: Registered protocol family 8
[    0.588051] NET: Registered protocol family 20
[    0.588084] NetLabel: Initializing
[    0.588087] NetLabel:  domain hash size = 128
[    0.588090] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.588111] NetLabel:  unlabeled traffic allowed by default
[    0.589576] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.589579]    actual entries 65620
[    0.589843] AppArmor: AppArmor Filesystem Enabled
[    0.589865] ACPI: RTC can wake from S4
[    0.596079] system 00:09: ioport range 0xa00-0xa0f has been reserved
[    0.596083] system 00:09: ioport range 0x290-0x29f has been reserved
[    0.596087] system 00:09: ioport range 0xa20-0xa2f has been reserved
[    0.596090] system 00:09: ioport range 0xa30-0xa3f has been reserved
[    0.596094] system 00:09: ioport range 0xa40-0xa4f has been reserved
[    0.596105] system 00:0a: ioport range 0x3e0-0x3e7 has been reserved
[    0.596109] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.596112] system 00:0a: ioport range 0x800-0x87f has been reserved
[    0.596115] system 00:0a: ioport range 0x400-0x41f has been reserved
[    0.596125] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.596129] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.596140] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.596144] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.596147] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.596151] system 00:0d: iomem range 0x100000-0x1bffffff could not be reserved
[    0.596155] system 00:0d: iomem range 0xff380000-0xffffffff has been reserved
[    0.631723] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.631727] pci 0000:00:01.0:   IO window: disabled
[    0.631735] pci 0000:00:01.0:   MEM window: 0xfca00000-0xfeafffff
[    0.631741] pci 0000:00:01.0:   PREFETCH window: 0x000000eff00000-0x000000f7efffff
[    0.631765] pci 0000:00:01.0: setting latency timer to 64
[    0.631771] bus: 00 index 0 io port: [0, ffff]
[    0.631774] bus: 00 index 1 mmio: [0, ffffffff]
[    0.631778] bus: 01 index 0 mmio: [0, 0]
[    0.631781] bus: 01 index 1 mmio: [fca00000, feafffff]
[    0.631783] bus: 01 index 2 mmio: [eff00000, f7efffff]
[    0.631786] bus: 01 index 3 mmio: [0, 0]
[    0.631803] NET: Registered protocol family 2
[    0.632054] Switched to high resolution mode on CPU 0
[    0.632481] Switched to high resolution mode on CPU 1
[    0.644120] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.644480] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.644633] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.644775] TCP: Hash tables configured (established 16384 bind 16384)
[    0.644779] TCP reno registered
[    0.652141] NET: Registered protocol family 1
[    0.652314] checking if image is initramfs... it is
[    1.383125] Freeing initrd memory: 8003k freed
[    1.385445] audit: initializing netlink socket (disabled)
[    1.385478] type=2000 audit(1229391542.384:1): initialized
[    1.391281] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.395176] VFS: Disk quotas dquot_6.5.1
[    1.395335] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.395512] msgmni has been set to 876
[    1.395716] io scheduler noop registered
[    1.395720] io scheduler anticipatory registered
[    1.395723] io scheduler deadline registered
[    1.395741] io scheduler cfq registered (default)
[    1.395767] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.395867] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    1.395883] pci 0000:01:00.0: Boot video device
[    1.396706] isapnp: Scanning for PnP cards...
[    1.628511] Clocksource tsc unstable (delta = 2244369460 ns)
[    1.748464] isapnp: No Plug & Play device found
[    1.812861] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.813037] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.814217] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.817642] brd: module loaded
[    1.817780] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.818033] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.818591] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.818606] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.820265] mice: PS/2 mouse device common for all mice
[    1.820564] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.820610] rtc0: alarms up to one year, y3k
[    1.820865] EISA: Probing bus 0 at eisa.0
[    1.820912] EISA: Detected 0 cards.
[    1.820920] cpuidle: using governor ladder
[    1.820923] cpuidle: using governor menu
[    1.821750] TCP cubic registered
[    1.821803] Using IPI No-Shortcut mode
[    1.822128] registered taskstats version 1
[    1.822312]   Magic number: 4:474:660
[    1.822320] block ram13: hash matches
[    1.822392] tty ptyeb: hash matches
[    1.822552] rtc_cmos 00:02: setting system clock to 2008-12-16 01:39:04 UTC (1229391544)
[    1.822556] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.822559] EDD information not available.
[    1.823157] Freeing unused kernel memory: 424k freed
[    1.823227] Write protecting the kernel text: 2576k
[    1.823272] Write protecting the kernel read-only data: 936k
[    1.853020] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.008676] fuse init (API version 7.9)
[    2.141708] ACPI:   &#65533; FFFF0000, 0000 (r0                        0             0)
[    2.141729] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU1._PDC] (Node db012150), AE_BAD_HEADER
[    2.148041] processor ACPI0007:00: registered as cooling_device0
[    2.148048] ACPI: Processor [CPU1] (supports 16 throttling states)
[    2.202107] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU2._PDC] (Node db0121e0), AE_ALREADY_EXISTS
[    2.202118] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
[    2.202347] processor ACPI0007:01: registered as cooling_device1
[    2.202356] ACPI: Processor [CPU2] (supports 16 throttling states)
[    2.614210] usbcore: registered new interface driver usbfs
[    2.614308] usbcore: registered new interface driver hub
[    2.622544] usbcore: registered new device driver usb
[    2.625136] No dock devices found.
[    2.628732] USB Universal Host Controller Interface driver v3.0
[    2.628849] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.628867] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.628945] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    2.628992] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000dc00
[    2.629282] usb usb1: configuration #1 chosen from 1 choice
[    2.629340] hub 1-0:1.0: USB hub found
[    2.629350] hub 1-0:1.0: 2 ports detected
[    2.666509] SCSI subsystem initialized
[    2.709099] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    2.719387] libata version 3.00 loaded.
[    2.836689] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.836706] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.836748] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    2.836780] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d880
[    2.836930] usb usb2: configuration #1 chosen from 1 choice
[    2.836972] hub 2-0:1.0: USB hub found
[    2.836985] hub 2-0:1.0: 2 ports detected
[    3.044664] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.044683] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.044724] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    3.044756] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    3.044896] usb usb3: configuration #1 chosen from 1 choice
[    3.044943] hub 3-0:1.0: USB hub found
[    3.044960] hub 3-0:1.0: 2 ports detected
[    3.252553] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.252570] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    3.252610] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    3.252645] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d480
[    3.252806] usb usb4: configuration #1 chosen from 1 choice
[    3.252850] hub 4-0:1.0: USB hub found
[    3.252864] hub 4-0:1.0: 2 ports detected
[    3.461307] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    3.461327] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    3.461377] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    3.461438] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfebff800
[    3.472045] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.472375] usb usb5: configuration #1 chosen from 1 choice
[    3.472420] hub 5-0:1.0: USB hub found
[    3.472439] hub 5-0:1.0: 8 ports detected
[    3.576705] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.581105] eth0: VIA Rhine II at 0xfebff400, 00:16:ec:d7:8c:6b, IRQ 23.
[    3.581816] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[    3.597477] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    3.597577] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    3.597605] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.597643] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    3.602169] sata_via 0000:00:0f.0: version 2.3
[    3.602189] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    3.602232] sata_via 0000:00:0f.0: routed to hard irq line 5
[    3.606868] scsi0 : sata_via
[    3.607178] scsi1 : sata_via
[    3.609953] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 20
[    3.609957] ata2: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 20
[    3.812034] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    4.016033] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    4.016215] pata_via 0000:00:0f.1: version 0.3.3
[    4.016239] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.016466] scsi2 : pata_via
[    4.017055] scsi3 : pata_via
[    4.020579] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    4.020584] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    4.394097] ata3.00: ATA-7: WDC WD1600BB-00RDA0, 20.00K20, max UDMA/100
[    4.394102] ata3.00: 312581808 sectors, multi 16: LBA48 
[    4.394130] ata3.01: ATAPI: LITE-ON DVDRW SHW-160P6S, PS08, max UDMA/66
[    4.400429] ata3.00: configured for UDMA/100
[    4.432263] ata3.01: configured for UDMA/66
[    4.599543] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BB-00R 20.0 PQ: 0 ANSI: 5
[    4.600730] scsi 2:0:1:0: CD-ROM            LITE-ON  DVDRW SHW-160P6S PS08 PQ: 0 ANSI: 5
[    4.610826] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[    4.610885] scsi 2:0:1:0: Attached scsi generic sg1 type 5
[    4.640913] Driver 'sd' needs updating - please use bus_type methods
[    4.641138] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.641179] sd 2:0:0:0: [sda] Write Protect is off
[    4.641184] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.641249] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.641386] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.641421] sd 2:0:0:0: [sda] Write Protect is off
[    4.641425] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.641488] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.641495]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    4.662252]  sda5 >
[    4.662499] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.666979] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.666988] Uniform CD-ROM driver Revision: 3.20
[    4.667141] sr 2:0:1:0: Attached scsi CD-ROM sr0
[    4.891490] PM: Starting manual resume from disk
[    4.891499] PM: Resume from partition 8:5
[    4.891502] PM: Checking hibernation image.
[    4.891728] PM: Resume from disk failed.
[    4.954443] kjournald starting.  Commit interval 5 seconds
[    4.954463] EXT3-fs: mounted filesystem with ordered data mode.
[   10.901614] udevd version 124 started
[   11.219727] Linux agpgart interface v0.103
[   11.237058] agpgart: Detected VIA VT3314 chipset
[   11.242357] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   11.342718] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.508033] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.605529] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   11.620057] ACPI: Power Button (FF) [PWRF]
[   11.620267] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[   11.652108] ACPI: Sleep Button (CM) [SLPB]
[   11.652306] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   11.684055] ACPI: Power Button (CM) [PWRB]
[   11.993928] Linux video capture interface: v2.00
[   12.052638] parport_pc 00:08: reported by Plug and Play ACPI
[   12.052697] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   12.123015] saa7130/34: v4l2 driver version 0.2.14 loaded
[   12.123134] saa7134 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.123145] saa7130[0]: found at 0000:00:09.0, rev: 1, irq: 17, latency: 64, mmio: 0xfebffc00
[   12.123159] saa7130[0]: subsystem: 1131:2341, board: Encore ENLTV [card=106,autodetected]
[   12.123180] saa7130[0]: board init: gpio is 5d31ff
[   12.123347] input: saa7134 IR (Encore ENLTV) as /devices/pci0000:00/0000:00:09.0/input/input5
[   12.358591] saa7130[0]: i2c eeprom 00: 31 11 41 23 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   12.358611] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[   12.358627] saa7130[0]: i2c eeprom 20: 41 41 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358643] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358659] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358675] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358691] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358707] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358723] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358739] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358755] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358771] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358787] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358803] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358819] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.358835] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.788061] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   12.820546] All bytes are equal. It is not a TEA5767
[   12.820685] tuner' 0-0060: chip found @ 0xc0 (saa7130[0])
[   12.828549] tuner' 0-0061: chip found @ 0xc2 (saa7130[0])
[   12.908543] tuner-simple 0-0060: creating new instance
[   12.908550] tuner-simple 0-0060: type set to 69 (Tena TNF 5335 and similar models)
[   12.937424] saa7130[0]: registered device video0 [v4l2]
[   12.937479] saa7130[0]: registered device vbi0
[   12.937538] saa7130[0]: registered device radio0
[   13.114951] saa7134 ALSA driver for DMA sound loaded
[   13.128025] saa7130[0]/alsa: saa7130[0] at 0xfebffc00 irq 17 registered as card -2
[   13.318252] VIA 82xx Modem 0000:00:11.6: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   13.323528] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   13.362311] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   13.830370] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   13.830549] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   14.897224] lp0: using parport0 (interrupt-driven).
[   15.079529] Adding 1309256k swap on /dev/sda5.  Priority:-1 extents:1 across:1309256k
[   15.650965] EXT3 FS on sda1, internal journal
[   16.770982] type=1505 audit(1229391559.013:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3970
[   16.996315] type=1505 audit(1229391559.241:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3975
[   16.996720] type=1505 audit(1229391559.241:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3975
[   17.168648] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.915168] ACPI: WMI: Mapper loaded
[   18.889773] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.990337] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   18.990355] apm: disabled - APM is not SMP safe.
[   19.140708] ppdev: user-space parallel port driver
[   23.446770] [drm] Initialized drm 1.1.0 20060810
[   23.458675] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.459572] [drm] Initialized via 2.11.1 20070202 on minor 0
[   23.486581] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   23.486642] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   23.486755] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   25.185361] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   25.370323] NET: Registered protocol family 17
[   82.867208] NET: Registered protocol family 10
[   82.869322] lo: Disabled Privacy Extensions
[ 1009.608541] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 1009.837682] usb 2-1: configuration #1 chosen from 1 choice
```

Es muy larga, disculpen si no había que poner todo pero no sabía cual era la parte importante.

---

### Post by mhoyos on 2008-12-15
cuando "pegaste" la salida de dmesg, conectaste la camara ??

sino, mandalo de nuevo, despues de conectar la camara... pero hacerlo asi:

```
#dmesg > dmesg.txt 
```
y adjunta el archivo.txt al post.. :)

salu2

---

### Post by Martinius on 2008-12-15
mhoyos, la cámara estaba conectada pero lo mando como txt para que sea más facil de analizar.

---

