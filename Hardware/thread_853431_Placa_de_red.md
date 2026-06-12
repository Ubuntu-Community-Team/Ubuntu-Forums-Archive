---
title: "Placa de red"
date: 2008-07-08
forum: Hardware
---

### Post by Millenium_arg on 2008-07-08
[FONT=Times New Roman][SIZE=3]Antes que nada, quiero aclarar que soy absolutamente nuevo en esto. O sea, no se nada de nada.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Hace muchos años ya, despues de la muerte y sepelio del DOS, creo que le vendí mi alma a BillGates y ahora estoy pagando las consecuencias.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Les cuento lo que me pasa.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Estoy tratando de instalar UBUNTU 8.04.1 Desktop en un Mother ASUS P5GC-MX/1333.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Este Mother tiene un chipset Intel82801, con placa de video Intel 82945, y placa de red Atheros L2 Fast Ethernet 10/100 BaseT[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]El problema es que parece que UBUNTU no puede manejar la placa de Red.[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]No envía ni recibe un solo paquete !![/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Buscando en la web de ASUS, encontré los drivers para Linux, de la placa de red y de la placa de sonido.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Así que procedí a instalar el driver de la placa de red, debidamente logueado como root.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Copio el resultado del comando make install[/FONT][/SIZE]
 
[FONT=Arial][SIZE=2][EMAIL="root@Linux-PC:~/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src"]root@Linux-PC:~/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src[/EMAIL]# clear[/SIZE][/FONT]
[FONT=Arial][SIZE=2][EMAIL="root@Linux-PC:~/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src"]root@Linux-PC:~/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src[/EMAIL]# make install[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make: Atención: El archivo `Makefile' tiene una hora de modificación 5,2e+07 en el futuro[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src modules[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]scripts/Makefile.build:46: *** CFLAGS was changed in "/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src/Makefile". Fix it to use EXTRA_CFLAGS. Alto.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make[1]: *** [_module_/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src] Error 2[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make: *** [default] Error 2[/SIZE][/FONT]
 
  
[FONT=Times New Roman][SIZE=3]Alguna idea ???[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]E[/SIZE][/FONT][FONT=Times New Roman][SIZE=3]n la documentación de ASUS, dice que este driver solo ha sido testeado para RedHat.  Significa que no andaría en UBUNTU ??[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Otras pruebas:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Por supuesto que hice el experimento de anular la Placa de Red del Mother, y colocarle una Realtek PCI común, a apenas arrancó configuró todo correctamente y me dejó navegar.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Desde ya, muchas gracias.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

### Post by pabloatilio on 2008-07-08
> **Millenium_arg said:**
> [FONT=Times New Roman][SIZE=3]Antes que nada, quiero aclarar que soy absolutamente nuevo en esto. O sea, no se nada de nada.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Hace muchos años ya, despues de la muerte y sepelio del DOS, creo que le vendí mi alma a BillGates y ahora estoy pagando las consecuencias.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Les cuento lo que me pasa.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Estoy tratando de instalar UBUNTU 8.04.1 Desktop en un Mother ASUS P5GC-MX/1333.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Este Mother tiene un chipset Intel82801, con placa de video Intel 82945, y placa de red Atheros L2 Fast Ethernet 10/100 BaseT[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]El problema es que parece que UBUNTU no puede manejar la placa de Red.[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]No envía ni recibe un solo paquete !![/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Buscando en la web de ASUS, encontré los drivers para Linux, de la placa de red y de la placa de sonido.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Así que procedí a instalar el driver de la placa de red, debidamente logueado como root.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Copio el resultado del comando make install[/FONT][/SIZE]
 
[FONT=Arial][SIZE=2][EMAIL="root@Linux-PC:~/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src"]root@Linux-PC:~/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src[/EMAIL]# clear[/SIZE][/FONT]
[FONT=Arial][SIZE=2][EMAIL="root@Linux-PC:~/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src"]root@Linux-PC:~/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src[/EMAIL]# make install[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make: Atención: El archivo `Makefile' tiene una hora de modificación 5,2e+07 en el futuro[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src modules[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]scripts/Makefile.build:46: *** CFLAGS was changed in "/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src/Makefile". Fix it to use EXTRA_CFLAGS. Alto.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make[1]: *** [_module_/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src] Error 2[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]make: *** [default] Error 2[/SIZE][/FONT]
 
  
[FONT=Times New Roman][SIZE=3]Alguna idea ???[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]E[/SIZE][/FONT][FONT=Times New Roman][SIZE=3]n la documentación de ASUS, dice que este driver solo ha sido testeado para RedHat.  Significa que no andaría en UBUNTU ??[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Otras pruebas:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Por supuesto que hice el experimento de anular la Placa de Red del Mother, y colocarle una Realtek PCI común, a apenas arrancó configuró todo correctamente y me dejó navegar.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Desde ya, muchas gracias.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

Hola Milleniun, estoy seguro de que en el siguiente enlace :

[http://ubuntuforums.org/showthread.php?t=429845](http://ubuntuforums.org/showthread.php?t=429845)

tratan la solución a tu problema y a algunos le funciona,  se trata de la misma placa de red (de red no de mother), por lo tanto el mismo driver, si tenés dificultades con el idioma avisa.

La más simple parece copiar el driver compilado que te ofrecen ahi de la forma :

 sudo insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko

el driver compilado está en :

[http://ubuntuforums.org/attachment.php?attachmentid=33221](http://ubuntuforums.org/attachment.php?attachmentid=33221)

Eso teniendo en cuenta que como vos decis, no tenes demasiada idea. Con el comando "uname -r" averiguas la "KERNEL VERSION" y reemplazas en la sentencia anterior. ESTA NO ES LA SOLUCIÓN IDEAL. Lo mejor es conseguir y compilar el driver en el equipo con los fuentes originales, pero no es tan fácil compilar para alguien que no tiene mucha idea y no sé donde se puedan conseguir esos drivers.

En caso que no te llegue a servir, (cosa que no creo), buscá información relativa a Attansic L2 fast ethernet. 

La página del fabricante es : [http://www.atheros.com/pt/ethernet_index.htm](http://www.atheros.com/pt/ethernet_index.htm)  , pero no sé cual opción de las que aparecen es la que corresponde a tu placa de red.

Suerte. Saludos

Pablo

---

### Post by Millenium_arg on 2008-07-08
Pablo:
 
Muchas gracias por tan pronta respuesta.
Lamentablemente, no anda !
Copiando el **atl2.ko** en la carpeta net, al ejecutar el comando 
 
 
[COLOR=red]sudo insmod /lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2.ko[/COLOR]
Me dá el siguiente error:
 
 
[COLOR=red]insmod: error inserting '/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2.ko': -1 Invalid module format[/COLOR]
 
[COLOR=black]También intente un Make Installl con los drivers que parecen mas nuevos. Bajados del mismo link que me pasaste, pero el resultado sigue siendo el mismo.[/COLOR]
 
[COLOR=red]root@Linux-PC:~/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src[/COLOR][COLOR=red]# make install[/COLOR]
[COLOR=red]make: Atención: El archivo `Makefile' tiene una hora de modificación 5,2e+07 en el futuro[/COLOR]
[COLOR=red]make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src modules[/COLOR]
[COLOR=red]make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'[/COLOR]
[COLOR=red]scripts/Makefile.build:46: *** CFLAGS was changed in "/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src/Makefile". Fix it to use EXTRA_CFLAGS. Alto.[/COLOR]
[COLOR=red]make[1]: *** [_module_/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src] Error 2[/COLOR]
[COLOR=red]make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'[/COLOR]
[COLOR=red]make: *** [default] Error 2[/COLOR]
 
 
Importante: la línea "*** CFLAGS was changed in....................." parece explicar la razón por lo cual no puede compilar el driver. Pero no puedo con mis conocimientos interpretarlo.
 
 
Y la página de Atheros, no parece tener Drivers disponibles en ninguna parte.
Además, el chip que tiene dice:
**0749**
**B82451 4C**
En ningún lado hay algo que se parezca a 
**AR8021** o **AR8216**
que son los chips que según esta página deberías encontrar en el Mother.
 
Se te ocurre alguna cosa ??
 
 
Nuevamente... muchas gracias.

---

### Post by pabloatilio on 2008-07-08
> **Millenium_arg said:**
> Pablo:
 
Muchas gracias por tan pronta respuesta.
Lamentablemente, no anda !
Copiando el **atl2.ko** en la carpeta net, al ejecutar el comando 
 
 
[COLOR=red]sudo insmod /lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2.ko[/COLOR]
Me dá el siguiente error:
 
 
[COLOR=red]insmod: error inserting '/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2.ko': -1 Invalid module format[/COLOR]
 
[COLOR=black]También intente un Make Installl con los drivers que parecen mas nuevos. Bajados del mismo link que me pasaste, pero el resultado sigue siendo el mismo.[/COLOR]
 
[COLOR=red]root@Linux-PC:~/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src[/COLOR][COLOR=red]# make install[/COLOR]
[COLOR=red]make: Atención: El archivo `Makefile' tiene una hora de modificación 5,2e+07 en el futuro[/COLOR]
[COLOR=red]make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src modules[/COLOR]
[COLOR=red]make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'[/COLOR]
[COLOR=red]scripts/Makefile.build:46: *** CFLAGS was changed in "/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src/Makefile". Fix it to use EXTRA_CFLAGS. Alto.[/COLOR]
[COLOR=red]make[1]: *** [_module_/root/LinuxDrivers/Lan/Attansic/l2-linux-v1.0.40.4/src] Error 2[/COLOR]
[COLOR=red]make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'[/COLOR]
[COLOR=red]make: *** [default] Error 2[/COLOR]
 
 
Importante: la línea "*** CFLAGS was changed in....................." parece explicar la razón por lo cual no puede compilar el driver. Pero no puedo con mis conocimientos interpretarlo.
 
 
Y la página de Atheros, no parece tener Drivers disponibles en ninguna parte.
Además, el chip que tiene dice:
**0749**
**B82451 4C**
En ningún lado hay algo que se parezca a 
**AR8021** o **AR8216**
que son los chips que según esta página deberías encontrar en el Mother.
 
Se te ocurre alguna cosa ??
 
 
Nuevamente... muchas gracias.

El error que te está dando cuando lo pones de una en la carpeta es probablemente porque el formato del módulo compilado no es el mismo que el de la versión de linux que tenes vos, eso puede ser que sea por ej porque uno es 64 bits y el otro 32 bits, hoy estoy sin tiempo, mañana miro un poco y te cuento, fijate si ahi donde te pase antes no aparece compilado en distintas versiones. El error que te da cuando compilas directamente coincido con vos pero no la tengo muy clara con eso, por las dudas probá de compilar con el comando sudo o sin, nose como hiciste, a mi una vez era ese el problema. Paciencia que ya vamos a encontrar alguna solución, acá en el foro hay algunos tipos grosos en linux que seguro  que cuando lean tu post te van a poder dar alguna mano. Saludos.
Pablo

---

### Post by faktorqm on 2008-07-09
Si, el comando es "sudo make install". nunca make install solo por que no anda. Como dice Pablo, el modulo no es compatible con la version del kernel que tenes vos. Tb toy con la facu a full, pero de ultima pone "uname -r" y postea el resultado, si tengo el mismo kernel te lo compilo yo y te lo paso. Salu2!!

---

### Post by Millenium_arg on 2008-07-10
[FONT=Times New Roman][SIZE=4]faktorqm[/SIZE][/FONT] :
 
[FONT=Times New Roman][SIZE=3]Gracias por la respuesta.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]El uso del comando **sudo,** no cambia el mensaje de error del **make install** ni del **insmod**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]El comando **uname -r** devuelve :[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]**2.6.24-19-generic**[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]En este link hay post de **Master Chief**[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][http://ubuntuforums.org/showthread.php?t=429845&page=8](http://ubuntuforums.org/showthread.php?t=429845&page=8)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]que explica el tema del error del CFLAG. (en el make install)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Traté de seguir sus consejos, pero da muchísmos errores y ya se me escapa la posibilidad de solucionarlos.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Así que repuse los archivos "tocados" con la copia que hice previamente.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]En fin... que estoy varado..[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Saludos !![/SIZE][/FONT]

---

### Post by faktorqm on 2008-07-10
No pude compilar el driver con ese source, saltié todos los errores pero me colgué con el de version.h, y no tengo ganas de andar dando vueltas.
Buscando y leyendo un poco, llegué a que el tipo lo compiló para la version de kernel que tenes vos, asi que nada, aca te dejo el link.

[http://ubuntuforums.org/attachment.php?attachmentid=76223&d=1215071065](http://ubuntuforums.org/attachment.php?attachmentid=76223&d=1215071065)

Ese módulo es para 64 bits. OJO!

Si queres ver el post es [http://ubuntuforums.org/showthread.php?p=5310139](http://ubuntuforums.org/showthread.php?p=5310139).

Espero que te haya servido. Salu2!

---

### Post by Millenium_arg on 2008-07-12
Gracias...
 
Pero no anduvo..
Lo más que conseguí es que estos comandos funcionaran:
 
[COLOR=red]/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2/atl2.ko [/COLOR][COLOR=black]OK !!![/COLOR]
[COLOR=red]sudo modprobe atl2 [/COLOR][COLOR=black]OK !!! (and sudo modprobe -r atl2 also)[/COLOR]
[COLOR=red]sudo dhclient eth0 [/COLOR][COLOR=black]Not work !!![/COLOR]
 
No encuentra el DHCP.
Asigna una dirección interna (16x.xxx.xxx.xxx)
Forzándola a (ej) 192.168.0.200 (válida en mi red), parece configurarse, pero no hay tráfico de salida ni de entrada.  O sea, no anda.
 
Alguien tiene alguna idea ??

---

