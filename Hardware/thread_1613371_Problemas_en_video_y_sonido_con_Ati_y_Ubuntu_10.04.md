---
title: "Problemas en video y sonido con Ati y Ubuntu 10.04"
date: 2010-11-04
forum: Hardware
---

### Post by alavorano on 2010-11-04
Hola, mi problema es el siguiente. Tengo Ubuntu 10.04 con una Ati Radeon HD 5770, y el tema es que cuando veo videos (tanto de megavideo, youtube, [me pasa con firefox y chromium], e incluso videos no desde internet sino desde mi disco) se ven bien y al cabo de unos minutos, o segundos ya se empieza a ver entrecortado. Se sigue viendo el video, pero todo lagueado. Esto me pasa tambien con la musica en gral. Si me pongo a escuchar algun mp3 (o cualkier extension..), tmb se escucha entrecortado.
Que hago?? Estuve buscando por tooodos lados, como 2 dias , y no encuentro la solucion!!! 
Onda.. kiero migrar a Ubuntu, pero estas cosas no lo facilitan.
Saludos

PD: Probe tanto con los drivers de ubuntu y los de la pagina de ati, pero es el mismo resultado.

---

### Post by hectorivand on 2010-11-04
> **alavorano said:**
> Hola, mi problema es el siguiente. Tengo Ubuntu 10.04 con una Ati Radeon HD 5770, y el tema es que cuando veo videos (tanto de megavideo, youtube, [me pasa con firefox y chromium], e incluso videos no desde internet sino desde mi disco) se ven bien y al cabo de unos minutos, o segundos ya se empieza a ver entrecortado. Se sigue viendo el video, pero todo lagueado. Esto me pasa tambien con la musica en gral. Si me pongo a escuchar algun mp3 (o cualkier extension..), tmb se escucha entrecortado.
Que hago?? Estuve buscando por tooodos lados, como 2 dias , y no encuentro la solucion!!! 
Onda.. kiero migrar a Ubuntu, pero estas cosas no lo facilitan.
Saludos

PD: Probe tanto con los drivers de ubuntu y los de la pagina de ati, pero es el mismo resultado.

Hola, instalaste los restricted codecs for Ubuntu?

Saludos
Nacho

---

### Post by alavorano on 2010-11-04
Los ubuntu-restricted-extras? Si, ya los tenia.

---

### Post by hectorivand on 2010-11-04
> **alavorano said:**
> Los ubuntu-restricted-extras? Si, ya los tenia.

OK, vamos por parte, si ves video con Totem, ahí ya hay problemas, porque es un bug conocido que entrecorta música, video, etc. Instalate VLC Player.

```
sudo apt-get install vlc
```

Para los vídeos de Internet, Flash Player... tenes instalado el de Adobe o los alternativos?

Saludos
Nacho

---

### Post by alavorano on 2010-11-05
Nacho, ya me habia instalado el VLC Player, y pasa lo mismo. Tanto pa musica como video. Respecto a lo de Flash Player, tengo instalados lo de Adobe.
Tengo los siguientes plugins:
DivX Web Player 1.4.0.233
IcedTea NPR Web 1.8.2
ITunes Application Detector
QuickTime 7.6.6
Shockwave Flash 10.1 r85
VLC 2.30.2
Win Media Player 2.30.2

PD: Por si me lo terminas sugiriendo en algun momento, de antemano t digo que la makina la formatee hace poco. Asi que no creo q formatear sea solucion. Por las :P

Aldu

---

### Post by hectorivand on 2010-11-05
> **alavorano said:**
> Nacho, ya me habia instalado el VLC Player, y pasa lo mismo. Tanto pa musica como video. Respecto a lo de Flash Player, tengo instalados lo de Adobe.
Tengo los siguientes plugins:
DivX Web Player 1.4.0.233
IcedTea NPR Web 1.8.2
ITunes Application Detector
QuickTime 7.6.6
Shockwave Flash 10.1 r85
VLC 2.30.2
Win Media Player 2.30.2

PD: Por si me lo terminas sugiriendo en algun momento, de antemano t digo que la makina la formatee hace poco. Asi que no creo q formatear sea solucion. Por las :P

Aldu

Entonces, tu problema es psicológico :P jejeje

Me mataste, si no es un tema de drivers, tampoco de codecs, menos de reproductores. Puede ser algún tema de hardware que se recaliente y baje rendimiento?

