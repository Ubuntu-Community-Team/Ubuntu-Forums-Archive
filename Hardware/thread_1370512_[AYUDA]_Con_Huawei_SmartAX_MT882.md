---
title: "[AYUDA] Con Huawei SmartAX MT882"
date: 2010-01-02
forum: Hardware
---

### Post by odlez on 2010-01-02
Buenas

Tengo un problema decidi instalar Ubuntu 9.10 en mi PC x XP me canso de lo asco virus, etc.
El problema que tengo es que NO tengo Internet estube investigando y leyendo bastante por internet sobre este tema pero no encontre mucho o màs bien no encontre sobre relacionado con el modem que tengo yo.

Mi modem: **Huawei SmartAX MT882**
Yo tengo 2 PC, una pc conectada con el cable de red, y la otra osea la mia (esta) esta conectada por **USB**.
Y leyendo por inet sobre este tema vi que tiene problemas con el USB el Ubuntu o algo asi.

Em Sonido y Video si tengo intalado en Ubuntu no me pidio intalaciòn de eso y eso que formatie primero como S.O. principal sin el XP y tenia sound y video..
Y pense que talves si intalo el XP y dsp el Ubuntu tenga inet, pero nop, no tengo sigue igual.

Probe con los acceso al modem x el navegador osea: 10.0.0.2 pero nada /3 tampoco nada. 

Yo tengo el CD de Arnet del Modem este pero Ubuntu no reconoce osea no acepta el CD, ya que tampoco acepta los .exe
Me dijieròn que me baje los Drivers de ese Modem pero como lo instalo para ubuntu? en que formato vendria?.

Es medio imposible encontrar los drivers para ese modem ya estube buscando y no encontre nada.

Aver si me ayudan

Saludos

---

### Post by z37a on 2010-01-02
> **odlez said:**
> Buenas

Tengo un problema decidi instalar Ubuntu 9.10 en mi PC x XP me canso de lo asco virus, etc.
El problema que tengo es que NO tengo Internet estube investigando y leyendo bastante por internet sobre este tema pero no encontre mucho o màs bien no encontre sobre relacionado con el modem que tengo yo.

Mi modem: **Huawei SmartAX MT882**
Yo tengo 2 PC, una pc conectada con el cable de red, y la otra osea la mia (esta) esta conectada por **USB**.
Y leyendo por inet sobre este tema vi que tiene problemas con el USB el Ubuntu o algo asi.

Em Sonido y Video si tengo intalado en Ubuntu no me pidio intalaciòn de eso y eso que formatie primero como S.O. principal sin el XP y tenia sound y video..
Y pense que talves si intalo el XP y dsp el Ubuntu tenga inet, pero nop, no tengo sigue igual.

Probe con los acceso al modem x el navegador osea: 10.0.0.2 pero nada /3 tampoco nada. 

Yo tengo el CD de Arnet del Modem este pero Ubuntu no reconoce osea no acepta el CD, ya que tampoco acepta los .exe
Me dijieròn que me baje los Drivers de ese Modem pero como lo instalo para ubuntu? en que formato vendria?.

Es medio imposible encontrar los drivers para ese modem ya estube buscando y no encontre nada.

Aver si me ayudan

Saludos

Mira, no se en especifico ese modem si requiere drivers, peor la gran mayoria no, simplemente deberias conectarlo a tu pc con Ubuntu, luego en el gestor de redes(Arriba a la derecha lo tenes).

Cualquier cosa aca tenes el como se haria en caso de que entres al gestor de redes y pongas "Editar las conxiones"(Se hace haciendo click derecho sobre el gestor de conexiones):

[img]http://img51.imageshack.us/img51/2382/pantallazoconexionesder.png[/img]

[img]http://img43.imageshack.us/img43/4240/pantallazoconexindeband.png[/img]

Luego seguís el asistente.

---

### Post by odlez on 2010-01-02
Pero que tiene que ver el Celular (Movil) para conectar mi Internet?

---

### Post by z37a on 2010-01-02
> **odlez said:**
> Pero que tiene que ver el Celular (Movil) para conectar mi Internet?

Es esactamente lo mismo, los telefonos traen incorporados modems desde hace años(Antes del 3G!), los modems de ahora 3G son simples telefonos, sin display, teclado micriosof ni parlantes, pero son telefonos.

---

### Post by harryscode on 2010-01-03
Hola, tengo el mismo modem, y me sucedía lo mismo, me harte de probar cuanta configuración daba vueltas por la red, hasta que la solución la encontré comprando un switch y con eso conecto las dos pc con cable de red y el usb ni lo uso. Sale $30 uno comunacho y me alivie de muchos dolores de cabeza. No se si te puede servir pero es la solución que le encontré al problema.

---

### Post by z37a on 2010-01-03
> **harryscode said:**
> Hola, tengo el mismo modem, y me sucedía lo mismo, me harte de probar cuanta configuración daba vueltas por la red, hasta que la solución la encontré comprando un switch y con eso conecto las dos pc con cable de red y el usb ni lo uso. Sale $30 uno comunacho y me alivie de muchos dolores de cabeza. No se si te puede servir pero es la solución que le encontré al problema.


Jajaja, no caia, pense que era un modem 3G, generlamente son los que mas problemas dan, pido mil disculpas!!!!!

Lo ideal siempre es utilizar la conexión por cable de red el usb anda muy mal, y como bien dijeron con un simple switch y configurando el modem ya quedaria andando sin problemas. Igualmente lo IDEAL es que compres un router, y de ahi distribuyas a las pcs.

---

### Post by dirty fingers on 2010-01-05
pese a que el mensaje de odlez parece escrito por el chino del supermercado de la esquina que acaba de migrar creo poder dar una solución.

Este modelo de modem se puede configurar como router en vez de bridge(yo lo hice así que no tengo duda). En algunas oportunidades viene bloqueada la interfaz para que no  lo puedas hacer pero por telnet no se resiste. 

Y otro detalle importante es que la pc conectada por usb debe tener los driver instalados.

---

### Post by andres2420 on 2010-01-23
> **dirty fingers said:**
> pese a que el mensaje de odlez parece escrito por el chino del supermercado de la esquina que acaba de migrar creo poder dar una solución.

Este modelo de modem se puede configurar como router en vez de bridge(yo lo hice así que no tengo duda). En algunas oportunidades viene bloqueada la interfaz para que no  lo puedas hacer pero por telnet no se resiste. 

Y otro detalle importante es que la pc conectada por usb debe tener los driver instalados.

jajajjaja como me reí con el primer párrafo.

Ahora realmente a lo que nos interesa...el modem que entrega arnet y mejor dicho TODOS los modem que entrega arnet YA VIENEN DE FABRICA NATEADOS.Todo modem ethernet provisto por arnet ya esta como router.El problema del amigo o la solución al mismo no es eso de que si esta o no como router.Por lo tanto con conectar tanto por cable de red o cable usb (este ultimo tiene que tener el driver usb instalado...que es el problema puntual) debería de salir andando.

EN lo particular yo estoy con lo mismo, sigo revolviendo google en busca del controlador usb para este modem.O claro está que si la segunda pc, la que ahora esta via cable de red tiene xp, lo mejor es que a esa le instales los drivers usb (10 segundos en taringa y los encontras para xp y vista...no se para el 7)y la conectes por ese medio y a esta que tiene ubuntu lo hagas por ethernet.

Saludos

---

