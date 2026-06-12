---
title: "[SOLVED] Aplicaciones se cierran y no se que hacer"
date: 2009-07-09
forum: Hardware
---

### Post by Melva on 2009-07-09
Vamos a aclarar primero lo primero. YO NO SE NADA DE LINUX. 

Aclarado eso, procedo a explicar mi problema.

Despues de cansarme de catalogar los tonos de azul de las pantallas azules de Windows XP, y a insistencia de un novio que no se hace cargo de sus consejos, instale Ubuntu.
Maravilloso, me encanta. Funciona. Abro ubuntu y la pantalla sigue siendo color naranja, no azul..

Lo cierto tambien es que mi lectora de CD se declaro en huelga y tuve un millon de problemas para instalarlo, que terminaron en un formateo de disco, una reinstalacion de windows XP y una instalacion de ubuntu desde el wubi. Y anduvo. Pero en este momento, WIndows XP tambien anda barbaro. Con el disco formateado todo anda barbaro. Pero ahora tengo el ubuntu y no quiero usar el xp. Porque, segun me dijeron "Es igual de Facil"

Bueno, si yo tengo que saber programar linux para usar el ubuntu, esa afirmacion es cuestionable.

Bien,hete aqui el problema. Tanto el Rhythmbox como el Pidgin u otros clientes de mensajeria instantanea se cierran sin explicacion alguna. En el rhythmbox me di cuenta de que es cuando apreto el boton para pasar a la siguiente cancion. En el pidgin, el amsn, o el emesene, no encuentro una secuencia logica.  Desinstale el amsn, el emesene, y ahora hace lo mismo con el pidgin, asi que no es una cuestion de cambiar de cliente. No me pasa con Firefox. Aclaro proque las soluciones que encontre eran para el firefox.

Despues de mucho rompedero de cabeza y leer foros donde me hablan de cosas muy extrañas de las que no entiendo nada, logre darme cuenta de:

1) Que es una terminal. 
2) Como abrirla
3) Como lanzar una aplicacion desde una terminal
4) Que error me da el pidgin o el rhythmbox cuando se cierran.

Entienden a QUE NIVEL no se NADA DE LINUX? Tuve que primero intentar entender que ES una terminal.

El error en cuestion es "Fallo de Segmentacion". Informativo, no?

Y aparentemente por lo que pude encontrar en los foros en los que busque, no solo yo, sino nadie, sabe que pasa.

Se sugieren cosas como formatear discos, reinstalar sistemas, o meter lineas de codigo que no se cuales son y no se que hacen. 

Esta es mi computadora: Tengo unos 700 mb de ram, un procesador AMD de 2.4 GHz, un disco de 40 gb donde tengo instalado el ubuntu 8.04 LTS y el windows XP Home Edition, y otro disco de 80 donde tengo basicamente, mis documentos.

Ahora, digo, alguien tiene una solucion que no incluya formateos de disco, ni reinstalaciones de ubuntu, y que me permita solucionar esto?

Y por favor, ruego una explicacion para tarados. No lo soy, pero tampoco entiendo muy bien como instalar una aplicacion, asi que a nivel Ubuntu, soy MOGOLICA.

Melva

PD: No, mi novio no se hace cargo; en el momento que yo le digo que tengo este problema parece repentinamente muy interesado en saber como me va en la facu, el trabajo o si mi mama mando saludos.

---

### Post by guillermolisi on 2009-07-09
Como para sintetizar el contexto: Estas usando Ubuntu 8.04 a traves de Wubi finalmente o hiciste una instalacion nativa y podes iniciar la maquina eligiendo si lo vas a hacer con Windows o con Ubuntu ?

La ultima instalacion hecha en la maquina la hiciste con esa unidad de CD que se ha tornado rebelde, casi lista para su jubilacion ?

Tu novio esta suscripto al foro ? (pregunta no vinculante y sin obligacion de respuesta) :)

---

### Post by Melva on 2009-07-09
Tengo instalado a traves del wubi, y cuando inicio me da a elegir si quiero windows o Ubuntu. No, no hay otras isntalaciones en este momento. Formatee el disco, instale XP, e instale el Ubuntu a traves del wubi, y esto es lo que tengo. No hay otras isntalaciones. Solo un windows que esta como Gates lo Trajo al Mundo, y el Ubuntu que no esta mucho mas vestido.