¿Qué maquina tenes? fijate si podes postear o controlar las temperaturas? con xsensors, lo podes hacer.

```
sudo apt-get install xsensors
```

Saludos
Nacho

---

### Post by alavorano on 2010-11-06
Hola nacho, t cuento:
Tengo un procesador AMD Athlon(tm) II x4 640, con 4 gb de ram, la placa ati hd 5770 (1gb), ubuntu 10.04, Gnome 2.30.2.
Aca t mando la imagen de las temperaturas, el tema es q no c que onda.. cuando lo veas vos sabras q es de cada cosa.

[IMG]http://img191.imageshack.us/img191/6862/temperaturas.png[/IMG]

Los 2 de la derecha de todo son el disco de los SO y el disco de datos, respectivamente.

Aldu

---

### Post by guillermolisi on 2010-11-06
Alavorano

Por favor adecua tu escritura porque:

Es de mal gusto escribir de esa forma cuando todos los demas te escriben corectamente. Si estas te faltan teclas por favor aclara que tenes un problema tecnico. Si directamente no tenes ganas o estas apurado, no escribas, nadie te obliga a hacerlo.

Escribiendo asi se hace imposible que alguien que necesite traducir tus posts pueda hacerlo via Google Translator o la herramientea que fuese.

Estas formas no son aceptadas en al Comunidad Ubuntu ya que se alejan del espiritu que se busca mantener (podes leer el Codigo de Conducta para mas informacion).

Gracias por prestar atencion a este asunto.

---

### Post by hectorivand on 2010-11-08
Las temperaturas están perfectas, me resulta raro que tengas ese tipo de problemas, los drivers que viene con la distro de hecho funcionan mejor que los provisto por ATI, con lo cual tiene que venir por otro lado el problema y siendo Ubuntu, ya se escapa de mis manos. 

Tal vez alguien con más experiencia en Ubuntu nos pueda iluminar sobre el problema que te afecta.

Por último, buscaste en Google sobre personas con problemas similares?

Saludos

Nacho

---

### Post by marcelo_bur on 2010-11-08
> **hectorivand said:**
> 

Por último, buscaste en Google sobre personas con problemas similares?

Saludos

Nacho

Hola. Yo, de puro curioso, busqué un poco en la red y por ahí leí que el problema puede estar en la tarjeta de sonido, no en la de video.
Saludos

---

### Post by hectorivand on 2010-11-08
> **marcelo_bur said:**
> Hola. Yo, de puro curioso, busqué un poco en la red y por ahí leí que el problema puede estar en la tarjeta de sonido, no en la de video.
Saludos

Hola Marcelo, es buena la observación, en ese caso aplicaría a solo reproducción de sonido, pero acá también, tenemos problemas en la reproducción de video, con lo cual, la cosa se pone más peliaguda, siendo que ya probo con los drivers, tanto propietarios como los que viene con la distro.

Saludos
Nacho

---

### Post by alavorano on 2010-11-08
> **hectorivand said:**
> Las temperaturas están perfectas, me resulta raro que tengas ese tipo de problemas, los drivers que viene con la distro de hecho funcionan mejor que los provisto por ATI, con lo cual tiene que venir por otro lado el problema y siendo Ubuntu, ya se escapa de mis manos. 

Tal vez alguien con más experiencia en Ubuntu nos pueda iluminar sobre el problema que te afecta.

Por último, buscaste en Google sobre personas con problemas similares?

Saludos

Nacho


Nacho, lo peor es que se que es algo de Ubuntu.. logicamente, porque en el win7 me funciona de 10, tanto video como sonido.
Respecto a la pregunta, sí.. me mate buscando antes de publicar. De hecho este fue mi ultimo recurso.

Saludos
Aldu

---

### Post by hectorivand on 2010-11-08
> **alavorano said:**
> Nacho, lo peor es que se que es algo de Ubuntu.. logicamente, porque en el win7 me funciona de 10, tanto video como sonido.
Respecto a la pregunta, sí.. me mate buscando antes de publicar. De hecho este fue mi ultimo recurso.

Saludos
Aldu

Ok, tenes razón, es algo de Ubuntu, no te estoy diciendo que no, el tema es que.

Si probaste todos los drivers, todas las aplicaciones, todas las opciones, que pueda ser, no lo se.

Yo tengo ATI, AMD y no tengo estos mismos problemas.

Saludos
Nacho

---

