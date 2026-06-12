---
title: "Webcam satellite"
date: 2009-10-26
forum: Hardware
---

### Post by eowynt on 2009-10-26
Hola. Soy nueva en esto del linux....en verdad todavía no entiendo la mayor parte de las cosas....
Hace 2 días desinstalé windows de mi PC...y ahora puse esta plataforma.
El tema es que no me reconoce la webcam :( .
Tengo una cámara SATELLITE....linda.... pero que no me funciona con este nuevo sistema.....](*,). 
Alguien podría decirme si hay algún truco para que la máquina la reconozca?????:confused:
Por favor, si alguien escribe tengan en cuenta que soy abogada y no programadora...con lo cual necesito una explicación a prueba de tontos.....:) (pueden escribir acá o a mi mail: [EMAIL="eowynt@yahoo.com"]eowynt@yahoo.com[/EMAIL])
Desde ya MUCHAS GRACIAS !!!!

---

### Post by pablo.s on 2009-10-26
Hola. En el menú Aplicaciones ->
Accesorios hay un programa que
se llama Terminal.
Abri ese programa y una vez que
esté abierto escribí:

```
lsusb
```

y lo que salga listado, por favor
lo copiás y lo pegás en un post 
nuevo. A partir de lo que te devuelva
vemos cuál puede ser el problema.

---

### Post by luks911 on 2009-10-26
Bienvenida.
Si la cámara es usb (seguramente lo sea) abrí una terminal (en Aplicaciones > Accesorios > Terminal) y ahí ejecutás el comando 
```
lsusb
```
le das enter y el resultado lo pegás acá. Eso te va a dar datos sobre la cámara (siempre que esté conectada, claro) útiles para saber si puede funcionar y cómo.
También contanos qué versión de Ubuntu estás usando.

Saludos

---

### Post by eowynt on 2009-10-26
Hola: ante todo MUCHAS GRACIAS !!!!
Intenté hacer lo que me dijiste y el resultado fue este:
[FONT=monospace]
lsusb
Bus 001 Device 004: ID 03f0:2504 Hewlett-Packard 
Bus 001 Device 002: ID 054c:01bd Sony Corp. MRW62E Multi-Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 WebCam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
graciela@graciela-desktop:~$ 

que por supuesto no tengo ni la más pálida idea de qué significa.....

Ayer cuando me trajeron la máquina, la cámara en un momento prendió la lucecita azul...pero luego no hubo forma de que funcionara.....

Por lo que pude ver me instalaron UBUNTU 9.04  (aunque tampoco tengo mucha idea de qué signifique esto....)

ya que estamos, y todo por el mismo precio...tenés idea porqué cuando voy a youtube muchos de los videos no los reproduce??? sólo está abriendo un 20% de los videos que selecciono  (anteriormente con windows nunca tuve problemas)

De tecnología cero, pero si alguna vez puedo darte un asesoramiento legal espero poder devolverte el favor. GRACIAS !!!!!
[/FONT]

---

### Post by eowynt on 2009-10-26
> **luks911 said:**
> Bienvenida.
Si la cámara es usb (seguramente lo sea) abrí una terminal (en Aplicaciones > Accesorios > Terminal) y ahí ejecutás el comando 
```
lsusb
```le das enter y el resultado lo pegás acá. Eso te va a dar datos sobre la cámara (siempre que esté conectada, claro) útiles para saber si puede funcionar y cómo.
También contanos qué versión de Ubuntu estás usando.

Saludos

Hola: ante todo MUCHAS GRACIAS !!!!
Intenté hacer lo que me dijiste y el resultado fue este:
[FONT=monospace]
lsusb
Bus 001 Device 004: ID 03f0:2504 Hewlett-Packard 
Bus 001 Device 002: ID 054c:01bd Sony Corp. MRW62E Multi-Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 WebCam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
graciela@graciela-desktop:~$ 

que por supuesto no tengo ni la más pálida idea de qué significa.....

Ayer cuando me trajeron la máquina, la cámara en un momento prendió la lucecita azul...pero luego no hubo forma de que funcionara.....

Por lo que pude ver me instalaron UBUNTU 9.04  (aunque tampoco tengo mucha idea de qué signifique esto....)

