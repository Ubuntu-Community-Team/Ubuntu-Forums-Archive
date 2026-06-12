---
title: "montar disketera al inicio en xubuntu 8.10"
date: 2009-06-20
forum: Hardware
---

### Post by ciriaco on 2009-06-20
Saludos.

No he podido montar la disketera en xubuntu.  Tengo la siguiente linea en fstab, pero me da la impresión que es erronea:

/dev/fd0 /media/floppy vfat rw,user,noauto,exec,utf8 0 0

El asunto es que el sistema me dice que el file system está mal, o que /dev/fd0 no es un dispositivo de bloques válido.

Ayuda please!

Gracias.

---

### Post by Carlos C on 2009-06-22
Te recomiendo hacer un respaldo de tu archivo fstab y luego probar con:
```
/dev/fd0        /media/floppy  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by moreback on 2009-06-22
Tengo la impresión que le falta hacer

**```
sudo modprobe floppy
```**antes de montar la disquetera.

---

### Post by ciriaco on 2009-06-25
Gracias por las respuestas.

sudo modprobe floppy lo hice y agregué el floppy en modules.

Intentaré nuevamente con la linea que sugieres Carlos.

---

### Post by kamus on 2009-06-26
> 
```
/dev/fd0        /media/floppy  auto    rw,user,auto,exec 0       0
```


Esto debería funcionar..

---

### Post by ciriaco on 2009-07-11
Saludos,

Probé poniendo vfat y sólo monta diskettes que hayan sido formateados con dos.  Pongo con auto y tampoco reconoce discos que se hayan formateado en un sistema linux.

Ej:  formateo un diskette de inicio para un thinclient para edulinux, que está basado en Fedora fc4, y al tratar de montarlo en xubuntu teniendo la línea sugerida en el fstab, me da un error diciendo que no se puede determinar el tipo de sistema de archivo.

Me es imposible abrir diskettes.  ¿Alguna idea del problema?


Gracias

---

### Post by kamus on 2009-07-11
> **ciriaco said:**
> Saludos,

Probé poniendo vfat y sólo monta diskettes que hayan sido formateados con dos.  Pongo con auto y tampoco reconoce discos que se hayan formateado en un sistema linux.

Ej:  formateo un diskette de inicio para un thinclient para edulinux, que está basado en Fedora fc4, y al tratar de montarlo en xubuntu teniendo la línea sugerida en el fstab, me da un error diciendo que no se puede determinar el tipo de sistema de archivo.

Me es imposible abrir diskettes.  ¿Alguna idea del problema?


Gracias

Probaste montando el disco de forma manual? Realmente esta bueno ese disco? Si fue formateado para linux probablemente esta formateado en ext3 o ext2, fuerza el parametro para el sistema de archivos haber que sucede..

---

### Post by ciriaco on 2009-07-14
Al parecer es un problema de diskette, digo al parecer pues he probado con varios y los monto y desmonto sin inconvenientes, pero el disco en cuestión es uno de inicio para un cliente liviano de edulinux y arranca sin problemas.

Entonces, me queda la duda de por qué no lo puedo leer en xubuntu.  Trataré de formatearlo y hacer nuevo el disco de inicio, a ver que pasa.


Gracias a todos.

---

