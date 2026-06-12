---
title: "No puedo conectarme a Internet :("
date: 2008-07-28
forum: Hardware
---

### Post by leo_liet on 2008-07-28
Antes que nada, hola a todos. 
Bueno, queria preguntarles porque no puedo conectarme a internet. Mi ISP es speedy, tengo un router ADSL SmartAX MT880(conectado a la placa ethernet)y mi SO es Ubuntu 8.04 Desktop Edition(64dit).
 Estuve buscando info. al respecto, pero siempre llego a lo mismo. Ir a la consola y poner 'sudo pppoeconf' y aceptar todo.
 Lo que hago es lo siguiente:
 Entro a la configuracion de red y configuro a eth0, de forma automatica(DHCP).Y luego abro la consola, pongo 'sudo pppoeconf' y me sale esto:
 
 - Se encontro un dispositivo ethernet eth0
 - Buscando un concentrador de acceso PPPoE en eth0
 - Buscando un concentrador de acceso PPPoE en oth0(modo multi-modem)
 - Lo siento, se consultaron 1 interface, pero no respondio el concentrador de acceso de su proveedor. Por favor, verifique sus cables de red y del modem. Otra razon del fallo puede ser tambien que este ejecutandose otro proceso pppoe y que este controlando el modem.

 Espero que puedan ayudarme

    Muchas Gracias :E

---

### Post by luchardi on 2008-07-28
No conozco ese modem, pero si podés entrar a su configuración posiblemente puedas hacer que "disque" automáticamente a tu conexión ADSL y quedaría como si fuera una red cableada sin discado automático para Windows / linux o el sistema operativo que uses.

---

### Post by rober-mpp on 2008-07-28
Te fijaste si tenes algun otro proceso corriendo ya ? 
Te podes fijar con:

```
ps aux
```

Fijate si encontras algun proceso con el nombre pppoe.
Nunca use adsl, siempre tuve cable modem y nunca use pppoe, por ende no te puedo ayudar mas que esto :S.

Suerte!!

---

### Post by atari130xe on 2008-07-28
re setea el modem es posible que si te lo entregaron nuevo haya que setearlo a cero, me paso con el thomson speedtouch s510 de Speedy, no habia manera de conectarme con pppoe (obteniendo el mismo resultado que vos= jasta que lo resetee.

---

### Post by vampichoke on 2008-07-29
Yo soy mas nuevo q vos en esto =) 

si tmb corres windows en paralelo (como yo) y internet tenes. 

lo mejor seria (es lo q hice yo y anduvo de una) q no tokes nada de la coneccion manual. dejalo como viene hardy (q buske automatica ip y dns) y dale en la terminal el pppoeconf y llena lo q te pide y tiene q andar.  

despues fijate q hay topics sobre ese modem.. talvez lo tengas q configurar como router =O

de ultima lo reseteas de cero (aunke speedy diga q es malo.. es lo mejor y mas rapido)


no puedo ayudar mas O.º)

---

### Post by jrferrari on 2008-07-29
Hola: Yo tengo speedy y el primer problema que tuve fue la falta de sincronismo con el servidor, que es lo que parece decir tu pppoeconf.
Verifica si el modem tiene encendida de manera permanente el indicador de adsl o dsl (no conozco tu modem yo tengo un zte).
Si esto esta OK verifica , antes de correr pppoeconf que no exista ningin pppd corriendo con: ps ax|grep pppd , si lo hubiera matalo con 
sudo killall pppd , y luego corre el pppoeconf. Tambien verificá con 
ifconfig el estado del vinculo ppp, debería darte algo como:

ppp0      Link encap:Protocolo punto a punto  
          inet dirección:190.174.219.253  P-t-P:200.51.241.203  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1492  Métrica:1
          RX packets:10064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8762 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:10250910 (9.7 MB)  TX bytes:1205172 (1.1 MB)

Suerte.

---

### Post by leo_liet on 2008-08-06
Hola, cuando pongo ifconfig me aparece esto:

eth0		Link encap:Ethernet direccionHW 00:lf:c6:af:3a:d8
		ARRIBA DIFUSION MULTICAST  MTU:1500  Metric:1
		RX packets:0 errors:0 dropped:0 overruns:0 frame:0
		TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
		colisiones:0 txqueuelen:1000
		RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
		Interrupcion:19 Direccion base: 0xdead

