---
title: "Ubuntu no reconoce CD-R DVD-R DVD+R"
date: 2009-04-16
forum: Hardware
---

### Post by KaKuS on 2009-04-16
Hola gente, les comento. Ayer termine de armar un par de equipos, uno totalmente nuevo y otro viejo que mejore.

En los dos equipos tengo el mismo problema, así que la causa debo ser yo que cargue ambos equipos....:oops:#-o#-o

Pongo un CD con datos y lo veo bien
Pongo un DvD con datos y lo veo bien

Pongo un DVD-R virgen y no termina de montarlo nunca (Se queda parpadeando y después de un rato deja de hacerlo)

Lo mismo con DVD+R, DL, marca HP, marca Philips.... probé varias marcas y formatos. 

Pongo el DvD que no anda en ubuntu en una notebook con WinXP y lo detecta como DVD virgen.

Al intentar usar los distintos paquetes para grabación siempre tengo mensajes parecidos, "Inserte un DvD virgen, no hay media para grabar, no se detectaron medios... etc" lo cuál es lógico ya que nunca monto el medio virgen.

Busque en internet y encontré dos posibles soluciones (NINGUNA ME ANDUBO)
1 - Agregar all_generic_ide a la linea del Kernel
2 - Agregar el rw a la linea del fstab para darle permisos de escritura al dispositivo

La segunda seria lógica en el caso que detectase el medio pero no permitiera escribir en él, igual no funciono.

Datos de uno de los equipos que les puede servir:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=aaf64bf9-5b6d-4b48-9a97-4d465bdef261 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=fa49ce28-b5ad-4616-9fb3-20d11b4ff725 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		aaf64bf9-5b6d-4b48-9a97-4d465bdef261
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=aaf64bf9-5b6d-4b48-9a97-4d465bdef261 ro vga=792 splash
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```

Ambos sistemas están actualizados al día de hoy.
En ambos sistemas reconoce las grabadoras como "UNIDAD DE CD-RW / DVD+RW"
Las grabadoras funcionan
Los medios (CD-R, DVD-R. DVD+R) están OK

Nose que más probar, me vuele que fue en una de las ultimas actualizaciones algo dejo de funcionar.

AYUDA

---

### Post by KaKuS on 2009-04-16
Bueno les comento mi progreso. Probé todo lo que encontré y termine volviendo a instalar ubuntu en uno de los equipos. Antes de tirarle las 259 actualizaciones graba, luego de las actualizaciones simplemente deja de funcionar. Intente cargando otro Kernel, reinstalando el Nautilus y todos sus módulos.... nada.


Por ahora para safar, lo volví a cargar y no lo actualice. Graba y hace todo lo que debe hacer, así que voy a ir contra mi costumbre de tener todo al día y le desactive las actualizaciones. Por suerte cuento con varios equipos a mi disposición y voy a seguir probando.


Por lo que leí es un bug que anda dando vueltas desde la versión anterior más estable. Pero no se sabe bien por donde viene, simplemente deja de montar unidades si estas contienen un DVD vacío.

---

### Post by Mauro22 on 2009-04-16
Calculo que /media/cdrom0 existe, no? 


Mete el dvd virgen y monta la unidad a mano, a ver que error te da:

sudo mount -t iso9660 /dev/sdc /media/cdrom0


Y esto encontre por ahi:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Esto es lo que tenes en tu fstab:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0


Ahi tambien hay diferencias, si queres comenta (#) la que tenes vos y agrega la otra que tiene el exec,utf8 que es lo unico distinto.


\\:D/

---

### Post by KaKuS on 2009-04-17
> **Mauro22 said:**
> Calculo que /media/cdrom0 existe, no? 

Si, existe y el tengo permisos de R/W sobre esa carpeta

> **Mauro22 said:**
> 
Mete el dvd virgen y monta la unidad a mano, a ver que error te da:

sudo mount -t iso9660 /dev/sdc /media/cdrom0




Me da esto:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido
```

> **Mauro22 said:**
> 
Y esto encontre por ahi:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Esto es lo que tenes en tu fstab:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
Ahi tambien hay diferencias, si queres comenta (#) la que tenes vos y agrega la otra que tiene el exec,utf8 que es lo unico distinto.


\\:D/

Pasa lo mismo, metes un DvD Virgen y no lo reconoce, se queda titilando un rato y después para. Ningún paquete de grabación reconoce el medio en blanco. El nautilus nunca me tiro la ventana que aparece cuando metes un medio en blanco.

Hasta ahora solo evite el bug no actualizando. En cuanto pueda dedicarle mas tiempo le voy a ir tirando los parches de a uno, a ver cual es el que me complica la vida. 

Según parece no soy el único que al actualizar de la versión que viene en el .ISO oficial a la última disponible sin pasar por las del medio se queda sin grabar DvDs.

---

### Post by faktorqm on 2009-04-17
postea marca y modelo (si podes version de firmware) de cada una de las grabadoras. Salu2!

---

### Post by KaKuS on 2009-04-18
> **faktorqm said:**
> postea marca y modelo (si podes version de firmware) de cada una de las grabadoras. Salu2!

No le veo la vuelta ya que son dos equipos totalmente diferentes de distintas marcas y modelos en todos sus componentes.

DVD Equipo 1:
Fabricante: HL-DT-ST
Modelo: DVD-RAM GH22NS30
Frimware: "No aparece", si lo pido desde la consola me devuelve que no hay medios.
Conexion: SCSI (no deberia ser SATA?)

DVD Equipo 2:
Fabricante: PHILIPS
Modelo: DVD+-RW DVD8801
Serie: (nada)
Firmware: (nada)
Conexión: SCSI

Ahora tengo problemas hasta para leer, sera por meter tanta mano. Puse el CD de ubuntu, después de un rato lo leyó y montó pero no me lo ejecta. Al darle al ejecutar el nautilus me devuelve:
```
El volumen «Ubuntu 8.10 i386» probablemente se montó manualmente desde la línea de comandos.
Detalles
Device to unmount is not in /media/.hal-mtab so it is not mounted by HAL

```


```
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Cada vez entiendo menos.

---

