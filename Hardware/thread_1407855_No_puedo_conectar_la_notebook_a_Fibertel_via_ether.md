---
title: "No puedo conectar la notebook a Fibertel via ethernet"
date: 2010-02-15
forum: Hardware
---

### Post by sefsinalas on 2010-02-15
Buenas...tengo este problema que me ha vuelto loco toda la tarde y no pude solucionar espero que ustedes me puedan ayudar.
Tengo una notebook nueva...le instale kubuntu, cuando termine de instalar me pidio reiniciar. Lo hice y tenia kubuntu 9.10 instalado y tenia internet (fibertel via ethernet) y al hacer ifconfig -a me detectaba eth0. Luego instale todas las actualizaciones (30 minutos) y me pidio reiniciar de neuvo...lo hice y seguia con internet...ahora lo que hice fue apagarla y prenderla y ya no tenia internet. Este mismo proceso lo hice varias veces y siempre con el mismo resultado.

al hacer lspci -a me tira esto lo, wlan0, wmaster0
al hacer lspci solo por ningun lado veo nada que diga Ethernet
el comando iwconfig tambien me tira lo, wlan0, wmaster0 pero no eth0
y el archivo /etc/network/interfaces solo tiene lo siguiente:
[B]auto lo
iface lo inet loopback[/B]

Otra cosa curiosa es que cuando saco el cable de la notebook y lo conecto a la pc de escritorio que tiene la misma distro...internet sale funcionando.

---

### Post by guillermolisi on 2010-02-15
> **sefsinalas said:**
> Buenas...tengo este problema que me ha vuelto loco toda la tarde y no pude solucionar espero que ustedes me puedan ayudar.
Tengo una notebook nueva...le instale kubuntu, cuando termine de instalar me pidio reiniciar. Lo hice y tenia kubuntu 9.10 instalado y tenia internet (fibertel via ethernet) y al hacer ifconfig -a me detectaba eth0. Luego instale todas las actualizaciones (30 minutos) y me pidio reiniciar de neuvo...lo hice y seguia con internet...ahora lo que hice fue apagarla y prenderla y ya no tenia internet. Este mismo proceso lo hice varias veces y siempre con el mismo resultado.

al hacer lspci -a me tira esto lo, wlan0, wmaster0
al hacer lspci solo por ningun lado veo nada que diga Ethernet
el comando iwconfig tambien me tira lo, wlan0, wmaster0 pero no eth0
y el archivo /etc/network/interfaces solo tiene lo siguiente:
[B]auto lo
iface lo inet loopback[/B]

Otra cosa curiosa es que cuando saco el cable de la notebook y lo conecto a la pc de escritorio que tiene la misma distro...internet sale funcionando.
Si la interface de red la administra Network Manager no la vas a ver en /etc/network/interfaces.

Fibertel registra, en el servidor DHCP de ellos, la MAC address de la maquina con la que haces la conexion. Si cambias la maquina y no reseteas la conexion, nuunca te dejara acceder a Internet. Para lograr la navegacion, tenes que conectar la note al cablemodem, apagar el cablemodem por unos diez segundos y volverlo a encender. Ahi booteas la note y probas la conexion.

Fijate tambien en el Network Manager (icono en la System Tray, normalmente abajo a la derecha de la pantalla) si aparece etho en las conexiones de cable/ethernet.

Comenta como te fue.

---

### Post by sefsinalas on 2010-02-15
Gracias por responder Guillermo pero sigue sin funcionar. Entiendo lo que dices pero no creo que sea el problema porque no explica porque sin sacar el cable de la notebook se me muere el internet luego de la 2 reiniciada despues de la instalacion de Kubuntu.

