---
title: "Problema Driver Nvidia 7600 GT"
date: 2009-04-27
forum: Hardware
---

### Post by ratas89 on 2009-04-27
Hola, les comento mi problema aver si alguno me puede dar una solucion, ya que probe de todo y parece no arreglarse con nada. El tema es el siguiente, Instale Ubuntu Hasta ahi todo feliz, me detecta la placa me dice para instalarla le doy ok a todo me pide reiniciar, al momento de reiniciar y despues del booteo la pantalla se queda en negro, para volver a a cceder tengo que entrar en "a prueba de fallos" deshabilitando el controlador Nvidia, Pruebo instalando con Envy y sucede lo mismo y de forma manual lo mismo, los drivers se instalan pero nose por que no "arrancan" la pantalla se queda en negro y el monitor entra en suspension

Espero que alguno me tire una soga 

Un abrazo!

---

### Post by luks911 on 2009-04-27
¿Qué versión de Ubuntu usás? ¿Y qué versión del driver instalaste 173 o 180?
Algo más: ¿cuando el monitor se pone negro probaste con Ctrl+Alt+F1 para entrar a una consola?

---

### Post by pablo.s on 2009-04-27
Problema de tasa de refresco...

50 patacones a 1

---

### Post by anarko on 2009-04-27
Voy con los 50 patacones a 1. 

Pegate una vuelata por /var/log/Xorg.algo.log y busca las lineas que comienzan con ( EE ) que significan error, por ahi tenes alguna pista de lo que te pasa, siempre lo primero es mirar los logs.

---

### Post by ratas89 on 2009-04-27
Gracias, ahora voy a probar lo que me dijieron, lo de la tasa de refresco como lo modifico? y lo de las lineas con error que deberai fijarme? perdon si pregunto mucho pero soy absolutamente nuevo en esto gracias qeu se poner sudo en la consola jajaj

El monitor aparece en "Modo de ahorro de energia" nose por que se pone asi


Ubuntu 8.10 version de driver no lo se el que instalo el sistema :S

---

### Post by pablo.s on 2009-04-27
> **ratas89 said:**
> Gracias, ahora voy a probar lo que me dijieron, lo de la tasa de refresco como lo modifico?

Fijate en el manual del monitor
que dice en las especificaciones
técnicas

> **ratas89 said:**
> y lo de las lineas con error que deberai fijarme? 
Comenzá por darnos la información
que te faltó: que versión de driver
le autorizaste a instalar/desinstalar


> **ratas89 said:**
> perdon si pregunto mucho pero soy absolutamente nuevo en esto gracias qeu se poner sudo en la consola jajaj

No hay problema por eso, ya vas
a ir interiorizandote en este mundo.

> **ratas89 said:**
> El monitor aparece en "Modo de ahorro de energia" nose por que se pone asi

Se pone asi por la tasa de refresco que es 
más alta de lo que soporta. También 
comentanos que modelo de monitor es.

---

### Post by ratas89 on 2009-04-28
> **pablo.s said:**
> Fijate en el manual del monitor
que dice en las especificaciones
técnicas

El monitor en windows funciona a 60 hz y anda perfecto asi que esa debe ser la tasa soportada. el monitor es un lg 1900r


> **pablo.s said:**
> Comenzá por darnos la información
que te faltó: que versión de driver
le autorizaste a instalar/desinstalar

Eso no lo se, primero le puse instalar el driver automaticamente, cuando ubuntu detecta la placa, y despues el ultimo driver de la pagina de nvidia fue el 180.51



pd: Ahora la placa ni me aparece en los controladores de placa, si me dicen como cambiar la tasa a 60 hz una vez instalado el driver reinstalo ubuntu a ver si lo puedo hacer andar y cuqndo pongo /var/log/Xorg.algo.log me dice que el fichero no existe

y busdando en internet quise entrar al xorg.conf pero me tira acceso denegado asi le ponga sudo adelante o entre como root estoy poniendo /etc/X11/xorg.conf y tira permiso denegado

Gracais muchachos por las rtas!

---

### Post by pablo.s on 2009-04-28
> **ratas89 said:**
> El monitor en windows funciona a 60 hz y anda perfecto 

Instalá Grandr con [COLOR=Green]**sudo apt-get install grandr**[/COLOR]

Después ejecutá en la terminal
**[COLOR=Green]grandr[/COLOR]**

