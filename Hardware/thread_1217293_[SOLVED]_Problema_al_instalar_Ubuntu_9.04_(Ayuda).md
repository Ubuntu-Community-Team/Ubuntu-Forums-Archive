---
title: "[SOLVED] Problema al instalar Ubuntu 9.04 (Ayuda)"
date: 2009-07-19
forum: Hardware
---

### Post by bloodytanga on 2009-07-19
Hola, yo soy un usuario de Windows XP y empece a incursionar en el tema del software libre hace unas semanas. Finalmente habia decidido instalar ubuntu como OS pero tuve un problema.

Descargue la imagen de disco de la pagina oficial de Ubuntu y la queme en un DVD. Cuando traraba de arrancar el disco llegaba al primer menu donde elegis el idioma y luego si queres iniciar sin alterar tu OS o si lo queres instalar etc, Pulsase la opcion q pulsase ya sea probar, instalar o incluso chekear el disco me saltaban dos errores:

[12.192007] ate3 failed (errno = -16)
[22.204007] ate3 failed (errno = -16)

Luego de mostrarme esos errores aparecia una imagegn de ubuntu cargando una barra y luego me aparecia una pantalla negra con los errores previamente escritos y abajo decia:

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2 Ubuntu7) built-in shell (ash)

Y abajo me dice que escriba "help" para recibir una serie de comandos. Pero nunca puedo pasar de esa parte (que supuestamente no tendria que pasar)

Al ver esto decidi descargar nuevamente la imagen por si la habia bajado con errores y  la volvi a grabar en un DVD, pasaba lo mismo. Por ultimo pense que quizás tenia que estar grabado si o si en un CD por lo q lo grabe en un CD pero siempre me pasa lo mismo, a veces cambian los numeros de error entre [] pero siempre empiezan con 12. y 22.

Me seria de muchisima ayuda si alguien pudiese ayudarme a solucionar este problema ya que quiero instalar ubuntu.

Gracias por su atencion y espero su ayuda.

---

### Post by juancarlospaco on 2009-07-19
La ISO esta jodida, proba bajarlo de nuevo y quemalo de nuevo, 
*cosa e'mandinga.*

---

### Post by staar on 2009-07-19
bajala por torrent, ganas velocidad y te aseguras que se baje bien (porque se comprueba lo descargado constantemente)

además grabala a la menor velocidad posible...

saludos

---

### Post by bloodytanga on 2009-07-19
bueno gracias por los consejos, ahora me estoy bajando de torrent y grabo de nuevo a poca velocidad el DVD. Despues aviso si se soluciono el problema o no xq me lo volvi a bajar de la pagina oficial de ubuntu y me paso lo mismo.

---

### Post by bloodytanga on 2009-07-19
Acabo de grabar la imagen en un DVD a la menor velocidad q pude (1x) y sin embargo me paso exactamente lo mismo. la imagen me la baje con el bit torrent y sin embargo me paso lo mismo, ya es el 5to intento asi q dudo q 5 veces se me halla bajado mal la imagen encima una por torrent. Alguien tiene algun otro consejo? porque ya estoy cansado de desperdiciar discos

---

### Post by staar on 2009-07-19
bueno, descartada la imagen...

que motherboard tenés? los discos son SATA? la lectora? en que modo están en la BIOS?

saludos

---

### Post by bloodytanga on 2009-07-19
Nombre de la Placa Base    Asus K8V-MX
Mi disco rigido es SATA
y no entiendo a que te referis con en que modo estan en la bios

---

### Post by guillermolisi on 2009-07-19
> **bloodytanga said:**
> Nombre de la Placa Base    Asus K8V-MX
Mi disco rigido es SATA
y no entiendo a que te referis con en que modo estan en la bios
Me parece que se refiere a esto:
```
[IMG]http://es.asus.com/999/images/products/754/01.gif[/IMG] Serial ATA RAID 
Serial ATA es la especificación ATA de próxima generación que proporciona rendimiento escalar. La transferencia de datos es de 150 MB/s, muy superior al actual Parallel ATA y ofrece un 100% de compatibilidad con todo el software involucrado. El Southbridge ULI® M1573 soporta configuraciones RAID 0, 1, 0+1 y JBOD para los conectores SATA.
```EL BIOS te da varias alternativas de configuracion para tu disco, ademas de la de RAID que para tu caso y con un solo disco no es aplicable.

