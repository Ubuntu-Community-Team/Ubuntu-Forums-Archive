---
title: "[AYUDA] Router Noganet"
date: 2008-06-13
forum: Hardware
---

### Post by agusssshhhh on 2008-06-13
La pregunta no es de Ubuntu, pero estoy desesperado así que lo vale.
Hace unas semanas adquirí un router Noganet (el modelo no me lo acuerdo) ADSL+WIFI.
Realicé las conexiones y lo configuré tal cual decía el manual. Cuando probé conectar la notebook vía WiFi, se conectó sin problemas. El tema es que la Pc que está conectada vía Ethernet al router nunca funcionó, no tengo internet ni red. Si conecto el cable Ethernet del modem a la Pc tampoco tengo internet. Antes de tener el router podía conectarme porque tenía el modem conectado a USB (es un modem Motorola de Fibertel que permite las dos conexiones). La verdad es que estoy desesperado y no puedo encontrar la solución a este problema. Lo más extraño, es que el sábado pasado, la PC se conectó sin haber tocado nada, y tuve internet y red por dos días aprox (hasta funcionaba tanto en XP como en Ubuntu!) hasta que se jodió todo de nuevo. Por el momento, sé que el router anda bien porque puedo conectarme a WiFi, sé que la placa de red anda bien porque se conectó el sábado...entonces, ¿cuál es el problema? Estuve leyendo en foros algo del DHCP pero no tengo idea de nada...
Tengo internet Fibertel 3M. Debe ser algún problema con las IPs.
Alguien me ayuda?

---

### Post by anka on 2008-06-13
Mmmh.., trata de poner el modelo asi sabemos mas o menos que caracteristicas tiene el router, pero mas o menos te voy adelantenado el tema porque si es como me paso una vez, es cosa del router, especificamente, del tipo de router que tenes.

Habia un modem de fibertel (el coso negro donde esta el "cable"), de ahi salia un cable de red a un router "adsl+wifi" y de ahi a 2 pc via cable y a una notebook via wireless. Que paso?, solo se conectaba 1 maquina por vez a internet. Que significa? el modem saltaba al router y le asignaba la ip a la primera maquina que levantaba. Por que? router equivocado, era adsl+wifi y el servicio era cablemodem. Conclusion? cambiar el router.

No quiere decir que sea esto lo que te pase, pero por los datos que das podria llegar a ser. Si podes, pone el modelo del router, tiene que estar escrito en alguna parte del aparatito.

PD: Yo no encuentro un switch de la misma marca.., en algun lado tiene que estar.. ¬_¬!!

---

### Post by agusssshhhh on 2008-06-13
No creo que sea ese el problema porque, como ya dije, el sábado, SIN TOCAR ABSOLUTAMENTE NADA las 2 máquinas tenían internet y pude crear una red. Duró poco (2 días), pero me dió la pauta de que el hw funciona, lo que debe estar mal es la configuración.
Un dato curioso es que si conectó la PC al modem vía Ethernet tampoco funciona. Es como que "no se da cuenta" de que le estoy enchufando algo (salvo que la placa de red prende el led indicador).
La máquina que no tiene problema en conectarse es la notebook por WiFi, eso anda perfecto.
El modelo del router es: NOGANET NG-W3304N.
Gracias.

---

### Post by fgl82 on 2008-06-13
A ver si entiendo bien los datos:

1) por wifi va todo bien
2) un tiempo te anduvo por ethernet
3) dejó de andar ethernet de golpe sin que toque absolutamente ninguna configuración ni cambies la ip de ninguna máquina.

mi conclusión es que puede estar jodida la salida ethernet del router. A mí me pasó con un modem de fibertel que se le quemó la salida ethernet y lo tenía que usar por usb.

Fijate si no es eso.

---

### Post by faktorqm on 2008-06-13
A ver, primero vamos a verificar que tengas todo en orden.

del cable coaxil -> modem de fibertel.
modem -> cable ethernet CRUZADO (a menos que sea auto mdi/mdix el router) -> router wi fi
router wi fi -> cable ethernet DERECHO -> PC
router wi fi -> por el aire :P -> otra PC