ya que estamos, y todo por el mismo precio...tenés idea porqué cuando voy a youtube muchos de los videos no los reproduce??? sólo está abriendo un 20% de los videos que selecciono (anteriormente con windows nunca tuve problemas)

De tecnología cero, pero si alguna vez puedo darte un asesoramiento legal espero poder devolverte el favor. GRACIAS !!!
[/FONT]
 		                   		  		  		  		  		  	   	   	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]

---

### Post by eowynt on 2009-10-26
Hola: ante todo MUCHAS GRACIAS !!!!
Intenté hacer lo que me dijiste y el resultado fue este:
[FONT=monospace]
lsusb
Bus 001 Device 004: ID 03f0:2504 Hewlett-Packard 
Bus 001 Device 002: ID 054c:01bd Sony Corp. MRW62E Multi-Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 WebCam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
graciela@graciela-desktop:~$ 

que por supuesto no tengo ni la más pálida idea de qué significa.....

Ayer cuando me trajeron la máquina, la cámara en un momento prendió la lucecita azul...pero luego no hubo forma de que funcionara.....

Por lo que pude ver me instalaron UBUNTU 9.04  (aunque tampoco tengo mucha idea de qué signifique esto....)

ya que estamos, y todo por el mismo precio...tenés idea porqué cuando voy a youtube muchos de los videos no los reproduce??? sólo está abriendo un 20% de los videos que selecciono (anteriormente con windows nunca tuve problemas)

De tecnología cero, pero si alguna vez puedo darte un asesoramiento legal espero poder devolverte el favor. GRACIAS !!!!!
[/FONT]
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8170054") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8170054")

---

### Post by luks911 on 2009-10-26
Bien. Aparentemente hace falta instalar un driver para que funcione. Vamos a tratar con lo siguiente:
1) Volvé a una terminal y ejecutá
```
sudo apt-get install module-assistant
```
te va a pedir tu contraseña, la escribís (no la vas a ver) y le das enter. Eso instala un programa que te va a ayudar en la instalación del driver.

2) Ejecutás el programa con
```
sudo module-assistant
```

3) Va a aparecer un menú así:
```
1. UPDATE
2. PREPARE
3. SELECT 
4. GET
5. BUILD
6. INSTALL
```

Vas a pasar por cada una de las opciones presionando el número que corresponde. Pero en 3 (SELECT) buscás la opción gspca (es el driver que necesitás), lo seleccionás con la barra espaciadora y luego con el tabulador cambias hasta aceptar, donde le das enter. Después sí, seguis con los pasos 4, 5 y 6.
No estoy seguro si ya va a estar funcionando o necesitás reiniciar antes.

Por lo de YouTube, te recomiendo abrir un nuevo hilo y explicá cómo es que no se reproducen (no se ve nada, se traban, etc).

---

### Post by eowynt on 2009-10-27
Hola:

Ante todo MIL GRACIAS nuevamente.
Te cuento que seguí bien las instrucciones hasta  sudo module-assistant...
pero allí me varió la cosa...
en vez de aparecer el menú de pantalla que vos me señalaste, apareció este:

overview
update
prepare
select
exit

igualmente intenté seguir, y cuando llegué a "select" pude ingresar a una lista larga (ordenada alfabéticamente), pero allí no figuraba la opción  gspca

Después de eso no supe qué hacer.....


:cry:

Así que estoy como cuando vinimos de España.... snif, snif, snif

Si se te ocurre algún otro paso que pueda dar esperaré tu ayuda.
Saludos

Graciela


> **luks911 said:**
> Bien. Aparentemente hace falta instalar un driver para que funcione. Vamos a tratar con lo siguiente:
1) Volvé a una terminal y ejecutá
```
sudo apt-get install module-assistant
```te va a pedir tu contraseña, la escribís (no la vas a ver) y le das enter. Eso instala un programa que te va a ayudar en la instalación del driver.

