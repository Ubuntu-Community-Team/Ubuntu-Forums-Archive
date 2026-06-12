---
title: "No soy propietario de mi disco (?)"
date: 2009-04-01
forum: Hardware
---

### Post by KaKuS on 2009-04-01
Buenas, disculpen si mi cuestión es muy básica.

Me compre un disco nuevo de 160GB, use el gparted y cree una partición ext3, luego agregue una línea en el fstab para montarlo. Pero no puedo crear carpetas dentro del disco y cuando voy a propiedades me dice que el propietario es root y que mi usuario no puede hacer nada.


Que hice mal?
Mi fstab:
```
proc                                       /proc          proc         defaults                    0  0  
UUID=111c357e-e6de-4dc4-9118-816b261aa065  /              ext3         relatime,errors=remount-ro  0  1  
UUID=fa49ce28-b5ad-4616-9fb3-20d11b4ff725  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdc1                                  /media/sdc1    ext3         defaults                    0  0  
```

Saludos

---

### Post by Hei Ku on 2009-04-01
o cambias el fstab para que lo monte como user, y te das permisos en el punto de montaje, o en el administrador de discos le pones que el propietario sea user y no root.

---

### Post by clasificado on 2009-04-02
fiajte que el scd0 tiene un "user" que el sdc1 no tiene

agregaseló, que es para eso

Es que los puntos de montaje de fstab estan pensados para una perspectiva de root. Para habilitar usuarios y grupos extra hay que agregarle switches en el lugar de los options

clasificado

---

### Post by KaKuS on 2009-04-02
Bueno ahora mi fstab es:

```
proc                                       /proc          proc         defaults                    0  0  
UUID=111c357e-e6de-4dc4-9118-816b261aa065  /              ext3         relatime,errors=remount-ro  0  1  
UUID=fa49ce28-b5ad-4616-9fb3-20d11b4ff725  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdc1                                  /media/sdc1    ext3         user  
```

Pero tengo el mismo problema, ¿algún alma caritativa me daría los pasos a prueba de nabos (como yo)?

---

### Post by pablo.s on 2009-04-02
Probá lo siguiente:

sudo apt-get install pysdm

Es un gestor de discos con asistente programado en... 
PyGTK (vamos ******!) que te resolverá la cuestión.

Saludos.

---

### Post by Hei Ku on 2009-04-02
Tenes que fijarte tambien que el punto de montaje tenga permisos para tu usuario

Eso lo podes ver con un click derecho sobre esa carpeta.

---

### Post by exegeses on 2009-04-02
veamos qué permisos y grupos tienen sus otros dispositivos
digo, por ahí ayuda antes de modificarlos

no se olviden que siempre hay un grupo **disk** para los sda

y ojo, que suelen estar ocultos. no es lo mismo hacer un ls -al en /dev que en /media

calculo que con agregar el punto de montaje al grupo **plugdev** podría alcanzar.
voy a investigar a ver qué encuentro.
saludos

---

### Post by exegeses on 2009-04-02
> **KaKuS said:**
> Bueno ahora mi fstab es:

```
proc                                       /proc          proc         defaults                    0  0  
UUID=111c357e-e6de-4dc4-9118-816b261aa065  /              ext3         relatime,errors=remount-ro  0  1  
UUID=fa49ce28-b5ad-4616-9fb3-20d11b4ff725  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdc1                                  /media/sdc1    ext3         user  
```

Pero tengo el mismo problema, ¿algún alma caritativa me daría los pasos a prueba de nabos (como yo)?


perdón, corrijo mi burrada.
faltan los permisos de lectura/escritura  ese 0 del final, tenés que cambiarlo por un 1.  ese número representa el Bit de Permiso de Lectura/Escritura para el Dispositivo de Almacenamiento.

debería quedar así.

```
proc                                       /proc          proc         defaults                    0  0  
UUID=111c357e-e6de-4dc4-9118-816b261aa065  /              ext3         relatime,errors=remount-ro  0  1  
UUID=fa49ce28-b5ad-4616-9fb3-20d11b4ff725  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdc1                                  /media/sdc1    ext3         user       [COLOR="DarkSlateBlue"]**0  1  **[/COLOR]
```

probalo y contanos.
saludos

---

### Post by josecuervo86 on 2009-04-02
Hago una pregunta que talves sea super-****** pero no tendria que tener los mismos permisos que el otro disco? o sea, copiar los mismos?

---

### Post by KaKuS on 2009-04-02
Creo que lo solucionaron.

Mi fstab quedo así:

```
proc                                       /proc          proc         defaults                    0  0  
UUID=111c357e-e6de-4dc4-9118-816b261aa065  /              ext3         relatime,errors=remount-ro  0  1  
UUID=fa49ce28-b5ad-4616-9fb3-20d11b4ff725  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdc1                                  /media/Tools   ext3         users	                   0  1  
```

Además ejecute el Nautilus como root, cambie los permisos del punto de montaje /media/tools y santo remedio.

Muchas gracias a todos y perdon por mi ignorancia.....

---

### Post by clasificado on 2009-04-03
me alegro por vos!

con tu resultado aprendemos todos

clasificado

---

