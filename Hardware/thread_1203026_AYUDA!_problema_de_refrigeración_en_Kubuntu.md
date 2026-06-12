---
title: "AYUDA! problema de refrigeración en Kubuntu"
date: 2009-07-02
forum: Hardware
---

### Post by r@fitiiixxx on 2009-07-02
Hola a todos!,

en este momento tengo otro thread activo pero este tema no tiene nada que ver con Software, porque este se puede patear,

tengo un problema muy grave, hoy estaba jugando al urban terror 4.1 en mi Kubuntu JJ, estube jugando 2 hs y empecé a sentir una baja en FPS (frames per second) muy alta!, considerando que tengo una GeForce 8600 GT 512mb con los drivers actualizados privativos [ver. 180 recomendada] para Kubuntu, me pareció raro,
además del juego tenía en ejecución los efectos de escritorio KDE, el Amarok 2 reproduciendo musica y el Konqueror con 10 pestañas habiertas a la vez, entonces se me ocurrió tocar el CPU a ver que onda,
lo toqué serca de la placa de video, y cuando lo toqué ME QUEMÉ LA MANO!
traté de apagar todo lo rapido que pude y espero que la placa de video no se alla estropeado con la alta temperatura, jamas en Ubuntu con este juego y musica o en win me paso esto, lo mas raro es que también la fuente estaba ardiendo pero como a 90º masomenos!, había olor a plastico quemado
no quiero exagerar pero si la tocaba con el dedo me quedaba rojito, y el disipador del procesador doble también estaba que pelaba, la habrí toda y la dejé "enfriar" como 2 hs, Aclaro que la unica que ves que mi placa de video tomó algo de temperatura y no se compara con lo de hoy, fue bajo la exigencia del Engine Cry Engine 2 jugando al Crysis, el cual tiene mil veces mas graficos que el motor grafico del Quake III, quien mueve al Urban Terror 4.1.
porfavor nesesito ayuda o consejo! tengo miedo que se me queme la PC la proxima ves que me ponga a jugar!

nota: cuando inicié recién me apareció un mensaje de que los efectos de escritorio estaban desactivados! :S, apreté Ctrl + Alt + F12 para activar devuelta, y se reinició la pc y ahora si lo tengo activado...

---

### Post by staar on 2009-07-02
los fans (ventiladores) están funcionando correctamente? el gabinete está razonablemente limpio? en uso normal, levanta mucha temperatura?

saludos

PD: la combinación es Alt + Shift + F12

---

### Post by guillermolisi on 2009-07-02
Cuantos ventiladores y de que tamaño tiene el gabinete ?

La fuente estaba tan caliente como el resto de los componentes que tocaste ?

Tenes monitores de temperatura en el escritorio grafico (CPU, HD, MB, etc., etc.) ?

---

### Post by r@fitiiixxx on 2009-07-03
Primero, gracias por contestar, que con este problema tan grave la verdad no se que haría sin uds!

> **staar said:**
> los fans (ventiladores) están funcionando correctamente? el gabinete está razonablemente limpio? en uso normal, levanta mucha temperatura?

saludos

PD: la combinación es Alt + Shift + F12

si, claro que tonto, leí mal y ejecuté mal la combinación de teclas, igual después releí lo que posteaste en mi otro thread y me fije bien y ahí no tuve mas problemas en activar y desactivar efectos.

los coolers del disipador y del procesador y el minicooler de la placa de vid andan, así también como el fan de la fuente...

el gabinete... está razonablemente limpio, tiene poca pelusa, es mas, hoy que lo abrí le saqué bastante mugre de los ventiladores, pero así y todo el problema sigue...

no levanta temperaturas extrañas cuando no estoy jugando al juego este (llamese uso cotidiano), además en el juego noto que tengo lag, no una baja de fps lo cual me indica el indicador, pero si siento como si  estuviera descargando algo por torrent o algo así, probé de jugar sin efectos de escritorio y pasa lo mismo, ahora la pc me anda perfecto, en windows no tengo este problema, y en Ubuntu tampoco lo tenía.
> **guillermolisi said:**
> Cuantos ventiladores y de que tamaño tiene el gabinete ?

La fuente estaba tan caliente como el resto de los componentes que tocaste ?

