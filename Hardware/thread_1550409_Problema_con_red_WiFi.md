---
title: "Problema con red WiFi"
date: 2010-08-11
forum: Hardware
---

### Post by Deathster on 2010-08-11
Hola, primero me presento pues soy nuevo en el foro, soy Gabriel y además de ser nuevo en la comunidad, soy nuevo en Ubuntu.

Mi problema: hace poco instalé Ubuntu 10.04 e inmediatamente traté de conectarme a mi red WiFi (con ISP VTR) y no me reconocía red alguna, así pues averigüé un poco y resulta que **al parecer** no tengo instalados los drivers de la tarjeta de red, por lo que intenté correr desde el CD de Ubuntu los drivers (me lo recomendó un amigo) y no funcionó, traté de correr algunos comandos que encontré en Internet y nada resultó. Es por esto que les pido su ayuda.

¡Gracias!.

Saludos.

PS: tengo un Lenovo G450, y pareciera ser que mi tarjeta de red es broadcom.

---

### Post by themasterdark on 2010-08-11
Hola intenta con lo siguiente (debes tener conectado a internet tu notebook, por cable de red ya que tu inalambrica esta sin funcionamiento por ahora)

ve a administracion -> controladores de hardware

en caso de mostrar algun controlador disponible habilitalo, quizas muestre dos controladores para tu inalambrica broadcom, uno sta y otro libre te recomiendo actives el libre ya que a mi almenos me funciona mucho mejor, bueno debes estar conectado a internet ya que descarga los paquetes necesarios desde la net.

Saludos =)

---

### Post by andrestester on 2010-08-12
hola que tal .
 
yo tenia el mismo problema y esto es lo que me recomendaron y funciono muy bien.
 
```
http://ubuntuforums.org/showthread.php?t=1535094
```
 
saludos..

---

### Post by Deathster on 2010-08-14
Gracias muchachos, lamentablemente por tiempo no he podido probar las soluciones, pero a penas pueda (yo creo que mañana) voy a intentar y comento.

Saludos.

---

### Post by Deathster on 2010-08-21
Muchachos, conecté el cable de red a mi PC con Ubuntu corriendo y tampoco me pescó, es decir, detectaba una conexión cableada llamada "Auto eth0" o algo así y no lograba conectar...¿que puedo hacer?.

Saludos.

---

### Post by Carlos C on 2010-08-23
[http://ubuntuforums.org/showthread.php?t=1410957](http://ubuntuforums.org/showthread.php?t=1410957)

---

### Post by Deathster on 2010-10-12
Bueno por fin lo arreglé, no sé exactamente que pasó, pero conecté el cable de red al laptop y me conecté a Internet, luego me preguntó el mismo SO por la Broadcom que no estaba siendo utilizada y que no había driver open source para ella, por esto ofrecía un driver no-open source que servía, y listo.

Saludos y muchas gracias.

---

