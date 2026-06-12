---
title: "El Grub Rompediscos!!!"
date: 2008-10-05
forum: Hardware
---

### Post by victor_nesta on 2008-10-05
Titulo de película. Paso a explicar...
Ayer mientras paveaba, mi mama estaba mirando Dominio Digital (Se ve que no había buenas pelis), y con su escaso conocimiento y atención me conto que el canoso (Se refiere al ¨Chakal¨ Daniel Sentinelli) comento que el tener wingows y ubuntu en el mismo sistema, te rompe el disco. 

Después de varias horas tratando de descifrar los ¨cuadraditos¨ el ¨taka-taka¨ y demás explicaciones poco técnicas. Deduje que lo que dijo el Chakal es mas o menos esto.

Como todos sabemos el arranque de Guindows se graba en el MBR del disco, tambien llamada pista 0, el grub por su parte evita la carga de este posicionando parte de el por delante (los primero 512kb del disco, si no me equivoco).
Lo que decían es que el grub provocaba un salto del cabezal de lectura/escritura del disco, haciéndolo golpear y que después de muchos golpes obviamente se rompía.  

Hasta ahí pude deducir. No encontré el programa como para verlo con mis propios ojos y dar una explicación en detalle. 
Pero se que ustedes son muy pero muy Geeks Ubunteros y sabrán dar una respuesta. Jeje

---

### Post by pol666 on 2008-10-05
que se yo, a mi se me hizo percha un disco hace un mes cuando la prendi ni llego a cargar el... grub.



Che, lo que dice este tipo puede ser cierto :|???

---

### Post by victor_nesta on 2008-10-05
El ¨Chakal¨ era un grosso, una especie de NEO argento. Y por eso me llamo la atención.
Ahora si se lo chupo el sistema y arreglo con micro$$$oft , no lo se.

---

### Post by pol666 on 2008-10-05
Por cierto, ese "chacal" era un famoso hacker que estuvo en cana y todo?.

---

### Post by guisheca on 2008-10-05
Lo que mas me gusta de esta entrada es que se van a deschavar todos los que tienem dual boot con win jajajajaja, como yo :(.
En fin, alguien sabe mas o menos si esto es cierto o no??? Y si es cierto, se soluciona el problema quitando win?? o hay que deshacerse del grub?

---

### Post by santiagoward2000 on 2008-10-05
No sé técnicamente si es verdad o no, pero mi laptop vieja estuvo arrancando con GRUB un dual-boot con XP durante 2 años y el disco seguía andando...

---

### Post by Mauro22 on 2008-10-05
Si tenes linux solo, tambien se instala grub, aunque sin opciones...

Al cabo es lo mismo, tener dual boot o tener linux solo, siempre va a estar grub. Podes tener 2 distro de linux y, obvio, vas a tener grub ...


O sea... cual es el punto? sacamos el grub y volvemos a LILO ??

---

### Post by victor_nesta on 2008-10-05
Si este es el chakal que estuvo en cana. 
Estoy esperando que den la repetición del programa o que lo suban a la web.
Como dije, es una deduccion de lo que me dijo mi vieja que no entiende nada, de lo que si estaba segura que escucho es de que el dual-boot con win te rompe el HDD.

Daniel Sentinelli
[IMG]http://www.consejo.org.ar/Cv05/images/sentinelli_daniel.jpg[/IMG]
&#8226; Es un consultor en seguridad informática que se inició como hacker a comienzos de los años 80. Es conocido popularmente su intensa presencia en los medios (gráficos, radio, TV), pero también por sus actividades que a lo largo de los años han abarcan desde la investigación en inteligencia artificial, hasta el asesoramiento a organismos militares y de gobierno, corporaciones y pymes (tanto en el país como en el exterior)..."
fuente:[www.consejo.org.ar/Cv05/sentinelli_daniel.htm](www.consejo.org.ar/Cv05/sentinelli_daniel.htm)

---

### Post by leo_rockway on 2008-10-05
No sé por qué se me hace que es terrible FUD... pero bueh...

---

### Post by sajnox on 2008-10-05
FUD = [http://es.wikipedia.org/wiki/FUD](http://es.wikipedia.org/wiki/FUD)

Che, si en vez de decir lo que dijo la mama del que dijo que dijo lo que dijo.

1) Como dijeron antes todas las maquina tienen Grub, que no lo tengas con Dual boot de windows no quiere decir que no este, lo tenes aunque sea para arrancar en modo seguro.

2) Mas de una vi lo hasta muchacho de pelo canoso con remeras de open BSD y hablando bien de sistemas libres.

3) Antes de decir estas cosas que hacen ruido y no aclaran nada se puede enviar un mail al programa preguntando si efectivamente lo que entediste a tu mama, que como decis no entiende nada, es lo que efectivamente interpretas que dijo. 

Basicamente, manda un mail al programa y no digan cosas sin fundamento.

---

### Post by santiagoward2000 on 2008-10-05
> **sajnox said:**
> 1) Como dijeron antes todas las maquina tienen Grub, que no lo tengas con Dual boot de windows no quiere decir que no este, lo tenes aunque sea para arrancar en modo seguro.

La mía no (por lo menos no en el mrb). (Aclaro que no lo cambié por esto, pero bue...)

---

### Post by sajnox on 2008-10-05
Ya les mande un mail para ver si pueden ver el thread y aclarar esto.

Por el momento no hagamos mas comentarios salvo que alguien haya visto el programa y este seguro que entendio claramente lo que se dijo

---

