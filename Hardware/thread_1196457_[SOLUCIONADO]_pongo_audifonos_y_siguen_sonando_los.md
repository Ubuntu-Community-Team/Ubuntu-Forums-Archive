---
title: "[SOLUCIONADO] pongo audifonos y siguen sonando los parlantes - vaio VGN-N160G"
date: 2009-06-25
forum: Hardware
---

### Post by clave on 2009-06-25
buenas, tengo un notebook y hoy instale ubuntu, mi problema esque cuando pongo los audifonos siguen sonando los parlantes y me gustaria saber como arreglarlo. por ahora lo que hago es en el controlador de volumen le puse mute al front, pero la idea es no estar moviendolo cada vez que ponga o saque los audifonos, gracias de antemano.

---

### Post by CdK1 on 2009-06-25
Ya, mira, en tu barra superior izquierda, hay un "parlante", dale dos click o botón derecho, ve a propiedades, y configura, o aplica en consola "alsamixer"

---

### Post by clave on 2009-06-25
esque ya estoy con el Alsa mixer y no pasa nada, probe apretando el muteo del front, esa cosa como 2 cadenas que se juntan y separa, y tickeando y des-tickeando el conmutador del audifono, y no pasa nada.

---

### Post by aledruetta on 2009-06-25
> **clave said:**
> ...mi problema es que cuando pongo los audifonos siguen sonando los parlantes ... por ahora lo que hago es en el controlador de volumen le puse mute al front, pero la idea es no estar moviendolo cada vez que ponga o saque los audifono...

Es cierto, esa es una característica bastante incómoda y para la que nunca encontré una forma práctica de resolverla. ¿Alguien consiguió hacerlo?

Saludos,
Alejandro.

---

### Post by RafaelG on 2009-06-25
Disculpa podrias decir que Notebook tienes, que tipo de instalacion de Ubuntu hiciste y por ultimo escribe esto en un terminal y pega aca lo que salga.

> aplay -l

---

### Post by augias on 2009-06-25
Hola hola clave. Yo tuve el mismo problema que tu. Pero la solucion que conozco solo funciona para laptops de Vaio. Tu cual modelo usas? Dependiendo de eso te puedo buscar una solucion por la web y te posteo como arreglarlo. Saludos!

---

### Post by clave on 2009-06-25
bueno, tengo un Vaio VGN-N160G, lamentablemente no me se todas las caracteristicas, no se exactamente cual es la tarjeta de sonido, y todavia no tengo idea de como usar la terminal; y bueno como instale ubuntu.... como soy newbie lo explicaré paso por paso pq no se exactamente que es lo que se necesita saber; originalmente  en windows instale con wubi, para saber en que me iva a meter, pero el mismo dia lo desinstale de ahi y defragmente hasta que quedo toda la info en una eskina, luego use el partition magic y redimensione esa unidad, dejando como 35 gb libres. despues puse el disco del ubuntu y reinicie; lo instale haciendo una particiones "manualmente" (siguiendo las instrucciones de aca [http://myubuntuestudio.wordpress.com/2008/03/25/como-instalar-ubuntu-studio-sin-afectar-o-quitar-windows-2-segunda-forma/](http://myubuntuestudio.wordpress.com/2008/03/25/como-instalar-ubuntu-studio-sin-afectar-o-quitar-windows-2-segunda-forma/) ) hize una swap y otra para ubuntu, despues use el gestor de actualizaciones y tambien busqué con el gestor de paquetes synaptic el paquete de audio de ubuntu studio mas los audioplugins y controls (pq soy musico y quiero poder usar ubuntu como mi estacion multimedia profesional). bueno esop.

gracias =)

ps: ah! algo que recuerdo esque cuando instale ubuntu con el wubi ponia los audifonos y efectivamente dejaba de sonar los parlantes, saqué eso para instalarlo "bien" pq le comente a un amigo que me corria un poco lento y me dijo que era pq ntfs era lento y que lo probara en el formato ext3 o mejor el 4 (pq me dijo que era mas rapido), como no tuve tiempo de investigar, la particion donde esta ubuntu es ext3.

---

### Post by Carlos C on 2009-06-26
Tengo dos observaciones que hacer. La primera es que debes siempre dar toda la información relevante. Si tu problema es de hardware, evidentemente debes decir las características del mismo. Si es un laptop, obviamente el modelo. Si hubieras partido por decir que el equipo era un vaio todo hubiera sido más fácil.

La segunda observación es que debes siempre usar el buscador del foro. Este problema ya ha sido planteado antes y se encuentra la solución fácilmente si escribes "vaio" en el buscador del subforo, allí donde dice "search this forum".

Te voy a pedir que leas esto antes de publicar nuevamente:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Eso.

... perdón, perdón, ¡olvidaba lo más importante!, el enlace a la solución:

[http://ubuntuforums.org/showthread.php?t=1170537&highlight=vaio](http://ubuntuforums.org/showthread.php?t=1170537&highlight=vaio)

Saludos.

---

### Post by clave on 2009-06-26
busqué pero no supe buscar, lei lo que me dijiste; soy ultranuevo, disculpa las molestias y gracias por los datos.

con respecto al problema, funciono a la perfección lo que me dijiste, muchas gracias.

---

