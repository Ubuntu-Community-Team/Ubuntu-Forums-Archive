---
title: "Desde la instalación del Ubuntu 9.04 el ordenador se cuelga"
date: 2009-05-07
forum: Hardware
---

### Post by Urfe on 2009-05-07
Hoy se me ha colgado ya unas 4 veces. Ocurre haciendo diversas tareas, a veces abriendo el menu Sistema, otras navegando con Firefox.

Parece que no soy el único al que le pasa, pero no encontramos solución.

Tengo una tarjeta Nvidia 7700 i una CPU AMD Athlom 64 X2 Dual Core Processor 4200+

Saludos.

---

### Post by pablo.s on 2009-05-07
Verifica que la temperatura del
procesador no esté alcanzando
puntos máximos. Si está llegando
a 85 - 90° C es un indicio.

---

### Post by guillermolisi on 2009-05-09
> **pablo.s said:**
> Verifica que la temperatura del
procesador no esté alcanzando
puntos máximos. Si está llegando
a 85 - 90° C es un indicio.
Agrego revisar el estado y capacidad operativa de la fuente de alimentacion.
Con una placa de video como la que tenes si la fuente esta medio pinchada es posible que el sistema se torne inestable con una fuente en malas condiciones.

---

### Post by Urfe on 2009-05-11
Gracias por las respuestas.

La temperatura no llega a niveles tan altos. Alguna vez sí ha subido bastante, pero otras veces el ordenador se cuelga a temperaturas menores.

Guillermolisi: ¿Cómo podría saber el estado y capacidad operativa de la fuente de alimentación? Cuando dices que la fuente puede estar medio pinchada, ¿qué quieres decir exactamente?

Gracias de nuevo.

---

### Post by guillermolisi on 2009-05-11
> **Urfe said:**
> Gracias por las respuestas.

La temperatura no llega a niveles tan altos. Alguna vez sí ha subido bastante, pero otras veces el ordenador se cuelga a temperaturas menores.

Guillermolisi: ¿Cómo podría saber el estado y capacidad operativa de la fuente de alimentación? Cuando dices que la fuente puede estar medio pinchada, ¿qué quieres decir exactamente?

Gracias de nuevo.
Las fuentes de alimentacion tienen caracteristicas operativas en regimen y una especial para el momento del inicio conocida como HiPot (alta potencia) que permite entregar mucha mas potencia que la nominal en una cantidad de tiempo chica (hasta que el resto de los componentes entran en regimen).

Es conocido que muchas marcas genericas de fuentes mienten con su verdadera potencia. Asi, vas a encontrar algunas que dicen ser de 400Watts y entregan a lo sumo 300W.

Luego, si sus componentes (particularmente sus condensadores electroliticos) no estan bien dimensionados o la fuente no esta bien ventilada, es comun qeu con el uso y el paso del tiempo se degrade y en lugar de poder entregar su potencia nominal entregue una menor logrando que cuando le agregas a la maquina un componente que requiere mucha corriente la maquina se torne inestable (como una placa de video con aceleracion 3D).

Tambien juega que otros componentes estan instalados ya que a veces con solo enchufar un periferico USB es suficiente para que la maquina se apague (la corriente maxima de un port USB es de alrededor de 500mA).

Como medir el estado de la fuente ? Laboratorio, revision ocular (los capacitores/condensadores se hinchan y hasta puede haber perdida del electrolito que contienen). Ver si levanta temperatura excesiva, tanto que se sienta desde la parte externa del gabiente como muy caliente (en general es normal que se encuentre tibia si hace tiempo que la maquina esta encendida).

Hay fuentes con sensores, como algunos modelos ThermalTake, pero son muucho mas caras de lo que mucha gente estaria dispuesta a pagar.

---

### Post by Urfe on 2009-05-13
Gracias, Guillermolisi por la extensa explicación.

No parece que la fuente de alimentación se caliente excesivamente.

Pero lo que más me hace pensar que se trata de un problema de software es que como Ubuntu se cuelga continuamente, llevo días usando el Windows que tengo en otra partición y no se ha colgado nunca.

En cuanto a la temperatura de la CPU y la placa base, he observado varias veces que en el momento de colgarse no estaban muy calientes.

---

