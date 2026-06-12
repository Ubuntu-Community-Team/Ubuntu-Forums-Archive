---
title: "Se cuelga raro..."
date: 2008-10-27
forum: Hardware
---

### Post by erdosain9 on 2008-10-27
Hola a todos.  El tema es este:
luego de dejar la máquina sola por un tiempo (sin hacer nada) al volver  puedo mover el mouse pero no puedo entrar a nada... Por ejemplo en Aplicaciones no hay iconos, y si toco algo no arranca diciéndome que no hay nada en tal dirección (del disco rígido), tampoco están los iconos de mozilla o evolution... o el de apagar... que es el único que "funciona" (si pongo apagar sale el cartel pero con símbolos extraños... que igualmente no cumplen su función.

A eso le doy reiniciar con el botón del cpu y la máquina se me tilda en la bios... como esperando el disco rígido.  Para que vuelva a funcionar tengo que apagarla completamente y volver a encenderla.

Esto me hace pensar que es algo del tema de hibernación... pienso que el disco rígido se queda dormido... pero tal vez no, por eso pregunto.

Intenté sacar la hibernación por Bios pero no sé cómo... creo que no existe la opción... (da varias opciones pero ninguna es deshabilitar completamente)... y por software, saqué la "gestión de energía"... pero sigue sucediendo todo (aunque creo que sí sacó la hibernación porque ya no me tira esa opción cuando pongo apagar).

Bueno, espero ayuda... tal vez no sea lo que pienso (igualmente no sé como solucionarlo)

Gracias
   Erdosain9

---

### Post by pol666 on 2008-10-27
capas es un problema físico, del disco

---

### Post by sajnox on 2008-10-27
Que hardware tenes? Puede haber alguna incompatibilidad en el manejo de energia, cada tanto tenemos alguna pregunta de ese tipo por aca.

Sino sabes precisamente cual es tu hard postea la salida del comando 

```
lshw
```


Saludos

---

### Post by erdosain9 on 2008-10-27
Hola. Gracias por contestar.  Acá pego todo.  Por cierto, no es mi computadora entonces no estoy mucho... pero hoy estuve un ratito y veo que pasa lo mismo incluso mientras estas "haciendo cosas"; esta vez se fueron algunos iconos, el firefox se puso todo negro y si intentaba iniciar algún programa se generaba un error... reinicié por botón del cpu y se quedaba trabado pasando el bios pidiéndome un disco...  Al iniciar por el botón principal del cpu arrancaba ya sin problemas...

```
computadora               
    description: Computer
    width: 32 bits

  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 895MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          version: 15.11.2
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 6
             bus info: pci@0000:01:06.0
             logical name: eth1
             version: 10
             serial: 00:e0:7d:a8:bf:78
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.1 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW DRU-830A
             vendor: SONY
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: SS23
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:22:15:c8:d2:e2
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=190.19.106.68 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: GeForce 6100 nForce 430
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: vga_controller bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
```


¿qué podrá ser?!!!!!!!!!!!!!!!!!!!!!!

Parece ser algo del disco rígido... será, hay algo para hacer algún test... el disco rígido se supone que es nuevo como toda la máquina.  Bueno, no quiero generar un pista falsa así que tal vez no sea el disco.

Salutes
  Erdosain9

---

### Post by chalito on 2008-10-28
Me huele a una fuente defectuosa o insuficiente.

---

### Post by erdosain9 on 2008-10-28
uhhh! esto está peor ahora se tilda constantemente incluso mientras logeo el usuario... alguna otra idea...? hay formas de corroborar, test, algo???
salutes

---

### Post by sajnox on 2008-10-28
Con otros sistemas operativos hace lo mismo? En caso que lo haga el problema es del hard y no del soft.

abri una consola y ejecuta el comando top eso te va a tener abierto que procesos son los que estan corriendo y con que consumo de cpu.

Tambien podes tener el applet de temperatura para saber sino tenes un problema por ahi

---

### Post by erdosain9 on 2008-10-29
No sé si cuelga con otros porque esta máquina sólo tiene Ubuntu.... y ya puse el applet de temperatura y los valores son normales....  
voy a probar con el top... se supone que lo deje siempre abierto hasta que ocurra el cuelgue y veo qué consume más memoria???
Saludos

---

### Post by erdosain9 on 2008-11-03
Reviviendo mi post... ehhh, pues tal vez esto dé alguna pista.  Resulta que he notado que al tildarse como comento (que por cierto no es después de entrar en reposo ni nada... simplemente en CUALQUIER MOMENTO), quiero decir se queda sin algunos iconos, y no puedo iniciar programas.. si le doy al boton reiniciar del cpu la maquina se queda booteando y al entrar al bios veo que no figura el disco rígido, para que se vuelva a cargar tengo que darle al boton de apagado/encendido
pues he notado que la luz roja de la cpu se queda encendida por siempre... como si estuviera trabajando...
Bueno si eso da alguna pista... por cierto al poner top como me recomendaban no se ve nada extraño consumiendo memoria...
Saludos

---

### Post by vampichoke on 2008-11-03
yo siempre recomiendo (por q me parece q es puramente hardware tu problema. (desarmar toda la pc. limpiarla de paso =)y armarla fuera del gabinete.. (a lo eduhard.  ^^) y prenderla bootearla reiniciarla etc etc y si es fisico te das cuenta al toke. 

sino fijate de instalarle otra distro livianita. o correr el live cd un rato a ver si se reinicia asi de la nada como decis

---

### Post by erdosain9 on 2008-11-03
tal vez me expliqué mal... pero no se reinicia sola... soy yo el que "si le doy al boton reiniciar del cpu la maquina se queda booteando y al entrar al bios veo que no figura el disco rígido, para que se vuelva a cargar tengo que darle al boton de apagado/encendido"...
la máquina todavía está en garantía... puedo ir con el armatoste y decirle al tipo "miralo" y que el encuentre el problema que supongo tendrá más experiencia... o al tener un linux puede retovarse y decirme que es tema del S.O.  porque yo también creo que es cosa del hardware... tienen experiencia en esto con los tipos que arreglan??

---

### Post by mhoyos on 2008-11-03
> **erdosain9 said:**
> tal vez me expliqué mal... pero no se reinicia sola... soy yo el que "si le doy al boton reiniciar del cpu la maquina se queda booteando y al entrar al bios veo que no figura el disco rígido, para que se vuelva a cargar tengo que darle al boton de apagado/encendido"...


simple: 
tenes problemas con el controlador del disco rigido..!! cuando el BIOS no lo ve, o falla, o se "estupidiza" empieza a hacer cosas raras (cuelgues, frizados, etc)....


es nueva ?? llevala a la garantia..!! no lo dudes..

ah..!! que no te vayan con el verso de que el problema es linux..!! :)

salu2

---

### Post by erdosain9 on 2008-11-04
che... muchas gracias... sí! qué tanto romperme la cabeza... y preguntar... que se fijen ellos...
Saludos

---

