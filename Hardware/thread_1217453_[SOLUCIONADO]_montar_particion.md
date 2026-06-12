---
title: "[SOLUCIONADO] montar particion"
date: 2009-07-19
forum: Hardware
---

### Post by darky! on 2009-07-19
hola, mi problema es el siguiente ahora cuando inicio mi ubuntu abro la particion de windows manualmente y ningun problema, puedo acceder a su informacion modificar y hacer lo q quiera en ella, lo q quiero es  q al iniciar ubuntu mi particion de windows ya este montada y poder crear enlaces de las carpetas ya q ahi es donde tengo toda mi musica y cosas.


ya habia preguntado esto antes en el foro antiguo y me dijeron q agregara esta linea 
al           archivo fstab 

>   /dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0pero al hacerlo y reiniciar ubuntu, me aparece montada la particion pero no puedo modificar
ni borrar nada y tampoco crear enlaces.

q puedo hacer???

de antemano gracias.

---

### Post by pagondel on 2009-07-19
Intenta cambiar el dueño del directorio con chown:

```
chown -R tuUsuario /media/windows
```

EDIT: [Aca](http://ubuntuforums.org/showthread.php?p=7634793#post7634793) Carlos_C explica mas detallado ;)

---

### Post by darky! on 2009-07-19
hice lo que me dijiste, pero me decia operacion no permitida en todo :(, asi q los permisos
siguieron iguales.

aca un ejemplo cmo de las 1000 lineas q me me mando.
> 
chown: cambiando el propietario de «/media/windows/Archivos de programa/Image-Line/FL Studio 8/Plugins/Fruity/Generators/Slicex/Data/Default/Pan.fnv»: Operación no permitida



[[IMG]http://img169.imageshack.us/img169/2295/pantallazo.th.png[/IMG]]("http://img169.imageshack.us/i/pantallazo.png/")
[IMG]http://img169.imageshack.us/i/pantallazo.png/[/IMG]

---

### Post by moreback on 2009-07-19
Borra esa línea de tu /etc/fstab y aplica lo que dice este link: [http://pcarmona.wordpress.com/2009/04/12/montar-discos-de-windows-al-logearse-en-gnome/](http://pcarmona.wordpress.com/2009/04/12/montar-discos-de-windows-al-logearse-en-gnome/)

Saludos.

---

### Post by darky! on 2009-07-20
me funciono usando gnome-mount y colocando "gnome-mount -d /dev/sda1&#8243;" :P

muxas gracias!!!

---