### Post by guillermolisi on 2009-05-13
> **Urfe said:**
> Gracias, Guillermolisi por la extensa explicación.

No parece que la fuente de alimentación se caliente excesivamente.

Pero lo que más me hace pensar que se trata de un problema de software es que como Ubuntu se cuelga continuamente, llevo días usando el Windows que tengo en otra partición y no se ha colgado nunca.

En cuanto a la temperatura de la CPU y la placa base, he observado varias veces que en el momento de colgarse no estaban muy calientes.
Ok. En ese caso lo primero que haria es leer los logs: /var/log/dmesg y /var/log/messages por lo menos en busca de algun indicio.

Con Win no tenes "blue screen" en forma repetida ?

---

### Post by bolhas on 2009-05-14
Me pasa lo mismo con un Compaq 2520EU, en windows funciona y no en Ubuntu 9.04.
 en el log :
"May 13 10:38:38 gabriel-laptop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] last_pfn = 0x37f70 max_arch_pfn = 0x100000
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] Scanning 0 areas for low memory corruption
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] modified physical RAM map:
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 00000000000d8000 - 00000000000e0000 (reserved)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 0000000000100000 - 0000000037f70000 (usable)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 0000000037f70000 - 0000000037f7c000 (ACPI data)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 0000000037f7c000 - 0000000037f80000 (ACPI NVS)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 0000000037f80000 - 0000000038000000 (reserved)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 0000000047f80000 - 0000000048000000 (reserved)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] RAMDISK: 3782c000 - 37f5fbf2
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] Allocated new RAMDISK: 00881000 - 00fb4bf2
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] Move RAMDISK from 000000003782c000 - 0000000037f5fbf1 to 00881000 - 00fb4bf1
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] ACPI: RSDP 000F6AB0, 0014 (r0 PTLTD )
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] ACPI: RSDT 37F75284, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] ACPI: FACP 37F7BF64, 0074 (r1 ATI    Salmon    6040000 ATI     F4240)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] ACPI: DSDT 37F752B0, 6CB4 (r1    ATI MS2_1535  6040000 MSFT  100000E)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] ACPI: FACS 37F7CFC0, 0040
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] ACPI: BOOT 37F7BFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] 11MB HIGHMEM available.
May 13 10:38:38 gabriel-laptop kernel: [    0.000000] 883MB LOWMEM available."

---

### Post by guillermolisi on 2009-05-14
A los que se les cuelga la maquina con JJ, que version de Kernel estan usando ?

---

### Post by Urfe on 2009-05-14
La versión que tengo es 2.6.28-11-generic

Los archivos messages y dmesg son muy largos y no soy capaz de postearlos. Como adjuntos ocupan 45 KB, más del límite. Y copiados directamente parecen tener más de 8 imágenes (no tienen ninguna ¿?).

Pego un extracto de messages. Entre las 17:56 y las 18:06 la computadora se colgó.