Si tenes eso ok, entonces lo que tenes que hacer es ponerle a la interfaz de WAN del router, la ip, mascara, puerta de enlace y dns que tenias vos en la pc. 
A la interfaz LAN, le tenes que poner una RED DISTINTA de la anterior, sino no anda nada. Si la red que tenias era 192.168.0.X, la de ahora debe ser 192.168.1.X ó 192.168.2.X, por ejemplo. Intenta poner en dhcp para no tener problemas con esto.

Salu2!

---

### Post by agusssshhhh on 2008-06-13
Creo que no me estoy haciendo entender. La cosa es así: Nunca, pero NUNCA tuve internet. El sábado pasado, sin tocar nada, empezó a andar solo. A los 2 días, dejó de andar. Tengo conectado el modem al router y de ahi a la pc y el wifi por el aire je. El modem anda, sino no tendría wifi y en este momento no podría estar escribiendo esto :P. En cuanto a lo de cable cruzado...es cable simple. El problema tiene q ser con el DHCP del modem que entra en conflicto con el del router, pero mucha idea no tengo :(.

---

### Post by aragorn4763 on 2008-07-21
Hola, por favor quisiera saber si hay alguna forma de instalar una webcam NogaNet. Hace solo unos dias comence a usar Ubuntu y todavia no pude descubrir como agregar hard que no este reconocido. Tampoco encuentro driver para esa camara.
Desde ya agradezco cualquier ayuda.

---

### Post by Hei Ku on 2008-07-22
> **aragorn4763 said:**
> Hola, por favor quisiera saber si hay alguna forma de instalar una webcam NogaNet. Hace solo unos dias comence a usar Ubuntu y todavia no pude descubrir como agregar hard que no este reconocido. Tampoco encuentro driver para esa camara.
Desde ya agradezco cualquier ayuda.

Abri un thread aparte. La ultima webcam Noganet que vimos por aca tenia un chipset bastante feo, espero que tengas suerte con la tuya. Para tener más datos, necesitaria que pongas la salida que te da este comando: lspci
Copialo en el thread que abras.

---

### Post by Duyos on 2008-08-18
Mira,
por lo que entendi tenes fibertel, de manera que el problema podria solucionarse si cuando configuras el router en la primera pantalla de wan tildas la opcion de clon mac address.
El tema es que la ip de fibertel es dinamica, y no te dejan meter dos maquinas porque la tienen asignada a la mac.
Si clonas la maquina fibertel va a ver una sola mac y vas a podes tener internet y red.
espero que te sirva
saludos

---

### Post by Lokkete on 2008-08-20
mmmm yo creo q se estan ahogando en un vaso de agua

antes q esta guia intenta desbloquear el el ethernet... las placas de red tienen un sistema de bloqueo que se puede activar por disntitos motivos q no vienen al caso, lo q tienes q hacer para desbloquearlas, es apagar la pc desenchufarla, apretar el boton del power para quitar toda carga de energia que haya quedado en la pc esperas un par de segundos y la enchufas de nuevo e intenta conectarte

(por mas que tu veas q tu placa de red esta activada tu lo ves por software pero como esta blockeada por hardware no tienes forma de saberlo hasta intentar esto q te dije)

1º antes que nada pero q nada nada nada de nada.... proba cambiar el cable de red... que sea como lo pide en el manual... suele ser derecho pero depende el router aveces es cruzado.... 

ahi descartas q sea el cable... 

2º corrobora que las dos pcs tenga ip automático asi no se pisan entre si las ip... (la notebook y la desktop)

ahi descartas problemas de ip que son muy normales

3º chequea los ping entre el router y tu pc desktop (ping "nº ip router"). Si no tenes respuesta es problema de hardware sea

         -Cable erroneo
         -Tu placa de red
         -el ethernet del router


cuando sepas que problema es te diré como seguir, si ya lo solucionaste te felicito...xD

si no sabes cual es el ip de tu router.. con el ip configurado como automático pon en la consola ifconfig. la puerta de enlace es el ip de tu router. si no aparece puerta de enlace el ip default aparece en el manua.. si no bue, lo veremos depues...:P intenta lo de arriba antes  q nada

---

### Post by condes on 2009-12-18
Yo tengo un problema similar. Tengo un router Encore. Una placa de red Nforce 680i que tiene dos salidas de red. Intente de todo para configurarla y nada. No tengo internet y el router es como si no existiera. A ver si alguien tiene una solución...
 
Saludos

---

