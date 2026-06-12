---
title: "[SOLUCIONADO] problema en imagenes y videos acer aspire 5000"
date: 2009-06-28
forum: Hardware
---

### Post by tralala321 on 2009-06-28
hola soy nueva en el mundo de ubuntu y entiendo algo gracias a la bioinformatica..... bueno pasa que instale ubuntu 9.04 en mi semiportatil jeje acer aspire 5000 y todo esta relativamente bien, salvo que cuando intente colocar los drivers de wireless, creo q hice algo mal (de hecho) y comenzaron a verse rayas en las imagenes del escritorio y del internet y bueno todo lo que tenga animacion tiene un tono amarillo y tambien unas rayas.He intentado arreglarlo pero no entiendo muy bien como instalar los drivers de video e internet inalambrico
Se que el tema esta resulto en otros post, pero estan en ingles y no me manejo muy bien.
Esop gracias de antemano.:KS

---

### Post by Carlos C on 2009-06-28
Hola tralala. Antes de ayudarte necesitamos saber las características de tu equipo. Por favor escribe en el terminal:
```
lspci
```
y copia el resultado acá de lo que te salga. Respecto a tu problema de video no debiera tener relación con el wifi. Lo importante es saber qué has hecho en tu sistema, si has seguido algún tutorial dinos cuál, si has instalado algo, dinos qué.
Sobre tu problema de wifi, tendríamos que verlo en un post aparte.
Saludos.

---

### Post by tralala321 on 2009-06-28
hola, he instalado tantas cosas que prefiero obviarlo y seguir como si nada he hecho xD.

esto me salio:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by CdK1 on 2009-06-28
Cuando dices "intenté", lo lograste? tienes corriendo tú "wifi"?, recuerdas que hiciste?, has intentado borrar los .* de tu $HOME/ para ver que no es drama de configuración?, bueno para más dudas y algo rápido entra al canal IRC...

---

### Post by tralala321 on 2009-06-29
no se q es esto  .* de tu $HOME/  talvez sea configuracion
es raro el problema; por ejemplo en este momento todo se ve mejor (no muy bien) pero de a poco comienzan a salir las rayas amarillas y blancas q estan moviendose.

---

### Post by CdK1 on 2009-06-29
Veamos, trataré, a petición de unos trollsillos, de ser más claro:

1.- Que tarjeta de video tienes
2.- pega lo que sale con este comando: cat /etc/X11/xorg.conf
3.- Cuando estés usando tú sistema, pon este comando en la terminal; dmesg y envíalo
4.- Asu vez, en la misma terminal, usando el sistema, pon tail -f /home/USUARIO/.xsession-errors  ==> USUARIO=tunombre de usuario
5.- Dime cuando comenzño a suceder esto, después de una actualización?, de instalar algo?, antes te funcionaba bien? etc...

---

### Post by tralala321 on 2009-06-30
hola, perdon por mis preguntas, es q soy ignorante en esto de ubuntu; igual entiendo que debe ser molesto que yo pida que me digan cada paso que debo dar.

bueno... esto me salio 

tralala@tralala-laptop:~$ **lspci**
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter



tralala@tralala-laptop:~$ **cat /etc/X11/xorg.conf**
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


tralala@tralala-laptop:~$ **tail -f /home/tralala/.xsession-errors**
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
evolution-alarm-notify-Message: Setting timeout for 84782 1246492800 1246408018
evolution-alarm-notify-Message:  Wed Jul  1 20:00:00 2009



el problema de los colores, los videos y las rayitas comenzo cuando trate de colocar el wifi (voy a medias en eso y antes se veia bien) y entonces pense que era por que no lo habia actualizado (entonces actualice a 9.04 y se mejoro un poco el problema);luego vine al foro en busca de soluciones y me dijieron q no tenia nada que ver con los drivers que intente colocar para el wifi y luego estudio estudio y ahora estoy sentada frente al pc. esop

saludos ):P

---

### Post by CdK1 on 2009-06-30
Has lo siguiente;

dpkg -l | grep xserver-xorg-video-sis



Si lo tienes entonces haz esto:

lsmod | grep sis

Debería salirte algo similar a esto:

sis900                 
mii                     
sis_agp               
agpgart                

Si es así, entonces haz esto:


