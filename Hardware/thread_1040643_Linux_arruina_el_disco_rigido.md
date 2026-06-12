---
title: "Linux arruina el disco rigido?"
date: 2009-01-15
forum: Hardware
---

### Post by Kartwizard on 2009-01-15
Hola! Como estan? Este es mi primer mensaje en este foro. Espero no estar duplicando otro pero realmente no logro encontrar una solucion al problema. Todo comenzo leyendo el comentario de un comprador de una Dell Studio en la web de Dell Argentina. En el cual decia lo siguiente: 

"Windows Vista. ¡vaya sistema operativo! por llamarle algo. Mejor procesador, más memoria.... pero tarda más en arrancar el Studio 15 con Vista que el Inspiron 6400 con XP
Ojo con Linux, **en 6 meses que lo tuve instalado se pulió 260.000 de los 300.000 ciclos de Load/Unload del cabezal del disco duro**. 300.000 es solo un valor de referencia, pero Linux no es lo mejor para el disco de un portatil.
Tener que pagar 35 euros por el Bluetooth"

En vistas de que vengo testeando Ubuntu y luego del cambio de ntk pensaba instalarlo de nuevo (Ubuntu o Mandriva, no estoy seguro) haciendo dual boot con Vista en mi Dell Inspiron 1525 fue que me puse a investigar sobre el tema y al parecer es algo relacionado con la "bios" del disco que frena los cabezales constantemente. A diferencia de Vista, por ejemplo. Saben si esto es real? (A que arruina el HDD me refieron) De ser asi, hay alguna solucion? Tengo miedo de arruinar la nbk o la desktop. Gracias!!!

Saludos.

---

### Post by pante on 2009-01-15
En una búsqueda rápida, encontré esto, relacionado, [http://www.vicente-navarro.com/blog/2007/10/28/linux-no-mata-discos-duros-se-mueren-solos/](http://www.vicente-navarro.com/blog/2007/10/28/linux-no-mata-discos-duros-se-mueren-solos/)

Aunque yo no confiaría en un comentario que diga que Win Vista tenga "mejor procesador y mejor memoria" :confused: :confused: Ningún sistema operativo tiene memoria ni CPU.

Saludos :)

---

### Post by Hei Ku on 2009-01-15
Los discos tienen un tiempo de espera recomendado antes de apagarse, que esta seteado por el fabricante. Cuando se apaga, el disco estaciona las cabezas en una zona segura. (Generalmente se escucha un click cuando sucede esto)
Algunos fabricantes ponen un valor demasiado chico que causa stress en las cabezas y algunos dicen que puede terminar en que se rompa un disco.

Windows (XP y Vista) sobreescribe este valor a uno que se les ocurre. Linux deja el valor que puso el fabricante, pero permite cambiarlo si uno quiere. 

Es un "problema" conocido y la solucion no lleva mas de 10 minutos si sos uno de los usuarios afectados. No es algo común o tendrías miles de personas reportando ese problema. Seguí el link de pante y en 2 minutos podes ver si sos uno de los afectados y como solucionarlo.

En cuanto al mensaje en ese foro, esta puesto a proposito para meter miedo, incertidumbre y engañar a la gente. Clasico de Microsoft y sus partners.

---

### Post by Kartwizard on 2009-01-15
Gracias por la respuesta. De lo otro seguro! Se mando cualquiera! jaja aunque seguramente habra querido poner que tiene mejor manejo del procesador y de la memoria (cosa que tampoco es cierta como sabemos). Si la version estable de Windows 7 es como la beta (acabo de probar la de 32 bits....que no me deja instalar ni el F1 Challenge ni el NFSU para probar...asi que fue, pero es agil como Ubuntu...en los primeros 40 minutos de test liviano), bue me refui de tema, lo que queria decir es que ese mensaje es del 2007, tal vez en Intrepid Ibez el bug venga correjido. De todas formas me parece que me voy a quedar con las ganas de hacer el dualboot para no arruinar el HDd...:(:(:(:(:(:(:(

Saludos.

---

### Post by Hei Ku on 2009-01-15
Busca en este mismo foro que hubo personas con dudas similares.

---

### Post by santiagoward2000 on 2009-01-15
> **Kartwizard said:**
> lo que queria decir es que ese mensaje es del 2007, tal vez en Intrepid Ibez el bug venga correjido. De todas formas me parece que me voy a quedar con las ganas de hacer el dualboot para no arruinar el HDd...:(:(:(:(:(:(:(

Hola!
Yo tengo ese problema con Intrepid en mi Dell XPS M1330. Me subió como 62500 ciclos en 2 meses. Pero usé la solución de [este thread]("http://ubuntuforums.org/showthread.php?t=805570"), y desde entonces subió menos de 200 en 1 mes. Como el máximo aprox para las laptops es de 300000, yo ahora estoy re tranquilo.
Espero que te sirva, y que no te asuste eso!
Saludos!

---

### Post by staar on 2009-01-15
estan de suerte, ayer nomas salio una actualizacion que aparentemente soluciona el problema :D

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695")

saludos

---

### Post by sergiom99 on 2009-01-16
tambien podes mirar este thread para un script para manejar esto. es un 'work-around', la solucion definitiva esta por venir (dicen)
[http://ubuntuforums.org/showthread.php?t=1038233](http://ubuntuforums.org/showthread.php?t=1038233)

---

### Post by Kartwizard on 2009-01-16
Buenisimo! Gracias a todos por las respuestas, si bien ya estoy con ideas raras y locas, todavia me considero un principiante en lo que a Linux respecta. Sera cuestion de probar la solucion para ver si funciona. De todas formas lo voy a hacer a partir del lunes (vacaciones!!!) ya que estoy leyendo un poco ahora los links y no entiendo nada sobre como instalarlos!!! Gracias.

Saludos.

---

### Post by staar on 2009-01-16
> **Kartwizard said:**
> De todas formas lo voy a hacer a partir del lunes (vacaciones!!!) ya que estoy leyendo un poco ahora los links y no entiendo nada sobre como instalarlos!!! Gracias.

de nada, para eso esta el foro, el link que te pase yo, ni te mates tratando de entenderlo, solo avisa que el parche que soluciona el problema en el paquete involucrado (acpi-support), ya fue liberado, y que te va aparecer entre las actualizaciones de ubuntu ;)

saludos

---

### Post by Kartwizard on 2009-01-20
Clap CLap Clap! Gracias! Anoche instale desde cero Intrepid, con el comando sudo smartctl -a /dev/sda | grep Load_Cycle_Count fui testeando el disco que en 10 minutos subio 8 puntos y en 20 minutos 25 puntos. Instale solo la actualizacion que me pasaste y se quedo colgado en 2165 durante 55 minutos que fue cuando apague la nbk. Ahora la volvi a encender y desde las 13:20 que esta en 2166 (Son las 13:55). En un rato voy a proceder a reinstalar todo de nuevo con dual boot junto a Vista (Tal vez aproveche el Dell MediaDirect para usar las 2 teclas de encendido y elegir con que bootear). Gracias por todo! Saludos.

---

