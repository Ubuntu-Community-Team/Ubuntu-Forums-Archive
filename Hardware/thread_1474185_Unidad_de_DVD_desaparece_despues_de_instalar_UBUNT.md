---
title: "Unidad de DVD desaparece despues de instalar UBUNTU 10.4"
date: 2010-05-05
forum: Hardware
---

### Post by jolfig on 2010-05-05
Datos del Notebook: Lenovo 3000 N200 Type 0687-2ES
[INDENT]T2310(1.46GHz), 1GB RAM, 120GB 5400rpm HD, 14.1in 1280x800, Intel X3100, CDRW/DVDRW, 802.11bg wireless, Modem, 10/100 Ethernet, Touchpad, Secure chip, Camera, 6c Li-Ion, WinVista Home Basic[/INDENT]


Es recurrente el error producido en varios notebooks (en mi caso el  Lenovo 3000 N200), en donde desaparece la unidad de DVD después de la instalación. En configuraciones de arranque dual (Ubuntu + Windows) la unidad de DVD también desaparece del Windows


**_Aspectos Técnicos:_**
[LIST=1]
[*]El AHPI (Advanced Host Controller Interface), es una interfaz de programación de aplicaciones definida por Intel, que define el funcionamiento de los adaptadores de bus Serial ATA, de una manera sin-implementacion-específica (non-implementation-specific). La especificación describe una estructura de memoria del sistema,(para los fabricantes de hardware informático), para el intercambio de datos entre la memoria del sistema host y los dispositivos de almacenamiento conectados. Muchos controladores SATA ofrecen modos de operación seleccionables: Emulación del legado Parallel ATA, el modo AHCI estándar, o vendedor-RAID específica. Intel recomienda seleccionar el modo RAID en sus placas madre (que también permite AHCI) en lugar del modo AHCI/SATA para una máxima flexibilidad, debido a los problemas causados cuando el modo se cambia una vez que un sistema operativo ya se ha instalado.

[INDENT][LIST]Este Notebook viene con un disco duro tipo SATA1 (Seagate Momentus 5400.3) con opciones de modos de controlador SATA configurables a AHPI/Compatibilidad en la BIOS; y un grabador de DVD ATA (Matshita UJ-850S). Acá hay una combinación de dispositivos SATA - ATA.[/LIST][/INDENT]
[*]**GRUB** (grub, grub2) no funciona con BIOS que usan el modo AHCI para discos SATA. Si lo hace, presenta errores perdiendo "particiones" al escribir el código de arranque. Revertir al modo Compatibility IDE Legacy, parece ser una solución teórica (pero ralentiza las unidades y hace aumentar la temperatura del notebook a niveles peligrosos).
[INDENT][LIST]En el caso de este notebook (y muchos otros) que usan chipsets de Intel en modo AHPI (Force mode APHI enabled), **se pierde el lector de DVD/CD**. Antes de forzar el modo APHI existe un "dispositivo" que ve los 2 canales SATA, y los 2 canales IDE. Cuando se fuerza el modo AHCI, este dispositivo se convierte en el controlador de AHCI (que cambia la ID del dispositivo), y el controlador IDE aparecerá como un nuevo dispositivo aparte (con otra ID de dispositivo), pero está deshabilitado. Hay registros en el ICH8 que permiten establecer estados activado/desactivado, pero de acuerdo a la documentación, no se debe permitir activar un dispositivo después de que ha sido desactivado. En la práctica, no pude conseguir volver a habilitar el CD-ROM.[/LIST][/INDENT]
[/LIST]


**_Consideraciones que hay que tomar en cuenta_**:
[LIST=1]
[*]No sirve actualizar la BIOS porque el error se mantiene, el problema es el grub2.
[*]Por lo tanto en este tipo de computadores, NO DEBEMOS MANTENER GRUB como gestor de arranque, deberemos **reemplazarlo por LILO**.
[*]Otro aspecto importante a tener en cuenta es que aunque el hardware soporta perfectamente la versión AMD64 y debe ser la elección natural si tienes más de 3 GB de RAM (como en mi caso), pero el soporte para periféricos (impresoras, escáners, y otros dispositivos) no es completo. Por lo tanto, si tienes menos de 3 GB en RAM, puedes instalar la versión i386, para no toparte con sorpresas más adelante.[/LIST]

Después de ese marco teórico necesario, manos a la obra:

[LIST=1]

[*]Para cambiar el gestor de arranque de GRUB a LILO, deberemos hacer lo siguiente:
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

Con eso tendremos funcionando nuevamente la unidad de DVD de éste notebook. Dió algún trabajo, pero nada del otro mundo.

Saludos

José Luis Figueroa (JoLFiG)

---

### Post by Carlos C on 2010-05-06
Buenísimo, gracias por el aporte.

---

### Post by svillega on 2010-05-12
tenia ese mismo problema, despues de instalar ubuntu 10.4 la unidad de dvd no me aparece pero......

tengo un problemita con esto, hice todo lo que decian arriba pensando que esto me solucionaria mi problema con la unidad de dvd pero no se que paso, es la primera ves que uso el lilo y ya no me deja bootiar el linux me manda directamente al windows , si me pueden ayudar se lo agredeciera eternamente no soporto estar en windows me siento como un pendejo aqui.

mil gracias

---

### Post by jolfig on 2010-08-05
Al parecer LiLo no se instaló.
Prueba lo siguiente:
Cuando se inicia el Boteo presiona la flecha hacia abajo (de las teclas para mover el cursor)
Si es que no te aparece el menu de LiLo entonces el LiLo no esta instalado correctamente.
Es importante que no olives las instrucciones:

    * sudo lilo -M /dev/sda mbr

    * Y luego:

      sudo lilo

Para corregir el problema inicia con el CD de Ubuntu y elige la opción reparación de un sistema dañado.
Te permitirá elegir entre LiLo y Grub aunque lo más probable es que te instale de nuevo el Grub.

Vuelve a seguir el turorial paso a paso sin omitir nada.

Saludos

JoLFiG

---

