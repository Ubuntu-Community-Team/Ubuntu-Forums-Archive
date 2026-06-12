---
title: "ACER ASPIRE 3650 Enciende solo con batería, al enchufar a la corriente se apaga la pa"
date: 2010-04-16
forum: Hardware
---

### Post by cantervilotis on 2010-04-16
Estimados:

tengo un paortatil acer aspire 3650, el cual tiene instalado (instalacion limpia) Ubuntu 9.10
El computador enciende, si lo hago con la batería (sin estar conectado a la electricidad) no tiene problemas.
Pero si lo enciendo conectado a la electricidad, prende todo salvo la pantalla q se queda en negro (suenan "las piezas" del ordenador, prenden los led, etc)

Una vez prendido con la carga de la bateria si lo enchufo a la corriente se apaga la pantalla y queda el led de encendido.... si lo prendo con la bateria esta se acaba a los 15 min y la pantalla se apaga nuevamente y queda el led de encendido.....

Fui a Sistemas----preferencias.. etc y me sale lo siguiente

CON ADAPTADOR DE CORRIENTE
ACCIONES
poner el equipo.... NUNCA
al cerrar la tapa del portatil.... SUSPENDER
PANTALLA
poner la pantalla.... 30 MINUTOS
poner brillo al monitor 100 %

CON BATERIA
poner el equipo.... NUNCA
al cerrar.... SUSPENDER
cuando la carga de la bateria... HIBERNAR

En este ordenador (que por cierto no es mío) no tenía problemas con windows. Una vez corrí un live cd de xubuntu (no recuerdo la version, pero tiene q haber sido alguna del año pasado) y sucedio el mismo problema descrito anteriormente.

Espero me puedan ayudar.

Saludos atentos

---

### Post by Carlos C on 2010-04-18
No he encontrado información respecto a lo que te pasa. Por favor escribe en el terminal:
```
lspci
```
para que veamos si tienes algun componente que de algún tipo de problema.

---

### Post by cantervilotis on 2010-04-20
Siento la tardanza, aquí va lo que aparece:

> user@laptop:~$ **lspci**

00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

user@laptop:~$ 


Saludos atentos
Muchas gracias

---

### Post by Lutho on 2010-04-24
una consulta, cuando realizaste la instalacion 
lo hiciste con la bateria cargada.. o conectado directamente a la corriente?..

te pregunto esto por que en mi poca experiencia que tengo en linux, cada vez que hacia una instalacion con un equipo (notebook) conectado a la corriente ..la bateria se desgastaba mas rapido y no me reconocia cuando estaba conectado a la corriente o con bateria..

nose si me explico bien... parece un trabalenguas jiji
saludos!

---

### Post by cantervilotis on 2010-04-25
Hola, gracias por responder.
La verdad es que no entendí mucho, dices que una posible solución sería instalarlo con la batería solamente (sin que esté enchufado a la corriente eléctrica)?

Efectivamente lo instalé conectado a la electricidad, si la solución pudiera ser instalarlo con la batería solamente, estaría en problemas aún debido a que la batería dura 5 minutos máximo

Saludos cordiales

---

### Post by Carlos C on 2010-04-25
Hola. Tu modelo de tarjeta es una ATI que no tiene problemas en Ubuntu, de hecho funciona con los drivers libres, lo sé porque tengo la misma. Verifica que no sea tan simple como configurar el gestor de energía. No estoy en gnome ahora, pero lo encontrarás en Sistema-->Preferencias-->Administrador de energía (o algo parecido). También puedes ver en Sistema-->Administración-->Hardware Drivers (no recuerdo la traducción de esta última).

Si no es eso, entonces habrá que investigar un poco más.

¿Cuando arrancas desde el LiveCD pasa lo mismo?
¿Habías usado ese equipo con otros sistemas operativos anteriormente?

---

### Post by cantervilotis on 2010-04-25
Hola, muchas gracias de nuevo.

La configuración de energía está detallada en el primer post, creo que está correcta.

Respecto a la otra pregunta, usando windows xp no había problemas. Una vez usé un live cd de xubuntu q corrió sin problemas. Al sacar el cd y prender el equipo (con win xp) tuve q desenchufarlo de la corriente eléctrica para q encendiera (con el enchufe, no respondía el botón de encendido).

