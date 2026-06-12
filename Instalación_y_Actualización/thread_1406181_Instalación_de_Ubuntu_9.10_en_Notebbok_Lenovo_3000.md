---
title: "Instalación de Ubuntu 9.10 en Notebbok Lenovo 3000 N200 0687-2ES"
date: 2010-02-13
forum: Instalación y Actualización
---

### Post by jolfig on 2010-02-13
Configuración Original: 
[INDENT]T2310(1.46GHz), 1GB RAM, 120GB 5400rpm HD, 14.1in 1280x800, Intel X3100, CDRW/DVDRW, 802.11bg wireless, Modem, 10/100 Ethernet, Touchpad, Secure chip, Camera, 6c Li-Ion, WinVista Home Basic[/INDENT]


Despues de haber experimentado con las versiones 8.04 8.10 9.04 y con varias configuraciones me animé a realizar una **instalación limpia** de Ubuntu 9.10


**_Aspectos Técnicos:_**
[LIST=1]
[*]El AHPI (Advanced Host Controller Interface), es una interfaz de programación de aplicaciones definida por Intel, que define el funcionamiento de los adaptadores de bus Serial ATA, de una manera sin-implementacion-específica (non-implementation-specific). La especificación describe una estructura de memoria del sistema, para los fabricantes de hardware informático, para el intercambio de datos entre la memoria del sistema host y los dispositivos de almacenamiento conectados. Muchos controladores SATA ofrecen modos de operación seleccionables: Emulación del legado Parallel ATA, el modo AHCI estándar, o vendedor-RAID específica. Intel recomienda seleccionar el modo RAID en sus placas madre (que también permite AHCI) en lugar del modo AHCI/SATA para una máxima flexibilidad, debido a los problemas causados cuando el modo se cambia una vez que un sistema operativo ya se ha instalado.

[INDENT][LIST]Este Notebook viene con un disco duro tipo SATA1 (Seagate Momentus 5400.3) con opciones de modos de controlador SATA configurables a AHPI/Compatibilidad en la BIOS; y un grabador de DVD ATA (Matshita UJ-850S). Acá hay una combinación de dispositivos SATA - ATA.[/LIST][/INDENT]
[*]**GRUB** (grub, grub2) no funciona con BIOS que usan el modo AHCI para discos SATA. Si lo hace, presenta errores perdiendo "particiones" al escribir el código de arranque. Revertir al modo Compatibility IDE Legacy, parece ser una solución teórica (pero ralentiza las unidades y hace aumentar la temperatura del notebook a niveles peligrosos).
[INDENT][LIST]En el caso de este notebook (y muchos otros) que usan chipsets de Intel en modo AHPI (Force mode APHI enabled), **se pierde el lector de DVD/CD**. Antes de forzar el modo APHI existe un "dispositivo" que ve los 2 canales SATA, y los 2 canales IDE. Cuando se fuerza el modo AHCI, este dispositivo se convierte en el controlador de AHCI (que cambia la ID del dispositivo), y el controlador IDE aparecerá como un nuevo dispositivo aparte (con otra ID de dispositivo), pero está deshabilitado. Hay registros en el ICH8 que permiten establecer estados activado/desactivado, pero de acuerdo a la documentación, no se debe permitir activar un dispositivo después de que ha sido desactivado. En la práctica, no pude conseguir volver a habilitar el CD-ROM.[/LIST][/INDENT]
[/LIST]


**_Consideraciones que hay que tomar en cuenta_**:
[LIST=1]
[*]No sirve actualizar la BIOS porque el error se mantiene, el problema es el grub2.
[*]Por lo tanto en este tipo de computadores, NO DEBEMOS MANTENER GRUB como gestor de arranque, deberemos **reemplazarlo por LILO**.
[*]Otro aspecto importante a tener en cuenta es que aunque el hardware soporta perfectamente la versión AMD64 y debe ser la eleccion natural si tienes más de 3 GB de RAM (como en mi caso), pero el soporte para periféricos (impresoras, escáners, y otros dispositivos) no es completo. Por lo tanto, si tienes menos de 3 GB en RAM, puedes instalar la versión i386, para no toparte con sorpresas más adelante.[/LIST]

Después de ese marco teórico necesario, manos a la obra:

[LIST=1]
[*]Descargamos y grabamos el CD de Ubuntu 9.10
[INDENT][LIST]Instalamos cambiando idioma a español, (en mi caso también, el país a Chile y el teclado a Latinoamericano). Al momento de particionar el disco le indicamos que ocupe todo el disco para la instalación. Esto borrará las particiones de fábrica ocultas que trae el notebook y limpiará el Windows Vista Home. Es buena idea aceptar las particiones propuestas si no se tiene mucha experiencia. (En mi caso como aumenté la RAM de 1 a 4 GB y deseaba tener el /home aparte, tuve que crear 3 particiones: Una de 37,6 GB ext4 para /, otra de 4,6 Gb para intercambio y otra de 70 GB ext4 para /home). [/LIST]
[LIST]El proceso e instalación creará un usuario, y una contraseña maestra. Al finalizar la instalación tendremos un sistema base funcional, pero por lo que explicamos líneas arriba ya no podremos leer nada en el DVD.[/LIST]