2) Ejecutás el programa con
```
sudo module-assistant
```3) Va a aparecer un menú así:
```
1. UPDATE
2. PREPARE
3. SELECT 
4. GET
5. BUILD
6. INSTALL
```Vas a pasar por cada una de las opciones presionando el número que corresponde. Pero en 3 (SELECT) buscás la opción gspca (es el driver que necesitás), lo seleccionás con la barra espaciadora y luego con el tabulador cambias hasta aceptar, donde le das enter. Después sí, seguis con los pasos 4, 5 y 6.
No estoy seguro si ya va a estar funcionando o necesitás reiniciar antes.

Por lo de YouTube, te recomiendo abrir un nuevo hilo y explicá cómo es que no se reproducen (no se ve nada, se traban, etc).

---

### Post by luks911 on 2009-10-27
Tenés razón, me estaba guiando por un tutorial para una versión de Ubuntu más vieja. Perdón.
Ahora, me parece que la cámara debería funcionar sin tocar mucho más. Para ver qué está pasando decime qué versión de Ubuntu usás, contame cómo probaste la cámara (una forma es ejecutando en una terminal el comando gstreamer-properties y en el cuadro de diálogo que se abre ir a la pestaña Video, en Default Input chequear que esté seleccionada la cámara y clickear en test) y, por último, decime qué te devuelve en la terminal el comando 
```
lsmod | grep gs
```
Después vemos cómo seguimos. En el peor de los casos habrá que bajar y compilar el driver. Pero son sólo seis sencillos pasos.

---

### Post by eowynt on 2009-10-28
Hola:

Te cuento que la versión de UBUNTU que me instalaron es la 9.04 y no se si servirá el dato, pero me fijé que el el escritorio es GNOME, y dice versión 2.26.1

cuando puse el comando gstreamer-properties  abrió un cuadro de diálogo llamado "selector de sistema multimedia", allí fui a  VIDEO en ENTRADA DE PRUEBA y está activada la opción que dice VIDEO POR LINUX (V4L2), (también aparecen las opciones: entrada de prueba, video for linux (V4) y personalizado.
Lo dejé el VIDEO FOR LINUX (V4L2) y apreté el botón PRUEBA....mágicamente la cámra se activó, es decir pude ver mi propia imagen)

Cuando puse el comando   ```
lsmod | grep gs[/code, apareció esto :

graciela@graciela-desktop:~$ [code]lsmod | grep gs
```
bash: ```
lsmod: orden no encontrada
graciela@graciela-desktop:~$ 


luego quise chequear el programa emesene, para ver si funcionaba la cámara y cuando seleccioné un contacto con el que habitualmente podía comunicarme bien me apreció este mensaje:

YOU DON'T HAVE LIBMIMIC, SO YOU CAN'T SEND OR RECEIVE WEBCAM


No se qué significa esto, pero pensé que el dato podía ser de ayuda.
En un rato tengo que viajar para Baires por razones de trabajo, y recién volve&#341;e el sábado a la noche, con lo cual podré recibir mails, pero desde una PC con windows (jaja, aunque me contaron que por estos lares esta es una mala palabra), así es que hasta ese momento no podré seguir con la lucha.
Recién podré seguir intentando la instalación a partir del domingo.
Ya suena repetitivo, pero en verdad MUCHAS GRACIAS por tu ayuda y tu paciencia !!!!

Graciela

> **luks911 said:**
> Tenés razón, me estaba guiando por un tutorial para una versión 
de Ubuntu más vieja. Perdón.
Ahora, me parece que la cámara debería funcionar sin tocar mucho más. Para ver qué está pasando decime qué versión de Ubuntu usás, contame cómo probaste la cámara (una forma es ejecutando en una terminal el comando gstreamer-properties y en el cuadro de diálogo que se abre ir a la pestaña Video, en Default Input chequear que esté seleccionada la cámara y clickear en test) y, por último, decime qué te devuelve en la terminal el comando 
[code]lsmod | grep gs
```Después vemos cómo seguimos. En el peor de los casos habrá que bajar y compilar el driver. Pero son sólo seis sencillos pasos.

---

