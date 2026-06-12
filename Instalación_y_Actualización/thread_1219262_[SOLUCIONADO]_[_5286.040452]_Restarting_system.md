---
title: "[SOLUCIONADO] [ 5286.040452] Restarting system"
date: 2009-07-21
forum: Instalación y Actualización
---

### Post by aledruetta on 2009-07-21
Hola Comunidad!

Estoy instalando Ubuntu Jaunty a un amigo, en su computador. Es un Pentium 4 de 2.66Hz; 512 de RAM. Jaunty está en una partición EXT3, y en otra partición (FAT32) tiene Windows XP.

El problema es el siguiente, cuando reinicio el computador, efectúa aparentemente todo el proceso de cierre (Con la barrita que se va llenando. Perdón, no sé de que otra manera decirlo) pero al final, la pantalla queda en negro y se lee (el número nunca es el mismo):
```
[ 5286.040452] Restarting system
```Ahí se queda clavado. Tengo que reiniciar con el botón del gabinete. 

¿Alguién sabe qué puede estar sucediendo?

Mil gracias,
Alejandro.

El mismo post en Ubuntu-ar: [http://ubuntuforums.org/showthread.php?p=7653807#post7653807](http://ubuntuforums.org/showthread.php?p=7653807#post7653807)

---

### Post by kornykyano on 2009-07-21
Deberías contar como se llego a este error. Que programa haz instalado, previo a este bug?

Probaste eligiendo un kernel mas viejo?

---

### Post by aledruetta on 2009-07-21
> **kornykyano said:**
> Deberías contar como se llego a este error. Que programa haz instalado, previo a este bug?

Probaste eligiendo un kernel mas viejo?

Fue inmediato a la instalación de Ubuntu. Al reiniciar por primera vez apareció el mensaje y a partir de ahí, cada vez que reinicio.

Voy a probar con el kernel anterior, ahora está usando el 2.6.28-13 generic

Gracias.

---

### Post by aledruetta on 2009-07-21
Ya probé con la versión 2.6.28-11 del kernel y el problema continúa.
Otra cosa que noté es que con la opción de "apagar", si bien el mensaje sigue apareciendo por una fracción de segundo, la máquina se apaga, no queda ahí congelada.

---

### Post by kamus on 2009-07-21
> **aledruetta said:**
> Ya probé con la versión 2.6.28-11 del kernel y el problema continúa.
Otra cosa que noté es que con la opción de "apagar", si bien el mensaje sigue apareciendo por una fracción de segundo, la máquina se apaga, no queda ahí congelada.

Creo que hay algun tipo de incompatibilidad con algunas funciones de tu placa madre y ubuntu (tirado para acpi), podrias intentar algunos parametros al kernel y ver que tal reacciona (tienes actualizada la BIOS de tu placa madre?)

[1]https://wiki.kubuntu.org/DebuggingACPI

:o

---

### Post by aledruetta on 2009-07-22
> **kamus said:**
> Creo que hay algun tipo de incompatibilidad con algunas funciones de tu placa madre y ubuntu (tirado para acpi), podrias intentar algunos parametros al kernel y ver que tal reacciona (tienes actualizada la BIOS de tu placa madre?)

[1]https://wiki.kubuntu.org/DebuggingACPI

:o

Hola kamus,

Supongo que no está actualizada la BIOS (es la computadora de un amigo que estoy tratando de introducir a Linux) Voy a ver qué consigo averiguar sobre la placa madre y si puedo actualizar la BIOS. No es un problema grave, pero me gustaría que todo funcione bien porque de eso va a depender el grado de aceptación sobre el nuevo sistema.

En cuanto al Kernel ¿Qué me sugerís?

Gracias,
Alejandro.

---

### Post by aledruetta on 2009-07-22
Bueno, el comando:
```
sudo dmimode
```
me tira:
```
BIOS Information
    Vendor: Award Software International, Inc.
    Version: F1
    Release Date: 09/23/2005

```
Así que está bien desactualizada. Estoy buscando en google cómo actualizar esa BIOS.

Gracias,
Alejandro.

---

### Post by aledruetta on 2009-07-22
No hay caso, no encuentro información sobre el driver para actualizar la BIOS. Por otro lado, lo que dicen acá me da un poco de miedo, si fuera mía la máquina no habría problema, pero...

> **jmorelli said:**
> El Uniflash es una utilidad universal que sirve para flashear ( borrar la data anterior que esta en una Eprom en el mother y cargar la nueva ). Se le dice comunmente flashear porque el proceso que lleva a cabo anteriormente se llevaba a cabo aplicando una luz sobre la ventanita que contenía la eprom dentro del chip, eso hacía que se borre el contenido y quede libre para cargarle otra información. Obviamente esto se hacía sobre una plaqueta aparte de la computadora que efectuaba el proceso, Ahora como todo se evolucionó en el tema y el mother puede quedar durante unos segundos sin su bios ( ya que la PC ya arrancó y mantiene esos seteos hasta que la energía se corte nuevamente ) para poder cargar la nueva versión de bios que el fabricante publica.
Volviendo al uniflash, es un programa que se encarga de borrar y subir el archivo con el nuevo bios ( generalmente un archivo .bio o .rom ). Pero este proceso es peligroso ya que si uno le da un .bio o .rom que no corresponde exactamente con el mother, éste generalmente luego de resetear no arranca nunca más, en estos casos lo único que se puede hacer es: conseguir el mismo mother, sacarle el chip y usarlo en el viejo ( o sea entre dos mothers hacer uno ) o tirarlo a la basura :( ( hay más opciones pero bueno, ninguna sirve de mucho y son arriesgadas )
Resumiendo, si el fabricante pone en la web un archivo .exe con una nueva versión de bios para cierto mother, generalmente tiene ya incluído: un chequeador para saber si el modelo del mother que se quiere flashear es el correcto, el ejecutable que se encarga de hacer el flash ( uniflash, iflash, etc ) y el archivo del bios propiamente.
A veces el exe descomprime todas estas herramientas en un diskete para bootear desde ahi y automatizar el proceso y a veces ( caso intel ) tambien están los .exe para correr desde el entorno Win ( tiene un par de instrucciones que resetean la máquina y le hacen correr el update en el proximo booteo.
Espero haber sido claro porque escribí todo de corrido :P[URL="http://ubuntuforums.org/newreply.php?do=newreply&p=2644248"]
[/URL]

---

### Post by nopersona on 2009-07-23
Me huele a ACPI, qué opciones tiene el kernel cuándo botea?


P.S.: NO recomiendo, PARA NADA, intentar flashear la bios!

---

### Post by aledruetta on 2009-07-24
> **nopersona said:**
> Me huele a ACPI, qué opciones tiene el kernel cuándo botea?

Perdón, pero ¿cómo averiguo esas opciones?

---

### Post by nopersona on 2009-07-24
El archivo se llama menu.lst, es la lista de boteo de él o los kernels instalados en el sistema, busca en 

```
/boot/grub/menu.lst
```

Si tienes más de un kernel y no estás seguro de cuál usas, en un terminal tipea

```
uname -r
```

---

### Post by aledruetta on 2009-07-24
Saqué las líneas que estaban comentadas, ahí va el menu.lst:
```
default        0
timeout        3
hiddenmenu

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        5a5b7dd5-57e2-4a35-a803-f18a984e6714
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5a5b7dd5-57e2-4a35-a803-f18a984e6714 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        5a5b7dd5-57e2-4a35-a803-f18a984e6714
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5a5b7dd5-57e2-4a35-a803-f18a984e6714 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, memtest86+
uuid        5a5b7dd5-57e2-4a35-a803-f18a984e6714
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=78ee87a5-d8c8-4a45-9c46-208d711b53e1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=78ee87a5-d8c8-4a45-9c46-208d711b53e1 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot

```

El kernel que uso es el:
```
Ubuntu 9.04, kernel 2.6.28-13-generic
```

---

### Post by nopersona on 2009-07-24
Se me olvidaba de que es posible ver el log del error, cuando te aparezca presiona CTRL+ALT+F7.

Respecto a lo otro, agrega noapic                                                    a la linea del kernel, quedaría así, también puedes probar con acpi=off o ambas juntas. 

```
sudo gedit /boot/grub/menu.lst 
``````
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5a5b7dd5-57e2-4a35-a803-f18a984e6714 ro quiet splash **noapic**
```Si no llegase a funcionar, basta con apretar escape al momento de inicio, selecionar el kernel, luego "e" para editar, borrar lo escrito, y después botear con "b". Luego lo puedes editar como al principio. 

Veamos si funciona esto primero.

---

### Post by aledruetta on 2009-07-24
Probé las tres opciones:

noacpi
acpi=off
noacpi acpi=off

Pero no dio resultado.
¿Qué más puedo intentar?

---

### Post by nopersona on 2009-07-24
A ver, veamos el ACPI

```
dmesg |grep -i acpi
```

Sólo de curioso, el equipo es de marca o armado?

Probemos apagando por terminal, alguna opción te tira errores?

```
sudo halt
```

```
sudo poweroff
```

```
sudo shutdown -h now
```


También busca en la BIOS algo así como power management setup el parametro IPCA (Advanced Configuration and Power management Interface) ACPI y pruebas activando desactivando. 

P.S.: Y el log de error?

---

### Post by aledruetta on 2009-07-24
El equipo es un clon, armado, sí. 

```
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data)
[    0.000000]  modified: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[    0.000000]  modified: 000000001dff3000 - 000000001e000000 (ACPI data)
[    0.000000] Kernel command line: root=UUID=c06631ca-b6b5-4fe4-add2-8f1c60a4c745 ro locale=pt_BR quiet splash acpi=off noacpi
[    0.337875] ACPI: Interpreter disabled.
[    0.340243] pnp: PnP ACPI: disabled

```

ahora pruebo lo otro.

---

### Post by aledruetta on 2009-07-24
```
sudo halt
```da el mismo resultado, sólo que el mensaje cambia:
```
[ 3307.803515] System halted.
``````
sudo poweroff
``````
[   60.720536] System halted.
``````
sudo shutdown -h now
``````
[   76.491151] System halted.
```
Y presiono ctrl+Alt+F7 y no sucede nada.

---

### Post by nopersona on 2009-07-24
> **aledruetta said:**
> ```
sudo halt
```da el mismo resultado, sólo que el mensaje cambia:
```
[ 3307.803515] System halted.
``````
sudo poweroff
``````
[   60.720536] System halted.
```

Prueba todas las opciones, quiero asegurarme. Revisaste el ACPI en la bios? todavía tienes acpi=off noacpi en el kernel, editalo y vas probando. Luego de editarlo, y en el caso de que encuentres la opción, y ningún comando te arroje resultados, prueba agregando al kernel 

```
acpi=force
```

Revisando Launchpad, encontré el bug, pero primero terminemos con esto. 

P.S.: Y el log?

---

### Post by aledruetta on 2009-07-24
Justo estaba editando mi respuesta, cuando llegó la tuya. Algunas cosas las respondí ahí arriba.

En cuanto al Setup de la Bios, encontré algo sobre ACPI, únicamente en el Power Managment Setup. Ahí hay una opción que es: "ACPI Suspend Type" con dos parámetros para elegir: "S3(STR)" y "S1(POS)".

---

### Post by aledruetta on 2009-07-24
Edité el menu.lst, quité no-acpi y acpi=off, y coloqué acpi=force. Sigue dando el mismo mensaje:
```
[   58.156471] Restarting system
```

Y presiono Ctrl+Alt+F7 y no pasa nada.

---

### Post by nopersona on 2009-07-24
> **aledruetta said:**
> Edité el menu.lst, quité no-acpi y acpi=off, y coloqué acpi=force. Sigue dando el mismo mensaje:
```
[   58.156471] Restarting system
```Y presiono Ctrl+Alt+F7 y no pasa nada.

Probaste seleccionando s1 y s3 respesctivamente? 

**S1**: También llamado Power On Standby o POS, es el modo que más energía consume, pero el que menos tarda en volver al estado de trabajo. La CPU deja de trabajar y se guarda su caché. Se mantiene alimentada la CPU, la memoria RAM, los ventiladores y la fuente de alimentación. El resto de dispositivos pueden o no apagarse.

**S3**: Modo que se conoce como Suspender. También llamado STR (de Suspend to RAM), en este modo la memoria RAM es el único componente que se mantiene alimentado. De esta forma, dado que el estado de los programas se mantiene en memoria, el usuario puede volver a lo que estaba haciendo rápidamente.

[En launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213754") mencionan el error del kernel en equipos de frabrica y en uno que otro armado.  Una posible solución fue agregar 

```
reboot=b
```

en la linea del kernel. Para un equipo dell el dmesg es casi igual al tuyo. Si nada de sto llegase a funcionar, sería una buena idea reportar el bug en launchpad, con las especificaciones del equipo. 

Lo otro que se me ocurre es instalar el kernel 2.6.30 (a todo esto, no te había preguntado si la maquina y el sistema era 32 o 64 bits, error de mi parte, si es 64 bits, los paquetes son los mismos, pero para esa arquitectura)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

Creas una carpeta, por ejemplo: kernel 2.6.30, y descargas:

```
linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb
linux-headers-2.6.30-020630_2.6.30-020630_all.deb
linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb
linux-source-2.6.30_2.6.30-020630_all.deb
```

Luego ingresas al directorio e instalas

```
sudo dpkg -i *.deb
```

Después boteas con el nuevo kernel. No te preocupes, es seguro realizar esta acción, si llegase a suceder cualquier problema, tienes el antiguo kernel. 

También encontré que el error se debía a que el kernel intentaba leer un modulo cuando reiniciaba, otra persona lo solucionó instalando los  *linux-backports-modules-jaunty*

A ver qué sale :P

---

### Post by aledruetta on 2009-07-24
¡Impresionante lo tuyo, nopersona!!! Sin palabras!!!

agregar
```
reboot=b
```
fue la solución.

Después de hacerte trabajar tanto, vamos a abusar un poquito más de tu paciencia y sabiduría ¿qué significa agregar eso en la línea del kernel?

Mil millones de gracias,
Alejandro.

---

### Post by nopersona on 2009-07-24
> **aledruetta said:**
> ¡Impresionante lo tuyo, nopersona!!! Sin palabras!!!

agregar
```
reboot=b
```fue la solución.

Después de hacerte trabajar tanto, vamos a abusar un poquito más de tu paciencia y sabiduría ¿qué significa agregar eso en la línea del kernel?

Mil millones de gracias,
Alejandro.

Eso le indica al kernel que reinicie haciendo un "jumping" por la bios, como esto sólo es para equipos de 32 bits, ahora sé la máquina es de este tipo, jeje.  Hay muchas más opciones que son de utilidad en [la documentación del kernel]("http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php"), por ejemplo para botear:

reboot=b[ios] | s[mp] | t[riple] | k[bd] | e[fi] [, [w]arm | [c]old]
    warm   Don't set the cold reboot flag
    cold   Set the cold reboot flag
    bios   Reboot by jumping through the BIOS (only for X86_32)
    smp    Reboot by executing reset on BSP or other CPU (only for X86_32)
    triple Force a triple fault (init)
    kbd    Use the keyboard controller. cold reset (default)
    acpi   Use the RESET_REG in the FADT
    efi    Use efi reset_system runtime service
    force  Avoid anything that could hang.

Qué bueno que solucionaste tu problema, ahora creo que sabes mucho más de cómo funciona el sistema, y podrás usar tus conocimientos para ayudar a más gente. Edita el titulo con un lindo (SOLUCIONADO)

Hasta la próxima, saludos!

---

### Post by aledruetta on 2009-07-24
[quote=nopersona] Edita el titulo con un lindo (SOLUCIONADO)

Hasta la próxima, saludos![/quote]

Ups, lo primero que voy a tener que aprender es a editar el título del post, jejeje. No sé cómo se hace...

---

### Post by xavicob on 2009-08-01
hola a todos
tengo un reelbox avantgarde y desde que le hice el update nuevo el reelbox no funciona mas.
Podrian decirme en donde esta el problema y como solucionarlo?
gracias.
xavicob

---