### Post by guillermolisi on 2010-11-08
> **hectorivand said:**
> Ok, tenes razón, es algo de Ubuntu, no te estoy diciendo que no, el tema es que.

Si probaste todos los drivers, todas las aplicaciones, todas las opciones, que pueda ser, no lo se.

Yo tengo ATI, AMD y no tengo estos mismos problemas.

Saludos
Nacho
Si es "algo de Ubuntu" entonces probaria con otra distribucion en modo live a ver que pasa (Suse, Debian, Arch, etc.).

En general lo que no funciona en una distribucion suele no funcionar en otras porque tiene que ver con cuestiones de drivers/modulos que no estan pulidos a raiz de que la tecnologia y especificaciones del hardware no se brindan en forma completa y adecuada. Tambien suele ocurrir que quienes trabajan esos drivers/modulos lo hacen en tiempos marginales con lo cual una version pulida de los mismos demora un poco mas que sus equivalentes para Win, por dar un ejemplo.

La prueba en modo Live nunca hay que descartarla, aunque sea con la misma version que se instalo, si es posible antes.

---

### Post by marcelo_bur on 2010-11-08
> **alavorano said:**
> Hola, mi problema es el siguiente. Tengo Ubuntu 10.04 con una Ati Radeon HD 5770, y el tema es que cuando veo videos (tanto de megavideo, youtube, [me pasa con firefox y chromium], e incluso videos no desde internet sino desde mi disco) se ven bien y al cabo de unos minutos, o segundos ya se empieza a ver entrecortado. Se sigue viendo el video, pero todo lagueado. **[COLOR="Red"]Esto me pasa tambien con la musica en gral. Si me pongo a escuchar algun mp3 (o cualkier extension..), tmb se escucha entrecortado.[/COLOR]**
Que hago?? Estuve buscando por tooodos lados, como 2 dias , y no encuentro la solucion!!! 
Onda.. kiero migrar a Ubuntu, pero estas cosas no lo facilitan.
Saludos

PD: Probe tanto con los drivers de ubuntu y los de la pagina de ati, pero es el mismo resultado.

Nacho, si tomé en cuenta esa observación que encontré en la red se debe a lo que remarqué en el primer post de este tema. ¿No es posible que el mal funcionamiento de la tarjeta de audio influya en el video?
Saludos

---

### Post by guillermolisi on 2010-11-08
> **marcelo_bur said:**
> Nacho, si tomé en cuenta esa observación que encontré en la red se debe a lo que remarqué en el primer post de este tema. ¿No es posible que el mal funcionamiento de la tarjeta de audio influya en el video?
Saludos
Si, y mas si la placa de audio no procesa por si misma la señales sino que se las pasa a la CPU para que ella misma se encargue. Es decir, algo similar a lo que pasa con placas de video comunes, pero con el audio.

Si la carga en procesar las señales de audio es alta, se resentira no solo el video sino el rendimiento de toda la maquina.

Para verificar esto con un "top" en consola/terminal mientras se escucha/ve material multimedia alcanzaria. Las variables a observar son Load Average y CPU(s). tambien podria aportar informacion ver si hay algun proceso que monopoliza el uso de CPU /en la lista de procesos corriendo).

---

### Post by hectorivand on 2010-11-09
> **guillermolisi said:**
> Si, y mas si la placa de audio no procesa por si misma la señales sino que se las pasa a la CPU para que ella misma se encargue. Es decir, algo similar a lo que pasa con placas de video comunes, pero con el audio.

Si la carga en procesar las señales de audio es alta, se resentira no solo el video sino el rendimiento de toda la maquina.

Para verificar esto con un "top" en consola/terminal mientras se escucha/ve material multimedia alcanzaria. Las variables a observar son Load Average y CPU(s). tambien podria aportar informacion ver si hay algun proceso que monopoliza el uso de CPU /en la lista de procesos corriendo).

Esta bueno, lo que decis, sobre todo al revisarlo, pero Guillermo, eso pasaba con sistemas viejos, cuando empezaba a venir todo onboard, allá por el 2000 o antes con chipsets SIS 530, para que tengan como referencia. Ahí si, usar una placa de sonido Onboard o peor aun, vídeo, significaba perdida terrible de rendimiento en el equipo, si eso funcionaba mal por algún motivo. sonaste.

A menos que el sonido este usando algo tipo Kernel en tiempo real, en los sistemas actuales, no te cuelga el equipo, ni te lo satura. Los SB (South Bridge) que son los que controlan ese tipo de "periféricos" están muy bien desarrollados y la carga del CPU que les puede generar es mínima, por más que no este andando como debería.

