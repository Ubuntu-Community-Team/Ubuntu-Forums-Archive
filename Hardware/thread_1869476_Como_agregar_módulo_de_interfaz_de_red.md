---
title: "Como agregar módulo de interfaz de red"
date: 2011-10-25
forum: Hardware
---

### Post by losoollenos on 2011-10-25
Hola muy buenas noches,

El problema que estoy teniendo es que intento instalar la 10.04 64bits en un Netbook con el mini cd cargado al pendrive, para luego ir instalando a gusto las cosas. Pero la instalación no me detecta ninguna interfaz de red y me dice que si quiero cargar un módulo específico vuelva al paso de detección de red. Esto no ocurre si instalo desde la imagen completa de Lucid, pero me gustaría solucionar la cuestión de la red e instalar el sistema base y luego los programas que uso.

La placa de red que trae es Atheros ar8152 pci-e.

Será posible agregar el driver o configurar la red de antemano o en el proceso mismo???.

Muchísimas gracias por las ayudas !!!!

---

### Post by hictio on 2011-10-25
Probaste usando el CD de instalación (desde USB) Alternate?

---

### Post by losoollenos on 2011-10-25
Tampoco se puede, sale el mísmo problema con la red

---

### Post by granjero on 2011-10-26
hola, pasanos la salida de ```
sudo ifconfig
``` para después editar el archivo ```
/etc/network/interfaces
```

salud!

---

### Post by guillermolisi on 2011-10-26
Creo que lo aconsejable en estos casos es iniciar la maquina en modo Live para verificar funcionalidad con el hardware.
Si no funciona en modo Live entonces hay que trabajar para encontrarle la vuelta al momento de instalar.

---

### Post by EnriqueK on 2011-10-26
también tuve este problema, lo solucioné haciendo 
sudo -i
apt-get remove network-manager
echo 'auto eth0' >> /etc/network/interfaces
echo 'iface eth0 inet dhcp' >> /etc/network/interfaces
/etc/init.d/networking restart

Lo que si es que te va a desaparecer el icono de conexión a la red
Te recomiendo promero probar esta solución en una sesión Live USB

---

### Post by losoollenos on 2011-10-26
Hola gracias a todos por las respuestas, me expliqué mal.

El problema es que al no detectar red no puede seguir con la instalación, ya que necesita conectarse y descargar "todo" para instalar el sistema, la mini imagen pesa 12 o 13 megas.

Disculpen y muchas gracias nuevamente.

---

### Post by guillermolisi on 2011-10-26
> **losoollenos said:**
> Hola gracias a todos por las respuestas, me expliqué mal.

El problema es que al no detectar red no puede seguir con la instalación, ya que necesita conectarse y descargar "todo" para instalar el sistema, la mini imagen pesa 12 o 13 megas.

Disculpen y muchas gracias nuevamente.
Casualmente por eso mi sugerencia de la prueba previa con un Live CD/USB.
Con lo que resulte vemos como seguir.

---

### Post by losoollenos on 2011-10-27
Sí Guillermo, instalando desde live-cd detecta todo bien y se puede instalar, conecta por wifi y/o por lan.

Pero la idea es, repito, instalar el sistema base desde el minimal-cd (en versiones anteriores de Ubuntu, se podía hacer con el alternate-cd, pero ahora parece que no está más esa posibilidad), y luego instalar sólo los programas que uso.

saludos

---

### Post by guillermolisi on 2011-10-27
Ok. No me habia quedado claro si habias probado o no.

Creo que [este sintetico tutorial]("http://www.psychocats.net/ubuntu/minimal") (en Ingles) puede ser de ayuda. Habla sobre como agregar modulos (drivers) cuando instalas Ubuntu Minimal.

---

### Post by losoollenos on 2011-10-27
Mil gracias, voy a ver si da mi inglés....y mi coco jjejeje

saludos

---

### Post by losoollenos on 2011-10-27
Perdoná Guillermo, pero no veo que la guía explique cómo agregar drivers para que detecte la red y pueda conectarse a internet.

saludos

---