### Post by victor_nesta on 2008-10-05
Bueno justamente abri el tema por que me llamo la atención por quien lo dijo. y abrí el tema para saber si alguien vio el programa, o tiene idea de que esto puede pasar.  
Busque en la pagina de Dominio Digital, en su foro y en toda la red, sobre este tema.
Masvale que cuando vea la repetición del programa si dijo otra cosa, lo voy a decir y si aporto algún otro dato también. No te equivoques, no fue para tirar bomba por que si. Es mas puse un titulo gracioso y le agregue Chimento?. para que no se tome tan enserio hasta no tener una prueba fehaciente.  

En fin, veremos que es lo que dijo si es que realmente dijo algo.
Saludos

---

### Post by Air23 on 2008-10-05
Yo lo vi el programa en cuestion. Por lo que me acuerdo de lo que dijo el chacal, el problema es con ciertas notebooks y ubuntu (y otras distro pero no todas). Estrictamente hablando, segun lo que entendi, el problema pasa por los fabricantes de los rigidos (y/o los de las notebooks) que solamente piensan que se va a usar windows.
Mis conocimientos tecnicos no son los mejores como para explicarlo con claridad, pero lo intentare. Parece que de fabrica vienen con politicas de ahorro de energia muy agresivas pero windows las sobreescribe y establece las propias, pero ubuntu no toca nada y entonces el disco se parkea muy seguido. Luego el numero de veces que se puede parkear es limitado y por ende el disco se arruina.
Les paso unos cuantos links para ampliar la informacion, sepan disculpar los errores que puedan existir en mi mini-explicacion.

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)
[http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)
[http://foros.3dgames.com.ar/linux-nix.112/453341.ubuntu-killing-laptop-harddrive.html](http://foros.3dgames.com.ar/linux-nix.112/453341.ubuntu-killing-laptop-harddrive.html)
[http://www.mail-archive.com/lugro@lugro.org.ar/msg23037.html](http://www.mail-archive.com/lugro@lugro.org.ar/msg23037.html)

Esta es la pagina del programa: [http://www.dominio-digital.com.ar/veronline.htm](http://www.dominio-digital.com.ar/veronline.htm) y pueden ver los programas enteros (creo que todavia no esta el programa del que hablamos)
El chacal parece buena onda, no hablo del tema con mala intencion anti GNU/Linux ni nada por el estilo.

---

### Post by victor_nesta on 2008-10-05
Sisi, tal cual entre los gerogrificos de mi vieja estaba el de notebooks!
y el resultado es el esperado, el problema no es ubuntu.
estoy buscando el P*** programa, en cuanto lo suban aviso.
Gracias AIR23, me sacaste de un brete ya que en parte es verdad que no tenia nada que ver con lo que dije. jeje pero ya lo aclare.

---

### Post by Air23 on 2008-10-05
> **victor_nesta said:**
> Gracias AIR23, me sacaste de un brete ya que en parte es verdad que no tenia nada que ver con lo que dije. jeje pero ya lo aclare.

De nada :)

---

### Post by sajnox on 2008-10-05
> **victor_nesta said:**
> Bueno justamente abri el tema por que me llamo la atención por quien lo dijo. y abrí el tema para saber si alguien vio el programa, o tiene idea de que esto puede pasar.  
Busque en la pagina de Dominio Digital, en su foro y en toda la red, sobre este tema.
Masvale que cuando vea la repetición del programa si dijo otra cosa, lo voy a decir y si aporto algún otro dato también. No te equivoques, no fue para tirar bomba por que si. Es mas puse un titulo gracioso y le agregue Chimento?. para que no se tome tan enserio hasta no tener una prueba fehaciente.  

En fin, veremos que es lo que dijo si es que realmente dijo algo.
Saludos

No dudo de tus buenas intenciones el tema es que si alguien busca algo parecido a grub y se encuentra con esto puede llegar a conclusiones equivocadas. Hay que ser muy medido en cuanto hablas de problemas de ese tipo.

---

### Post by victor_nesta on 2008-10-05
> **sajnox said:**
> No dudo de tus buenas intenciones el tema es que si alguien busca algo parecido a grub y se encuentra con esto puede llegar a conclusiones equivocadas. Hay que ser muy medido en cuanto hablas de problemas de ese tipo.

Tal cual. Y pido disculpas. por eso le como tags puse chimentos y no una palabra clave importante, aunque el titulo puede confundir.
Mil perdones

---

### Post by pol666 on 2008-10-05
Osea, Existe una posibilidad que mi disco Samsung se halla cagaù por eso mismo?

---

### Post by Hei Ku on 2008-10-05
Este es un problema conocido, y no tiene que ver con el GRUB, si no con las politicas de parking cuando usas ahorro de energia. De hecho, hay varios threads referidos a este tema y cómo configurar los parámetros.

---

### Post by faktorqm on 2008-10-06
```
man hdparm
``` :D

---

### Post by sajnox on 2008-10-06
A todos,

La gente de Dominio Digital rapidamente respondio la pregunta con dos mails.

Primer Mail: Hoy a la mañana

```
Estimado Miguel,

Lo que dijo Sentinelli es que Ubuntu mantiene los parametros definidos
por el fabricante en cuanto al funcionamiento del disco sin intervenir
en cuanto a lo que se refiere al parkeo de las cabezas del disco y eso
si se mantiene por default causa que este ciclo acelere el desgaste
del disco rigido.

Saludos,

El equipo de DD.
```


Segundo mail: 15hs

```
Estimado Miguel,

Ya hemos subido el programa y pueden ver exactamente que se dijo. Hay
una confusion, nunca se hablo de problemas cuando se tiene un  dual boot.

En caso de que uds quieran hacer alguna aclaracion estan invitados al
proximo programa a dar su opinion en caso de que sea diferente a la de
Daniel.

http://video.google.com/videoplay?docid=-9145371969406643708&hl=en

Saludos,

El Equipo de DD.
```

Obviamente les agradeci su colaboracion y su rapida respuesta en el tema.

Si bien esto se hablo en threads anteriores y en la lista les pido a algunos de los amigos que "que la tienen clara" que expliquen en lenguage humano de que hablan y cuales eran las posibles soluciones.

Saludos a todos.

---

### Post by victor_nesta on 2008-10-06
Quedo Clarisimo!
Gracias Sajnox

---

### Post by guisheca on 2008-10-06
Tengo unas ganas imparables de golpearlo al pelado de microsoft, hasta que le salgan pelos de tantos golpes...
Me pase, saludos

---

### Post by Mister X on 2008-10-06
> **guisheca said:**
> Tengo unas ganas imparables de golpearlo al pelado de microsoft, hasta que le salgan pelos de tantos golpes...
Me pase, saludos

jajajaja

por las dudas no abramos una encuesta para ver quien mas tiene ganas de pegarle...

---

### Post by Hei Ku on 2008-10-06
> **guisheca said:**
> Tengo unas ganas imparables de golpearlo al pelado de microsoft, hasta que le salgan pelos de tantos golpes...
Me pase, saludos
Tambien podriamos obligarlo a usar Vista en una pc con menos de 1GB, sin placa aceleradora. :lolflag:

---

### Post by Air23 on 2008-10-06
> **Hei Ku said:**
> Tambien podriamos obligarlo a usar Vista en una pc con menos de 1GB, sin placa aceleradora. :lolflag:

Demasiada crueldad

---

### Post by sajnox on 2008-10-06
> **Hei Ku said:**
> Tambien podriamos obligarlo a usar Vista en una pc con menos de 1GB, sin placa aceleradora. :lolflag:

No podemos obligar a hacer lo que no se puede hacer

---

### Post by faktorqm on 2008-10-06
Son todos unos ignorantes los que hacen ese programa, no merecen estar al aire, pero... como siempre, los ***** con guita.... hacen lo que quieren. 

Creo que se dedican a hacer ese programa por que laburando de informaticos se **** de hambre... malisimos todos.

Mi calificacion (de 1 a 10): -14

---

### Post by sajnox on 2008-10-06
> **faktorqm said:**
> Son todos unos ignorantes los que hacen ese programa, no merecen estar al aire, pero... como siempre, los ***** con guita.... hacen lo que quieren. 

Creo que se dedican a hacer ese programa por que laburando de informaticos se **** de hambre... malisimos todos.

Mi calificacion (de 1 a 10): -14

Y como siempre les recordamos que las opiniones vertidas por los participantes del foro no necesariamente revelan la posicion de los moderadores del foro, ni de Canonical ni de ninguna de sus empresas.

---

### Post by pol666 on 2008-10-06
> **faktorqm said:**
> Son todos unos ignorantes los que hacen ese programa, no merecen estar al aire, pero... como siempre, los ***** con guita.... hacen lo que quieren. 

Creo que se dedican a hacer ese programa por que laburando de informaticos se **** de hambre... malisimos todos.

Mi calificacion (de 1 a 10): -14

O_o ... si al final, no habian dicho en nada en contra de Ubuntu ni de grub ni de nada.

---

### Post by faktorqm on 2008-10-07
> **pol666 said:**
> O_o ... si al final, no habian dicho en nada en contra de Ubuntu ni de grub ni de nada.

una tipa, que se maravilla por tener un pendrive de 1gb del tamaño de una tarjeta de credito, existiendo hace años las memorias micro SD, (y ahora estan las de 8gb), hola? hola? tuuuu tuuu tuuu...

el chabon, (daniel) y a menos que yo haya escuchado mal (lo puse 4 veces) en el minuto 1:58 dice "uno punto ocho megahertz" (verificar por favor) 
o sea que su micro es mas lento que un usb normal....

el pelado, (que defiende a microsoft sin decirlo), cuando hablaron de servidores dijo "no, si eso no lo discuto, blabla" pero cada vez que daniel decia algo de ubuntu el pelado ponia cara de "ese sistema no anda, jajaja".

El conductor... bueno lo perdono por que solo era conductor :P

---

### Post by Hei Ku on 2008-10-07
Mi impresion, cuando lo vi hace unos años, fue que eran 3 paquetes alrededor de Daniel. No era un programa bueno tecnicamente sino apenas de divulgación para "gente común" en un canal de cable de Argentina. O sea, no le pidas demasiado.
Es como pedirle a Fabian Garcia que te tire la posta tecnica de algo (los que trabajan en sistemas sabrán de quién hablo). Hace muchos años, puede ser, pero hoy ya no se dedica a eso.

---

### Post by victor_nesta on 2008-10-07
Y es como con el programa EDUHARD. En un primer momento era ¨entretenido¨ no se si muy innovador pero entretenido. Depues cuando firmaron con ******* quedo súper propagandístico y demasiado bolu**. 
-¿Con esta placa sintonizadora puedo mirar la TV? 
-Si, instalas el w***** v***, y con el superdriver podes mirar la tv.

---

### Post by DanielSentinelli on 2008-10-08
-----BEGIN PGP SIGNED MESSAGE-----

"...hola, soy Troy McClure, y quizás me recuerden de películas como
'Las locuras de los hackers de vacaciones' o 'Los que usan Linux las
prefieren tetonas'..."

Digo... ¡Hola! Soy Daniel Sentinelli, y quizás me recuerden de
programas como 'Dominio Digital' temporadas 1, 2, 3, 4, 5, 6, 7, 8, 9,
10, 11, 12 y 13...

Hablo de muchas cosas en el programa y no se que es lo que finalmente
sale al aire después de la edición, pero efectivamente en una grabación
hace un par de semanas hablé sobre Ubuntu, y entre otras muchas cosas,
mencioné el tema del desgaste prematuro de algunos discos en algunas
notebooks.

El problema es conocido, fue reportado inicialmente hace dos años en
https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695 , y se
viene discutiendo desde entonces.

A pesar de eso (y es parte de lo que planteaba en el programa),
muchísima gente no esta informada del tema tal como demuestran los
posts en este thread, aun cuando se ha discutido en infinidad de
lugares incluyendo acá en Ubuntu Forums, por ejemplo en
http://ubuntuforums.org/showthread.php?t=795327 .


victor_nesta:

* No es necesario que inventes la historia de "tu mama", podés
reconocer que ves Dominio Digital y que no entendiste nada de lo que
dije...

Ya que hablás de "explicaciones poco técnicas", quisiera aclararte que
la tuya está ligeramente equivocada. El MBR (Master Boot Record) no
está en tooooda la pista 0, si no que ocupa sólo el sector 0 del disco.
He tenido que programar varios boot loaders (en Assembler, por
supuesto) y te aseguro que es un soberano dolor de huevos, porque ni
siquiera tenés esos 512 bytes completos ya que el MBR comparte ese
sector con la tabla de particiones que empieza en el byte 01BEH, y
encima Windows 2000 o superior te estampan una "drive signature" en
01B8H. O sea que sólo tenes 440 bytes para tu código, datos, mensajes
de error, y todo lo que necesites como chequear si la BIOS soporta LBA,
etc.

Obviamente no es mucho lo que podes hacer allí, así que el loader en el
MBR solo puede hacer lo mínimo como para cargar un programa de booteo
mas sofisticado (como GRUB), y transferirle el control. Para peor, la
BIOS carga el MBR en la posición de memoria 0000:7C00, pero el
siguiente programa de booteo también espera ser cargado en ese lugar,
así que lo primero que tiene que hacer tu boot loader es auto
desplazarse a otra zona de memoria libre y transferir el control a la
nueva instancia de sí mismo. En fin, nada del otro mundo, pero es algo
engorroso.

Eso sí, todo esto no tiene *NADA* que ver con el tema que yo mencioné
en el programa.

* El que trabaja para Microsoft es Alejandro Ponike, el pelado. Yo no
recibo plata de nadie para hablar a favor o en contra de un producto.
Mis opiniones podrán parecerte estupideces, pero al menos son todas
mías y salidas de mi cabeza, no son escritas por el área de marketing
de ninguna empresa multinacional.


pol666:

* Es posible que tu disco haya muerto prematuramente por este problema.
Verificá en los links que menciono más arriba si el modelo esta listado
entre los conocidos.

* Afortunadamente, nunca estuve en cana. Bueno, de pibe he pasado
alguna noche por "averiguación de antecedentes" por estar fumando,
tomando birra y bardeando en una plaza. Pero creo que eso no cuenta,
¿no?


guisheca y Mauro22:

* Ni GRUB ni el dual boot son un problema, no se preocupen por eso.


sajnox, Air23:

* Buen trabajo parando la bola de rumores, recurriendo a las fuentes, y
aclarando el tema con info concreta.


faktorqm:

* En mi opinión, un comentario como "man hdparm" no resulta útil en el
contexto de la "gran masa" de usuarios que esperamos alcanzar con
Ubuntu. Esa forma de responder es ideal en otro contexto como puede ser
el de usuarios de Gentoo, por ejemplo, donde es esperable (y casi hasta
exigible) otro tipo de predisposición técnica.

Más aun, y es parte de lo que comentaba en el programa, creo que el
usuario "masivo" de Ubuntu no debería estar usando hdparm para resolver
este tema porque ya existe una solución más global implementada en
"laptop-mode-tools", más algún par de detalles extras que están bien
documentados en https://wiki.ubuntu.com/PowerManagement .

El problema es que todo esto sigue siendo demasiado confuso para el
usuario promedio. Creo que durante la instalación debería haber un
hermoso cartel que diga "¿Está instalando Ubuntu en una notebook? Si -
No" y a partir de ahí que se configuren los defaults de acuerdo a la
respuesta. Después, si el tipo sabe lo que hace, siempre puede tocar a
mano lo que quiera. Algunas de estas cosas ya van a estar más pulidas
en Intrepid, pero lamentablemente mientras que la gente que escribe al
dope es una multitud; los que laburan, escriben código, prueban betas y
reportan adecuadamente errores son una minoría en todos los proyectos.

* Después de tu inteligentísimo comentario sobre lo ignorantes y
malísimos que somos, no me queda nada más para aportar. Supongo que así
esperás estimular a que muchos otros periodistas se animen a hablar de
Linux y Ubuntu por TV, ¿no? Por favor, no dejes de mirarnos así el
rating no nos baja a la mitad, y mis hijas no se mueren de hambre
cuando dejen de pagarme millones por... ¡Ah, no!... Cierto que lo hago
de onda y nadie me da un centavo por esto. Ufff... por un momento me
había asustado...

En serio, pensalo un poco. Un comentario así a mi me importa un comino,
y si a vos te hace sentir que quedás como un piola bárbaro, me alegro
mucho por vos. Ahora imaginate el efecto que va tener en un periodista
junior de un medio masivo al que le gustaría jugarse por hacer una nota
sobre "Instale Linux en su PC" que van a leer millones de personas,
pero que ante el riesgo de que una crítica como la tuya llegue a su
jefe de redacción, va a optar por ir a lo seguro y escribir sobre "Como
aprovechar las cáscaras de zanahoria para hacer sopa". Y nunca te vas a
enterar...

* Si dije "megahertz" no te sorprendas. Da las gracias que no dije
"megaterios", "megalómanos" o "megáfonos". Ese programa lo grabamos a
las 10 de la mañana, y antes de que hubiera tomado café.


Hei Ku:

* La televisión es un medio masivo dirigido a "gente común" (como la
mamá de victor_nesta, por ejemplo). La información técnica
especializada podés encontrarla en algunos foros y sites temáticos. Si
esperás encontrar información técnica avanzada en un programa de TV
estás tan equivocado como si esperaras encontrar las zapatillas adentro
de la heladera (a no ser que tengas hábitos alimentarios muy
peculiares).


Todos:

Participo en Dominio Digital porque Claudio me invita y me sigue
invitando desde hace 13 años, y si bien tengo libertad para decir lo
que quiero, tengo que mantenerme dentro de ciertos márgenes de
razonabilidad en los que está planteado el programa. En ese contexto
hemos hablado de GNU/Linux, de distintas distros y programas, hemos
dedicado emisiones enteras a charlas con Richard Stallman, hemos hecho
notas con varios "referentes locales" de la comunidad, hemos
sponsoreado y transmitido eventos y conferencias generados por LUGar
y/o CaFeLUG como CaFeCONF, hemos distribuidos CDs de "Linux - Dominio
Digital" hace años cuando muchos de los que están acá todavía debían
estar en el colegio primario, etc, etc, etc...

Ahora, si para hablar de temas altamente técnicos tuviera que ponerme a
hacer mi propio programa de TV, la verdad es que no sabría ni por donde
empezar, además de que solo lo mirarías vos y otros 4 tipos. Y
honestamente tampoco tendría las ganas de hacerlo. El día tiene solo 24
horas y si bien me gusta estar en DD, tengo muchas otras prioridades.
Digamos que para mí participar en DD es quizás como puede ser para vos
participar en un foro como este.

Aun así, si comparás DD con otros programas pretendidamente
informáticos como alguno que es solo el frente publicitario de una
academia que enseña "reparación de PCs"... creo que sigue siendo de lo
más tecnológico que hay disponible.

Pero si alguien tiene la capacidad de hacer un programa de TV con
orientación altamente técnica; y consigue que le vendan el espacio; y
contrata estudios, y camarógrafos, y sonidistas; y alquila o compra sus
propias cámaras, micrófonos, consolas, etc.; y contrata muchas horas de
edición o pone su propia estructura para editar; y encuentra una manera
de pagar todo eso garantizando la continuidad por lo menos por un par
de años; y me invita a participar; desde ya que puede contar con toda
mi colaboración.

Es más, ni siquiera hace falta que haga su propio programa. Si alguien
se compromete a participar regularmente en DD hablando de Linux,
preparando unos 10 temas para cada grabación aunque al final sólo quede
al aire uno o dos, estando listo para suspender lo que sea necesario
para ir a grabar con sólo unas horas de anticipación, ensayando lo que
va a decir para no demorarnos la grabación porque se traba a cada rato
hasta que le tome la mano a la cosa después de unos años de grabar, y
estando dispuesto a que a pesar de todo su esfuerzo después lo bardeen
en todos los foros porque tenía desacomodado el
flequillo; estoy seguro de que Claudio va a estar más que dispuesto a
darle un lugar en el programa. Pero con continuidad, eh... no un par de
veces para que lo feliciten la mamá y los parientes y después
desaparece.

Ni siquiera hace falta que participe en el programa. Con que solo se
tomen el trabajo de redactar varios "scripts" básicos sobre algunos
temas, con un buen resumen de cada uno, links a imágenes, videos,
screenshots, etc, pensados como para una nota en TV de 5 minutos, ya
sería de mucha ayuda para preparar los temas.

Esto mismo ya lo he planteado cientos de veces en distintos lugares,
pero lamentablemente más allá de infinitas quejas y promesas varias (y
unas pocas y honrosas excepciones), es muy poca la colaboración que se
recibe.

En fin, por mi parte en particular, y de DD en general, están todas las
puertas abiertas (dentro del sentido común más elemental) para
contribuir como sea posible en la difusión del software libre en
general, y de Ubuntu en este caso en particular. Cualquier idea que
sirva para aprovechar mejor ese espacio es bienvenida.

Pueden comunicarse con nosotros a las direcciones de e-mail que figuran
(en algún lugar...) en el site de Dominio Digital.

-----BEGIN PGP SIGNATURE-----
Version: PGP 8.1

iQCVAwUBSOxNwjj/MqMeN4stAQHo2QP+O2WYg9IFD0iXXY57L1qVw0fF22UY5Ugo
0I6meMkHcRK3rhVElIl/gQW7+vYIL4f4rWOyP83//z+H/WsUZGeHppRajEq3jtt3
vQd7Eh/yHlfY4TTzE+HvJSJ8StHmIrUVbquVD1EX1V/Xwk0f1vq1h2vZPPYy5mx/
q8qvtmf4+2M=
=IILc
-----END PGP SIGNATURE-----

---

### Post by leo_rockway on 2008-10-08
-----CRAZY THING TO FEEL LIKE A GURU. SURELY OTHERWISE NOBODY WOULD BELIEVE I AM WHO I SAY I AM-----

> **DanielSentinelli said:**
> 
* El que trabaja para Microsoft es Alejandro Ponike, el pelado. 


Yo sabía que me sonaba ese nombre...
[http://ubuntuforums.org/showthread.php?t=861211](http://ubuntuforums.org/showthread.php?t=861211)

Bueno, sólo quería comentar que laptop-mode, hasta donde sé, no viene activado por default, ergo eso de que Ubuntu te rompe los discos sigue siendo, en mi opinión, FUD.

Igual no tengo ni idea de quién es Daniel Sentinelli ni de que programa están hablando, jaja.

EDIT: ¡yo también me quiero hacer el loco! ¡Mirá mamá, tengo una firma loca en un foro de GNU/Linux para seres humanos!

-----BEGIN CRAZY MESSAGE SIGNATURE-----
 Version: 1337
 
0+1_1)2(3*5.8&13^21%34$55#89@144!233
 -----END CRAZY MESSAGE SIGNATURE-----

---

### Post by victor_nesta on 2008-10-08
Guau!! 
Me contesto, me explico y me bajo linea el mismísimo Daniel Sentinelli!!

Ahora enserio.
Daniel:
 copado que contestes y ¨des la cara¨ (entre comilla :) ), soy un amateur en informática y mas aun en Linux, ya que hace poco comencé con esto.

Estaría bueno que como hacen todos lo chicos de acá que saben mucho mucho (faktorqm,  pol666, guisheca, Mauro22, sajnox, Air23, Hei Ku etc) sigas aportando explicaciones y soluciones a los diferentes temas que se van dando, aprovechando todo tu conocimiento a un bien común. ¿no?
Queda la invitación abierta

Saludos

---

### Post by Air23 on 2008-10-08
> **victor_nesta said:**
> Estaría bueno que como hacen todos lo chicos de acá que saben mucho mucho (faktorqm,  pol666, guisheca, Mauro22, sajnox, Air23, Hei Ku etc) sigas aportando explicaciones y soluciones a los diferentes temas que se van dando, aprovechando todo tu conocimiento a un bien común. ¿no?
Queda la invitación abierta

Saludos

Bueno, gracias pero igual aclaro que yo no se nada, recien llevo 8 meses con ubuntu y no trabajo ni estudio nada relacionado a informatica. La verdad me dio cosa ver mi nombre (bah, mi nick) en una lista con gente del foro que la tiene muy clara.
Simplemente agarre el programa y suelo tener buena memoria.

---

### Post by leo_rockway on 2008-10-08
[https://lists.ubuntu.com/archives/ubuntu-ar/2007-October/003683.html](https://lists.ubuntu.com/archives/ubuntu-ar/2007-October/003683.html)

27 de octubre de 2007: old FUD is old...

---

### Post by faktorqm on 2008-10-08
> **DanielSentinelli said:**
> faktorqm:

* En mi opinión, un comentario como "man hdparm" no resulta útil en el
contexto de la "gran masa" de usuarios que esperamos alcanzar con
Ubuntu. Esa forma de responder es ideal en otro contexto como puede ser
el de usuarios de Gentoo, por ejemplo, donde es esperable (y casi hasta
exigible) otro tipo de predisposición técnica.

Más aun, y es parte de lo que comentaba en el programa, creo que el
usuario "masivo" de Ubuntu no debería estar usando hdparm para resolver
este tema porque ya existe una solución más global implementada en
"laptop-mode-tools", más algún par de detalles extras que están bien
documentados en [https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement) .

El problema es que todo esto sigue siendo demasiado confuso para el
usuario promedio. Creo que durante la instalación debería haber un
hermoso cartel que diga "¿Está instalando Ubuntu en una notebook? Si -
No" y a partir de ahí que se configuren los defaults de acuerdo a la
respuesta. Después, si el tipo sabe lo que hace, siempre puede tocar a
mano lo que quiera. Algunas de estas cosas ya van a estar más pulidas
en Intrepid, pero lamentablemente mientras que la gente que escribe al
dope es una multitud; los que laburan, escriben código, prueban betas y
reportan adecuadamente errores son una minoría en todos los proyectos.


Hola Daniel, estoy de acuerdo, pero tambien voto a favor de que aprendan un poco, o mucho, o lo que quieran, por que despues cuando las cosas se ponen feas, lo van a tener que leer igual para el proximo disco que compren...

> **DanielSentinelli said:**
> * Después de tu inteligentísimo comentario sobre lo ignorantes y
malísimos que somos, no me queda nada más para aportar. 

Respecto de esto me voy a retractar, SOLO por vos, realmente estuve mal al poner al poner que todos eran ignorantes, y no haberte sacado a vos de ese "grupo". Si leiste el thread, ya expuse mis razones por la chica, y por ponicke podes leer este thread y mi contestacion abajo. ([http://ubuntuforums.org/showthread.php?t=861211&page=5](http://ubuntuforums.org/showthread.php?t=861211&page=5)) Y si seguis pensando que realmente no es ignorante despues de escribir lo que escribio, bueno... alla vos. La parte de malisimos la voy a dejar, por que para mi, si me hablas de assembler y como programar boot loaders, sos un grosso, si hablas de como poner el cubo en ubuntu, sos malisimo, y en el programa se habla de eso, por eso la critica, y a su vez tambien entiendo que ese programa no esta orientado a usuarios "como nosotros", como aclaraste en otro punto, entonces tambien entendenos a nosotros por la critica.

> **DanielSentinelli said:**
> Supongo que así
esperás estimular a que muchos otros periodistas se animen a hablar de
Linux y Ubuntu por TV, ¿no? 


¿Para que digan cualquier cosa?, mejor que antes de decir algo mal no digan nada!! 

> **DanielSentinelli said:**
> Por favor, no dejes de mirarnos así el
rating no nos baja a la mitad, y mis hijas no se mueren de hambre
cuando dejen de pagarme millones por... ¡Ah, no!... Cierto que lo hago
de onda y nadie me da un centavo por esto. Ufff... por un momento me
había asustado...

No lo mire nunca, ni lo voy a mirar en un futuro, uno solo me alcanzo para saber que ese programa no apunta al estilo de usuario que soy.

> **DanielSentinelli said:**
> En serio, pensalo un poco. Un comentario así a mi me importa un comino,
y si a vos te hace sentir que quedás como un piola bárbaro, me alegro
mucho por vos. Ahora imaginate el efecto que va tener en un periodista
junior de un medio masivo al que le gustaría jugarse por hacer una nota
sobre "Instale Linux en su PC" que van a leer millones de personas,
pero que ante el riesgo de que una crítica como la tuya llegue a su
jefe de redacción, va a optar por ir a lo seguro y escribir sobre "Como
aprovechar las cáscaras de zanahoria para hacer sopa". Y nunca te vas a
enterar...

repito: ¿Para que digan cualquier cosa?, mejor que antes de decir algo mal no digan nada!! Soy capaz de ponerme una zunga de ubuntu y bailar en 9 de julio y corrientes el meneadito al grito de "te gusta como gira mi cubo papi!?!?!", con tal de hacerle propaganda a ubuntu, pero "mala" propaganda, que digan cosas que no son, que informen la mitad, eso si que no.

> **DanielSentinelli said:**
> * Si dije "megahertz" no te sorprendas. Da las gracias que no dije
"megaterios", "megalómanos" o "megáfonos". Ese programa lo grabamos a
las 10 de la mañana, y antes de que hubiera tomado café.


OK... Ahora voy a sacar un programa que se llame "grupo de trabajo analogico" jajajajaj (ya se que es malisimo... pero me causo gracia :lolflag:)

Y con lo de ir al programa te digo la estuve pensando... lo que (particularmente yo) no puedo cumplir es el tema de la continuidad... pero creo que tener un espacio en television para promover el software libre es un ofrecimiento que no desaprovecharia... dejamelo pensar un poquito mas y cualquier cosa lo vamos viendo. (y en realidad creo que no deberia ir yo, capaz Miguel tiene "mejor perfil" para decir las cosas que yo, cuando yo digo "man hdparm" el diria, "no, lo que el quiere decir es que hay que hacer click en aca y tildar esta opcion y listo")

Que bueno que contestaste y diste la cara :D Salu2 al pelado! AJAJJAJAJA

---

### Post by sajnox on 2008-10-08
Daniel, millon de gracias por tus comentarios.

Y desde ya quiero invitarte a la [release party]("http://ubuntuforums.org/showthread.php?t=940250") que hacemos el dia 30 de Octubre; la casa invita ;)

Algunos comentarios de que cosas que se dijeron en el thread:

1) Para todos: Todos concordamos que ubuntu-ar es una meritocracia, actuemos en consecuencia.
2) Pocas veces vi DD, no por que no me guste sino por que no esta en horarios muy friendly. He visto programas con cosas que me interesaron y otras que no tanto. No hay que ser tan nerds de pedir un programa informatico con los titulos en binario!!, hablan de temas de interes general y le tienen que sacar algo de plata a su laburo. Si bien no soy productor de programas de television algo me dice que hacer un programa semanal en cable debe requerir de un poco de esfuerzo.
3) Acaso nosotros mismos no hablamos de que una de las mejores herramientas de difusion de ubuntu es compiz? No juzguemos a los demas por hacer lo mismo.
4) En lo particular recuerdo claramente un programa de DD respecto al voto electronico, recuerdo la posicion y la explicacion de Daniel que fue muy clara y concreta y hasta se animo a utilizar la frase "compilar codigo" :o. Ademas consultaron a ambas partes sobre el tema (los fabricantes de las urnas electronicas y a un grupito bancado por Microsoft que se llama "Via Libre")
5) > "...hola, soy Troy McClure, y quizás me recuerden de películas como
'Las locuras de los hackers de vacaciones' o 'Los que usan Linux las
prefieren tetonas'..."
lol