De todos modos, Alvaro, es altamente recomendable que pruebes lo que te comenta Guillermo, con un Live CD para ver que "dice", como se comporta.

Saludos
Nacho

---

### Post by hectorivand on 2010-11-09
Aclaro, antes de que me empiecen a tirar con cualquier cosa. NO digo que no pueda ser lo de la carga al cpu del la placa de sonido, tal vez es y como dice Guillermo, un mal driver hace que todo se vaya al cuerno.

Saludos
Nacho

---

### Post by sys.adm.og on 2010-11-09
A mi se me presento un problema similar hace meses en mi netbook, todo lo que reproducia se me entrecortaba, sea musica o video.
Acer Aspire One 1.6, 1.5Gb  RAM, 256 Mb Intel Grafica.

Como compartia con un windows con licencia en el y algunos programas a la vez no lo eliminaba.

Llegue a desarmar la netbook, hice de todo.
Pense que era el disco duro, pero mi instalacion de ubuntu era nueva. Entonces por probar reinstale el windows en su respectiva particion y me funciona de 10 a partir de eso!

Aunque en realidad iba a reinstalar los dos pero como me funciono no lo hice con el ubuntu!

Podría ser una alternativa!

---

### Post by guillermolisi on 2010-11-09
> **hectorivand said:**
> Aclaro, antes de que me empiecen a tirar con cualquier cosa. NO digo que no pueda ser lo de la carga al cpu del la placa de sonido, tal vez es y como dice Guillermo, un mal driver hace que todo se vaya al cuerno.

Saludos
Nacho
Una mala fuente de alimentacion o una CPU mal ventilada, tambien hacen mala magia.

Cuando recien empezas a exigirle rendimiento al hardware, posiblemente funcione bien hasta que comienza a levantar temperatura (por suciedad o porque la fuente no puede entregar la potencia que se requiere) y ahi empiezan los sintomas de perdida de cuadros en el video, congelamiento de imagenes, sonido entrecortado, etc. Hasta podria congelar o apagarse la maquina.

Lo menciono solo como para considerar otros aspectos posibles, por eso es importante leer los logs, monitorear procesos (top) y carga de maquina, temperaturas de CPU y discos.

Al margen de todo esto no sabemos que version de kernel se esta usando, detalles adicionales del hardware en uso, espacio libre en disco, estado de uso de la memoria RAM, que driver de video se esta utilizando realmente asociado a la placa, si hay algun proceso que se dispare y acapare recursos del sistema al ver/escuchar contenido multimedia, etc.

---

### Post by hectorivand on 2010-11-09
> **guillermolisi said:**
> Una mala fuente de alimentacion o una CPU mal ventilada, tambien hacen mala magia.

Cuando recien empezas a exigirle rendimiento al hardware, posiblemente funcione bien hasta que comienza a levantar temperatura (por suciedad o porque la fuente no puede entregar la potencia que se requiere) y ahi empiezan los sintomas de perdida de cuadros en el video, congelamiento de imagenes, sonido entrecortado, etc. Hasta podria congelar o apagarse la maquina.

Lo menciono solo como para considerar otros aspectos posibles, por eso es importante leer los logs, monitorear procesos (top) y carga de maquina, temperaturas de CPU y discos.

Al margen de todo esto no sabemos que version de kernel se esta usando, detalles adicionales del hardware en uso, espacio libre en disco, estado de uso de la memoria RAM, que driver de video se esta utilizando realmente asociado a la placa, si hay algun proceso que se dispare y acapare recursos del sistema al ver/escuchar contenido multimedia, etc.

Tranquilamente las opciones que comentas son validas, puede ser que una fuente que no este alimentando como corresponde el equipo hace que falle, lo mismo con la ventilación, sube la temperatura, no hay refrigeración y empieza a fallar. 

Al creador del tema, le pido que ponga un screenshot del monitor del sistema cuando el mismo este reproduciendo audio y vídeo, la solapa de recursos.

En una de esas, le esta pasando lo que me pasaba a mí con el driver privativo de ATI, se iba al 100% el procesador y se comía toda la memoria hasta que el sistema colapsaba. Eso no me pasa/ba con el driver que viene con la distro.

Saludos
Nacho

---

### Post by alavorano on 2010-11-09
Bueno, aca mando imagenes de lo que me piden:

