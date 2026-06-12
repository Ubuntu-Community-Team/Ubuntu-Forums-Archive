---
title: "Tocar con teclado Midi"
date: 2009-03-07
forum: Hardware
---

### Post by fausto_w on 2009-03-07
Buenas a todos!

Estoy dando mis primeros pasos en ubuntu y necesito un poco de ayuda..
tengo un teclado midi mooy barato con el q me gustaria tocar
la idea seria solamente tocar en tiempo real y q se escuche un sonido de piano saliendo de los parlantes de la laptop..
no se si soy específico..

probé con la pc y tiene un delay que asusta, mas de 1 segundo, (pero tengo una placa integrada q es realmente malisima)
asi q pense probar con esta q tiene ubuntu

es una acer travelmate 6291 si les sirve de algo, y tengo 8.10

alguien que sepa qué usar? q instalar? q configurar?
tambien pense q si no anda con la q viene podria probar con una de estas creative xmod q me presto un amigo [IMG]http://www.krunker.com/wp-content/uploads/2006/12/WindowsLiveWriter/CreativeXmodReview_A7BC/creative-xmod%5B2%5D.jpg[/IMG]

y ver de hacer salir el sonido por ahi..
bueno espero q se haya entendido algo

desde ya gracias por la ayuda!:)

---

### Post by pablo.s on 2009-03-08
Hola: Vamos por partes.

1) A lo que te referis como "delay", tecnicamente se llama [latencia]("http://www.musicador.com/la-latencia-de-audio-en-los-ordenadores-parte-1/")

2) No te recomiendo usar un teclado MIDI para tocar en vivo, a menos que estés
usando una Mbox de Digidesign o algo similar que tenga una latencia de 
microsegundos.

3) La Creative Xmod no la conozco personalmente, pero en el sitio de Creative
no aclara si reduce la latencia, y además me parece que necesitás Win XP SP2.

Saludos

---

### Post by NickCis on 2009-03-08
Hola, me intereso esto de usar la Pc como sintetizador.
Tengo un Korg Tr-61, que lo podria conectar por usb, ya que no tengo placa de sonido con MIDI in.
Probe conectandolo, y Ubuntu me lo reconoce perfectamente, hasta pude hacer que salga sonido atravez del teclado (usando el Tuxguitar, el programa usaba el teclado para una pista, por ejemplo la de un piano) y se escuchaba de una manera fluida, sin o con muy poca latencia.

Me gustaria probar algun programa que sintetize los sonidos en ubuntu, asi puedo usar mi sinte como teclado midi, y capas lograr mejor sonidos de Piano/etc. Que programas existen?, cual me recomiendan?.

Saludos.

---

### Post by pablo.s on 2009-03-08
Ah, pero el Korg TR-61 es una workstation, no es un controlador de $500 pesos!
Con la cantidad de patches que podés hacer con el aparato este no necesitas casi
de ningún software, me parece. Pero me estoy yendo por las ramas...

Podés ver aca un [proyecto]("http://www.musix.org.ar/wiki/index.php/Manual_de_Usuario") interesante que se llama Musix.

Saludos.

---

### Post by faktorqm on 2009-03-09
Instalense el kernel que viene con ubuntu studio. Esta compilado con los flags de tiempo real y baja latencia. Para hacer musica, es lo que va. salu2!

---

### Post by NickCis on 2009-03-10
> **pablo.s said:**
> Ah, pero el Korg TR-61 es una workstation, no es un controlador de $500 pesos!
Con la cantidad de patches que podés hacer con el aparato este no necesitas casi
de ningún software, me parece. Pero me estoy yendo por las ramas...

Podés ver aca un [proyecto]("http://www.musix.org.ar/wiki/index.php/Manual_de_Usuario") interesante que se llama Musix.

Saludos.

El tema es que no tengo el expansor sampler (sale como $1000, cosa que no puedo pagar) y los sonidos de Piano dejan mucho que desear...

Ahora miro esa pagina. Que dijeron del Ubuntu Studio que no lo entendi?, donde me lo puedo bajar para probar? xD

Saludos.

Edit: no conocen algun programa que me sirva para sintetizar sonidos de piano, o usar sonidos de piano sampleados, busco algo que tenga una mas o menos buena calidad de sonido, (por que si no uso mi Tr,,,)

---

### Post by fausto_w on 2009-03-12
Tengo un amigo que tambien me recomendo el ubuntu studio para esto.. me quiso explicar "rapido" y por tel como hacer para bajar la latencia al minimo pero era demasiado.. apenas consiga traerlo aca a mi casa les posteo la solucion =) 
Obvio q si alguien la tiene antes de q yo postee seria muuuucho mejor =)

btw, q envidia (sana) el teclado de mr NickCis, yo q voy a hacer con mi controladorcito de 100 mangos??
ah, aclaro q por fin lo hice andar con una latencia dentro de todo aceptable (pero calidad horrenda) en winxp, usando el reason de propellerhead. A lo mejor lo podria usar con wine en la laptop tb? ya probaré...

---

### Post by NickCis on 2009-03-14
Jeje,,, no envidies mi sinte que tampoco es tan bueno, deja mucho que desear x el precio :S...

Cuando sepas mas de los programas que sinteticen (o que reproduzcan los sonidos sampleados), por favor, postealo que me va a ser de mucha ayuda :P

Saludos.

---