Ademas supongo que los de fibertel pueden negarme el acceso a internet pero no creo que puedan hacer que desaparezca mi controlador de ethernet que al principio si me lo detectaba con ifconfig pero luego no :(

Es raro esto...quisiera mas ayuda y sugerencias por favor.

---

### Post by User21 on 2010-02-15
Si es una cuestión de que Fibertel ve tu MAC, podrías usar macchanger para que cada vez que te conectes uses una diferente, en tus PCs. Yo lo hacía para reiniciar mi conexión con Rapidshare y Megaupload, en FIBERTEL.
Create un script que ejecute macchanger y después reinicie la red.

sudo macchanger -r eth0 
sudo /etc/init.d/networking restart

siendo eth0 la interfase de red cableada. Al menos, yo lo hacía asi, no soy muy letrado en esto! n_n!

---

### Post by sefsinalas on 2010-02-15
Pero como le decia a Guillermo no es esa la cuestion, o al menos no la cuestion principal, porque directamente no me reconoce eth0 asi que ese comando solo dara error.
La cosa es que al principio al hacer lspci si me sale algo como Ethernet Controller pero luego de unas cuantas reiniciadas ya no sale nada. Como si se perdiera la placa o algo asi...nose :(

---

### Post by User21 on 2010-02-15
> **sefsinalas said:**
> 
Ademas supongo que los de fibertel pueden negarme el acceso a internet pero no creo que puedan hacer que desaparezca mi controlador de ethernet que al principio si me lo detectaba con ifconfig pero luego no :(


y dmesg tira algo sospechoso?..

---

### Post by sefsinalas on 2010-02-15
probe con dmesg | grep eth y dmesg | grep Ethernet pero nuevamente no tira nada...recien probe con Linux Mint 8 que es un derivado de Kubuntu 9.10 y es el mismo problema.

---

### Post by User21 on 2010-02-15
Especificanos marca y modelo de la laptop, vamos a ver si hay algún bug conocido! :)

---

### Post by sefsinalas on 2010-02-15
Es una COMMODORE KE 8322
yo busque info al respecto pero no encontre practicamente nada directamente relacionado con la notebook.

---

### Post by sefsinalas on 2010-02-15
esta es la salida del comando dmesg [http://pastebin.com/f8ea9073](http://pastebin.com/f8ea9073) espero que sirva para solucionar mi problema

---

### Post by User21 on 2010-02-15
Tenés DUAL BOOT en esa máquina? Window$ puede estar "administrando" la configuración de energía de esa placa, dejandola "OFF". n_n

---

### Post by sefsinalas on 2010-02-15
WHAT?! nono...no tengo mocosoft en mi pc. Pero igual la bateria no es porque esta al 100%

---

### Post by josecuervo86 on 2010-02-15
probaste con pppoeconf? a mi siempre me salva las papas

---

### Post by guillermolisi on 2010-02-16
> **josecuervo86 said:**
> probaste con pppoeconf? a mi siempre me salva las papas
Las conexiones de cablemodem no usan ese protocolo, son Ehternet lisa y llanas.

Se me ocurre que deberiamos ir al principio y esto es tener a la vista la salida de los comandos en consola/terminal de "lspci", "lsusb" (por las dudas) y "lshw" (sin las comillas) asi tendremos una vision concreta de que cosas de hardware ve, como las ve y que es lo que no ve. Ademas nos dara la informacion necesaria sobre el chip de la interfaces de red en cuestion.

Que dice la configuracion de redes de Network Manager ? Que adaptadores de red esta gestionando ?

---

### Post by sefsinalas on 2010-02-16
Bueno...aqui estan las 3 salidas que me dices:

lsusb:
Bus 002 Device 002: ID 0951:1625 Kingston Technology 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 002: ID 5986:0240 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:07.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)


lshw:
sefsinalas-laptop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2004MiB
     *-cpu
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:25 memory:f0000000-f00fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f0100000-f01fffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f0504800-f0504bff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f0300000-f0303fff
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0504c00-f0504fff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f4
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:2000(size=4096) memory:f0200000-f02fffff memory:80000000-83ffffff(prefetchable)
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:17 memory:f0200000-f0200fff ioport:2000(size=256) ioport:2400(size=256) memory:80000000-83ffffff(prefetchable) memory:88000000-8bffffff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:24 ioport:1c00(size=8) ioport:18d4(size=4) ioport:18d8(size=8) ioport:18d0(size=4) ioport:18e0(size=32) memory:f0504000-f05047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:84000000-840000ff ioport:1c20(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:25:d3:2a:7a:4c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


Como veras en ninguna aparece nada de Ethernet. Estoy un poco embolado porque no entiendo como puede no andar :x

---

### Post by guillermolisi on 2010-02-16
El BIOS de la notebook tiene opcion para habilitar/deshabilitar el adaptador de red (LAN)(no me refiero a bootear desde la LAN sino a encenderlo/apagarlo).

Por las salidas que mostraste no hay ningun adaptador Ethernet por cable electrica/fisicamente incorporado a la maquina, lo que realmente me parece muy raro considerando es una notebook.

---

### Post by sefsinalas on 2010-02-16
Claro...pero si aparece durante los primeros 2 booteos despues de instalar el S.O. 
ya busque en la BIOS pero no encontre nada. A mi tambien me parece rarisimo. Alguna otra idea? Porque de que si funciona como ya dije...pero despues de unas cuantas reiniciadas deja de andar.

---

### Post by guillermolisi on 2010-02-16
Sugiero que inicies la note con un LiveCD/pendrive con 9.10 y en ese modo (sin instalar nada de nada) te fijes que salidas te dan los comandos que corriste.

Si con la version basica de la 9.10 (sin actualizaciones) se ve la placa de red Ethernet, entonces podria ser una cuestion de software. Si el contenido de las salidas de esos comandos, particularmente "lspci" y "lshw" (ya que esta claro que la placa es PCI y no USB), no difiere de lo que obtuviste un par de post antes, entonces diria que el problema esta en el hardware, en la maquina precisamente.

---

### Post by sefsinalas on 2010-02-16
Me parece buena idea...

reinstale kubuntu y esto fue el resultado:

el comando lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
04:07.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)


el comando lshw:
sefsinalas-laptop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2004MiB
     *-cpu
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:27 memory:f0000000-f00fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f0100000-f01fffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f0604800-f0604bff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f0400000-f0403fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:2000(size=4096) memory:f0200000-f02fffff
           *-network
                description: Ethernet interface
                product: 88E8039 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 14
                serial: 00:14:0b:66:bc:6d
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
                resources: irq:28 memory:f0200000-f0203fff ioport:2000(size=256)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0604c00-f0604fff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f4
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:3000(size=4096) memory:f0300000-f03fffff memory:80000000-83ffffff(prefetchable)
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 7
                bus info: pci@0000:04:07.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:800000000-7ffffffff irq:17 memory:f0300000-f0300fff ioport:3000(size=256) ioport:3400(size=256) memory:80000000-83ffffff(prefetchable) memory:88000000-8bffffff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:1c00(size=8) ioport:18d4(size=4) ioport:18d8(size=8) ioport:18d0(size=4) ioport:18e0(size=32) memory:f0604000-f06047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:84000000-840000ff ioport:1c20(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:25:d3:2a:7a:4c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

como veran ahora si aparece en ambas salidas la palabra Ethernet...y tengo internet, ahora mismo escribo este post desde internet. Una vez que baje las actualizaciones y reinicie todavia funcionara...pero a la siguiente vez seguramente ya no tendre internet. Buscare mas info pero si alguien sabe algo aviseme por favor.

---

### Post by alfplayer on 2010-02-16
Si empieza a fallar de nuevo se podría probar apagando la fuente o desconectando la fuente, para intentar descubrir un problema con  la adminstración de energía.

---

### Post by sefsinalas on 2010-02-16
> **alfplayer said:**
> Si empieza a fallar de nuevo se podría probar apagando la fuente o desconectando la fuente, para intentar descubrir un problema con  la adminstración de energía.

No entiendo...ya lo probe con la bateria al 100%, con la bateria al 6%, conectada a 220 y desconectada tambien y siempre es el mismo resultado

---

### Post by alfplayer on 2010-02-16
> **sefsinalas said:**
> No entiendo...ya lo probe con la bateria al 100%, con la bateria al 6%, conectada a 220 y desconectada tambien y siempre es el mismo resultado

OK. Mi idea es quitarle la energía al motherboard. Para una portátil sería tener la batería y el cable de 220 V desconectados al mismo tiempo, volver a conectar, y después ver si aparece en la salida de lspci.

---

### Post by sefsinalas on 2010-02-16
No paso nada..no hubo cambios...sigue sin aparecer Ethernet :(

---

### Post by guillermolisi on 2010-02-16
Podria ser alguna opcion utilizada en la linea de boteo del Grub relacionada con ACPI o con PCI que hace que no pueda "leer" la placa de red Ehternet, cosa que en las versiones anteriores (basicamente Kernels anteriores a los que se instalan con las actualizaciones) no usaba.

Es decir, en alguna actualizacion posiblemente se haya modificado la line donde se carga el boot y se le pasan parametros al kernel, como por ejemplo acpi=off o cosas similares.

Para verificar esto habria que ver el contenido de /boot/grub/menu.lst (si estas con la version tradicional de Grub) o en los archivos del Grub nuevo (algo mas complejo y donde no puedo decir aun que archivo hay que revisar) tanto en la instalacion recien hecha (la que "ve" la placa de red, como en la instalacion actualizada para luego ver que cambios se produjeron.

---

### Post by sefsinalas on 2010-02-16
Seria una buena idea pero no me aparece ese archivo. Igual me fije en menu del boot cuando apenas inicia, cuando me da a elegir con que sistema operativo elegir y no hay nada como acpi=off ni nada parecido...todo parece normal.

---

### Post by alfplayer on 2010-02-16
Tiene que aparecer en dmesg (cuando funciona), pero no es necesario que aparezca usando "eth" o "Ethernet". Se puede probar con "88E" o "Marvell".

---

