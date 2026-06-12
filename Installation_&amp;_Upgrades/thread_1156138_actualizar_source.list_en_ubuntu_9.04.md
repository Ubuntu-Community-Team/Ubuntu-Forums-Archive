---
title: "actualizar source.list en ubuntu 9.04"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by mikflichy on 2009-05-11
Hola compañeros.
Acabo de actualizar a Ubuntu 9.04. Se me ha desinstalado la barra avant window navigator y ahora no me deja instalarla de nuevo.
He intentado modificar las lineas necesarias en source.list, pero me dice que hay un error en la linea 52. La he intentado borrar pero a la hora de guardar me dice que no puedo ya que no tengo privilegios root.

A ver si me podeis orientar, para poder conseguir estos privilegios o borrar la linea chunga.
También me vale otro método para instalar de nuevo la barra awn.

Gracias.

---

### Post by lovinglinux on 2009-05-11
This forum is English only.

Have you tried this:

```
sudo apt-get install avant-window-navigator
```


To edit files as root use the *gksudo* command:

```
gksudo gedit /etc/apt/sources.list
```

Please notice that *gksudo* is used when you need root provileges for graphical interfaces, while *sudo* is used for command-line.

You can also change the software sources through the menus. Go to "System >> Administration >> Software Sources".

---

