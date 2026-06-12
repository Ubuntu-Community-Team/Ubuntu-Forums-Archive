---
title: "Compartir coneccion"
date: 2009-06-01
forum: Hardware
---

### Post by matitoro on 2009-06-01
Hola soy nuevo me llamo matias,acabo de instalar Ubuntu en mi pc,estoy muy contento por el rendimiento q tengo.
Bueno a ver si me pueden ayudar,tengo coneccion adsl Arnet q configure por medio de pppoeconf,la coneccion anda de 10 mucho mas rapido q con wi....,pero no logro compartir internet a la notebook de mi mama q tiene win,les comento como tengo todo ,modem tainet viejito ,el modem usa una placa de red,y la otra la uso para darle internet a la notebook,.

Bueno desde ya muchas gracias por el espacio.

---

### Post by guillermolisi on 2009-06-01
> **matitoro said:**
> Hola soy nuevo me llamo matias,acabo de instalar Ubuntu en mi pc,estoy muy contento por el rendimiento q tengo.
Bueno a ver si me pueden ayudar,tengo coneccion adsl Arnet q configure por medio de pppoeconf,la coneccion anda de 10 mucho mas rapido q con wi....,pero no logro compartir internet a la notebook de mi mama q tiene win,les comento como tengo todo ,modem tainet viejito ,el modem usa una placa de red,y la otra la uso para darle internet a la notebook,.

Bueno desde ya muchas gracias por el espacio.
Pega en un mensaje la salida de ```
ifconfig
``` en Ubuntu e ```
ipconfig
``` en Win.

Las dos maquinas deberian estar en la misma red y la notebook deberia tener como default gateway la IP del modem/router al igual que la PC. Esto para empezar.

Bienvenido.

---

### Post by matitoro on 2009-06-01
pruebo y te comento gracias por ahora
;)

---

### Post by matitoro on 2009-06-01
no tiene la misma ip :S

---

### Post by guillermolisi on 2009-06-01
> **matitoro said:**
> no tiene la misma ip :S
Y si pegas las salidas de esos comandos que te pase ?

En ubuntu se corre en una terminal/consola y en Windows en una sesion DOS (Inicio - Ejecutar - cmd)

---

### Post by staar on 2009-06-01
siendo nuevo, lo más recomendable es que uses firestarter (buscalo en Synaptic), un frontend para el firewall de linux, que te permite compartir el internet con un asistente muy sencillo...

lo necesario para que esto funcione es tener la red entre ambas pc, configurada con ip fijas (obvio que dentro del mismo rango, por ej. 192.168.x.x) y, en la pc con windos, configurar como gateway (puerta de enlace) la ip de la máquina con ubuntu, y los dns que uses...

saludos

---

### Post by matitoro on 2009-06-02
> **staar said:**
> siendo nuevo, lo más recomendable es que uses firestarter (buscalo en Synaptic), un frontend para el firewall de linux, que te permite compartir el internet con un asistente muy sencillo...

lo necesario para que esto funcione es tener la red entre ambas pc, configurada con ip fijas (obvio que dentro del mismo rango, por ej. 192.168.x.x) y, en la pc con windos, configurar como gateway (puerta de enlace) la ip de la máquina con ubuntu, y los dns que uses...

saludos
voy a probar con el firestart,despues comento como me fue,muchas gracias

---

### Post by guillermolisi on 2009-06-02
> **matitoro said:**
> voy a probar con el firestart,despues comento como me fue,muchas gracias
Nunca esta de mas darle una leida a su manual antes de ponerse a experimentar (hasta ahora solo lo vi en Ingles. No se si alguien ha hecho una traduccion).

---

### Post by matitoro on 2009-06-02
> **guillermolisi said:**
> Nunca esta de mas darle una leida a su manual antes de ponerse a experimentar (hasta ahora solo lo vi en Ingles. No se si alguien ha hecho una traduccion).
No me funca che,lo configuro y me dice q no esta conectado probe de mil maneras con firestar no se q voy hacer,seguire probando gracias.

---

