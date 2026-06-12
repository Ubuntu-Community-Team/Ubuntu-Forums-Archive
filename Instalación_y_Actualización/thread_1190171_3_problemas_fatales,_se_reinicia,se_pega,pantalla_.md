---
title: "3 problemas fatales, se reinicia,se pega,pantalla negra"
date: 2009-06-17
forum: Instalación y Actualización
---

### Post by mario2130 on 2009-06-17
POrfa ayuda estoy mas que arto, tengo tres problemas que no me han dejado disfrutar de mi nuevo notebook con ubuntu 9.04., como ven tengo tres problemas que me han mortificado mucho los cuales pasare a describir a continuación.

1) El notebook se pega y queda operando solo el mouse, no puedo acceder a ningun comando y tengo que apagar a la fuerza.

2)cuando cierro la tapa el noteook se pega pero con la pantalla negra(aca verifico el tipico Bloq Mayus, para ver si esta operando y prenden las luces del teclado), no tengo manera de volverlo a la vida, lo apago a la fuerza

3)estoy trabajando y se pega, la pantallla cambia a colores(se pone negra, luego muchos colores en forma de linea) y se reinicia la seccion, cerrando todo con lo cual trabajo.

ahora las caracteristicas de mi notebook

xps m1330
tarjeta de video: Mobile GM965/GL960 Integrated Graphics Controller

[html]
mario-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3520MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
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
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0 module=ssb
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5906M Fast Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:15:c5:7c:99:6d
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ricoh-mmc latency=64 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-cdrom
                description: DVD writer
                product: DVDRW  GSA-S10N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: A100
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:60:b3:af:61
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 32:f4:1b:94:93:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

[/html]algunos reporte del visor de sucesos cuando pasa loque pasa

[html]

Jun 17 03:46:45 mario-laptop gdm[3646]: pam_unix(gdm:session): session closed for user mario
Jun 17 03:46:47 mario-laptop gnome-keyring-daemon[4070]: dbus failure unregistering from session: Connection is closed
[/html]la configuracion del xorg
[html]
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
[/html]Help porfa no puedo trabajar tranquilo... estoy perdiendo informacion, y tiempo PORFA 
seguire investigando y comentando si alguien tiene el mismo problema a modo de guia. saludos

pd: Puede ser por que le instale 4G de ram? ubuntu tiene algun problema con eso? no e haberiguado eso

saludos

---

