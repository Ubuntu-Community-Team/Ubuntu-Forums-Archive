---
title: "Problema con Wireless Broadcom 4311 Jaunty"
date: 2009-06-14
forum: Hardware
---

### Post by Black-Knight on 2009-06-14
Antes que todo quero decir que soy UN FISH no cacho nada.
Buenas tengo Ubuntu 9.04 y una tarjeta de wireles Broadcom 4311.
El controlador de la broadcom esta activado y todo de hecho me encuentra redes alrededor , pero al momento de querer conectarme a mi red me pide la contraseña y todo pero sale como que se esta conectando y no se conecta y me vuelve a pedir la contraseña ( se que esa es la contraseña correcta) y luego me intente conectar a una red abierta y no me pesca tampoco 
puse iwconfig y por si aporta algo dejo esto

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:163
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.



pd: que es pan0 ??

---

### Post by Patriciologico on 2009-06-14
> **Black-Knight said:**
> pd: que es pan0 ??

Entiendo que es Personal Area Network creada por los enlaces Bluetooth

¿tienes Bluetooth?

Respecto al problema ¿lograste alguna vez conectarte a una red o nunca ha funcionado?

Pregunto por habia leido que en las versiones de Linux, a esa broadcom le instalaban el driver de Windows via ndiswrapper y no se si Jaunty ya la reconoce por completo.

Saludos

Pd ¿Puedes editar el titulo del Thread para que sea mas descriptivo agregando Broadcom 4311 en Jaunty?

---

### Post by Black-Knight on 2009-06-14
en estricto rigor si tiene para bluetooth pero nunca lo eh ocupado ni configurado :)

y antes si me habia podido conectar por la wireles y no tenia problemas , solo oidia no se que hice que no se puede conectar a nada ahora.
Gracias por estar atento para ayudarme :)

---

### Post by Patriciologico on 2009-06-14
Agregue algunas preguntas al post anterior, este es para que te llegue el mail y me las respondas y sigamos avanzando:)

---

### Post by Patriciologico on 2009-06-14
Prueba lo siguiente. 


```
sudo ifconfig eth1 up
sudo iwconfig eth1 essid elnombredelaESSID
sudo iwconfig eth1 key s:lacontraseña
sudo dhclient eth1
```

---

### Post by Black-Knight on 2009-06-14
Hice lo que me dijiste pero luego de ingresar la contraseña me salio esto

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Invalid argument.

algun otro comando para ingresar ?

---

### Post by Patriciologico on 2009-06-14
```
cat /etc/network/interfaces
```

Que muestra eso?

que tipo de clave usa tu red?

---

### Post by Black-Knight on 2009-06-14
cat /etc/network/interfaces 
auto lo
iface lo inet loopback

eso sale 
y la seguridad de mi red es WPA..

---

### Post by Carlos C on 2009-06-14
No sé si esto sirva para algo, pero yo verificaría que el paquete wpasupplicant esté instalado y probaría usando wicd para administrar mis conexiones wifi. Pero, insisto, no estoy seguro de que sea la solución.

---

### Post by moreback on 2009-06-14
Si es WPA creo que la cosa va por wpa_supplicant.

---

### Post by Jonathan Dud Rodriguez on 2009-06-15
llegas al router inalambrico con un ping?

cuando pasa eso de no concectarse a internet es por tema de clave de encriptacion erronea...

probaste la configuracion del router?
chekeaste que tengas la coneccion automatica por DCHP?


saludos

---

### Post by Black-Knight on 2009-06-21
claramente el router esta bien configurado si me conecto desde xp y mi hmna tambien por lo demas con cable de red configure el router bien 
el problema como dije es la Broadcom.
y con wicd como me sugirieron no me pude conectar viendo todo.
como dicen debe ser wpa_supplicant , pero busque en google
y segun veo no tengo nada parecido a las config que aparecen por lo demas
como dije anteriormente no me manejo mucho :S
asi que yo cacho que mañana formateo :P! me aburri de estar por cable de red
o a ver si encuentro algo por internet que me sirva

---

### Post by Carlos C on 2009-06-22
Antes de formatear verifica que el módulo b43 esté instalado. Escribe por favor en el terminal:
```
lsmod| grep b43
```
y dinos qué te sale. En caso de que el módulo no esté cargado lo cargas:
```
sudo modprobe b43
```
En caso de que no sea lo anterior ve a Sistema-->Administración-->Gestor de paquete synaptic. Has click en "Buscar" y busca el paquete "wpasupplicant". Si no está instalado lo instalas.
Estas son algunas cosas que verificaría antes de hacer algo tan drástico como formatear.
Saludos.

---