### Post by guillermolisi on 2009-06-02
> **matitoro said:**
> No me funca che,lo configuro y me dice q no esta conectado probe de mil maneras con firestar no se q voy hacer,seguire probando gracias.
No te enojes (no habria razon para ello pero lo digo por las dudas) pero lo primero que te sugiero es que leas bien los mensajes que se cursaron en este thread.

Te sugeri que envies las salidas de dos comandos, uno en Linux y otro en Win, para saber de primera mano y a ciencia cierta como tenes configuradas las maquinas y establecer con ello un punto de partida solido.

Si no tenes resuelto el tema de la red, a nivel fisico y/o de IPs, en nada te ayudaran Firestarter o similares.

---

### Post by matitoro on 2009-06-02
> **guillermolisi said:**
> No te enojes (no habria razon para ello pero lo digo por las dudas) pero lo primero que te sugiero es que leas bien los mensajes que se cursaron en este thread.

Te sugeri que envies las salidas de dos comandos, uno en Linux y otro en Win, para saber de primera mano y a ciencia cierta como tenes configuradas las maquinas y establecer con ello un punto de partida solido.

Si no tenes resuelto el tema de la red, a nivel fisico y/o de IPs, en nada te ayudaran Firestarter o similares.

por favor como me voy a enojar si me estan ayudando,desde ya les agradesco por bancarme lo hincha q soy jaja,bueno me voy a fijar y te digo gracias por ahora estoy muy contento,por la comunidad y por el SO.

---

### Post by totolinux on 2009-06-03
hola en este tópico ya fue resuelto 
[http://ubuntuforums.org/showthread.php?t=1036910&highlight](http://ubuntuforums.org/showthread.php?t=1036910&highlight)
suerte 
PD me refiero a la config de firestarter

---

### Post by matitoro on 2009-06-03
> **totolinux said:**
> hola en este tópico ya fue resuelto 
[http://ubuntuforums.org/showthread.php?t=1036910&highlight](http://ubuntuforums.org/showthread.php?t=1036910&highlight)
suerte 
PD me refiero a la config de firestarter

buen dato pruebo y comento gracias

---

### Post by matitoro on 2009-06-03
> **matitoro said:**
> buen dato pruebo y comento gracias

Me parece q me voy a comprar un router cable derecho y a la merda valen 39 dolares q opinan?

---

### Post by josecuervo86 on 2009-06-03
Antes de andar comprando cosas que tal vez no necesites seria bueno que pruebes los comandos que te recomendo Guillermo. Si no sabes como hacerlo, pregunta que seguro alguien te va a indicar como lograrlo ;)

---

### Post by matitoro on 2009-06-03
> **josecuervo86 said:**
> Antes de andar comprando cosas que tal vez no necesites seria bueno que pruebes los comandos que te recomendo Guillermo. Si no sabes como hacerlo, pregunta que seguro alguien te va a indicar como lograrlo ;)

[ [IMG]http://www.subiimagenes.com/thumbnails/513539ad86aaf66f512f763dc2cf2a35.png[/IMG]]("http://www.subiimagenes.com/show-image.php?id=b9ad682ad30c7590cfc0f28580bd678c")

puse ifconfig y me aparece asi .

---

### Post by guillermolisi on 2009-06-03
> **matitoro said:**
> [ [IMG]http://www.subiimagenes.com/thumbnails/513539ad86aaf66f512f763dc2cf2a35.png[/IMG]]("http://www.subiimagenes.com/show-image.php?id=b9ad682ad30c7590cfc0f28580bd678c")

puse ifconfig y me aparece asi .

Esa es la salida de ifconfig, en Ubuntu. Falta la salida de ipconfig en Windows.

---

### Post by matitoro on 2009-06-03
> **guillermolisi said:**
> Esa es la salida de ifconfig, en Ubuntu. Falta la salida de ipconfig en Windows.
 
ahi va guille eso aparece en la notebook de mi vieja 
 
[URL="http://www.imaxenes.com/imagen/untitled1vh65y7.png.html"]
[/URL]

---