6) Me gusta saber que puede haber un minimo espacio para ubuntu en el programa, y me encataria poder decir que ya estoy haciendo algo con eso...pero dame un poco de tiempo.

Daniel, en resumen muchas gracias por tu tiempo!! y te aseguro que si te queres quedar dando un par de vueltas por aca va a ser apreciado por muchos, incluso por faktorqm que mas alla de su intrepidez y velocidad para hablar es un buen pibe, y si se sienta un rato a hablar con vos, algo me dice que pone una foto tuya a los pies de su cama y te prende una vela todas las noches.

---

### Post by faktorqm on 2008-10-08
> **sajnox said:**
> Daniel, en resumen muchas gracias por tu tiempo!! y te aseguro que si te queres quedar dando un par de vueltas por aca va a ser apreciado por muchos, incluso por faktorqm que mas alla de su intrepidez y velocidad para hablar es un buen pibe, y si se sienta un rato a hablar con vos, algo me dice que pone una foto tuya a los pies de su cama y te prende una vela todas las noches.

Tanto no... pero si te venis a la release party nos tomamos unas cuantas birras, y vamos a estar mucho mas contentos de lo normal, con foto incluida jajajaja 
Igual tengo miedo que se desvirtue para atras y termines dando una clase de assembler... espero que no pase :P Salu2!

