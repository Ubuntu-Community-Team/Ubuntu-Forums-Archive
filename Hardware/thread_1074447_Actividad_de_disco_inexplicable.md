---
title: "Actividad de disco inexplicable"
date: 2009-02-19
forum: Hardware
---

### Post by pabloatilio on 2009-02-19
Hola amigos, les cuento algo que observo en uno de mis equipos y que no le puedo encontrar explicación, el fenómeno es aleatorio, algunas veces enciendo el equipo y no lo hace nunca y otras si.

Resulta que el led rojo situado en el gabinete que indica la actividad del disco en algunas ocasiones permanece encendido todo el tiempo, no se apaga nunca, como si el disco no dejara de trabajar, pero no estoy haciendo absolutamente nada y la luz no se apaga, puede permanecer horas asi (¿será que efectivamente no deja de estar girando o trabajando ? ).

Otras veces el funcionamiento es normal, es decir se enciende por un momento cuando se abre un programa y carga a el mismo, o cuando lee o escribe en el disco, lo hace  por unos instantes y tiene el "parpadeo" normal que todos hemos visto, de las actividades que está desarrollando. 

El equipo tiene 3 discos, un maestro y un esclavo en una ide y un sata.
El S.O. Linux está cargado en el esclavo, el sata es sólo para datos. 

Además cuenta con dual boot con XP. En XP nunca tengo ese problema. Y no estoy seguro pero creo que antes no me hacia esto el linux. Traté de observar si lo empieza a hacer después de abrir tal o cual programa o cosas así pero no pude descubrir nada al respecto.

Gracias a todos, saludos.

Pablo A

---

### Post by guillermolisi on 2009-02-19
> **pabloatilio said:**
> Hola amigos, les cuento algo que observo en uno de mis equipos y que no le puedo encontrar explicación, el fenómeno es aleatorio, algunas veces enciendo el equipo y no lo hace nunca y otras si.

Resulta que el led rojo situado en el gabinete que indica la actividad del disco en algunas ocasiones permanece encendido todo el tiempo, no se apaga nunca, como si el disco no dejara de trabajar, pero no estoy haciendo absolutamente nada y la luz no se apaga, puede permanecer horas asi (¿será que efectivamente no deja de estar girando o trabajando ? ).

Otras veces el funcionamiento es normal, es decir se enciende por un momento cuando se abre un programa y carga a el mismo, o cuando lee o escribe en el disco, lo hace  por unos instantes y tiene el "parpadeo" normal que todos hemos visto, de las actividades que está desarrollando. 

El equipo tiene 3 discos, un maestro y un esclavo en una ide y un sata.
El S.O. Linux está cargado en el esclavo, el sata es sólo para datos. 

Además cuenta con dual boot con XP. En XP nunca tengo ese problema. Y no estoy seguro pero creo que antes no me hacia esto el linux. Traté de observar si lo empieza a hacer después de abrir tal o cual programa o cosas así pero no pude descubrir nada al respecto.

Gracias a todos, saludos.

Pablo A
Estas usando las smartmon tools para generar informacion sobre la "salud" de los discos (que sean SMART compatibles) ?

---

### Post by rojojuan on 2009-02-19
> **pabloatilio said:**
> Hola amigos, les cuento algo que observo en uno de mis equipos y que no le puedo encontrar explicación, el fenómeno es aleatorio, algunas veces enciendo el equipo y no lo hace nunca y otras si.

Resulta que el led rojo situado en el gabinete que indica la actividad del disco en algunas ocasiones permanece encendido todo el tiempo, no se apaga nunca, como si el disco no dejara de trabajar, pero no estoy haciendo absolutamente nada y la luz no se apaga, puede permanecer horas asi (¿será que efectivamente no deja de estar girando o trabajando ? ).

Otras veces el funcionamiento es normal, es decir se enciende por un momento cuando se abre un programa y carga a el mismo, o cuando lee o escribe en el disco, lo hace  por unos instantes y tiene el "parpadeo" normal que todos hemos visto, de las actividades que está desarrollando. 

El equipo tiene 3 discos, un maestro y un esclavo en una ide y un sata.
El S.O. Linux está cargado en el esclavo, el sata es sólo para datos. 

Además cuenta con dual boot con XP. En XP nunca tengo ese problema. Y no estoy seguro pero creo que antes no me hacia esto el linux. Traté de observar si lo empieza a hacer después de abrir tal o cual programa o cosas así pero no pude descubrir nada al respecto.

