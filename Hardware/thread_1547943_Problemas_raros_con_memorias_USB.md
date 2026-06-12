---
title: "Problemas raros con memorias USB"
date: 2010-08-07
forum: Hardware
---

### Post by z37a on 2010-08-07
Últimamente vengo notando algunos problemas con las memorias flash usb, en Ubuntu algunas unidades flash andan mas lentas de lo normal, o al copiar archivos vía gnome copia al instante, pero el disco sigue ocupado y copiando, como si mintiera al dar el dato de que copio.

Hasta ahora esto no me traía ningún problema, pero estos dias me trajeron un ereader, y este tiene una memoria flash interna(se carga todo como a un pendrive) y esta si bien dice que copio al archivo tarda montones en poder sacarlo y hasta a veces los copia mal. Pensé que era el aparato pero hice la prueba desde un windows con el soft del fabricante y este anda de 10. En ubuntu utilizo calibre o copio como a una unidad flash, pero con archivos grandes me da problemas.

Alguien mas noto esto? En mi caso la pc tiene chipset amd, por tanto el usb es de AMD, los dispositivos con este problema son muchos, pero en este caso particular es un eReader Touch de Sony, y también me copia lento(pero sin problemas) a la memoria de mi teléfono Nokia(un N97), con los pendrives algunos si y otros no(marca Kingston todos).

---

### Post by euzkoarima on 2010-08-09
Problemas que copie mal no tuve, por suerte, pero lento si. Pone la barra de avance, llega al final y depués se queda ahí un buen rato.

Probe solo con pendrives kingston y memorias SD. También tengo chips amd.

Saludos,
Eduardo

---

### Post by z37a on 2010-08-10
> **euzkoarima said:**
> Problemas que copie mal no tuve, por suerte, pero lento si. Pone la barra de avance, llega al final y depués se queda ahí un buen rato.

Probe solo con pendrives kingston y memorias SD. También tengo chips amd.

Saludos,
Eduardo

Eso mismo, el problema es que por ejemplo el eReader tiene una memoria flash, se conecta como un pendrive, pero justamente anda lentísimo y nunca me deja desconectarlo, termino teniendo que sacarlo a la fuerza.

Igualmente con el mismo también pude notar ciertos errores en windows, se ve que hay algún tema con el driver de ese aparato o algo así, pero aun así sigue con el tema del teléfono.

---

### Post by Andyvec on 2010-08-10
YO también estoy teniendo problemas con las memorias USB (pendrives) desde 10.04.

Me pasa lo mismo que a ustedes, cuando copio algo aparentemente lo copia al instante, pero todo que en realidad no terminó y debo expulsarlo con seguridad donde tarda varios segundos en hacerlo.

Noto un problema serio y es que falla al copiar archivos grandes, por ejemplo recién intenté copiar una ISO de un DVD de 3.2 GB en un pendrive Kingston vacío de 4GB y falló por supuestos errores de I/O, el tema es que el pendrive funciona bien, desde Windows no tiene ningún problema en hacer movimientos de archivos grandes... con lo que molesta tener que abrir Windows :mad:...

Edito: Yo siempre usé pendrives formateados en FAT 32, cuando los formateo en EXT4 funcionan a la perfección sin ninguno de estos problemas.

---

### Post by alfplayer on 2010-08-10
> **z37a said:**
> Últimamente vengo notando algunos problemas con las memorias flash usb, en Ubuntu algunas unidades flash andan mas lentas de lo normal, o al copiar archivos vía gnome copia al instante, pero el disco sigue ocupado y copiando, como si mintiera al dar el dato de que copio.

> **Andyvec said:**
> Me pasa lo mismo que a ustedes, cuando copio algo aparentemente lo copia al instante, pero todo que en realidad no terminó y debo expulsarlo con seguridad donde tarda varios segundos en hacerlo.

Esto es normal en mi opinión. Por eso es muy importante lo de "expulsar con seguridad", para asegurarse que haya terminado la escritura en el disco antes de desconectarlo.

Lo de los errores de I/O sí sería un problema serio.

---

### Post by z37a on 2010-08-11
> **Andyvec said:**
> 
Noto un problema serio y es que falla al copiar archivos grandes, por ejemplo recién intenté copiar una ISO de un DVD de 3.2 GB en un pendrive Kingston vacío de 4GB y falló por supuestos errores de I/O, el tema es que el pendrive funciona bien, desde Windows no tiene ningún problema en hacer movimientos de archivos grandes... con lo que molesta tener que abrir Windows :mad:...

Edito: Yo siempre usé pendrives formateados en FAT 32, cuando los formateo en EXT4 funcionan a la perfección sin ninguno de estos problemas.

Eso pasa por usar FAT32, no podes utilizar archivos tan grandes a menos que el tamaño de bloque del disco se grande, si no hay un maximo, en ext4 no pasa eso pro que soporta archivos de no se cuantos PB's(o sea miles de gigas).

En realidad a mi no me da errores de I/O si no que se desconecta solo, como si desenchufaras el cable, pero sigue conectado, lo conectas y vuelve a tomar la memoria, pero si copias el mismo archivo lo repite, ahora si lo haces con otros archivos "por ahi" los copia bien.

---