---

### Post by felipelerena on 2008-10-08
Gracias Chakal por opinar en el foro, Considero muy util tu intervencion y esta bueno que te hayas tomado el tiempo de responder a cada uno de los mensajes.

Yo no veo tu programa por varias razones.
1) al pelado ese no lo puedo ver
2) no veo la tele para que me hablen de windows vista... la veo para distenderme ( y la verdad que no me interesan tampoco los trucos de vista).
3) el horario no es muy bueno y no suelo andar por abajo del canal 25 (soy nerd, si veo que veo hay deportes vuelvo rapido para arriba)
4) la verdad que los temas que tratan nunca estan "al super dia" (De todos modos ya se que no pueden hacer slashdot TV :) )

ah, una cosa mas... no puedo comprobar tu firma
gpg: Firmado el mié 08 oct 2008 03:05:54 ART usando clave RSA ID 1E378B2D
gpg: Firma INCORRECTA de "Daniel Sentinelli <daniels@chacal.com.ar>"
pero lo mas probable es que publicarlo en el foro haya alterado el mensaje y la firma sea incorrecta por eso.

De nuevo muchas gracias por tomarte el tiempo de opinar en este foro
Lipe

---

### Post by pol666 on 2008-10-08
> 
Estaría bueno que como hacen todos lo chicos de acá que saben mucho mucho (faktorqm, pol666, guisheca, Mauro22, sajnox, Air23, Hei Ku etc



No, participo mucho del foro, pero se poco  y nada.
----------------------------------------------------



Daniel, Muchas gracias por registrarte, y tomarte el tiempo de desasnarnos, y desatar los malos entendidos.
 Sos una de las pocas personas que leí, que sabe muchisimo de informatica, y a su vez tiene un buen sentido del humor (no se por que, pero generalmente es incompatible),DD, lo habre visto 3 veces cuando estaba linkeado en Taringa! y por alguna casualidad sacaron el enlace, me olvide el nombre, y despues de un tiempo me acorde. No vi ni escuche lo que hablaron del Grub, del disco, o del mbr, lo ignoro, me llamo la atencion que justo hacia un tiempo habia perdido el disco y podia ser por ello, por cierto, me fije en el listado pero no encontre el modelo de mi disco, aunque tendria que releerlo.
 Respecto a la carcel, plena ignorancia, me habian comentado de algo por el estilo, y me quedo en la cabeza, es mas, no sabia exactamente quien eras. Nuevamente, Muchas gracias por contestar, y no dudes en volver a pasar por el foro.

---

### Post by Mauro22 on 2008-10-08
Que Groso!! :)


