---
title: "Conexión con Módem Nokia CS-10 - Banda Ancha móvil Entel - Ubuntu 9.10???"
date: 2010-02-10
forum: Hardware
---

### Post by NOVATA1173 on 2010-02-10
Holaaaaaa!!! ):P


Primero que todo aclaro que soy una SUPER NOVATA en UBUNTU y estoy tratando de conectar mi Banda Ancha Móvil de Entel con un Módem Nokia CS-10 obviamente en un netbook con SO Ubuntu 9.10 pero por supuesto "algo" no funciona y NO HAY CASO que me conecte :confused: les comento los pasos que he seguido:

1.- Conectaba el módem y mi netbook ni se inmutaba, por lo que supuse que me faltaba el driver apropiado.

2.-Estuve investigando (obvio que no preg sin googlear y pasar HORAS tratando de buscar una solución) y según [http://ubuntuforums.org/showthread.php?t=1310892](http://ubuntuforums.org/showthread.php?t=1310892) hay un bug pero aue ya fué resuelto, pero NO ENTIENDO NI JOTA la solución que dan ahi :-k 

3.- Después de copiar "cosas" en la Terminal y hacer "no sé que" logré que por lo menos el módem "funcionara" yo hasta ahí feliz! :) jurando que mis problemas se habían resuelto... PERO.... al realizar la conexión ingresando Chile, Entel PCS, y too me pide un password pal modem y ahí keo ](*,)

4.- Intenté cambiar los DNS como ví por ahí en algún foro... y NO HAY CASO!!!

Situación Actual:

1.- Inserto el módem, luz roja, luz verde...
2.- Me aparece la "bendita" conexión a Entel PCS 
3.- PERO al tratar de conectar me aparece un mensaje de un password para el módem QUE NO CONOZCO!! 
4.- Llamé a Entel y me dicen "No la vamos a poder ayudar porque no prestamos soporte a ese sistema operativo linussssssss" (nótese las eses finales)


Weno y ahí quedé po!](*,)