El chipset de esa maquina es VIA K8M800 + VT8237R (tomado de la [pagina de Asustek]("http://es.asus.com/products.aspx?l1=3&l2=14&l3=225&model=754&modelmenu=1")) con lo cual su placa de video es todo un problema salvo que se use con driver Vesa (los drivers para video VIA no funcionan).

---

### Post by bloodytanga on 2009-07-19
y todo eso q significa exactamente?

---

### Post by guillermolisi on 2009-07-19
> **bloodytanga said:**
> y todo eso q significa exactamente?
Como te sintetice antes, hay posibilidad de que por cuestiones de implementacion de algunas distribuciones, la maquina se inicie sin problemas con algunas y con otras no.

Que significa cuestiones de implementacion ? Que algunas distribuciones asumen o esperan que tu hardware sea de cierta tecnologia, consideran algunas alternativas posibles respecto a como esta configurado (aqui podria jugar el tema de que el BIOS de tu maquina no este configurado para un disco SATA simple sino para un arreglo de discos u otra cosa distinta que algunas distribuciones no esperan encontrar habiendo detectado que solamente tenes un disco fisico) y otras no o no lo hacen de la misma forma.

Si fuera que ningun sistema operativo hace iniciar tu maquina decididamente hay un problema grave, un disco roto, un cable suelto, etc., es decir una causa bien explicita.

Pero como algunos funcionan y otros no, hay que indagar en profundidad hasta encontrar la causa y esta indagacion es netamente tecnica y requiere de algunos conocimientos y la logica voluntad de por lo menos enterarse de algunos de ellos.

---

### Post by bloodytanga on 2009-07-19
claro, etonces no voy a poder instalar ubunto a exepcion que me lea toda la fuente de arranque buscando el componente que analiza mi BIOS? aparte de disco rigido tengo grabadora de dvd y floppy disck (q nunca me anduvo), eso cuenta como discos fisicos?

---

### Post by bloodytanga on 2009-07-19
Queria decir que aparte de la tarjeta de mi placa tengo una nVIDIA GeForce FX 5500

---

### Post by pablo.s on 2009-07-19
Me parece que este
problema se soluciona
poniendo el modo de
disco de LBA a AUTO
en la BIOS y listo...

---

### Post by bloodytanga on 2009-07-19
ahora lo pruebo

---

### Post by bloodytanga on 2009-07-19
trate de probbarlo, pero ya estaba en auto

---

### Post by bloodytanga on 2009-07-19
en mi casa tengo otras 2 computadoras en las cuales probe el disco y me andaban perfectamente asi que tiene que ser mi computadora la que no tolera el ubuntu, es eso posible? hay manera de solucionarlo?

---

### Post by guillermolisi on 2009-07-21
Si, es posible que en algunas maquinas te encuentres con situaciones que en otras no suceden, aunque sean iguales las maquinas.

Por que ? Porque pueden estar configuradas de distinta forma, particularmente en su BIOS y hasta una pequeña variacion de version de este ultimo puede hacer que no se comporten iguales.

Probaste modificando esa opcion de Auto a Normal y/o Large (no se si tiene estas alternativas, pero para probar si se inicia con el LiveCD no se pierde nada mas que un rato).

---

### Post by bloodytanga on 2009-07-21
Las unicas opciones que m da es SATA auto o apagado, pero son las unicas dos opciones que me aparecen. Ahora que lo pienso puede q mi disco no soporte SATA. Eso es un problema?

---

### Post by bloodytanga on 2009-07-21
Me confundí, el LBA digo lo que solo me da las opciones Auto o apagado.

---

### Post by guillermolisi on 2009-07-21
En la foto de la placa en el site de Asustek pareceria que ademas de dos conectores SATA tiene dos conectores PATA (los tradicionales).

En base a esto y para no seguir "adivinando", tenes que confirmar de que tecnologia es el disco (ideal si pasas marca y modelo) y ver en el BIOS como esta configurado para saber si esta correcto y/o hay alternativas que permitan adecuar la configuracion para que te funcione con cualquier sistema operativo, Ubuntu inclusive.

Mientras no se cuente con estos datos no le veo sentido a seguir tirando posibilidades a tientas.

---

### Post by bloodytanga on 2009-07-21
De qué placa estamos hablando exactamente? Porque yame perdí.

---

### Post by bloodytanga on 2009-07-21
Mi mother es  Asus K8V-MX