### Post by guillermolisi on 2011-10-27
> **losoollenos said:**
> Perdoná Guillermo, pero no veo que la guía explique cómo agregar drivers para que detecte la red y pueda conectarse a internet.

saludos

Es cierto, no dice lo que esperaba deebria decir. Seguiremos buscando. Disculpas por no haber leido mas profundamente (demasiada confianza en las busquedas de Google).

---

### Post by fmsismo on 2011-10-28
Por lo que leí tus placas de red no están soportadas en el kernel que trae la 10.04.  Probaste con la 11.10?  Estas usando 10.04 por algún tema en especial?

Si estas obligado a usar 10.04, te diría que pongas una placa de red extra instales el sistema, buscar el módulo para la placa de red que necesitas y ver si lo podes compilar para el kernel que te viene en la 10.04.  Tene en cuenta que puede que te dejen de andar las placas si te cae una actualización del kernel, en ese caso deberías tener que compilar el driver de nuevo.

Saludos

---

### Post by losoollenos on 2011-10-28
Gracias fmsismo.
Los motivos de porqué la 10.04 son varios, agilidad, interfaz, soporte y alguno que otro más.

Creo que el kernel debe soportar esta placa, porque, cómo contaba más arriba, lo hace desde el live-cd y también instalando Debian 6.03 netinstall, que viene con el kernel 2.6.32-5 (en lucid está 2.6.32-34), lo que pasa que en Debian nunca termino de solucionar algunas cosas. 

Y la idea de instalar desde el sistema base es que, en mi experiencia, el sistema lo noto más ágil, y eso me gusta en la Netbook o en lo que sea jejjeje.

Saludos

---

### Post by scrooge_74 on 2011-10-31
Hola,

acabo de comprar una de esas Acer Aspire con el mismo problema con los drivers para el Atheros, al parecer en 10.10 ya està en orden, pero en Lucid da problemas.

Hay varias soluciones:

[http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697) El usuario pytheas22 expuso la soluciòn, por alguna razòn el driver para los Atheros està en el compat-wireless y las instrucciones le han funcionado a varios. A mi no, pero en el mismo sitio de linux wireless hay pàquetes para Ubuntu.

[http://linuxwireless.org/en/users/Download#Getting_compat-wireless_on_Ubuntu](http://linuxwireless.org/en/users/Download#Getting_compat-wireless_on_Ubuntu)

El detalle es que la instrucción es para usar backports para que este funcione. Y en mi caso la broadcom wireless dejó de funcionar al arreglar los drivers de la Atheros wired.

Así que sigo buscando la solución completa

---

### Post by losoollenos on 2011-10-31
Gracias, igual no es el problema que tengo.

Saludos

---

### Post by scrooge_74 on 2011-11-01
Hice una instalación completa de la ver 11.10 y todo está bien hasta el momento que desconecto el cable de red.

Por lo que leo en los foros y en los bug reports al parecer el driver del Atheros AR8152 en kernel tiene problemas.

Los freeze que he sufrido todos tienen que ver con esa tarjeta de red

---

### Post by losoollenos on 2011-11-01
Yo la verdad que estoy usando lucid, 64 bits (instalado desde live-cd) y "cero" problemas.

---

### Post by scrooge_74 on 2011-11-01
Al final es cuestión de drivers, acabo de tomarme unos minutos para analizar el asunto. Mi solución poco elegante es la siguiente:

en **/etc/network/interfaces**

pongo las siguientes líneas:

[B]noauto eth0
iface eth0 inet dhcp
[/B]

Esto le quita a Network Manager el control sobre la interfaz de red cableada.

El wifi sigue funcionando y si me hace falta conectarme a una red por cable en una terminal pongo.

**sudo ifup eth0 **

Lo que sí que tengo que tener cuidado si desconecto el cable de red tengo que desactivar primero la interfaz

**sudo ifdown eth0**

o me corro el chance que se congele la laptop.

En lo particular para mi está bien, en casa soy el único que se conecta a través de cable de red, el resto usarían el wifi, igual cuando estoy fuera es por wifi.

Puedo continuar disfrutando linux mientras los desarrolladores logran arreglar el driver

---

