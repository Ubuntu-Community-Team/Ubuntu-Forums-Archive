---
title: "Desaparece el Grub al instalar XP"
date: 2009-09-16
forum: Instalación y Actualización
---

### Post by Visente on 2009-09-16
Acabo de instalar Xp en una partición secundaria; lo necesito para utilizar algunos programas que necesitan bastante RAM para arrancar, así que no puedo hacerlo con VirtualBox.

Al instalarlo ha desaparecido el GRUB y no puedo elegir el sistema operativo. Es como si XP hubiera tomado el control e ignorara que hay otro... xD

¿Hay forma de solucionarlo desde XP?

No puedo utilizar el disco Live de ubuntu (bueno, supongo que con un poco de cabezonería podría, pero tengo algunos problemas); sólo funciona la instalación *alternate*.

---

### Post by Carlos C on 2009-09-16
Hola. Creo que tu problema es que perdiste el GRUB al instalar windows y debes recuperarlo. Te recomiendo que leas lo que dice la Guía Ubuntu al respecto:

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

Saludos.

---

### Post by gmunioz on 2009-09-16
Hola vis....:


Inicia con el alternate cd

Elige:

Restaurar sistema

Reinstalar GRUB

Contesta en que sector del disco (mbr)

---

### Post by 3nG3ndR0 on 2009-09-16
como te dice carlos c. yo ocupo la opción 2 es la mas fácil para mi, tienes que iniciar con el livecd y en el terminal ejecutar los siguientes comandos.

** Opción 2 **

 
[LIST=1]
[*] Desde una consola ejecutamos los siguientes comandos:
[/LIST]
 $ sudo grub                *--> ejecutamos el interprete de comando de grub*
> find /boot/grub/stage1   *--> busca donde esta la partición de ubuntu*
> root (hdX,Y)             *--> poner el valor devuelto anterior*
> setup (hd0)              *--> instala grub en nuestro primer disco duro (hd0), *
                               *que es con el que inicia la computadora*
> quit                     *--> salimos del interprete de comando de grub*

---

### Post by kamus on 2009-09-16
eso es porque sobre escribiste el registro del MBR blablabla.., lo que yo hago es arrancar con un live cd y luego:

1)creo una carpeta llamada temporal (mkdir temporal)

2)monto la partición donde tenia montado anteriormente la raiz del sistema (/), digamos que era /dev/sda2

3)luego ejecuto grub-install --root-directory=temporal/ --recheck /dev/sda

4)Fin, reinicio el equipo y ya.

---

### Post by moreback on 2009-09-18
Mmmh... cada uno tiene su método, yo a veces uso el [Super Grub Disk]("http://www.supergrubdisk.org/"), pero tengo la impresión que se podría hacer con el Live CD de Ubuntu. ¿Alguien sabe cómo?

---

### Post by Carlos C on 2009-09-19
> **moreback said:**
> Mmmh... cada uno tiene su método, yo a veces uso el [Super Grub Disk]("http://www.supergrubdisk.org/"), pero tengo la impresión que se podría hacer con el Live CD de Ubuntu. ¿Alguien sabe cómo?

En el enlace de la Guía Ubuntu que señalé antes sale cómo hacerlo con el Live CD.

Saludos.

---