[COLOR="DarkOrange"]**[SIZE="4"]Recursos del sistema al reproducir musica:[/SIZE]**[/COLOR]
[CENTER][SIZE="2"][IMG]http://img824.imageshack.us/img824/1302/10202480.png[/IMG][/SIZE][/CENTER]


[COLOR="DarkOrange"]**[SIZE="4"]Recursos del sistema al reproducir video:[/SIZE]**[/COLOR]
[CENTER][SIZE="2"][IMG]http://img64.imageshack.us/img64/9589/40770768.png[/IMG][/SIZE][/CENTER]


[COLOR="DarkOrange"]**[SIZE="4"]El comando "top":[/SIZE]**[/COLOR]
[CENTER][SIZE="2"][IMG]http://img222.imageshack.us/img222/6254/topvu.png[/IMG][/SIZE][/CENTER]


**Por otro lado, mando mas especificaciones de mi maquina:**
(Al final actualice a ubuntu 10.10)
[LIST]
[*]Kernel 2.6.35-22
[*]Ram 4GB
[*]Espacio Libre 80GB
[*]Procesador AMD Athlon II x4 640
[*]Estoy usando el driver del de ubuntu (el que esta para activar en controlador de hardware) (ya intente cno el nativo de ati, no funciona tampoco)
[*]Estuve revisando, no hay ningun proceso que se dispare al reproducir algo
[*]Por otro lado, la fuente es de 600w, funciona de 10 (en mi compu q tenia el año pasado nunca ningun problema, es la misma fuente).
[*]La maquina esta bien ventilada, y de hecho se ve en imagen posteada anteriormente que todas las temperaturas estan normales.
[*]Tengo dos disco de 500GB:
1er disco) Una particion win7, otra particion ubuntu, y otra mas para datos.
2do disco) Puro datos
[/LIST]
Todo parece estar de 10, por esa razon yo no veo donde esta el problema.

_**PD:**_ No se si es el momento o que, pero desde que actualice a 10.10 me esta funcionando genial el sonido, pero con el video seguimos con el problema. Igualmente, voy a tener el ojo puesto, a ver si fue coincidencia lo de la mejora de audio o efectivamente esa parte se resolvio.

Saludos
Aldu

---

### Post by guillermolisi on 2010-11-10
Efectivamente no hay carga significativa por lado alguno.

Si usas VLC, ahora con 10.10, tambien tenes problemas cuando reproducis video ?

Que driver de video estas usando ahora ? Para esto podes mostrarnos la salida del comando en consola/terminal "lsmod" (sin las comillas).

---

### Post by alavorano on 2010-11-10
Guillermolisi, usando el VLC del 10.10 sigo teniendo el mismo problema. No se soluciono nada. 
Un touh aparte:
Es más, de hecho ahora estoy desde otra compu, porque de la nada cuando prendo ubuntu me apaga, en el router, la luz que muestra que esta mi compu conectada por red; y por ende no me toma internet. Ayer funciono de 10, voy a suponer q es algo del momento, a ver si a la noche se arregla

[COLOR=DarkOrange]**[SIZE=4]Mando la imagen del lsmod:[/SIZE]**[/COLOR]

[IMG]http://img600.imageshack.us/img600/3497/lsmod.png[/IMG]

Saludos
Aldu

---

### Post by alavorano on 2010-11-10
> **alavorano said:**
> 
_**PD:**_ No se si es el momento o que, pero desde que actualice a 10.10 me esta funcionando genial el sonido, pero con el video seguimos con el problema. Igualmente, voy a tener el ojo puesto, a ver si fue coincidencia lo de la mejora de audio o efectivamente esa parte se resolvio.

Saludos
Aldu

Estuve viendo un par de cosas y me di cuenta que, por lo menos el sonido (video sigue siendo el mismo asunto), no se escucha entrecortado si lo leo desde alguna carpeta raiz. Si lo leo desde mi 2do disco (que es solo de datos, ahi no esta el ubuntu), entonces se escucha entrecortado. Asi que seguramente era por eso que me funcionaba bien, aunque no deberia pasar eso, porque en el win7 funciona de 10 si lo leo desde ese disco (donde tampoco tengo el win7).

Saludos
Aldu

---

