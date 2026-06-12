---
title: "Control remoto para media center casero."
date: 2009-02-27
forum: Hardware
---

### Post by valucha on 2009-02-27
[COLOR="DarkOrchid"]Hola! como andan?, espero que bien.
Volví para contarles que ando tratando de hacer un media center casero, de hecho tengo todo ya, solo me falta algo con que manejarlo y que no sea un mouse inalámbrico.

Anduve buscando por todos lados alternativas, como el nunchuck de la wii que se que anda bien pero es muuuy caro, hasta pointers para pasar diapositivas que no sé si andarán para lo que yo quiero, hasta que decidí postear acá a ver si alguien me guía.

Mi idea es instalar el XBMC que es hermoso, rápido y bien bien útil para lo que yo quiero. Enontré este control [http://articulo.mercadolibre.com.ar/MLA-49027339-media-center-control-remoto-y-receptor-kit-de-hauppauge-_JM](http://articulo.mercadolibre.com.ar/MLA-49027339-media-center-control-remoto-y-receptor-kit-de-hauppauge-_JM) y al parecer funciona, pero quería saaber si alguien me podría asegurar, así no gasto 170 pesos al **** :).y sino, en todo caso, que alternativas me proponen.

Espero sus respuestas, y gracias desde ya :)[/COLOR]

---

### Post by NickCis on 2009-02-27
Mira, lo qe yo te recomiedo es armar un receptor infrarojo y despues comprar un control remoto universal (o usar cualquier control remoto qe tengas tirado por casa).