[LIST]En primer lugar deberemos activar el controlador de red inalámbrica, y eso se consiguede una manera bastante sencilla.[/LIST]
[LIST]Conecta un cable de red al puerto ethernet y verifica que tengas conexión a internet. (Abre el Firefox y usa el google)[/LIST]
[LIST]En Sistema/Administracion/Controladores de Hardware deberás escoger Broadcom B43 wirless driver. (Es preferible escoger la opcion que trae el fwcutter, por si más adelante deseas poner el controlador wirless en modo promiscuo.) Luego haces clic en el botón activar y listo... ya tendrás la tarjeta de red inalámbrica funcionado. Te queda simplemente conectarla a tu servicio de internet escogiendo tu red inalámbrica y digitando la contraseña.[/LIST]
[LIST]En Sistema/Administración/Soporte de Idiomas, te permitirá descargar las traducciones de los programas instalados.[/LIST][/INDENT]
[*]Luego actualizamos el sistema: Sistema/Administración/Gestor de Actualizaciones.
[INDENT][LIST]Descarga todas las actualizaciones disponibles, acutalizará el software y el núcleo del kernel a la versión más reciente.[/LIST]
[LIST]Reiniciamos el sistema e iniciamos sesión nuevamente[/LIST][/INDENT]

[*]Ahora la parte más importante, cambiamos el gestor de arranque de GRUB a LILO, para ello deberemos hacer lo siguiente:
[INDENT][LIST]Abrimos una consola (Aplicaciones/Accesorios/Terminal) y digitamos lo siguiente: (en el terminal para "pegar" las instrucciones lo puedes hacer con Ctrl+Mayus+v)
sudo apt-get remove grub-pc
sudo apt-get update
sudo apt-get install lilo
sudo apt-get install lilo-doc
sudo apt-get install mbr[/LIST]
[LIST]Deberás crear/editar el lilo.conf (sudo gedit /etc/lilo.conf) y copia o reemplázalo por lo siguiente:```


# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
    # ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
    #                       and `/usr/share/doc/mbr/'.
 
    # +---------------------------------------------------------------+
    # |                        !! Reminder !!                         |
    # |                                                               |
    # | Don't forget to run `lilo' after you make changes to this     |
    # | conffile, `/boot/bootmess.txt', or install a new kernel.  The |
    # | computer will most likely fail to boot if a kernel-image      |
    # | post-install script or you don't remember to run `lilo'.      |
    # |                                                               |
    # +---------------------------------------------------------------+
 
    # Support LBA for large hard disks.
    #
    lba32
 
    # Specifies the boot device.  This is where Lilo installs its boot
    # block.  It can be either a partition, or the raw device, in which
    # case it installs in the MBR, and will overwrite the current MBR.
    #
    boot=/dev/sda1
 
    # Specifies the device that should be mounted as root. (`/')
    #
    root=/dev/sda1
 
    # Enable map compaction:
    # Tries to merge read requests for adjacent sectors into a single
    # read request. This drastically reduces load time and keeps the
    # map smaller.  Using `compact' is especially recommended when
    # booting from a floppy disk.  It is disabled here by default
    # because it doesn't always work.
    #
    compact
 
    # Installs the specified file as the new boot sector
    #
    # install=/boot/boot.b
 
    # Specifies the location of the map file
    #
    # map=/boot/map
 
    # You can set a password here, and uncomment the `restricted' lines
    # in the image definitions below to make it so that a password must
    # be typed to boot anything but a default configuration.  If a
    # command line is given, other than one specified by an `append'
    # statement in `lilo.conf', the password will be required, but a
    # standard default boot will not require one.
    #
    # This will, for instance, prevent anyone with access to the
    # console from booting with something like `Linux init=/bin/sh',
    # and thus becoming `root' without proper authorization.
    #
    # Note that if you really need this type of security, you will
    # likely also want to use `install-mbr' to reconfigure the MBR
    # program, as well as set up your BIOS to disallow booting from
    # removable disk or CD-ROM, then put a password on getting into the
    # BIOS configuration as well.  Please RTFM `install-mbr(8)'.
    #
    # password=tatercounter2000
 
    # Specifies the number of deciseconds (0.1 seconds) LILO should
    # wait before booting the first image.
    #
    # delay=20
 
    # You can put a customized boot message up if you like.  If you use
    # `prompt', and this computer may need to reboot unattended, you
    # must specify a `timeout', or it will sit there forever waiting
    # for a keypress.  `single-key' goes with the `alias' lines in the
    # `image' configurations below.  eg: You can press `1' to boot
    # `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
    #
    # message=/boot/bootmess.txt
        prompt
    #       single-key
           delay=100
           timeout=100
 
    # Specifies the VGA text mode at boot time. (normal, extended, ask, )
    #
    # vga=9
    #
    vga=normal
 
    # Kernel command line options that apply to all installed images go
    # here.  See: The `boot-prompt-HOWO' and `kernel-parameters.txt' in
    # the Linux kernel `Documentation' directory.
    #
    # append=""
 
    # Boot up Linux by default.
    #
    default=Linux
 
    image=/vmlinuz
            label=Linux
            read-only
    #       restricted
    #       alias=1
 
    image=/vmlinuz.old
            label=LinuxOLD
            read-only
            optional
    #       restricted
    #       alias=2
 
    # If you have another OS on this machine to boot, you can uncomment the
    # following lines, changing the device name on the `other' line to
    # where your other OS' partition is.
    #
    # other=/dev/hda1
    #        label=FreeBSD
    #       restricted
    #       alias=3