y te va a mostrar distintos modos
y tasas de refresco (se describen en
hertzios, o sea Hz)


> **ratas89 said:**
> cuqndo pongo /var/log/Xorg.algo.log me dice que el fichero no existe

Es que no existe ese archivo: lo que
anarko te explicó es que xorg.algo.log
quiere decir que donde dice "algo" ahi
va un cero generalmente, o un uno
digamos. Si escribís en una terminal
**[COLOR=Green]cat /var/log/Xorg.0.log [/COLOR]**[COLOR=Black]te[/COLOR][COLOR=Green][COLOR=Black] devuelve
un "dump" del archivo que podés
copiar y pegar en un mensaje, asi
analizamos la configuración.
[/COLOR][/COLOR]

---

### Post by ratas89 on 2009-04-28
Les dejo adjunto el log 


Gracias :)

---

### Post by pablo.s on 2009-04-28
No aparece.

---

### Post by ratas89 on 2009-04-28
GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT, 
    GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400, 
    Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT, 
    GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600, 
    GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL, 
    GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550, 
    Quadro FX 540, GeForce 6200, GeForce 6500, 
    GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM), 
    GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400, 
    GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800, 
    GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200, 
    GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX, 
    GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800, 
    GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE, 
    GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400, 
    GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M, 
    GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT, 
    GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT, 
    GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT, 
    Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560, 
    GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS, 
    GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M, 
    Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500, 
    Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100, 
    GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS, 
    GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS, 
    GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT, 
    GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M, Quadro FX 570M, 
    Quadro FX 1600M, Quadro FX 570, Quadro FX 1700, GeForce 8500 GT, 
    GeForce 8400 GS, GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, 
    GeForce 8400M GT, GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, 
    Quadro NVS 130M, Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290, 
    GeForce 8800 GT, GeForce 8800 GS, GeForce 8800 GS, GeForce 8800 GT, 
    Quadro FX 3700, GeForce 9600 GT, GeForce 8400 GS 
(II) Primary Device is: PCI 01:00:0 
(--) Assigning device section with no busID to primary device 
(--) Chipset GeForce 7600 GT found

---

### Post by ratas89 on 2009-04-28
No me deja subirlo por que me dice q es muy pesado y cuando lo quiero pegar aca la otra parte me dice que mi mensaje invluye 12 imagenes :S

---

### Post by pablo.s on 2009-04-28
Y lo de instalar grandr?
Puede solucionar el tema...

---

### Post by axelbrz on 2009-10-13
Hola,

Tengo una NVIDIA 7900 GT, y tengo exactamente el mismo problema.

¿Alguien lo pudo solucionar?

Gracias!

---

### Post by pablo.s on 2009-10-13
¿Cuál versión de Ubuntu estás
usando? ¿El núcleo, los drivers?
¿El monitor?
Detallanos la situación un poco
mas y los sacamos andando.

---

### Post by axelbrz on 2009-10-13
Holas,

Raramente ahora ya no se me suspende el monitor, pero me pasa lo que me pasó un tiempo.

Estoy usando:
- Ubuntu: 9.04
- Kernel: 2.6.28-15-generic
- Placa de video: MSI nVidia 7900 GT
- Driver: NVIDIA-Linux-x86-185.18.36-pkg1 (pero me pasa lo mismo con otras versiones)
- Monitor: ViewSonic vx724

La última instalación del driver que intenté realizar, fue hacer directamente ./NVIDIA.., lo que me dice que no tengo ningún kernel precompilado, y elijo que lo compile en el momento, lo que parece bajarse algo de la página de NVIDIA, y me instala todo, pero cuando reinicio consigo este mensaje:

**Ubuntu is running in low-graphics mode**
Failed to initialize the NVIDIA kernel module. Please see the system's kernel log for additional error messages and consult the NVIDIA README for details.
*** Aborting ***
Screen(s) found, but none have a usable configuration.

Cuando le doy aceptar, me aparece "Stand by a minute while the display restarts", y al rato en consola aparece:

There already appears to be an X server running on display :0. Should another display number by tried?. Answering no will cause GDM attempt starting the server on :0 again.

Y al darle al yes, aparece en X un mensajito "The specified display number was busy, so this server was started on display :1.", le doy aceptar, y luego me entra pero con todos los efectos deshabilitados, etc, etc.

¿Qué hago?