Yo lo hice usando esta guia: [http://taringa.net/posts/info/940315/Mod-3---Tu-control-remoto-para-PC.html](http://taringa.net/posts/info/940315/Mod-3---Tu-control-remoto-para-PC.html) [( Por si esta caida, ak google cache :P ) ](http://74.125.47.132/search?q=cache:x0PA_ljOYtsJ:www.taringa.net/posts/info/940315/Mod-3---Tu-control-remoto-para-PC.html+http://taringa.net/posts/info/940315/Mod-3---Tu-control-remoto-para-PC.html&hl=es&ct=clnk&cd=1&gl=ar)

Los materiales los compras en una casa de electronica, y dspues la cosa es re facil. Lo unico que no consegui fue ese receptor infrarojo, pero pedis cualqier receptor infrarojo, y que te especifiqen los pines (que es cada patita) y sirve.

Yo lo arme y lo use un por un tiempo en windows, no probe usarlo en linux, pero por lo que lei no es muy dificil.

Preguntando en este post ( [http://ubuntuforums.org/showthread.php?t=1055241](http://ubuntuforums.org/showthread.php?t=1055241) ) me dijeron qeu con el xmapkeys podes asignale acciones a cada boton.

Lo que tiene bueno esto, es que no es muy dificil hacerlo y es barato. Si tenes dudas, imprimite la lista de materiales y el esquema del circuito ( te recomiendo que uses el primero, el que usa mas componentes) y llevaselo al flaco del local de electronica, si le vas con buena onda, seguro te explica como tenes que hacer todo (acordate de anotarlo!! xD).

Saludos, cualquier cosa preguntame acerca del circuito :P.

P.d.: acordate que la Placa universal tiene que ser marcada, osea, es como un cuadrado con todos agugeros, que de un lado tiene metal para que pegue el estaño.

Edit: Busque mas info y encontre esto: [http://stuff.nekhbet.ro/2006/07/10/make-an-infrared-remote-control-for-pc.html](http://stuff.nekhbet.ro/2006/07/10/make-an-infrared-remote-control-for-pc.html) 
Guia en castellano: [http://www.fullcustom.es/guias/control-remoto-infrarrojo-software-usb-serie](http://www.fullcustom.es/guias/control-remoto-infrarrojo-software-usb-serie)

Podes buscar mas info en esta pagina: [http://www.lirc.org/](http://www.lirc.org/)

Y aca, te dice como instalar el LIRC para dispositivos serial en ubuntu: [http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install](http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install) y [https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy)

Tambien podes probar esto, creo qe es mas facil, solo nececitas un receptor infrarojo [http://www.lirc.org/ir-audio.html](http://www.lirc.org/ir-audio.html) y [http://www.lirc.org/html/audio-alsa.html](http://www.lirc.org/html/audio-alsa.html)

---

### Post by guisheca on 2009-02-28
Que hilo mas interesante, me encató lo que posteaset NickCis, es lo mas práctico y barato que vi en mi vida, es casi una obligación hacerlo.
Saludos.

---

### Post by NickCis on 2009-02-28
> **guisheca said:**
> Que hilo mas interesante, me encató lo que posteaset NickCis, es lo mas práctico y barato que vi en mi vida, es casi una obligación hacerlo.
Saludos.

jeje, yo cuando lo vi tambien me parecio una obligacion, a la semana estaba llendo a comprar las cosas xD. 
Lo que vi ahora que me intereso, era el receptor infrarojo, pero usando la placa de sonido :|, es mucho mas simple de hacer (solo nececita el receptor infrarojo xD). Pero te ocupa la entrada de sonido, encambio si usas el otro le das un uso a ese puerto com/serial que esta tan al **** xD.

Acuerdense que el receptor infrarojo si o si tiene qe tener 3 patitas :P

Saludos.

---

### Post by faktorqm on 2009-03-01
che muy buena onda tu post, soy tecnico en electronica y me encantó, lo que si, mepa que la mataste a val con esto, por que no la veo soldando patitas... xD

---

### Post by santiagoward2000 on 2009-03-01
> **faktorqm said:**
> che muy buena onda tu post, soy tecnico en electronica y me encantó, lo que si, mepa que la mataste a val con esto, por que no la veo soldando patitas... xD

Uhh! Qué agresivo! DEFENDETE VALUCHA!

Y a NickCis: muy buena guía! Cuando tenga tiempo tengo que probarlo.

---

### Post by valucha on 2009-03-02
[COLOR="DarkOrchid"]Jajajaja, muuuuuy bueno lo que me mandaste Nickcis, me vas a hacer ahorrar un montón de guita :), además de entretenerme por unos cuantos findes jajaja.
Igualmente no creo poder armarlo yo solita, no por ser mujer (!!!!!!!!!!!!!) sino porque soy bruta con las manos (hasta para cocinar y limpiar :P), pero teniendo un papá y un novio ingenieros no creo que me haga drama.
Mil gracias, después (en unos meses cuando lo termine) te digo como queda :)[/COLOR]

---

### Post by valucha on 2009-03-02
[COLOR="rgb(153, 50, 204)"]emmm donde quedó la estrellita para agradecer?![/COLOR]

---

### Post by sergiom99 on 2009-03-02
desde la caida de los foros quedo desactivada, al igual que la opcion para marcar como 'Solved'.

---

### Post by NickCis on 2009-03-03
El tiempo qe me pase buscando el solved,,,, xD,,,
Era muy util, lastima qe lo sacaron...

Saludos.

P.D.: el post ese de taringa, no es mio, lo tenia en favoritos y vino re bien cuando lei este thread xD

---

### Post by c4d0rn4 on 2009-03-06
recien terminado de armar! xD

en win ya lo pude hacer funcar, me itra error instalando lirc ubuntu =S

en

MICROELECTRONICA S.H.
J. D. Peron 1455 - Capital Federal - (1037)
(011)4371-0123 - Fax: (011)4371-0123


comprate el Everlight IRM-8601M 

y armalo con esto

[http://www.lirc.org/receivers.html](http://www.lirc.org/receivers.html)

me rajo pal baile cya!

---

### Post by NickCis on 2009-03-08
Avisen si alguien logra hacerlo andar en Ubuntu, me parece que esta siendo un poco jodido :S...

Saludos.

---

### Post by c4d0rn4 on 2009-03-09
> **NickCis said:**
> Avisen si alguien logra hacerlo andar en Ubuntu, me parece que esta siendo un poco jodido :S...

Saludos.

ya lo hice andar, pero no con los repositorios dado que me tiran error siempre. A lo macho hay que compilarlo, me parece que es la mejor solución.

[http://ubuntuforums.org/showthread.php?t=163496&highlight=lirc+homebrew](http://ubuntuforums.org/showthread.php?t=163496&highlight=lirc+homebrew)

@Valucha
Después para media center, si le ponés xbmc (que me dio problemas con el pulseaudio, pero le encontré la vuelta matandolo) hay un archivo Lircmap.xml en su carpeta de configuración.

Editas el archivo poniendo el nombre del control y los nombres de los botones y en dos patadas tenés andando el control con el xbmc.

Luego para todo lo demás hay que editar  ~/.lircrc que no es tan amigable, recién le estoy agarrando un poco la mano.
[http://www.lirc.org/html/configure.html#lircrc_format](http://www.lirc.org/html/configure.html#lircrc_format)

---