POR FISSSS[-o< si alguien me puede ayudar se lo agradecería un montón!!! y como soy muy muy novata si me lo explican con manzanitas MEJOR!:oops:

---

### Post by asterix77 on 2010-02-10
Por lo que comentas, creo que estàs tratando de conectarte con network manager, que es la aplicaciòn por defecto en karmic.
 
Suponiendo que te conectas con network manager ¿cual es el mensaje específico que te aparece?¿algo relacionado con el "anillo de claves predeterminado"?, si es asì tienes que ingresar la clave de tu nombre de usuario con privilegios de root (la que usas cuando escribes sudo en la terminal).
 
De todos modos tipea en la consola lo siguiente para saber si te reconoce bien el modem (aunque creo que si está bien reconocido)
 
#lsusb
 
Pega acá el resultado.
 
 
Saludos

---

### Post by NOVATA1173 on 2010-02-10
Hola!!! Gracias por tu respuesta... lo del password que me pide no es el del anillo de redes, si no es esto: MOBILE BROADBAND NETWORK PASSWORD, a password is requiered to connect to 'Entel PCS default", ahi me keo... le ingreso cualkier cosa, y de ahi me pide el del anillo de redes le pongo DENY (no uso psw en el anillo, así me funciona con Wifi) y de ahi me dice que estoy OFFLINE :(

Lo que me pidiste que hiciera lo copio acá:

ubuntu@ubuntu:~$ lsusb

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 008: ID 0421:060e Nokia Mobile Phones 

Bus 001 Device 005: ID 05c8:0202 Cheng Uei Precision Industry Co., Ltd (Foxlink) 

Bus 001 Device 003: ID 0951:1607 Kingston Technology Data Traveler 2.0

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 003 Device 002: ID 13d3:3249 IMC Networks 

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Carlos C on 2010-02-11
Hola NOVATA1173. Por favor evita escribir con modismos o con "k", la idea es que utilices el castellano más neutro posible para que tus respuestas aparezcan al hacer búsquedas y además sean entendidas por personas de distintas procedencias. Antes de volver a publicar te pido que las [esto]("http://ubuntuforums.org/showthread.php?t=1162750").

Sobre tu problema:
> Después de copiar "cosas" en la Terminal y hacer "no sé que" logré que por lo menos el módem "funcionara" yo hasta ahí feliz! Aquí estamos un poco mal, porque es difícil ayudarte si no sabemos qué hiciste. Buscando con google descubrí que existe un paquete deb para ese modelo que lo proporciona nokia:

[http://europe.nokia.com/support/product-support/cs-10/software](http://europe.nokia.com/support/product-support/cs-10/software)

Descarga el archivo [Linux_2.10.zip]("http://europe.nokia.com/EUROPE_NOKIA_COM_3/Get_Support/Product_Support/Support_for_Accessories/IMAGING/Nokia_Internet_Stick_CS-10/linux_2.10.zip"). En su interior encontraras el paquete en cuestión.

Si lo anterior no es suficiente podemos intentar ayudarte con la solución que encontraste en ubuntuforums.

Saludos.

---

### Post by moreback on 2010-02-13
Puede ser que sea la password de la conexión de Entel, en cuyo caso debiera ser **entelpcs** (usuario y contraseña son iguales).

Lo otro podría ser que te pida el PIN o PUK, pero se supone que estos datos los puedes agregar a la conexión que ya quedó hecha en **Sistema -> Preferencias -> Conexiones de red**.

Saludos.

---

### Post by NOVATA1173 on 2010-02-14
Hola, gracias por las respuestas y disculpa por no escribir en español neutro, lo que pasa es que tengo tan arraigados mis modimos que no me doy ni cuenta.

Bueno, les comento que el .deb que indicas lo tenía instalado y por las dudas lo reinstalé, PERO sigue pidiendome el MOBILE BROADBAND NETWORK PASSWORD, intenté con entelpcs como me indica moreback pero tampoco funciona!!

¿Qué puede ser?¿Cómo puedo asegurarme que el hardware está bien instalado? Ojalá me puedan ayudar ya que no quiero depender de Windows sólo por el internet!

---

### Post by asterix77 on 2010-02-15
Prueba si esta solución arregla tu problema.

En resumen tienes que editar el archivo /etc/ppp/options, y luego deshabilitar la opción correspondiente en Network Manager

[http://ubuntuforums.org/showthread.php?t=1354619&page=2](http://ubuntuforums.org/showthread.php?t=1354619&page=2)

Saludos

---

### Post by NOVATA1173 on 2010-02-15
He probado de todo y no hay caso.... a ver si mañana con la asesoria de un amigo que conoce más de Linux puedo arreglarlo. Ahí les cuento como me va! 

Mañana publicaré todos los mensajes que me manda la terminal.

Gracias por las respuestas!!

---

### Post by moreback on 2010-02-15
¿Es prepago? ¿Le echaste platita?

---

### Post by asterix77 on 2010-02-16
Bueno, espero que puedas solucionar tu problema pronto. Lo bueno de linux, es que hay varias formas de poder solucionar un problema.
Si no te funciona el network manager, puedes intentar usando wvdial.
 
 
Saludos

---

### Post by CdK1 on 2010-02-16
Con esto, supongo/espero, bastará...

[https://bugs.launchpad.net/ubuntu/+bug/456162](https://bugs.launchpad.net/ubuntu/+bug/456162)
[http://forum.ubuntu-it.org/index.php?topic=343595.msg2740670](http://forum.ubuntu-it.org/index.php?topic=343595.msg2740670)


Sino, intentaría con usar un kernel anterior y/o version anterior de network-manager y seguir estos pasos: 

[http://crear-paginas-web.blogspot.com/2009/09/modem-3g-nokia-cs-10-en-ubuntu.html](http://crear-paginas-web.blogspot.com/2009/09/modem-3g-nokia-cs-10-en-ubuntu.html)

También podrías usar Wicd en vez de Netork-Manager...


[http://segvfault.wordpress.com](http://segvfault.wordpress.com)

---

### Post by kamus on 2010-02-19
Hola, al parecer ya lo solucionar en Karmic por lo que pude ver en [https://bugs.edge.launchpad.net/modemmanager/+bug/470728](https://bugs.edge.launchpad.net/modemmanager/+bug/470728) (incluye un parche) y según comenta el autor, saco todo desde [http://islascruz.org/html/index.php/blog/show/Nokia-Internet-Stick-CS-10-on-Linux.html](http://islascruz.org/html/index.php/blog/show/Nokia-Internet-Stick-CS-10-on-Linux.html) . 

Saludos

---

### Post by smo0th on 2010-06-03
> **kamus said:**
> Hola, al parecer ya lo solucionar en Karmic por lo que pude ver en [https://bugs.edge.launchpad.net/modemmanager/+bug/470728](https://bugs.edge.launchpad.net/modemmanager/+bug/470728) (incluye un parche) y según comenta el autor, saco todo desde [http://islascruz.org/html/index.php/blog/show/Nokia-Internet-Stick-CS-10-on-Linux.html](http://islascruz.org/html/index.php/blog/show/Nokia-Internet-Stick-CS-10-on-Linux.html) . 

Saludos

Confirmo que la solucion descrita en islacruz funciona a la perfeccion, usen sudo al ejecutar wvdial.

Salu2,

:guitar:

---

