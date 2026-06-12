---
title: "Problema para montar particiones"
date: 2009-02-09
forum: Hardware
---

### Post by Criminel on 2009-02-09
Hola,
Habiendo leído varios foros aún tengo problemas para lo siguiente:

En un disco de 80GB tenía una partición de XP que borré (de 21GB el gparted me dejó una micro partición de 384MB que descoozco para qué la usa). Intenté darle formato ext3 a los 20MB restantes para usarlos bajo Ubuntu, pero al montar la partición (cosa que hice por consejo de un foro en /media) el "disco" no aparece por ninguna parte, y además se me anula el lectograbador de DVD (ese problema lo he corregido volviendo a anular la partición de 20GB y desmontándola).

No sé qué hago mal, pero el objeto es tener esos 20Gb disponibles para data bajo Ubuntu.

¿Hay otra solución que no sea formatear la máquina e instalar todo desde cero?

Gracias.

---

### Post by Dies on 2009-02-09
> **Criminel said:**
> 

¿Hay otra solución que no sea formatear la máquina e instalar todo desde cero?

Gracias.

Seguro.

Empecemos con los resultados de

```
sudo fdisk -l
```

---

### Post by Criminel on 2009-02-10
La respuesta a eso es:
"el punto de montaje no existe"

---

### Post by sajnox on 2009-02-11
Esa respuesta no puede ser para la salida de ese comando

Abri una terminal y escribi nuevamente

```
sudo fdisk -l
```

Copia y pega todo lo que aparezca (para copiar desde la terminal tenes que hacer ctrl+shift+c en la terminal y ctrl+v en la pagina)

Saludos

---

### Post by Criminel on 2009-02-13
Disco /dev/sda: 80.0 GB, 80032038912 bytes
255 cabezas, 63 sectores/pista, 9730 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x70994fbd

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          47      377496   83  Linux
/dev/sda2            2862        9730    55175242+   5  Extendida
/dev/sda5            2862        9444    52877916   83  Linux
/dev/sda6            9445        9730     2297263+  82  Linux swap / Solaris

---

### Post by Dies on 2009-02-13
> **Criminel said:**
> Disco /dev/sda: 80.0 GB, 80032038912 bytes
255 cabezas, 63 sectores/pista, 9730 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x70994fbd

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1          47      377496   83  Linux
/dev/sda2            2862        9730    55175242+   5  Extendida
/dev/sda5            2862        9444    52877916   83  Linux
/dev/sda6            9445        9730     2297263+  82  Linux swap / Solaris

Por favor dar esos resultados despues de haber creado la partición que planea usar.

Edit -

Para ahorrar tiempo vamos a decir que la partición que se va a utilizar es "/dev/sda3" ;)

Primero le damos un nombre con

```
sudo e2label /dev/sda3 EXAMPLE
```

claro que EXAMPLE debe ser reemplazado con algo que tenga mas sentido para el uso. Ahora hacemos un lugar para poner la partición 

```
sudo mkdir /media/EXAMPLE
sudo cp /etc/fstab /etc/fstab-original
gksudo gedit /etc/fstab

```

y la añadimos al fstab

```
LABEL=EXAMPLE  /media/EXAMPLE  ext3   auto,user,rw,relatime   0  0
```

ya se puede montar con

```
sudo mount -a
```

Si después de un "restart" no aparece en su carpeta para no tener que ir a /media/EXAMPLE todo el tiempo podemos hacer

```
ln -s /media/EXAMPLE ~/Desktop/
```

Buena suerte.  :)

---

### Post by Criminel on 2009-02-17
e2label: No es un directorio mientras se intentaba abrir /dev/sda3/DATOS
No se pudo encontrar un superbloque válido para el sistema de ficheros.
drutus@drutus-desktop:~$ sudo e2label/dev/sda3/DATOS
sudo: e2label/dev/sda3/DATOS: command not found
drutus@drutus-desktop:~$ sudo e2label /dev/sda3/DATOS
e2label: No es un directorio mientras se intentaba abrir /dev/sda3/DATOS
No se pudo encontrar un superbloque válido para el sistema de ficheros.


Y ahí se trabó.

¿Alguna idea?

---

### Post by Criminel on 2009-02-17
Pude seguir, pero ahora me trabé aquí:


ntfs-3g: Failed to access volume '/dev/hda1': No existe el fichero ó directorio
Please type '/sbin/mount.ntfs --help' for more information.
NTFS signature is missing.
Failed to mount '/dev/sda1': Argumento inválido
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
mount: el dispositivo especial Disco de datos 21 GB no existe
mount: el punto de montaje /media/DATOS no existe
drutus@drutus-desktop:~$

---