Gracias a todos, saludos.

Pablo A
No se si será esto, pero podría ser:
Te fijaste en Sistema - Administración -Orígenes del software - Actualizaciones - Comprobar actualizaciones? Si esta marcado diariamente, una vez al día intenta comunicarse vía Internet y a veces pasa que un Repositorio no responde y sigue buscando

---

### Post by h9005 on 2009-02-19
Cuando hace eso, te fijaste si el disco realmente está trabajando o solo prende la luz? El disco hace un sonido aunque mínimo cuando está trabajando.

---

### Post by pabloatilio on 2009-02-20
> **guillermolisi said:**
> Estas usando las smartmon tools para generar informacion sobre la "salud" de los discos (que sean SMART compatibles) ?


Hola, no estoy usando los smartmon , no está instalado el paquete, además me fijé en la BIOS y S.M.A.R.T. está desactivado (por si tiene algo que ver).

Gracias por tu respuesta. Saludos

Pablo A

---

### Post by pabloatilio on 2009-02-20
> **h9005 said:**
> Cuando hace eso, te fijaste si el disco realmente está trabajando o solo prende la luz? El disco hace un sonido aunque mínimo cuando está trabajando.

Me da toda la sensación de que el disco efectivamente está trabajando, además lo veo por un aumento de temperatura que me tiran los sensores que tengo instalados (aumentos dentro de los valores normales, pero que reflejan que el disco está generando calor).

Gracias por tu respuesta. Saludos.

Pablo A

---

### Post by pabloatilio on 2009-02-20
> **rojojuan said:**
> No se si será esto, pero podría ser:
Te fijaste en Sistema - Administración -Orígenes del software - Actualizaciones - Comprobar actualizaciones? Si esta marcado diariamente, una vez al día intenta comunicarse vía Internet y a veces pasa que un Repositorio no responde y sigue buscando


Efectivamente está marcado que compruebe si hay actualizaciones diariamente, pero suponiendo que haya un  repositorio que no responde ¿si o si se reflejaría en una actividad de disco ? ¿no sería en todo caso de internet ? ¿como puedo averiguar si hay un repositorio que no responde ?, 

Es interesante tu pregunta porque por ej. hoy después de actualizar un par de cosas (de gedit) y al rato de terminar la actualización, empezó otra vez con el problema, no lo hizo inmediatamente después de encender el equipo, sino un rato después (pongamos 20 minutos aprox) de terminar de actualizar.

También estoy revisando si no hay nada de esas indexaciones de contenidos y cosas por el estilo activadas, cualquier cosa que encuentre aviso.

Gracias por tu respuesta. Saludos.

Pablo A

---

### Post by guillermolisi on 2009-02-20
> **pabloatilio said:**
> Efectivamente está marcado que compruebe si hay actualizaciones diariamente, pero suponiendo que haya un  repositorio que no responde ¿si o si se reflejaría en una actividad de disco ? ¿no sería en todo caso de internet ? ¿como puedo averiguar si hay un repositorio que no responde ?, 

Es interesante tu pregunta porque por ej. hoy después de actualizar un par de cosas (de gedit) y al rato de terminar la actualización, empezó otra vez con el problema, no lo hizo inmediatamente después de encender el equipo, sino un rato después (pongamos 20 minutos aprox) de terminar de actualizar.

También estoy revisando si no hay nada de esas indexaciones de contenidos y cosas por el estilo activadas, cualquier cosa que encuentre aviso.

Gracias por tu respuesta. Saludos.

Pablo A
Tener SMARTmon tools permite detectar problemas causados por un regimen de trabajo forzado por causa de temperaturas extremas.

No seria la primera vez que un disco se termina "cocinando" por estar expuesto a un entorno termico extremo. Un sintoma previo a su rotura es la generacion de fallas y reintentos que desemboca en un circulo vicioso (mas fallas, mas reintentos, mas temperatura).

No todos los discos generan la misma temperatura. En una de las maquinas que uso tengo dos discos de la misma marca y tecnologia, ambos ventilados, y uno siempre esta dos o tres grados por encima del otro (una razon es porque contiene torrents que se comparten continuamente).

---

