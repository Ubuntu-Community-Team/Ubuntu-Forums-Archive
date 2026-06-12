---
title: "no puedo instalar ningun ubuntu"
date: 2011-01-09
forum: Hardware
---

### Post by marcelocool on 2011-01-09
:confused::confused: hola, primero q nada pido disculpas si esto ya fue publicado.

tengo problemas al intentar instalar ubuntu 9.10, 10.4 o 10.10...(otras versiones no intente)
siempre con el mismo error y no encuentro ni en google este tipo de error.
la pc es algo ¨vieja¨ en un P 4 de 3.00GHz, 1 Gb de ram, una nvidia 6200 de 512....

adjunto tomas de mi pantalla

init: line 7: can´t open /dev/sdb: No medium found 
init: line 7: can´t open /dev/sdb: No medium found 
init: line 7: can´t open /dev/sdb: No medium found

---

### Post by biale on 2011-01-10
En general conviene habilitar para el disco el SMART por BIOS...

Si completas el arranque live (probar sin instalar)  (1) Probaste instalar desde alli? (2) El gestor de particiones (gparted), que te muestra? (3) Y la comprobacion del Sistema?

---

### Post by marcelocool on 2011-01-10
hola biale, gracias por responder...
Te cuento que soy muy amateur en ubuntu pero tengo cierta idea, me defiendo ja.
voy a ver si habilito el smart desde el bios
2) el g Gparted no lo podía ejecutar pero de un día para el otro pude.
muestra las particiones donde tengo windows xp (ntfs 80 Gb) una q deje sin formato para ubuntu (80 Gb) y el resto en datos (también en ntfs)
3) la comprobación de sistema esta todo ok.

voy a intentar ¨ probar sin instalar¨ y a habilitar el smart.

cuento q paso...gracias nuevamente por la respuesta

---

### Post by mama21mama on 2011-01-10
proba con un ubuntu alternate desde un usb.

Saludos

---

### Post by marcelocool on 2011-01-10
> **biale said:**
> En general conviene habilitar para el disco el SMART por BIOS...

Si completas el arranque live (probar sin instalar)  (1) Probaste instalar desde alli? (2) El gestor de particiones (gparted), que te muestra? (3) Y la comprobacion del Sistema?




bueno amigo no paso nada. mismo error. todo esta en orden pero no pasa nada...

---

### Post by biale on 2011-01-10
O sea: no arranca live /o/ no quiere instalar?

Habría que verificar si la iso bajo bien y si el cd esta bien grabado.

---

### Post by marcelocool on 2011-01-10
> **biale said:**
> O sea: no arranca live /o/ no quiere instalar?

Habría que verificar si la iso bajo bien y si el cd esta bien grabado.


tal y como se muestra en la imagen...arranca el live pero me quedo esperando y m muestra el error al termino de unos minutos..
el resto esta todo ok...la iso esta bien y el cd esta normal...todo verificado. :confused:

---

### Post by mama21mama on 2011-01-10
> **marcelocool said:**
> tal y como se muestra en la imagen...arranca el live pero me quedo esperando y m muestra el error al termino de unos minutos..
el resto esta todo ok...la iso esta bien y el cd esta normal...todo verificado. :confused:

probate la version alternate viejo

---

### Post by biale on 2011-01-11
Parece raro que justo haya problemas en la detección de un IDE. Si lo damos como un problema en el instalador, tiene sentido probar con el alternate CD. Y si se aplica a un drive USB entoces nos independizamos de la lectora 

En un arranque live (cualquier distro) en principio solo pesa la lectora de CD y el CD. Salvo interferencias tendría que arrancar bien, y luego acceder bien al HDD. Ya arrancado, los comandos dmsg, lshw (etc) tendrían que mostrar todo bien...

---

### Post by gmunioz on 2011-01-11
Sugerencia:
Coloca el disco rígido como master en ide0
Coloca el cdrom como master en ide1 o como slave
en ide0

---

### Post by marcelocool on 2011-01-11
voy a hacer un ubuntu para q arranque desde usb...sospecho de la lectora de cd, voy desconectarla para ver q onda y anularla desde la bios
la lectograbadora  es una BenQ ata esta como master, mi disco es sata de 500 y esta tal cual se muestra en la foto con la variacion de smart activado.
tengo tambien una lectora de tarjetas no creo q sea eso o si? no se..
voy intentar lo q ma han dicho..:(

gracias a todos por responder :D

---

### Post by biale on 2011-01-11
Coincido con gmunioz. La diferencia de velocidades es muy grande. Ojo que a veces si hay un solo dispositivo, en lugar de Master hay que jumpear como "single".

> tengo tambien una lectora de tarjetas 

Me parece que la cosa puede estar ahi. Si la lectora de tarjetas no tiene alguna tarjeta que se pueda leer, podría aparecer un mensaje de error de ese tipo. Podes probar dejando colocada una tarjeta o directamente desconectandola.

---

### Post by marcelocool on 2011-01-14
hola...primero gracias por responder..
el problema fue una estupidez...cambie el soft grabador, usaba ImgBurn y grabe la ISO con Nero...y bingo.Arranco lo mas bien...la verdad es una cosa tonta pero no m dejo instalar el soft...
Repito, gracias a todos por responder, por lo pronto se ha solucionado el problema ( esperemos) saludos

---

### Post by mama21mama on 2011-01-14
por eso dije usb ;)

---

### Post by biale on 2011-01-15
Genial que haya funcionado!

Ahora bien, habías dicho:

> el resto esta todo ok...la iso esta bien y el cd esta normal...todo verificado

A su vez ImgBurn no parece mal software. Podemos preguntar como habías verificado la grabación?

---