Tenes monitores de temperatura en el escritorio grafico (CPU, HD, MB, etc., etc.) ?

tengo 1 cooler para el procesador, el ventilador de la fuente, y el cooler de la VGA, nada mas...

el gabinete es tamaño, un poco mas reducido que el estandard, pero la cantidad de espacio adentro que sobra es muy buena, además este problema es la primera ves que me pasa, y encima jugando un juego tan fácil de correr

mm los tamaños exactos no los se, pero tamaño standard el cooler del procesador (de por medio el disipador metálico), la placa de video es una XFX GeForce 8600 GT 512mb, quienes la conozcan sabrán que tiene un cooler de juguete casi, pero hasta ahora se ha bancado motores gráficos de ultima generación sin problemas. y sin recalentar demasiado

la fuente estaba tanto o mas caliente que el resto de los componentes, me arriesgo a decir que en una escala de mas caliente a menos,

Fuente > Placa de vid > disipador del procesador > mother

igual la direfencia entre la placa de vid, y el disipador no había mucha diferencia
--------------------------------
mi conclusión es que el S.O. en algún punto manda la orden de que giren los ventiladores, pero no que aumenten o no la velocidad con respecto a la aplicación que está corriendo, porque cuando se juega 1 video juego es ovio que necesita mas refrigeración.

ahora mismo está tibia la placa...

algún screenlet o como se llamen en KDE para poder medir la temperatura de la placa? porque la de los procesadores tengo, pero de la placa no tengo.

el sensor que tengo por ahora muestra estos datos:
Imsensors/k8temp-pci-00c3/temp3 temp3     - -    temp3 = 34ºC
Imsensors/k8temp-pci-00c3/temp1 temp1     - -    temp1 = 45ºC

mil gracias y un saludo ):P

r@fitiiixxx

---

### Post by guillermolisi on 2009-07-03
Para remover el polvo/hollin acumulado entre las aletas de los disipadores del procesador y de la fuente de alimentacion (fundamentales estos ultimos) no hay nada como aire comprimido. Soplar con la boca es como hacerle una caricia.

Fijate en el BIOS si soporta ajuste dinamico por temperatua para cambiar la vueltas del ventilador del procesador y el gabinete/chassis. Es buen practica usar esto ya que en bajas temperaturas disminuye el consumo de energia, preserva la vida util de los ventiladores y disminuye el ruido. Y cuando exigis la maquina literalmente llegan a levantar vuelo (3000 o mas rpm)

El volumen del gabinete no cuenta tanto como la cantidad de aire que moves internamente y el sentido en que fluye. He visto maquinas donde los ventiladores ingresaban aire y solo el de la fuente extraia cuando lo correcto es que todos extraigan.

Ademas, que no levante temperatura en Windows no significa que este todo bien. Solamente usar otros drivers para video, motores graficos diferentes (con solo portarlos a otra platadorma ya es distinto), etc. hacen que el hardware se comporte diferente.

Si la fuente esta muy justa en potencia y, encima, mal ventilada, tambien puede hacer que el resto de la maquina recaliente porque a medida que la usas las tensiones y niveles de corriente que entrega se van de rango (se "sale de punto") y afecta al resto del sistema. Por eso el componente mas importante de un equipo es la fuente de alimentacion.

---

### Post by sp33d3rs on 2009-07-03
> **guillermolisi said:**
> Para remover el polvo/hollin acumulado entre las aletas de los disipadores del procesador y de la fuente de alimentacion (fundamentales estos ultimos) no hay nada como aire comprimido. Soplar con la boca es como hacerle una caricia.

Fijate en el BIOS si soporta ajuste dinamico por temperatua para cambiar la vueltas del ventilador del procesador y el gabinete/chassis. Es buen practica usar esto ya que en bajas temperaturas disminuye el consumo de energia, preserva la vida util de los ventiladores y disminuye el ruido. Y cuando exigis la maquina literalmente llegan a levantar vuelo (3000 o mas rpm)

El volumen del gabinete no cuenta tanto como la cantidad de aire que moves internamente y el sentido en que fluye. He visto maquinas donde los ventiladores ingresaban aire y solo el de la fuente extraia cuando lo correcto es que todos extraigan.