---

### Post by guillermolisi on 2009-07-21
Si, de esa, de la unica que se esta hablando en este thread.

---

### Post by bloodytanga on 2009-07-21
Esa es la marca y modelo. Asus K8V-MX es X series.

---

### Post by guillermolisi on 2009-07-22
Dije
> En base a esto y para no seguir "adivinando", tenes que confirmar de que tecnologia es el disco (ideal si pasas marca y modelo) y ver en el BIOS como esta configurado para saber si esta correcto y/o hay alternativas que permitan adecuar la configuracion para que te funcione con cualquier sistema operativo, Ubuntu inclusive.

No estas leyendo, solo miras. Asi no vamos a poder ayudarte.

---

### Post by bloodytanga on 2009-07-22
Perdón, mi disco es un HDS72808PLAT20

---

### Post by guillermolisi on 2009-07-22
Googleando un poquito encontre que ese disco es
> This is a Hitachi Deskstar 82.3GB **[COLOR="Red"]IDE[/COLOR]** 7200RPM Hard Drive, Model: HDS728080PLAT20

Asi que hay que ver como esta configurado en el BIOS y que alternativas ofrece pero en la seccion que habla sobre IDE disks, no SATA disks.

---

### Post by bloodytanga on 2009-07-22
Ok. Y dónde está esa sección?

---

### Post by bloodytanga on 2009-07-22
Bueno, acá dejo la configuración de mi disco en la BIOS. Lo que esta después de los dos puntos es la opción que está seleccionada y lo que esta entre paréntesis las opciones que tengo que no estan seleccionadas.

Type: Auto (Not Installed, CDRom, ARMD)
LBA/Large Mode: Auto (Disabled)
Black (Multi-Sector Transfer) M: Auto (Disabled)
Pio Mode: Auto (0,1,2,3,4)
DMA Mode: Auto (SWDMA0, SWDMA1, SWDMA2, MWDMA0, MWDMA1, MWDMA2, UDMA0, UDMA1, UDMA2)
Smart Monitoring: Auto (Enabled, Disabled)
32 Bit Transfer: Disabled (Enabled)
Acoustics: Maximum Performance (Medium, Silent)

Bueno esas son todas las configuraciones que hay en la BIOS de mi disco rígido.

---

### Post by jules_cesar_44 on 2009-07-22
I thought it was an english site.... Cannot understand my friend, so I do not benefit from the discussion.

Moi aussi je peux parler dans ma langue maternelle, mais beaucoup moins de monde va comprendre : est-ce bien la meilleure façon de propager et échanger nos connaissances ?????

---

### Post by bloodytanga on 2009-07-22
I can speak in english et je comprende un peux de français.

---

### Post by staar on 2009-07-22
this is the Argentina LoCo Team subforum, we speak spanish here...

c'est le Argentina LoCo Team subforum, nous parlons espagnol ici...

;-)

---

### Post by bloodytanga on 2009-07-22
Ok. Yo solo decía que si me podía ayudar por mas que fuese en ingles o francés iba a poder entender.

---

### Post by guillermolisi on 2009-07-22
> **bloodytanga said:**
> Bueno, acá dejo la configuración de mi disco en la BIOS. Lo que esta después de los dos puntos es la opción que está seleccionada y lo que esta entre paréntesis las opciones que tengo que no estan seleccionadas.

Type: Auto (Not Installed, CDRom, ARMD)
LBA/Large Mode: Auto (Disabled)
Black (Multi-Sector Transfer) M: Auto (Disabled)
Pio Mode: Auto (0,1,2,3,4)
DMA Mode: Auto (SWDMA0, SWDMA1, SWDMA2, MWDMA0, MWDMA1, MWDMA2, UDMA0, UDMA1, UDMA2)
Smart Monitoring: Auto (Enabled, Disabled)
32 Bit Transfer: Disabled (Enabled)
Acoustics: Maximum Performance (Medium, Silent)

Bueno esas son todas las configuraciones que hay en la BIOS de mi disco rígido.
Donde dice:

LBA/Large Mode, selecciona Auto (Enabled)
Black (Multi-Sector Transfer) M: Auto (Enabled)
Smart Monitoring: Auto (Enabled)
32 Bit Transfer: Enabled (Disabled)


Edit: Si lo que esta entre parentesis son las demas opciones del menu para cada funcion, entonces mi sugerencia es solo modificar las siguientes:

 Smart Monitoring: Enabled