### Post by sys.adm.og on 2010-11-11
> **alavorano said:**
> Estuve viendo un par de cosas y me di cuenta que, por lo menos el sonido (video sigue siendo el mismo asunto), no se escucha entrecortado si lo leo desde alguna carpeta raiz. Si lo leo desde mi 2do disco (que es solo de datos, ahi no esta el ubuntu), entonces se escucha entrecortado. Asi que seguramente era por eso que me funcionaba bien, aunque no deberia pasar eso, porque en el win7 funciona de 10 si lo leo desde ese disco (donde tampoco tengo el win7).


Yo creo que deberias de realizar un formateo de tu disco ya que es un disco particionado que no habras desfragmentado (esto es solo para las partiones ntfs o fat ya que en linux en las particiones ext2,3,4 se almacenan mas ordenaditos los archivos)!
Es por eso que tienes problemas con la lectura de datos.
Mira este post [http://www.vinagreasesino.com/articulos/para-que-sirve-desfragmentar-un-disco-duro.php](http://www.vinagreasesino.com/articulos/para-que-sirve-desfragmentar-un-disco-duro.php)
Talvez no parezca que eso sea el problema pero no esta demas salirse de la duda!
Pues como te mencione en ocasion anterior a mi me ocurrio lo mismo y asi lo solucione! Ademas desde la version vista de windows el manejo de partiones de la misma es mas delicada y sensible!

---

### Post by alavorano on 2010-11-11
Cuando tenga la pc de vuelta lo voy a probar (no deberia ser diferente, porque en win7 leo desde el mismo disco y se lee bien). Porque con esto de que perdi internet en los dos SO, estoy convencidisima (despues de hacer mil pruebas de hard y de soft) que se jodio el puerto de red del mother. Asi que dí la maquina para que me la arreglen (o cambien de mother que esta en garantia).

Saludos

PD: Formatee (por otra razon) volviendo al ubuntu 10.04 y no cambio nada, asi que.. formatear no es la solucion :P jaja

Aldu

---

### Post by marcelo_bur on 2010-11-11
> **alavorano said:**
> 
PD: Formatee (por otra razon) volviendo al ubuntu 10.04 y no cambio nada, asi que.. formatear no es la solucion :P jaja

Aldu

Hola. Creo que reinstalar o formatear siempre debe ser la última opción para un usuario de linux, eso se lo dejamos a los WIN USERS.
Saludos

---

### Post by hectorivand on 2010-11-11
> **marcelo_bur said:**
> Hola. Creo que reinstalar o formatear siempre debe ser la última opción para un usuario de linux, eso se lo dejamos a los WIN USERS.
Saludos

[OT] Ni tanto, por más errores que tenga, para todo hay una solución y no es precisamente el format C:. Aunque anda a decirle eso a todos los técnicos que veas.

Estaba leyendo y leí "convencidisima" y yo la llame Alvaro, Perdón :(  [/OT)

Saludos
Nacho

---

### Post by sys.adm.og on 2010-11-11
> **marcelo_bur said:**
> Hola. Creo que reinstalar o formatear siempre debe ser la última opción para un usuario de linux, eso se lo dejamos a los WIN USERS.
Saludos

soy de buscar el error a fondo ya que eso me permite conocer mas de errores de SO ya que estoy haciendo el mio y en mi trabajo tampoco puedo formatear por cualquier cosa los servidores:P
Pero no todos son amantes de buscar una solucion hasta esa instancia mas para los nuevos usuarios!

Saludos

---

### Post by sys.adm.og on 2010-11-11
> **alavorano said:**
> 
PD: Formatee (por otra razon) volviendo al ubuntu 10.04 y no cambio nada, asi que.. formatear no es la solucion :P jaja

Me referia a que formatees tu partion ntfs (osea win7) y la de datos! Mira el video de la importancia de desfragmentar particiones ntfs!
Aclaro nuevamente que en particiones ext2,3,4 no hace falta porque se almacenan en i-nodos!

PD: Lo formatear suguiero por la necesidad de desfragmentar los datos del disco! Para mejor rendimiento, velocidad y menos desgaste!

---

### Post by alavorano on 2010-11-14
Bueno, les comento que se me murio el puerto de red (es decir, el mother mató esa parte) por lo que le di la compu a un amigo mio que va a cmabiarme el mother, xq ta en garantia. Esto quiere decir que hasta que no me la devuelvan no voy a poder probar las cosas que ustedes me dicen. 
Asi que cuando la tenga de vuelta, voy a actualizarles el estado de la pc... quien sabe, a lo mejor cuando vuelva, "magicamente" funcione todo.

Saludos
Aldu

---