Intenta hacer esto para la configuración de las X;

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf y déjalo similar a esto:

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/X11R6/lib/X11/fonts/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/X11R6/lib/X11/fonts/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/X11R6/lib/X11/fonts/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/X11R6/lib/X11/fonts/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/usr/X11R6/lib/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "speedo"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "es"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or
 662/761Gx PCIE VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
             
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or
 662/761Gx PCIE VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection


Y reinicias;

En el caso que el dpkg -l no te tire nada, intálalo de la siguiente manera;

sudo apt-get install xserver-xorg-video-sis 

Y reinicias.


Para lo siguiente;

tralala@tralala-laptop:~$ tail -f /home/tralala/.xsession-errors
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
evolution-alarm-notify-Message: Setting timeout for 84782 1246492800 1246408018
evolution-alarm-notify-Message: Wed Jul 1 20:00:00 2009

Usas Opera? como lo instalaste?, si lo usas haz esto:

sudo apt-get autoremove opera

sudo gedit /etc/apt/sources.list y agrega lo siguiente;

deb [http://deb.opera.com/opera](http://deb.opera.com/opera) testing non-free

Guarda y cierra y ejecuta;

sudo apt-get update
sudo apt-get install opera sun-java6-jre 

Y la wifi, la tienes andando?

---

### Post by tralala321 on 2009-06-30
hice todo lo anterior pero me costo entrar.
antes de iniciar salia un mensaje que decia ubuntu va  a iniciar en modo de graficos bajos, y otro monton de mesajes mas, por ejemplo que ya existia el servidos x en ejecucion en la pantalla:0 
y cuando logre entrar no hay rayas pero todo se ve extragrande (como en el modo a prueba de fallos de wondows)  y al apagar el equipo para volver a entrar salen los mismos mensajes asi que elegi el de restaurar los graficos anteriores y bueno denuevo se ve con rayitas #-o


deje de usar opera, es q antes no podia usar google pero ya puedo

y lo del wifi, ya me dijieron como arreglarlo en otro post, aun no lo intento 

gracias por darse el tiempo de ayudar a todos  ):P

---

### Post by CdK1 on 2009-06-30
Que resolución de pantalla usas?

Además puedes pegarme este comando por favor:

cat /var/log/Xorg.0.log

---

### Post by tralala321 on 2009-07-01
la resolucion que uso es 1280x800


y con el comando salio esto, uuff es mucho:

