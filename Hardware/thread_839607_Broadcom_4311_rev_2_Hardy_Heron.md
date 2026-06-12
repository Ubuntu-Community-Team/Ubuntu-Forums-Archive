---
title: "Broadcom 4311 rev 2 Hardy Heron"
date: 2008-06-24
forum: Hardware
---

### Post by Apipote on 2008-06-24
Pude instalar finalmente luego de actualizar los mas de 200 mb, los drivers de la broadcom en mi compaq f566la antilinux en Hardy.

Se prende la luz azul de la wifi, veo todas las conexiones perifericas a mi casa, incluso mi acces point con buena señal.

Pero no entiendo porque me conecto SIN actividad ( 0 % ) ,no anda internet y el pppoeconf se cuelga.

Si desconecto la wifi broadcom 4311, el pppoeconf...reconoce la ethernet y estoy escribiendo esto.

Es cosa de mandinga...ayudenme por favor !!

Ahhh, si booteo con xp anda todo perfecto.

Saludos y gracias

---

### Post by faktorqm on 2008-06-25
y mira, me da la sensacion de que estas teniendo ahi un router que ya esta conectado, entonces por ethernet pones dhcp, y ya salis con internet. ¿por que queres usar pppoeconf? contanos un poco mas sobre tu red, proveedor, si tenes modem adsl, router wi fi, todo junto, etc. Salu2!

---

### Post by Apipote on 2008-06-25
Desde la casa de un vecino recibe Millicom, y de ahi por medio de un mikrotic reparte. Si o si cada vecino tiene su name y password. O sea pppoe, asi anda en xp, y en ubuntu por ethernet.

Yo capto con un acces point como cliente conectado a una antena en mi techo, y de ahi baja un cable de red, que lo enchufo en otro acces point que actua como swich entre la pc y la notebook.

Con xp todo anda de maravillas.

Que me sugeris que haga para poder conectarme con ubuntu?

Porque se ven todas las conexiones de mis vecinos, incluso la mía pero me conecto ( wifi ) con NULA actividad.
Con ethernet todo bien.

Gracias

---

### Post by faktorqm on 2008-06-25
AHHHH VOS SOS EL DE LA ANTENA EN EL TECHO?!?!?!?!?

te estuve buscando....... cuando nos juntamos en abril para jugar al pool y tomar... ejem... digo, para festejar la aparicion de HH le pregunte a medio mundo si tenia una antena en el techo... y nadie respondio... jajaj

ahora que te encontre duermo mejor... bueno, para mi lo que tenes que hacer es lo siguiente, tirar en una consola:

```
sudo ifconfig eth0 down
```

para "dar de baja" la placa de red por cable, asumo que eth0 es la cableada y wlan0 es la wi-fi.

Entonces ahora le pones ip automatica a la wi-fi (de ser necesario ip pone ip, mascara y puerta de enlace SOLO, sin DNS) y ahi ejecutas el pppoeconf.
Cuando te pregunta por que placa queres que busque la conexion le pones wlan0 (no deberia aparecerte eth0, pero por las dudas...) y ahi configuras. si no te anda, asegurate de poner hacer ping a la puerta de enlace (router). esto lo haces con

```
ping -c 4 ip_de_la_puerta_De_enlace
```

si no llegas hasta ahi, tenes problemas con el wi-fi. si llegas y no te anda el pppoeconf, volve a postear. Para eso haces 

```
sudo ifconfig eth0 up
```

y lo vemos. Salu2!!

---

### Post by Apipote on 2008-06-25
> AHHHH VOS SOS EL DE LA ANTENA EN EL TECHO?!?!?!?!?
Si estimado...soy ese. De Cba Cap, detrás de la Fico.

Todo está en automático ( así lo manda el nodo de mi vecino ) en xp, y en Ubuntu en "roaming". Pero el pppoeconf si esta "activada" la placa wifi...no funca.

Voy a probar lo que vos me decis.

Abrazo.

---

### Post by Apipote on 2008-06-25
No nada che. pppoe escanea no encuentra nada, y termina con "timed Out". Si voy a la configuración manual de redes...adsl pppoe no ve mi wlan.

Sigo pensando que los drivers de los repositorios no sirven para una ******.

Me pueden dar un guia para bobos, para hacerla andar con Ndiswrapper por favor ??

Gracias.

---

### Post by faktorqm on 2008-06-26
Bue pero para, pusiste ip automatica, y pingueaste al gateway? esa es la prueba que te dice si el que no anda es el driver... vos pones ip automatica, y tu vecino te da una, entonces ahi haces ifconfig y te fijas que ip te dio. luego probas. cual es el problema de instalarla con ndiswrapper? si a los que les anda les anda bien creo que es la mejor solucion.. no? Salu2!!

---

### Post by Apipote on 2008-06-26
No me cierra el Ndiswrapper, pero lo voy a probar.

Tenes un tutorial de Ndiswrapper para novatos?

Gracias.

---

### Post by faktorqm on 2008-06-27
La verdad que no, pero empece a buscar para darte uno y me topé con esto:

> **Ayuthia said:**
> 
Chipsets known not to be working in Ubuntu with b43/b43legacy(you can check by typing lspci -nn at the terminal):
14e4:4311 rev 01
14e4:4312 rev 02
From what I understand, there was a patch applied right before the Hardy release that fixed them, but it broke most of the other ones! From what I understand the developers for the b43/b43legacy drivers have it fixed in the 2.6.25 kernel. For those who are brave, you can go to their site ([http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)) and try to patch it on your own


lo leiste? (está en inglés) pero ahi dice que tu placa supuestamente esta soportada por los releases de los drivers libres, o sea que no hace falta ir al ndiswrapper. 

Ahi dice: 

Chipsets conocidos que no funcionan en ubuntu con el driver b43/b43legacy (podes chequear esto poniendo "lspci -nn" en la terminal):

14e4:4311 rev 01
14e4:4312 rev 02

Por lo que yo entiendo, hubo un parche aplicado antes de la salida de Hardy que lo arreglaba, pero rompia la mayoria de las otras! Por lo que tengo entendido, los desarrolladores de los drivers b43/b43legacy lo arreglaron en el kernel 2.6.25. Para los que son valientes, pueden ir al sitio de ellos [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) y probar de parchearlo vos mismo.

Bueno la cosa es que me gustaria que antes de morir en el ndiswrapper pruebes lo de la pagina, lo lei y la verdad no es dificil, asi que te invitaria a que vayas y hagas las cosas que proponen ahi (ojo con la version del kernel) y si no te anda nada te vamos ayudando a ver si de una vez por todas hacemos andar esa placa. Salu2!!!!

---

### Post by Apipote on 2008-06-27
Bueno, finalmente anda con Ndiswrapper. Te escribo por wifi.
Veremos que pasa en Hardy.

Gracias Faktorqm !!!!!!!!

---