lo		Link encap:Bucle local
		inet direccion:127.0.0.1  Mascara:255.0.0.0
		direccion inet6: ::1/128  Alcance:Anfitrion
		ARRIBA LOOPBACK CORRIENDO MTU:16436 Metric:1
		RX packets:1472 errors:0 dropped:0 overruns:0 frame:0
		TX packets:1472 errors:0 dropped:0 overruns:0 carrier:0
		colisiones:0 txqueuelen:0
		RX bytes:73792	(72.0 KB) TX bytes:73792 (72.0 KB)


Tambien tengo problemas porque no puedo conectarme al router. Es decir, si pongo en mi navegador, la IP del router para configurarlo, etc. Me dice que no puede, como si no estuviera encendido/conectado. ¿Como hago para poder configurarlo?
Lamento no haber podido responder antes, lo que pasa es que con mi ISP(speedy) no podia conectarme ni desde windows, por 'problemas tecnicos'...

        Gracias

---

### Post by pol666 on 2008-08-06
yo tenia ese modem pero configurado como modemn no como router, y en modo roaming (no DHCP) con pppoe andabas... aora tengo un zyxel y es igual ;)

---

### Post by faktorqm on 2008-08-07
En el foro alguien posteo un paso a paso de como configurar ese "modem" en modo "router".
Usar pppoeconf trae muchas desventajas, a pesar de que varios lo sigan recomendando, asi que a menos que no tengan ganas de aprender y de tener una solucion profesional para su conexión a internet, usen pppoeconf. Salu2!

---

### Post by pol666 on 2008-08-07
faktorqm no serias tan ambale de indicar donde buscar ese tutorial?, por que yo se la forma pero solo desde windows, y a mi me interesa hacerlo desde ubuntu, usar pppoe me trae lios, no tanto en ubuntu pero por ejemplo no puedo hacer un Debian Net Install,  :(

---

### Post by faktorqm on 2008-08-08
Aca esta: [http://ubuntuforums.org/showthread.php?t=779717&page=2](http://ubuntuforums.org/showthread.php?t=779717&page=2)
De usar el search ni hablar no? ¬¬ (aunque debo reconocer que anda MUY mal, y no se por que, tuve que buscar "huawei mt" para que me devolviera resultados coherentes... :S)
De los otros modelos de modems (ethernet), proximamente en la pagina de ubuntu-ar :D Salu2!!

---

### Post by pol666 on 2008-08-08
A gracias, igual soy un papafrita pense que era del zyxel, no lei bien,

---

### Post by emi_cba on 2009-10-03
yo tengo una placa Sis190 y no puedo en Ubuntu 9.04 amd64. Nose si hay que instalar algun deb o que. La cuestion es que no me puedo conectar a internet punto a punto. Es decir que una maquina le provee internet a la Ubuntu

---

### Post by rubioo on 2009-10-03
Hola emi, [acá]("http://ubuntu-ar.org/node/181") tenes un tutorial que te puede ayudar.

  Saludos

---

### Post by emi_cba on 2009-10-04
Muchas gracias rubioo!! no le tengo mucha fe a esta chipse (me hizo renegar mucho en instalación, placa de video y ahora la red) pero la intención es lo que vale. Voy a renegar y si lo logro les avisare. Gracias por la ayuda. Saludos

---

### Post by rubioo on 2009-10-04
Jejeje yo tengo una placa SiS191 y en su momento, cuando trate de hacerla funcionar no pude. Y me compre otra placa de red.

 Saludos

---

### Post by emi_cba on 2009-10-04
y como me hace renegar la cosa parece q voy a tener q hacer lo mismo q vos.. Por ahora me tengo q conectar con Windows ;-(. Gracias por todo, saludos

---

### Post by faktorqm on 2009-10-07
mostrame la salida de todos estos comandos por favor:

```
lspci
```este lista los dispositivos pci de la compu

```
sudo lshw -C network
```este te lista los dispositivos de red mas detalladamente

```
lsmod | grep sis
```este te lista los modulos que tenes en memoria actualmente y se fija si tenes alguno que empiece con la palabra "sis"

```
uname -r
```este te da la version del kernel

```
ls /usr/src/linux-source-$(uname -r)/drivers/net/ 
```este lista los archivos que hay en esa carpeta.

Si alguno de los comandos no te funciona, tenes que probar con sudo adelante. Salu2!

---