Muchas gracias!

---

### Post by guillermolisi on 2009-10-13
> **axelbrz said:**
> Holas,

Raramente ahora ya no se me suspende el monitor, pero me pasa lo que me pasó un tiempo.

Estoy usando:
- Ubuntu: 9.04
- Kernel: 2.6.28-15-generic
- Placa de video: MSI nVidia 7900 GT
- Driver: NVIDIA-Linux-x86-185.18.36-pkg1 (pero me pasa lo mismo con otras versiones)
- Monitor: ViewSonic vx724

La última instalación del driver que intenté realizar, fue hacer directamente ./NVIDIA.., lo que me dice que no tengo ningún kernel precompilado, y elijo que lo compile en el momento, lo que parece bajarse algo de la página de NVIDIA, y me instala todo, pero cuando reinicio consigo este mensaje:

**Ubuntu is running in low-graphics mode**
Failed to initialize the NVIDIA kernel module. Please see the system's kernel log for additional error messages and consult the NVIDIA README for details.
*** Aborting ***
Screen(s) found, but none have a usable configuration.

Cuando le doy aceptar, me aparece "Stand by a minute while the display restarts", y al rato en consola aparece:

There already appears to be an X server running on display :0. Should another display number by tried?. Answering no will cause GDM attempt starting the server on :0 again.

Y al darle al yes, aparece en X un mensajito "The specified display number was busy, so this server was started on display :1.", le doy aceptar, y luego me entra pero con todos los efectos deshabilitados, etc, etc.

¿Qué hago?

Muchas gracias!
Empezaria revisando el log del x-server (/var/log/Xorg.0.log) y luego seguirira por /var/log/messages y/o dmesg.

---

