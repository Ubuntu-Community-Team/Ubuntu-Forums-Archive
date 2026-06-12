---
title: "Instalar driver modem pci"
date: 2008-01-09
forum: Hardware
---

### Post by .NicK_LoVe on 2008-01-09
Hola, necesito ayuda por favor!!!!

El tema es el siguiente: Tengo un modem 56k pci Encore con chip NetoDragon y no se como configurarlo para q funcione en ubuntu, me baje el driver para linux pero no entiendo bien las instrucciones (sobre todo el punto 3).
Esto es lo q aparece en las instrucciones:

Installation
============

1. Unpack tar.gz package file:

	$ gzip -dc slmdm-2.X.X.tar.gz | tar xf -

2. 'cd' to package directory:

	$ cd slmdm-2.X.X

3. Review and edit (if need) 'Makefile'.

   Note: Probably you will want to correct in Makefile path to your
         local linux kernel header files:

         	KERNEL_INCLUDES=/path/to/linux/include

         Another way is to pass command line the parameter while
         running 'make':

         	$ make KERNEL_INCLUDES=/path/to/linux/include ...

4. Run 'make' command to compile package:

	$ make

5. Install.

   If you are going to use AMR/CNR/PCI modem type (as superuser):

	# make install-amr

   , or 

	# make install-usb

   if you are going to use USB modem.

   It will install:
   - modem kernel modules slmdm.o (modem core), slfax.o (fax)
     into '/lib/modules/<kernel-version>/misc' directory
     (standard linux modules' directory).
   - hardware specific kernel module slamrmo.o (for AMR/CNR/PCI) or
     slusb.o (for USB) into '/lib/modules/<kernel-version>/misc'
     directory (standard linux modules' directory).
   - country settings data file 'country.dat' into directory '/etc'.

   Also it will:
   - create character tty device entry '/dev/ttySL0' with major
     number 212 and symbolic link 'dev/modem'.
   - config you '/etc/modules.conf' file in order to provide
     possibility for loading the modem modules into kernel on demand
     automatically by kmod, when you are going to use them.

   Note: currently you cannot use both AMR/CNR/PCI and USB Modems.

6. Config modem country.

   You can configure your current country by using module parameters
   'country' or 'country_code'.
   Add 'options' directive line to file '/etc/modules.conf':

	options slmdm country=<MyCountry>

   , for example

	options slmdm country=USA

   , or use module parameter while module loading:

	# modprobe slmdm country=<MyCountry>

   Use 'slver -c' to see list of all supported countries and their
   codes (utility 'slver' may be found in package directory).

   Note: Command ATI7 shows installed country setting.

7. Using the modem.

   Installation will automatically create character tty device entry
   '/dev/ttySL0' with major number 212 and symbolic link '/dev/modem'.
   Use one of them as modem device for your dialing application.

8. Uninstallation.

   In package directory just type:

	# make uninstall

Espero q puedan ayudarme, saludos!!!!!!!!!!!

---

### Post by faktorqm on 2008-01-10
Creo que estan aca, en "/usr/src/linux-headers-2.6.20-16/include", ese es para el mio, para cualquier kernel podes hacer ```
/usr/src/$(uname -r)/include
``` o tb ```
/usr/src/`uname -r`/include
```
el paso 3 dice que si necesitas podes rever o editar el archivo "Makefile", que adentro de ese archivo le podes setear el directorio de arriba o sino tambien cuando llamas al make con el comando que te pone ahi.

Entonces, el paso 3 obvialo, salta al 4 que seria algo asi digamos (sin editar nada) 
```
make KERNEL_INCLUDES=/usr/src/$(uname -r)/include --prefix=/usr
```
(respeta mayusculas y minusculas)

En el paso 5 recordar ser root o poner sudo, es lo mismo. salu2!!

---

### Post by .NicK_LoVe on 2008-01-10
:~/Escritorio/slmdm-2.7.10_debug$ make KERNEL_INCLUDES=/usr/src/$(uname -r)/include --prefix=/usr
make: opción desconocida `--prefix=/usr'
Modo de empleo: make [opciones] [objetivo] ...
Opciones:
  -b, -m                      No se tendrá en cuenta por compatibilidad.
  -B, --always-make           Hace incondicionalmente todos los objetivos.
  -C DIRECTORIO, --directory=DIRECTORIO
                              Se cambia al DIRECTORIO antes de hacer nada.
  -d          Se imprimirán grandes cantidades de información de depurado.
  --debug[=BANDERAS]    Se imprimirán varios tipos de información de depurado.
  -e, --environment-overrides
                Las variables ambientales se imponen a las de los makefiles.
  -f ARCHIVO, --file=ARCHIVO, --makefile=ARCHIVO
                                   Lee al ARCHIVO como un makefile.
  -h, --help                  Muestra este mensaje y finaliza.
  -i, --ignore-errors         No se toman en cuenta los errores provenientes de las instrucciones.
  -I DIRECTORIO, --include-dir=DIRECTORIO
                       Busca dentro del DIRECTORIO los makefiles incluidos.
  -j [N], --jobs[=N]      Se permiten N trabajos a la vez; si no se especifica un
argumento son infinitos.
  -k, --keep-going            Sigue avanzando aún cuando no se puedan crear algunos objetivos.
  -l [N], --load-average[=N], --max-load[=N]
      No inicia con trabajos múltiples a menos que la carga esté por debajo de N.
  -L, --check-symlink-times   Utiliza el último mtime entre los enlaces simbólicos y los objetivos.
  -n, --just-print, --dry-run, --recon
                              No ejecuta ninguna instrucción; sólo las muestra.
  -o ARCHIVO, --old-file=ARCHIVO, --assume-old=ARCHIVO
                           Supone que ARCHIVO es muy viejo y no lo reconstruye.
  -p, --print-data-base       Se imprime la base de datos interna de `make'.
  -q, --question                     No se ejecutan las instrucciones; el estado de salida
indicará si están actualizados.
  -r, --no-builtin-rules      Se deshabilitan las reglas implícitas almacenadas internamente.
  -R, --no-builtin-variables  Se deshabilitan los ajustes a las variables almacenadas internamente.
  -s, --silent, --quiet       No muestra las intrucciones.
  -S, --no-keep-going, --stop
                    Desactiva la opción -k.
  -t, --touch                 Se tocan los objetivos en vez de reconstruirlos.
  -v, --version               Muestra la versión del make y finaliza.
  -w, --print-directory       Muestra el directorio actual.
  --no-print-directory        Desactiva -w, aún cuando haya sido activado implícitamente.
  -W ARCHIVO, --what-if=ARCHIVO, --new-file=ARCHIVO, --assume-new=ARCHIVO
                               Supone que ARCHIVO es infinitamente reciente.
  --warn-undefined-variables  Advierte cuando se hace una referencia a una variable no definida.

Este programa fue construido para x86_64-pc-linux-gnu
Informe sobre los errores a <bug-make@gnu.org>



Esto es lo q me aparece cuando pongo make KERNEL_INCLUDES=/usr/src/$(uname -r)/include --prefix=/usr

Que estoy haciendo mal???

---

### Post by .NicK_LoVe on 2008-01-11
Ayuda!!!

---

### Post by faktorqm on 2008-01-11
perdon, me colgue del cable :P

```
make KERNEL_INCLUDES=/usr/src/$(uname -r)/include
```

hace eso sin el prefix. La verdad no se que paso con eso, lo sacaron? ya no era necesario? algun programador que me tire una ayuda? salu2!

---

### Post by .NicK_LoVe on 2008-01-12
Todo bien, de paso me sirvió un poco para buscar en la web ;)

Esto es lo q  me aparece cuando pongo:

 make KERNEL_INCLUDES=/usr/src/$(uname -r)/include

:~/Escritorio/slmdm-2.7.10_debug$ make KERNEL_INCLUDES=/usr/src/$(uname -r)/include
gcc -Wall -O3 -fomit-frame-pointer -D__KERNEL__ -DMODULE -DEXPORT_SYMTAB -I. -I/usr/src/2.6.22-14-generic/include  -DMODVERSIONS --include /usr/src/2.6.22-14-generic/include/linux/modversions.h -DMODEM_DEBUG=1 -o sllog.o -c sllog.c
cc1: error: /usr/src/2.6.22-14-generic/include/linux/modversions.h: No existe el fichero ó directorio
sllog.c:47:26: error: linux/module.h: No existe el fichero ó directorio
sllog.c:49:24: error: linux/init.h: No existe el fichero ó directorio
sllog.c:50:30: error: linux/miscdevice.h: No existe el fichero ó directorio
sllog.c:51:24: error: linux/slab.h: No existe el fichero ó directorio
sllog.c:52:26: error: linux/string.h: No existe el fichero ó directorio
sllog.c:53:26: error: linux/bitops.h: No existe el fichero ó directorio
sllog.c:56:29: error: linux/interrupt.h: No existe el fichero ó directorio
sllog.c:59:25: error: asm/uaccess.h: No existe el fichero ó directorio
sllog.c:73: error: expected specifier-qualifier-list before ‘wait_queue_head_t’
sllog.c:87: error: expected ‘)’ before string constant
sllog.c:88: error: expected ‘)’ before string constant
sllog.c:91: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sllog_lock’
sllog.c: En la función ‘log_data’:
sllog.c:103: error: ‘struct sllog’ no tiene un miembro llamado ‘mon’
sllog.c:105: error: ‘struct sllog’ no tiene un miembro llamado ‘log_mask’
sllog.c:108: aviso: declaración implícita de la función ‘test_bit’
sllog.c:108: error: ‘struct sllog’ no tiene un miembro llamado ‘log_mask’
sllog.c:115: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:115: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:116: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:116: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:118: aviso: conversión de puntero a entero de tamaño diferente
sllog.c:124: aviso: conversión de puntero a entero de tamaño diferente
sllog.c:133: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:133: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:134: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:134: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:138: aviso: declaración implícita de la función ‘memcpy’
sllog.c:138: aviso: declaración implícita incompatible de la función interna ‘memcpy’
sllog.c:138: error: ‘struct sllog’ no tiene un miembro llamado ‘buf’
sllog.c:138: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:142: aviso: declaración implícita incompatible de la función interna ‘memcpy’
sllog.c:142: error: ‘struct sllog’ no tiene un miembro llamado ‘buf’
sllog.c:142: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:147: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:148: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:148: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:148: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:151: aviso: declaración implícita de la función ‘wake_up_interruptible’
sllog.c:151: error: ‘struct sllog’ no tiene un miembro llamado ‘wait’
sllog.c: En la función ‘modem_debug_log_data’:
sllog.c:160: aviso: declaración implícita de la función ‘spin_lock_irqsave’
sllog.c:160: error: ‘sllog_lock’ no se declaró aquí (primer uso en esta función)
sllog.c:160: error: (Cada identificador no declarado solamente se reporta una vez
sllog.c:160: error: ara cada funcion en la que aparece.)
sllog.c:161: error: ‘struct sllog’ no tiene un miembro llamado ‘mon’
sllog.c:164: aviso: declaración implícita de la función ‘spin_unlock_irqrestore’
sllog.c: En la función ‘sllog_vprintf’:
sllog.c:180: aviso: declaración implícita de la función ‘strlen’
sllog.c:180: aviso: declaración implícita incompatible de la función interna ‘strlen’
sllog.c:183: aviso: declaración implícita de la función ‘do_gettimeofday’
sllog.c:187: error: l-valor inválido en incremento
sllog.c:198: error: ‘struct sllog’ no tiene un miembro llamado ‘temp’
sllog.c:201: aviso: declaración implícita de la función ‘sprintf’
sllog.c:201: aviso: declaración implícita incompatible de la función interna ‘sprintf’
sllog.c:202: aviso: declaración implícita de la función ‘in_interrupt’
sllog.c:206: aviso: declaración implícita de la función ‘vsprintf’
sllog.c:209: error: ‘struct sllog’ no tiene un miembro llamado ‘temp’
sllog.c:210: error: ‘struct sllog’ no tiene un miembro llamado ‘temp’
sllog.c:213: aviso: declaración implícita de la función ‘printk’
sllog.c:213: error: ‘struct sllog’ no tiene un miembro llamado ‘temp’
sllog.c:215: error: ‘struct sllog’ no tiene un miembro llamado ‘mon’
sllog.c:216: error: ‘struct sllog’ no tiene un miembro llamado ‘temp’
sllog.c:223: error: ‘struct sllog’ no tiene un miembro llamado ‘temp’
sllog.c:227: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:227: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:228: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:228: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:229: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:229: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:230: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:230: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:233: aviso: declaración implícita incompatible de la función interna ‘memcpy’
sllog.c:233: error: ‘struct sllog’ no tiene un miembro llamado ‘buf’
sllog.c:233: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:237: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:237: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:237: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:238: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:241: error: ‘struct sllog’ no tiene un miembro llamado ‘wait’
sllog.c: En la función ‘modem_debug_printf’:
sllog.c:255: error: ‘sllog_lock’ no se declaró aquí (primer uso en esta función)
sllog.c: En el nivel principal:
sllog.c:273: aviso: se declaró ‘struct file’ dentro de la lista de parámetros
sllog.c:273: aviso: su ámbito es solamente esta definición o declaración, lo cual probablemente no sea lo que desea
sllog.c:273: aviso: se declaró ‘struct inode’ dentro de la lista de parámetros
sllog.c: En la función ‘sllog_open’:
sllog.c:279: error: ‘EBUSY’ no se declaró aquí (primer uso en esta función)
sllog.c:281: error: ‘MOD_INC_USE_COUNT’ no se declaró aquí (primer uso en esta función)
sllog.c:282: aviso: declaración implícita de la función ‘kmalloc’
sllog.c:282: error: ‘GFP_KERNEL’ no se declaró aquí (primer uso en esta función)
sllog.c:282: aviso: la asignación crea un puntero desde un entero sin una conversión
sllog.c:284: error: ‘MOD_DEC_USE_COUNT’ no se declaró aquí (primer uso en esta función)
sllog.c:285: error: ‘ENOMEM’ no se declaró aquí (primer uso en esta función)
sllog.c:287: aviso: declaración implícita de la función ‘memset’
sllog.c:287: aviso: declaración implícita incompatible de la función interna ‘memset’
sllog.c:288: error: ‘struct sllog’ no tiene un miembro llamado ‘buf’
sllog.c:288: aviso: declaración implícita de la función ‘__get_free_pages’
sllog.c:288: aviso: conversión a puntero desde un entero de tamaño diferente
sllog.c:289: error: ‘struct sllog’ no tiene un miembro llamado ‘buf’
sllog.c:290: aviso: declaración implícita de la función ‘kfree’
sllog.c:294: aviso: declaración implícita de la función ‘init_waitqueue_head’
sllog.c:294: error: ‘struct sllog’ no tiene un miembro llamado ‘wait’
sllog.c:295: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:295: error: ‘PAGE_SIZE’ no se declaró aquí (primer uso en esta función)
sllog.c:297: error: ‘sllog_lock’ no se declaró aquí (primer uso en esta función)
sllog.c:301: aviso: declaración implícita de la función ‘free_pages’
sllog.c:301: error: ‘struct sllog’ no tiene un miembro llamado ‘buf’
sllog.c:318: error: puntero deferenciado a tipo de dato incompleto
sllog.c: En el nivel principal:
sllog.c:323: aviso: se declaró ‘struct file’ dentro de la lista de parámetros
sllog.c:323: aviso: se declaró ‘struct inode’ dentro de la lista de parámetros
sllog.c: En la función ‘sllog_close’:
sllog.c:325: error: puntero deferenciado a tipo de dato incompleto
sllog.c:329: error: ‘sllog_lock’ no se declaró aquí (primer uso en esta función)
sllog.c:332: error: ‘struct sllog’ no tiene un miembro llamado ‘buf’
sllog.c:334: error: ‘MOD_DEC_USE_COUNT’ no se declaró aquí (primer uso en esta función)
sllog.c: En el nivel principal:
sllog.c:339: aviso: se declaró ‘struct file’ dentro de la lista de parámetros
sllog.c: En la función ‘sllog_read’:
sllog.c:341: error: puntero deferenciado a tipo de dato incompleto
sllog.c:346: error: ‘sllog_lock’ no se declaró aquí (primer uso en esta función)
sllog.c:347: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:348: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:349: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:349: error: ‘struct sllog’ no tiene un miembro llamado ‘tail’
sllog.c:350: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c:350: error: ‘struct sllog’ no tiene un miembro llamado ‘tail’
sllog.c:356: aviso: declaración implícita de la función ‘interruptible_sleep_on’
sllog.c:356: error: ‘struct sllog’ no tiene un miembro llamado ‘wait’
sllog.c:357: aviso: declaración implícita de la función ‘signal_pending’
sllog.c:357: error: ‘current’ no se declaró aquí (primer uso en esta función)
sllog.c:358: error: ‘ERESTARTSYS’ no se declaró aquí (primer uso en esta función)
sllog.c:361: aviso: declaración implícita de la función ‘copy_to_user’
sllog.c:361: error: ‘struct sllog’ no tiene un miembro llamado ‘buf’
sllog.c:361: error: ‘struct sllog’ no tiene un miembro llamado ‘tail’
sllog.c:362: error: ‘EFAULT’ no se declaró aquí (primer uso en esta función)
sllog.c:367: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:368: error: ‘struct sllog’ no tiene un miembro llamado ‘tail’
sllog.c:368: error: ‘struct sllog’ no tiene un miembro llamado ‘tail’
sllog.c:368: error: ‘struct sllog’ no tiene un miembro llamado ‘size’
sllog.c: En el nivel principal:
sllog.c:376: aviso: se declaró ‘struct file’ dentro de la lista de parámetros
sllog.c:376: aviso: se declaró ‘struct inode’ dentro de la lista de parámetros
sllog.c: En la función ‘sllog_ioctl’:
sllog.c:378: error: puntero deferenciado a tipo de dato incompleto
sllog.c:382: aviso: declaración implícita de la función ‘_IOW’
sllog.c:382: error: expected expression before ‘unsigned’
sllog.c:382: error: la etiqueta de `case' no se reduce a una constante entera
sllog.c:385: error: expected expression before ‘unsigned’
sllog.c:385: error: la etiqueta de `case' no se reduce a una constante entera
sllog.c:386: error: ‘struct sllog’ no tiene un miembro llamado ‘log_mask’
sllog.c:387: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función)
sllog.c:389: aviso: declaración implícita de la función ‘set_bit’
sllog.c:389: error: ‘struct sllog’ no tiene un miembro llamado ‘log_mask’
sllog.c:391: aviso: declaración implícita de la función ‘_IO’
sllog.c:391: error: la etiqueta de `case' no se reduce a una constante entera
sllog.c:392: error: ‘sllog_lock’ no se declaró aquí (primer uso en esta función)
sllog.c:393: error: ‘struct sllog’ no tiene un miembro llamado ‘mon’
sllog.c:394: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:394: error: ‘struct sllog’ no tiene un miembro llamado ‘tail’
sllog.c:394: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:397: error: la etiqueta de `case' no se reduce a una constante entera
sllog.c:399: error: ‘struct sllog’ no tiene un miembro llamado ‘mon’
sllog.c:400: error: ‘struct sllog’ no tiene un miembro llamado ‘head’
sllog.c:400: error: ‘struct sllog’ no tiene un miembro llamado ‘tail’
sllog.c:400: error: ‘struct sllog’ no tiene un miembro llamado ‘cnt’
sllog.c:404: error: ‘ENOIOCTLCMD’ no se declaró aquí (primer uso en esta función)
sllog.c: En el nivel principal:
sllog.c:409: error: la variable ‘sllog_fops’ tiene inicializador pero de tipo de dato incompleto
sllog.c:411: error: se especificó el campo desconocido ‘owner’ en el inicializador
sllog.c:411: error: ‘THIS_MODULE’ no se declaró aquí (no en una función)
sllog.c:411: aviso: exceso de elementos en el inicializador de struct
sllog.c:411: aviso: (cerca de la inicialización de ‘sllog_fops’)
sllog.c:413: error: se especificó el campo desconocido ‘read’ en el inicializador
sllog.c:413: aviso: exceso de elementos en el inicializador de struct
sllog.c:413: aviso: (cerca de la inicialización de ‘sllog_fops’)
sllog.c:414: error: se especificó el campo desconocido ‘poll’ en el inicializador
sllog.c:414: aviso: exceso de elementos en el inicializador de struct
sllog.c:414: aviso: (cerca de la inicialización de ‘sllog_fops’)
sllog.c:415: error: se especificó el campo desconocido ‘ioctl’ en el inicializador
sllog.c:415: aviso: exceso de elementos en el inicializador de struct
sllog.c:415: aviso: (cerca de la inicialización de ‘sllog_fops’)
sllog.c:416: error: se especificó el campo desconocido ‘open’ en el inicializador
sllog.c:416: aviso: exceso de elementos en el inicializador de struct
sllog.c:416: aviso: (cerca de la inicialización de ‘sllog_fops’)
sllog.c:417: error: se especificó el campo desconocido ‘release’ en el inicializador
sllog.c:418: aviso: exceso de elementos en el inicializador de struct
sllog.c:418: aviso: (cerca de la inicialización de ‘sllog_fops’)
sllog.c:420: error: la variable ‘misc_sllog’ tiene inicializador pero de tipo de dato incompleto
sllog.c:421: error: se especificó el campo desconocido ‘minor’ en el inicializador
sllog.c:421: error: ‘MISC_DYNAMIC_MINOR’ no se declaró aquí (no en una función)
sllog.c:421: aviso: exceso de elementos en el inicializador de struct
sllog.c:421: aviso: (cerca de la inicialización de ‘misc_sllog’)
sllog.c:422: error: se especificó el campo desconocido ‘name’ en el inicializador
sllog.c:422: aviso: exceso de elementos en el inicializador de struct
sllog.c:422: aviso: (cerca de la inicialización de ‘misc_sllog’)
sllog.c:423: error: se especificó el campo desconocido ‘fops’ en el inicializador
sllog.c:423: aviso: exceso de elementos en el inicializador de struct
sllog.c:423: aviso: (cerca de la inicialización de ‘misc_sllog’)
sllog.c:437: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
sllog.c:443: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’
sllog.c:448: aviso: la definición de datos no tiene tipo o clase de almacenamiento
sllog.c:448: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘module_init’
sllog.c:448: aviso: nombres de parámetros (sin tipos) en la declaración de la función
sllog.c:449: aviso: la definición de datos no tiene tipo o clase de almacenamiento
sllog.c:449: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘module_exit’
sllog.c:449: aviso: nombres de parámetros (sin tipos) en la declaración de la función
sllog.c:451: aviso: la definición de datos no tiene tipo o clase de almacenamiento
sllog.c:451: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL_NOVERS’
sllog.c:451: aviso: nombres de parámetros (sin tipos) en la declaración de la función
sllog.c:452: aviso: la definición de datos no tiene tipo o clase de almacenamiento
sllog.c:452: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL_NOVERS’
sllog.c:452: aviso: nombres de parámetros (sin tipos) en la declaración de la función
make: *** [sllog.o] Error 1

¿ :( ?

---

### Post by faktorqm on 2008-01-12
no te preocupes, esos son los errores que tira cuando no encuentra lo sarchivos .h que te indica al principio. El problema es que yo si tengo esos archivos que dice tu compilacion que no estan..... Fijate si en esta ruta "/usr/src/2.6.22-14-generic/include/linux/" tenes lo archivos que te dice ahi, module.h, init.h y demas.
Sino fijate con el sinaptic de instalar las cabeceras del kernel, linux-header o linux-kernel-header, no me acuerdo el nombre. Salu2!

---

### Post by .NicK_LoVe on 2008-01-14
Revise los archivos q me dice q faltan y están en la carpeta, y busque los headers y estan actualizados.
:(

---

### Post by rojojuan on 2008-12-24
Tengo que instalar este modem.
Cómo siguió la cosa?
Alguien lo pudo instalar?

---

