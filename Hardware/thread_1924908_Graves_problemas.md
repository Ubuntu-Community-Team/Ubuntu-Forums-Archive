---
title: "Graves problemas"
date: 2012-02-13
forum: Hardware
---

### Post by Vero1 on 2012-02-13
Hola a todos,

Así es. Tengo graves problemas con mi SO. Uso Ubuntu 11.10.
No sé por dónde empezar...
Bueno, tengo problemas con el Update Manager, con el Centro de Soft y con todo programa que tenga algo que escribir.
El sistema está como lectura solamente y no sé la razón.
Hice fsck con un Live CD y me informó que todo estaba ok????
Cuando corro la herramienta de recuperación(al inicio) me salen muchos errores. Algunos son: Host bus error, mountall:Error fsck no recuperable: /boot, error serio controlador disco para /home, habla de journal y de superbloques y no sé cuántas cosas mas.
Ya he enviado reporte a Launchpad sobre Update Manager y me indicaron unos comandos que no funcionaron. No puedo actualizar, no puedo usar Synaptic, no puedo usar el Centro de Soft.
Firefox se cuelga al igual que Thunderbird.
Cuando hace el fsck informa que algunas particiones tienen bloques no contíguos. Aparentemente no arregla nada el modo de recuperación.
Ubuntu no tiene una herramienta parecida al Defrag de Windows?
La verdad es que no sé qué hacer ya y lo peor es que no sé a qué se debe todo ésto.
Me dicen que puede ser algun corte de luz( que sí hubo) pero cuando pasa éso de inmediato apago la computadora.

Espero que me puedan dar una mano con ésto.
Si necesitan mas datos, me los piden sin problemas.

Gracias desde ya y saludos

---

### Post by Vero1 on 2012-02-17
Hola,
Bueno, Launchpad me solucionó el Update Manager con un comando que me indicó.Ahora, ya puedo usarlo y tambien Synaptic y el Centro de Soft.
Lo que no se soluciona es el problema del disco que se monta como SOLO LECTURA. Por lo tanto no me deja guardar, contestar mails y todo lo que tenga que ver con escritura.
En los chequeos que hago con la consola de recuperación, me hace el fsck, dice ARREGLADO pero despues en cada reinicio es como si nada se hubiera arreglado. 
Entre otros errores indica "host bus error", habla de Superbloques y hace referencia a la hora del hardware que se programó o algo así EN EL FUTURO...
Por favor, cómo se puede revertir el disco de solo lectura? Qué herramientas se pueden usar, aparte de fsck(que tambien usé con un Live CD), para arreglar el sistema de archivos?
Necesito, por favor, una soloución urgente porque usar así el SO es una tortura.

Espero su ayuda y desde ya muchas gracias

---

### Post by WthIteh on 2012-02-17
It's possible to remount a read-only filesystem with read/write option by (replace /dev/sda1 with the read-only mounted partition):
```
mount -o rw,remount /dev/sda1
```

---

### Post by Vero1 on 2012-02-17
Gracias por contestar WthIteh,

Tengo una pregunta:

En mi caso sería sdb1 y es donde está /boot

Estaría bien  

mount -o rw,remount /dev/sdb1   ?

Gracias

---

### Post by granjero on 2012-02-17
Vero1, posteá la salida de ```
sudo fdisk -l
``` y también la salida de ```
cat /etc/fstab
``` así vemos como esta particionado tu HD y como monta el sistema las particiones.

salud!

---

### Post by Vero1 on 2012-02-17
Hola Granjero:

Disco /dev/sda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros, 80293248 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x4f744f74

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    77288714    38644326    7  HPFS/NTFS/exFAT
/dev/sda2        77288715    80292869     1502077+   5  Extendida
/dev/sda5        77288778    80292869     1502046    7  HPFS/NTFS/exFAT

Disco /dev/sdb: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros, 156301488 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x2b2e2b2d

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *          63    39070079    19535008+  83  Linux
/dev/sdb2        39070080    92309489    26619705   83  Linux
/dev/sdb3        92309490   152344394    30017452+  83  Linux
/dev/sdb4       152344395   156296384     1975995   82  Linux swap Solaris


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=d7b5b274-099d-4475-b2c1-65c10011955d /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=b7c099a1-1a9a-45be-8314-4ac654a82325 /boot           ext3    defaults        0       2
# /home was on /dev/sdb3 during installation
UUID=b2c67cfd-5f98-42b4-aa2a-306a9aadf4d1 /home           ext3    defaults        0       2
# swap was on /dev/sdb4 during installation
UUID=459cf53e-7ca3-4f0c-a6ec-3e0ce4740e9c none            swap    sw              0       0