DD es entretenido y lo vi creo que un año seguido pero despues lo fueron cambiando de horario (o era yo :S ) y lo fui perdiendo....


Ahora que, el "Chakal", se haya tomado la molestia de registrarse y escribir un -semejante- post, realmente, me impresionó. Creo que el 99.9% de los miembros de aca, no hubieran pensado en que podria suceder. Bah, no se, esta bueno que alguien que sale en la TV conteste un post jejeje. Al fin y al cabo, el "chakal" es un luchador por el software libre y la filosofia de linux como la mayoria de nosotros; y con eso me alcanza :)...



Un Saludo!!

PS: Te va una medallita por el post

---

### Post by Hei Ku on 2008-10-08
Gracias por la respuesta.
> 
Hei Ku:

* La televisión es un medio masivo dirigido a "gente común" (como la
mamá de victor_nesta, por ejemplo). La información técnica
especializada podés encontrarla en algunos foros y sites temáticos. Si
esperás encontrar información técnica avanzada en un programa de TV
estás tan equivocado como si esperaras encontrar las zapatillas adentro
de la heladera (a no ser que tengas hábitos alimentarios muy
peculiares).


> 
Mi impresion, cuando lo vi hace unos años, fue que eran 3 paquetes alrededor de Daniel. No era un programa bueno tecnicamente sino apenas de divulgación para "gente común" en un canal de cable de Argentina. O sea, no le pidas demasiado.
Es como pedirle a Fabian Garcia que te tire la posta tecnica de algo (los que trabajan en sistemas sabrán de quién hablo). Hace muchos años, puede ser, pero hoy ya no se dedica a eso.