### Post by biale on 2009-02-20
Apoyo la propuesta de G Lisi. Y si por algún motivo no queres trabajar con las smartmontools, también estan los utilitarios del fabricante de cada disco. Grabas un diskette o Cd y corres los tests en modo standalone. Un test completo dura alrededor de 1/2 hora.

Si algo te induce a pensar que hay una elevación de temperatura en el interior del gabinete, directamente saca una de las tapas laterales y fijate como viene la mano. No te dejes estar porque los discos se arruinan. Recuerdo un disco SCSI que hacía escrituras incorrectas justamente por exceso de temperatura. ¿Los 3 discos estarán demasiado juntos?

Recien luego de descartar todo lo anterior analizaría el I/O. Yo no los usé nunca, pero hay paquetes linux que sirven para esto (systat?)

OT: Si no entendí mal tu configuración parece un tanto extraña, ya que los discos IDE son menos performantes que los sata.

Saludos a todos.

---

### Post by pabloatilio on 2009-02-20
Ahora volvió con el problema, como comenté, un rato después de hacer las actualizaciones, asi que reinicié y no lo hizo más, osea que tal vez, pudiera ser una de las cosas a ver, el tema ese de los repositorios que no encuentra. Voy a empezar a observar si el problema aparece después de que hace las actualizaciones automáticas y aviso.

Gracias a todos.

Saludos

Pablo A

---

### Post by pabloatilio on 2009-02-20
> **guillermolisi said:**
> Tener SMARTmon tools permite detectar problemas causados por un regimen de trabajo forzado por causa de temperaturas extremas.

No seria la primera vez que un disco se termina "cocinando" por estar expuesto a un entorno termico extremo. Un sintoma previo a su rotura es la generacion de fallas y reintentos que desemboca en un circulo vicioso (mas fallas, mas reintentos, mas temperatura).

No todos los discos generan la misma temperatura. En una de las maquinas que uso tengo dos discos de la misma marca y tecnologia, ambos ventilados, y uno siempre esta dos o tres grados por encima del otro (una razon es porque contiene torrents que se comparten continuamente).


Entiendo las razones de instalar SMARTmon tools, de momento el disco donde está instalado el S.O. parece que anda perfecto (ahora seguro que se rompe jaja) no da los síntomas de problemas por eso no agarro por ese lado. Lo que yo no puedo saber ni se me ocurre cómo hacerlo, es conocer CUAL es de los 3 discos que tengo el que marca actividad constante (voy a probar de desconectar el SATA y el otro ide para ver que onda).

Gracias por tu respuesta. Saludos.

Pablo A

---

### Post by pabloatilio on 2009-02-20
> **biale said:**
> 
Si algo te induce a pensar que hay una elevación de temperatura en el interior del gabinete, directamente saca una de las tapas laterales y fijate como viene la mano. No te dejes estar porque los discos se arruinan. Recuerdo un disco SCSI que hacía escrituras incorrectas justamente por exceso de temperatura. ¿Los 3 discos estarán demasiado juntos?

Recien luego de descartar todo lo anterior analizaría el I/O. Yo no los usé nunca, pero hay paquetes linux que sirven para esto (systat?)

OT: Si no entendí mal tu configuración parece un tanto extraña, ya que los discos IDE son menos performantes que los sata.

Saludos a todos.

Lo de la temperatura es algo que veo cuando se pone a funcionar sin parar el disco pero estoy hablando de uno a dos grados más o menos, encima hoy donde vivo hizo 45 grados de sensación térmica asi que si se bancan eso... jaja. Quizás sería cuestión de evaluar con 20 grados menos a ver que onda. Pero como puse en un post hace unos minutos, reinicié el equipo y anda perfecto y eso que hace más calor. Creo que cometí un error al mencionar lo de la temperatura porque puedo haber confundido o sugerido que hay un problema con eso y sinceramente no me parece que venga por ahi. 

Desde el mismo momento de armar el equipo busqué de situar los discos lo más separados posibles entre sí, dentro de las posibilidades que el gabinete me daba, están a no menos de 4 cm cada uno aproximadamente, no están pegados ni cerca de otra cosa que de calor. Incluso instalé hace un par de días (por las temperaturas que mencioné que hacen por aca) un nuevo ventilador que tira aire de afuera hacia el disipador del micro. 