Ademas, que no levante temperatura en Windows no significa que este todo bien. Solamente usar otros drivers para video, motores graficos diferentes (con solo portarlos a otra platadorma ya es distinto), etc. hacen que el hardware se comporte diferente.

Si la fuente esta muy justa en potencia y, encima, mal ventilada, tambien puede hacer que el resto de la maquina recaliente porque a medida que la usas las tensiones y niveles de corriente que entrega se van de rango (se "sale de punto") y afecta al resto del sistema. Por eso el componente mas importante de un equipo es la fuente de alimentacion.
Se, totalmente de acuerdo, y me inclino mas por la fuente. Por otro lado, sin ser mala onda, se habra jodido la placa de video?

---

### Post by staar on 2009-07-03
> ..cuando lo correcto es que todos extraigan. según las especificaciones ATX, lo correcto es que los fans delanteros (generalmente ubicados abajo) hagan ingresar aire, y los traseros (a veces solo el de la fuente, pero en máquinas más potentes se debe usar uno en el gabo) lo saquen, así se forma una corriente de aire, que es lo mejor para refrigerar (con aire obvio, sin hablar de agua o nitrógeno :-D)

con los componentes actuales, es recomendable usar algún fan lateral, a la altura del micro o de la placa de video...

en este caso, no se, puede ser la fuente, pero no descarto que algo (soft o configuración) este haciendo andar mal los coolers...

saludos

---

### Post by r@fitiiixxx on 2009-07-03
pero, a ver;

se están saltando la parte mas importante, en Ubuntu con GNOME esto no me pasó, y eso fue hace 4 días, mientras en windows con exigencias mucho mayores, no pasó nada en este mismo día, osea, probado que mi pc anda en las 2 plataformas, LINUX y WINDOW$ pero la verdad es que si en ubuntu o en cualquier distro se la banca no importa cual, y me muestra cuanto y que también sigue aguantando en windows y cosas muchisimo mas graves que el ioquake3, que con GNOME lo tenía corriendo 5 hs seguidas y sin problemas de temp... 

Estoy que me juego la cabeza que esto es problema de KDE
tal vez cambiarme a KDE fue una equivocación, lo digo solo por este problema ya que por todo lo demas me encanta, y eso que lo uso hace re poco, tal vez me convenga volver a Ubuntu, si uds dicen que no se puede resolver a menos que le agregue un... sistema de refrigeración nuevo :(
yo no tengo plata, pero en ubuntu me andaba bien
---------------------------------------
ya le saqué todo el polvo soplándola y con una carilina le saqué altas mugres,

como me fijo lo del ajuste dinámico? porque una vez me metí en la BIOS  y jodí la conexión al monitor y tuve que mandarla a arreglar. osea no piso en falso ni ahí.

mi gabinete tiene mas salidas y entradas que un pelado jaja, el calor fluye por todos lados, pero no tiene un ventilador solo para disipar, en conjunto todos tiran aire caliente para arriba, y la chapa de arriba es la que tiene muchos agujeros, también hay agujeros atrás, porque mi gabinete va acostado, o parado como mas te guste jeje.

no solo está todo bien en windows, también está todo bien en Ubuntu :S

y por ultimo, lo de la fuente no entendí mucho, yo igual tengo un estabilizador de corriente, y el ventilador de la fuente sí anda,

y mi placa de video no se jodió nada porque todavía me la reconoce, todavía me anda todo bien

EDIT: no se si tendrá que ver en algo, pero desde que instalé Kubuntu tube un problema con 6 actualizaciones que nunca pude actualizar, pongo actualizar y me salta un error, las actualizaciones son las siguientes:

> **[COLOR="RED"]X[/COLOR] 6 Actualizaciones bloqueadas:**
linux-headers-generic 2.6.28.11.15 (i386)
amarok - 2.2.0.2 mysql 5.1.30-0buntu3 (i386)
linux-restricted-modules-generic - 2.6.28.11.15 (i386)
linux-generic - v2.6.28.11.15 (i386)
linux-image-generic - 2.6.28.11.15 (i386)
amarok-common - 2.2.0.2 mysql 5.1.30-0buntu3 (all)

y cuando intento actualizar la lista me sale este mensaje > Refreshing cache failed: W:Failed to fetch cdrom://Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs , W:Failed to fetch cdrom://Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs , E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by guillermolisi on 2009-07-03
> **staar said:**
> según las especificaciones ATX, lo correcto es que los fans delanteros (generalmente ubicados abajo) hagan ingresar aire, y los traseros (a veces solo el de la fuente, pero en máquinas más potentes se debe usar uno en el gabo) lo saquen, así se forma una corriente de aire, que es lo mejor para refrigerar (con aire obvio, sin hablar de agua o nitrógeno :-D)

con los componentes actuales, es recomendable usar algún fan lateral, a la altura del micro o de la placa de video...

en este caso, no se, puede ser la fuente, pero no descarto que algo (soft o configuración) este haciendo andar mal los coolers...

saludos
Correcto, si hay ventiladores delanteros estos son lo unicos que deben ingresar aire dentro del gabinete.

Te olvidaste del aceite de oliva y aceite mineral:)