32 Bit Transfer: Enabled


Esto considerando que la autodeteccion funcione correctamente (en los casos que se deja Auto).

Proba y comenta como resulto.

---

### Post by bloodytanga on 2009-07-22
Pasó lo mismo. Me aparecieron los mismos dos errores.

---

### Post by guillermolisi on 2009-07-22
Proba con 

LBA/Large Mode: Enabled

Otra cosa que estaba pensando ... el disco esta como master o como slave ?
Deberia estar como master si no tenes otro disco.

Eso se configura en el disco mismo, con un jumper/puente entre el conector de alimentacion y el de datos que tiene el disco.

---

### Post by bloodytanga on 2009-07-22
El disco está como master. Como Slave tengo la grabadora de DVD. El LBA no me da la opción de Enabled, sólo Auto o Disabled.

---

### Post by guillermolisi on 2009-07-22
> **bloodytanga said:**
> El disco está como master. Como Slave tengo la grabadora de DVD. El LBA no me da la opción de Enabled, sólo Auto o Disabled.
Proba con Disabled.

Si con eso no sale funcionando, entonces solo me queda decir que se me quemaron todos los papeles.

---

### Post by staar on 2009-07-23
se me ocurre que, siendo ambos, la grabadora y el disco, ide, sea la grabadora la que esté dando problemas (más que nada porque si fuera el disco, teóricamente el livecd tendría que seguir booteando) tenés la posibilidad de probar con otra lectora de dvd en la misma pc? que lectora es?

probá seteando los jumpers de la grabadora de DVD y del disco como 'cable select' (y obviamente, colocando correctamente el cable ide, la ficha que está más lejos de la que se conecta a la mother es la slave, la otra es la master)

ah, y si eso no te funciona, al iniciar el livecd, apretá F6 y agregá el parámetro debug a la línea de booteo (simplemente escribí debug), por lo menos así vamos a tener más datos, y no vamos a seguir andando a tientas, con un error tan vago y amplio...

saludos

---

### Post by bloodytanga on 2009-07-23
Con otra lectora no puedo probar. Lo que me dijo Guillermo no me funcionó. Después me pongo a ver lo que me dijiste vos staar. Pero no tengo mucha idea de como hacerlo así que me va a llevar un tiempo. uando lo haga posteo dando los resultados.

---

### Post by bloodytanga on 2009-07-23
Perdón me olvidé. La grabadora es HL-DT-ST DVDRAM GSA-4167B.

---

### Post by bloodytanga on 2009-07-23
Cuando pongo debug me aparece una pantalla llena de cosas así que no sabría que reportar.
Lo de los jumpers todavía no lo probé.

---

### Post by bloodytanga on 2009-07-23
Disculpen mi ignorancia pero recién abrí mi computadora y no encontré por ningún lado los jumpers del rígido o de la grabadora. Ambos estan enchufados a la fuente con unos cables rojos amarillos y negros y a la mother con una cinta. Estube un rato largo buscando con cuidado de no romper nada y sinebargo no encontré los jumpers. Alguien me podría dar una ayuda?

---

### Post by bloodytanga on 2009-07-23
Estem, estuve tocando los jumpers pero mi grabadora no tiene el esquema de cómo tienen que ir así que improvisé y ahora no me anda nada. En un momento logre iniciar el ubuntu desde el cd pero no me tomaba el rígido. Alguna ayuda? porque ahora tengo los jumpers ocmo estaban antes pero no me detecta ningun IDE.

---

### Post by bloodytanga on 2009-07-23
Bueno solucioné ese tema. Pero sigo sin poder saber como configurar en cable select. Lo deje como estaba antes porque sino no me arrancaba nada. El rigido tiene 2 jumpers y la lectora uno solo. El de la lectora esta en el set del medio (hay 3) y los de el rígido estan en las dos puntas dejando los 2 del medio libres. Alguien me podría ayudar? Después la banda esta conectado el cabezal A al rigido el del medio a la mother y el otro extremo a la grabadora.

Otra cosa: en un momento me olvidé de enchufar el IDE del disco rígido entonces el CD booteó lo más bien, pero como no había rígido no había dónde instalar el OS. Si dejo la lectora sola y conecto el rígio junto con el floppy disck al otro puerto de la mother puede funcionar?

---

