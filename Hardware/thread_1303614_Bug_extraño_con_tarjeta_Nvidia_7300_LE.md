---
title: "Bug extraño con tarjeta Nvidia 7300 LE"
date: 2009-10-28
forum: Hardware
---

### Post by pablo.s on 2009-10-28
Desde hace un par de dias tengo
un problema en una de mis màquinas.
El tema comenzò cuando subitamente
tuve un cuelgue desde Jaunty, sin que
hubiera ninguna razòn especial, segùn
recuerdo estaba editando un texto en
gedit.
Cuando reseteo, elijo Jaunty en grub
y me dà como error "Memory corruption
detected in low memory - Check for BIOS
corruption", sin llegar a cargar el sistema.
Que raro, me digo, a ver que sucede con
Karmic. En 9.10 es peor el error, porque
me envia a una consola con BusyBox.

A ver que sucede con <Marca Registrada
de Sistema Propietario>? Carga de manera
normal e incluso me parece escuchar risitas
de fondo.

Decidido a ver que problema extraño tiene,
retiro la tarjeta de video NVidia, conecto el
monitor a la tarjeta on-board Intel (la cual
se arruinò con una especie de corto y muestra
la pantalla en un feo azul monocromàtico)
y... cargan tanto Jaunty còmo Karmic!

Como no encuentro un problema definido y
lògico, recurro a ustedes para que me puedan
tirar alguna punta. Me he fijado en Launchpad
y no encuentro nigùn reporte de bug que me
sirva. A alguien le ha pasado algo asì?

---

### Post by guidito73 on 2009-10-28
Wo, es raro. Pero viendo la naturaleza repentina del problema se me viene a la cabeza alguna caída de tensión o algo.

La placa funcionará bien en otra PC?

---

### Post by pablo.s on 2009-10-28
> **guidito73 said:**
> Wo, es raro. Pero viendo la naturaleza repentina del problema se me viene a la cabeza alguna caída de tensión o algo.

La placa funcionará bien en otra PC?

Funciona perfecto en ESA misma
PC pero en <Marca Registrada de
Sistema Propietario>.

---

### Post by guillermolisi on 2009-10-28
> **pablo.s said:**
> Funciona perfecto en ESA misma
PC pero en <Marca Registrada de
Sistema Propietario>.
Considerando que posiblemente pueda haber algun conflicto con la placa de video, que dice el log del Xorg ? (no hubo una actualizacion reciente para el motor X ?)

Ese warning en low memory no lo marcaba antes tambien, cuando todo andaba sin problemas ?

---

### Post by pablo.s on 2009-10-28
> **guillermolisi said:**
> Considerando que posiblemente pueda haber algun conflicto con la placa de video, que dice el log del Xorg ? (no hubo una actualizacion reciente para el motor X ?)

Esta màquina no tiene actualizaciones
desde hace mas o menos tres meses
en Jaunty y por lo menos desde la Beta
de Karmic. Es muy extraño porque estoy
en un 90% convencido que el conflicto
es con la tarjeta y por lo visto no està
dañada. En este rato probè con tres LiveCD
de Ubuntu, Xubuntu y el de Gentoo 10.0
y todos tienen mas o menos el mismo
conflicto.
¿Es posible que tenga que actualizar la
BIOS de la tarjeta?

> **guillermolisi said:**
> Ese warning en low memory no lo marcaba antes tambien, cuando todo andaba sin problemas ?

No, me fijè en el dmesg de hace una
semana y no hace ninguna advertencia.

---

### Post by anarko on 2009-10-28
Ojo no le des mucha vola a si levanta con W ya que no hace mucho chequeo de errores de memoria, he visto andar W "sin problemas" con memos pinchadas que al menor intento de levantar un kernel linux tirba panic.
Yo probaria la misma placa en otra PC con linux para ver si repite el problema, por ahi el problema no es la placa en si, puede que un bajon de tencion te arruine el slot o parte del chipset que controla la placa de video.

---

### Post by guillermolisi on 2009-10-28
> **pablo.s said:**
> Esta màquina no tiene actualizaciones
desde hace mas o menos tres meses
en Jaunty y por lo menos desde la Beta
de Karmic. Es muy extraño porque estoy
en un 90% convencido que el conflicto
es con la tarjeta y por lo visto no està
dañada. En este rato probè con tres LiveCD
de Ubuntu, Xubuntu y el de Gentoo 10.0
y todos tienen mas o menos el mismo
conflicto.
¿Es posible que tenga que actualizar la
BIOS de la tarjeta?



No, me fijè en el dmesg de hace una
semana y no hace ninguna advertencia.

Y .. actualizar BIOS no siempre soluciona estos problemas. En general no.

Luego actualizar a ciegas, si bien no cuesta mucho esfuerzo, es como jugar a los dados. Puede que salga bien, puede que no. Igual es cuestion de gustos/metodologia. A mi me gusta saber por que y para que voy a hacer lo que hare.

Que dicen en el resto del foro y en San Gugul al respecto ?

Las pruebas con los LiveCD las hiciste sin drivers propietarios ?
Que pasa en otra maquina pero con Ubuntu ? Como para quitar de juego el tema drivers, no vaya a ser cosa que tengan algun bug.

---

### Post by pablo.s on 2009-10-28
> **guillermolisi said:**
> Que dicen en el resto del foro y en San Gugul al respecto ?