Me alegra que concordemos en que no es esperable informacion tecnica de un programa como DD, que fue lo que dije.

Ahora, que es eso de Ponicke? Es el pelado del programa? jua.
Avisale que vuelva a contestar porque dejo una thread inconclusa. ;)

---

### Post by faktorqm on 2008-10-08
> **Hei Ku said:**
> 
Ahora, que es eso de Ponicke? Es el pelado del programa? jua.
Avisale que vuelva a contestar porque dejo una thread inconclusa. ;)

Si esperás a que el pelado PUEDA contestar ese thread, estás tan equivocado como si esperaras encontrar las zapatillas adentro
de la heladera (a no ser que tengas hábitos alimentarios muy
peculiares) :lolflag:

---

### Post by crosssover on 2008-10-09
que groso el chakal, respondiendo y dando catedra.

 El programa dominio digital, esta bueno, que yo sepa, hoy en dia no hay otro programa que hable sobre tecnologia en la TV de hoy, los muchachos tienen merito por ir por la temporada 12 y todo a fuerza de pulmon si no me equivoco.

Como decian arriba, muchos no lo miran porque hablan cosas basicas, pero seria imposible que pasaran por la tele un programa de como porgramar un bootloader en assembler o compilar un kernel en vivo, no lo veria nadie, ni los mas freaks (me incluyo).
 
Yo tampoco, como muchos, me banco a Ponike ni a la mina, pero creo que cada uno del programa cumple un rol, la mina hace informes basicos, el pelado es el abanderado de bill gates, infaltable en todo programa, esta el pibe que conduce, y daniel que es el que tira la posta y refuta todo lo que dice Ponike :)

Si nunca vieron el programa, denle una oportunidad, hagan de cuenta que es un Nivel-x pero mas piola ñ__ñ
Antes que "Bolu-Hard" miro Almorzando con Mirtha

PD: a los de Dominio Digital, si se enteran los de la banda TOOL de que usan uno de sus temas como separador se van a meter en quilombos ñ__ñ

---

