---
title: "Problemas con resolución en Nvidia"
date: 2010-07-20
forum: Hardware
---

### Post by marcelo_bur on 2010-07-20
Hola. Estaba por abrir un tema, pero viendo que aqui se trata más o menos de lo mismo que quiero preguntar creo que es mejor usar este tema.
Vamos al grano... yo tengo una pc de escritorio cuya mother tiene una tarjeta de vidie Nvidia. Hasta hace poco estuve usando Ubuntu 8.04 y un monitor viejo de 15 pulgadas sin ningún problema. Luego migré a Ubuntu 10.04, tambien sin problemas salvo que el monitor parpadeaba bastante en una esquina (ya lo hacia, aunque menos, con el 8.04). Como ya tenía decidido cambiar el monitor compré un Samsung de 22 pulgadas. El SO operativo lo reconoció sin problemas y abrió la sesión con la resolución adecuada 1920x1080 a 60 Hz. Sin embargo la pantalla se me puso muy lenta, algo no está bien. Leí que podía ser un problemas de drivers e instalé el propietario de Nvidia, lo cual no mejoró para nada la situación, por el contrario, sin este driver consigo que la pc funcione mejor bajando la resolución, con el de Nvidia la bajaba y al encender de nuevo la maquina volvia a 1920x1080 automáticamente. Lo quité y estoy usando una resolucion menor, 1440x900 a 60 Hz (si bien no es la adecuada ya que este monitor es para una relacion 16:9 y esta es 16:10) con lo cual anda bastante bien, pero no del todo bien. Me han sugerido que agregue  una tarjeta de video y le he encargado a un técnico al que considero bueno que me averigue sobre la mejor opción para esta máquina y este sistema operativo. Pero se me ocurrio que aquí hay gente que sabe mucho de todo esto y quizás me pueda decir si, primero, una nueva tarjeta puede solucionar el problema y, segundo, cual es a su criterio la más adecuada. 
No se que modelo de mother tengo, el procesador es un AMD Athlon (tm) 64x2 Dual Core Processor 5200+, al menos eso sale en el monitor de sistema, tengo una memoria de un giga que, descontado lo que consume la tarjeta de video integrada, me deja 875.5 MB de RAM.
Desde ya muchas gracias por cualquier consejo o idea que me puedan aportar.

---

### Post by guillermolisi on 2010-07-20
Probaste lo que sugiere Starr en el How To ?
Que resultados obtuviste ?

Personalmente no veo necesidad de utilizar otra placa de video a menos que quieras contar con memoria propia y asi no consumir de la RAM general o porque existan bien fundamentadas sospechas de que la placa integrada esta defectuosa.

---

### Post by alfplayer on 2010-07-20
Con *lspci* podés saber que chip de video tenés, y después podés buscar información de qué versión del driver funciona.

---

### Post by marcelo_bur on 2010-07-20
> **guillermolisi said:**
> Probaste lo que sugiere Starr en el How To ?
Que resultados obtuviste ?

Personalmente no veo necesidad de utilizar otra placa de video a menos que quieras contar con memoria propia y asi no consumir de la RAM general o porque existan bien fundamentadas sospechas de que la placa integrada esta defectuosa.

Hola y gracias por responder. No probé con las instrucciones de ese tema, en el cual erróneamente publiqué mi consulta, porque si bien el tema es similar mi problema es otro. Desde que uso este monitor con Ubuntu 10.04 la imagen se desplaza con lentitud, si estoy trabajando con una planilla de calculo y quiero seleccionar una cantidad grande de datos, lo hace lentamente, y cosas así. Como si quisieses utilizar programas muy pesados en una máquina vieja, sin embargo la mía quizás no sea la "GRAN COSA", pero tampoco es un cacharro viejo. A mi se me hace cosa de memoria, aunque no se lo suficiente para estar seguro.
Lo curioso es que tengo una partición con window$, por si las moscas, y si bien no lo he usado mucho, parece funcionar mejor. Tal vez porque el driver instalado es el que vino con el cd de la motherboard.
Sigo investigando.

---

### Post by marcelo_bur on 2010-07-20
> **alfplayer said:**
> Con *lspci* podés saber que chip de video tenés, y después podés buscar información de qué versión del driver funciona.

Gracias Alfaplayer.
Esto es lo que me tiró lspci, con la opción más sencilla para buscar datos:


marcelo@ubuntu:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 2f00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at ec00 [size=64]
	I/O ports at 2d00 [size=64]
	I/O ports at 2e00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fdffec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fdffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fdffe800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fdff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at e480 [size=8]
	I/O ports at e400 [size=4]
	I/O ports at e080 [size=8]
	I/O ports at e000 [size=4]
	I/O ports at dc00 [size=16]
	Memory at fdff6000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 31
	Memory at fdffc000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d880 [size=8]
	Memory at fdffe400 (32-bit, non-prefetchable) [size=256]
	Memory at fdffe000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
	Expansion ROM at fdfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau

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

marcelo@ubuntu:~$ 


Veremos que puedo sacar en claro a partir de estos datos y voy a buscar en la base de datos de drivers para Unix de Nvidia.
Saludos

---

### Post by alfplayer on 2010-07-20
Creo que lo importante es ésto: GeForce 7050 PV (de la serie GeForce 7). Puede ser que funcione sólo con algunas versiones del driver. No pude encontrar información para Ubuntu.

---

### Post by guillermolisi on 2010-07-20
Funciona lento porque esta usando driver Noveau en lugar de uno privativo de nVidia.

> 00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050  PV / nForce 630a] (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
	Expansion ROM at fdfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau

Habria que forzar que use driver generico VESA, poner en blacklist el driver Noveau y luego instalar el de nVidia que corresponda a ese modelo de placa.

Recuerdo que al principio del lanzamiento de la 10.04 hubo problemas con Noveau y hay documentada una solucion a partir de una configuracion en el Grub 2.

Habria que buscar en este foro y/o Google por nvidia - noveau - grub2.

---

### Post by kornykyano on 2010-07-21
Yo no soy un experto, pero creo cel chip Nvidia integrado no le “alcanza” para ese monitor, en general son para monitores de 17" y menos. Estoy casi seguro(99.99%), que si le agregas una nueva tarjeta, reconocera la resolución y no será lenta. Espero no equivocarme. :)

---

### Post by alfplayer on 2010-07-21
> **kornykyano said:**
> Yo no soy un experto, pero creo cel chip Nvidia integrado no le “alcanza” para ese monitor, en general son para monitores de 17" y menos. Estoy casi seguro(99.99%), que si le agregas una nueva tarjeta, reconocera la resolución y no será lenta. Espero no equivocarme. :)

Yo estoy casi seguro que te equivocás :)

---

