---
title: "wifi no funciona"
date: 2012-01-23
forum: Hardware
---

### Post by capcabgue on 2012-01-23
Hola: les cuento tengo un Dell inspiron 1525, con ubuntu 11.10.
Desde que hice la actualización a Ubuntu 11.04 no ha funcionado bien el internet inalambrico no mejoró gran cosa al instalar el 11.10 en noviembre (pensé que podía ser porque tengo mi switch dlink en el canal 6).
Bueno desde hace 1 semana no veo ninguna red wifi y si la agrego manualmente no sucede nada.
Sin embargo ve el HW, pero no tengo idea de como se puede solucionar esto, alguien me puede ayudar, les dejo lo que me arroja si hago un ifconfig -a

eth1      Link encap:Ethernet  HWaddr 00:22:5f:46:1c:97  
          inet6 addr: fe80::222:5fff:fe46:1c97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 


Gracias y en verdad espero que alguien me pueda ayudar

---

### Post by Kobin on 2012-01-23
Este es un mensaje de google traducido: Puede usted por favor enviar el resultado de la siguiente en una terminal

```
lspci
```

Yo he visto aquí que al menos algunos Dell Inspiron 1525 tiene las siguientes controlador de wifi:

Dell Wireless 1390 
[http://reviews.cnet.com/laptops/dell-inspiron-1525/4507-3121_7-32814939.html]("http://reviews.cnet.com/laptops/dell-inspiron-1525/4507-3121_7-32814939.html")

lspci debe mostrar un controlador Broadcom wifi.

Si el equipo tiene este controlador de wifi puedes probar con los consejos que se dan aquí:

[http://ubuntuforums.org/showthread.php?t=1861669]("http://ubuntuforums.org/showthread.php?t=1861669")

---

### Post by 3nG3ndR0 on 2012-01-24
> **capcabgue said:**
> Hola: les cuento tengo un Dell inspiron 1525, con ubuntu 11.10.
Desde que hice la actualización a Ubuntu 11.04 no ha funcionado bien el internet inalambrico no mejoró gran cosa al instalar el 11.10 en noviembre (pensé que podía ser porque tengo mi switch dlink en el canal 6).
Bueno desde hace 1 semana no veo ninguna red wifi y si la agrego manualmente no sucede nada.
Sin embargo ve el HW, pero no tengo idea de como se puede solucionar esto, alguien me puede ayudar, les dejo lo que me arroja si hago un ifconfig -a

eth1      Link encap:Ethernet  HWaddr 00:22:5f:46:1c:97  
          inet6 addr: fe80::222:5fff:fe46:1c97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 


Gracias y en verdad espero que alguien me pueda ayudar

coloca esto en la terminal para saber que controlador wireless tiene tu equipo

```
lspci | grep Wireless

```

como cosa aparte, yo siempre e instalado en 0 al cambiar de versión de Ubuntu par no tener problemas, lo mas conveniente es tener la ~HOME en una partición separada del / sistema de archivos

---

### Post by capcabgue on 2012-01-24
> **3nG3ndR0 said:**
> coloca esto en la terminal para saber que controlador wireless tiene tu equipo

```
lspci | grep Wireless

```como cosa aparte, yo siempre e instalado en 0 al cambiar de versión de Ubuntu par no tener problemas, lo mas conveniente es tener la ~HOME en una partición separada del / sistema de archivos
PLOP!!!

No me arroja ningun controlador, al apretar enter, vuelve a salir el cursor (no me indica nada.
Sin embargo puse en el terminal lspci y me dio esto (creía que era el controlador de mi tarjeta wifi):
Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

Como le instalo el driver, al hacer correr el additional drivers, me indica :
Broadcom STA wirless driver esta actualmente en uso.

Por otra parte si hago un ifconfig, me reconoce el eth1 (el wireless).

Gracias y en verdad hoy ni sospecho como lo puedo solucionar.

Gracias por el consejo de como instalar Ubuntu y efectivamente tengo separado el home, uno para los archivos de sistema, otro para la swap y finalmente uno por intercambio con malous.

---

### Post by moreback on 2012-01-25
Esos drivers "Broadcom STA" nunca me dieron buenos resultados cuando tenía una tarjeta de esas. Trata mejor de instalar el que usa ndiswrapper (o algo así).

---

### Post by capcabgue on 2012-01-26
> **moreback said:**
> Esos drivers "Broadcom STA" nunca me dieron buenos resultados cuando tenía una tarjeta de esas. Trata mejor de instalar el que usa ndiswrapper (o algo así).
mmmm. Como lo hago, es decir como averiguo cual es realmente mi hardware, ya que aún navegar por wifi es notoriamente más lento (youtube se abre casi con 1 o más de espera) que por cable (youtube  no se demora ni siquiera 10 sec).

Bueno el problema que tenía, era quee  mi hijo me había apagado la antena (lo encendí y ahora funcionó (capa 1)

---

### Post by capcabgue on 2012-01-28
Les cuento, estuve googleando bastante y encontre en un foro que aqui se arreglaba mi problema, sin embargo no había que olvidar leer el archivo readme.txt y que se visitara esta página [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Bueno al leer el readme, indicaba que efectivamente venía instalado el broadcom (driver de mi notebook) en la versión de Ubuntu, pero que algunas veces falla. La solución hacer un update y reinstalar el driver y reiniciar el pc.

Dejo los comandos para si alguien tiene el mismo problema:

From the shell:
sudo apt-get update sudo apt-get --reinstall install bcmwl-kernel-source  In either GUI or text case, after reinstalling, reboot your machine.  Now go back to System->Administration->Hardware Drivers and you should see the driver enabled and working.
En mi caso esta reconocido el driver STA, pero esta vez mejoro la velocidad por internet

---

