---
title: "Grub"
date: 2011-04-10
forum: Instalación y Actualización
---

### Post by Grasber on 2011-04-10
Hola, lo que  pasa es que instalé Ubuntu 10.10 en mi disco secundario, que particioné  en: 1. disco sin formato (50 GB) 2. disco ext4 (para Ubuntu) 3. swap (al  final del disco).
Cuando en la instalación me preguntó dónde quería poner el boot loader o algo asi, le dije que en el disco secundario.

La cosa es que instaló todo bien y reinicié incluso y el grub se portó  bien (me detectó también mi particion con Win7), pero cuando en Win7  borré la partición sin formato de 50GB que había creado para formatearla  con NTFS dejó de funcionar el Grub, al parecer algo tenía instalado  ahí.

Ahora cuando parte el pc me aparece la consola Grub rescue. En ella puedo tipear comandos para hacer partir Ubuntu.
(Las unidades que se pueden reconocer desde esta consola son [comando  ls]:  (hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)  (hd2) (hd2,msdos1) (fd0))

Lo que pasa ahora es que ejecuto el comando sudo grub-update dentro de  Ubuntu y no funciona. Tengo que aclarar que antes de ejecutar el comando  grub-update mi archivo grub.cfg tenía referencias a la unidad  (hd0,msdos3) que no sé cual es [IMG]https://www.u-cursos.cl/uchile/diseno/images/emoticons/xd.png[/IMG].  Luego de ejecutar sudo grub-update las referencias en el archivo  cambiaron a la unidad (hd0,msdos2), la cual es la que booteo desde la  consola de grub rescue y que me funciona para hacer partir Ubuntu desde  Grub rescue. Luego reinicio y no funciona, aparece Grub rescue otra vez.  Veo desde la consola de grub rescue a dónde tiene las referencias y las  tiene a la unidad anterior (hd0,msdos3).

No sé sí cacharon el problema, sino lo cacharon lo explico de nuevo [IMG]https://www.u-cursos.cl/uchile/diseno/images/emoticons/big_smile.png[/IMG]

aquí está el grub.cfg que tengo
[pastebin.com/CpvfcGxp]("http://pastebin.com/CpvfcGxp")

---

### Post by Grasber on 2011-04-11
Solucionado ;)

[http://ubuntuforums.org/showthread.php?p=10662477](http://ubuntuforums.org/showthread.php?p=10662477)

---

