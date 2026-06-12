---
title: "[SOLVED] Router WRT54G en Hardy Heron Dudas Varias"
date: 2008-06-11
forum: Hardware
---

### Post by lega on 2008-06-11
Hola, ayer me compré este router para darle conexión wireless a la notebook, hice la configuración desde la notebook que tiene Vista, y aparentemente anda todo bien.

Cuento como tenia configurada antes del router la red, el modem de Arnet (Aztech DSL600) con ip 10.0.0.2 configurado como router conectado a un switch, la pc y la notebook conectadas al switch con ip 10.0.0.3 y 10.0.0.4, ahora el switch voló y la pc de escritorio esta conectada al router.
A la configuración del router accedo con la ip 192.168.1.1 (creo)a la pc le puse ahora la ip 192.168.1.2 y la notebook no le toque nada simplemente seleccioné la red wifi que detecta, la pc anda bien salvo que tengo id baja en el Amule y el deluge me tira puerto  bloqueados.
En la notebook no tenia internet, se me ocurrio mirar en el apartado red y me figuraba como dns 10.0.0.2, la cambié por la ip  del router 192.168.1.1 y salió andando, al cabo de un tiempo la conexión en la notebook se cayó, reinicie notebook,modem,router, volví a probar...y nada, fuí a red y ahí estaba otra vez la DNS 10.0.0.2, volví a cambiarla y anduvo.

Hay algo que estaré haciendo mal? tendré que cambiar la ip del modem? del router?leí por ahí que el modem conviene ponerlo como bridge, pero no se muy bien como hacerlo, el modem está con el firmware original de Arnet si alguien sabe como se hace...

Tambien leí que recomiendan reemplazar network-manager por Wicd para gestionar las conexiones wifi alguien lo probó?

Resumiendo, el problema que tengo es puertos bloqueados en la pc de escritorio para el Amule y Deluge, y perdida de conexión en la notebook, estoy seguro en un 99% que es algo que estoy haciendo mal en la configuración del router.

Si alguien tiene experiencia con este modelo de router y me da una mano estaré muy agradecido.

---

### Post by sergiom99 on 2008-06-11
por el tema de los puertos:
tenes que fijarte que puertos tenes configurados en el Amule y despues dentro de la config del router forwardear esos mismos puertos a la IP de la maquina que use el Amule (tiene que tener IP fija dentro de la red). En la web oficial de emule hay tutoriales de como hacerlo para cada router, y sino buscando en google lo vas a encontrar. No me acuerdo las pantallas para buscarlo, pero creo que en el config del router esta en la parte de Aplications & Games o algo por el estilo. Port Forwarding.

Yo tengo el mismo router (WRT54G v8 ) con el firmware opensource de dd-wrt.com en vez del orginal de Cisco. Tengo cablemodem asi q no tengo idea como hacer con lo de arnet.

---

### Post by faktorqm on 2008-06-11
Bueno, vamos por partes:

Vos ahi lo que hiciste, es poner un server DHCP para wlan en 10.0.0.X y el router en 192.168.1.X (¿por que lo hiciste?).

Esto es así, vos te conectas a arnet y los tipos te dan un ip dinamico, con toda la bola, vos de eso no te tenes que preocupar, esa es la parte de lo que el router llama "WAN".

Ahora bien, vos tenes que configurar el router de manera tal que el tipo se encargue de todo, (no se de donde sacaste lo del modo bridge pero es la solucion menos profesional). Entonces lo que hacés es darle un IP al router, y éste tiene 2 interfaces, una Wireless y una (o mas) Ethernet.
La onda es que vos al tipo le pongas de IP por ejemplo 10.0.0.1 y ahi solucionas el problema de conectividad en las dos computadoras. (poniendole claro a la de escritorio ip 10.0.0.4, mascara 255.255.255.0 y puerta de enlace y dns: 10.0.0.1; a la notebook dejala como esta, supongo en ip automatica, DHCP)

Bueno ahora que tenemos el problema de conectividad solucionado, vamos a ver el tema de los puertos. Para que te ande el reenvio de puertos, debes tener ip fija (por eso le puse fija a la de escritorio, considerando que en la notebook no bajas nada) y en el router, tenes que decirle que puerto queres reenviar y a donde. Esto es por que vos del lado de la WAN, quiero decir, si alguien te mira de afuera, "ve" 65.535 puertos, pero vos tenes dos computadoras atras, entonces el router lo que hace es decir bueno, este puerto te lo redirecciono a vos, y este otro a la otra pc, todos contentos.

Entonces vos le pones, por ejemplo, 7632 tcp para emule, reenvialo al 4662 de la ip 10.0.0.4 (la de escritorio); el 7642 udp (tmb para amule) mandamelo al 4672 de la ip 10.0.0.4. el 7635 tcp tambien reenviatelo al 4665 del ip de la pc de escritorio.

