---
title: "how-to Conectar Modem SonyEricsson MD300 Entel en Jaunty"
date: 2009-06-15
forum: Hardware
---

### Post by 3nG3ndR0 on 2009-06-15
Hola Tengo este módem hace un rato y me consto mucho configurar lo en su tiempo en hardy e intrepid, pero en jaunty no me funcionaba la misma forma, así que navegando encontré esta solución que me funciono enseguida y con Network-Manager

- Mantener desconectado el modem SE MD300

- Deshabilitar Dispositivo de Almacenamiento del módem SE MD300

En el terminal escriben lo siguiente:

```
$ sudo gedit /etc/udev/rules.d/50-md300.rules
```Agregamos las lineas siguientes en el archivo:

```
ACTION!="add", GOTO="3G_END"
BUS=="usb", SYSFS{idProduct}=="d0cf", SYSFS{idVendor}=="0fce", PROGRAM="/bin/sh -c 'echo 3 >/sys/%p/device/bConfigurationValue'"
LABEL="3G_END"
```Reiniciar el servicio de reglas para los dispositivos :

```
$ sudo /etc/init.d/udev restart
```

**Configurar Acceso de Red:**

Sistemas>Preferencias>Conexiones de red

- En la Pestaña **Banda ancha móvil**
- Pulsamos el botón **Añadir**
- En la ventana de Bienvenido, pulsamos el botón **Adelante**
- Seleccionamos el país **cl - Chile**
- Seleccionamos Proveedor **Entel PCS**
- En la ventana de Resumen pulsamos el botón **Aplicar**

**Realizar la Conexión :**

- Conectar el Modem SE MD300
- Esperar algunos segundo mientras el sistema lo reconoce
- Ir al indicador de conexión de red
(debe aparecer debajo de Red cableada la opción EntelPCS)

Conectarnos a la Banda ancha móvil en mi caso (EntelPCS):

[IMG]http://2.bp.blogspot.com/_tAId1qMnPV8/SfsZp0mNCKI/AAAAAAAAAKM/VJWiEbXHbUQ/s400/entelpcs.png[/IMG]

Listo ya estas conectado a tu banda ancha móvil.

[IMG]http://4.bp.blogspot.com/_tAId1qMnPV8/SfsablG4U7I/AAAAAAAAAKU/VhNNC2X_KE4/s400/conectado_entelpcs.png[/IMG]

Para desconectarse pulse sobre network-manager y debajo de EntelPCS dice Desconectar, a disfrutar del Internet con tu Banda ancha móvil desde Ubuntu Jaunty

---

### Post by Carlos C on 2009-06-22
[**[COLOR=DarkRed]Post de la semana]("http://ubuntuforums.org/showthread.php?t=1176055")[/COLOR]**: 22 de junio de 2009:

[http://ubuntucl.wordpress.com/2009/06/22/conectar-modem-sonyericsson-md300-en-jaunty/](http://ubuntucl.wordpress.com/2009/06/22/conectar-modem-sonyericsson-md300-en-jaunty/)

---

### Post by Pcniatic on 2009-07-01
Funciona perfectamente, muchas gracias.....

---

### Post by asterix77 on 2009-07-02
En intrepid bajé un driver de entel pc para este modem: md300Config. Lo instalé y no me dió ningún drama. El problema me lo dió en mi pc de escritorio con Jaunty en el cual hice el mismo procedimiento y no me funcionó. Así es que seguí lo indicado anteriormente en este post para conectar mi md300 a Jaunty. Igual tuve problemas, ya que no siempre me detectaba el módem; en la mayoría de los casos no me lo detectaba. Así es que por probar lo que hice fue borrar todos los archivos que se generaron (según el post) en jaunty, y luego hice una copia de los archivos de configuración del modem pero en mi notebook (Intrepid), y los copié en las mismas rutas en Jaunty, y oh sorpresa, conecté el módem, espero unos par de segundos y me aparece la conexión en el network manager. Me conecto y no tengo ningún problema ahora. Lo que si ahora no sé porqué cuando le doy a desconectar no lo hace, pero bueno eso es lo de menos. Lo importante es que ahora me conecta a la primera.


Saludos

---

### Post by Carlos C on 2009-07-02
> **asterix77 said:**
> lo que hice fue borrar todos los archivos que se generaron (según el post) en jaunty, y luego hice una copia de los archivos de configuración del modem pero en mi notebook (Intrepid), y los copié en las mismas rutas en Jaunty

¿Podrías decirnos qué archivos son y dónde los copiaste?
Saludos.

---

### Post by asterix77 on 2009-07-02
Carlos, primero traté de realizarlo siguiendo este how to:

"Mantener desconectado el modem SE MD300

Deshabilitar Dispositivo de Almacenamiento del modem SE MD300

En el terminal escriben lo siguiente:

    $ sudo gedit /etc/udev/rules.d/50-md300.rules



Agregamos las lineas siguientes:

    ACTION!="add", GOTO="3G_END"
    BUS=="usb", SYSFS{idProduct}=="d0cf", SYSFS{idVendor}=="0fce", PROGRAM="/bin/sh -c 'echo 3 >/sys/%p/device/bConfigurationValue'"
    LABEL="3G_END"



Reiniciar el servicio de reglas para los dispositivos :

    $ sudo /etc/init.d/udev restart



Configurar Acceso de Red:

Sistemas>Preferencias>Conexiones de red

- En la Pestaña Banda ancha móvil
- Pulsamos el botón Añadir
- En la ventana de Bienvenido, pulsamos el botón Adelante
- Seleccionamos el país mi caso cl Chile
- Seleccionamos Proveedor Entel PCS
- En la ventana de Resumen pulsamos el botón Aplicar

Realizar la Conexión :

- Conectar el Modem SE MD300
- Esperar algunos segundo mientras el sistema lo reconoce
- Ir al indicador de conexión de red
(debe aparecer debajo de Red cableada la opción EntelPCS)
- Disfrutar del Internet móvil desde Ubuntu Jaunty

Conectarnos a la Banda ancha móvil en mi caso (EntelPCS):"


Pero por alguna razón que desconozco, me resultaba solo unas par de ocasiones, por lo que hice lo que comenté anteriormente, es decir

Copié desde intrepid los siguientes archivos y los coloqué en las mismas rutas:

/etc/udev/rules.d/50-md300config.rules
/etc/wvdial.conf
/etc/EntelPCS.conf

Después de esto no se porqué, pero no he tenido ningún problema en conectarme.

Saludos

---

### Post by moreback on 2009-07-03
> **asterix77 said:**
> Copié desde intrepid los siguientes archivos y los coloqué en las mismas rutas:

/etc/udev/rules.d/50-md300config.rules
/etc/wvdial.conf
/etc/EntelPCS.conf

Después de esto no se porqué, pero no he tenido ningún problema en conectarme.

Saludos

Sólo el primer archivo es el que funciona ya que contiene reglas para inhabilitar el dispositivo de almacenamiento que trae el modem. Después de enchufar el modem debe aparecer el dispositivo disponible en el NM, pero debes crearle también una conexión a tu ISP.

Los otros dos archivos no influyen ya que son para gente que le gusta complicarse la vida con scripts para el wvdial (razón por la que no viene instalado en Ubuntu), siendo que con Network-Manager es demasiado simple.

Saludos.

---

