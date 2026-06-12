---
title: "Problema con tranferencia de usb en ubuntu karmic"
date: 2009-12-15
forum: Hardware
---

### Post by martin1717 on 2009-12-15
Cada vez que intento hacer una transferencia por usb me sale un error, deja de reconocer el pen drive y debo reiniciar para q reconozca el usb de nuevo. la transferencia arranca bien, se vuelve lenta y luego tira un error de entrada/salida. tengo ubuntu 9.10 32 bit, mi maquina es una toshiba satellite m55-s141, el usb funciona en otras compus con windows. tal vez tenga q instalar algun driver o algo, me ayudan? 
gracias de antemano.

---

### Post by julicabrini on 2009-12-16
Podes especificar el error? osea decime que aparece adentro de la ventana de error.. que tipo de sistemas de archivos es? tambien eso es importante..

---

### Post by martin1717 on 2009-12-17
Error al abrir el archivo «/media/USB DISK/Friends 1/sdneirF.1x01.rmvb»: Error de entrada/salida. gracias por contestar.
el sistema de archivos de un pendrive es msdos, otro es vfat

---

### Post by martin1717 on 2009-12-17
hice lo q decia aca:

[http://www.linuxzone.es/howtos-manuales/solucionar-los-problemas-con-usb-en-linux/](http://www.linuxzone.es/howtos-manuales/solucionar-los-problemas-con-usb-en-linux/)

pero no en menu.lst sino en grub.cfg y anduvo bastante bien, es decir lento pero no me daba error, pero no me terminaba de apagar el equipo, es decir cerraba todo el sitema pero se quedaba con la pantalla negra y prendida la compu. 
entonces deshice lo q decia en el post y ahora sigue como antes, logicamente. alguna idea?

pd.: no uso hub y anda en otras compus con window$

---

### Post by julicabrini on 2009-12-17
mira desde mi experiencia se que todos los pendrives vienen formateados de fabrica en formato apto para windows ya sea ntfs o fat32. Tambien lo que se que en el sistema de archivos fat32 no soporta tener archivos de mas de 4gb. la verdad que mucha ayuda no te puedo dar pero esto es lo que se! estuve averiguando pero nada... si encuentro alguna cosa que te sirva la posteo!

---

### Post by guillermolisi on 2009-12-17
Esa guia que citas es algo vieja, Octubre 2008.
Desde entonces a la fecha varias cosas han cambiado, particularmente el kernel que administra el hardware de una forma diferente a la version en uso de esa epoca.

Mi recomendacion es no usar acpi=off salvo que la maquina no inicie. Hay muchas funcionalidades relacionadas con la administracion de energia, entre otras, que dejan de funcionar.

Que pasa si transferis un archivo mas chico que ese que mencionas en el mensaje de error ?

Si dejas el pendrive montado pero no moves archivos, ocurre lo mismo al tiempo cuando queres leer o grabar algo en el pendrive ?

---

### Post by martin1717 on 2009-12-17
si intento con archivos de 25 mb me pasa lo mismo, si intento con archivos de 5mb funciona bien. si dejo el pendrive montado no pasa nada. gracias por contestar. se te ocurre algo?

---

### Post by guillermolisi on 2009-12-17
De que capacidad es el pendrive y que tamaño tiene cada particion ?

---

### Post by martin1717 on 2009-12-18
uno de los pendrive es de 2 gb, otro es de 4, otro es un disco externo de 500gb. como hago para ver las particones¡?

---

### Post by guillermolisi on 2009-12-19
> **martin1717 said:**
> uno de los pendrive es de 2 gb, otro es de 4, otro es un disco externo de 500gb. como hago para ver las particones¡?
En modo consola tenes fdisk y en modo grafico gParted.

Podes probar ese pendrive en otra maquina con Ubuntu, como para ver si se repite el sintoma ?

---