### Post by kamus on 2009-06-17
Para el problema de video (seguramente tiene que ver con tu problema #1), la verdad no me pasa y tengo una tarjeta de video integrada Intel : 00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02) que funciona bien con el controlador libre que viene por defecto.

Para lo del apagado, seguramente es un problema con la hibernacion, quizas deberias buscar por problemas de ACPI.

Descargaste las ultimas actualizaciones de sistema?
Instalaste la version final de ubuntu 9.04? actualizaste desde una version anterior o fue una instalacion limpia?

Saludos

---

### Post by mario2130 on 2009-06-17
> 
Para el problema de video (seguramente tiene que ver con tu problema #1), la verdad no me pasa y tengo una tarjeta de video integrada Intel : 00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02) que funciona bien con el controlador libre que viene por defecto.

para este caso deberia modificar el xorg como algunos lo plantean para el tipo de modelo de tarjeta grafica que tengo?, actualmente esta con efectos UXA

> **kamus said:**
> 
Para lo del apagado, seguramente es un problema con la hibernacion, quizas deberias buscar por problemas de ACPI.


Como puedo ver si tengo problemas de ACPI?

> 
Descargaste las ultimas actualizaciones de sistema?
Instalaste la version final de ubuntu 9.04? actualizaste desde una version anterior o fue una instalacion limpia?

Lo instale del CD que te manda para la casa Ubuntu.
particiones asi:
1:seven 30G
2:Respaldo 40G
3:Ubuntu 40G
4:Swap  2G

____________________________

Ahora poco se me pego y el visor de sucesos me tiro esto. estare aberiguando haber que onda

[HTML]
Clocksource tsc unstable (delta = -138356594 ns)
[/HTML]

---

### Post by AlvaroV on 2009-06-17
Por que no pruebas con ubuntu 8.04. Yo también trate de instalar 9.04 y comenzaron los cuelgues. Solución: volvía a 8.04 y todo resuelto. Por lo demás la 8.04 es una LTS por lo cual se va a estar actualizando hasta el 2011.

Si la versión te esta haciendo perder el tiempo ocupa una que te funcione bien.

Te aconsejo que si reinstalas separa la particón raiz  (/) de la Home, así si tienes que reinstalar no pierdes datos.

---

### Post by EnriqueK on 2009-06-17
[http://phyx.wordpress.com/2009/05/30/como-regresar-al-driver-2-4-de-intel-jauntyxorg/](http://phyx.wordpress.com/2009/05/30/como-regresar-al-driver-2-4-de-intel-jauntyxorg/)

---

### Post by CdK1 on 2009-06-17
Al parecer, como se ve en al configuración de Xorg, el driver no esta señalado, por lo demás es una configuración bastante pobre, si fuese tú, además que tengo la misma tarjeta, configuraría mi xorg.conf:

El segundo problema es cosa de hiberación, el último kernel -2.6.20- resuelve bastante esos problemas, además que existen unos parches que puedes encotrar en tus repositorios.

Lo de quedarse pegado es relativo, ya que debes especificar cuando, porque y como se queda pegado, ya sea si conectaste algún dispositivo, estás haciendo algo etc, los archivos de log de tu $HOME -.xsession-error-; dmesg y Xorg.0.log son de mucha ayuda ;)

---

### Post by mario2130 on 2009-06-17
Gracias por responder, bueno ahora estoy probando el en arranque **clocksource=hpet ** esto deberia de alguna forma parar con peges. por ahora probaré que sucede por estos dias. 

> 
Al parecer, como se ve en al configuración de Xorg, el driver no esta señalado, por lo demás es una configuración bastante pobre, si fuese tú, además que tengo la misma tarjeta, configuraría mi xorg.conf:
con respecto a la configuración del **xorg** intente modificarla pero al reiniciar para ver los resultado, el entorno gráfico se cayo y se restablecio sólo. por que no quise seguir modificando. Lo cambios que efectue son estos:

Section “Device”
Identifier “Configured Video Device”
Option “AccelMethod” “uxa”
Option “EXAOptimizeMigration” “true”
Option “MigrationHeuristic” “greedy”
Option “Tiling” “true” 
EndSection

> 
El segundo problema es cosa de hiberación, el último kernel -2.6.20- resuelve bastante esos problemas, además que existen unos parches que puedes encotrar en tus repositorios.
> 
Por que no pruebas con ubuntu 8.04. Yo también trate de instalar 9.04 y comenzaron los cuelgues. Solución: volvía a 8.04 y todo resuelto. Por lo demás la 8.04 es una LTS por lo cual se va a estar actualizando hasta el 2011.

Si la versión te esta haciendo perder el tiempo ocupa una que te funcione bien.
bueno probaré con ese cambio del clock, si no me funka creo que cambie a otra versión más estable como la 8.04.


> 
Te aconsejo que si reinstalas separa la particón raiz  (/) de la Home, así si tienes que reinstalar no pierdes datos.     
No en ese sentido no me preocupo por que los documentos importante, los voy guardando en el disco "Respaldo". en / tengo los programas intalados y cosas que se pueden volver a descargar.



Gracias por la ayuda muchachos, comentaré como voy para ver si a mejorado la cosa


pd: aca da gusto postear.

---

### Post by moreback on 2009-06-18
Tengo la impresión que no te está funcionando bien con UXA, así que mejor edita tu¿ xorg.conf y cambia "UXA" por "EXA".

PD. el cuelgue n°1 tb me ha pasado, pero ya estoy con EXA que es más estable (debería)

---

### Post by mario2130 on 2009-06-18
> **CdK1 said:**
> Al parecer, como se ve en al configuración de Xorg, el driver no esta señalado, por lo demás es una configuración bastante pobre, si fuese tú, además que tengo la misma tarjeta, configuraría mi xorg.conf:

El segundo problema es cosa de hiberación, el último kernel -2.6.20- resuelve bastante esos problemas, además que existen unos parches que puedes encotrar en tus repositorios.

Lo de quedarse pegado es relativo, ya que debes especificar cuando, porque y como se queda pegado, ya sea si conectaste algún dispositivo, estás haciendo algo etc, los archivos de log de tu $HOME -.xsession-error-; dmesg y Xorg.0.log son de mucha ayuda ;)

Cdk1, viejo me podrias mostrar tu xorg como lo tienes configurado, porfa

e tratado de rescatar info del dmesg y Xorg.0 pero no e entendido mucho, puesto que ahi mucha información


**e tenido mas cuelges asi que lo del clock descartado :(**

ahora vere el asunto del Xorg, modificado con UXa y EXA como sugiere moreback. estare reportando.. saludos

---

### Post by mario2130 on 2009-06-18
Me reporto, llevo como 3 horas sin caida(cuelge total del sistema) luego de configurar el xorg, aer si dura por hoy al tuto
gracias

---

### Post by CdK1 on 2009-06-18
Lo bueno que no has tenido problema, yo use uno similar a este:

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "latam"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "Device"
    Identifier    "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Driver        "intel"
    Option        "DRI" "true"
    BusID        "PCI:0:2:0"
    Option        "AllowGLXWithComposite" "true"
    Option        "RenderAccel" "true"
    Option        "XAANoOffscreenPixmaps" "True"
    Option        "UseFBDev" "true"
    Option        "AccelMethod" "XAA"
EndSection

Section "Monitor"
    Identifier    "Monitor genérico"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Monitor        "Monitor genérico"
    DefaultDepth    24
#    Option        "AddARGBGLXVisuals" "True"
    SubSection "Display"
        Modes        "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection

Section "DRI"
    Group 0
    Mode 0666
EndSection

---

### Post by mario2130 on 2009-06-18
bueno lo deje prendido no paso nada, solo que cuando configure la pantalla para que el protector de pantalla apareciera(para dejar descargando) pasaron como 2 minutos y paso el problema numero dos (pantalla se fue a negro, se pego equipo reinicio con force) asi que algo tiene con eso, reinicie y guarde el redorte Xseccion.error
[HTML]

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=es_CL.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-xypzNa/socket
SSH_AUTH_SOCK=/tmp/keyring-xypzNa/socket.ssh

(gnome-settings-daemon:4280): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:4280): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1drm_i915_getparam: -22
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: drm_i915_getparam: -22
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
drm_i915_getparam: -22
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I/O warning : failed to load external entity "/home/mario/.compiz/session/109bddc9b3abb9d8e124531413012217900000041800023"
** (gnome-panel:4343): DEBUG: Adding applet 0.
** (gnome-panel:4343): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:4343): DEBUG: Adding applet 1.
** (gnome-panel:4343): DEBUG: Adding applet 2.
** (nm-applet:4371): DEBUG: applet_common_device_state_changed
** (nm-applet:4371): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:4371): DEBUG: applet_common_device_state_changed
** (nm-applet:4371): DEBUG: applet_common_device_state_changed
** (nm-applet:4371): DEBUG: applet_common_device_state_changed
** (nm-applet:4371): DEBUG: foo_client_state_changed_cb
** (gnome-panel:4343): DEBUG: Adding applet 3.
** (gnome-panel:4343): DEBUG: Adding applet 4.
** (gnome-panel:4343): DEBUG: Adding applet 5.
** (gnome-panel:4343): DEBUG: Adding applet 6.
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
** (gnome-panel:4343): DEBUG: Adding applet 7.
** (gnome-panel:4343): DEBUG: Adding applet 8.
** (gnome-panel:4343): DEBUG: Adding applet 9.
** (gnome-panel:4343): DEBUG: Adding applet 10.
** (gnome-panel:4343): DEBUG: Adding applet 11.
** (gnome-panel:4343): DEBUG: Adding applet 12.
** (gnome-panel:4343): DEBUG: Adding applet 13.
** (nm-applet:4371): DEBUG: applet_common_device_state_changed
** (gnome-panel:4343): DEBUG: Adding applet 14.
** (gnome-panel:4343): DEBUG: Adding applet 15.
** (gnome-panel:4343): DEBUG: Adding applet 16.
Starting gtk-window-decorator
** (gnome-panel:4343): DEBUG: Adding applet 17.
** (gnome-panel:4343): DEBUG: Adding applet 18.

** (nautilus:4347): WARNING **: Unable to add monitor: No soportado

(gnome-panel:4343): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (nm-applet:4371): DEBUG: applet_common_device_state_changed
** (gnome-panel:4343): DEBUG: Adding applet 19.
Nautilus-Share-Message: Called "net usershare info" but it failed: La «red compartida» devolvió el error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No existe el fichero ó directorio
Please ask your system administrator to enable user sharing.

** (nm-applet:4371): DEBUG: foo_client_state_changed_cb

