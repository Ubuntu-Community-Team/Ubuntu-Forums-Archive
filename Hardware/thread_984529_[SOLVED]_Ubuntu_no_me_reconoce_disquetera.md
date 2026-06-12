---
title: "[SOLVED] Ubuntu no me reconoce disquetera"
date: 2008-11-16
forum: Hardware
---

### Post by majatu on 2008-11-16
Como dice el titulo, no me aparece la disquetera por ningún lado y es muy raro porque antes en versiones anteriores de Ubuntu andaba de 10.

No es muy importante porque casi ni la uso pero me es raro, en Windows si anda bien :confused:

Alguna idea? Habrán quitado el soporte para disquetes?

Saludos!

---

### Post by guillermolisi on 2008-11-17
El soporte para diskettes sigue existiendo.

Si haces
```
ls -al /dev/f*
```
ves una linea que hace referencia a /dev/fd0 o no ?

En /media tenes un link y un directorio llamados floppy y floppy0 ?

Cuando pones un diskette, que haces inmediatamente ? Como intentas accederlo ?

---

### Post by majatu on 2008-11-17
La salida que me tira el comando **ls -al /dev/f*** es:

[B]lrwxrwxrwx  1 root root      13 2008-11-17 15:37 /dev/fd -> /proc/self/fd
crw-rw-rw-  1 root root  1,   7 2008-11-17 13:37 /dev/full
crw-rw----+ 1 root fuse 10, 229 2008-11-17 13:37 /dev/fuse[/B]

En /media no me aparece link a ninguna disquetera, solo a grabadoras.

y para acceder a disquetes, en versiones anteriores iba a Lugares/Unindad de Disquetes (o similar, no me acuerdo bien, pero era un icono) o en Equipo me aparecía sino.

por eso me es raro, Ubuntu ni se chistó de que tiene disquetera la pc :confused:

---

### Post by leosr on 2008-11-28
> **majatu said:**
> La salida que me tira el comando **ls -al /dev/f*** es:

[B]lrwxrwxrwx  1 root root      13 2008-11-17 15:37 /dev/fd -> /proc/self/fd
crw-rw-rw-  1 root root  1,   7 2008-11-17 13:37 /dev/full
crw-rw----+ 1 root fuse 10, 229 2008-11-17 13:37 /dev/fuse[/B]

En /media no me aparece link a ninguna disquetera, solo a grabadoras.

y para acceder a disquetes, en versiones anteriores iba a Lugares/Unindad de Disquetes (o similar, no me acuerdo bien, pero era un icono) o en Equipo me aparecía sino.

por eso me es raro, Ubuntu ni se chisto de que tiene disquetera la pc :confused:

Hola. Tengo el mismo problema y me aparece lo mismo. Con Hardy funcionaba.
Alguna idea?

Saludos.

---

### Post by faktorqm on 2008-11-28
Hola, tienen el modulo levantado para la diskettera?

Intrepid capaz lo obvio... eso lo pueden ver haciendo

```
lsmod | grep floppy
```

mi salida es esta (yo lo tengo, si no esta no aparece nada):

```
faktorqm@the-edge:~$ lsmod | grep floppy
floppy                 59588  0 
faktorqm@the-edge:~$ 

```

o sea que tengo el modulo levantado. Si no lo tienen lo pueden levantar con:

```
sudo modprobe floppy
```

y una vez que lo levantan, se fijan que onda con:

```
ls -la /dev/fd*
```

y mi salida es esta:

```
faktorqm@the-edge:~$ ls -la /dev/fd*
lrwxrwxrwx 1 root root       13 2008-11-28 07:18 /dev/fd -> /proc/self/fd
***brw-rw---- 1 root floppy 2,   0 2008-11-28 05:18 /dev/fd0***
brw-r----- 1 root disk   2,  84 2008-11-28 07:18 /dev/fd0u1040
brw-r----- 1 root disk   2,  88 2008-11-28 07:18 /dev/fd0u1120
brw-r----- 1 root disk   2,  28 2008-11-28 07:18 /dev/fd0u1440
brw-r----- 1 root disk   2, 124 2008-11-28 07:18 /dev/fd0u1600
brw-r----- 1 root disk   2,  44 2008-11-28 07:18 /dev/fd0u1680
brw-r----- 1 root disk   2,  60 2008-11-28 07:18 /dev/fd0u1722
brw-r----- 1 root disk   2,  76 2008-11-28 07:18 /dev/fd0u1743
brw-r----- 1 root disk   2,  96 2008-11-28 07:18 /dev/fd0u1760
brw-r----- 1 root disk   2, 116 2008-11-28 07:18 /dev/fd0u1840
brw-r----- 1 root disk   2, 100 2008-11-28 07:18 /dev/fd0u1920
brw-r----- 1 root disk   2,  12 2008-11-28 07:18 /dev/fd0u360
brw-r----- 1 root disk   2,  16 2008-11-28 07:18 /dev/fd0u720
brw-r----- 1 root disk   2, 120 2008-11-28 07:18 /dev/fd0u800
brw-r----- 1 root disk   2,  52 2008-11-28 07:18 /dev/fd0u820
brw-r----- 1 root disk   2,  68 2008-11-28 07:18 /dev/fd0u830
faktorqm@the-edge:~$ 

```

Si no pasa nada, les recomendaria enfaticamente que agreguen la linea de la diskettera en el fstab, en el mio esta asi:

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

eso se hace en gnome (ubuntu) con:

```
sudo gedit /etc/fstab
```

en kde (kubuntu) con:

```
sudo kate /etc/fstab
```

en xfce (xubuntu) con:

```
sudo mousepad /etc/fstab
```

y luego hagan:

```
sudo mount -a
```

Y luego fijense de vuelta. Si anda, para que tome los cambios en el proximo reinicio deberan hacer:

```
sudo gedit /etc/modules
``` o kate o mousepad :P

y agregan al final del archivo 

```
floppy
```

guardan y cuando reinicien ya no deberian tener problemas. Salu2!!! :KS

---

### Post by majatu on 2008-11-28
> **faktorqm said:**
> :KS

Muchas Gracias! como siempre, buena respuesta y super completa. Saludos!

:KS! jeje ;)

--- EDIT ---

Le ponen **Solved** al thread?

---