Mi novio vive en un mundo paralelo; lleno de flores, dulces y muchos colores. Y no, no esta suscripto al foro. A el le funciona todo barbaro y de cualquier manera en este momento tiene una Mac, asi que cosas como que sistema operativo deberia usar un mortal, por mas que se da el lujo de dar consejo, no son parte de sus preocupaciones desde hace unos cuantos meses.

---

### Post by staar on 2009-07-09
por casualidad, recordás si las pantallas azules de Ventanas incluian la frase STATUS_ACCESS_VIOLATION? si ese es el caso, podrías estar teniendo problemas con las memorias de tu equipo, para asegurarte podés correr un memtest, al inicio, en el menú que te permite elegir si iniciar windos o ubuntu, seleccioná la opción de ubuntu que dice 'memtest' y dejala corriendo durante por lo menos 20 minutos o más, después contanos si te salieron errores y cuantos...

PD: no estoy seguro si la instalación mediante wubi trae el memtest, si no te aparece, podés usar el cd de ubuntu, colocalo al inicio y, en el menú que te sale, seleccioná 'Comprobar memoria' (no recuerdo si es eso exactactamente lo que dice, pero es similar)

saludos

---

### Post by Melva on 2009-07-09
Ehhmmm....

Me salieron 598 errores....

Eso no puede ser bueno, no?

---

### Post by staar on 2009-07-09
> **Melva said:**
> Ehhmmm....

Me salieron 598 errores....

Eso no puede ser bueno, no?

obviamente no, indican que, al menos uno de los módulos (si decís que tenés 768 MB de ram, supongo que tendrás dos módulos, uno de 512 y otro de 256, por lo menos es así en la mayoría de los casos) de la ram tiene fallas, y, en la mayoría de los casos, se debe cambiar el módulo...

lo que podés hacer, si te animás, es abrir la pc, sacar uno de los módulos, volver a armar la pc, y correr nuevamente el memtest y verificar si tiene errores, y después hacer lo mismo con el otro módulo, de esta manera podés saber si es uno solo el módulo defectuoso, o son los dos...

si solo uno de los módulos anda mal, mientras podés usar la pc con el otro (obviamente vas a tener menos ram) y después, si querés y/o podés, comprar otro y reemplazar el defectuoso...

PD: si no tenés idea como es un módulo ram, es una cosa parecida a  [esta]("http://img.confronte.com/productos/big/6/62851.jpg")

saludos

---

### Post by Melva on 2009-07-09
Jajaja, no, no tengo ni idea de como se ve un modulo ram, gracias por la imagen.
Igual ya me venia suponiendo que el problema era de ram; y venia planeando como meterle ram nueva.
Ahora lo unico que tengo que hacer es conseguir un criptologo para entender que es lo que significa exactamente lo que dice el manual del mother en cuanto a la ram y ver que compro.
Gracias :)

PD: Seeee, me animo a abrirlaaaa.... Porque soy re heavy re j****a y igual tengo buenos destornilladores en casa asi que no se me va a romper ninguna uñaaaaaa

---

### Post by pablo.s on 2009-07-09
Podés extraer un modulo
de la máquina y llevarlo
al señor memoriero. Ahi
nomás le decís: Deme 100
pesos de esto.

---

### Post by Melva on 2009-07-10
Sisi, lo lleve al señor memoriero, pero por 100 pesos me da uno igual nomas, y me parece que gastar cien pesos en una RAM de 256 cuando por 180 me llevo una de 1 gb, no tenia mucho sentido...

Igual me acabo de comprar un monitor pechocho que es todo chatito y finito y bonito y de mi sueldito no quedo un pesito, asi que la ram, pidgin, rhythmbox y demas quedan para el proximo sueldo.

De haber sabido que iba a romperse la ram no compraba el monitor y me compraba un par gigas de ram, pero bue, fue.

El mes que viene ver la ram, y comprarle un gabinete nuevo, que me acabo de dar cuenta que el original tiene la fuente encima de la salida del procesador, y sospecho que eso no puede ser bueeeeeno. 

De cualquier manera la fuente suena parecido al 151 cuando para en la puerta de mi casa, asi que preveo un cambio de fuente en un futuro no muy lejano, pero a menos que la computadora reviente, no creo que sea ni el mes que viene ni el otro.