Granjero, aparte de todo ésto, vos a veces estás en ubuntu-es?

Gracias y saludos

---

### Post by granjero on 2012-02-17
Vero1, Fiajte que / lo tenés en /dev/sdb2 y tu home en /dev/sdb3

```
# / was on /dev/sdb2 during installation
UUID=d7b5b274-099d-4475-b2c1-65c10011955d / ext3 errors=remount-ro 0 1
# /home was on /dev/sdb3 during installation
UUID=b2c67cfd-5f98-42b4-aa2a-306a9aadf4d1 /home ext3 defaults 0 2

```

Me parece que está bien el fstab. Ahora podés hacer lo que te dice WthIteh.

Con respescto a la mención de un sistema hecho en el futuro es porque tenés la fecha mal en la bios. 

Y con respecto a lo que preguntás de #ubuntu-es sí, si dice granjero el nick debo ser yo \\:D/ También ando por #ubuntu-ar. siempre conectado pero poco frente a la pantalla

salud!

---

### Post by Vero1 on 2012-02-17
ok haré lo que dice el amigo.


Lo que me comentas de la ubicación de /home y /raíz, es un comentario nada mas o debo revisar algo?

En cuanto al reloj de BIOS, me fijé justamente hoy y está correcto, me parece. En pantalla, por ejemplo, figura la fecha y la hora correcta. No sé qué pueda estar mal en BIOS.

Así que sos vos el de ubuntu-es. Ultimamente están un poco perezosos para contestar consultas o me parece a mi?

Los únicos que contestan, a veces, son fosco y mimecar.

Y... ya que estamos, sabés algo de er-USUL? Hace mucho que no se lo ve en ubuntu-es.

saludos

---

### Post by granjero on 2012-02-17
Lo que te comentaba de la ubicación es para que puedas ejecutar el comando que te pasó WthIteh sobre la partición problemática. 

A mi una vez me pasó que me al iniciar me decía que el filesystem se había creado en el futuro y era porque le había sacado la pila al mother y estaba con la fecha que viene de fábrica. 1990 o por ahí. Cuando le puse la fecha correcta dejo de decirme eso.

Por el canal de ayuda, tené en cuenta que son/somos todos voluntarios, así que mucho no se puede exigir. :D

salud!

---

### Post by Vero1 on 2012-02-19
Hola granjero,

Si bien saqué la pila para poner una nueva, luego pasé por BIOS y cambié la fecha y la hora, como debía ser.

En cuanto al canal de ayuda, sé que todos son/somos voluntarios pero de ahí a ni siquiera contestar tu saludo hay un trecho.

Aparte, años atrás había otra gente que ayudaba mucho, entre ellos er-USUL que lamentablemente no está más y no sé por que. Pregunté pero no supieron contestar.

Hice lo que recomendó el amigo pero de nada sirvió. 

salud!

---

### Post by granjero on 2012-02-19
Que lástina que no anduvo. Otra cosa que se me ocurre es que abras un nautilus como root alt+F2 ```
gksudo nautilus
```y le des click derecho a la partición sobre la que no tenés derecho de escritura, como si quisieras crear una carpeta pero vayas a propiedades y en la solapa permisos le pongas como dueño y grupo a tu user y le des permiso de crear y eliminar archivos.


:KS

---

### Post by Vero1 on 2012-02-19
Lo malo es que es todo el disco, que tiene 3 particiones.

Cuando reinicio la máquina, directamente abre como lectura.
Para tener lectura/escritura tengo que empezar con la Consola de Recupèración e indicarle que remonte todo. Eso permite despues escribir tambien- Esto en cada reinicio. Lindo no?

En fin, me estoy volviendo monaaaaaaaaa.

Gracias Granjero.

---

### Post by Vero1 on 2012-02-20
Buenas,
Sigo con problemas todavía mas gordos ahora.
Ayer parecía que todo estaba bien.
Actualicé BIOS y marchaba todo a las mil maravillas.
Hoy encendí el equipo y salieron errores nuevamente.
Hice fsck con Live CD.
Cuando reinicié me salió la pantalla negra diciendo:

hda1 out of disk (nada menos)
Ahora escribo desde Windows.

hda1 o sea para mi sdb1 es el boot, por lo tanto ahí me quedo sin poder siquiera correr la consola de reparación.

La verdad que ahora sí no sé qué hacer. 
Cómo recupero el hda1?

Espero que alguien me saque de este atolladero.

Desde ya  muchas gracias
p.d.
Por si sirve tengo el Super-Grub Disk2.

saludos

---