Partiendo de la porquería que es el gabinete que tengo, está todo armado para que sea lo más fresco posible. Lo usaba sin la tapa lateral que me bajaba unos buenos grados pero la mugre que acumuló me terminó haciendo funcionar mal los ventiladores, disipador etc, pero esa es otra historia y muy larga de contar. 

Creo que no es algo relacionado con la temperatura porque como dije antes, en XP no hace esto. Me parece que no hay que buscar por ahí pero como no lo puedo descartar en un 100 %, aviso que onda con esa posibilidad.

Con respecto a tu comentario de la configuración de los discos, si, coincido con vos, no es la más indicada, o es "extraña" como diplomáticamente dijiste, te cuento que está así por la forma en que se fueron sucediendo las "capas geológicas" de discos en el equipo, porque me sirve para llevarme el SATA a otros equipos con todos los datos que necesito que están absolutamente todos ahí, y porque me da una pa*a (falta la j) tremenda reinstalar o reconfigurar o lo que sea, todo de nuevo jaja , tengo tantas cosas instaladas y puestas a punto que de solo pensar en eso me canso. La idea más adelante es sacar los ide y poner otro sata para los S.O.

Muchísimas gracias a todos.
Saludos.

Pablo

---

### Post by guillermolisi on 2009-02-20
> **pabloatilio said:**
> Lo de la temperatura es algo que veo cuando se pone a funcionar sin parar el disco pero estoy hablando de uno a dos grados más o menos, encima hoy donde vivo hizo 45 grados de sensación térmica asi que si se bancan eso... jaja. Quizás sería cuestión de evaluar con 20 grados menos a ver que onda. Pero como puse en un post hace unos minutos, reinicié el equipo y anda perfecto y eso que hace más calor. Creo que cometí un error al mencionar lo de la temperatura porque puedo haber confundido o sugerido que hay un problema con eso y sinceramente no me parece que venga por ahi. 

Desde el mismo momento de armar el equipo busqué de situar los discos lo más separados posibles entre sí, dentro de las posibilidades que el gabinete me daba, están a no menos de 4 cm cada uno aproximadamente, no están pegados ni cerca de otra cosa que de calor. Incluso instalé hace un par de días (por las temperaturas que mencioné que hacen por aca) un nuevo ventilador que tira aire de afuera hacia el disipador del micro. 

Partiendo de la porquería que es el gabinete que tengo, está todo armado para que sea lo más fresco posible. Lo usaba sin la tapa lateral que me bajaba unos buenos grados pero la mugre que acumuló me terminó haciendo funcionar mal los ventiladores, disipador etc, pero esa es otra historia y muy larga de contar. 

Creo que no es algo relacionado con la temperatura porque como dije antes, en XP no hace esto. Me parece que no hay que buscar por ahí pero como no lo puedo descartar en un 100 %, aviso que onda con esa posibilidad.

Con respecto a tu comentario de la configuración de los discos, si, coincido con vos, no es la más indicada, o es "extraña" como diplomáticamente dijiste, te cuento que está así por la forma en que se fueron sucediendo las "capas geológicas" de discos en el equipo, porque me sirve para llevarme el SATA a otros equipos con todos los datos que necesito que están absolutamente todos ahí, y porque me da una pa*a (falta la j) tremenda reinstalar o reconfigurar o lo que sea, todo de nuevo jaja , tengo tantas cosas instaladas y puestas a punto que de solo pensar en eso me canso. La idea más adelante es sacar los ide y poner otro sata para los S.O.

Muchísimas gracias a todos.
Saludos.

Pablo
Si solo sucede con Ubuntu podriamos empezar por ver que particiones tenes alojadas de Ubuntu en ese disco. Por ahi encontramos la respuesta a esa actividad anormal que percibis.

---

### Post by sebastianabate on 2009-02-21
Monitoreaste los procesos en el momento en que el disco está en actividad constante?
Lo que haría yo es finalizar todos los programas que tenga ejecutándose en primer plano, fijarme si existe algún proceso en segundo plano que esté haciendo uso del procesador (aunque sea mínimo) y detenerlo (con el comando correspondiente o en el último de los casos con un kill); si la actividad continúa hacer lo mismo con todos los demás procesos (estén o no usando el procesador) hasta determinar cuál es el que provoca la actividad del disco.