```[/LIST]
[LIST]Luego:

sudo lilo -M /dev/sda mbr[/LIST]
[LIST]Y luego:

sudo lilo[/LIST] 
[LIST]Reinicias el sistema y con LILO como gestor de arranque tendrás funcionanado el DVD de nuevo.[/LIST][/INDENT]
[/LIST]

Con eso tendremos funcionando este notebook. Dió algún trabajo, pero nada del otro mundo.

Saludos desde Calama

José Luis Figueroa (JoLFiG)

---

### Post by Scorpion8491 on 2010-04-13
Muchas gracias funcionó de lujo en lucid :P

---

### Post by niustid on 2010-10-18
Exeletente!!! me funciono muy bien te agradezco mucho!

---

### Post by jldiaz29 on 2011-09-06
Hola, bueno este es mi primer post aqui y al parecer hace mucho tiempo que nadie continuo este tema.

Tengo un Notebbok Lenovo 3000 N200 y le acabo de instalar el Ubuntu 10.04

Es posible hacer funcionar la camara web de este equipo con este OS?

Muchas gracias de ante mano, y cordiales saludos.

- JLDiaz

---

### Post by asterix77 on 2011-09-06
pues si, claro que depende del modelo de webcam que tengas, pero en general esta bien soportado

Yo tengo lucid (10.04), que en algún momento le instalé una webcam usb un poco antigua que tenía, y me funcionó. Eso fue hace un tiempo, la resolución no era muy buena, pero funcionaba.

Ahora uso la cámara de mi teléfono como webcam, con mejor resolución, mejor calidad, y ..... sin cables, ya que se conecta mediante bluetooth

[http://www.linlap.com/wiki/lenovo+3000+n200](http://www.linlap.com/wiki/lenovo+3000+n200) en ese link indica que si es soportada la camara web e incluso te da el link del driver

[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

Para ubuntu acá hay algo más especifico  [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

para más detalles abre una terminal, y pega la salida de los siguientes comandos

lspci
lsusb

para ver si te reconoce la cámara.

Saludos.  

PD: creo que deberías iniciar un nuevo post tal vez en la sección hardware

---

### Post by jldiaz29 on 2011-09-13
> **asterix77 said:**
> pues si, claro que depende del modelo de webcam que tengas, pero en general esta bien soportado

Yo tengo lucid (10.04), que en algún momento le instalé una webcam usb un poco antigua que tenía, y me funcionó. Eso fue hace un tiempo, la resolución no era muy buena, pero funcionaba.

Ahora uso la cámara de mi teléfono como webcam, con mejor resolución, mejor calidad, y ..... sin cables, ya que se conecta mediante bluetooth

[http://www.linlap.com/wiki/lenovo+3000+n200](http://www.linlap.com/wiki/lenovo+3000+n200) en ese link indica que si es soportada la camara web e incluso te da el link del driver

[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

Para ubuntu acá hay algo más especifico  [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

para más detalles abre una terminal, y pega la salida de los siguientes comandos

lspci
lsusb

para ver si te reconoce la cámara.

Saludos.  

PD: creo que deberías iniciar un nuevo post tal vez en la sección hardware

Oye muchas gracias por tu respuesta estimado, visite la pagina y ejecute estos codigos de abajo en la terminal

git clone git://linuxtv.org/media_build.git --*esto descargo algo*
cd media_build --*se creo esta carpeta*
./build   -- *esto no se que significa*
make install -- e*sto da un error*

Tendre que seguir intentando de algun modo, el error que dio fue este..


make[2]: Entering directory `/home/jldiaz/media_build/v4l/firmware'
make[2]: *** No rule to make target `../../linux/firmware/ihex2fw.c', needed by `ihex2fw'.  Stop.
make[2]: Leaving directory `/home/jldiaz/media_build/v4l/firmware'
make[1]: *** [firmware_install] Error 2
make[1]: Leaving directory `/home/jldiaz/media_build/v4l'
make: *** [install] Error 2
root@ubuntu:/home/jldiaz/media_build# 


No se si tu sabes interpretar eso, pero gracias por el dato igual..

Slds!
Jose Luis

---