Gracias chicos :)

---

### Post by Mauro22 on 2009-07-10
> **Melva said:**
> ... y comprarle un gabinete nuevo,... asi que preveo un cambio de fuente en un futuro no muy lejano,..


Hola!!


Si compras un gabinete nuevo, te viene con la fuente ya incluida, y si compras con kit te viene teclado, mouse y parlantes, aunque solo sirven para darle contra la pared. Pero la fuente te viene y son ""clasicas""... cumplen con lo que prometen para un usuario promedio.

---

### Post by staar on 2009-07-10
la fuente es un componente vital, si suena mal el cooler, abrila, limpiala y aceitala...

OJO si se te j**e la fuente, se puede llevar a toda la pc con ella...

saludos

---

### Post by Melva on 2009-07-10
Nah, me compro un gabinete, nomas. Tengo unos parlantes divinos que suenan excelente, y el mouse y el teclado sufrieron un pequeño accidente involucrando una noche particularmente frustrante y un vaso de gin tonic particularmente mal ubicado, asi que son nuevitos y son los dos genius. No tengo ningun interes en cambiarlos, asi que kit, no.

No necesito mas que una fuente clasica; nunca fui gamer y no planeo empezar a serlo anytime soon, (no es que el universo del gaming no me insterese, es solo que no puedo pretender estudiar, trabajar, estar de novia, pelearme con mi computadora y ademas ser gamer todo al mismo tiempo)

Un amigo de mi novio me dijo que me convenia comprar un gabinete, no un kit, y yo me quede con carita de signo de pregunta, preguntandome que diferencia habia y como los distinguia... ahi tenes, kit es con mouse y teclado :)

---

### Post by sergiom99 on 2009-07-10
Ja, que buena onda. Me alegro que resolvieras el problema original.

Los invitamos a vos, a tu novio, al amigo de tu novio y a todos los nuevos a pasar por 
[http://ubuntuforums.org/showthread.php?t=861391](http://ubuntuforums.org/showthread.php?t=861391)
y presentarse.
Saludos!

---

### Post by guillermolisi on 2009-07-10
Lo movi a Hardware ya que termino definiendose por ese lado este tema.

---

### Post by Melva on 2009-07-10
Si, se que si se j**e la fuente se puede llevar a toda la PC con ella, pero ya le cambie la fuente a esta una vez, y ya he cambiado fuentes a otras ocmputadoras, y esta tira unos meses mas tranquila. 

Cuando tenga que empezar a sacudir la maquina para que deje de hacer ruido, me preocupo mas.

Y ya me paso una vez que empezo a largar olor a quemado, y esa es una señal indiscutible de uqe la Hora de la Fuente ha llegado.
 Y si, me ha pasado (y es computadora mis viejos todavia la usan), pero no pretendo llegar ni a tener que sacudirla. Es solo que se banque un par de meses mas.

Ya aclare que mi novio vive en un universo paralelo lleno de flores, dulces y muchos colores, y el amigo vive en la casita con dos ventanitas al lado de la de el en ese universo. 

Como sea, ahi me presente. :)

pd: Gracias Guillermo.

---

### Post by cimarrón argento on 2009-09-03
Agrego acá un comentario porque tuve el mismo problema pero la solución fue otra en mi caso y quisiera compartirla para que le sirva a otros:
Hice lo del memtest pero CERO errores tenía, así que use la imaginación y la memoria (la mía que si debe tener errores) y busqué por otro lado que estuviera relacionado con el tema memoria y lo que resolví fue lo siguiente (perdonen si peco, soy novato linuxero, pero creo que no estoy equivocado)
Hace unos días cree un archivo swap para usar como memoria de intercambio, le asigné unos pocos 65MB.
Cuando instale Ubuntu Jaunty hace casi un mes solo estaba probandoló así que lo hice junto a "guinXP" en una partición pequeña y no hice particiòn de intercambio, resulta que dicha partición está llena hasta desbordar, y como ese archivo swap está alocado ahí mismo, al parecer el sistema intentaba mover algúnos procesos entre ellos algunos de Pidgin y como no hay espacio se caía la aplicación. Al ejecutar desde una terminal me salía el error "fallo de segmentación". al liberar espacio todo volvió a ser normal. Espero ayude a alguien.

---