May 13 17:56:17 albert-desktop kernel: [    7.529112] usb 2-10: configuration #1 chosen from 1 choice 
May 13 17:56:17 albert-desktop kernel: [   12.510769] udev: starting version 141 
May 13 17:56:17 albert-desktop kernel: [   12.830989] resource map sanity check conflict: 0xff000000 0xffffffff 0xfff80000 0xfff80fff pnp 00:0d 
May 13 17:56:17 albert-desktop kernel: [   12.830997] ------------[ cut here ]------------ 
May 13 17:56:17 albert-desktop kernel: [   12.831000] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390() 
May 13 17:56:17 albert-desktop kernel: [   12.831002] Modules linked in: ck804xrom(+) mtd chipreg map_funcs usbhid forcedeth floppy fbcon tileblit font bitblit softcursor 
May 13 17:56:17 albert-desktop kernel: [   12.831013] Pid: 913, comm: modprobe Not tainted 2.6.28-11-generic #42-Ubuntu 
May 13 17:56:17 albert-desktop kernel: [   12.831015] Call Trace: 
May 13 17:56:17 albert-desktop kernel: [   12.831023]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90 
May 13 17:56:17 albert-desktop kernel: [   12.831027]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10 
May 13 17:56:17 albert-desktop kernel: [   12.831029]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10 
May 13 17:56:17 albert-desktop kernel: [   12.831033]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390 
May 13 17:56:17 albert-desktop kernel: [   12.831037]  [<ffffffffa00792db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom] 
May 13 17:56:17 albert-desktop kernel: [   12.831041]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20 
May 13 17:56:17 albert-desktop kernel: [   12.831044]  [<ffffffffa00792db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom] 
May 13 17:56:17 albert-desktop kernel: [   12.831048]  [<ffffffffa007f041>] init_ck804xrom+0x41/0x59 [ck804xrom] 
May 13 17:56:17 albert-desktop kernel: [   12.831051]  [<ffffffffa007f000>] ? init_ck804xrom+0x0/0x59 [ck804xrom] 
May 13 17:56:17 albert-desktop kernel: [   12.831055]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170 
May 13 17:56:17 albert-desktop kernel: [   12.831060]  [<ffffffff8041bee9>] ? rb_insert_color+0x109/0x140 
May 13 17:56:17 albert-desktop kernel: [   12.831065]  [<ffffffff802424b2>] ? enqueue_entity+0x122/0x2b0 
May 13 17:56:17 albert-desktop kernel: [   12.831068]  [<ffffffff802486cd>] ? enqueue_task_fair+0x3d/0x80 
May 13 17:56:17 albert-desktop kernel: [   12.831071]  [<ffffffff8023e2a9>] ? wakeup_preempt_entity+0x59/0x60 
May 13 17:56:17 albert-desktop kernel: [   12.831073]  [<ffffffff80249330>] ? check_preempt_wakeup+0x210/0x230 
May 13 17:56:17 albert-desktop kernel: [   12.831076]  [<ffffffff8024a3cc>] ? try_to_wake_up+0x12c/0x2e0 
May 13 17:56:17 albert-desktop kernel: [   12.831082]  [<ffffffff8027ef9d>] sys_init_module+0xad/0x1e0 
May 13 17:56:17 albert-desktop kernel: [   12.831085]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b 
May 13 17:56:17 albert-desktop kernel: [   12.831087] ---[ end trace 953bec0046610fad ]--- 
May 13 17:56:17 albert-desktop kernel: [   13.662592] nvidia: module license 'NVIDIA' taints kernel. 
May 13 17:56:17 albert-desktop kernel: [   13.695266] parport_pc 00:0a: reported by Plug and Play ACPI 
May 13 17:56:17 albert-desktop kernel: [   13.695293] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP] 
May 13 17:56:17 albert-desktop kernel: [   13.726640] Linux video capture interface: v2.00 
May 13 17:56:17 albert-desktop kernel: [   13.750083] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00 
May 13 17:56:17 albert-desktop kernel: [   13.750088] ACPI: I/O resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM01 [0x1c40-0x1c45] 
May 13 17:56:17 albert-desktop kernel: [   13.750090] ACPI: Device needs an ACPI driver 
May 13 17:56:17 albert-desktop kernel: [   13.750124] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40 
May 13 17:56:17 albert-desktop kernel: [   13.769401] input: PC Speaker as /devices/platform/pcspkr/input/input5 
May 13 17:56:17 albert-desktop kernel: [   13.804437] ppdev: user-space parallel port driver 
May 13 17:56:17 albert-desktop kernel: [   13.813842] gspca: main v2.3.0 registered 
May 13 17:56:17 albert-desktop kernel: [   13.841820] Found: PMC Pm49FL004 
May 13 17:56:17 albert-desktop kernel: [   13.841829] ck804xrom @fff80000: Found 1 x8 devices at 0x0 in 8-bit bank 
May 13 17:56:17 albert-desktop kernel: [   13.885312] number of JEDEC chips: 1 
May 13 17:56:17 albert-desktop kernel: [   13.885316] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness. 
May 13 17:56:17 albert-desktop kernel: [   13.918517] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16 
May 13 17:56:17 albert-desktop kernel: [   13.918530] nvidia 0000:07:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16 
May 13 17:56:17 albert-desktop kernel: [   13.919245] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009 
May 13 17:56:17 albert-desktop kernel: [   13.925293] gspca: probing 046d:0920 
May 13 17:56:17 albert-desktop kernel: [   13.982992] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21 
May 13 17:56:17 albert-desktop kernel: [   13.982998] HDA Intel 0000:00:06.1: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21 
May 13 17:56:17 albert-desktop kernel: [   14.046043] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17 
May 13 17:56:17 albert-desktop kernel: [   14.046055] ENS1371 0000:01:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17 
May 13 17:56:17 albert-desktop kernel: [   14.668164] gspca: probe ok 
May 13 17:56:17 albert-desktop kernel: [   14.668187] usbcore: registered new interface driver tv8532 
May 13 17:56:17 albert-desktop kernel: [   14.668208] tv8532: registered 
May 13 17:56:17 albert-desktop kernel: [   15.280895] Control name 'Sigmatel Surround Phase Inversion Playback Switch' truncated to 'Sigmatel Surround Phase Inversion Playback ' 
May 13 17:56:17 albert-desktop kernel: [   15.402806] lp0: using parport0 (interrupt-driven). 
May 13 17:56:17 albert-desktop kernel: [   15.590036] Adding 3012148k swap on /dev/sda6.  Priority:-1 extents:1 across:3012148k 
May 13 17:56:17 albert-desktop kernel: [   16.143421] EXT3 FS on sda5, internal journal 
May 13 17:56:17 albert-desktop kernel: [   17.226955] type=1505 audit(1242230175.565:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2119 
May 13 17:56:17 albert-desktop kernel: [   17.280367] type=1505 audit(1242230175.617:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2123 
May 13 17:56:17 albert-desktop kernel: [   17.280515] type=1505 audit(1242230175.617:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2123 
May 13 17:56:17 albert-desktop kernel: [   17.280560] type=1505 audit(1242230175.617:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2123 
May 13 17:56:17 albert-desktop kernel: [   17.280604] type=1505 audit(1242230175.617:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2123 
May 13 17:56:17 albert-desktop kernel: [   17.403740] type=1505 audit(1242230175.741:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2128 
May 13 17:56:17 albert-desktop kernel: [   17.403928] type=1505 audit(1242230175.741:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2128 
May 13 17:56:17 albert-desktop kernel: [   17.433235] type=1505 audit(1242230175.773:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2132 
May 13 17:56:19 albert-desktop kernel: [   21.041330] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
May 13 17:56:19 albert-desktop kernel: [   21.041333] Bluetooth: BNEP filters: protocol multicast 
May 13 17:56:19 albert-desktop kernel: [   21.055312] Bridge firewalling registered 
May 13 17:56:33 albert-desktop pulseaudio[3393]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 44099 Hz. 
May 13 18:06:04 albert-desktop syslogd 1.5.0#5ubuntu3: restart. 
May 13 18:06:04 albert-desktop kernel: Inspecting /boot/System.map-2.6.28-11-generic 
May 13 18:06:04 albert-desktop kernel: Cannot find map file. 
May 13 18:06:04 albert-desktop kernel: Loaded 75342 symbols from 53 modules. 
May 13 18:06:04 albert-desktop kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Initializing cgroup subsys cpu 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Command line: root=UUID=467aa755-9d2b-4dfb-8906-3d146bda952f ro quiet splash 
May 13 18:06:04 albert-desktop kernel: [    0.000000] KERNEL supported cpus: 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   Intel GenuineIntel 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   AMD AuthenticAMD 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   Centaur CentaurHauls 
May 13 18:06:04 albert-desktop kernel: [    0.000000] BIOS-provided physical RAM map: 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] DMI 2.4 present. 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around. 
May 13 18:06:04 albert-desktop kernel: [    0.000000] last_pfn = 0x3fee0 max_arch_pfn = 0x3ffffffff 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Scanning 0 areas for low memory corruption 
May 13 18:06:04 albert-desktop kernel: [    0.000000] modified physical RAM map: 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  modified: 0000000000100000 - 000000003fee0000 (usable) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  modified: 000000003fee0000 - 000000003fee3000 (ACPI NVS) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  modified: 000000003fee3000 - 000000003fef0000 (ACPI data) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  modified: 000000003fef0000 - 000000003ff00000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000003fee0000 
May 13 18:06:04 albert-desktop kernel: [    0.000000] last_map_addr: 3fee0000 end: 3fee0000 
May 13 18:06:04 albert-desktop kernel: [    0.000000] RAMDISK: 3786a000 - 37fef05f 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: RSDP 000F7760, 0024 (r2 Nvidia) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: XSDT 3FEE30C0, 0044 (r1 Nvidia AWRDACPI 42302E31 AWRD        0) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: FACP 3FEEC380, 00F4 (r3 Nvidia AWRDACPI 42302E31 AWRD        0) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (8) does not match PM1_EVT_LEN (4) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: DSDT 3FEE3240, 90ED (r1 NVIDIA AWRDACPI     1000 MSFT  100000E) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: FACS 3FEE0000, 0040 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: HPET 3FEEC580, 0038 (r1 Nvidia AWRDACPI 42302E31 AWRD       98) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: MCFG 3FEEC600, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: APIC 3FEEC4C0, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD        0) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] (6 early reservations) ==> bootmem [0000000000 - 003fee0000] 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000] 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000] 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0] 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   #3 [003786a000 - 0037fef05f]          RAMDISK ==> [003786a000 - 0037fef05f] 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000] 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   #5 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000] 
May 13 18:06:04 albert-desktop kernel: [    0.000000] found SMP MP-table at [ffff8800000f5a80] 000f5a80 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Zone PFN ranges: 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000 
May 13 18:06:04 albert-desktop kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Movable zone start PFN for each node 
May 13 18:06:04 albert-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges 
May 13 18:06:04 albert-desktop kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f 
May 13 18:06:04 albert-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0003fee0 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1]) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1]) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0]) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information 
May 13 18:06:04 albert-desktop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs 
May 13 18:06:04 albert-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000 
May 13 18:06:04 albert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000 
May 13 18:06:04 albert-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:b0100000) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] PERCPU: Allocating 69632 bytes of per cpu data 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 255622 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Kernel command line: root=UUID=467aa755-9d2b-4dfb-8906-3d146bda952f ro quiet splash 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Initializing CPU#0 
May 13 18:06:04 albert-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes) 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Extended CMOS year: 2000 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Fast TSC calibration using PIT 
May 13 18:06:04 albert-desktop kernel: [    0.000000] Detected 2209.894 MHz processor. 
May 13 18:06:04 albert-desktop kernel: [    0.004000] Console: colour VGA+ 80x25 
May 13 18:06:04 albert-desktop kernel: [    0.004000] console [tty0] enabled 
May 13 18:06:04 albert-desktop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes) 
May 13 18:06:04 albert-desktop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes) 
May 13 18:06:04 albert-desktop kernel: [    0.004000] allocated 10485760 bytes of page_cgroup 
May 13 18:06:04 albert-desktop kernel: [    0.004000] please try cgroup_disable=memory option if you don't want 
May 13 18:06:04 albert-desktop kernel: [    0.004000] Scanning for low memory corruption every 60 seconds 
May 13 18:06:04 albert-desktop kernel: [    0.004000] Checking aperture... 
May 13 18:06:04 albert-desktop kernel: [    0.004000] No AGP bridge found 
May 13 18:06:04 albert-desktop kernel: [    0.004000] Node 0: aperture @ 8cb0000000 size 32 MB 
May 13 18:06:04 albert-desktop kernel: [    0.004000] Aperture beyond 4GB. Ignoring.