### Post by axelbrz on 2009-10-13
Les dejo los dos archivos que me piden:
[B]
/var/log/Xorg.0.log[/B]
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux axelpc-lin 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 13 18:38:37 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) nVidia Corporation G71 [GeForce 7900 GT/GTO] rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
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
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) NVIDIA(0):     system's kernel log for additional error messages and
(EE) NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```**/var/log/messages** (últimas líneas)
```
Oct 13 18:38:31 axelpc-lin kernel: [ 9047.310161] NVRM: API mismatch: the client has the version 185.18.36, but
Oct 13 18:38:31 axelpc-lin kernel: [ 9047.310163] NVRM: this kernel module has the version 180.44.  Please
Oct 13 18:38:31 axelpc-lin kernel: [ 9047.310165] NVRM: make sure that this kernel module and all NVIDIA driver
Oct 13 18:38:31 axelpc-lin kernel: [ 9047.310166] NVRM: components have the same version.
Oct 13 18:38:34 axelpc-lin kernel: [ 9050.459661] NVRM: API mismatch: the client has the version 185.18.36, but
Oct 13 18:38:34 axelpc-lin kernel: [ 9050.459663] NVRM: this kernel module has the version 180.44.  Please
Oct 13 18:38:34 axelpc-lin kernel: [ 9050.459664] NVRM: make sure that this kernel module and all NVIDIA driver
Oct 13 18:38:34 axelpc-lin kernel: [ 9050.459665] NVRM: components have the same version.
Oct 13 18:38:37 axelpc-lin kernel: [ 9053.596510] NVRM: API mismatch: the client has the version 185.18.36, but
Oct 13 18:38:37 axelpc-lin kernel: [ 9053.596512] NVRM: this kernel module has the version 180.44.  Please
Oct 13 18:38:37 axelpc-lin kernel: [ 9053.596514] NVRM: make sure that this kernel module and all NVIDIA driver
Oct 13 18:38:37 axelpc-lin kernel: [ 9053.596515] NVRM: components have the same version.
Oct 13 18:39:44 axelpc-lin pulseaudio[7122]: pid.c: Stale PID file, overwriting.
```Bueno, según lo que leí en el messages, parece que la versión del driver (185) no es la misma que la versión del kernel (180).. 

¿Cómo sigo?

---

### Post by guillermolisi on 2009-10-13
No recuerdo haber leido si ya probaste con la version de driver nvidia 180, que es la que tenes compilada para ese kernel (por los mensajes que mostraste).

---

### Post by axelbrz on 2009-10-13
Sí, e instalando todo por default (como me recomendó Ubuntu al principio) me generaba que el monitor se me suspenda como dije al principio.

El problema es que ahora no sé cómo quitar el de versión 185, y cuando voy a Hardware Drivers me dice que está instalado el de versión 180..

Qué hago?

Gracias.

---

### Post by luks911 on 2009-10-13
> **axelbrz said:**
> Sí, e instalando todo por default (como me recomendó Ubuntu al principio) me generaba que el monitor se me suspenda como dije al principio.

El problema es que ahora no sé cómo quitar el de versión 185, y cuando voy a Hardware Drivers me dice que está instalado el de versión 180..

Qué hago?

Gracias.

¿Cómo instalaste el 185? Si lo bajaste de la página de Nvidia, para desisntalarlo deberías ejecutar

```
sudo nvidia-installer --uninstall
```

---

### Post by axelbrz on 2009-10-13
Hice:

[FONT=Courier New]sudo nvidia-installer --uninstall[/FONT]

Y volví al problema original (por el cuál posteé en este thread), la pantalla se me suspende al iniciar gdm.

Para poder volver a X tuve que malformar el xorg.conf para que me de el siguiente error (pero por lo menos pude entrar a X con low-graphics):

[FONT=Courier New]Problem parsing the config file
Error parsing the confir file[/FONT]

Lo que también intenté es, dentro de Screen, dentro de Display usar:

[FONT=Courier New]Modes "1280x1024_75[/FONT]"

pero mi pantalla se sigue suspendiendo.

Cómo sigo? :)

---

### Post by luks911 on 2009-10-13
> **axelbrz said:**
> Hice:

[FONT=Courier New]sudo nvidia-installer --uninstall[/FONT]

Y volví al problema original (por el cuál posteé en este thread), la pantalla se me suspende al iniciar gdm.

Para poder volver a X tuve que malformar el xorg.conf para que me de el siguiente error (pero por lo menos pude entrar a X con low-graphics):

[FONT=Courier New]Problem parsing the config file
Error parsing the confir file[/FONT]

Lo que también intenté es, dentro de Screen, dentro de Display usar:

[FONT=Courier New]Modes "1280x1024_75[/FONT]"

pero mi pantalla se sigue suspendiendo.

Cómo sigo? :)

Sí, lo que te pasaba era para desinstalar el 185. Se me ocurre probar de instalarlo de nuevo, pero antes desinstalando el 180.
Lo desisntalás ejecutando

```
sudo aptitude remove nvidia-glx-180 nvidia-180-kernel-source 
```

Después instalá el 185 con el procedimiento que utilizaste antes. Se supone que de ese modo ya no habría conflicto de versiones y tendrías sólo el 185.

---

### Post by axelbrz on 2009-10-13
luks911, seguí tus pasos desinstalando primero el 180, y luego instalando el 185, pero tengo el mismo problema. Para volver a X lo que tuve que hacer fue malformar el xorg.conf para entrar con low-graphics y obtener el mensaje:

Problem parsing the config file
Error parsing the config file

Pero por lo menos pude entrar a X otra vez :)

Les mando mi xorg.conf sin malformar generado por nvidia-xconfig (con Modes agregado por mi, pero aunque tenga eso, sigue sin funcionar):

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    Modes "1280x1024_75"
    EndSubSection
EndSection

```Además, escuchando los parlantes, me doy cuenta que puedo iniciar sesión lo más bien (poniendo usuario y contraseña se escucha el sonido de iniciada la sesión), lo que significa que no me tira ningún error, sólo se suspende la pantalla.

Como creí que el problema era el refresco, actualicé el xorg.cong agregando también (encontré esta info en internet sobre mi monitor):

```
Section "Monitor"
        Identifier      "VX724"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     50-75
    ModelName        "VX724"
    Option           "PreferredMode" "1280x1024"
    VendorName       "VIEWSONIC"
EndSection
```Y actualizando el respectivo Monitor en Screen (poniendo VX724), pero me sigue pasando lo mismo.

Otra cosa que probé, es usar de Driver "vesa" en vez de "nvidia" y ahí funciona perfecto! no se suspende el monitor, así que lo que hace que se suspenda el monitor es poner "nvidia" en Driver dejando el resto del xorg.conf intacto..

