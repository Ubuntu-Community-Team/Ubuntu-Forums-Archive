---
title: "Instalar un windows xp o vista, despues de haber instalado ubuntu 9.04"
date: 2009-05-20
forum: Instalación y Actualización
---

### Post by hiphosama on 2009-05-20
hola
me gustaria saber si es recomendable instalar windows xp o un vista, despues de haber instalado ubuntu 9.04, la instalacion de ubuntu esta ocupando todo el disco duro.

quiero saber especificamente si va a funcionar el sistema para elegir con que disco arrancar de ubuntu, creo que GRUB.
es recomendable o no tendre problema alguno con hacer esto. leei por ahi que era mejor instalar windows y luego ubuntu.

por la dudas tengo presario3000 v3418la, cualquier dato me lo piden. el xp que pienso instalar es el windows ue sp3 2009.1 o sino el vista que venia con el compu pero eso es solo en caso extremo, si ahi otro xp que funke recomiendenlo. de ubuntu no me despego ni cagando

---

### Post by felipeleven on 2009-05-20
Si instalas Windows Xp o Windows Vista posteriormente a haber instalado Ubuntu, Windows sobreescribirá su gestor de arranque y se perderá grub, por lo que solo podrás iniciar windows.

Para estos casos lo que hice una vez fue instalar windows posteriormente a haber instalado Ubuntu, se perdió mi grub y quedó el gestor de arranque de windows, para solucionarlo lo que hice fue descargar un programa llamado **Super Grub Disc** que se graba a un CD o usb y se pone en el PC antes de iniciarlo y al prenderlo te dará opciones para recuperar el Grub y mucho más.

Tambien se puede recuperar a través de el live cd de ubuntu pero lo intenté y no pude :(.

Te dejo las siguientes pa&#501;inas:

-Página oficial de Super Grub Disc: [URL="http://supergrub.forjamari.linex.org/"]http://supergrub.forjamari.linex.org/
[/URL]
-Guia de como recuperar el grub (Guia-ubuntu.org): [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

Espero que te sea de utilidad, saludos :p

---

### Post by hiphosama on 2009-05-20
> **felipeleven said:**
> Si instalas Windows Xp o Windows Vista posteriormente a haber instalado Ubuntu, Windows sobreescribirá su gestor de arranque y se perderá grub, por lo que solo podrás iniciar windows.

Para estos casos lo que hice una vez fue instalar windows posteriormente a haber instalado Ubuntu, se perdió mi grub y quedó el gestor de arranque de windows, para solucionarlo lo que hice fue descargar un programa llamado **Super Grub Disc** que se graba a un CD o usb y se pone en el PC antes de iniciarlo y al prenderlo te dará opciones para recuperar el Grub y mucho más.

Tambien se puede recuperar a través de el live cd de ubuntu pero lo intenté y no pude :(.

Te dejo las siguientes pa&#501;inas:

-Página oficial de Super Grub Disc: [URL="http://supergrub.forjamari.linex.org/"]http://supergrub.forjamari.linex.org/
[/URL]
-Guia de como recuperar el grub (Guia-ubuntu.org): [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

Espero que te sea de utilidad, saludos :p

Vere las paginas.
gracias por la ayuda
espero no tener que ocupar windows pero nunca se sabe.

---

### Post by augias on 2009-05-28
para los que vengan a ver este tema posteriormente, dejo el contenido clve del grub how-to posteado. A mi me sirvio mucho instalando diferentes distros de linux y windows tambien.

Cargando el livecd de ubuntu, abre una consola y escribe:
```
sudo grub
```
el sudo es importante. no te pedira clave

una vez en grub escribes: 

```
root (hd0,0)
```

donde hd0,0 es el disco y la particion donde tienes ustalado ubuntu actualmente. si ubuntu esta en la primera particion, sera hd0,0. si es la segunda particion, sera en hd0,1. y asi consecutivamente.

luego

```
setup (hd0)
```

y

```
quit
```

y reinicias. tendras tu grub como antes + windows.

si no aparece windows, desde ubuntu tienes que editar el menu.lst de grub

escribes en una consola en ubuntu

```
sudo gedit /boot/grub/menu.lst
```

Baja al fondo de la lista y escribe lo siguiente:
```

title Windows XP
root (hd0,1)
makeactive
chainloader +1 
```

nuevamente, usando (hd0,X) dependiendo del lugar de tu particion windows.

---

### Post by moreback on 2009-05-29
El [Super Grub Disk]("http://www.supergrubdisk.org") salva bastante :-)

---

### Post by AlvaroV on 2009-05-30
> **hiphosama said:**
> Vere las paginas.
gracias por la ayuda
espero no tener que ocupar windows pero nunca se sabe.


¿Y para que podrías necesitar Windows?

Saludos

---

### Post by moreback on 2009-05-30
> **AlvaroV said:**
> ¿Y para que podrías necesitar Windows?

Saludos

De hecho si fuera necesario (algún programa importante para el cual sólo hay versión para win32) es mejor instalarlo en una máquina virtual de VirtualBox, así lo tienes más controlado.

---

### Post by aolivares on 2009-06-02
De todas formas si lo que quieren es recuperar grub después de instalar el xp, aquí una chiquilla explica como se hace (Gracias Carlos_C por el dato)

[http://nixiepixel.com/blog/blog7.php/video-quickies-from-linuxhaxor](http://nixiepixel.com/blog/blog7.php/video-quickies-from-linuxhaxor)

Basicamente es lo mismo que puso augias, pero el video es imperdible

---

### Post by Patriciologico on 2009-06-04
Jajaa y seguimos con los videos, nunca debi compartirlo!

---