Para determinar si el problema es un paquete que quedó a medio instalar (lo que hace que cada vez que hacés una actualización intente realizar la configuración posterior) podés probar haciendo un "sudo apt-get install -f" y verificar si esto dispara la actividad del disco. Esto último se me ocurre por lo que comentabas sobre la relación que tiene tu problema con el momento en que se actualiza el sistema.

---

### Post by biale on 2009-02-21
>  puede permanecer horas asi (¿será que efectivamente no deja de estar girando o trabajando ? ).

Es que me parece raro que un proceso se vaya por I/O y sin afectar a los otros dos paramatros (CPU y memoria). Por ejemplo, un logging que escriba sobre el disco lo terminaría llenando y se nota. La actividad de paginacion desaforada tambien se notaría. ¿Un "busca pero, no encuentra y sin saltar error? Desde root, el comando top tendría que mostrar algo anornal. Cuando sucede el problema, notas alguna degradación en la performance?

Ahora bien y solo hasta donde yo se, el led indica direccionamiento de disco/s mas que actividad de disco/s. Lo descartaría en tu caso, pero solo como ejemplo comento que la confusión entre el jumpeo "simgle" versus "master" da este tipo de errores. A la larga, problemas mas bien de HW. 

Espero que algo de esto tenga alguna utilidad. Saludos a todos.

---

### Post by pabloatilio on 2009-02-24
Revisé todo de nuevo, repositorios, jumpers, cables, procesos, etc etc etc, hasta ahora, nada de nada. Les agradezco la ayuda a todos, voy a seguir trabajando en este asunto teniendo en cuenta los consejos que me han dado.

Si bien pienso buscar en internet, les pregunto : ¿ Qué herramientas de análisis y diagnóstico de discos para linux conocen/recomiendan ?. 

En especial me interesa alguna que hayan utilizado personalmente, y me puedan dar su opinión sobre la misma. 

También me gustaría algún soft  que revise la estructura lógica del disco, es decir la consistencia del sistema de archivos. Se me ocurre que pudiera existir alguna inconsistencia por efecto de algún corte de luz por ej.  Cuando me pasó eso, el sistema se encargó de revisar el disco y todo esa onda, pero tal vez no haya quedado bien.


Cuando vea que es lo que pasa exactamente les cuento.
Gracias de nuevo, saludos.

Pablo A

---

### Post by rojojuan on 2009-02-24
Yo no lo probé pero fijate aquí:

[http://www.laconsolablog.com/2009/02/23/gsmartcontrol-como-es-la-salud-de-su-hd-en-linux/](http://www.laconsolablog.com/2009/02/23/gsmartcontrol-como-es-la-salud-de-su-hd-en-linux/)

---

### Post by guillermolisi on 2009-02-24
> **pabloatilio said:**
> 

También me gustaría algún soft  que revise la estructura lógica del disco, es decir la consistencia del sistema de archivos. Se me ocurre que pudiera existir alguna inconsistencia por efecto de algún corte de luz por ej.  Cuando me pasó eso, el sistema se encargó de revisar el disco y todo esa onda, pero tal vez no haya quedado bien.


Cuando vea que es lo que pasa exactamente les cuento.
Gracias de nuevo, saludos.

Pablo A
```
fsck
```

---

### Post by hictio on 2009-02-24
> **guillermolisi said:**
> ```
fsck
```

Mhhhm, permitime que agregue algo; lee el man page de 'fsck', no podés ejecutarlo así como así en un HDD montando y funcionando.


pabloatilio,

Tu máquina qué es? Un desktop? Qué Desktop Environment estás usando?
Cuáles son las características de tu máq. (RAM, CPU, etc)?
Tenés poco espacio libre en tu HDD?
hay un proceso en particular 'scrollkeeper' que es mortal para las máquinas más o menos viejitas.

---

### Post by pabloatilio on 2009-02-25
Conozco el comando fsck, yo me refería a si había alguna otra herramienta.
Perdón por no aclararlo. Gracias a todos.

Saludos


Pablo A

---

### Post by pabloatilio on 2009-02-25
> **rojojuan said:**
> Yo no lo probé pero fijate aquí:

[http://www.laconsolablog.com/2009/02/23/gsmartcontrol-como-es-la-salud-de-su-hd-en-linux/](http://www.laconsolablog.com/2009/02/23/gsmartcontrol-como-es-la-salud-de-su-hd-en-linux/)

Lo voy a ver, muchas gracias. Saludos.

Pablo A

---