### Post by staar on 2009-07-23
el del medio a la mother?? mmm, raro, generalmente el del medio es el master, el más cercano a este es el slave, y el otro va a la mother, funciona de todas maneras, pero es recomendable ponerlo como se debe...

la lectora no tiene un esquema (arriba o abajo, o en la etiqueta) con la configuración de los jumpers? a veces solo son las letras M (de master), S (de slave) y CS (de cable select), de última sacale una foto y posteala, para ver si te podemos ayudar asi...

pero si el livecd arrancó en algún momento quiere decir que vamos por el buen camino...

saludos

---

### Post by bloodytanga on 2009-07-23
Puede que la lectora tenga el esquema por arriba porque llegué a leer algunas letras y algunas líneas pero como est atornillado al gabinete me daba cosa sacarlo. Mañana lo saco y le saco una foto o reproduzco el esquema y lo subo. Entonces me recomendás poner el rigido con la ficha del medio, la lectora con la más corta y la más larga a la mother?
Intenté sacar el de la mother pero estaba muy duro. Se saca a la fuerza o hay que apretar algo?

---

### Post by staar on 2009-07-23
los ide son a la fuerza, pero con mucho cuidado, lentamente, y no tires mucho del cable porque se rompe la parte de arriba del conector...

intentá trabajar cómodo, así podés hacer mejor fuerza, recomendado porner el gabinete acostado sobre una mesa...

saludos

---

### Post by guillermolisi on 2009-07-23
Y tirar parejo para que no se doblen los pines de los conectores.

Indudablemente hay alguna configuracion mal en la identificacion de Master/Slave entre el disco y la lectora optica. Para mi es suficiente prueba el hecho que sin el disco inicio perfectamente desde el LiveCD.

Los discos IDE generalmente poseen en la etiqueta donde figura marca, modelo y demas detalles tecnicos y de fabricacion, un esquema de configuracion de jumpers para ponerlo como corresponde segun el resto de las unidades que posea la maquina.

Una mejor alternativa, desde el punto de vista funcional, es que teniendo solo dos unidades, ambas sean Master y cada una se conecte a un canal IDE con cable de datos independiente. Es decir, el disco como Master al canal IDE 1 y la unidad optica tambien como Master al canal IDE 2 (fijate que los dos conectores estan juntos en la motherboard y tienen su identificacion en la placa y en su manual).

Luego, e hilando mas finito, si los cables planos son de 80 hilos mejor aun.

---

### Post by bloodytanga on 2009-07-23
Eso es lo que preguntaba, si podía hacer eso. Porque tengo un floppy en el IDE 2 pero que nunca uso. Lo puedo poner como sslave en el 1 con el rígido o simplemente no ponerlo y que queden dos masters?

---

### Post by staar on 2009-07-23
los cables para floppy son diferentes a los IDE, son más chicos, asi que no va a andar...

para poner los dos como master necesitas dos cables IDE y dos conectores IDE en la mother (la tuya los tiene)

saludos

---

### Post by guillermolisi on 2009-07-23
> **bloodytanga said:**
> Eso es lo que preguntaba, si podía hacer eso. Porque tengo un floppy en el IDE 2 pero que nunca uso. Lo puedo poner como sslave en el 1 con el rígido o simplemente no ponerlo y que queden dos masters?
Nunca podrias tener un cable que va al floppy disk unit en IDE porque son fisicamente de otro tamaño. Y si lo tenes, esta MAL !

Por favor fijate bien como esta armada esa maquina y/o lee el manual de la motherboard y/o hacela revisar por alguien que entienda de hardware de PC.

---

### Post by bloodytanga on 2009-07-23
Gente les vengo a agradecer su esmero en ayudarme. Lo que hice fue sacar la grabadora, bajarla (porque estaba muy alta para que llegara el cable ide corto que estaba en el rigido) entonces la bajé, cambié las puntas de los cables IDE es decir la que enchufaba en el rígido la puse en la grabadora y al reés y probé y funcionó. Así que ahora estoy backupeando algo que baje hace un rato y me pongo a instalar el Ubuntu.
Nuevamente muchisimas gracias.

---

### Post by guillermolisi on 2009-07-23
Confirma que hayas podido instalar y apenas avises me voy de vacaciones por prescripcion medica :)

---

### Post by bloodytanga on 2009-07-23
Andá de vacaciones nomás que se me instaló perfectamente.

---

