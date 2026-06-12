---
title: "imposible montar unidad usb (pendrive)"
date: 2009-08-10
forum: Hardware
---

### Post by cokoliche on 2009-08-10
Hola a todos...
Tengo Ubuntu 9.04 y al insertar un pendrive al puerto usb del pc me aparece:
No se pudo montar Soporte de 2,1 GiB
Ha ocurrido un error al ejecutar el proceso hijo «gnome-mount» (No existe el fichero ó directorio)

cualquier aparato que conecte al usb lo mismo......

espero de su ayuda

saludos...

---

### Post by Carlos C on 2009-08-11
Hola. Parece que tienes problemas para montar unidades, al menos cuando se trata de  usar gnome-mount. Lo digo porque en el otro post que publicaste a raíz de tus problemas con el dvd presentas el mismo error.

---

### Post by cokoliche on 2009-08-11
> **Carlos C said:**
> Hola. Parece que tienes problemas para montar unidades, al menos cuando se trata de  usar gnome-mount. Lo digo porque en el otro post que publicaste a raíz de tus problemas con el dvd presentas el mismo error.

asi es...

alguna solucion??????

---

### Post by CdK1 on 2009-08-12
Ha ocurrido un error al ejecutar el proceso hijo «gnome-mount» (No existe el fichero ó directorio)

sudo apt-get install gnome-mount

---

### Post by moreback on 2009-08-13
> **CdK1 said:**
> Ha ocurrido un error al ejecutar el proceso hijo «gnome-mount» (No existe el fichero ó directorio)

sudo apt-get install gnome-mount

¿No se supone que ese programa debiera venir instalado? De hecho en Synaptic aparece marcado como de los paquetes oficiales.

---

### Post by CdK1 on 2009-08-13
Por lo general sí, pero hay veces ya sea en la instalación como en la administración que al borrar packages usar autoremove etc, se ensucia el sistema... y hay muchas veces que dependiendo del ripo de instalación no viene incluído... "Instalación del sistema base", por ejemplo...

---

