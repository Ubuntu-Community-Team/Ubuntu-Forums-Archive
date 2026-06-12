---
title: "problema con VirtualBox y los USB"
date: 2008-01-31
forum: Hardware
---

### Post by Thalskarth on 2008-01-31
Bueno, mi rpoblema ocurrio hace poco...


yo uso virtualbox hace un tiempo para virtualizar un WinXP dentro de mi Gutsy.

En su momento active los USB en VirtualBox, con el turorial que esta en todos lados que es mas o menos asi:
> Editar el siguiente archivo: 

sudo gedit /etc/init.d/mountdevsubfs.sh 

Y 'des-comentar' (quitarle los &#8216;#&#8217;) a las siguientes lineas después de donde dice "Magic to make /proc/bus/usb work". 

#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb 

Quedarian asi: 

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb 

A continuación editamos:

sudo gedit /etc/udev/rules.d/40-permissions.rules 

En el archivo de texto que abre, buscamos la linea 

SUBSYSTEM=="usb_device", MODE="0664" 

Y la cambiamos por: 

SUBSYSTEM=="usb_device", MODE="0666"


Tras reiniciar todo estará listo.

Pero hace poco se actualizo virtualbox. y desde entonces no me reconoce mas los USB. Intente usar el mismo tutorial pero no cambio nada. desintale el Vbox y borre la carpeta .virtualbox de mi home y lo reinstale de cero... pero nada cambio.

me tira este error:

```

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

 
```

como puedo solucionarlo???

---

### Post by clasificado on 2008-01-31
[Tenia entendido que el soporte para USB de virtualbox solo estaba en la versión closed source paga (y guacha).]("http://www.virtualbox.org/wiki/Editions")

De hecho, es esa perspectiva lo que me hace detestarlo. No me extrañaria que un cambio en el codigo fuente haya dejado afuera las versiones no-oficiales del soporte USB, solo porque les conviene al bolsillo.

Por supuesto, conspiro sin tener la mas minima experiencia :lolflag:

clasificado

---

### Post by Thalskarth on 2008-01-31
> **clasificado said:**
> [Tenia entendido que el soporte para USB de virtualbox solo estaba en la versión closed source paga (y guacha).]("http://www.virtualbox.org/wiki/Editions")

De hecho, es esa perspectiva lo que me hace detestarlo. No me extrañaria que un cambio en el codigo fuente haya dejado afuera las versiones no-oficiales del soporte USB, solo porque les conviene al bolsillo.

Por supuesto, conspiro sin tener la mas minima experiencia :lolflag:

clasificado

no conocia la existencia de esa otra version... pero en la pagina no dice nada de quitar USB o algo asi....

igualmente.. alguien sabe como solucionarlo???

desdeya muchas gracias

---

### Post by clasificado on 2008-02-01
¿De que manera instalaste el Virtualbox? ¿Repositorios, Debs, Bin.Tar, Compilado desde el fuente?

Asi llego a casa y lo pruebo :D

clasificado

---

### Post by Thalskarth on 2008-02-01
> **clasificado said:**
> ¿De que manera instalaste el Virtualbox? ¿Repositorios, Debs, Bin.Tar, Compilado desde el fuente?

Asi llego a casa y lo pruebo :D

clasificado

Lo instale desde este repositorio:

```
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free
```

que esta sacado de la [pagina oficial]("http://www.virtualbox.org/wiki/Downloads")


Como dije, antes si me andaban... pero luego dejo de andar... y no pude solucionarlo :confused:

Podra ser algo de cuando intente habilitarlos USB tocando los archivos: "/etc/init.d/mountdevsubfs.sh" y "/etc/udev/rules.d/40-permissions.rules" y halla tocado algo de mas sin querer??? y por eso no funcione.. o sea, no creo porque dejo de andar al actualizarse sin tocar yo nada... pero no se :(

---

### Post by jclevien on 2008-02-02
Hola Thalskarth,

Yo no uso ni recomiendo más el VirtualBox, por ese motivo y por algunas inestabilidades serias (de repente, no se puede ejecutar más como un usuario distinto a root, errores mal documentados, como uno que no tenía ID y de casualidad encontré la solución cambiando permisos en /dev/vboxdrv, etc).

VMware también tiene sus cosas, hablo de la versión Server que es gratis, es lento, pesado, no tiene soporte USB y encima la placa de red virtual me anda en forma intermitente (esto también admitido por la gente de VMware).

Ahora me volqué por el QEMU, tengo un poco de miedo por el QEMU Accelerator, que no se si es estable, pero veremos que pasa.

Saludos.


Juan

---

### Post by Thalskarth on 2008-02-02
> **jclevien said:**
> Ahora me volqué por el QEMU, tengo un poco de miedo por el QEMU Accelerator, que no se si es estable, pero veremos que pasa.
Una pregunta, el QEMU tiene soporte USB? y permite compartir carpetas entre el Host y el Guest?? esas son las 2 funciones que yo necesito...

---

### Post by Thalskarth on 2008-02-02
perdon por el doble post...


pero queria comentarles que pude arreglar el problema. lo hice con estas instrucicones:

```
Añadir la siguiente linea al final de  /etc/fstab

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

el numero de devgid es el vboxusers group id (por defecto)

una vez, guardado los cambios, ejecutar sudo mount -a y listo
```


sacado de: [http://ubuntuforums.org/showpost.php?p=3679471&postcount=3](http://ubuntuforums.org/showpost.php?p=3679471&postcount=3)

---

### Post by marianom on 2008-02-02
> **Thalskarth said:**
> Una pregunta, el QEMU tiene soporte USB? y permite compartir carpetas entre el Host y el Guest?? esas son las 2 funciones que yo necesito...

Si mal no recuerdo....

1- le haces saber al SO invitado que hay un usb con un comando desde la consola de Qemu.
2- si podes, yo he compartido archivos entre mi ubuntu y varias distros de linux virtualizadas sin problemas, con ssh. Supongo que el método equivalente para windows debe funcionar.


y lo que digo desde hace meses, Qemu tendrá sus cosas pero sigue siendo el virtualizador libre, funciona bien y debería ser siempre la opción por defecto para todos salvo que algo que es realmente necesario no esté y debamos recurrir a los otros.

---

### Post by jclevien on 2008-02-03
Hola marianom,

Mirá, yo realmente estaba desilusionado con los virtualizadores.
Hace poco probé el QEMU, quise arrancar dos instancias de un programa pesado, y se colgó completamente la máquina virtual.

Nada, intenté recompilar el QEMU en mi Gutsy, lo logré, instalé el paquete que hice yo, el Windows reportaba mi procesador (en lugar de Pentium II que reportaba el QEMU), y lo mismo, se volvió a colgar.

Le asigné memoria (512 MB RAM), pero parece que QEMU también tiene sus temas.

Por este thread, se me dió probar la última versión de VirtualBox, la verdad, yo había probado la versión 1.2. Por aquél entonces había bastantes problemas, pero he quedado sorprendido con esta última release. Muy eficiente, soporta USB, tiene un server RDP integrado, y otras yerbas.

Lo que me llamó la atención, es que el VirtualBox no cobra por la versión cerrada, tiene una licencia personal. Ahora si uno le da un uso comercial, entonces ahí si hay que pagar.

Saludos.



Juan

---

### Post by krinblin on 2008-10-19
Holas soy nuevo en esto, e mirado por todos lados pero no me funciona el usb cuando trato de activarlo me tira este error.


Failed to create a proxy device for the USB device. (Error: VERR_READ_ERROR).


Código Resultado: 
NS_ERROR_FAILURE (0x80004005)
Componente: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}


bueno eso es por ahora y gracias.

---