También probé seguir este tutorial:
[http://ubuntuforums.org/showthread.php?t=1183319](http://ubuntuforums.org/showthread.php?t=1183319)

Pero no hay caso! :(

¿Alguna idea?

---

### Post by axelbrz on 2009-10-13
Es más, les dejo el Xorg.0.log generado (lo que sigue fue generado sólo al iniciar gdm con "nvidia" en Driver.. los logs anteriores los eliminé antes de iniciar gdm para asegurarme de que no haya más información de la que debe haber):

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux axelpc-lin 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 13 22:35:36 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "VX724"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) nVidia Corporation G71 [GeForce 7900 GT/GTO] rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "UseEDID" "False"
(**) NVIDIA(0): Option "MetaModes" "1280x1024 +0+0"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 7900 GT/GTO (G71) at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.12.02
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7900 GT/GTO at
(--) NVIDIA(0):     PCI:2:0:0:
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-1's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1280x1024+0+0"
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) Loading extension NV-GLX
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(WW) NVIDIA(0): Option "PreferredMode" is not used
(WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to write-back cached memory.
(II) NVIDIA(0): Initialized GPU GART.
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
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) AT Translated Set 2 keyboard: xkb_layout: "es"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) config/hal: Adding input device Genius Optical Mouse
(**) Genius Optical Mouse: always reports core events
(**) Genius Optical Mouse: Device: "/dev/input/event4"
(II) Genius Optical Mouse: Found 3 mouse buttons
(II) Genius Optical Mouse: Found x and y relative axes
(II) Genius Optical Mouse: Configuring as mouse
(**) Genius Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE)
(**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
(**) Genius Optical Mouse: (accel) filter chain progression: 2.00
(**) Genius Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Genius Optical Mouse: (accel) set acceleration profile 0
(II) Genius Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```

Espero respuestas,

Gracias!

---

### Post by guillermolisi on 2009-10-13
> **axelbrz said:**
> Es más, les dejo el Xorg.0.log generado (lo que sigue fue generado sólo al iniciar gdm con "nvidia" en Driver.. los logs anteriores los eliminé antes de iniciar gdm para asegurarme de que no haya más información de la que debe haber):

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux axelpc-lin 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 13 22:35:36 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "VX724"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) nVidia Corporation G71 [GeForce 7900 GT/GTO] rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "UseEDID" "False"
(**) NVIDIA(0): Option "MetaModes" "1280x1024 +0+0"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 7900 GT/GTO (G71) at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.12.02
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7900 GT/GTO at
(--) NVIDIA(0):     PCI:2:0:0:
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-1's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1280x1024+0+0"
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) Loading extension NV-GLX
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
[COLOR=Red](EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***[/COLOR]
[COLOR=Red](II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled[/COLOR]
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
[COLOR=Red](WW) NVIDIA(0): Option "PreferredMode" is not used
(WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to write-back cached memory.[/COLOR]
(II) NVIDIA(0): Initialized GPU GART.
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
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) AT Translated Set 2 keyboard: xkb_layout: "es"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) config/hal: Adding input device Genius Optical Mouse
(**) Genius Optical Mouse: always reports core events
(**) Genius Optical Mouse: Device: "/dev/input/event4"
(II) Genius Optical Mouse: Found 3 mouse buttons
(II) Genius Optical Mouse: Found x and y relative axes
(II) Genius Optical Mouse: Configuring as mouse
(**) Genius Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE)
(**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
(**) Genius Optical Mouse: (accel) filter chain progression: 2.00
(**) Genius Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Genius Optical Mouse: (accel) set acceleration profile 0
(II) Genius Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```Espero respuestas,

Gracias!
Ahi te marque en rojo los errores que esta dando el inicio del X-server con ese driver y esa placa. La placa queda configurada con aceleracion 2D solamente porque cuando inicializa la aceleracion 3D falla.

Pregunta medio tonta: Estara funcionando bien esa placa ?

---

### Post by axelbrz on 2009-10-13
Je, no es una pregunta tonta, últimamente cada tanto me aparecen píxeles misteriosos volando por ahí.. y lo mismo en la consola, sólo que en vez de píxeles el problema está en que algunas letras me aparecen de colores, y otras son reemplazadas por otros caracteres :P

En windows me pasa lo mismo, pero en windows me funciona bien la aceleración gráfica, y estos píxeles aparecen desde hace muy poco, y el problema de la suspención del monitor ya hace bastante..

De todas formas, ¿se puede asumir que la placa anda bien y seguir viendo cuál es el problema? Porque si la placa llegase a funcionar bien, y nos quedamos con "anda mal la placa" nunca voy a terminar de resolver el problema :(

En fin, qué más necesitan para seguir buscando el problema?

---

### Post by guillermolisi on 2009-10-13
> **axelbrz said:**
> Je, no es una pregunta tonta, últimamente cada tanto me aparecen píxeles misteriosos volando por ahí.. y lo mismo en la consola, sólo que en vez de píxeles el problema está en que algunas letras me aparecen de colores, y otras son reemplazadas por otros caracteres :P

En windows me pasa lo mismo, pero en windows me funciona bien la aceleración gráfica, y estos píxeles aparecen desde hace muy poco, y el problema de la suspención del monitor ya hace bastante..

De todas formas, ¿se puede asumir que la placa anda bien y seguir viendo cuál es el problema? Porque si la placa llegase a funcionar bien, y nos quedamos con "anda mal la placa" nunca voy a terminar de resolver el problema :(

En fin, qué más necesitan para seguir buscando el problema?
Entiendo tu punto pero es que podemos quemarnos la cabeza probando drivers, configuraciones, versiones de kernels, etc. y puede que todo se resuma en un chip de memoria fallido en la placa de video. Muy sugestivo lo que decis de los pixeles y las letras, inclusive en Windows.

Me gustaria ver alguna opinion mas al respecto.

---

### Post by pablo.s on 2009-10-13
> **guillermolisi said:**
>  Muy sugestivo lo que decis de los pixeles y las letras, inclusive en Windows.
Me gustaria ver alguna opinion mas al respecto.

Concuerdo con Guille. 
No es para nada normal que
muestre errores asi.
¿Es nueva la placa?

---

### Post by axelbrz on 2009-10-13
Nop, la debo tener hace unos 2 o 3 años más o menos..

¿Pero no se puede hacer algo para que los errores que aparecen se arreglen? ¿Tocando algún archivo de configuración? ¿Algo?

Hace un tiempo Ubuntu me funcionaba bárbaro, inclusive con XGL, luego lo dejé de usar por unos años, y ahora el nuevo Ubuntu me trajo este problemita.. La placa de video era la misma en ese entonces..

---

### Post by guillermolisi on 2009-10-13
> **axelbrz said:**
> Nop, la debo tener hace unos 2 o 3 años más o menos..

¿Pero no se puede hacer algo para que los errores que aparecen se arreglen? ¿Tocando algún archivo de configuración? ¿Algo?

Hace un tiempo Ubuntu me funcionaba bárbaro, inclusive con XGL, luego lo dejé de usar por unos años, y ahora el nuevo Ubuntu me trajo este problemita.. La placa de video era la misma en ese entonces..
O sea que esa placa estuvo guardada sin usar por unos años ?
Y cuando comenzo a "fallar" con Windows, antes o despues de usarla con Ubuntu ?

---

### Post by staar on 2009-10-13
si los artifacts te aparecen incluso en Ventanas, es casi seguro un problema de hardware, y desconozco (y dudo mucho) si existe alguna forma de solucionarlos desde el lado de los drivers/configuración...

los drivers de linux y Ventanas funcionan, y están en un grado de desarrollo, diferente, por eso existen casos donde un hardware defectuoso "funciona", relativamente, en un sistema y no en el otro...

chequeaste la temperatura de la placa cuando te salen los errores? la pc está limpia por dentro? el cooler de la placa anda bien? la fuente?

saludos

---

### Post by mama21mama on 2009-10-14
[instala NVIDIA v185.18.36 ]("http://mamalibre.eshost.com.ar/?q=node/30")

es el que uso y anda joya en mi jaunty.

---

### Post by axelbrz on 2009-10-14
> **mama21mama said:**
> [instala NVIDIA v185.18.36 ]("http://mamalibre.eshost.com.ar/?q=node/30")

es el que uso y anda joya en mi jaunty.
Es el que instalé..

Hace un tiempo la placa me calentaba mucho, abrí la compu, limpié la placa (estaba llena de polvo jeje), y nunca más subió de temperatura.. pero tuve el gabinete un tiempo abierto y seguro que la placa está llena de polvo otra vez..

Estos días abro la compu y limpio la placa, y esperaré a ver si con eso se soluciona.. les aviso cuando lo haga!

Muchas gracias por todo!

---

