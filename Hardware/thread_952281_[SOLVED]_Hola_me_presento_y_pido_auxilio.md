---
title: "[SOLVED] Hola me presento y pido auxilio"
date: 2008-10-19
forum: Hardware
---

### Post by pachecojuancarlos on 2008-10-19
soy juan y tengo 52 años y como no podia ser de otra manera quiero iniciarme en el uso de ubuntu, me compre una maquina que tiene un mother Asus p5kn-am, y  tiene corel cuard chico, memoria de 4 Gb y disco de 252 Gb, pero cuando le puse el ubuntu live no pude activar la conexion en internet, tampoco tiene sonido, quise provar cafeina pero no funciona , tampoco kanoppy, pero no se si es hardware o software, como sea pido disculpas a la comunidad, pero quisiera que me ayuden a instalarlo, quiero saber si tengo que particionar mas el disco, ahora mal que me pese, estoy con windows pero solo le deje 80 GB creo que es mas que suficiente, pero el resto no se como seguir, bueno desde ya un abrazo y quedo a la espera.

Hold-E

---

### Post by gonzalo4018 on 2008-10-19
yo tampoco tengo conexion a internet, mira aca, capas encontras la solucion a tu problema

[http://ubuntuforums.org/showthread.php?t=948131](http://ubuntuforums.org/showthread.php?t=948131)

---

### Post by etitor on 2008-10-19
> **pachecojuancarlos said:**
> soy juan y tengo 52 años y como no podia ser de otra manera quiero iniciarme en el uso de ubuntu, me compre una maquina que tiene un mother Asus p5kn-am, y  tiene corel cuard chico, memoria de 4 Gb y disco de 252 Gb, pero cuando le puse el ubuntu live no pude activar la conexion en internet, tampoco tiene sonido, quise provar cafeina pero no funciona , tampoco kanoppy, pero no se si es hardware o software, como sea pido disculpas a la comunidad, pero quisiera que me ayuden a instalarlo, quiero saber si tengo que particionar mas el disco, ahora mal que me pese, estoy con windows pero solo le deje 80 GB creo que es mas que suficiente, pero el resto no se como seguir, bueno desde ya un abrazo y quedo a la espera.

Hold-E

Hola Juan. No nos decís qué tipo de conexión a Internet estás queriendo usar. Así es difícil saber qué puede estar fallando. Contanos todo sobre tu conexión.

---

### Post by guisheca on 2008-10-19
Dejo un pequeño aporte, acá tenés todo para empezar:
[http://guia-ubuntu.org](http://guia-ubuntu.org)
[http://sinwindows.wordpress.com/2008/07/22/curso-de-ubuntu-por-fin-completo/](http://sinwindows.wordpress.com/2008/07/22/curso-de-ubuntu-por-fin-completo/)
Saludos, perdón que no aporte algo mas.

---

### Post by pachecojuancarlos on 2008-10-21
Hola etitor y a todos tardo algo porque estuve leyendo las ayudas que me dieron,puse algunas en practicas pero no consigo entrar en internet, les cuento que incluso lo instale para saber si se configuraba pero no lo consegui, bien etitor te contesto la pregunta el sistema que tengo de conexion es de un vecino que vende servicio de manera inalambrica pero como yo estoy hace 22años al lado de su casa me dice que no me vende antena y que me pasa los cable que necesite y solo pague el servicio, en el icono sale que la velocidad es de 100 Mbps,y tardo para bajar por ejemplo el cd de ubunto 1 dia. dice que es banda ancha y tengo ip fija

---

### Post by chalito on 2008-10-21
pero entonces lo que vos tenes es un cable de red que te tira tu vecino hasta tu casa?

Si es así, y dice que te da una IP fija, tenes que usar los datos que el te provea. Básicamente te tiene que dar :

- Dirección IP tuya
- Mascara de red
- Dirección IP del default gateway
- Dirección IP de uno o más DNSs

una vez que tengas todo eso, vas a System->Administration->Network

y hace click en el boton de "Unlock" abajo. Ponés tu contraseña, y despues seleccionás "Wired Connection" y clickeas el boton de "Properties"
Ahi tenes que desactivar el tilde en "Enable Roaming mode", e ingresar los datos que te dio tu vecino.
El unico que no va ahi es el DNS, eso lo pones en la pantalla anterior, fijate que hay una solapa que dice "DNS". ahi tenes que agregar la(s) IP(s) de DNS que te haya dado.

---

### Post by faktorqm on 2008-10-22
> **chalito said:**
> una vez que tengas todo eso, vas a System->Administration->Network

y hace click en el boton de "Unlock" abajo. Ponés tu contraseña, y despues seleccionás "Wired Connection" y clickeas el boton de "Properties"
Ahi tenes que desactivar el tilde en "Enable Roaming mode", e ingresar los datos que te dio tu vecino.
El unico que no va ahi es el DNS, eso lo pones en la pantalla anterior, fijate que hay una solapa que dice "DNS". ahi tenes que agregar la(s) IP(s) de DNS que te haya dado.

Te traduzco por si de casualidad vivis en Argentina y tenes el ubuntu en castellano.........

una vez que tengas todo eso, vas a Sistema -> Administracion -> Red
y hace click en el boton de "Desbloquear" abajo. Ponés tu contraseña, y despues seleccionás "Conexion cableada" y clickeas el boton de "Propiedades".
Ahi tenes que desactivar el tilde en "Activar modo itinerante", e ingresar los datos que te dio tu vecino.
El unico que no va ahi es el DNS, eso lo pones en la pantalla anterior, fijate que hay una solapa que dice "DNS". ahi tenes que agregar la(s) IP(s) de DNS que te haya dado.

Salu2!

---

### Post by chalito on 2008-10-22
Gracias, faktorqm. Acá tengo el ubuntu en inglés y no estaba seguro de como lo tradujeron en castellano, asi que no me animé a traducirlo yo literalmente para no confundir ;)

---

### Post by superjulin on 2008-10-22
Hola juan ,me presento ante toda la comunidad ubuntera,espero poder ayudar a la cominudad dentro de mis posibilidades.
Con respecto a tu coneccion a internet ,seguiria los pasos de chalito para ver si funciona (con la traduccion de faktorqm),siempre y cuando la placa halla sido reconocida.
Ahora con el tema de sonido seria bueno ver chipset que trae,una ojeada al manual de mother dice que chipset es,y buscarlo en el fabricante,generalmente los chipset de asus (no todos)se pueden descargar los drivers para linux.

---

### Post by pachecojuancarlos on 2008-10-22
> **chalito said:**
> pero entonces lo que vos tenes es un cable de red que te tira tu vecino hasta tu casa?

Si es así, y dice que te da una IP fija, tenes que usar los datos que el te provea. Básicamente te tiene que dar :

- Dirección IP tuya
- Mascara de red
- Dirección IP del default gateway
- Dirección IP de uno o más DNSs

una vez que tengas todo eso, vas a System->Administration->Network

y hace click en el boton de "Unlock" abajo. Ponés tu contraseña, y despues seleccionás "Wired Connection" y clickeas el boton de "Properties"
Ahi tenes que desactivar el tilde en "Enable Roaming mode", e ingresar los datos que te dio tu vecino.
El unico que no va ahi es el DNS, eso lo pones en la pantalla anterior, fijate que hay una solapa que dice "DNS". ahi tenes que agregar la(s) IP(s) de DNS que te haya dado.

Chalito: el vecino me dijo que tengo IP,DNS,Mascara de red y puerta de enlace, lo que sucede es que los datos los coloco pero igual no los toma tal vez sea el mother porque es de los mas economicos(asus p5kpl-am), gracias a factorqm, por la traduccion, QUE GRAN DETALLE, a superjulin te cuento que era yo nomas que no habia abierto le ventana que aumenta el volumen que viene por defecto baja asi que igual gracias ahora veo videos y sobre todo musica, lamentablemente seguire molestando porque no pienso aflojar ahora, espero mas sugerencia ¡ hasta la victoria !( que exagerado ¿no?)los dejo tengo que ir a trabajar pero nos vermos mañana

---

### Post by chalito on 2008-10-22
Ehm.. pero exactamente como es que no te los toma? te da algun error? los valores desaparecen?

Podes probar poner todos esos datos, darle ok y cerrar la ventana y despues en una terminal tipear: ifconfig -a
y postear el resultado nuevamente?

---

### Post by superjulin on 2008-10-22
voy a preguntar algo simple,el cable esta bien armado?la placa de red linkea?te reconoce la placa linux?porque cargando los datos que te paso tu vecino ip,gateway,dns tiene que salir funcionando solo.No creo que sea el mother como mucho no funcionara la placa de red.Con los datos cargados proba haciendo un ping al getaway para si responde.

---

### Post by sebastianabate on 2008-10-22
Ese mother tiene una placa de red de 1GB. Yo he tenido varios problemas con placas de 1GB con los switchs baratos; lo que te recomiendo es que setees a mano la velocidad de la placa y el tipo de duplex. Esto lo hacés con:

```
sudo apt-get install ethtool
```y cuando ya esté instalada la utilidad vas probando con las distintas configuraciones, empezá con la más lenta y andá subiendo hasta ver con cuál es que falla (si es que éste es el problema):

```
sudo ethtool -s eth0 speed 10 duplex half
``````
sudo ethtool -s eth0 speed 10 duplex full
``````
sudo ethtool -s eth0 speed 100 duplex half
``````
sudo ethtool -s eth0 speed 100 duplex full
```

---

### Post by pachecojuancarlos on 2008-10-23
> **chalito said:**
> Ehm.. pero exactamente como es que no te los toma? te da algun error? los valores desaparecen?

Podes probar poner todos esos datos, darle ok y cerrar la ventana y despues en una terminal tipear: ifconfig -a
y postear el resultado nuevamente?

Hola Chalito, me parece que debe andar por ahi el asunto porque cuando fui a siste/admi/redes, me abrio la solapa y no tengo habilitado el boton desbloquear, por lo que fue inutil todo lo que realice, puedo selecionar conexion cableada y me permite ingresar ip, dns y puerta de enlace, al darle ok toma la configuracion, pero  no puedo navegar, quiero contarte que esta maquina viene con una placa inalambrica, y un como pendrive pero es blootho o algo asi y en windows estan configurados, aunque aca no hay redes inalambricas y de las otras,asi que un solo crucerio en la barra y anda la del cable nomas, otra cosa nunca me salio cuando solicite ayuda en la ventana, la misma figura de placas de red solo carteles que decian red cableada y punto a punto y el cuadradito de la tilde, bueno ahora vere que me sale con lo de la terminal, luego te cuento saludos y gracias a sebastianabate y superjulin,y logicamente a vos por el aguante.

---

### Post by erdosain9 on 2008-10-23
ejm! bueno, yo no tengo muchos conocimientos sobre linux o ubuntu (podés sacar el "muchos" si querés).  Pero me tira que estás en red y que la computadora de tu vecino debe ser la cliente y tenés que configurar también esa para poder salir...  Digo tal vez estés en red con su computadora y por eso vos podés toquetear la tuya pero no va a pasar nada hasta que no toques algo en la otra y veas luego de configurar la tuya en función de esa...
es así??? estás en red con la de tu vecino???
Saludos, espero haber ayudado algo

---

### Post by pachecojuancarlos on 2008-10-24
> **erdosain9 said:**
> ejm! bueno, yo no tengo muchos conocimientos sobre linux o ubuntu (podés sacar el "muchos" si querés).  Pero me tira que estás en red y que la computadora de tu vecino debe ser la cliente y tenés que configurar también esa para poder salir...  Digo tal vez estés en red con su computadora y por eso vos podés toquetear la tuya pero no va a pasar nada hasta que no toques algo en la otra y veas luego de configurar la tuya en función de esa...
es así??? estás en red con la de tu vecino???
Saludos, espero haber ayudado algo

Hola Erdosain9, no tal vez no supe explicarme, mi vecino vende servicio de internet inalambrico,por la cercania me dijo no te vendo la antena, te tiro cable, el cable va a lo que parece un servidor de la central que esta mas lejos, de la maquina esa salen cables para todos lados y sale tambien para la antena y para mi, pero yo pago el servicio como el resto de los vecinos asociados, solo que yo no compre antena nada mas, pero te aclaro que nunca tuve problemas, por ejemplo, con la maquina mas vieja (k62-500) que ahora tiene mi señora, ahi tengo internet tampoco lo tuve con la maquina de mi hijo esa es un pentium 4, en ambas hay internet, y ambas en su tiempo use kanoppy,cafeina y fedora todos live y podia configurar sin problemas internet y el resto de las cosas ,creo que debe ser algo del hard.
si tenes tiempo te tiro algo que me hace, fijate, cuando voy a admin/herram de red, dispositivos de red interfaz ethernet (0)informacion ip
protocolo= IPV4
direc. ip= ok
masc. de red= OK
difucion = ahi me lanza un error me da un valor a 255 yo me acuerdo que en knoppy, me daba el mismo valor y debia cambiarlo, no se si ahi va el ip o la puerta de enlace pero eso es secundario por ahora, porque cuando lo marco y aprieto configurar, me saca una pantalla que dice "la interfaz no existe
compruebe que el dispositivo este escrito correctamente y que este soportado por su sistema.
Por otro lado tambien le hice pig al la puerta de enlace, y me da 100% exitoso

---

### Post by pachecojuancarlos on 2008-10-24
> **erdosain9 said:**
> ejm! bueno, yo no tengo muchos conocimientos sobre linux o ubuntu (podés sacar el "muchos" si querés).  Pero me tira que estás en red y que la computadora de tu vecino debe ser la cliente y tenés que configurar también esa para poder salir...  Digo tal vez estés en red con su computadora y por eso vos podés toquetear la tuya pero no va a pasar nada hasta que no toques algo en la otra y veas luego de configurar la tuya en función de esa...
es así??? estás en red con la de tu vecino???
Saludos, espero haber ayudado algo

> **pachecojuancarlos said:**
> Hola Chalito, me parece que debe andar por ahi el asunto porque cuando fui a siste/admi/redes, me abrio la solapa y no tengo habilitado el boton desbloquear, por lo que fue inutil todo lo que realice, puedo selecionar conexion cableada y me permite ingresar ip, dns y puerta de enlace, al darle ok toma la configuracion, pero  no puedo navegar, quiero contarte que esta maquina viene con una placa inalambrica, y un como pendrive pero es blootho o algo asi y en windows estan configurados, aunque aca no hay redes inalambricas y de las otras,asi que un solo crucerio en la barra y anda la del cable nomas, otra cosa nunca me salio cuando solicite ayuda en la ventana, la misma figura de placas de red solo carteles que decian red cableada y punto a punto y el cuadradito de la tilde, bueno ahora vere que me sale con lo de la terminal, luego te cuento saludos y gracias a sebastianabate y superjulin,y logicamente a vos por el aguante.

> **sebastianabate said:**
> Ese mother tiene una placa de red de 1GB. Yo he tenido varios problemas con placas de 1GB con los switchs baratos; lo que te recomiendo es que setees a mano la velocidad de la placa y el tipo de duplex. Esto lo hacés con:

```
sudo apt-get install ethtool
```y cuando ya esté instalada la utilidad vas probando con las distintas configuraciones, empezá con la más lenta y andá subiendo hasta ver con cuál es que falla (si es que éste es el problema):

```
sudo ethtool -s eth0 speed 10 duplex half
``````
sudo ethtool -s eth0 speed 10 duplex full
``````
sudo ethtool -s eth0 speed 100 duplex half
``````
sudo ethtool -s eth0 speed 100 duplex full
```


Sebastian, trate de escribir en una terminal las lineas pero me dice no sabe que es sudo o algo asi lo siento, necesito mas datos te lo agradeceria

---

### Post by superjulin on 2008-10-24
juan podrias postear lo que te da la salida de 

ifconfig -a

lspci | grep ethernet

y las ips que te paso tu vecino,y el /etc/netwok/interfaces

Los comandos que te paso sebastian los podes haces sin **sudo** tranquilo

---

### Post by hictio on 2008-10-24
> **superjulin said:**
> 
Los comandos que te paso sebastian los podes haces sin **sudo** tranquilo

Ojo, si se necesita sudo, particularmente para el 1ro.

---

### Post by pachecojuancarlos on 2008-10-24
> **superjulin said:**
> juan podrias postear lo que te da la salida de 

ifconfig -a

lspci | grep ethernet

y las ips que te paso tu vecino,y el /etc/netwok/interfaces

Los comandos que te paso sebastian los podes haces sin **sudo** tranquilo

Hola superjulin, te mando las ip, 192.168.0.51
masc. 255.255.255.0, y puerta de enlace 192.168.0.1, respecto al ifconfig -a te cuento que probe pero me dio lo siguiente-: 
ubuntu@ubuntu: $ bash ifconfig  -a orden no encontrada, pero ahora veo que debo escribir lspci | grep ethernet seguidamente asi que te ruego paciencia me voy a trabajar y al regreso a las 01 de la mañana lo pruebo y te contesto tambien probare lo de sebastian, gracias a todos nos vemos

---

### Post by pachecojuancarlos on 2008-10-25
Hola nuevamente, estuve investigando algo mas,alle que no tuve usar sudo, para la prueba de la tarjeta solo escribia ethtool -s eth0 speed 100 duplex half o full y lo tomaba bien no se que hace pero se que lo tomaba lo deje en 100, tambien probe el ifconfig -a y le agregue el resto (ispci | grep - ethernet, la respuesta fue 
ispci: error al obtener informacion sobre4 la interfaz: dispositivo no encontrado 
bash : grep - ethernet
finalmente como descubri que el comando ifconfig andaba sin mas lo invoque y me dice: eth0 link encap : ethernet direccion 00:15:c7:ce:ll
inet direccion: 192.168.0.51  difusion 192.168.0.255  masc. 255.255.255.0
como veran estuve haciendo los deberes y otra vez me sale ese valor de difusion, cuando en realidad deberia ser 1 o 51 no se cual porque no se si es puerta de enlace o el otro valor que no conozco el nombre, pero como hago para cambiarlo, estoy cerca lo siento en mis huesos, gracias por el aguante a todos

---

### Post by hictio on 2008-10-25
> 
le agregue el resto (ispci | grep - ethernet, la respuesta fue
ispci: error al obtener informacion sobre4 la interfaz: dispositivo no encontrado
bash : grep - ethernet


Probalo asi, a diferencia de Windows/ DOS, todos los comandos (y los nombres de archivo) son case sensitive en linux, no es lo mismo tipear 'ls' que 'LS' en el Terminal.

```

lspci | grep thernet

```

O bien

```

lspci | grep Ethernet

```

Otra forma de obtener informacion sobre la tarjeta de red, si esta activa, es reconocida por el sistema, es tipear en el Terminal:

```

lshw -C Network

```

Y te va a imprimir algo similar a esto:
```

esteban@tango:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:1c:d6:43
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=10.120.10.5 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes

```


Hey, ahora entiendo porque no necesito de sudo para esto:
```

sudo apt-get install ethtool

```

Hardy ya viene con ethtool instalado!

---

### Post by pachecojuancarlos on 2008-10-25
hola ictio: te comento que realice esta vez bien la tarea, lspci | grep ethernety la respuesta fue la siguiente: 
01:00.0 Ethernet controller:Realtek semiconductor Co., Ltd. RTL 810lE PCI Express, Fast Ethernet Controller (Rev 02)
03:00.0 Ethernet controller : Realtek  Semiconductor Co. Ltd.,RTL -8185IEEE 802.11e\b\g wireless Lan Controller (Rev 20).
Ahora si bien entiendo creo que la tarjeta la reconoce , pero porque no me deja escribir el dato que falta o sea no puedo acceder desde el menu herramientas de red a configurar porque me habla de que no reconoce la interfaz y que el dispositivo este escrito correctamente

---

### Post by hictio on 2008-10-26
Hola Juan Carlos, cuando puedas, por favor postea el resultado de este comando, lo tipeas en un terminal, lo mejor es que maxifiques la ventana para que veas todo el output.

```

lshw -C Network

```

---

### Post by pachecojuancarlos on 2008-10-27
Hola hictio: primero gracias, por el aguante, vamos a lo nuestro
el comando lshw -C Network

lshw -C Network:
WARNING: you should run this program as super-user
* -network
descrption:  Ethernet interface
product:  TRL 8101E pci Express fast Ethernet controler
vendor:  Realtek Semiconductor Co. , Ltd.
physical id:  0
bus info:  pci@0000:01:00.0
logical name:  eth0
version:  02
serial:  00:22:15:c7:ce:11
width:64bits
clock:  33MHz
capabilities:  bus master cap_list ethernet physical
configuration:  broadcast=yes  driver=r8169  driverversion=2.2LK
latency=0  module=r8169  multicast=yes
* -network UNCLAIMED
desciption:  ethernet controller
product:  RTL-8185 IEEE 802.11a/b/g wireless LAN controller
vendor:  Realtek Semiconductor Co. Ltd.
physical id:  1
bus info:  pci@0000:03:01.0
version:  20
width:  32bits
clock: 33MHz
capabilities:  bus master cap_List
configuration:latency=64 maxlatency=64 mingnt=32  

espero esto sirva te comento que primero no estaba instalada el no se que, para ejecutar el lsh, y me dio un mensaje para hacerlo  con sudo, pero como  antes funciono directo lo instale y se colgo la terminal, abri otra pestaña,cerre la colgada y alli obtuve este resultado.
bien seguimos en contacto saludos

---

### Post by hictio on 2008-10-27
Hola,

Conecta el cable de red a la placa, abri un terminal y tipea esto, 2 dos comandos, ENTER para terminar c/u, te va a pedir tu password luego del 1er ENTER:

```

sudo ifconfig eth0 192.168.0.51 netmask 255.255.255.0 up
sudo route add default gw 192.168.0.1

```

Despues de eso, tipea en el terminal:
```

ping 192.168.0.1

```

y postea el resultado (para interrumpir el ping, tipea la teclas Ctrl + c)

---

### Post by superjulin on 2008-10-27
Hola juan,nuevamente por aca ,a ver si lo podemos sacar.Vi que posteastes las salidas y las placas estan funcionando y estan reconocidas,si no entendi mal podes agregar los valores pero no te los deja grabar,de ser asi,postea la siguiente salida con el comando en una consola
**cat /etc/networ/interfaces** a ver que resultado da,en caso que no aparezcan las ip,hay que agregarlos a mano a ver si zafa.
Para agregarlos hace lo siguiente
**gedit /etc/network/interfaces** (lo vas a tener que hacer como superusuario)y a continuacion agregas las siguiente lineas.
el archivo lo vas a ver asi :
[B]auto lo
iface eth0 inet loopback
auto eth0
iface eth0 inet dhcp(cambias el dhcp por static)y agregas esas lineas abajo
 address 192.168.0.51
 netmask 255.255.255.0
 gateway 192.168.0.1[/B]

esto por un lado,grabas y guardas,despues haces esto 
**gedit /etc/resolv.conf**(abrir como superusuario)
y agregas las ip de los DNS .terminado esto ejecutas este comando 
**/etc/init.d/networking restart**cruzamos los dedos y esperemos que funcione .
Contanos como te fue

---

### Post by superjulin on 2008-10-27
Bueno Juan es lo mismo que posteo hictio,se ve que cuando escribia posteo antes el,esperemos que funcione

---

### Post by pachecojuancarlos on 2008-10-29
Hola disculpen la demora es que esta vez fue de terror, aca estan los resultados de las pruebas:
1º hictio_

juan@juan-desktop:~$ sudo ifconfig eth0 192.168.0.51 netmask 255.255.255.0 up

[sudo] password for juan: 

juan@juan-desktop:~$ sudo route add default gw 192.168.0.1

juan@juan-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=19.7 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=7.05 ms....chorizo de datos y luegp ctrl+ c

--- 192.168.0.1 ping statistics ---
18 packets transmitted, 18 received, 0% packet loss, time 17002ms
rtt min/avg/max/mdev = 7.009/9.553/19.714/3.378 ms
 resultado no tengo internet.

2º superjulin
juan@juan-desktop:~$ cat/etc/network/interfaces
bash: cat/etc/network/interfaces: No existe el fichero ó directorio
 
juan@juan-desktop:~$ gedit/etc/network/interfaces
bash: gedit/etc/network/interfaces: No existe el fichero ó directorio

a esta altura me , me pregunte si existia el fichero, te cuento que lo busque y esta el archivo en la direccion que me dio superjulin pero que es claro lo escribi cuando use el sudo de hictio, ahora bien luego de eso apague todo un rato arranque pero no funciona internet realice ping desde herramientas de red, sobre el gw y me volvio a dar 100% pero no funciona, prodra ser que el sistema no reconozca el hard? .. asi que seguimos molestando, otra pregunta, como hago para escuchar musica siempre me pide istalar codec pero me sale que se produjo un error y son la mayoria mp3 de blue y rock nada mas gracias

---

### Post by hictio on 2008-10-29
Si te entiendo correctamente lo que posteaste, te aclaro, los comandos:
```

sudo ifconfig eth0 192.168.0.51 netmask 255.255.255.0 up
sudo route add default gw 192.168.0.1

```

Te asignan datos a tu tarjeta de red, pero no son estaticos, las asignaciones duran mientras no las cambies nuevamente, o si apagas la maquina los perdes, eran para ver si te anda correctamente el hardware, lo cual parece ser el caso.
Cuando puedas, por favor, prende todo, conecta el cable de red nuevamente, dale a los dos comandos, y testea si llegas a internet, hace esto:
```

ping 208.67.222.222

```

Si estas saliendo a internet, te tiene que responder el ping correctamente, es el DNS de OpenDNS.
Si eso ya te anda, solo faltaria agregar la data de tus DNS a /etc/resolv.conf, y ver que settee los valores a tu tarjeta de red cada vez que bootea, y listo.

Si no te la guarda en el archivo 'interfaces' -como casi todo en Linux- se puede usar otro metodo para que cargue la data de la tarjeta de red cuando booteas.

Para los mp3s tenes que instalar una serie de programas para que los reproduzca, suena mas dificil de lo que :D con internet andando en unos 5 mins esta hecho.
Mi consejo, segui viendo que le pasa hasta tener acceso a internet, una vez hecho eso, lo demas es mas facil; ademas, a estas alturas, una computadora sin internet casi no sirve :D

---

### Post by pachecojuancarlos on 2008-10-30
Hola hictio, te comento que realice los pasos que me distes pero no  se conecta al rebootear, mire en los directios y algunos archivos estan pero como vos decis se desaparecen, tambien tuve problemas al inicio porque no hacia ping con nada, luego desconecte todo y empece otra vez,estos son los resultados.

juan@juan-desktop:~$ sudo ifconfig eth0 192.168.0.51 netmask 255.255.255.0 up

[sudo] password for juan: 

juan@juan-desktop:~$ sudo route add default gw 192.168.0.1

juan@juan-desktop:~$ ping 208.67.222.222

PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.

64 bytes from 208.67.222.222: icmp_seq=1 ttl=52 time=238 ms

64 bytes from 208.67.222.222: icmp_seq=2 ttl=52 time=209 ms

64 bytes from 208.67.222.222: icmp_seq=3 ttl=52 time=205 ms

--- 208.67.222.222 ping statistics ---

10 packets transmitted, 10 received, 0% packet loss, time 9002ms
rtt min/avg/max/mdev = 

190.183/210.863/238.881/15.278 ms

juan@juan-desktop:~$ /etc/resolv.conf
bash: /etc/resolv.conf: No existe el fichero ó directorio
juan@juan-desktop:~$ 

espero que este bien lo que hice, otra cosa el comando 

cat /etc/networ/interfaces, me muestra la ip, netmask y gw correctas y todo parece estar bien pero el poncho no aparece, como sea si no molesto sigo esperando ayuda, hasta luego

---

### Post by superjulin on 2008-10-30
Juan los archivos en muy dificil que se hallan borrado,y en caso de haber sido siempre que se modifica algun archio linux hace back up,con respecto al hard quedate tranquilo porque esta detectado y pasa mas por un tema de configuracion,con respecto a los comando que te pase recorda de dejar un espacio entre CAT y / si se tipea todo junto el shell no lo reconoce.
Lo que me parece que tendrias que hacer es de hacer son los comandos que te paso hictio pero agregarle los DNS en /etc/resolv.conf ,recorda de hacer gedit /etc/resolv.conf(respectar el espacio)grabar y guardar.
Proba y contanos como te fue ,pero no desistas que esta cerca de salir funcionando

---

### Post by hictio on 2008-10-30
```

juan@juan-desktop:~$ ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=52 time=238 ms
64 bytes from 208.67.222.222: icmp_seq=2 ttl=52 time=209 ms
64 bytes from 208.67.222.222: icmp_seq=3 ttl=52 time=205 ms
--- 208.67.222.222 ping statistics ---

10 packets transmitted, 10 received, 0% packet loss, time 9002ms
rtt min/avg/max/mdev =

190.183/210.863/238.881/15.278 ms

```

Ya tenes acceso a Internet, no estas contento? :D

Ok, prende la Ubuntu, conectala a la red, repeti lo que hiciste de asignarle una direccion IP a eth0, y agregar la ruta al default gateway, y tenes que agregar la data de los servidores DNS en el archivo '/etc/resolv.conf' como dice superjulin. Te recomiendo esto, tipea:
```

Alt + F2

```

y dentro, tipea esto:

```

gksudo gedit /etc/resolv.conf (ENTER)

```

te abre un editor de texto, agrega esto:
```

nameserver 208.67.222.222
nameserver 208.67.220.220

```

Y guarda los cambios. Proba algunos pings para ver si todo camina Ok, abri un terminal y testea a:

ping yahoo.co.uk
ping gmail.com
ping casarosada.gov.ar

A menos que el vecino que te da internet (o su ISP) sea muy anal en cuanto a seguridad, deberias poder resolver nombres usando los DNS de OpenDNS.
Si todo eso camina Ok, avisanos para automatizar la asignacion de al info de tu tarjeta de red cuando bootea Ubuntu, y se acabo el tema.

---

### Post by pachecojuancarlos on 2008-10-31
Hola amigos aca les mando los resultados:
juan@juan-desktop:~$ sudo ifconfig eth0 192.168.0.51 netmask 255.255.255.0 up
[sudo] password for juan: 

juan@juan-desktop:~$ sudo route add default gw 192.168.0.1

juan@juan-desktop:~$ gksudo gedit /etc/resolv.conf

juan@juan-desktop:~$ ping yahoo.co.uk

ping: unknown host yahoo.co.uk

juan@juan-desktop:~$ ping gmail.com

ping: unknown host gmail.com

juan@juan-desktop:~$ ping casarosada.gov.ar

ping: unknown host casarosada.gov.ar

juan@juan-desktop:~$ ping anses.gov.ar

ping: unknown host anses.gov.ar

juan@juan-desktop:~$ ping 208.67.222.222

PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.

From 192.168.0.51 icmp_seq=1 Destination Host Unreachable

--- 208.67.222.222 ping statistics ---
10 packets transmitted, 0 received, +9 errors, 100% 

packet loss, time 9036ms
, pipe 3
ATENCION ACA SI QUE NO ENTENDI NADA. PERO LA COMUNIDAD TE BANCA LEI POR AHI QUE SI DESCONECTA TODO Y VOLVES A ARRANCAR PUEDE QUE FUNCIONE, ASI LO HICE Y ESTE ES EL RESULTADO:

juan@juan-desktop:~$ 

juan@juan-desktop:~$ sudo ifconfig eth0 192.168.0.51 netmask 255.255.255.0 up

[sudo] password for juan: 

juan@juan-desktop:~$ sudo route add default gw 192.168.0.1
juan@juan-desktop:~$ ping 

208.67.222.222

PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.

64 bytes from 208.67.222.222: icmp_seq=1 ttl=51 time=260 ms

--- 208.67.222.222 ping statistics ---

6 packets transmitted, 6 received, 0% packet loss, time 4999ms
rtt min/avg/max/mdev = 

189.528/224.676/272.608/30.709 ms


juan@juan-desktop:~$ gksudo gedit /etc/resolv.conf
ACA ESCRIBI EN LA PANTALLA QUE ABRIO Y GUARDE DESPUES CERRE

juan@juan-desktop:~$ ping yahoo.co.uk

PING yahoo.co.uk (217.146.186.221) 56(84) bytes of data.

64 bytes from rc1.vip.ird.yahoo.com (217.146.186.221): icmp_seq=1 ttl=49 time=292 ms

--- yahoo.co.uk ping statistics ---

7 packets transmitted, 6 received, 14% packet loss, time 5995ms
rtt min/avg/max/mdev = 

284.463/290.245/294.712/3.404 ms


juan@juan-desktop:~$ ping gmail.com

PING gmail.com (209.85.171.83) 56(84) bytes of data.

64 bytes from cg-in-f83.google.com (209.85.171.83): icmp_seq=1 ttl=237 time=294 ms

--- gmail.com ping statistics ---

7 packets transmitted, 7 received, 0% packet loss, time 6055ms
rtt min/avg/max/mdev = 

264.538/314.947/544.089/94.013 ms


juan@juan-desktop:~$ ping casarosada.gov.ar

PING casarosada.gov.ar (208.69.32.132) 56(84) bytes of data.

64 bytes from hit-nxdomain.opendns.com (208.69.32.132): icmp_seq=1 ttl=52 time=199 

ms

--- casarosada.gov.ar ping statistics ---

8 packets transmitted, 7 received, 12% packet loss, time 6997ms
rtt min/avg/max/mdev = 

190.418/201.616/208.448/5.712 ms


juan@juan-desktop:~$

De este modo queda demostrado que funciona todo, ahora falta la frutilla o el bicarbonato para la indigestion (lo digo por lo que a mi respecta acuerdence que vengo de dos lados, de vuelta y de window, :)) 
bueno gente espero las ultimas instrucciones y gracias

---

### Post by hictio on 2008-10-31
Parece que va bien encamina la cosa :)

Para automatizar la carga de los valores a tu tarjeta de red, vamos a hacer lo siguiente, editar un archivo de configuracion, es un archivo de texto de plano, con las instrucciones para que cargue la informacion de la tarjeta de red.
Bootea tu Ubuntu y tipea:

```

gksudo gedit /etc/rc.local (ENTER)

```

Te pide tu passwd, y abre el editor de texto con el archivo de configuracion listo para editar.
Agrega esto:

```

ifconfig eth0 192.168.0.51 netmask 255.255.255.0 up
route add default gw 192.168.0.1

```

antes de la linea que dice "exit 0", guarda, cerra.
Conectale el cable de red, y rebootea la maquina de nuevo a Ubuntu.
Una vez booteada, tendrias que tener acceso a internet sin necesidad de tipear nada de nada, hace las pruebas de ping como antes, tanto por direccion IP como con hostname para ver si no hay problemas de resolucion de nombre con el archivo '/etc/resolv.conf'.

Si esto esta todo Ok, avisanos para poder haer un test mas y ver si el router de tu vecino funciona ademas como DNS, para agregarlo a la lista de servidores del archivo '/etc/resolv.conf'.

Si esto te camina Ok, por lo menos no tenes que tipear nada raro para conectarte a internet, pero hay que ver que le pasa tu setup que no te permite asignarle la data de la tarjeta de red a traves del GUI.

---

### Post by hictio on 2008-10-31
Una pregunta que se me olvido, en el ultimo test, cuando ya te respondian los pings hechos por hostname, abriste Firefox y navegaste por internet?

---

### Post by pachecojuancarlos on 2008-11-01
HICTIO - SUPERJULIN
¡¡FRUTILLA, FRUTILLA!!  digo EXITO EXITO GLOBLAL:guitar:
Bien luego de esta extraña demostracion de alegria senil, les cuento que estoy escribiendo desde UBUNTU, mientras escucho unoS temasos de pappo y estoy leyendo algo del diario, tu ultima pregunta fue que si habia navegado por el firefox , la verdad que no, lo intente anteriormente y no pude, asi que la ultima vez no lo hice, lo del tes conta conmigo, no se de que se trata pero vamos, Hasta aca fue muy bueno, ahora te cuento porque queria ubuntu, resulta que quiero aprender a progamar en c o c++, porque yo trabajo con plc y esos se programan en lader pero nunca sabes, que hay detras de cada paso, ademas es una deuda personal, solo he escrito el famoso "hola mundo" pero es un problema ver el resultado, asi que te pido indicame como se compila y como hago para ver el resultado despues te llamo nuevamente cuando cuelge el sistema por algun error jua jua , bueno hictio, superjulin y a todos gracias y aca estoy esperando que tengo que hacer con lo del tes nos vemos, me esperan unos blue de aquellos chau

---

### Post by sam_award on 2008-11-01
> **pachecojuancarlos said:**
> Chalito: el vecino me dijo que tengo IP,DNS,Mascara de red y puerta de enlace, lo que sucede es que los datos los coloco pero igual no los toma tal vez sea el mother porque es de los mas economicos(asus p5kpl-am), gracias a factorqm, por la traduccion, QUE GRAN DETALLE, a superjulin te cuento que era yo nomas que no habia abierto le ventana que aumenta el volumen que viene por defecto baja asi que igual gracias ahora veo videos y sobre todo musica, lamentablemente seguire molestando porque no pienso aflojar ahora, espero mas sugerencia ¡ hasta la victoria !( que exagerado ¿no?)los dejo tengo que ir a trabajar pero nos vermos mañana

 ps yo te digo lo mismo , yo tambien manejo ip fija , y xq mejor no tomas los datos de tu conexion de xp y la piones en ubuntu , osea , tomas la ip , las DNS , la puerta de enlace y la busqueda primaria , y la copias en las respactivas areas de coneccion de ubuntu

aparte para lo del sonido , alamejor no tienes bien instalados todos los codecs , aca te dejo un trukin q m funciono :

sudo gedit /etc/apt/sources.list



Agregar esto hasta el final:



## Medibuntu - Ubuntu 8.04 &#65533;hardy&#65533;

## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free



En terminal escribir: ( para lo de la clave GPG )


wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update



Regresamos a la terminal y lo actualizamos con:



sudo apt-get update



Escribimos esto en la terminal:



sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3



Despues de hacer todo esto nos vamos a la terminal y copiamos y pegamos:



sudo apt-get install libdvdcss2



Despues de instalarlo y bla bla bla &#65533;


sudo apt-get install w32codecs


Despues de instalarlo y bla bla bla &#65533;



sudo apt-get install ffmpeg



y ya con todo eso, podremos disfrutar nuestros videos xD


suerte y ojala te sirva , salu2

---

### Post by superjulin on 2008-11-01
Juan buenisimo me alegra que tengas internet ,confirmanos si estas con firefox o algun otro navegador

---

### Post by pachecojuancarlos on 2008-11-01
> **superjulin said:**
> Juan buenisimo me alegra que tengas internet ,confirmanos si estas con firefox o algun otro navegador

hola Superjulin, no te digo que es cuestion de senilidad,me olvide de lo tecnico, si todo el tiempo que escribi lo hice desde firefox que lo uso desde que era phoenix, ahora  volviendo, no se donde se mira la velocidad (aun) estuve mirado algunos videos y bueno las fotos, pero basicamente todo lo hacia desde el navegador, los ping me respondieron todos desde que inicie el programa,no hubo necesidad de tocar nada solo que los televisores de la red no cambian de color como en windows,entonces tarde en darme cuenta que tenia internet hasta que habri el navegador y la pagina cambio es decir se conecto y a partir de ahi vamos nomas. 
Bien espero haber sido mas especifico , saludos

---