(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched sis from file name sis.ids
(==) Matched sis for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 0.10.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for sis
(WW) SIS: No matching Device section for instance (BusID PCI:0@0:0:0) found
(--) Assigning device section with no busID to primary device
(--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [21] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [22] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [24] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [25] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [26] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [33] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [34] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.5.99.902)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0xA000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) SIS(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) SIS(0): Depth 24, (--) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(WW) SIS(0): Could not find/read video BIOS
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor
(==) SIS(0): Color HW cursor is enabled
(II) SIS(0): Using VRAM command queue, size 512k
(==) SIS(0): Hotkey display switching is enabled
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
        [http://www.winischhofer.at/linuxsispart1.shtml#sisctrl](http://www.winischhofer.at/linuxsispart1.shtml#sisctrl)
(==) SIS(0): DRI disabled
(II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
(--) SIS(0): 131072K shared video RAM (UMA)
(--) SIS(0): DRAM type: DDR SDRAM
(--) SIS(0): Memory clock: 198.861 MHz
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xE8000000
(--) SIS(0): MMIO registers at 0xE2100000 (size 64K)
(--) SIS(0): VideoRAM: 131072 KB
(II) SIS(0): Using 130496K of framebuffer memory at offset 0K
(--) SIS(0): Hardware supports two video overlays
(II) SIS(0): 
    Dear SiS76x user, your machine is using a shared memory framebuffer.
    Due to hardware limitations of the SiS chip in combination with the
    AMD CPU, video overlay support is very limited on this machine. If you
    experience flashing lines in the video and/or the graphics display
    during video playback, reduce the color depth and/or the resolution
    and/or the refresh rate. Alternatively, use the video blitter.
(--) SIS(0): Detected SiS302LV video bridge (Charter/UMC-1, ID 1; Rev 0xe1)
(--) SIS(0): BIOS uses LCDA for low resolution and text modes
(--) SIS(0): No CRT1/VGA detected
(--) SIS(0): Detected LCD/plasma panel (1280x800, 11, non-exp., RGB18 [3cc506])
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): CRT1 gamma correction is enabled
(II) SIS(0): Separate Xv gamma correction for CRT1 is disabled
(II) SIS(0): CRT2 gamma correction is enabled
(--) SIS(0): Memory bandwidth at 32 bpp is 397.722 MHz
(--) SIS(0): Detected LCD PanelDelayCompensation 0x00 (for LCD=CRT2)
(--) SIS(0): Detected LCD PanelDelayCompensation1 0x04 (for LCD=CRT1)
(--) SIS(0): 302LV/302ELV: Using EMI 0x600d703f (LCD)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SIS(0): CRT2 DDC probing failed
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 290 MHz
(II) SIS(0): Replaced entire mode list with built-in modes
(II) SIS(0): Correcting missing CRT2 monitor HSync range
(II) SIS(0): Correcting missing CRT2 monitor VRefresh range
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Configured Monitor: Using hsync range of 30.00-80.00 kHz
(II) SIS(0): Configured Monitor: Using vrefresh range of 59.00-61.00 Hz
(II) SIS(0): Configured Monitor: Using vrefresh value of 71.00 Hz
(WW) SIS(0): Unable to estimate virtual size
(II) SIS(0): Clock range:  10.00 to 290.64 MHz
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (unknown reason)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x720" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x960" (unknown reason)
(II) SIS(0): Not using default mode "1280x960" (unknown reason)
(II) SIS(0): Not using default mode "1280x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1400x1050" (unknown reason)
(II) SIS(0): Not using default mode "1400x1050" (unknown reason)
(II) SIS(0): Not using default mode "1152x864" (unknown reason)
(II) SIS(0): Not using default mode "1152x864" (unknown reason)
(II) SIS(0): Not using default mode "1152x864" (unknown reason)
(II) SIS(0): Not using default mode "848x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "856x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "1360x768" (unknown reason)
(II) SIS(0): Not using default mode "1280x800" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(II) SIS(0): Not using default mode "1680x1050" (unknown reason)
(II) SIS(0): Not using default mode "1920x1080" (unknown reason)
(II) SIS(0): Not using default mode "1280x854" (unknown reason)
(II) SIS(0): Not using default mode "1280x854" (unknown reason)
(II) SIS(0): Not using default mode "1280x854" (unknown reason)
(--) SIS(0): Virtual size is 1280x800 (pitch 1280)
(**) SIS(0): *Default mode "1280x800" (1280x800) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)
(**) SIS(0): *Default mode "1280x768" (1280x768) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)
(**) SIS(0): *Default mode "1280x720" (1280x720) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)
(**) SIS(0): *Default mode "1024x768" (1024x768) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
(**) SIS(0): *Default mode "1024x576" (1024x576) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
(**) SIS(0): *Default mode "960x600" (960x600) (For CRT device: 41.5 MHz, 37.1 kHz, 60.0 Hz)
(**) SIS(0): *Default mode "960x540" (960x540) (For CRT device: 37.3 MHz, 33.8 kHz, 60.0 Hz)
(**) SIS(0): *Default mode "800x600" (800x600) (For CRT device: 40.0 MHz, 37.9 kHz, 60.3 Hz)
(**) SIS(0): *Default mode "768x576" (768x576) (For CRT device: 35.0 MHz, 35.9 kHz, 60.1 Hz)
(**) SIS(0): *Default mode "720x576" (720x576) (For CRT device: 32.7 MHz, 35.9 kHz, 60.1 Hz)
(**) SIS(0): *Default mode "856x480" (856x480) (For CRT device: 33.9 MHz, 31.7 kHz, 59.8 Hz)
(**) SIS(0): *Default mode "848x480" (848x480) (For CRT device: 33.7 MHz, 31.0 kHz, 60.0 Hz)
(**) SIS(0): *Default mode "800x480" (800x480) (For CRT device: 39.8 MHz, 37.7 kHz, 60.0 Hz)
(**) SIS(0): *Default mode "720x480" (720x480) (For CRT device: 28.3 MHz, 31.6 kHz, 61.0 Hz)
(**) SIS(0): *Default mode "640x480" (640x480) (For CRT device: 25.1 MHz, 31.3 kHz, 59.7 Hz)
(**) SIS(0): *Default mode "640x400" (640x400) (For CRT device: 25.1 MHz, 31.6 kHz, 71.6 Hz)
(**) SIS(0): *Default mode "512x384" (512x384) (For CRT device: 32.6 MHz, 48.5 kHz, 60.1 Hz (D))
(**) SIS(0): *Default mode "400x300" (400x300) (For CRT device: 20.0 MHz, 37.9 kHz, 60.3 Hz (D))
(**) SIS(0): *Default mode "320x240" (320x240) (For CRT device: 12.5 MHz, 31.3 kHz, 60.7 Hz (D))
(**) SIS(0): *Default mode "320x200" (320x200) (For CRT device: 12.5 MHz, 31.3 kHz, 70.9 Hz (D))
(==) SIS(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) SIS(0): 2D acceleration enabled
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
    [21] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
    [22] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [24] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [25] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [26] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [33] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [34] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 16384 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 6330