### Post by luks911 on 2009-10-28
Bueno, para cuando vuelvas a tu Ubuntu: el problema no es con la cámara, si no con el emesene. Falta un paquete necesario para usar esa funcionalidad del programa. Para instalarla es más sencillo desde Ubuntu 9.10, porque ya está incluida en los repositorios, sólo tendrías que ejecutar
```
sudo aptitude install python-libmimic
```
Pero como estás en 9.04, hay que hace un poco más de lío. Son los siguientes pasos siempre en una terminal (paso las indicaciones por terminal porque es más fácil copiar y pegar los comandos ahí):
1) Bajás los paquetes necesarios
```
wget http://mirrors.kernel.org/ubuntu/pool/main/p/python-support/python-support_1.0.3ubuntu1_all.deb http://mirrors.kernel.org/ubuntu/pool/universe/libm/libmimic/libmimic0_1.0.4-2_i386.deb http://mirrors.kernel.org/ubuntu/pool/universe/libm/libmimic/python-libmimic_1.0.4-2_i386.deb
```

2) Los instalás así (te va a pedir la contraseña):
```
sudo aptitude install python2.5 python2.5-minimal
```
```
sudo dpkg -i python-support_1.0.3ubuntu1_all.deb
```
```
sudo dpkg -i libmimic0_1.0.4-2_i386.deb
```
```
sudo dpkg -i python-libmimic_1.0.4-2_i386.deb
```

Después de eso, debería funcionar la cámara en el emesene. A pesar de que hay que instalar paquetes de versiones posteriores, lo probé en una máquina con 9.04 y no hay conflictos.

Un saludo

PD: Ah, cuando antes te dijo que no encontraba la orden es porque había que ejecutar lsmod | grep gs, sin el "[code]" adelante, je :-P De todos modos, eso ya no es necesario.

---

### Post by anarko on 2009-10-28
Hola puedo intentar yo?
Porque mepa que la estan metiendo en un embrollo del cual se le va a hacer difil salir.

Eowynt hace lo siguiente, anda al menu aplicaciones -> añadir quitar programas 
Esto te abre una ventana por la cual podes instalar/desinstalar software en ubuntu, ahi marca "todas las aplicaciones disponibles" y en el cuadro para buscar busca : cheese, abajo te deberia aparecer en el listado algo como " Cheese - Cabina de camara web", marcas el cuadradito para que lo instale y le das al boton "Aplicar"
Luego de que termine de hacer todo el proceso de descarga e instalacion en el menu aplicaciones -> Graficos deberia aparecer el menu para iniciar Cheese, algo como "Fotomaton de camara web Cheese"

Cheese es un programita para jugar con la webcam, tambien sirve para ver si la camarita fue correctamente detectada por ubuntu, ya que los programas como emesene o amsn o lo quemsnfuera todavia esta muy verdes con el tema de la webcam, esto no quiere decir que la camara no funcione en ubntu sino que los desarrolladores todabia no han terminado la parte de la transmision de video.

Bueno abri el Cheese y fijate si se ve la camarita, con eso te sacas la duda sin recurrir a primero recompilar modulos del kernel que ya vienen por defecto en el kernel default de ubuntu o hacer cosas raras como instalar libmimic.

Si no llega a funcionar la camara con Cheese, hace lo siguiente, abri la terminal que te mencionaron antes, desenchufa la camarita ( todo esto suponiendo que es USB, lo que asumo una suposicion acertada ) y volve a enchufarla. Luego de esa accion en la terminal escribi : "dmesg" sin las comillas y dale enter.

Luego de un monton de lineas que no nos interesan deberia aparecerte algo como, que deberian ser las ultimas lineas ya que has desconectado y conectado la camara, esto lo delimitas cuando dice algo como "[113930.637662] usb 2-7: USB disconnect, address 6" Donde dice usb 2-7 address 6 puede variar dependiendo de que enchufe USB estes usando vos, pero basicamente es eso.
Deberias ver algo como. 

```

[180244.643369] usb 2-7: USB disconnect, address 6
[180244.647258] gspca: disconnect complete
[180248.744051] usb 2-7: new full speed USB device using ohci_hcd and address 7
[180248.976675] usb 2-7: configuration #1 chosen from 1 choice
[180248.978171] gspca: probing 046d:092e
[180249.181272] gspca: probe ok

```
Ami me esta diciendo que el modulo gspca detecto OK la camarita, pero basados en esta informacion si a vos no te funciono podremos ver el porque. 

Saludos y espero que sirva.

---

