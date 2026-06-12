---
title: "Eliminar kernel antiguo"
date: 2009-06-30
forum: Instalación y Actualización
---

### Post by jorval on 2009-06-30
Hi, debido a las actualizaciones del kernel, nuestro grub comienza a estar lleno de kerneles ¿cómo eliminar los más antiguos? En este artículo está la solución. Bye.

[http://tuxpepino.wordpress.com/2007/06/26/tip-eliminar-un-kernel-antiguo/]("http://tuxpepino.wordpress.com/2007/06/26/tip-eliminar-un-kernel-antiguo/")

---

### Post by nagash93 on 2009-06-30
:O justo estaba buscando esto te pasaste

Una pregunta cuendo elimino el kernel se elimina completo o solo del grub cuendo inicio pc ?

---

### Post by zhelo on 2009-06-30
gracias amigo

---

### Post by CdK1 on 2009-06-30
No es por nada, pero este tema ya estaba resuelto en otro post...

---

### Post by moreback on 2009-06-30
> **nagash93 said:**
> :O justo estaba buscando esto te pasaste

Una pregunta cuendo elimino el kernel se elimina completo o solo del grub cuendo inicio pc ?
Si lo desinstalas como sale en la guía con aptitude (apt-get también sirve) y no has hecho modificaciones al grub.conf, deberían eliminarse automáticamente las entradas agregadas a este último archivo.

---

### Post by radixs on 2009-07-02
> **moreback said:**
> Si lo desinstalas como sale en la guía con aptitude (apt-get también sirve) y no has hecho modificaciones al grub.conf, deberían eliminarse automáticamente las entradas agregadas a este último archivo.

Yo no lo quise eliminar solo comente (se añade un #) las lineas del Kernel antiguo asi evite que me saliera en menu del GRUB.

Para modificar el GRUB

```
# nano /boot/grub/menu.lst
```PS: nano editar en la consola, si deseas al mas grafico, en vez de nano [I]"gedit"

NOTA: Siempre que vayan a modificar algo asi, recuerden siempre realizar una copia de respaldo, en caso que cometieran un error
[/I]

---

### Post by teamcpc on 2011-03-29
También se puede hacer de una manera rápida e intuitiva con ubuntu tweak:
[http://malagaoriginal.blogspot.com/2011/03/limpieza-de-kernels-en-ubuntu-1010.html](http://malagaoriginal.blogspot.com/2011/03/limpieza-de-kernels-en-ubuntu-1010.html)

---

