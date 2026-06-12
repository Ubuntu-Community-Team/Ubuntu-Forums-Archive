---
title: "wifi led en Acer Aspire"
date: 2008-11-15
forum: Hardware
---

### Post by sitiomatic on 2008-11-15
Para los que tienen una Acer y lograron hacer andar el wifi pero no enciende el led que muestra la conexion y el trafico, encontre unas instrucciones para una Aspire One y lo probe en mi notebook que es una 5315 y anduvo, por lo que pienso que debe andar en varios modelos de Aspire.
El tema es agregar lo siguiente en /etc/sysctl.conf
# Led Wifi
dev.wifi0.ledpin=3
dev.wifi0.softled=1

Hoy estuve en el Festival de Fallas. Gracias a los chicos de Ubuntu-ar que ubicaron donde poner esas instrucciones ya que yo no tenia ni idea.

Saludos
Sergio

---

### Post by luks911 on 2008-11-16
También me está funcionando en una Compaq Presario F754la con un chip Atheros AR5007EG y el driver Madwifi. 

Comento que usaba el driver ath5k que viene en el paquete linux-backports-modules-intrepid y con el que mi wifi funciona. Con ese driver el dispositivo de red se llama wlan0. Probé de hacer la modificación sugerida por sitiomatic en el archivo sysctl.conf y la luz seguía sin funcionar. También intenté reemplazando wifi0 por wlan0 en el archivo, pero no hubo caso.
Hoy cambié el driver por el madwifi (noté que con el anterior la conexión se interrumpía tras cierto tiempo de inactividad de la máquina, lo cual me cortaba la descarga de torrents y la conexión al aMSN, por ejemplo) y ahora con la modificación del sysctl.conf el led cambia de naranja a azul. Si ahora deja de cortarse la conexión seré feliz del todo, je.

Saludos y gracias

---

### Post by z37a on 2008-11-16
> **sitiomatic said:**
> Para los que tienen una Acer y lograron hacer andar el wifi pero no enciende el led que muestra la conexion y el trafico, encontre unas instrucciones para una Aspire One y lo probe en mi notebook que es una 5315 y anduvo, por lo que pienso que debe andar en varios modelos de Aspire.
El tema es agregar lo siguiente en /etc/sysctl.conf
# Led Wifi
dev.wifi0.ledpin=3
dev.wifi0.softled=1

Hoy estuve en el Festival de Fallas. Gracias a los chicos de Ubuntu-ar que ubicaron donde poner esas instrucciones ya que yo no tenia ni idea.

Saludos
Sergio

Gracias, funciono de 10 esto, la verdad nunca me preocupe pro que no funcionara, pero vii esto y lo probe y bue funciono, asi que comento que funciona perfecto con una laptop Acer Aspire 5310 - 2054

---

### Post by vk-cdg on 2008-11-16
> **luks911 said:**
> También me está funcionando en una Compaq Presario F754la con un chip Atheros AR5007EG y el driver Madwifi. 

Comento que usaba el driver ath5k que viene en el paquete linux-backports-modules-intrepid y con el que mi wifi funciona. Con ese driver el dispositivo de red se llama wlan0. Probé de hacer la modificación sugerida por sitiomatic en el archivo sysctl.conf y la luz seguía sin funcionar. También intenté reemplazando wifi0 por wlan0 en el archivo, pero no hubo caso.
Hoy cambié el driver por el madwifi (noté que con el anterior la conexión se interrumpía tras cierto tiempo de inactividad de la máquina, lo cual me cortaba la descarga de torrents y la conexión al aMSN, por ejemplo) y ahora con la modificación del sysctl.conf el led cambia de naranja a azul. Si ahora deja de cortarse la conexión seré feliz del todo, je.

Saludos y gracias


Epa epa! que buena noticia!
Que driver nuevo instalaste? Yo tengo instalado este:

```
madwifi-hal-0.10.5.6-r3835-20080801
```


