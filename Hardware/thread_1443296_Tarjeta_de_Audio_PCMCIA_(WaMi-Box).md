---
title: "Tarjeta de Audio PCMCIA (WaMi-Box)"
date: 2010-03-30
forum: Hardware
---

### Post by daggaz on 2010-03-30
Hola.
Bueno, sé que muchas veces en cuanto a hardware, y más aún en cuanto a tarjetas de audio, no hay mucho que hacer en Linux. Pero no pierdo la esperanza.
Resulta que tras un triste incidente me quedé sin mi bonita tarjeta M-audio, la cual nunca me dio problemas en Ubuntu. Todo funcionaba a pedir de boca. Luego de que me la robaran trabajé un rato con la tarjeta interna de mi Lap... Sin mucho que esperar, pero funcionó más o menos bien hasta que pasé a Karmic. Donde muchos programas se peleaban con ALSA y luego... Ya saben la historia del inicio de Karmic en cuanto a audio.
Aún sigo sin poder hacer que muchas cosas funcionen bien (me las he ingeniado con Jack), Pensé entonces que con una buena tarjeta las cosas podrían mejorar quizás. Entonces me acordé de mi vieja WaMi Box de EGO-SYS, abandonada en una caja. 
[http://www.neoseeker.com/Articles/Hardware/Reviews/egosyswami/](http://www.neoseeker.com/Articles/Hardware/Reviews/egosyswami/)
Esta se conecta a través de PCMCIA y me funcionaría muy bien para lo que la necesito. Problema: Ubuntu no reconoce la tarjeta. He buscado algo de información pero al escribir  «WaMi Box Linux» en Google no hay mucho.
*lspcmcia* me dice:
```
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:06.0)
Socket 0 Device 0:    [-- no driver --]    (bus ID: 0.0)
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:06.1)
Socket 1 Device 0:    [pata_pcmcia]        (bus ID: 1.0)
```Actualmente utilizo Ubuntu normal, no sé si cambiar a Studio mejore algo la situación... No sé si algo se puede hacer al respecto. ¿Habrá paquetes con controladores de Audio extras?

---

### Post by guillermolisi on 2010-03-30
Buscaste en Google por "yenta cardbus" (que es en definitiva como la reconoce Ubuntu) ?.

Yo probe y me trajo varios links en Ingles referidos a ese hardware y Linux. Varios aludiendo problemas de deshabilitacion de IRQ al insertar la tarjeta. No se si te servira para tu problema pero si ya buscaste una vez, un poco mas no sera tan grave. :)

---

### Post by daggaz on 2010-04-08
Hola.
 Sospecho que eso de Yenta es la unidad en sí (el lector). Me puse a buscar sobre mi tarjeta y pues me di cuenta que necesito actualizarme : P Ya no tiene soporte ni en Güindous. El último controlador fue para Win2000 y en la página del fabricante la encontré en una sección llamada «Museo de historia». Así que supongo, menos aún lo encontraré para Linux.
Mejor me pongo a ahorrar y me compro de nuevo una buena tarjeta. Investigaré cuales son las que mejor funcionan en Ubuntu.
¡Gracias!

---