Aceite mineral [http://www.engadget.com/2007/05/12/puget-custom-computers-mineral-oil-cooled-pc/](http://www.engadget.com/2007/05/12/puget-custom-computers-mineral-oil-cooled-pc/)

Aceite de cocina (oliva u otro vegetal) [http://www.markusleonhardt.de/en/oelbilder.html](http://www.markusleonhardt.de/en/oelbilder.html)

---

### Post by Mauro22 on 2009-07-03
Si la fuente calienta son dos estas cosas nomas:

* La fuente te queda "chica" y re calienta, calentando el aire en el interior del gabinete, dando la falsa sensacion de que lo demas esta "que arde"

* Tierra o ventiladores con rulemanes gastados/trabados que no brindan el 100% del aire fresco.

* Mal posicionamiento del gabinete con respecto a una corriente fresca de aire, lo que obtaculiza el refresco de los componentes...



PD: Si el micro se recalienta, se apaga solo. Si la placa de video se recalienta, se reincia la pc. Esos dos no son!

---

### Post by r@fitiiixxx on 2009-07-03
> **Mauro22 said:**
> Si la fuente calienta son dos estas cosas nomas:

* La fuente te queda "chica" y re calienta, calentando el aire en el interior del gabinete, dando la falsa sensacion de que lo demas esta "que arde"

* Tierra o ventiladores con rulemanes gastados/trabados que no brindan el 100% del aire fresco.

* Mal posicionamiento del gabinete con respecto a una corriente fresca de aire, lo que obtaculiza el refresco de los componentes...



PD: Si el micro se recalienta, se apaga solo. Si la placa de video se recalienta, se reincia la pc. Esos dos no son!

a tu posdata primero, y si tal vez yo le mandé apagar antes de que llegue al punto critico?
 además si es la fuente como decís vos, no sería correcto que también recaliente fuera del juego? o sigue cumpliendo que puede calentar mas cuando solo estoy jugando?, ahora en este momento la temperatura de los micros, y creo que son los micro porq no entiendo que carancho marca el desklet este;
temp1 47ºC
temp2 38ºC
supongo que son los procesadores, ahora en mi pieza hace mucho frio,

otra cosa, es que no me leyeron de que en Ubuntu con GNOME esto no me pasó nunca y ayer mismo limpié toda la CPU por dentro? realmente creen que sea un problema de refrigeración?

justo ahora estoy descargando un archivo, cuando lo termine me voy a windows a jugar al Far Cry 2 como 5 hs para ver como trata la temp, 
otra cosa,
por mas que el consumo del motor ioquake3 sea diferente en linux que en windows,
la tecnología de renderizado del motor del far cry 2 es tan superior que aunque en linux el urban terror tuviera un desempeño deficiente no se compararía con el esfuerzo que tiene que hacer mi placa para cargar mapas continentales como los del far cry 2.

---

### Post by guillermolisi on 2009-07-03
Ok. Supongamos que no es problema de hardware, que sea de software.

Cuando empieces a jugar bajo Linux, particularmente con Kubuntu, abri una consola/terminal y pone top o htop.

Fijate cual es el programa que se lleva todo el uso de CPU a lo largo del tiempo y ahi tendrias una punta como para empezar a ver de que se trata.

---

### Post by staar on 2009-07-03
> **guillermolisi said:**
> Correcto, si hay ventiladores delanteros estos son lo unicos que deben ingresar aire dentro del gabinete.

Te olvidaste del aceite de oliva y aceite mineral:)

Aceite mineral [http://www.engadget.com/2007/05/12/puget-custom-computers-mineral-oil-cooled-pc/](http://www.engadget.com/2007/05/12/puget-custom-computers-mineral-oil-cooled-pc/)

Aceite de cocina (oliva u otro vegetal) [http://www.markusleonhardt.de/en/oelbilder.html](http://www.markusleonhardt.de/en/oelbilder.html)

la del aceite mineral la conocía (lo malo que tiene es que hay que olvidarse de sacar o cambiar un componente, porque el aceite se mete en las ranuras y fuiste), pero la otra no, le ponés un prescott y hacés papas fritas :lolflag:

r@fitiiixxx, se, es raro que solo te pase en kubuntu...
una cosa, con otro juego masomenos potente (onda sauerbrauten) en el kubuntu te pasa lo mismo? o solo con el urban terror?

saludos

---

### Post by r@fitiiixxx on 2009-07-03
> **guillermolisi said:**
> Ok. Supongamos que no es problema de hardware, que sea de software.

Cuando empieces a jugar bajo Linux, particularmente con Kubuntu, abri una consola/terminal y pone top o htop.

Fijate cual es el programa que se lleva todo el uso de CPU a lo largo del tiempo y ahi tendrias una punta como para empezar a ver de que se trata.

Gracias, voy a probar eso, aunque no estoy seguro de como visualizar la terminal "Konsole" con el comando "top" mientras estoy jugando, voy a probar jugar en modo ventana con resolución mas baja, claro que eso puede que afecte los resultados pero voy a probar...

> **staar said:**
> la del aceite mineral la conocía (lo malo que tiene es que hay que olvidarse de sacar o cambiar un componente, porque el aceite se mete en las ranuras y fuiste), pero la otra no, le ponés un prescott y hacés papas fritas :lolflag:

r@fitiiixxx, se, es raro que solo te pase en kubuntu...
una cosa, con otro juego masomenos potente (onda sauerbrauten) en el kubuntu te pasa lo mismo? o solo con el urban terror?

saludos

rarisimo jaja, la verdad no se que pasa, vos siempre me decís esas cosas que son obias y que no se me ocurren jaja, ahora después de probar viendo la consola me pongo a bajar el Cube 2 o el Nexuiz que también le saca jugo y comento...

EDIT: los resultados de la prueba con la terminal Konsole y cmd "top" mientras juego al UT_4.1 me arrojan lo siguiente:
> 
PID: 26093
user: nicolas
PR: 20
NI: 0
VIRT: 366m
RES: 106m
SHR:10m
S: R
%CPU: **100** (OMFG!!!)
%MEM: 5.3
TIME+: 3:3x:xx (las "x" son porque cambiaba constantemente, creo que era el tiempo en ejecución del proceso, no?)
COMMAND: iourbanTerror.i

EDIT.2: Estoy descargando el Sauerbraten o como se llame, lo encontré en los repositorios afortunadamente. luego lo pruebo y les comento...

EDIT.3-Add: probé el Sauerbraten y tiene el mismo efecto, solo que no noto una caída ni en fps ni en lag ni nada parecido, ahora la temperatura de la placa entra a levantar... pff
me falta probar en windows ahora me voy ahí a jugar a algo a ver si pasa lo mismo...

---

### Post by r@fitiiixxx on 2009-07-04
OMFG! abrí el gabinete andando la pc, y ME DI CUENTA QUE EL COOLER DE LA FUENTE NO ESTÁ GIRANDO!!!!!!!!
perdon muchachos :oops: me siento taaan tonto. 
mi querido kubuntu!, yo ya te echaba la culpa! :oops:
lo que pasa es que si miro al ventilador de la fuente desde afuera con la chapa puesta parece que girara porque queda muy tapado por las rejitas, y no se, generan el efecto de que girara, encima ponía la oreja pero seguía sonando, con todo el ruido de los coolers del disipador y de la VGA me habré confundido, no puedo creer que me halla pasado esto,

me fijé después de darme cuenta de que en windows también recalentaba, lo raro es que ayer (en realidad hace 36 hs) andaba bien en windows, justo antes de instalar Kubuntu, entonces se me ocurrió abrirla andando, lo cual me tomó un gran trabajo, ya que con el tema de los cables y el espació, (gabinete horizontal con monitor arriba y cables cortos y todo eso, es un problema grave,

igual concuerda con la instalación de Kubuntu, puede ser que al instalar Kubuntu algo en la BIOS se me halla descalibrado?

mil disculpas, no fue mi intención molestar, espero que no se enojen con migo jeje, pasa que hacer lo que hice ahora para fijarme con la pc abierta requería correr muebles! lo hice ahora porque si no después tengo problemas con mi vieja, (¡tuve que correr una estantería!)

si me pueden orientar para revisar la BIOS sería genial,

> *...y el ventilador de la fuente sí anda...*
no tengo perdón de dios,
 mañana mismo le hago un agujero a esa reja de $%&!@ así puedo ver mejor (na mentira), menos mal que no quemé la pc, o la casa o lo que sea :oops:

bueno ahora apago y mañana me voy al Cyber a revisar el thread porque la pc si no se me va a quemar...
otra ves perdón a todos, me gustaría decir que a cualquiera le puede pasar, pero no jaja, solo a mi,
igual si saben de alguna solución para reparar el ventilador o tal ves algún toque en la BIOS porque ahora no tengo plata para otra fuente y esta solo tiene 1 año maso-menos (creo que es poco, no?)

finalmente he aprendido algo, nunca tengo que estar 100% seguro de algo, mejor chequear y doble-chequear todo.

un Saludo,

r@fitiiixxx

---

### Post by totolinux on 2009-07-04
hola si te animas mete mano a la fuente, desarmala, limpia los componentes con un soplete y fijate si el ventilador esta con tierra, si gira.
podes limpiarlo y aceitarlo con aceite de maquina justo donde tiene una calco de la marca, sacala y debajo esta el eje. El recambio es simple y cuesta unos 15$  20$.  saludos

---

### Post by staar on 2009-07-04
exactamente, limpiá muy bien la fuente, aceitala y después fijate si funciona el cooler, si no funciona, cambialo...

por lo menos en la mayoría de las pc, el fan de la fuente no se puede controlar desde la BIOS...

saludos

---

### Post by Hei Ku on 2009-07-04
Cambiala, y asegurate que sea una fuente buena, no de esas que te prometen 450W por $100.

---

### Post by guillermolisi on 2009-07-04
> **Hei Ku said:**
> Cambiala, y asegurate que sea una fuente buena, no de esas que te prometen 450W por $100.
Voy a decir algo totalmente empirico: Las mejores fuentes siempre pero siempre han sido mas pesadas que las equivalentes pero berretas.
Tambien, como dice Hei Ku, si por 500W te piden $ 600.- y por otra marca te piden $ 100.- por la misma potencia, hay algo que no funciona, no son lo mismo, estas hablando de dos cosas totalmente diferentes.

[comentario OT]
Si seguimos asi varios vamos a engordar varios kilos comiendo panchos y coca-cola gratis
[/comentario OT]

---

### Post by Mauro22 on 2009-07-04
> **guillermolisi said:**
> 
[comentario OT]
Si seguimos asi varios vamos a engordar varios kilos comiendo panchos y coca-cola gratis
[/comentario OT]


Que rico jejee


Estarìa bueno que Hei Ku traiga otro troll asi nos sacamos la ganas de postear OT's.... y de paso sumo porotos a mi canasta que estoy cerca de los 1k


):P

---

### Post by r@fitiiixxx on 2009-07-04
Holas, a todos! 

A que no saben de donde escribo esto, desde el célu con el Ópera Mini 4.2!! Es muy buen navegador!

Voy a contactarme con un amigo que arregla pc's así capaz que logro resolver el asunto con sólo arreglar el ventilador, sí no se puede voy a tener que juntar plata de no se donde...

En fin, voy a probar de todos los consejos, y desde ya muchas gracias a todos,

Salu2,):P

r@fitiiixxx

---

### Post by guillermolisi on 2009-07-04
Que te ponga un ventilador montado en rulemanes. Es mas caro que los comunes pero te olvidas el asunto practicamente de por vida. Ademas son los que mas aire mueven. Nada de Noganet.

---