(gnome-panel:4343): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24
** (gnome-panel:4343): DEBUG: Adding applet 20.
** (gnome-panel:4343): DEBUG: Adding applet 21.
** (gnome-panel:4343): DEBUG: Adding applet 22.
evolution-alarm-notify-Message: Setting timeout for 55434 1245369600 1245314166
evolution-alarm-notify-Message:  Thu Jun 18 20:00:00 2009

evolution-alarm-notify-Message:  Thu Jun 18 04:36:06 2009

** (update-notifier:4368): DEBUG: /usr/lib/update-notifier/apt-check returned 11 (security: 0)
** (update-notifier:4368): DEBUG: crashreport_check

[/HTML]


saludos, seguiremos problando hasta ahora no pegaciones del tipo 1

---

### Post by CdK1 on 2009-06-18
2)cuando cierro la tapa el noteook se pega pero con la pantalla negra(aca verifico el tipico Bloq Mayus, para ver si esta operando y prenden las luces del teclado), no tengo manera de volverlo a la vida, lo apago a la fuerza

Significa que tienes problemas con la hibernación verdad?

[http://blog.netmasters.cl/solucion-a-hibernar-y-suspender-ubuntu/](http://blog.netmasters.cl/solucion-a-hibernar-y-suspender-ubuntu/)
[http://ubuntuforums.org/showthread.php?t=327868](http://ubuntuforums.org/showthread.php?t=327868)

---

### Post by mario2130 on 2009-06-18
> **CdK1 said:**
> 2)cuando cierro la tapa el noteook se pega pero con la pantalla negra(aca verifico el tipico Bloq Mayus, para ver si esta operando y prenden las luces del teclado), no tengo manera de volverlo a la vida, lo apago a la fuerza

Significa que tienes problemas con la hibernación verdad?

[http://blog.netmasters.cl/solucion-a-hibernar-y-suspender-ubuntu/](http://blog.netmasters.cl/solucion-a-hibernar-y-suspender-ubuntu/)
[http://ubuntuforums.org/showthread.php?t=327868](http://ubuntuforums.org/showthread.php?t=327868)

Es que por lo que leo, eso deberia ser, pero lo tengo configurado para que no se hiberne o suspenda.

Este proceso pasa solo cuando pongo el modo de "salva pantalla" (y al cabo de un rato se pega) o cuando bajo la tapa del notebook y reitero lo tengo configurado que cuando se baje la tapa, no haga nada(para descartar que es la hibernación)

ahora con el link que me mandaste lo lei tambien en otro foro, pero ese NvAgp es para tarjetas Nvidia o Ati, y estado viendo si puede ser faltible para el resto de las tarjetas.. bueno si de aca a un rato mas no encuentro nada lo probare haber que onda.

[B]con respecto a los pegadas sin que la patalla se ponga negra (caso 1 y 3) hasta ahora no a pasado nada, ojala siga asi.. saludos

[/B]se me olvido mensionar que si, tengo hibernacion tengo que tener la misma o mas cantidad de swap que la memoria fisica que poseo.

pregunta: ¿si quiero pasar la swap de 2 a 4 tengo que necesariamente formatear?

---

### Post by CdK1 on 2009-06-18
No, puedes crearla mediante un live CD o un swap file:

[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

---

### Post by mario2130 on 2009-06-18
No ahi caso, el problema de los pegado creo que por ahora se an solucionado, el problema persiste que  cuando baje la tapa del notebook, este se pega.

mmmm no se que hacer ahora se me acabaron las alternativas
creo que tendre que evaluar la opción de cambiar a 8.04 o 8.10.. 

¿que recomiendan?

---

### Post by CdK1 on 2009-06-18
Actualizar siempre es bueno, pero que dice el comando dmesg luego que reinicias?

---

### Post by mario2130 on 2009-06-19
> **CdK1 said:**
> Actualizar siempre es bueno, pero que dice el comando dmesg luego que reinicias?

[HTML]
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000df692400 (usable)
[    0.000000]  BIOS-e820: 00000000df692400 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xdf692 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000df692400 (usable)
[    0.000000]  modified: 00000000df692400 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378c0000 - 37fef779
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb0779
[    0.000000] Move RAMDISK from 00000000378c0000 - 0000000037fef778 to 00881000 - 00fb0778
[    0.000000] ACPI: RSDP 000FBBF0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT DF693E00, 005C (r1 DELL    M08     27D70903 ASL        61)
[    0.000000] ACPI: FACP DF693C9C, 00F4 (r4 DELL    M08     27D70903 ASL        61)
[    0.000000] ACPI: DSDT DF694400, 5739 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS DF6A2C00, 0040
[    0.000000] ACPI: HPET DF693F00, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC DF694000, 0068 (r1 DELL    M08     27D70903 ASL        47)
[    0.000000] ACPI: MCFG DF693FC0, 003E (r16 DELL    M08     27D70903 ASL        61)
[    0.000000] ACPI: SLIC DF69409C, 0176 (r1 DELL    M08     27D70903 ASL        61)
[    0.000000] ACPI: BOOT DF693BC0, 0028 (r1 DELL    M08     27D70903 ASL        61)
[    0.000000] ACPI: SSDT DF692682, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2690MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb0779]      NEW RAMDISK ==> [0000881000 - 0000fb0779]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000df692
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x000df692
[    0.000000] On node 0 totalpages: 914967
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 5382 pages used for memmap
[    0.000000]   HighMem zone: 683406 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e2000000 (gap: e0000000:18000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 907817
[    0.000000] Kernel command line: root=UUID=eca79b8e-aba1-45b3-868c-3dcd70d4d927 ro quiet splash notsc clocksource=hpet 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] allocated 18301800 bytes of page_cgroup
[    0.000000] please try cgroup_disable=memory option if you don't want
[    0.000000] Scanning for low memory corruption every 60 seconds
[    0.000000] Memory: 3596436k/3660360k available (4126k kernel code, 62508k reserved, 2208k data, 532k init, 2755152k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.000000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.000000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.000000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.000000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Calibrating delay loop... 2981.88 BogoMIPS (lpj=5963776)
[    0.096000] Security Framework initialized
[    0.096000] SELinux:  Disabled at boot.
[    0.096000] AppArmor: AppArmor initialized
[    0.096000] Mount-cache hash table entries: 512
[    0.096000] Initializing cgroup subsys ns
[    0.096000] Initializing cgroup subsys cpuacct
[    0.096000] Initializing cgroup subsys memory
[    0.096000] Initializing cgroup subsys freezer
[    0.096000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.096000] CPU: L2 cache: 2048K
[    0.096000] CPU: Physical Processor ID: 0
[    0.096000] CPU: Processor Core ID: 0
[    0.096000] using mwait in idle threads.
[    0.096000] Checking 'hlt' instruction... OK.
[    0.112000] ACPI: Core revision 20080926
[    0.116000] ACPI: Checking initramfs for custom DSDT
[    0.508001] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.548001] CPU0: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz stepping 0d
[    0.548001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay loop... 2990.08 BogoMIPS (lpj=5980160)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.652002] CPU1: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz stepping 0d
[    0.652002] Brought up 2 CPUs
[    0.652002] Total of 2 processors activated (5971.96 BogoMIPS).
[    0.652002] CPU0 attaching sched-domain:
[    0.652002]  domain 0: span 0-1 level MC
[    0.652002]   groups: 0 1
[    0.652002] CPU1 attaching sched-domain:
[    0.652002]  domain 0: span 0-1 level MC
[    0.652002]   groups: 1 0
[    0.652002] net_namespace: 776 bytes
[    0.652002] Booting paravirtualized kernel on bare hardware
[    0.652002] Time:  5:17:51  Date: 06/19/09
[    0.652002] regulator: core version 0.5
[    0.652002] NET: Registered protocol family 16
[    0.652002] EISA bus registered
[    0.652002] ACPI: bus type pci registered
[    0.652002] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.652002] PCI: MCFG area at f8000000 reserved in E820
[    0.652002] PCI: Using MMCONFIG for extended config space
[    0.652002] PCI: Using configuration type 1 for base access
[    0.656002] ACPI: EC: Look up EC in DSDT
[    0.668002] ACPI: SSDT DF6A2C80, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[    0.688002] ACPI: Interpreter enabled
[    0.688002] ACPI: (supports S0 S3 S4 S5)
[    0.692002] ACPI: Using IOAPIC for interrupt routing
[    0.744002] ACPI: No dock devices found.
[    0.744002] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.744002] pci 0000:00:02.0: reg 10 64bit mmio: [0xfea00000-0xfeafffff]
[    0.744002] pci 0000:00:02.0: reg 18 64bit mmio: [0xe0000000-0xefffffff]
[    0.744002] pci 0000:00:02.0: reg 20 io port: [0xefe8-0xefef]
[    0.744002] pci 0000:00:02.1: reg 10 64bit mmio: [0xfeb00000-0xfebfffff]
[    0.744002] pci 0000:00:1a.0: reg 20 io port: [0x6f20-0x6f3f]
[    0.744002] pci 0000:00:1a.1: reg 20 io port: [0x6f00-0x6f1f]
[    0.744002] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
[    0.744002] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.744002] pci 0000:00:1a.7: PME# disabled
[    0.744002] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe9fc000-0xfe9fffff]
[    0.744002] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.744002] pci 0000:00:1b.0: PME# disabled
[    0.744002] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.744002] pci 0000:00:1c.0: PME# disabled
[    0.744002] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.744002] pci 0000:00:1c.1: PME# disabled
[    0.744002] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.744002] pci 0000:00:1c.3: PME# disabled
[    0.744002] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.744002] pci 0000:00:1c.5: PME# disabled
[    0.744002] pci 0000:00:1d.0: reg 20 io port: [0x6f80-0x6f9f]
[    0.744002] pci 0000:00:1d.1: reg 20 io port: [0x6f60-0x6f7f]
[    0.744002] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
[    0.744002] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
[    0.744002] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.744002] pci 0000:00:1d.7: PME# disabled
[    0.744002] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.744002] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.744002] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.744002] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.744002] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.744002] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.744002] pci 0000:00:1f.1: reg 20 io port: [0x6fa0-0x6faf]
[    0.744002] pci 0000:00:1f.2: reg 10 io port: [0x6eb0-0x6eb7]
[    0.744002] pci 0000:00:1f.2: reg 14 io port: [0x6eb8-0x6ebb]
[    0.744002] pci 0000:00:1f.2: reg 18 io port: [0x6ec0-0x6ec7]
[    0.744002] pci 0000:00:1f.2: reg 1c io port: [0x6ec8-0x6ecb]
[    0.744002] pci 0000:00:1f.2: reg 20 io port: [0x6ee0-0x6eef]
[    0.744002] pci 0000:00:1f.2: reg 24 io port: [0xeff0-0xefff]
[    0.744002] pci 0000:00:1f.2: PME# supported from D3hot
[    0.744002] pci 0000:00:1f.2: PME# disabled
[    0.744002] pci 0000:00:1f.3: reg 10 32bit mmio: [0xfe9fbf00-0xfe9fbfff]
[    0.744002] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.744002] pci 0000:0c:00.0: reg 10 32bit mmio: [0xfe8fc000-0xfe8fffff]
[    0.744002] pci 0000:0c:00.0: supports D1 D2
[    0.744002] pci 0000:00:1c.1: bridge 32bit mmio: [0xfe800000-0xfe8fffff]
[    0.744002] pci 0000:00:1c.3: bridge io port: [0xd000-0xdfff]
[    0.744002] pci 0000:00:1c.3: bridge 32bit mmio: [0xfe600000-0xfe7fffff]
[    0.744002] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf0000000-0xf01fffff]
[    0.744002] pci 0000:09:00.0: reg 10 64bit mmio: [0xfe5f0000-0xfe5fffff]
[    0.744002] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.744002] pci 0000:09:00.0: PME# disabled
[    0.744002] pci 0000:00:1c.5: bridge 32bit mmio: [0xfe500000-0xfe5fffff]
[    0.744002] pci 0000:03:01.0: reg 10 32bit mmio: [0xfe4ff800-0xfe4fffff]
[    0.744002] pci 0000:03:01.0: supports D1 D2
[    0.744002] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.744002] pci 0000:03:01.0: PME# disabled
[    0.744002] pci 0000:03:01.1: reg 10 32bit mmio: [0xfe4ff400-0xfe4ff4ff]
[    0.748002] pci 0000:03:01.1: supports D1 D2
[    0.748002] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.748002] pci 0000:03:01.1: PME# disabled
[    0.748002] pci 0000:03:01.2: reg 10 32bit mmio: [0xfe4ff500-0xfe4ff5ff]
[    0.748002] pci 0000:03:01.2: supports D1 D2
[    0.748002] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.748002] pci 0000:03:01.2: PME# disabled
[    0.748002] pci 0000:03:01.3: reg 10 32bit mmio: [0xfe4ff600-0xfe4ff6ff]
[    0.748002] pci 0000:03:01.3: supports D1 D2
[    0.748002] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.748002] pci 0000:03:01.3: PME# disabled
[    0.748002] pci 0000:03:01.4: reg 10 32bit mmio: [0xfe4ff700-0xfe4ff7ff]
[    0.748002] pci 0000:03:01.4: supports D1 D2
[    0.748002] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.748002] pci 0000:03:01.4: PME# disabled
[    0.748002] pci 0000:00:1e.0: transparent bridge
[    0.748002] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe400000-0xfe4fffff]
[    0.748002] bus 00 -> node 0
[    0.748002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.748002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.748002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.748002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.748002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.748002] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.764002] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.764002] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.764002] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.764002] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.764002] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.764002] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.764002] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.764002] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.764002] ACPI: WMI: Mapper loaded
[    0.764002] SCSI subsystem initialized
[    0.768002] libata version 3.00 loaded.
[    0.768002] usbcore: registered new interface driver usbfs
[    0.768002] usbcore: registered new interface driver hub
[    0.768002] usbcore: registered new device driver usb
[    0.768002] PCI: Using ACPI for IRQ routing
[    0.772002] Bluetooth: Core ver 2.13
[    0.772002] NET: Registered protocol family 31
[    0.772002] Bluetooth: HCI device and connection manager initialized
[    0.772002] Bluetooth: HCI socket layer initialized
[    0.772002] NET: Registered protocol family 8
[    0.772002] NET: Registered protocol family 20
[    0.772002] NetLabel: Initializing
[    0.772002] NetLabel:  domain hash size = 128
[    0.772002] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.772002] NetLabel:  unlabeled traffic allowed by default
[    0.772002] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.772002] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.776002] AppArmor: AppArmor Filesystem Enabled
[    0.780004] Switched to high resolution mode on CPU 0
[    0.780621] Switched to high resolution mode on CPU 1
[    0.788002] pnp: PnP ACPI init
[    0.788002] ACPI: bus type pnp registered
[    0.804007] pnp 00:09: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.804007] pnp 00:09: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.804007] pnp 00:0a: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.804007] pnp 00:0a: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.804007] pnp 00:0a: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.804007] pnp 00:0a: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.836006] pnp: PnP ACPI: found 12 devices
[    0.836006] ACPI: ACPI bus type pnp unregistered
[    0.836006] PnPBIOS: Disabled by ACPI PNP
[    0.836006] system 00:05: ioport range 0xc80-0xcff could not be reserved
[    0.836006] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.836006] system 00:09: ioport range 0x900-0x97f has been reserved
[    0.836006] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.836006] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[    0.836006] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[    0.836006] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[    0.836006] system 00:0a: ioport range 0x809-0x809 has been reserved
[    0.836006] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[    0.836006] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[    0.836006] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.836006] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.836006] system 00:0b: iomem range 0x100000-0xdf6923ff could not be reserved
[    0.836006] system 00:0b: iomem range 0xdf692400-0xdf6fffff has been reserved
[    0.836006] system 00:0b: iomem range 0xdf700000-0xdf7fffff has been reserved
[    0.836006] system 00:0b: iomem range 0xdf700000-0xdfefffff could not be reserved
[    0.836006] system 00:0b: iomem range 0xffe00000-0xffffffff has been reserved
[    0.836006] system 00:0b: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.836006] system 00:0b: iomem range 0xfec00000-0xfec0ffff has been reserved
[    0.836006] system 00:0b: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.836006] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.836006] system 00:0b: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.836006] system 00:0b: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.836006] system 00:0b: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.836006] system 00:0b: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.836006] system 00:0b: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.836006] system 00:0b: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.868005] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.868005] pci 0000:00:1c.0:   IO window: disabled
[    0.868005] pci 0000:00:1c.0:   MEM window: disabled
[    0.868005] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.868005] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.868005] pci 0000:00:1c.1:   IO window: disabled
[    0.868005] pci 0000:00:1c.1:   MEM window: 0xfe800000-0xfe8fffff
[    0.868005] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.868005] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.868005] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.868005] pci 0000:00:1c.3:   MEM window: 0xfe600000-0xfe7fffff
[    0.868005] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.868005] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.868005] pci 0000:00:1c.5:   IO window: disabled
[    0.868005] pci 0000:00:1c.5:   MEM window: 0xfe500000-0xfe5fffff
[    0.868005] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.868005] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.868005] pci 0000:00:1e.0:   IO window: disabled
[    0.868005] pci 0000:00:1e.0:   MEM window: 0xfe400000-0xfe4fffff
[    0.868005] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.868005] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.868005] pci 0000:00:1c.0: setting latency timer to 64
[    0.868005] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.868005] pci 0000:00:1c.1: setting latency timer to 64
[    0.872005] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.872005] pci 0000:00:1c.3: setting latency timer to 64
[    0.872005] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.872005] pci 0000:00:1c.5: setting latency timer to 64
[    0.872005] pci 0000:00:1e.0: setting latency timer to 64
[    0.872005] bus: 00 index 0 io port: [0x00-0xffff]
[    0.872005] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.872005] bus: 0b index 0 mmio: [0x0-0x0]
[    0.872005] bus: 0b index 1 mmio: [0x0-0x0]
[    0.872005] bus: 0b index 2 mmio: [0x0-0x0]
[    0.872005] bus: 0b index 3 mmio: [0x0-0x0]
[    0.872005] bus: 0c index 0 mmio: [0x0-0x0]
[    0.872005] bus: 0c index 1 mmio: [0xfe800000-0xfe8fffff]
[    0.872005] bus: 0c index 2 mmio: [0x0-0x0]
[    0.872005] bus: 0c index 3 mmio: [0x0-0x0]
[    0.872005] bus: 0d index 0 io port: [0xd000-0xdfff]
[    0.872005] bus: 0d index 1 mmio: [0xfe600000-0xfe7fffff]
[    0.872005] bus: 0d index 2 mmio: [0xf0000000-0xf01fffff]
[    0.872005] bus: 0d index 3 mmio: [0x0-0x0]
[    0.872005] bus: 09 index 0 mmio: [0x0-0x0]
[    0.872005] bus: 09 index 1 mmio: [0xfe500000-0xfe5fffff]
[    0.872005] bus: 09 index 2 mmio: [0x0-0x0]
[    0.872005] bus: 09 index 3 mmio: [0x0-0x0]
[    0.872005] bus: 03 index 0 mmio: [0x0-0x0]
[    0.872005] bus: 03 index 1 mmio: [0xfe400000-0xfe4fffff]
[    0.872005] bus: 03 index 2 mmio: [0x0-0x0]
[    0.872005] bus: 03 index 3 io port: [0x00-0xffff]
[    0.872005] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.872005] NET: Registered protocol family 2
[    0.888002] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.888002] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.888002] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.888002] TCP: Hash tables configured (established 131072 bind 65536)
[    0.888002] TCP reno registered
[    0.892003] NET: Registered protocol family 1
[    0.892003] checking if image is initramfs... it is
[    1.684020] Freeing initrd memory: 7357k freed
[    1.684020] Simple Boot Flag at 0x79 set to 0x1
[    1.687310] cpufreq: No nForce2 chipset.
[    1.687310] audit: initializing netlink socket (disabled)
[    1.687310] type=2000 audit(1245388671.684:1): initialized
[    1.700002] highmem bounce pool size: 64 pages
[    1.700002] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.700002] VFS: Disk quotas dquot_6.5.1
[    1.700002] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.700002] fuse init (API version 7.10)
[    1.700002] msgmni has been set to 1659
[    1.700002] alg: No test for stdrng (krng)
[    1.700002] io scheduler noop registered
[    1.700002] io scheduler anticipatory registered
[    1.700002] io scheduler deadline registered
[    1.700002] io scheduler cfq registered (default)
[    1.700002] pci 0000:00:02.0: Boot video device
[    1.703854] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.703854] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.703854] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.703854] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.703854] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.703854] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.703854] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.703854] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.703854] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    1.703854] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.703854] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.703854] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.703854] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.703854] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.703854] pcieport-driver 0000:00:1c.3: irq 2301 for MSI/MSI-X
[    1.703854] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.703854] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.703854] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.703854] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.703854] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.703854] pcieport-driver 0000:00:1c.5: irq 2300 for MSI/MSI-X
[    1.703854] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.703854] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.703854] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.703854] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.703854] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.703854] ACPI: AC Adapter [AC] (on-line)
[    1.740002] ACPI: Battery Slot [BAT0] (battery present)
[    1.740002] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.744250] ACPI: Lid Switch [LID]
[    1.744250] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.744250] ACPI: Power Button (CM) [PBTN]
[    1.744250] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.744250] ACPI: Sleep Button (CM) [SBTN]
[    1.744250] ACPI: SSDT DF6931B8, 01C0 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.744250] ACPI: SSDT DF692B4E, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.744250] Monitor-Mwait will be used to enter C-1 state
[    1.744250] Monitor-Mwait will be used to enter C-2 state
[    1.744250] Monitor-Mwait will be used to enter C-3 state
[    1.744250] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.744250] processor ACPI_CPU:00: registered as cooling_device0
[    1.744250] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.744250] ACPI: SSDT DF693378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.744250] ACPI: SSDT DF693133, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.744250] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.744250] processor ACPI_CPU:01: registered as cooling_device1
[    1.744250] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.749162] thermal LNXTHERM:01: registered as thermal_zone0
[    1.753115] ACPI: Thermal Zone [THM] (55 C)
[    1.753115] isapnp: Scanning for PnP cards...
[    2.109004] isapnp: No Plug & Play device found
[    2.117007] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.117007] brd: module loaded
[    2.117007] loop: module loaded
[    2.117007] Fixed MDIO Bus: probed
[    2.117007] PPP generic driver version 2.4.2
[    2.117007] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.117007] Driver 'sd' needs updating - please use bus_type methods
[    2.117007] Driver 'sr' needs updating - please use bus_type methods
[    2.117007] ata_piix 0000:00:1f.1: version 2.12
[    2.117007] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.117007] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.120002] scsi0 : ata_piix
[    2.120002] scsi1 : ata_piix
[    2.123469] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    2.123469] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    2.288002] ata1.00: ATAPI: HL-DT-ST DVDRW  GSA-S10N, A100, max UDMA/33
[    2.304002] ata1.00: configured for UDMA/33
[    2.304002] ata2: port disabled. ignoring.
[    2.308494] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRW  GSA-S10N  A100 PQ: 0 ANSI: 5
[    2.316868] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    2.316868] Uniform CD-ROM driver Revision: 3.20
[    2.316868] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.316868] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.316868] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.316868] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.471992] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.471992] scsi2 : ata_piix
[    2.471992] scsi3 : ata_piix
[    2.471992] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    2.471992] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    3.268004] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.268004] ata3.01: SATA link down (SStatus 0 SControl 300)
[    3.335801] ata3.00: ATA-8: WDC WD1200BEVS-75UST0, 01.01A01, max UDMA/133
[    3.335801] ata3.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    3.344494] ata3.00: configured for UDMA/133
[    3.988002] ata4.00: SATA link down (SStatus 0 SControl 300)
[    3.988002] ata4.01: SATA link down (SStatus 0 SControl 0)
[    3.988002] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-7 01.0 PQ: 0 ANSI: 5
[    3.988002] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.988002] sd 2:0:0:0: [sda] Write Protect is off
[    3.988002] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.988002] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.988002] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.988002] sd 2:0:0:0: [sda] Write Protect is off
[    3.988002] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.988002] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.988002]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    4.064806] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.064806] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    4.064806] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.064806] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    4.064806] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.064806] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.064806] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.065007] ehci_hcd 0000:00:1a.7: debug port 1
[    4.065007] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.065007] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    4.084002] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.084002] usb usb1: configuration #1 chosen from 1 choice
[    4.084002] hub 1-0:1.0: USB hub found
[    4.084002] hub 1-0:1.0: 4 ports detected
[    4.084002] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.084002] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.084002] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.084002] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.084002] ehci_hcd 0000:00:1d.7: debug port 1
[    4.084002] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.084002] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    4.100002] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.100002] usb usb2: configuration #1 chosen from 1 choice
[    4.100002] hub 2-0:1.0: USB hub found
[    4.100002] hub 2-0:1.0: 6 ports detected
[    4.100002] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.100002] uhci_hcd: USB Universal Host Controller Interface driver
[    4.100002] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.100002] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.100002] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.100002] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.100002] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    4.100002] usb usb3: configuration #1 chosen from 1 choice
[    4.100002] hub 3-0:1.0: USB hub found
[    4.100002] hub 3-0:1.0: 2 ports detected
[    4.100002] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.100002] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.100002] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.100002] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.100002] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    4.100002] usb usb4: configuration #1 chosen from 1 choice
[    4.100002] hub 4-0:1.0: USB hub found
[    4.100002] hub 4-0:1.0: 2 ports detected
[    4.100002] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.100002] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.100002] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.100002] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    4.100002] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    4.100002] usb usb5: configuration #1 chosen from 1 choice
[    4.100002] hub 5-0:1.0: USB hub found
[    4.100002] hub 5-0:1.0: 2 ports detected
[    4.100002] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.100002] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.100002] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.100002] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.100002] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    4.100002] usb usb6: configuration #1 chosen from 1 choice
[    4.100002] hub 6-0:1.0: USB hub found
[    4.100002] hub 6-0:1.0: 2 ports detected
[    4.100002] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    4.100002] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.100002] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.100002] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.100002] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    4.100002] usb usb7: configuration #1 chosen from 1 choice
[    4.100002] hub 7-0:1.0: USB hub found
[    4.100002] hub 7-0:1.0: 2 ports detected
[    4.100002] usbcore: registered new interface driver libusual
[    4.100002] usbcore: registered new interface driver usbserial
[    4.100002] USB Serial support registered for generic
[    4.100002] usbcore: registered new interface driver usbserial_generic
[    4.100002] usbserial: USB Serial Driver core
[    4.100002] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.100176] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.100176] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.108002] mice: PS/2 mouse device common for all mice
[    4.108002] rtc_cmos 00:03: RTC can wake from S4
[    4.108002] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.108002] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.108002] device-mapper: uevent: version 1.0.3
[    4.108002] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.108002] device-mapper: multipath: version 1.0.5 loaded
[    4.108002] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.108002] EISA: Probing bus 0 at eisa.0
[    4.108002] Cannot allocate resource for EISA slot 1
[    4.108002] EISA: Detected 0 cards.
[    4.108002] cpuidle: using governor ladder
[    4.108002] cpuidle: using governor menu
[    4.108002] TCP cubic registered
[    4.108002] NET: Registered protocol family 10
[    4.108002] Marking TSC unstable due to TSC halts in idle
[    4.108002] lo: Disabled Privacy Extensions
[    4.108002] NET: Registered protocol family 17
[    4.108002] Bluetooth: L2CAP ver 2.11
[    4.108002] Bluetooth: L2CAP socket layer initialized
[    4.108002] Bluetooth: SCO (Voice Link) ver 0.6
[    4.108002] Bluetooth: SCO socket layer initialized
[    4.108002] Bluetooth: RFCOMM socket layer initialized
[    4.108002] Bluetooth: RFCOMM TTY layer initialized
[    4.108002] Bluetooth: RFCOMM ver 1.10
[    4.108002] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.108002] Using IPI No-Shortcut mode
[    4.108002] registered taskstats version 1
[    4.108002]   Magic number: 13:673:264
[    4.108002] rtc_cmos 00:03: setting system clock to 2009-06-19 05:17:55 UTC (1245388675)
[    4.108002] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.108002] EDD information not available.
[    4.111564] Freeing unused kernel memory: 532k freed
[    4.111564] Write protecting the kernel text: 4128k
[    4.111564] Write protecting the kernel read-only data: 1532k
[    4.361014] tg3.c:v3.94 (August 14, 2008)
[    4.361014] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.361014] tg3 0000:09:00.0: setting latency timer to 64
[    4.385012] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.385012] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    4.437011] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    4.445010] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    4.508005] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.560063] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fe4ff800-fe4fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.572007] usb 2-1: configuration #1 chosen from 1 choice
[    4.600008] Initializing USB Mass Storage driver...
[    4.624008] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.632006] usbcore: registered new interface driver usb-storage
[    4.632006] USB Mass Storage support registered.
[    4.632006] usb-storage: device found at 2
[    4.632006] usb-storage: waiting for device to settle before scanning
[    4.653011] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:15:c5:7c:99:6d
[    4.653011] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[    4.653011] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.861033] usb 2-6: new high speed USB device using ehci_hcd and address 5
[    4.996183] usb 2-6: configuration #1 chosen from 1 choice
[    5.232049] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    5.299945] PM: Starting manual resume from disk
[    5.299945] PM: Resume from partition 8:6
[    5.299945] PM: Checking hibernation image.
[    5.299945] PM: Resume from disk failed.
[    5.304149] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.304149] EXT3-fs: write access will be enabled during recovery.
[    5.405135] usb 5-2: configuration #1 chosen from 1 choice
[    5.424130] usbcore: registered new interface driver hiddev
[    5.441918] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input5
[    5.444031] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1d.0-2/input0
[    5.444031] usbcore: registered new interface driver usbhid
[    5.444031] usbhid: v2.6:USB HID core driver
[    5.657104] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    5.836029] usb 7-1: configuration #1 chosen from 1 choice
[    5.904026] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00012568da1]
[    9.632027] usb-storage: device scan complete
[    9.632027] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[    9.632027] sd 4:0:0:0: [sdb] 7827392 512-byte hardware sectors: (4.00 GB/3.73 GiB)
[    9.632027] sd 4:0:0:0: [sdb] Write Protect is off
[    9.632027] sd 4:0:0:0: [sdb] Mode Sense: 16 03 09 51
[    9.632027] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    9.636015] sd 4:0:0:0: [sdb] 7827392 512-byte hardware sectors: (4.00 GB/3.73 GiB)
[    9.636015] sd 4:0:0:0: [sdb] Write Protect is off
[    9.636015] sd 4:0:0:0: [sdb] Mode Sense: 16 03 09 51
[    9.636015] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    9.636015]  sdb: sdb1
[    9.636015] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    9.636015] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   10.696324] kjournald starting.  Commit interval 5 seconds
[   10.696324] EXT3-fs: sda4: orphan cleanup on readonly fs
[   10.696324] ext3_orphan_cleanup: deleting unreferenced inode 1522385
[   10.722162] ext3_orphan_cleanup: deleting unreferenced inode 1275463
[   10.734637] ext3_orphan_cleanup: deleting unreferenced inode 1275459
[   10.734637] ext3_orphan_cleanup: deleting unreferenced inode 1275462
[   10.734637] ext3_orphan_cleanup: deleting unreferenced inode 1275458
[   10.743407] ext3_orphan_cleanup: deleting unreferenced inode 1275460
[   10.743407] ext3_orphan_cleanup: deleting unreferenced inode 1275461
[   10.743407] ext3_orphan_cleanup: deleting unreferenced inode 1243518
[   10.743407] ext3_orphan_cleanup: deleting unreferenced inode 1243510
[   10.750216] ext3_orphan_cleanup: deleting unreferenced inode 188050
[   10.750216] ext3_orphan_cleanup: deleting unreferenced inode 1520907
[   10.763833] ext3_orphan_cleanup: deleting unreferenced inode 662508
[   10.783234] ext3_orphan_cleanup: deleting unreferenced inode 1479869
[   10.801331] ext3_orphan_cleanup: deleting unreferenced inode 1831427
[   10.812081] ext3_orphan_cleanup: deleting unreferenced inode 1831444
[   10.818005] ext3_orphan_cleanup: deleting unreferenced inode 1831428
[   10.825825] ext3_orphan_cleanup: deleting unreferenced inode 1546540
[   10.837845] ext3_orphan_cleanup: deleting unreferenced inode 1546539
[   10.845647] ext3_orphan_cleanup: deleting unreferenced inode 1546538
[   10.845647] ext3_orphan_cleanup: deleting unreferenced inode 1831426
[   10.854808] ext3_orphan_cleanup: deleting unreferenced inode 1831430
[   10.856490] ext3_orphan_cleanup: deleting unreferenced inode 1831425
[   10.856490] ext3_orphan_cleanup: deleting unreferenced inode 1523920
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 1211139
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 1283646
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 1283645
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 1283644
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 1283643
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 1283642
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 1283641
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 1283640
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 1030364
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 2272936
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 2272935
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 2272934
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 2272933
[   10.864904] ext3_orphan_cleanup: deleting unreferenced inode 2272932
[   10.864904] EXT3-fs: sda4: 37 orphan inodes deleted
[   10.864904] EXT3-fs: recovery complete.
[   10.980066] EXT3-fs: mounted filesystem with ordered data mode.
[   17.774095] udev: starting version 141
[   17.976997] acpi device:37: registered as cooling_device2
[   17.976997] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:34/input/input6
[   17.997010] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   18.000132] ACPI Warning (nspredef-0357): \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) [20080926]
[   18.000132] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:39/input/input7
[   18.021011] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   18.089010] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   18.681012] Linux agpgart interface v0.103
[   19.161594] sdhci: Secure Digital Host Controller Interface driver
[   19.161594] sdhci: Copyright(c) Pierre Ossman
[   19.180411] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.236450] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   19.322447] cfg80211: Calling CRDA to update world regulatory domain
[   19.338121] iTCO_vendor_support: vendor-support=0
[   19.354632] Linux video capture interface: v2.00
[   19.418354] cfg80211: World regulatory domain updated:
[   19.418354]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.418354]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.418354]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.418354]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.418354]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.418354]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.438259] ricoh-mmc: Ricoh MMC Controller disabling driver
[   19.438259] ricoh-mmc: Copyright(c) Philip Langdale
[   19.438259] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   19.438259] ricoh-mmc: Controller is now disabled.
[   19.463501] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   19.463501] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   19.468011] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   19.468011] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   19.468011] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   19.472007] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   19.516031] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   19.516031] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   19.516031] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.663694] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   19.666477] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   19.667088] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input9
[   19.667346] usbcore: registered new interface driver uvcvideo
[   19.667346] USB Video Class driver (v0.1.0)
[   19.702200] b43-phy0: Broadcom 4311 WLAN found
[   19.772034] phy0: Selected rate control algorithm 'pid'
[   19.908021] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.908021] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.908021] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   19.944016] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   20.105741] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04753/0x200000
[   20.141194] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   20.618884] lp: driver loaded but no devices found
[   20.709348] Adding 1951856k swap on /dev/sda6.  Priority:-1 extents:1 across:1951856k
[   21.260027] EXT3 FS on sda4, internal journal
[   22.781007] type=1505 audit(1245403094.173:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2266
[   22.837006] type=1505 audit(1245403094.229:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2270
[   22.837006] type=1505 audit(1245403094.229:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2270
[   22.837006] type=1505 audit(1245403094.229:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2270
[   22.837006] type=1505 audit(1245403094.229:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2270
[   23.001007] type=1505 audit(1245403094.393:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2275
[   23.001007] type=1505 audit(1245403094.393:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2275
[   23.093005] type=1505 audit(1245403094.484:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2279
[   23.128008] type=1505 audit(1245403094.520:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2283
[   26.558702] /dev/vmmon[2757]: Module vmmon: registered with major=10 minor=165
[   26.558702] /dev/vmmon[2757]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
[   26.558702] /dev/vmmon[2757]: Module vmmon: initialized
[   26.610278] /dev/vmci[2769]: VMCI: Driver initialized.
[   26.610278] /dev/vmci[2769]: Module vmci: registered with major=10 minor=57
[   26.610278] /dev/vmci[2769]: Module vmci: initialized
[   26.928006] ppdev: user-space parallel port driver
[   28.068172] /dev/vmnet: open called by PID 3369 (vmnet-dhcpd)
[   28.068172] /dev/vmnet: hub 1 does not exist, allocating memory.
[   28.068172] /dev/vmnet: port on hub 1 successfully opened
[   28.100033] /dev/vmnet: open called by PID 3373 (vmnet-netifup)
[   28.100033] /dev/vmnet: port on hub 1 successfully opened
[   28.181036] /dev/vmnet: open called by PID 3379 (vmnet-dhcpd)
[   28.181036] /dev/vmnet: hub 8 does not exist, allocating memory.
[   28.181036] /dev/vmnet: port on hub 8 successfully opened
[   28.252107] /dev/vmnet: open called by PID 3381 (vmnet-natd)
[   28.252107] /dev/vmnet: port on hub 8 successfully opened
[   28.276327] /dev/vmnet: open called by PID 3385 (vmnet-netifup)
[   28.276327] /dev/vmnet: port on hub 8 successfully opened
[   32.135837] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.135837] Bluetooth: BNEP filters: protocol multicast
[   32.196023] Bridge firewalling registered
[   33.693006] [drm] Initialized drm 1.1.0 20060810
[   33.804544] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   33.804544] pci 0000:00:02.0: setting latency timer to 64
[   33.804544] pci 0000:00:02.0: irq 2299 for MSI/MSI-X
[   33.804544] [drm] Initialized i915 1.6.0 20080730 on minor 0
[/HTML]



bueno ya esta desidido formateare y pondre ubuntu 8.04 con 4G de swap haber si con esto se acaba, 1 semana completa para que me la ganara. ya no puedo seguir invirtiendo mas tiempo por que ahora me salio pega.. PORFA NO ME FALLES WASHITO funciona xD

como tanto, digo yo

---