(II) SIS(0): VESA VBE OEM Product Rev: 2.27.g8
(II) SIS(0): Setting standard mode 0x16
(II) SIS(0): SiS76x/UMA: two video overlay(s) available in current mode
(II) SIS(0): RENDER acceleration enabled
(II) SIS(0): Framebuffer from (0,0) to (1279,26097)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    8x8 color pattern filled rectangles
    Solid Lines
    Dashed Lines
    Setting up tile and stipple cache:
        32 128x128 slots
        32 256x256 slots
        16 512x512 slots
        32 8x8 color pattern slots
(--) SIS(0): CPU frequency 1800.00Mhz
(II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
(--) SIS(0):     Checked libc memcpy()...     190.4 MiB/s
(--) SIS(0):     Checked built-in-1 memcpy()...     190.7 MiB/s
(--) SIS(0):     Checked built-in-2 memcpy()...     63.8 MiB/s
(--) SIS(0):     Checked MMX memcpy()...     376.2 MiB/s
(--) SIS(0):     Checked 3DNow! memcpy()...     374.8 MiB/s
(--) SIS(0):     Checked MMX2 memcpy()...     376.0 MiB/s
(--) SIS(0): Using MMX method for aligned data transfers to video RAM
(--) SIS(0): Using MMX method for unaligned data transfers to video RAM
(==) SIS(0): Backing store disabled
(==) SIS(0): Silken mouse enabled
(II) SIS(0): DPMS enabled
(II) SIS(0): Using SiS300/315/330/340 series HW Xv
(II) SIS(0): Default Xv adaptor is Video Overlay
(II) SIS(0): Initialized SISCTRL extension version 0.1
(II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.99.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found


:p

---

### Post by CdK1 on 2009-07-01
OK, haz esto:

sudo gedit /etc/X11/xorg.conf

y en la parte;

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or
 662/761Gx PCIE VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Dejaló así:

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or
 662/761Gx PCIE VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes                     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes                     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes                     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

y haz esto: 

sudo rm /var/log/Xorg.0.log

Reinicias y me pegas de nuevo el archivo por favor...

---

### Post by tralala321 on 2009-07-01
a patriciologo sorry no se carga eso del irc..........otro cuac! para mi pc supongo


cuando coloco esto: sudo gedit /etc/X11/xorg.conf

sale esto:

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



entonces tu me dices q pegue esto otro y lo deje asi:


Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or
 662/761Gx PCIE VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes                     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes                     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes                     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

(ya lo habia intentado) y paso lo mismooooo, mas cuac!!! para mi pc :frown:

---

### Post by CdK1 on 2009-07-01
Pues no... la idea de editar ese archivo, es que quede de la siguiente manera:

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/X11R6/lib/X11/fonts/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/X11R6/lib/X11/fonts/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/X11R6/lib/X11/fonts/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/X11R6/lib/X11/fonts/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/usr/X11R6/lib/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "speedo"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "es"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or
 662/761Gx PCIE VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
             
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or
 662/761Gx PCIE VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes                     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes                     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes                     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection


Así es como debe quedar el archivo...

---

### Post by tralala321 on 2009-07-01
holis, ya se como arreglar todos los problemillas......... formateando el pc xD, puse windows y ubuntu y esta todo bien la imagen y estoy usando internet inalambrico jejeje.

Gracias muchas gracias son todos muy amorosos en ayudar. Bendiciones.

---