Para el deluge, lo mismo, si te dice el puerto (ejemplo) 12345, lo UNICO que tenes que hacer, es especificar un puerto desde afuera DISTINTO al que elegiste para el emule, entonces uno puede ser el mismo puerto, total el 12345 el emule no lo usa. Creo que al deluge le podes especificar un rango de puertos, lo cual es mucho mejor que darle uno solo. Le pones por ejemplo 12345 al 12355.

Para hacer todo esto, tenes que tener habilitado lo que se llama NAT (Network Address Translation; Traducción de direcciones de red) en el router, que eso ya lo tenés. (Si tuvieras el modo bridge como leiste solo tendrias internet de una maquina por vez, con el agravante de correr el marcador y el firewall por software)

En esta página ([http://www.adslzone.net/tutorial-18.1.html](http://www.adslzone.net/tutorial-18.1.html)) explican como configurar los puertos para abrir. No le des importancia a lo que dice primero, vos entra al router (primero 192.168.1.1 creo que era, cambia la ip en la parte de lan por 10.0.0.1 o la red que hayas definido, reinicia y luego volve a entrar)
y lee a partir de la parte que dice:

" nos dirigimos a Applications & Gaming 2º A continuación veremos una tabla para rellenar las reglas del mapeo de puertos. Veremos algo así:"

Espero haber sido de ayuda. Salu2!!

---

### Post by sergiom99 on 2008-06-11
eso, eso mismo!
mas completo y claro que lo mio, jaja.

Yo siempre forwardeo el mismo puerto. si en el eMule pongo 5432 en el router tambien forwardel el 5432.

Y algo que tenes que hacer Lega es filtrar el acceso al wifi. Lo podes hacer por las MAC address de las placas habilitadas para conectarse y ADEMAS con una clave WPA2 que el router ese se lo banca.
no es cuestion de andar financiando conectividad para los vecinos y abriendo tu red de gusto.

---

### Post by lega on 2008-06-11
Gracias a los dos por las respuestas esta tarde veo la explicación de faktorqm en mi casa, sergio, seguiste algun tuto para actualizar el firmware del linksys? me pasas el link? tengo la version 8 tambien
Gracias y esta tarde aviso como me fue.
Saludos

---

### Post by faktorqm on 2008-06-11
> **sergiom99 said:**
> Yo siempre forwardeo el mismo puerto. si en el eMule pongo 5432 en el router tambien forwardel el 5432.


Es lo mismo, la cosa es no dejar los defaults del emule, pero en mi casa por ejemplo, tenemos 2 pc's que bajan con emule, entonces si o si tengo que usar puertos distintos.

> **sergiom99 said:**
> 
Y algo que tenes que hacer Lega es filtrar el acceso al wifi. Lo podes hacer por las MAC address de las placas habilitadas para conectarse y ADEMAS con una clave WPA2 que el router ese se lo banca.
no es cuestion de andar financiando conectividad para los vecinos y abriendo tu red de gusto.

Aguantaaaaaaa dale 10 minutos a que configure la red, una vez que tenga todo andando, recien ahi blindás la conexion, si no no sabes si no tenes conexion, si no tenes internet o si metiste mal la clave xDXD :lolflag:

---

### Post by lega on 2008-06-11
> **faktorqm said:**
> 
Aguantaaaaaaa dale 10 minutos a que configure la red, una vez que tenga todo andando, recien ahi blindás la conexion, si no no sabes si no tenes conexion, si no tenes internet o si metiste mal la clave xDXD :lolflag:
jaja...agrego una duda que me surgió ahora , en el modem de Arnet tengo que hacer algo, en el modem no tengo que abrir puertos? porque hasta ayer tenía abiertos los puertos para la ip de la pc de escritorio, digo el modem no me va a bloquear los puertos por mas que esten abiertos desde el router?

---

### Post by faktorqm on 2008-06-11
amm, tenes un modem y despues el router wi-fi? o sea tenes:

cable telefono -> modem adsl -> router wifi -> notebook wifi y escritorio ethernet?

Si es asi no te mandes ninguna con el tema del direccionamiento, por que tenes que usar 2 redes distintas, una entre el modem y el router, y otra entre el router y las pc's. 

Contestando a tu pregunta original, el que rutea es el router justamente, si vos antes tenias modem adsl + switch sí reenviabas los puertos con el modem, pero ahora tenes que poner digamos que sea "transparente" (sin forwardeo de puertos) por que el decide que paquete va a cada pc es el router wi-fi, no el modem. Si vos lo dejas como está, hacés cualquiera. Si tenés esta configuracion decime y te explico bien como tendrias que hacer. Salu2!

---

### Post by lega on 2008-06-11
Si tengo esa configuración, a la configuración del modem accedo por la ip 10.0.0.2 y a la del router por 192.168.0.1 o similar ( no estoy en casa ahora)

---

### Post by sergiom99 on 2008-06-11
> **lega said:**
> sergio, seguiste algun tuto para actualizar el firmware del linksys? me pasas el link? tengo la version 8 tambien

Segui este tutorial: [http://www.dd-wrt.com/wiki/index.php/How_To_Flash_the_WRT54Gv8](http://www.dd-wrt.com/wiki/index.php/How_To_Flash_the_WRT54Gv8)

Fijate de estar seguro lo que estas haciendo. Yo NO tengo ADSL sino cablemodem, asi que el router esta conectado directo a la WAN.

Cambie el firmware por 2 motivos ppales: 
1. podes subir la potencia de emision del wifi (default 28mW, maximo 250mW, maximo sin agregar coolers y disipadores= 70mW. yo lo puse a 65mW)
2. podes cronear el apagado del radio, para que cuando no estas no emita wireless.
3. podes ver graficos de trafico y algunas cosas mas.

espero te sirva.

PS: con ese firmware funciona el script que postee para que la notebook te "cante" la potencia de la señal si tenes que orientar antenas.
HAsta la v6 este router tenia antenas removibles, para que pongas alguna mejor. ya no y lo que hay que hacer es abrirlo y operarlo para ponerle conectores.

---

### Post by faktorqm on 2008-06-11
Bueno, lo que tenés que hacer es algo así:

El modem de adsl dejalo como está, asi te auto-marca a arnet y tiene puesto como LAN la red 192.168.1.1, mascara 255.255.255.0. Tenés que poner con las reglas de los puertos, que todos los puertos los re-direccione pero a la direccion 192.168.1.2 (despues vas a ver por que). Entonces esa parte la tenemos ok. Tenemos conectandose automaticamente el modem adsl a arnet y un cable ethernet que va a la boca WAN del wireless.

Ahora bien, en el router, tenes que poner la WAN con la ip FIJA la direccion 192.168.1.2; mascara 255.255.255.0; puerta de enlace 192.168.1.1 y DNS: 192.168.1.1. 

Ahora en la parte de LAN le pones: 192.168.2.1, mascara 255.255.255.0. 
En la pc de escritorio tenes que poner 192.168.2.2, mascara 255.255.255.0, puerta de enlace 192.168.2.1; DNS 192.168.2.1.
En la parte del servidor de DHCP, donde dice pool dhcp, pone la red 192.168.2.0 desde el 4 al 10. Asi la notebook te va a agarrar alguna de esas direcciones. (lo podes verificar con el comando ifconfig)

Para redireccionar los puertos, lo mismo que antes pero cambia la direccion ip de la pc del escritorio.

Che y una pregunta me olvidaba, el wireless, no tiene para ponerle el cable del telefono? asi te ahorras el modem de arnet en el medio. supongo que no, pero pregunto igual. Salu2!!!

---

### Post by lega on 2008-06-11
Gracias faktorqm, el router es solo eso, router por eso va el modem enchufado a la entrada WAN del router,hay algo que no entiendo me parece que entre tantos numeros de ip yo no me expliqué bien.

el modem tiene como LAN la red 10.0.0.2 te adjunto capturas de la parte de WAN del modem y la parte de LAN, el router estaba mirandolo ahora tiene la IP 10.0.0.3 y como puerta de enlace la ip del modem 10.0.0.2 ,en cambio para el router en la LAN tiene la IP 192.168.1.1 y asigna IPs desde 192.168.1.100 al x.x.x.149 te adjunto capturas de esto tambien.

yo lo que hice fue poner a la pc de escritorio  la ip 192.168.1.100 mascara 255.255.255.0 y puerta de enlace 192.168.1.1 que es la ip del router, como servidor DNS en la pc me figura 10.0.0.2, navegar navega, pero lento, y me sigue tirando id baja el amule, trate de hacer el reenvío de puertos pero no entiendo que es eso de

> Entonces vos le pones, por ejemplo, 7632 tcp para emule, reenvialo al 4662 de la ip 10.0.0.4 (la de escritorio); el 7642 udp (tmb para amule) mandamelo al 4672 de la ip 10.0.0.4. el 7635 tcp tambien reenviatelo al 4665 del ip de la pc de escritorio
gracias por la ayuda, la verdad que me estoy sintiendo bastante inutil en este tema,:oops:
Saludos

---

### Post by lega on 2008-06-11
hago otro post para adjuntar mas caps
Gracias

---

### Post by faktorqm on 2008-06-11
Bueno, numero de izquierda a derecha las fotos como primer post, y lo mismo para el post que agregaste, para poder hacer referencia a ellas.
Asi, la foto 1.3 y 1.5 es la foto del modem de adsl, la 1.1, 1.2 y la 2.1 del router, y la 2.2 y 2.3 la de tu compu. 

La foto 1.5 corresponde a la parte de WAN de tu modem de adsl. Eso no tenes que tocar nada.

En la foto 1.3 cambiá, donde dice 10.0.0.2, poné 10.0.0.1.
Donde dice "enable DHCP server" debe ir seleccionado "server and relay off". Guardas y reinicias.

1.1 y 1.4 son la misma foto.... 

la foto 1.2 tiene que mostrar: 

tipo de conexion: FIJA, NO AUTOMATICA COMO DICE AHI
direccion ip: 10.0.0.2
mascara: 255.255.255.0
puerta de enlace: 10.0.0.1
DNS 1: 10.0.0.1
MTU: 1500 (si te deja ponelo en 1492, si no dejalo en 1500)

Fijate que donde dice 10.0.0.1 le estoy diciendo que se remita al modem de adsl para resolver nombres de dominio y direcciones ip's que no esten en mi red.

Bueno, ahora la parte de red local dejala como está, total esta ok, salvo el tema del dhcp que lo corregimos despues, no tiene importancia por ahora.

Ahi la pc del escritorio te tiene que quedar con:

direccion ip: 192.168.1.2
mascara: 255.255.255.0
puerta de enlace: 192.168.1.1
dns: 192.168.1.1

No me pusiste la configuracion inalambrica, asi que no te puedo decir si esta bien o mal, pero al menos si o si deberias salir con la de escritorio con internet andando. 

Segui posteando asi seguimos viendo que onda. Salu2!!

---

### Post by lega on 2008-06-11
Bueno faktorqm, no me funciono, al cambiar la ip del modem de Arnet no podía ni siquiera acceder a la configuracion del modem,así que lo hice fue seguír esta guia que encontré para configurarlo como bridge [http://cablemodem.fibertel.com.ar/dalmiroy2k/modemaztechcomar/Aztechguia4.txt](http://cablemodem.fibertel.com.ar/dalmiroy2k/modemaztechcomar/Aztechguia4.txt) lo que hice fue lo siguiente, configuré el modem de arnet como bridge, luego en el router le configure una conexion del tipo PPPoE, entonces ahí pongo los datos que estaban en el modem cuando estaba como router, de este modo el Linksys, hace la peticion al modem para que marque(eso es lo que yo entiendo)le puse ip fija a la pc y anduvo, despues configuré en el Linksys los puertos del amule para la ip de mi pc para probar y anduvo tengo id alta, lo que veo es que la conexion del modem como bridge no  no es muy estable, y a la configuracion del modem ahora no puedo acceder, asi que no se cuanto me va a durar...
Graacias por la ayuda capo, tenes una paciencia de locos

---

### Post by sergiom99 on 2008-06-11
me alegro que lo hayas arreglado. La verdad faktorqm se pasó.

Creo que cuando configuras la conexión podés poner que mantenga/reconecte el enlace. Mi firmware  [DD-WRT v24 RC-5 (11/22/07) micro]  dice "Force reconnect =Enable/disable" Ahí debería decir algo parecido. Así si se corta el ADSL, lo vuelve a marcar, y si no hay actividad lo mantiene conectado.
(Creo... yo tengo cablemodem)

---

### Post by faktorqm on 2008-06-12
Bueno, yo te iba a decir que hagas eso como segunda solución al caso, si es que no podías rutear efectivamente. Al modem, deberias acceder sin ningun problema con la ip 10.0.0.1. Esto no es asi?

Lo que hiciste vos ahí es usar un router menos digamos, y pasar de usar 2 routers a usar uno solo, pero aprovechando la interfaz de telefono del otro que el wi fi no tiene. Eso de que se te cae la conexion me parece que le activaste la opcion equivocada, como dice sergio hay una opcion mal puesta por ahi. Fijate que en el post de las fotitos hay una opcion que dice "connect on demand" y otra que dice "keep alive: 10 min". Busca en el router wi fi una opcion parecida. Yo en el mio (un zyxel 600) tengo 2 opciones, "connect on demand" y "nailed-up coneection". Y tengo connect on demand y nunca tuve dramas.

Me voy a rendir fisica I y welvo ... :S

---

### Post by lega on 2008-06-12
me voy a fijar, pero creo haberlo visto que estaba puesto en on demand, de todas maneras lo miro, el modem le cambie la ip a 10.0.0.1 y no podia entrar asi que lo resetee y me quedo con las opciones por default es decir con ip 10.0.0.2 lo configuré como bridge y a partir ahí ya no pude entrar, igual anda, así que no hay problema :) 

Gracias

---