### Post by luks911 on 2009-10-28
> **anarko said:**
> Hola puedo intentar yo?
Porque mepa que la estan metiendo en un embrollo del cual se le va a hacer difil salir.

Eowynt hace lo siguiente, anda al menu aplicaciones -> añadir quitar programas 
Esto te abre una ventana por la cual podes instalar/desinstalar software en ubuntu, ahi marca "todas las aplicaciones disponibles" y en el cuadro para buscar busca : cheese, abajo te deberia aparecer en el listado algo como " Cheese - Cabina de camara web", marcas el cuadradito para que lo instale y le das al boton "Aplicar"
Luego de que termine de hacer todo el proceso de descarga e instalacion en el menu aplicaciones -> Graficos deberia aparecer el menu para iniciar Cheese, algo como "Fotomaton de camara web Cheese"

Cheese es un programita para jugar con la webcam, tambien sirve para ver si la camarita fue correctamente detectada por ubuntu, ya que los programas como emesene o amsn o lo quemsnfuera todavia esta muy verdes con el tema de la webcam, esto no quiere decir que la camara no funcione en ubntu sino que los desarrolladores todabia no han terminado la parte de la transmision de video.

Bueno abri el Cheese y fijate si se ve la camarita, con eso te sacas la duda sin recurrir a primero recompilar modulos del kernel que ya vienen por defecto en el kernel default de ubuntu o hacer cosas raras como instalar libmimic.

Si no llega a funcionar la camara con Cheese, hace lo siguiente, abri la terminal que te mencionaron antes, desenchufa la camarita ( todo esto suponiendo que es USB, lo que asumo una suposicion acertada ) y volve a enchufarla. Luego de esa accion en la terminal escribi : "dmesg" sin las comillas y dale enter.

Luego de un monton de lineas que no nos interesan deberia aparecerte algo como, que deberian ser las ultimas lineas ya que has desconectado y conectado la camara, esto lo delimitas cuando dice algo como "[113930.637662] usb 2-7: USB disconnect, address 6" Donde dice usb 2-7 address 6 puede variar dependiendo de que enchufe USB estes usando vos, pero basicamente es eso.
Deberias ver algo como. 

```

[180244.643369] usb 2-7: USB disconnect, address 6
[180244.647258] gspca: disconnect complete
[180248.744051] usb 2-7: new full speed USB device using ohci_hcd and address 7
[180248.976675] usb 2-7: configuration #1 chosen from 1 choice
[180248.978171] gspca: probing 046d:092e
[180249.181272] gspca: probe ok

```
Ami me esta diciendo que el modulo gspca detecto OK la camarita, pero basados en esta informacion si a vos no te funciono podremos ver el porque. 

Saludos y espero que sirva.

Fijate que más arriba la cámara fue probada con gstreamer-properties y funciona. El problema es con el emesene.

---

### Post by guillermolisi on 2009-10-28
> **anarko said:**
> Hay Hay Hay tenes razon,mil perdones, sabes que lei todo el Th viendo si habia logrado probar la camarita y lo pase por alto, = ami me gusta mas el cheese porque despues me cuelgo con los efectos :)

Je Je Ya que estamos me prendo a ver si me explican como hacer andar la camarita con el emesene, ya tengo instalado libmimic la camarita andando ( probada con cheese :p ) en las opciones del emesene la puedo seleciconar y me aparece el preview, pero despues cuando la quiero usar, osea enviar video desde el emesene no hace nada, vuelvo a las propiedades y no esta seleccionada la camarita.
Osea cuando un contaco requiere ver mi camara aparece la ventanita de preview, pero sin imagen y la otra persona no ve nada le dice que no se peude conectar.

Desde ya muchas gracias.
Movido a un [nuevo thread especifico de software]("http://ubuntuforums.org/showthread.php?t=1303595").

---

### Post by guillermolisi on 2009-10-28
> **luks911 said:**
> Fijate que más arriba la cámara fue probada con gstreamer-properties y funciona. El problema es con el emesene.
Con lo cual este thread estaria para ser marcado como resuelto.

Todo lo referido a webcam con emesene puede ir [aqui]("http://ubuntuforums.org/showthread.php?t=1303595").

---

