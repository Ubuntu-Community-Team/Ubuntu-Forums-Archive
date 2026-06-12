---
title: "Con Ubuntu 8.04 se escucha un pitido adentro de la PC"
date: 2008-06-10
forum: Hardware
---

### Post by fedeavila on 2008-06-10
hola! que tal? bueno aca escribiendo una vez mas, espero alguien me pueda ayudar o al menos tenga 1 idea de lo que le pasa a mi compu, creo que me estoy volviendo loco :/

me instale ubuntu 8.04 sin ningun problema... primero windows xp para usar los programas a los que estoy acostumbrado (msn live, office, photoshop, etc) y despues me baje el wubi installer; y con eso me instale ubuntu 8.04 al toke

bueno la cosa es rara, 1ro. no tengo internet (compartida... a traves de una red local) antes, cuando tenia windows xp y ubuntu 7.10, a veces internet no me funcaba en windows (x razones desconocidas) entonces usaba ubuntu xq andaba TODO!

ahora es al reves! la red con el nuevo ubuntu no me funca ni ahi (y x lo q lei a otras personas le paso lo mismo), pero eso para mi no es tanto problema xq tengo windows como salida... lo que mas me da un poco de cag*** es un ruido que escucho cada vez q inicio ubuntu :S

sisi! un pitido, muy muy bajito... se que suena bastante raro pero cada vez que inicio sesion y hago algo, (x ej. abro alguna aplicacion) me hace un ruido "pi-pi-pi-pi-piiiiiiiiiiiiiiiiiiii" muy pero muy finito...

la compu me la compre hace 2 dias! y con windows no me pasa... no se xq pero tengo el presentimiento de que es la placa de red... es una nvidia networking por lo que lei en la caja...

lo peor de todo es que me tire atras de la pc jaja y no entiendo de donde sale! no me doy cuenta... no lo escucho por los parlantes, es mas, estan completamente desconectados... tampoco siento que sale de adentro del gabinete... 

no se porque pero como la luz de la placa de red titila de verde y naranja presiento que sale de ahi, aunque puse el oido y no escucho que salga de ahi! sera posible que tenga algun parlantito que lo haga sonar? desde adentro digo... :S

yo siempre antes de hacer alguna pregunta trato incanzablemente de buscar yo mismo la respuesta antes, y la encontre! en la mayoria de las veces... pero esto... la verdad que me sorprende... 

perdon por decir esto pero siento que en vez de hacer mejores las cosas y buscar la sencillez pareciera que las empeoran... si no es esto, es el monitor que si lo tengo apagado ubuntu se me inicia en 640*480 ahora que tengo una placa de video masomenos decente, me doy cuenta que no puedo usar los efectos porque se me tiene que descargar el controlador de la nvidia, y se esta descargando!! a 15 kb/s!!! son 5 megas nada mas y hace como 20 min que estoy esperando... y lo PEOR de todo es que me di cuenta que "se tiene que dar cuenta" que uso internet, o sea, para que internet me funcione (a 1/4 de motor) tengo que abrir el firefox y simular que estoy navegando, ahi recien synaptic empieza a bajar las cosas...

jaja me da risa porque si con 5 megas me tarda tanto, no quiero saber lo que me va a tardar con los 140 de las actualizaciones...

saludos :/

otro problem: me bajo el controlador, reinicie, se ve todo GENIAL, las ventanas son como de gelatina jaja es lo mas, pero tengo la resolucion en 800x600 y desde las preferencias es lo maximo que me deja elegir...

chau gente! chau ubuntu jaja

---

### Post by gefarion on 2008-06-10
Es raro, con el tema del pitido verifica que no sea el monitor porque a veces suele pasar, simplemente apagalo.

Con respecto a el tema de la resolucion de pantalla date una vuelta por [aca]("http://pmartinez.wordpress.com/2008/04/26/cambiar-resolucon-de-pantalla-ubuntu-804/")

Saludos.-

---

### Post by jorgito on 2008-06-11
Hola fedeavila, 

Si te preocupa el sonido podes hacer la del mecanico.
A falta de un estetoscopio, usa por ejemplo un destornillador.
El mango te lo llevas a la oreja, y la punta la vas apoyando en los lugares sospechosos.
Antes que salgas corriendo a intentarlo, pensa si vas a poder evitar que la punta metalica haga un corto en algun lado. Si crees que no podes, entonces trata de usar un palito de plastico o de madera, cuanto mas duro mejor, asi atenua menos el sonido.
Placas de red con parlantes no vi, pero placas de modem si.

Espero que sirva
Saludos

---

### Post by anka on 2008-06-11
Puede llegar a ser culpa del cable que lleva audio desde el cd-rom a la placa de sonido. Me paso un par de veces que hacian ese ruido y los cables eran tan, pero tan pedorros que el aislante no servia y dispersaban la señal, generando ruido tipo pii-piiiiiii-pi-cuinch-cuinch, con lo que lo saque y tema solucionado. Tambien pudo ser pura casualidad o miedo a que le saque otro cable ("no te callas?!!, no te callas?!!!.., te saco el de power!!!" :P).

Suerte!

---

### Post by fedeavila on 2008-06-11
> **anka said:**
> Puede llegar a ser culpa del cable que lleva audio desde el cd-rom a la placa de sonido. Me paso un par de veces que hacian ese ruido y los cables eran tan, pero tan pedorros que el aislante no servia y dispersaban la señal, generando ruido tipo pii-piiiiiii-pi-cuinch-cuinch, con lo que lo saque y tema solucionado. Tambien pudo ser pura casualidad o miedo a que le saque otro cable ("no te callas?!!, no te callas?!!!.., te saco el de power!!!" :P).

Suerte!

jajajaja no sé... siempre los problemas mas raros me pasan a mi... nunk me pasa un "se te **** el disco rigido" o un "se te habrá quemado cuando se te volcó coca adentro del gabinete" .... y encima el chabon de arriba quiere que me ponga un DESTORNILLADOR adentro del oido... BASTA he dicho jaja despues vere como lo soluciono, voy a llamar al tecnico de donde la compre...

muchas gracias!

---

### Post by kornykyano on 2008-06-14
Hola creo que esto pueda ayudarte:
Si tienes un monitor del tipo tubo, el zumbido debe ser de este ya que a mi me ha pasado, te sugiero que disminuyas la resolución y/o la frecuencia  desde sistema>pantalla y gráfico

si no puedes prueba con nvidia-settings y cambialo desde ahí

---

### Post by valucha on 2008-06-15
[COLOR="DarkOrchid"]A mi novio le pasa que el disco rígido al trabajar hace ese pitido insoportable. Pero le pasa en ambos sistemas operativos. Pero en tu caso puede ser que como los componentes trabajan distinto en Windows que en Linux solo lo sienteas en el 2do.

El tema de la lentitud con la que bajan las actualizaciones y controladores restringidos y demases, se puede deber a una falla momentanea en el servidor. A mi me pasaba, (a todos creo) cuando salia una nueva version y luego de instalarla, buscaba las actualizaciones o los drivers restringidos, como los servidores están que explotan, me iba super lento.
[/COLOR]

---

