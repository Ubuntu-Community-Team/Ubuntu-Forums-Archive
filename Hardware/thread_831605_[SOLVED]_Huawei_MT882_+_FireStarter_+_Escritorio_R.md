---
title: "[SOLVED] Huawei MT882 + FireStarter + Escritorio Remoto"
date: 2008-06-17
forum: Hardware
---

### Post by User21 on 2008-06-17
Poseo una conexion ADSL de 1mbps de Arnet, con el modem Huawei MT882 SmartAX via ethernet. A su vez, comparto Internet con una pc con Win via FireStarter. Uso el servicio de DYNDNS.org para redireccionar mi IP a un DNS con ddclient corriendo como servicio en mi PC. 

Puedo ingresar remotamente, usando mi direccion IP, pero no desde el DNS. Ddclient o le da una IP erronea, o lo redirecciona a la pagina de settings de mi modem, lo que a mi entender, es PELIGROSO!

Alguien tiene el mismo perfil de uso? Como lo resolvio?

---

### Post by faktorqm on 2008-06-17
No entendi nada de lo que pusiste. Creo que estas super confundido. Primero, pusiste una pagina web en tu pc? O sea, cuando decis que queres entrar desde afuera y te redirecciona a la ip del modem, a donde te queres conectar vos? Digamos, no es tan descabellado eso (en realidad acabas de descubrir que te olvidaste de deshabilitarle el acceso remoto al modem lo cual ya era un problema de antes), pero si queres que te redireccione a tu pagina web deberias primero de haber instalado un apache o algun servidor web en tu linux, luego redireccionar el puerto 80 en el modem a tu ip y recien ahi te estarias conectando.
Si no queres esto e instalaste algun tipo de vnc o terminal server, primero te tenes que conectar a tu ip, redireccionar tambien el puerto en el modem. Conta que quisiste inventar. Salu2!

---

### Post by User21 on 2008-06-17
No, no tengo ni pagina web, ni servidor apache ni patatin, ni patatan, ni nada por el estilo. Simplemente quiero tener acceso remoto a escritorio via vncviewer, desde afuera. 
No puedo ingresar al pc por escritorio remoto desde afuera! Es el firestarter? Es el modem? Debo abrir puertos en Firestarter? Modificar algo en los settings del modem? Como acceden los que usan este modem?
 No, no quiero SSH. Solo quiero acceder remotamente a mi equipo, ver las X, como solia hacer con mi anterior conexion en Fibertel.

---

### Post by faktorqm on 2008-06-17
Y bueno, te tenes que instalar el vnc server. Leete alguna guia para que no te lo hackeen 10 veces por segundo. Una vez configurado, te fijas por que puerto escucha el vnc. supongamos que es el 12345. Entras al modem de asdl, BLOQUEAS EL ACCESO EXTERNO, despues vas a la tabla nat y le decis, que todo lo que entre por el puerto (podes elegir el que mas te guste a vos, por ejemplo 9876) 9876 lo tire al 192.168.1.2 puerto 12345. (192.168.1.2 tiene que ser el ip de tu compu, tengo entendido que no podes usar dhcp) 
Entonces ahora vas a una pc desde afuera, y conectas el vnc cliente a la direccion que te da dyndns al puerto 9876. y ahi deberias poder jugar tranquilo con tu conexion. Cualquier duda pregunta. Salu2!

---

### Post by User21 on 2008-06-17
Voy a probar! Pero pensé, que Ubuntu ya tenia una especie de servidor de vnc al activar las opciones de Escritorio Remoto, en Sistema, Preferencias. En fin, vere que sale esta misma tarde.

---

### Post by faktorqm on 2008-06-17
y..... no se en realidad, proba de conectarte al puerto 5900. Lo que tendrias que hacer es, ir al modem, redireccionar el puerto que mas te guste (tomo por ejemplo 12345, o tambien podes tomar el mismo) a la ip de tu compu, puerto 5900, y desde afuera entrar a nombre_dyndns:12345 ó nombre_dyndns:5900. De todas maneras te recomiendo cambiar el numero de puerto.

Y ahi probar con un cliente vnc a ver que pasa, si no conecta, primero intenta ver que demonios tenes corriendo a ver que servidor es. Salu2!

---

### Post by Mister X on 2008-06-17
> **User21 said:**
> Voy a probar! Pero pensé, que Ubuntu ya tenia una especie de servidor de vnc al activar las opciones de Escritorio Remoto, en Sistema, Preferencias. En fin, vere que sale esta misma tarde.

Exacto, por defecto viene un servidor instalado (vino-session), y tenes que activarlo desde tu usuario. Tené en cuenta que es un servicio que funciona a nivel de usuario, por lo que para conectarte remotamente la sesion debe estar iniciada.

Tenes otras opciones, como establecer una sesion X remota, acordate que las X estan basadas en un sistema cliente-servidor, hacer esto es mucho mas versatil que con vnc y mas divertido :p

---

### Post by Hei Ku on 2008-06-17
podes instalar el x11-vnc, pero acordate de setearle una contraseña, y en lo posible cambiarle el puerto a otro que no sea el default.
pero primero que nada tenes que redirigirlo el puerto en tu modem, porque si no, no vas a pasar de ahi.

---

### Post by User21 on 2008-06-18
Resolví lo del escritorio remoto. Ya tengo acceso desde el exterior. De todas formas, es el **ddclient** el cual no actualiza mi IP apropiadamente en DYNDNS.org ! 
Al parecer, eth0, el cual es usado por el módem, asume como IP 10.0.0.3 y ddclient no envía la dirección Ip de Inet a DYNDNS...

---

### Post by Hei Ku on 2008-06-18
Fijate que el ddclient tiene una opcion web, que indica que le tiene q asignar la IP que da a internet. Ahora no encuentro donde esta el archivo de configuracion, pero recuerdo que tambien tuve ese problema, porque tengo un router, y lo resolvi con esa opcion.

---

### Post by User21 on 2008-06-19
Muchas gracias, Hei Ku! Logré configurarlo con la opción web. Editando el /etc/ddclient.conf de la siguiente forma:

```
# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf

pid=/var/run/ddclient.pid 
protocol=dyndns2
# En la linea siguiente cambie la orden anterior (use=if, if=eth0)
use=web
server=members.dyndns.org
login=TuUsuario
password='ContraSeña'
TuDNS.dyndns.org
```Una vez guardado el archivo, reinicié el ddclient con ```
sudo /etc/init.d/ddclient restart
``` y MAGIA! Ya obtenía la IP correcta, la cual es detectada desde el sitio de DYNDNS.org. 
Aparentemente, usando el enfoque de detección de IP desde DYNDNS.org, se debería resolver cualquier problema de router o módem, ya que se asigna TU IP en Internet, mas allá de cualquier dispositivo! Lo siguiente es tener en claro para qué aplicación vamos a usar este DNS dinámico, y qué puertos deben estar abiertos para su normal comunicación con el exterior. :)

---