Personalmente tampoco he encontrado mayor información, voy a tratar de instalarle Lubuntu o bien Lucid Lynx (intenté instlar lucid lynx beta2 y se quedaba "pegado" al entrar al escrtorio)

Gracias por su ayuda
saludos atentos

---

### Post by Lutho on 2010-04-26
sorry por el post .. era un tanto complicado jajajaj 

has probado con instalar otra distribucion de linux?..
o siempre lo has hecho con ubuntu...?

en caso de que no, intenta con probar otra distro aver si el problema persiste.

---

### Post by Carlos C on 2010-04-26
Antes de probar instalar otra versión de linux yo intentaría averiguar qué está fallando. De partida, para verificar que no sea una cuestión de configuración del usuario arrancaría con el LiveCd. También puedes crearte un usuario nuevo y ver si el problema persiste. En caso de que el LiveCD y el usuario nuevo fallen, ya sabes que tu problema es de hardware o de la configuración que ubuntu trae por defecto, pero esto último lo veo como una posibilidad muy remota.

Saludos.

---

### Post by cantervilotis on 2010-07-15
Estimados, continuo con el problema. Sin embargo esta vez el ordenador enchufado a la corriente no enciende, si retiro el enchufe (solo con batería) ahi si prende, pero al enchufarse se apaga. Como dije anteriormente esto no pasaba anteriormente con windows xp, voy a intentar con Linux Mint (no se si puede que no avance mucho, como es una distro basada en Ubuntu, o si no probaré con fedora 13), de no tener éxito no me queda más que volver a xp.
Tendrá algo que ver la tarjeta de video ati? si pruebo con envy?

Saludos cordiales

---

### Post by asterix77 on 2010-07-16
Recuerdo que a un compañero de trabajo, su notebok no le encendía al enchufarlo a la corriente. Después de buscar soluciones por todos lados, finalmente descubrió que el problema era la batería. Estaba con bastante vida útil, y solo le duraba lo suficiente como para respaldar sus archivos y apagar el note. Antes de comprarse una nueva batería, le recomendaron que antes de encender el equipo (conectado a la corriente), saque la batería y lo encienda; esto daba resultado en el 100% de los casos, inclusive a veces le resultaba encenderlo con la batería conectada, (pero muy raramente). La solución definitiva fue cuando e compró una nueva.

Tal vez no sea tu problema, pero encuentro muy similares los problemas.

Saludos

---

### Post by BenjaminChile on 2010-07-16
Hola,

concuerdo en una experiencia como la que relata Asterix, normalmente una bateria con problemas internos de retencion de carga (bloqueada) puede indicar un registro errado de carga al monitor upower de linux. Te recomiendo no llevar tu notebook a un sevicio de electricidad ( no de computadores, ni tampoco electronico), estas tiendas que tienen reparacion de motores, y cargadores de baterias, y lleva tu adaptador de corriente y bateria para que chequeen, si salen los 18 o 20 volts de DC o corriente continua que alimenta tu cargador, y que revisen la cantidad de carga de corriente a al hora o Ampere que registra tu transformador. Y hagan lo mismo con tu bateria, midan la corriente de carga o Ampere (corriente continua) de la bateria. (una bateria de hasta 2 horas y 30 minutos debe contener una carga maxima de 4, 3 Ampere de carga). Se que esto demasiado tecnico pero te servira para ir descartando el funcionamiento de los accesorios de tu notebook. Una vez realizada estas pruebas deberias llevar tu notebook a un servicio respetable para que le revisen la fuente de corriente interna o incorporada que es la parte que realiza la carga a tu bateria cuando dejas enchufado tu equipo y vez que el porcentaje de carga y tiempo en hora y minutos te dice que esta cargando.
Solo despues de estas 03 revisiones con resultados positivos, yo pondria los ojos en el software , o sea en Ubuntu, Linux Mint o Windows, o el que le quieras probar. Ojala pruebes instalar un disco original de Ubuntu, de Fedora, o de Windows porque a veces cuando bajas gratuitamente las imagenes ISO desde internet debes revisar si bajaron correctamente, a veces estas descargas traen pifias.
Salu2.

---