---

### Post by Urfe on 2009-05-14
Ahora pego el archivo dmesg.

Ah, por cierto, en Windows no aparece la pantalla típica azul con letras blancas que aparece a veces si el ordenador se cuelga, si es eso a lo que te referías. En windows todo va bien, no se cuelga nunca.

[   15.278945] ppdev: user-space parallel port driver 
[   15.284889] Linux video capture interface: v2.00 
[   15.330399] gspca: main v2.3.0 registered 
[   15.341752] gspca: probing 046d:0920 
[   15.399925] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00 
[   15.399930] ACPI: I/O resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM01 [0x1c40-0x1c45] 
[   15.399932] ACPI: Device needs an ACPI driver 
[   15.399966] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40 
[   15.417130] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16 
[   15.417145] nvidia 0000:07:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16 
[   15.417153] nvidia 0000:07:00.0: setting latency timer to 64 
[   15.417520] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009 
[   15.467744] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug? 
[   15.467755] resource map sanity check conflict: 0xff000000 0xffffffff 0xfff80000 0xfff80fff pnp 00:0d 
[   15.467763] ------------[ cut here ]------------ 
[   15.467766] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390() 
[   15.467768] Modules linked in: ck804xrom(+) mtd chipreg snd_seq_device snd_timer map_funcs i2c_nforce2 snd soundcore gspca_tv8532(+) gspca_main snd_page_alloc compat_ioctl32 videodev v4l1_compat pcspkr ppdev k8temp parport_pc parport nvidia(P) usbhid floppy forcedeth fbcon tileblit font bitblit softcursor 
[   15.467789] Pid: 922, comm: modprobe Tainted: P           2.6.28-11-generic #42-Ubuntu 
[   15.467791] Call Trace: 
[   15.467798]  [<ffffffff802509bf>] warn_on_slowpath+0x5f/0x90 
[   15.467801]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10 
[   15.467804]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10 
[   15.467807]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390 
[   15.467812]  [<ffffffffa08f32db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom] 
[   15.467815]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20 
[   15.467819]  [<ffffffffa08f32db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom] 
[   15.467822]  [<ffffffffa084b041>] init_ck804xrom+0x41/0x59 [ck804xrom] 
[   15.467826]  [<ffffffffa084b000>] ? init_ck804xrom+0x0/0x59 [ck804xrom] 
[   15.467829]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170 
[   15.467834]  [<ffffffff802424b2>] ? enqueue_entity+0x122/0x2b0 
[   15.467837]  [<ffffffff8024870b>] ? enqueue_task_fair+0x7b/0x80 
[   15.467840]  [<ffffffff8023e2a9>] ? wakeup_preempt_entity+0x59/0x60 
[   15.467842]  [<ffffffff80249330>] ? check_preempt_wakeup+0x210/0x230 
[   15.467845]  [<ffffffff8024a3cc>] ? try_to_wake_up+0x12c/0x2e0 
[   15.467850]  [<ffffffff8027ef9d>] sys_init_module+0xad/0x1e0 
[   15.467853]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b 
[   15.467856] ---[ end trace 2565950ba93d3175 ]--- 
[   15.531529] Found: PMC Pm49FL004 
[   15.531539] ck804xrom @fff80000: Found 1 x8 devices at 0x0 in 8-bit bank 
[   15.560008] number of JEDEC chips: 1 
[   15.560012] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness. 
[   15.612659] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17 
[   15.612674] ENS1371 0000:01:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17 
[   15.664242] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21 
[   15.664247] HDA Intel 0000:00:06.1: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21 
[   15.664312] HDA Intel 0000:00:06.1: setting latency timer to 64 
[   16.087157] gspca: probe ok 
[   16.087184] usbcore: registered new interface driver tv8532 
[   16.087206] tv8532: registered 
[   16.852521] Control name 'Sigmatel Surround Phase Inversion Playback Switch' truncated to 'Sigmatel Surround Phase Inversion Playback ' 
[   16.969422] lp0: using parport0 (interrupt-driven). 
[   17.147880] Adding 3012148k swap on /dev/sda6.  Priority:-1 extents:1 across:3012148k 
[   17.701809] EXT3 FS on sda5, internal journal 
[   18.691597] type=1505 audit(1242230763.028:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2143 
[   18.736517] type=1505 audit(1242230763.076:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2147 
[   18.736669] type=1505 audit(1242230763.076:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2147 
[   18.736714] type=1505 audit(1242230763.076:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2147 
[   18.736755] type=1505 audit(1242230763.076:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2147 
[   18.859122] type=1505 audit(1242230763.196:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2152 
[   18.859307] type=1505 audit(1242230763.196:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2152 
[   18.888762] type=1505 audit(1242230763.228:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2156 
[   22.366436] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   22.366439] Bluetooth: BNEP filters: protocol multicast 
[   22.382994] Bridge firewalling registered

---

### Post by bolhas on 2009-06-10
El kernel lo he actualizado a 2.6.29.02062903 y parece que el cuelgues no es tan radical  , consiguo apagar con el boton de apagado del portatil y no como antes que quitaba la bateria y la alimentación . Antes se quedaba con el bloq mayusculas parpadeando . he intendado trabajar sin el adaptador wireless usb y continua colgandose, no consiguo abrir sesión en terminal. Ocurre en cualquier aplicación fallando de repente.  En XP no me da error, pero todo apunta a fallo de harware , ¿Como puedo verificar el hard con Linux?,
Gracias !

---

### Post by Urfe on 2009-06-11
Hola, hace unos días actualicé el kernel a 2.6.30 por consejo obtenido en el siguiente hilo:

[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)   (en inglés)

Llevan ya 41 páginas debatiendo porqué a tanta gente se le cuelga la computadora.

Desde la actualización los cuelges se han vuelto mucho más esporádicos. Un par al día, mientras que antes se producían a los 10-30 minutos de encender la computadora.

---

### Post by pablo.s on 2009-06-11
Perdoná la pregunta,
pero ¿alguna razón para
actualizar a esa versión?
Es compilado por vos o
lo bajaste de un PPA?

---

### Post by Urfe on 2009-06-11
Lo bajé del siguiente lugar:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

Por cierto, que en la página 40 del hilo, petricb comenta que para el la solución definitiva ha sido instalar un controlador obtenido del sitio de nvidia.

¿Alguien sabe cómo se instala? Es demasiado complicado para mí.

---

### Post by pablo.s on 2009-06-11
> **Urfe said:**
> ¿Alguien sabe cómo se instala? Es demasiado complicado para mí.

Tenés que ir a [este sitio,]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run")
bajar el driver, darle
permisos de ejecución
y ejecutarlo en la terminal
con 
[B][COLOR=DarkGreen]
sh NVIDIA-Linux-x86-185.18.14-pkg1.run[/COLOR][/B]

y después vemos que pasa.
Por supuesto que yo no lo
hice, sigo las actualizaciones
normales de Jaunty y en diez
años y pico se me debe haber
colgado el sistema unas 
quince veces.

---

### Post by Urfe on 2009-06-11
Gracias por la info.

Qué suerte tienes de que se te haya colgado tan poco. Somos un montón los que sí tenemos cuelgues desde que llegó el Jaunty.

Cómo se le dan los permisos de ejecución?

Gracias.

---

### Post by pablo.s on 2009-06-11
> **Urfe said:**
> Cómo se le dan los permisos de ejecución?

[COLOR="DarkGreen"][B]chmod 755 NVIDIA-Linux-x86-185.18.14-pkg1.run
[/B][/COLOR]

Cuelgue de sistema, no,
y suelo comenzar cada ciclo
desde las Alpha 4, que es
cuando es mas inestable.
Si puedo tener muchos
segfaults e incluso kernel
panics, pero que explote
en el aire mientras lo
utilizo no, es muy muy raro.

---

### Post by Urfe on 2009-06-12
Cuando le intento dar los permisos con el comando que dijiste, devuelve el siguiente mensaje:

chmod: no se ha podido acceder a «NVIDIA-Linux-x86-185.18.14-pkg1.run»: No such file or directory

He pensado que ta vez el archivo no debía estar en el escritorio, sino en /home, pero no me deja mover el archivo.

---

### Post by staar on 2009-06-12
el archivo debería estar en /home/*tuusuario* para que ese comando funcione así, si no lo podés mover, antes de poner el comando poné ```
cd Escritorio
``` (o Desktop, según como tengas el sistema)

saludos

---

### Post by Urfe on 2009-06-12
Mmmm...

Empieza a instalar y aparece el mensaje siguiente:

Nvidia driver debe ser instalado como root

Pero yo soy el único usuario de esta computadora...

---

### Post by pablo.s on 2009-06-12
Entonces escribi:

[COLOR="DarkGreen"]**sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run**[/COLOR]

---

### Post by staar on 2009-06-12
pero antes de instalar el driver tenés que matar las X, si no no funca, los pasos son los siguientes:

-Ctrl + Alt + F1 para pasarte a una consola virtual
-loguearte con tu usuario en dicha consola
-correr ```
sudo /etc/init.d/gdm stop
```
-correr ```
cd Escritorio
```
-correr ```
sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run
```
-seguir el asistente para instalar el driver
-correr ```
sudo /etc/init.d/gdm start
```

saludos

---

