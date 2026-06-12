---
title: "HP P1005 en Jaunty"
date: 2009-07-22
forum: Hardware
---

### Post by Einfachlacm on 2009-07-22
Hola,

Estoy tratando de instalar una HP P1005 en Jaunty por USB, ya probé un monton de guias que vi por internet y nada...

Alguien ya la configuro en Jaunty?

Gracias de antemano.

---

### Post by guillermolisi on 2009-07-22
Con la funcion Search (en todo Ubuntu Forum) encontre dos casos de exito, en Ingles:

[http://ubuntuforums.org/showthread.php?t=967487&highlight=HP+P1005](http://ubuntuforums.org/showthread.php?t=967487&highlight=HP+P1005)
[http://ubuntuforums.org/showthread.php?t=1207881&highlight=HP+P1005](http://ubuntuforums.org/showthread.php?t=1207881&highlight=HP+P1005)

Si tenes problemas para interpretarlos, avisa y tratamos de pasarlo al Español.

---

### Post by gmunioz on 2009-07-23
Hola ein....:

Si.

La instalé en dos ordenadores.

Simplemente:

Bajé el último hplip de sourceforge.

Ejecute el .run con sudo, a pesar que dice que no es

conveniente hacerlo como administrador

Ejecute luego hp-setup -i tambien con sudo

conecte la impresora al usb, la encendí, segui

la guia de hp-lip, bajo un archivito de internet

Reinicié y listo.

En uno de los ordenadores, ya habian configurado la 

impresora, por lo que antes de hacer nada, la desinstalé.

---

### Post by Einfachlacm on 2009-07-24
Hola Gabriel,

como lograste ejecutar en run? yo hago esto y mira lo que me aparece:

laclatyer@laclatyer:~$ sudo hplip-3.9.6b.run
sudo: hplip-3.9.6b.run: command not found

Losa dos en ingles ya los habia visto y nada.

No se que mas hacer... SOS

---

### Post by Hei Ku on 2009-07-24
sudo ./hplip-3.9.6b.run

---

### Post by gmunioz on 2009-07-24
Hola ein...:

Llegué tarde, efectivamente en consola

se antepone ./, me disculpo por no

aclararlo, lo que ocurre es que uso

por tenerlo incorporado, midnight commander

y desde este, simplemente doy enter sobre

el archivo y: lo ejecuto, lo abro si es iso

o comprimido etc. etc.

---