Ya me pongo a hacer la modificación para ver si anda!

---

### Post by luks911 on 2008-11-16
> **vk-cdg said:**
> Epa epa! que buena noticia!
Que driver nuevo instalaste? Yo tengo instalado este:

```
madwifi-hal-0.10.5.6-r3835-20080801
```


Ya me pongo a hacer la modificación para ver si anda!

Yo tengo el madwifi-hal-0.10.5.6-r3875-20081105, que es un poco más nuevo, pero porque lo instalé hoy y estaba ese. Supongo que debería funcionar de todos modos con el que tenés vos.
Y parece que el problema que tenía con la conexión era culpa del ath5k. Con el madwifi todo indica que no se corta.

:lolflag:

Ah, algo que me olvidaba: para probar el cambio sin reiniciar hay que ejecutar

```
sudo sysctl -p /etc/sysctl.conf
```

para recargar el archivo.

---

### Post by sitiomatic on 2008-11-16
Yo estoy usando madwifi-ng-r3366+ar5007
Me alegro que les funcione :)
Saludos
Sergio

---

### Post by vk-cdg on 2008-11-16
> **luks911 said:**
> 

Ah, algo que me olvidaba: para probar el cambio sin reiniciar hay que ejecutar

```
sudo sysctl -p /etc/sysctl.conf
```

para recargar el archivo.

Hice lo que vos pusiste acá arriba (luego de modificar el archivo con esas 3 lineas) y ahora me queda titilando entre rojo y azul.
Voy a ver de reiniciar a ver que pasa.

---

### Post by luks911 on 2008-11-16
A mí también, eh. Pero entiendo que se pone en azul cuando transmite y en naranja cuando no. Yo creía que esa era la idea. ¿No es? :confused:

Bueh, seguí metiendo mano. Si cambias el priemr valor de 3 a 2, se queda azul como querés. Tiene que quedar así:
```
dev.wifi0.ledpin=2
dev.wifi0.softled=1
```

La "ventaja" de que titile es que si se cae la conexión podés verlo a la distancia :-P

---

### Post by vk-cdg on 2008-11-16
Releyendo el post veo que lo que dice es justamente lo que vos comentás. Pero en mi lectura rápida (estoy tratando al mismo tiempo de estudiar para un parcial de java) entendí que quedaba como funciona en Vi$ta, es decir cuando está encendida queda en azul fijo. 

Creo que me gusta mas como está ahora... es como mas útil!

---

### Post by faktorqm on 2008-11-16
Esaaaa!!! Gracias Sergio por comentarlo acá en el foro! Un grosso! Ojala nos volvamos a ver en el proximo festival. Salu2!!!

---

### Post by lega on 2008-11-16
bueno bueno al fin la lucecita azul! :) gracias,lo voy a probar sale estrellita!

---

### Post by vk-cdg on 2008-11-17
Eso, sale estrellita!

Gracias miles!

---

### Post by benjamin_linux on 2008-11-21
Hola,

tengo una Compaq f754, por lo que debería funcionarme, pero no lo hace. 

Me dice 

seretur@dendro:~$ sudo sysctl -p /etc/sysctl.conf
error: "dev.wifi0.ledpin" is an unknown key
error: "dev.wifi0.softled" is an unknown key

Intrepid me detectó la placa Atheros automáticamente, ¿saben qué tengo que modificar para que me funcione el led?

---

### Post by luks911 on 2008-11-21
> **benjamin_linux said:**
> Hola,

tengo una Compaq f754, por lo que debería funcionarme, pero no lo hace. 

Me dice 

seretur@dendro:~$ sudo sysctl -p /etc/sysctl.conf
error: "dev.wifi0.ledpin" is an unknown key
error: "dev.wifi0.softled" is an unknown key

Intrepid me detectó la placa Atheros automáticamente, ¿saben qué tengo que modificar para que me funcione el led?

