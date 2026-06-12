---
title: "Duda con disco externo"
date: 2008-10-13
forum: Hardware
---

### Post by victor_nesta on 2008-10-13
Tengo un disco externo toshiba que uso de backup de mis datos, casi nunca lo saco a pasear, pero como digo "casi nunca". 
La idea es formatearlo a EXT3, pero cuando lo necesite para algún Window$, este no va a queres saber nada. 

¿Que idea se les ocurren, para tener un EXT3 y debes en cuando poder usar en una pc no libre?

Edito por si es relevante, tiene 320GB

---

### Post by santiagoward2000 on 2008-10-13
> **victor_nesta said:**
> Tengo un disco externo toshiba que uso de backup de mis datos, casi nunca lo saco a pasear, pero como digo "casi nunca". 
La idea es formatearlo a EXT3, pero cuando lo necesite para algún Window$, este no va a queres saber nada. 

¿Que idea se les ocurren, para tener un EXT3 y debes en cuando poder usar en una pc no libre?

Edito por si es relevante, tiene 320GB

Hola!
Se podría usar en Windows instalando [FS-Driver]("http://www.fs-driver.org/"). El tema es que tendrías que instalarlo en alguna máquina cada vez que lo saques a pasear.
Saludos!

---

### Post by victor_nesta on 2008-10-13
> **santiagoward2000 said:**
> Hola!
Se podría usar en Windows instalando [FS-Driver]("http://www.fs-driver.org/"). El tema es que tendrías que instalarlo en alguna máquina cada vez que lo saques a pasear.
Saludos!

Si es la única opción que conozco. y el problema no es solo el tener que instalarlo en cada maquina. Yo tuve una mala experiencia con eso de toquetear archivos ext3 en win de esa manera y quede con miedo.

---

### Post by ariel on 2008-10-13
> **victor_nesta said:**
> Si es la única opción que conozco. y el problema no es solo el tener que instalarlo en cada maquina. Yo tuve una mala experiencia con eso de toquetear archivos ext3 en win de esa manera y quede con miedo.

Hay otra opcion que yo use durante muchos años y jamás tuve problemas, 

[http://ext2fsd.sourceforge.net/index.htm](http://ext2fsd.sourceforge.net/index.htm)

Sigo usandolo de vez en cuando (hoy en dia casi todas las maquinas que uso son linux)

---

### Post by Mauro22 on 2008-10-13
Lo mas comodo es hacerlo en fat. De esta forma te evitas el uso de drivers para que te reconozca la particion ...

---

### Post by victor_nesta on 2008-10-13
Si pero un FAT en 320GB no termina siendo peor el remedio que la enfermedad?

Igual ya lo formatee a EXT3, :). 

Por ultimo, otra preguntita. En el disco me vino un programa para hacer backups automáticos, muy simple y muy copado, la cag*da es que solo para win o mac. En ubu lo estoy haciendo todo a mano.

¿Alguno sabe de algún programa para esto que sea bueno?

Gracias!!

---

### Post by Hei Ku on 2008-10-13
Para KDE, Keep.

---

### Post by victor_nesta on 2008-10-13
> **Hei Ku said:**
> Para KDE, Keep.

Bueno es una opción. Gracias :).
y para Gnome?

---

### Post by pol666 on 2008-10-13
Geep ? :P

no ni idea.

Mira, yo uso IFS esta muy bueno y ni me da problemas. Pero para un disco externo es molesto.

---

### Post by victor_nesta on 2008-10-13
Bueno gracias cumpas, ya me dieron una base, ahora google y a ver que info encuentro.

---

### Post by victor_nesta on 2008-10-13
Ya esta, probé el **Simple backup config/restore** (se encuentra en los repos) que esta bien, pero no el lo que estoy buscando, ya que me empaqueta todo en un .tgz.
Otra de las cosas es que funciona en 2plano, pero no te indica con nada que esta funcionando, por lo que podrías desmontar el disco en pleno funcionamiento :(. Me da la sensacion que esta orientado a un Backup mas de sistema que de archivos puntuales, en mi caso MP3, AVI, DOC y JPG 

Por lo que mire el Keep, es la aplicación que me hace falta, no lo probé todavía pero la interfaz es muy parecida al _Shawdow for PC/Mac_ que es el que me vino con el disco. La macana es que es KDE pero no es tan grave después de todo.

---

### Post by Hei Ku on 2008-10-13
Podrías probar con rsync, pero no recuerdo si tiene una interfaz gráfica.
Es un sincronizador de archivos.

---

### Post by victor_nesta on 2008-10-13
> **Hei Ku said:**
> Podrías probar con rsync, pero no recuerdo si tiene una interfaz gráfica.
Es un sincronizador de archivos.

Si, como opción esta buenisima. lastima que no tiene GUI. Igual por lo que vi no es tan jodido. 
[http://rsync.samba.org/](http://rsync.samba.org/)

---

### Post by chalito on 2008-10-16
> **victor_nesta said:**
> Si, como opción esta buenisima. lastima que no tiene GUI. Igual por lo que vi no es tan jodido. 
[http://rsync.samba.org/](http://rsync.samba.org/)

Yo uso rsnapshot, que se basa en rsync. Es bastante simple, 

Otra opcion a seguir de cerca es esta (no la conozco, recien la encuentro googleando un poco) :
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

---

### Post by victor_nesta on 2008-10-16
Gracias! La cheko como dicen mas al norte

---

