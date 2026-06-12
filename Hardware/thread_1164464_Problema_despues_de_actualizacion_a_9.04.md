---
title: "Problema despues de actualizacion a 9.04"
date: 2009-05-19
forum: Hardware
---

### Post by MPx1 on 2009-05-19
Bueno, señores, pasa que cuando le di actualice mi Ubuntu a 9.04 desde Synaptics y tengo unos problemillas.. primero, el cual creo que es el mas importante, es que ahora Ubuntu no me detecta la placa de sonido.. [descripcion de la placa: Sound Blaster 24 bits Modelo SB0410 PCI].. En 8.10 la detectaba y funcionaba a la perfeccion.. 9.04 me detecta solamente la "On Board" y como uds. saben.. no es una buena eleccion a la hora de trabajar con sonidos.. El segundo problemilla que tengo es: Los videos de Youtube y demas paginas de videos.. tardan en cargar.. no es mi conexion de internet [sepanlo] es el pugin de Flash.. funciona erraticamente.. ya sea el que te bajas desde la pagina de Adobe como los que estan disponibles en Synaptics.. estos es lo que tengo instalado:

flashplugin-nonfree-extrasound
flashplugin-nonfree
flashplugin-installer
gnash 

no se.. en 8.10 funcionaba perfecto.. :sad:
Si necesitan mas informacion, no duden en pedirla.. no pongo mas porque no se.. :P

---

### Post by guillermolisi on 2009-05-19
> **MPx1 said:**
> Bueno, señores, pasa que cuando le di actualice mi Ubuntu a 9.04 desde Synaptics y tengo unos problemillas.. primero, el cual creo que es el mas importante, es que ahora Ubuntu no me detecta la placa de sonido.. [descripcion de la placa: Sound Blaster 24 bits Modelo SB0410 PCI].. En 8.10 la detectaba y funcionaba a la perfeccion.. 9.04 me detecta solamente la "On Board" y como uds. saben.. no es una buena eleccion a la hora de trabajar con sonidos.. El segundo problemilla que tengo es: Los videos de Youtube y demas paginas de videos.. tardan en cargar.. no es mi conexion de internet [sepanlo] es el pugin de Flash.. funciona erraticamente.. ya sea el que te bajas desde la pagina de Adobe como los que estan disponibles en Synaptics.. estos es lo que tengo instalado:

flashplugin-nonfree-extrasound
flashplugin-nonfree
flashplugin-installer
gnash 

no se.. en 8.10 funcionaba perfecto.. :sad:
Si necesitan mas informacion, no duden en pedirla.. no pongo mas porque no se.. :P
Cuando inicias la maquina, Grub te muestra que tenes aun el kernel anterior al que te dejo la actualizacion, el que estabas usando con 8.10 ?

Si es asi, podrias probar de inicar la maquina con ese kernel y comentar que pasa ?

---

### Post by luks911 on 2009-05-19
Y con respecto a la cuestión del flash, ¿no tendría que tener instalado flash o gnash, pero no los dos?

---

### Post by guillermolisi on 2009-05-19
> **luks911 said:**
> Y con respecto a la cuestión del flash, ¿no tendría que tener instalado flash o gnash, pero no los dos?
I think so.

Para mi tambien es uno o el otro, no ambos simultaneamente.

---

### Post by mauriciog on 2009-05-19
Buenas noches estimados.
Por experiencia propia, probaria sacando la placa, reiniciando y luego volviendola a instalar. Resolvi una cuestion similar de esta forma.
Con respecto al reproductor de Flash, deberias optar por uno de los dos. GNASH funciona muy bien pero no es 100% compatible. Por ahora, te recomendaria utilizar el de Adobe.
Exitos!

---

### Post by MPx1 on 2009-05-19
guillermolisi: no, el grub solo me muestra que tengo solamente instalada la ultima version de Ubuntu.. y otro sistema "operativo".. jejeje.

mauriciog: mmm. voy a probar eso.. y si no pasa nada.. ya fue le instalo la version anterior.. con respecto a flash, ehmm.. es gnash o flash player? ok, le desinstalo todo lo referente a flash y le instalo el de adobe.. gracias por comentar.. despues les cuento como me fue..

---

### Post by guillermolisi on 2009-05-19
> **MPx1 said:**
> guillermolisi: no, el grub solo me muestra que tengo solamente instalada la ultima version de Ubuntu.. y otro sistema "operativo".. jejeje.

mauriciog: mmm. voy a probar eso.. y si no pasa nada.. ya fue le instalo la version anterior.. con respecto a flash, ehmm.. es gnash o flash player? ok, le desinstalo todo lo referente a flash y le instalo el de adobe.. gracias por comentar.. despues les cuento como me fue..
Desinstalar Flash es desinstalar Adobe. Gnash es el free y no es de Adobe.

---

### Post by MPx1 on 2009-05-20
Bueno, señores. solucionado el tema de flash. era cierto que no podían estar instalados Flah de Adobe con el Gnash [este ultimo hacia comportarse erraticamente] y con respecto a lo de la placa de sonido era que hace unos días habia reseteado la configuracion de bios a los que vienen por defecto [fabrica].. resulta que la placa no podia ser detectada porque la que estaba por defecto era la on board...#-o [si, si.. rianse]  jajajaja [que bolú]:lol:

---

### Post by guillermolisi on 2009-05-20
> **MPx1 said:**
> Bueno, señores. solucionado el tema de flash. era cierto que no podían estar instalados Flah de Adobe con el Gnash [este ultimo hacia comportarse erraticamente] y con respecto a lo de la placa de sonido era que hace unos días habia reseteado la configuracion de bios a los que vienen por defecto [fabrica].. resulta que la placa no podia ser detectada porque la que estaba por defecto era la on board...#-o [si, si.. rianse]  jajajaja [que bolú]:lol:
Por lo de Flash y mas aun por lo de la placa de sonido, estas nominado a pagar un pancho y una coca a los que participaron de este thread ;)

---

### Post by luks911 on 2009-05-21
> **guillermolisi said:**
> Por lo de Flash y mas aun por lo de la placa de sonido, estas nominado a pagar un pancho y una coca a los que participaron de este thread ;)

¿Pancho y coca? Qué baratos somos... :-P

Me alegro de que se haya solucionado.

---

### Post by MPx1 on 2009-05-21
jajajaja.. si, pero bien que no se dieron cuenta.. XD porque creo que todo el mundo sabe que para que funcione una placa de sonido o video, se tiene que deshabilitar la on board, no? XD.. un pancho y una gaseosa.. genial! jejeje

---

### Post by pablo.s on 2009-05-21
> **MPx1 said:**
> porque creo que todo el mundo sabe que para que funcione una placa de sonido o video, se tiene que deshabilitar la on board, no? 


Podés tener dos placas de sonido
funcionando a la vez, una onboard
y una PCI, o USB.

---

### Post by MPx1 on 2009-05-21
> **pablo.s said:**
> Podés tener dos placas de sonido
funcionando a la vez, una onboard
y una PCI, o USB.

ajá? mira vos.. no sabía.. pero era raro entonces porque tenía instalada la placa de video en PCI y la on board, pero solo podía escuchar en la on board..

---

### Post by Hei Ku on 2009-05-21
Eso depende del mother. El mio deshabilita automaticamente la onboard si detecta otra conectada, pero en otros lo tenes que hacer manualmente, y en otros pueden convivir. Viva la difference!

---