Estoy viendo en los foros de NVidia 
y no hay nada similar. Lo màs parecido
a mi problema son ciertas Lenovo que
dan ese error al volver de suspensiòn.
En Google no hay ninguna respuesta.
Me estoy decantando por anotarme en
un torneo de frisbee.  


> **guillermolisi said:**
> Las pruebas con los LiveCD las hiciste sin drivers propietarios ? Que pasa en otra maquina pero con Ubuntu ? Como para quitar de juego el tema drivers, no vaya a ser cosa que tengan algun bug.

Si, ninguno de los LiveCD tienen drivers
propietarios. No probè en otra màquina
todavia.
Estoy bastante ofuscado, sobre todo porque
no me causa gracia salir corriendo a comprar
un placa nueva.

---

### Post by rojojuan on 2009-10-28
Por si sirve tengo instalada una XfX 7300 GS y funciona bien en Hardy y Karmic. Los dos sistemas estan actualizados hasta hoy.

---

### Post by Mauro22 on 2009-10-29
Con el kernel genérico lo hace nomas? Tenés forma de compilar uno!?


Antes o después que carga el núcleo?

---

### Post by pablo.s on 2009-10-29
Lo hace con nùcleos genèricos
(2.6.28, 2.6.31) con nùcleo compilado
(2.6.30) y me parece que esta historia
termina con mi bolsillo vacio.

Lo hace mientras carga, en la parte
que carga rc_default.

---

### Post by Mauro22 on 2009-10-29
Este fuiste vos?


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350704](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350704)

Menciona algo de nvidia y lo de corrupt memory...

---

### Post by guillermolisi on 2009-10-30
> **pablo.s said:**
> Lo hace con nùcleos genèricos
(2.6.28, 2.6.31) con nùcleo compilado
(2.6.30) y me parece que esta historia
termina con mi bolsillo vacio.

Lo hace mientras carga, en la parte
que carga rc_default.
Con nucleos anteriores a los que mencionas, tambien lo hace ?

Me llama la atencion que pusiste 2.6.28. De ser un problema de kernel deberias haber tenido este problema mucho tiempo antes.

No hace mucho alguien abrio un thread con un problema similar. Si no recuerdo mal la placa de video se le arruino porque habia recalentado como producto de la acumulacion de polvo en los disipadores. Tambien probaba con Windows y funcionaba pero cuando la usaba con Ubuntu iba para atras.

---

### Post by pablo.s on 2009-10-30
> **guillermolisi said:**
> Con nucleos anteriores a los que mencionas, tambien lo hace ?

Me llama la atencion que pusiste 2.6.28. De ser un problema de kernel deberias haber tenido este problema mucho tiempo antes.

Exacto. Estoy investigando y al
parecer hay un pedazo de conflicto
entre la placa onboard Intel y la
NVidia, que hacen que si estàn las
dos juntas no cargue ningùn nùcleo.
Pruebo todos los metodos para que
no cargue la Intel en grub y sigue
pasando. En estos dias le hice todo
tipo de tests a la placa Nvidia y todos
salen bien.
Es extraño que antes estaba en la BIOS
configurado exactamente igual que
ahora y no habia conflicto. Quisiera poder
extirpar el chipset de Intel, directamente.

Alguien sabe de alguna manera cruenta
y dolorosa de arrancar con una pinza un
chipset 965 de la placa sin que la arruine?

---

### Post by pablo.s on 2009-10-31
Hay encuesta para que me
ayuden en la decisión.

---

### Post by Mauro22 on 2009-10-31
Vote la de opensolaris porque:

1) si ahí anda, queda descartado el hardware... No se si te hará lo mismo con el nuevo.

2) lo de rabino... No creo que lo solucione, a menos que creas en fuerzas sobrenaturales 

3) comandos.... La causa y la solución de todos los problemas!

---

### Post by guillermolisi on 2009-10-31
Pablo, pensas que quienes lean este thread tomaran el tema seriamente con la encuesta tal como la diseñaste ?
Que aporte comunitario crees que dejara como resultado la misma ?

---

### Post by pablo.s on 2009-11-01
Comencemos por el principio:

-A todos no ha sucedido que por
algún evento una pieza de hard
se rompe, se arruina, nos frustramos
y nos duele la cabeza, pegamos
golpes contra la mesa (aunque la
cabeza) y demostramos que poco
conveniente ha sido que eso haya
sucedido justo un dia 25, cuando la
plata queda bastante lejos de buenos
aires.

-Luego, después de barajar 65535
posibilidades en nuestra cabeza, de
pensar la forma más adecuada de
salvar el incendio, decidimos que la
vida es màs que una placa madre
arruinada. De una manera un poco
apresurada se nos ocurre que la
soluciòn es comprar una nueva.
La decisiòn ya la tomamos. Ahora,
y para hacer un poco de humor nerd
se nos apetece hacer una encuesta
al estilo Slashdot en tu foro favorito,
en un  estilo medio delirante, que no 
aporta nada intelectualmente, pero 
a lo mejor hace reir a alguien y con
eso basta.

- La encuesta no aporta nada, el
problema en tu cabeza ya está
resuelto, aunque no obstante la
forma y el lugar no son apropiados.
Va a dar lugar a la polémica, y
es muy probable que quedes mal
parado. Pero sos muy cabezòn y
la encuesta no se puede borrar.

-**Conclusiòn**: Para la pròxima,
comprá el motherboard.

---