Si te detectó la placa automáticamente asumo que estás usando el driver ath5k incluido en el paquete linux-backports-modules-intrepid. Comprobalo mirando en Sistema > Administración > Controladores de Hardware, ahí tiene que estar habilitado y en uso un driver que tiene un nombre que dice algo de 5xxx.
Si es así, esto no te va a funcionar. Sólo sirve si estás usando el driver madwifi compilado.
Por si querés probar, acá un tuto [http://ubuntuforums.org/showpost.php?p=5577447&postcount=13](http://ubuntuforums.org/showpost.php?p=5577447&postcount=13) para instalarlo.

Saludos

---

### Post by hictio on 2008-11-21
A mi en rojito me gusta... Es mi peque~na HAL, controlandome todo el tiempo :p

---

### Post by benjamin_linux on 2008-11-22
> A mi en rojito me gusta... Es mi peque~na HAL, controlandome todo el tiempo 

Jajajaja genial!

Gracias luks911 pero me quedo con el driver incluido por defecto, no es para tanto la lucesita, si me funciona perfecto.

---

### Post by dmela2012 on 2009-03-14
una pregunta, soy totalmente novato, me podrian explicar como se hace lo que dice, agregar, ya que no tengo ni idea, pero por favor paso por paso. y tambien si me dicen como se instala el madwifi, porque tengo una acer 5315 , instale el atheros 5xx y me funciono hasta que actualice el ubuntu y dejo de funcionar, ahora estoy con cable conectado y no funca wifi, si me pueden ayudar muchas gracias.

---

### Post by faktorqm on 2009-03-16
No se que placa tendras, pero el post que explico como se hace paso a paso es este [http://ubuntuforums.org/showpost.php?p=5633150&postcount=36](http://ubuntuforums.org/showpost.php?p=5633150&postcount=36)

Saludos

---

### Post by dmela2012 on 2009-05-09
Antes tenia intrepid y lo hice funcionar, pero con jaunty, que me reconocio automaticamente la placa wifi, lo instale desde 0, ahora no funciona, tienen idea como se hace. muchas gracias.

---

### Post by sitiomatic on 2009-05-09
A mi la luz me funciona haciendo lo mismo que hice antes, editando el archivo sysctl y agregando las lineas que estan al comienzo de este post.

---

### Post by luks911 on 2009-05-09
> **dmela2012 said:**
> Antes tenia intrepid y lo hice funcionar, pero con jaunty, que me reconocio automaticamente la placa wifi, lo instale desde 0, ahora no funciona, tienen idea como se hace. muchas gracias.

> **sitiomatic said:**
> A mi la luz me funciona haciendo lo mismo que hice antes, editando el archivo sysctl y agregando las lineas que estan al comienzo de este post.

La diferencia está en qué módulo/driver se use para el wifi. Si se usa el ath5k que viene por defecto en Jaunty, el led no funciona. Si se usa madwifi (módulo ath_pci), que hay que compilar e instalar, el led funciona con las modificaciones al sysctl.conf.

---

### Post by z37a on 2009-05-09
Alguna idea alguno de como hacerlo andar en ath5k???

---

### Post by aleveliz on 2009-12-30
lo unico que hay que hacer es instalar el kernell 2.6.32 y luego funciona el led azul,

---

### Post by Mauro22 on 2009-12-31
En mi Acer, el led funciona titilando cuando hay trasmision/recepcion de datos.

El otro dia encontré en:

/sys/class/leds/


Y alli:

ath9k-phy0::assoc  
ath9k-phy0::radio  
ath9k-phy0::rx  
ath9k-phy0::tx


assoc no se para que es.
radio es la luz del wifi
rx controla la recepcion
tx controla la transmision


adentro de cada carpeta hay un archivo llamado: brightness

Con un valor de 0 a 255 se puede prender o a apagar, por ejemplo un 0 en tx y un 255 en rx, simula el led titilando.

---

