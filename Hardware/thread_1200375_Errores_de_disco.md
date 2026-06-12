---
title: "Errores de disco"
date: 2009-06-29
forum: Hardware
---

### Post by clasificado on 2009-06-29
Queria compartir con ustedes estoy re divertido que me paso hoy!!

[Imagen adjunta]

Para el que diga "Hey! esto no es divertido" _tiene razón_: Es el disco que estaba usando como repositorio de código fuente, y server web de desarrollo.

Por suerte no perdí nada: tengo un rsync hacia otra pc copiando todo. bah, también bajaba torrents y eso si se perdió, pero los bajo de nuevo por lo que no me significa

Sospecho que son sectores malos y que el tema sea de error físico, despues de todo es un disco pata de 40gb al cual no le di descanso desde que lo compré hace tantos años ya, aunque la verdad es que es la primera vez que veo estos mensajes de error.

badblocks le está pasando un chequeo no destructivo desde hace unas cuantas horas, y saltaron de esos mensajes una bocha mas. 

No es la primera vez que ESTE disco me falla: Badblocks me lo salvó una vez ya y marcó una parva de sectores como defectuosos, y tiró como un año mas con el mismo disco. No se si va a volver a hacer el milagro.

ahora me da fiaca comprar otro disco, no quiero invertir en un pata de nuevo, la maquinola es una p3 que no entiende de sata ni boot por usb. la placa de red es pci asi que no se si butea por pxe (tendré que probar), lo unico que me queda es CD que lo dejaré para el final

Para el que nunca le pasó: así es como falla un disco :lolflag:

clasificado

pd: cada vez que tira uno de esos mensajes, hace un ruido horrible.

---

### Post by staar on 2009-06-30
lamentablemente, conozco bien esos mensajes... ¬¬

saludos

---

### Post by guillermolisi on 2009-06-30
Te van a pasar dos cosas si no reemplazas el disco inmediatamente: La primera y que ya debe estar ocurriendo es que se va a llenar el espacio extra para la tabla de pistas alternativas en el disco y a continuacion no vas a poder recuperar ningun block dañado concluyendo en perdida de datos/corrupcion del file system. La otra es que ese disco te va a dejar a pie en cualquier momento.

Si su conentido no vale otro disco nuevo, coincido con vos en que no vale la pena comprar otro PATA.

It's up to you.

---

