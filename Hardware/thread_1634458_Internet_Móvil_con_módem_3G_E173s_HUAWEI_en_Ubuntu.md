---
title: "Internet Móvil con módem 3G E173s HUAWEI en Ubuntu 10.10"
date: 2010-11-30
forum: Hardware
---

### Post by djthree on 2010-11-30
[MI ANTERIOR TUTORAIL ES OBSOLETO, AQUI DEJO UNA FORMA MAS FACIL Y SIMPLE DE CONECTAR CON EL MDEM HUAWEI E173s Y UBUNTU 11.04]

FUENTE: [http://www.mikejr1.es/linux/index.php/-aula-linuxera-/-aula-linuxera-/30-aula-linux/2664-huawei-e173s-en-ubuntu-1010.html]("http://www.mikejr1.es/linux/index.php/-aula-linuxera-/-aula-linuxera-/30-aula-linux/2664-huawei-e173s-en-ubuntu-1010.html")

Hace dias le monté un ordenador en el que instalé Ubuntu 10.10.Bueno, ya sé que hay una versión más nueva, pero para empezar me parecia más estable Maverick.

Pues bién, el rollo vino cuando conecté el modem usb Huawei E173s que te dá la compañía con la que contratas internet.

Para Huawei, se requieren los paquetes usb_modeswitch, que ya fueron incluidos en los repositorios de Ubuntu desde Lucid Lynx si mal no recuerdo.

El problema, es que la tecnología avanza muy rápido y esos paquetes ya no sirven para ese modelo de Huawei, entonces te lo detecta como una simple tarjeta SD, en lugar de como modem.

Probé en mi Oneiric y vi que funcionaba a la primera por que ya van por la versión 1.1.8-1 , así que lo que hice fué buscarlos en la web de Ubuntu.

[usb-modeswitch-data_20110714-1_all.deb]("http://packages.ubuntu.com/oneiric/all/usb-modeswitch-data/download") (Que es el que hay que instalar en primer lugar para que te deje instalar el siguiente)

Para máquinas AMD64

[usb-modeswitch_1.1.8-1_amd64.deb]("http://packages.ubuntu.com/oneiric/amd64/usb-modeswitch/download")

Para máquinas Intel x86
[usb-modeswitch_1.1.8-1_i386.deb]("http://packages.ubuntu.com/oneiric/i386/usb-modeswitch/download")

El problema, es que en Maverick está predetermiado el Centro de Software para que instale paquetes .deb y dá fallo y no los instala, así que lo que hice fué instalar Gdebi, que sinceramente, siempre me gustó más para ésta labor.

    sudo apt-get install gdebi

Una vez instalado todo, hay que esperar un poquito a que lo detecte y ya se puede configurar la conexión en el Network-manager tal como os contaba hace tiempo en ESTE artículo.

Y eso es todo. Otro Ubuntero más y otro ser conectado con el mundo.

---

### Post by Alejo. on 2011-02-02
Hola! Espero depronto no repetir la misma pregunta de nuevo o algo, soy nuevo acá y aún me pierdo dentro del foro.

La situación que tengo por comentar ( que espero me puedas sugerir algo) es la siguiente:
Tengo el módem ZTE MF626, utilizaba antes la versión de Ubuntu 10.04, a la cual después de conectar el módem, simplemente dabas click derecho expulsar y ya podías usarlo para navegar. Recién actualicé a Ubuntu 10.10 y se me presentó el problema de que el módem no era reconocido por Ubuntu. A sugerencia de un amigo descargué el ISO del Ubuntu y lo corrí sin instalarlo, es decir desde el cd y probé nuevamente el módem. Cuando lo conecté inmediatamente se pudo configurar la conexión a Internet sin problemas y navegar de manera correcta, a lo que decidí instalar la versión desde cero. Pero sucede que ya el Ubuntu 10.10 instalado de cero, tampoco reconoce el módem y sucede exactamente lo mismo que vos comentas con el módem HUAWEI, aparece pero como dispositivo de almacenamiento.

La pregunta es entonces porque sin instalar el sistema operativo (ejecutándolo desde el cd) el módem funcionó correctamente y después de finalizada la instalación del Ubuntu 10.10 no?
La otra cosa es que puedo seguir este mismo tutorial pero acomodarlo al ZTE verdad?

Muchas gracias !!!

---

### Post by mmva on 2011-03-05
> **djthree said:**
> Soy nuevo en el uso de UBUNTU y me gustaría compartir los pasos para conectarse a INTERNET MÓVIL con módem 3G marca: HUAWEI Modelo: E173s (No cofundir con el modelo E173 -sin "s" al final- ya que son distintos). Ya que me ha costado bastante y tuve que recorrer varios foros para lograr que funcione, quisiera dejar mi aporte y en un solo post volcar la mayor cantidad de información para poder lograr la conexión a Internet Móvil con UBUNTU 10.10

En mi caso me conecto por medio de la empresa PERSONAL pero debería funcionar con otras empresas como CLARO o MOVISTAR.

**_EMPEZAMOS_**:

Versión de UBUNTU: 10.10
Marca del Módem 3G: HUAWEI
Modelo: E173s

**_DESCRIPCIÓN DEL PROBLEMA_**: Cuando conectamos en  módem al puerto USB de la PC/Notebook con Ubuntu 10.10 el sistema no lo detecta como módem sino como unidad de almacenamiento ya que en el interior del dispositivo hay una ranura para insertar una memoria Micro SD. Por ese motivo por más que configuremos correctamente la conexión de internet móvil la misma no funciona por no haberse detectado el módem como nuevo hardware.    

(para poder realizar el tutorial debe estar instalado el paquete usb_modeswitch y usb-modeswitch-data, en mi caso ya estaban instalados, pero si necesitan verificar que están  instalados deben ir a Sistema -> Administración -> Gestor de paquetes Synaptic y en el buscador poner "usb-modeswitch". Aparecerán los dos paquetes mencionados. Si no están instalados, los marcamos para instalar y aplicamos.)

[SIZE=4]**1) Crear la conexión con el asistente**[/SIZE]
[SIZE=2](Fuente: [http://www.jampudia.com/linux/configurar-internet-movil-en-ubuntu.html](http://www.jampudia.com/linux/configurar-internet-movil-en-ubuntu.html))[/SIZE]

Primero debemos dar clic sobre el indicador de gestor de red que se encuentra al pie de la fecha en el panel superior, una vez allí se abrirá un menú y debemos dar clic en Conexiones VPN, allí nos aparecerá un sub menú donde escogeremos la opción Configurar VPN.

[IMG]http://www.jampudia.com/wp-content/uploads/2010/08/vpn.png[/IMG]

Ahora nos aparecerá la ventana de conexiones de red, damos clic sobre la pestaña Banda Ancha Móvil, y damos clic sobre añadir.

[IMG]http://www.jampudia.com/wp-content/uploads/2010/08/vpn2.png[/IMG]

Nos aparecerá una ventana de asistente de configuración de banda ancha móvil, damos clic en adelante, luego nos aparecerá una lista de países donde seleccionaremos el país donde residimos y de donde por razones obvias es el país donde se encuentra el proveedor de servicios de su internet móvil.

[IMG]http://www.jampudia.com/wp-content/uploads/2010/08/vpn3-300x212.png[/IMG]


Ahora aparecerá una lista de los proveedores de internet escogemos el proveedor de nuestro módem y damos clic en adelante, por ultimo escogemos el plan preferiblemente dejarlo predeterminado y dar clic en adelante y por ultimo saldrá un resumen de toda la configuración y damos clic en aplicar.

Ya con esto tendremos configurada la conexión a internet móvil que luego utilizaremos para conectarnos cuando el módem haya sido correctamente reconocido.

[SIZE=4]**2) Reconocimiento de nuestro módem HUAWEI E173s**[/SIZE]
- Conectamos el módem a un puerto USB
- Abrimos una Terminal y ejecutamos el comando lsusb
Aplicaciones -> Accesorios-> Terminal
```
user@NOTEBOOK:~$ lsusb
```Dará como resultado algo como esto:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 012: ID 12d1:1c0b Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 174f:1107 Syntek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ma
```La linea que nos interesa es:
```
Bus 002 Device 012: ID 12d1:1c0b Huawei Technologies Co., Ltd. 

```Ahora vamos a crear un archivo con gedit que se llamará E173s, para esto en la terminal ejecutamos:
```
user@NOTEBOOK:~$ sudo gedit /etc/usb_modeswitch.d/E173s
```Se abrirá el editor de texto con un archivo vacío, dentro compiamos lo siguiente (copiar y pegar, o hacerlo "a mano"):
```
#########
# Huawei E173s

DefaultVendor=  0x12d1
DefaultProduct= 0x1c0b

TargetVendor=  0x12d1
TargetProduct= 0x1c05

CheckSuccess=20

MessageEndpoint= 0x0f
MessageContent="55534243000000000000000000000011060000000100000000000000000000"
```Guardamos el archivo y cerramos el editor de texto gedit.

Luego ejecutamos lo siguiente en la terminal:
```
user@NOTEBOOK:~$ sudo usb_modeswitch -c /etc/usb_modeswitch.d/E173s

```Ahora debería aparecer en la terminal algo como esto:
```
matias@SK-NOTEBOOK:~$ sudo usb_modeswitch -c /etc/usb_modeswitch.d/E173s

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 005 on bus 002 ...
Using endpoints 0x0f (out) and 0x8f (in)
Using endpoints 0x0f (out) and 0x8f (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: HUAWEI  
   Model String: Mass Storage    
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Setting up communication with interface 0 ...
Using endpoint 0x0f for message sending ...
Trying to send message 1 to endpoint 0x0f ...
 OK, message successfully sent
Resetting response endpoint 0x8f
 Error resetting endpoint: -71
Resetting message endpoint 0x0f
 Error resetting endpoint: -19
 Device is gone, skipping any further commands

Checking for mode switch (max. 20 times, once per second) ...
 Original device is gone already, not checking
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Found correct target device

Mode switch succeeded. Bye.
```LISTO. YA DEBERÍA ESTAR RECONOCIDO NUESTRO MÓDEM.
Lo verificamos ejecutando en la terminal:
```
user@NOTEBOOK:~$ lsusb
```entre las lineas que aparecen debería aparecer una como esta:
```
Bus 002 Device 012: ID 12d1:1c05 Huawei Technologies Co., Ltd.
```Por último nos queda modificar el archivo 40-usb_modeswitch.rules para que el modem sea correctamente reconocido cada vez que lo conectemos al puerto USB. Lo hacemos de esta manera:
En la terminal ejecutamos:
```
user@NOTEBOOK:~$ sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules 

```Abajo de esta linea:
```
# Huawei E173
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1557", RUN+="usb_modeswitch '%b/%k'"

```Creamos una nueva que se va a llamar "#E173s", debe quedar así:
```
# Huawei E173s
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="usb_modeswitch '%b/%k'"
```LISTO. Guardamos el archivo. Cerramos la terminal, desconectamos y volvemos a conectar el módem y se debería conectar automáticamente (recordar que en la config. del punto 1) debe quedar tildada la opción "Conectar Automáticamente")

Espero que les sea útil y los que saben más del tema les pido que revisen el tutorial a ver si esta bien hecho.

SALUDOS!

PD: Según la empresa PERSONAL para tener una navegación más eficiente deberíamos realizar cambios en el configuración de la conexión. Aún no los he realizado porque me esta funcionando bien con la configuración por defecto, ya les contaré que ocurre cuando lo haga. les dejo el link del tutorial para realizar los cambios: [http://www.personal.com.ar/servicios/datos/mejoratunavegacion.html](http://www.personal.com.ar/servicios/datos/mejoratunavegacion.html)




hola soy nuevo en la comunidad, veran mi problema es el siguiente: no puedo conectarme a internet con mi modem ALCATEL ONE TOUCH X220Y en Ubuntu 10.10, he realizado el procedimiento mencionado cambiando "12d1:1c0b" por "1bbb:0017" y "huawei" por "T & A Mobile Phones" porque es lo que me aparece en la consola al ejecutar "lsusb", al llegar a la ejecucion de: "]matias@SK-NOTEBOOK:~$ sudo usb_modeswitch -c /etc/usb_modeswitch.d/X220y" me devuelve el mensaje siguiente:"no founded original driver" o algo asi luego me dice que espere :"waiting ...."
y finaliza, no sale lo que me dices que deberia salir, tal vez me podrias dar una mano, gracias adelantadas

---

### Post by djthree on 2011-03-05
Alejo,

No tengo el nivel de conocimientos adecuados para responder tu pregunta, probá republicar la misma en el foro de hardware.

Saludos,
DjThree

> **Alejo. said:**
> Hola! Espero depronto no repetir la misma pregunta de nuevo o algo, soy nuevo acá y aún me pierdo dentro del foro.

La situación que tengo por comentar ( que espero me puedas sugerir algo) es la siguiente:
Tengo el módem ZTE MF626, utilizaba antes la versión de Ubuntu 10.04, a la cual después de conectar el módem, simplemente dabas click derecho expulsar y ya podías usarlo para navegar. Recién actualicé a Ubuntu 10.10 y se me presentó el problema de que el módem no era reconocido por Ubuntu. A sugerencia de un amigo descargué el ISO del Ubuntu y lo corrí sin instalarlo, es decir desde el cd y probé nuevamente el módem. Cuando lo conecté inmediatamente se pudo configurar la conexión a Internet sin problemas y navegar de manera correcta, a lo que decidí instalar la versión desde cero. Pero sucede que ya el Ubuntu 10.10 instalado de cero, tampoco reconoce el módem y sucede exactamente lo mismo que vos comentas con el módem HUAWEI, aparece pero como dispositivo de almacenamiento.

La pregunta es entonces porque sin instalar el sistema operativo (ejecutándolo desde el cd) el módem funcionó correctamente y después de finalizada la instalación del Ubuntu 10.10 no?
La otra cosa es que puedo seguir este mismo tutorial pero acomodarlo al ZTE verdad?

Muchas gracias !!!

---

### Post by EduardoAB on 2011-05-29
Quiero resaltar la excelente nota de "djthree" acerca de la conectividad del E173s en Ubuntu 10.10. 
Hoy, tengo un problema similar, pero relacionado con el E173, sin "s", y el Ubuntu 11.04 (Natty).
¿Podrá "djthree" o alguien con su buena actitud y conocimientos intentar responder?
Desde ya muy agradecido.

PD: hago notar que la configuración del VPN funcionó bien luego de haber chequeado con la gente de CLARO, pero nada pueden decir acerca de como continuar.....ni tan siquiera dan la más mínima sugerencia. Mal...muy mal!

---

### Post by biale on 2011-05-29
Claro E176, a secas. Basicamente hay dos técnicas, una usando Network Manager y la otra configurando Wdial a fuerza de comandos AT. Describo la primera y que fué probada en Lucid con kernel 2.6.35.

Si lsusb muestra al modem, vamos bien. Dejo que Network Manager genere una conección en forma automatica y luego la edito para que ande. Y sino la genero completa. Nombre de la conexión "Claro"

En la pestaña &#8220;Banda ancha Móvil&#8221; completamos con estos datos:

Numero: *99#
Usuario: clarogprs
Contraseña: clarogprs999
Nombre del AP: ba.amx
Red: &#8230;.. (vacío)
PIN: 1111   >> salvo que lo hayas modificado por algun otro valor

Yo obtuve estos datos usando el utilitario de Claro bajo Windows. No se en que casos cambian.

En la pestaña &#8220;Ajustes de IPV4&#8243; tiene que quedar en Método &#8220;Automático (PPP)&#8221;. O sea, a la larga funciona como los viejos modems con algun agregado.

En la pestaña &#8220;Ajustes de PPP&#8221; hay que dejar como Métodos permitidos de Autenticación únicamente PAP y CHAP. Para ello presionar el botón &#8220;Configurar Métodos&#8221; y desactivar las demás. Pareciera que hay que embocar con algún metodo que le guste "de una"

las otras opciones tienen que quedar:
Permitir compresión de datos BSD 	> SI
Permitir compresión de datos deflate 	> SI
Permitir compresión de cabeceras TCP	> SI
Echo > NO

Listo.

Te recomiendo probarlo primero en algun horario "de baja". Por ejemplo, al mediodía la red se clava incluso bajo windows. Si tomo direccion de IP y DNS, lo doy por conectado, aunque no transmita nada.

Suerte...

---

### Post by EduardoAB on 2011-06-02
Gracias Biale, hice lo que indicaste, que de alguna manera replica lo que ya había intentado pero sin éxito. Si alguien más puede ayudar se lo voy a agradecer.
Saludos

---

### Post by biale on 2011-06-02
Fijate si los logs tiran algo. Tambien si se pudiera probar con el nucleo de Maverick.

Si enciende led verde, azul, cyan...

---

### Post by asterix77 on 2011-06-03
Haz intentado con los proyectos de Betavine?

Hay dos aplicaciones: La primera es Betavine Connection Manager (BCM), y la otra es Vodafone Mobile Connect Card Driver (VMCCD)

Están pensadas para modelos Huawei 3g, y casi estoy seguro de que soporta los modelos e173.

Actualmente uso BCM con mi módem e176, claro que al hacer un lsusb en la terminal, me lo reconoce como E220 

Te dejo los links directos:  [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12) para el VMCCD

[https://forge.betavine.net/frs/?group_id=76](https://forge.betavine.net/frs/?group_id=76) para BCM.


Espero que te sirva

Saludos

PD: Sería interesante saber también que arroja el comando por consola lsusb, para saber si el módem es reconocido solo como unidad de almacenamiento; o si efectivamente lo reconoce como módem. Si solo lo reconoce como unidad de almacenamiento no lo vas a hacer funcionar con nada, y para ello debes instalar el paquete usb-modeswitch y también el usb-modeswitch-data desde la terminal o desde synaptic.

---

### Post by EduardoAB on 2011-06-03
Asterix. Soy nuevo en esto. Tengo una netbook HP con Windows 7 y con Ubuntu 11.04, y me resulta dificil saber cual de los .deb bajar, y luego de ellos necesito saber como instalarlos. En fin, agradezco desde ya tu ayuda.
Saludos

---

### Post by asterix77 on 2011-06-04
Ok

Estos son los deb que debes bajar:

[  bcm_2.99.12-1_all.deb]("https://forge.betavine.net/frs/download.php/654/bcm_2.99.12-1_all.deb")

[  python-messaging_0.5.9-1_all.deb]("https://forge.betavine.net/frs/download.php/652/python-messaging_0.5.9-1_all.deb")

[  usb-modeswitch-data_20100826-1betavine1_all.deb]("https://forge.betavine.net/frs/download.php/651/usb-modeswitch-data_20100826-1betavine1_all.deb")

[  wader-core_0.5.5-1_all.deb]("https://forge.betavine.net/frs/download.php/653/wader-core_0.5.5-1_all.deb")

Al descargarlos simplemente dales un doble click, y se instalarán en forma automática. En caso de que tengan dependencias, se descargarán en forma automática. Creo que existe un orden de instalación, no recuerdo cual, pero prueba a instalarlos uno a uno hasta que se instalen todos.

Espero que te sirva....

Saludos

---

### Post by EduardoAB on 2011-06-07
Asterix
Baje los archivos y comencé la instalación con el siguiente resultado:
1.- Instalé:** usb-modeswitch-data_20100826-1betavine1_all.deb **y me lo rechazó porque hay una versión más actualizada que ya está instalada. Resultado: OK-
2.- La secuencia continúa con la instalación de: python-messaging_0.5.9-1_all.deb.  Resultado: OK
3.- El tercer paso es instalar: wader-core_0.5.5-1_all.deb que no puede completarse porque el instalador necesita dos paquetes, y para ello hay que estar conectado a Internet.
Dichos paquetes son:
python-gudev
python-tz
4.- El cuarto y último paso, que no es posible completar si no se puede completar la instalación del anterior, es: bcm_2.99.12-1_all.deb

Como ves, el tema parece encaminado, y con tu ayuda es probable que llegue a buen término.
Desde ya agradecido
Eduardo

---

### Post by asterix77 on 2011-06-08
Eduardo:

Lo ideal sería que mientras configuras el internet móvil, te conectaras a internet de alguna otra forma. Yo me conectaría via cable, que es la forma más sencilla, y que generalmente se autoconfigura solo según el caso.


De todos modos si no se puede, existe la alternativa de descargar los paquetes dependientes directamente de los repositorios.

Acá te dejo el link donde aparecen los paquetes de natty, y también los que mencionas que te piden.


[http://packages.ubuntu.com/natty/python/](http://packages.ubuntu.com/natty/python/)

Solo ten cuidado cual bajas, debes hacerlo según tu arquitectura de 32 ó 64 bit.


Saludos

---

### Post by EduardoAB on 2011-06-08
Asterix
He instalado todos los paquetes, con la precaución de usar solo 32 bit. Tengo también la configuración de banda ancha hecha tal como funciona en W7. No obstante, el modem no es reconocido. Supongo que algo debo estar haciendo mal o me falta hacer. Si se te ocurre algo, por favor solo házmelo saber.
Cordialmente
Eduardo

---

### Post by asterix77 on 2011-06-09
Te sugiero que abras una terminal y escribas lo siguiente:

$lsusb

Este comando lo que hace es listar los dispositivos vinculados a los puertos usb que estén conectados. Quiero saber si realmente ubuntu reconoce tu módem como tal, o solo como una unidad de almacenamiento.

Puedes intentar hacer lo siguiente también. Abres una terminal y escribes lo siguiente:


1) sudo gedit /usr/local/lib/python2.6/dist-packages/wader/common/backends/nm.py

En el editor que se abre, busca la linea que contenga lo siguiente lo siguiente (teclas crtl+F)

'org.freedesktop.NetworkManager.Devices' (en mi archivo es la linea 144), y borra la letra s final, quedando de la siguiente forma:

'org.freedesktop.NetworkManager.Device', luego cierra el editor.

2) De vuelta en la terminal agrega lo siguiente para que el paquete wader trabaje tanto con Python 2.7 como también con Python 2.6:

$sudo ln -s /usr/local/lib/python2.6/dist-packages/wader /usr/local/lib/python2.7/dist-packages/wader

Finalmente intenta conectarte de nuevo.

Espero que te sirva.

Saludos

---

### Post by EduardoAB on 2011-06-09
Asterix
El lsub reconoce al modem, de hecho lo muestra con su nombre. Luego segui tus instrucciones, las que se completaron sin inconvenientes, tanto en la edición del archivo como en la última línea que indicaste.
Luego inserté el modem en el usb, y....todo siguió igual, es decir sin conectarse. Evidentemente, si vos te has podido conectar y yo no, yo debo estar haciendo algo mal. O tengo alguna configuración que no es correcta.
Si no te molesta, y aun te queda algo de ganas de seguir lidiando con este pesado usuario, te pasaría mi cuenta de skype o gmail para chatear y ver si algo podemos hacer juntos.
Cualquiera fuera tu respuesta para mi está bien y me siento agradecido por la buena actitud.
Cordialmente
Eduardo

---

### Post by asterix77 on 2011-06-09
Por simple curiosidad ¿el modem y el chip pertenecen a la misma compañía?

Te lo pregunto porque yo tube un impass con un modem al cual le inserté un chip de otra compañía, y no me funcionó ya que las empresas bloquean los modem usb para otras compañías, y en tal caso habría que desbloquear el modem.


Con respecto al chateo no tengo inconvenientes, eso sí tendría que ser durante la noche, y solo poseo cuenta de gmail.


Saludos

---

### Post by EduardoAB on 2011-06-10
Si. Son de la misma Cia (Claro). Mi correo es [email]eduardo.bosio@gmail.com[/email]
Saludos y nos vemos en la web

---

### Post by pfrancav on 2011-06-11
Que tal, tengo el mismo problema que Eduardo. Tambien tengo una HP con Natty.

Segui los pasos de este thread, que ademas son los mismos que se indican en otros foros, pero si bien el modemo parece reconocerlo, la conexion no se inicia.


```
# Huawei E173
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1557", RUN+="usb_modeswitch '%b/%k'"

# Huawei E173s
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="usb_modeswitch '%b/%k'"
```

```
Bus 002 Device 013: ID 12d1:1c05 Huawei Technologies Co., Ltd. 
Bus 002 Device 004: ID 10f1:1a16 Importek 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 004: ID 03f0:231d Hewlett-Packard 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Quizas lo que me falte entender es como levantar la conexion, porque yo agregue en el network-manager la conexion con Personal, tal como viene por default pero no se como activarla (le puse que se conecte automaticamente). Puedo ver algun archivo de log ?

---

### Post by pfrancav on 2011-06-11
Un dato mas, mi conexion es Arnet, no personal como puse en el post anterior. Cuando saco el modem y lo vuelvo a poner, parpadea la luz azul, por lo que lei en el manual eso significa que esta tratando de registrarse en una red 3g, lo cual sería correcto. Tambien aclaro que el modem funciona perfecto en Windows por lo que no hay un problema de desbloqueo y esas cosas.

Gracias, saludos

---

### Post by cameroon_3000 on 2011-09-08
Hola djthree 

Hola segui los pasos pero no se logra realizar el "switch "

 me sale esto en lsusb

Bus 001 Device 021: ID 12d1:1c24 Huawei Technologies Co., Ltd. 

con    gedit /etc/usb_modeswitch.d/E173s

# Huawei E173s

DefaultVendor=  0x12d1
DefaultProduct= 0x1c24

TargetVendor=  0x12d1
TargetProduct= 0x1c06

CheckSuccess=20

MessageEndpoint= 0x0f
MessageContent="55534243000000000000000000000011060000000100000000000000000000"


cambie  default producto,  en lugar de 0x1c0b  puse 0x1c24  que es como me lo identifica , corri 

usb_modeswitch -c /etc/usb_modeswitch.d/E173s


y obtuve esto


looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 019 on bus 001 ...
Using endpoints 0x0f (out) and 0x8f (in)
Using endpoints 0x0f (out) and 0x8f (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: HUAWEI  
   Model String: Mass Storage    
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Setting up communication with interface 0 ...
Using endpoint 0x0f for message sending ...
Trying to send message 1 to endpoint 0x0f ...
 OK, message successfully sent
Resetting response endpoint 0x8f
Resetting message endpoint 0x0f
 Error resetting endpoint: -71
 Device is gone, skipping any further commands

Checking for mode switch (max. 20 times, once per second) ...
 Original device is gone already, not checking
 Searching for target devices ...
 Searching for target devices ...

No new devices in target mode or class found

Mode switch has failed. Bye.


parece que si lo reconoce como almacenamiento pero no logra encontrar el "target" tienes alguna idea de por que podria ser?

gracias de antemano excelente post.

---

### Post by djthree on 2011-09-26
[MI ANTERIOR TUTORAIL ES OBSOLETO, AQUI DEJO UNA FORMA MAS FACIL Y SIMPLE DE CONECTAR CON EL MDEM HUAWEI E173s EN UBUNTU 11.04 Y TAMBIEN UBUNTU 10.10]

FUENTE: [http://www.mikejr1.es/linux/index.php/-aula-linuxera-/-aula-linuxera-/30-aula-linux/2664-huawei-e173s-en-ubuntu-1010.html]("http://www.mikejr1.es/linux/index.php/-aula-linuxera-/-aula-linuxera-/30-aula-linux/2664-huawei-e173s-en-ubuntu-1010.html")

Hace dias le monté un ordenador en el que instalé Ubuntu 10.10.Bueno, ya sé que hay una versión más nueva, pero para empezar me parecia más estable Maverick.

Pues bién, el rollo vino cuando conecté el modem usb Huawei E173s que te dá la compañía con la que contratas internet.

Para Huawei, se requieren los paquetes usb_modeswitch, que ya fueron incluidos en los repositorios de Ubuntu desde Lucid Lynx si mal no recuerdo.

El problema, es que la tecnología avanza muy rápido y esos paquetes ya no sirven para ese modelo de Huawei, entonces te lo detecta como una simple tarjeta SD, en lugar de como modem.

Probé en mi Oneiric y vi que funcionaba a la primera por que ya van por la versión 1.1.8-1 , así que lo que hice fué buscarlos en la web de Ubuntu.

[usb-modeswitch-data_20110714-1_all.deb]("http://packages.ubuntu.com/oneiric/all/usb-modeswitch-data/download") (Que es el que hay que instalar en primer lugar para que te deje instalar el siguiente)

Para máquinas AMD64

[usb-modeswitch_1.1.8-1_amd64.deb]("http://packages.ubuntu.com/oneiric/amd64/usb-modeswitch/download")

Para máquinas Intel x86
[usb-modeswitch_1.1.8-1_i386.deb]("http://packages.ubuntu.com/oneiric/i386/usb-modeswitch/download")

El problema, es que en Maverick está predetermiado el Centro de Software para que instale paquetes .deb y dá fallo y no los instala, así que lo que hice fué instalar Gdebi, que sinceramente, siempre me gustó más para ésta labor.

    sudo apt-get install gdebi

Una vez instalado todo, hay que esperar un poquito a que lo detecte y ya se puede configurar la conexión en el Network-manager tal como os contaba hace tiempo en ESTE artículo.

Y eso es todo. Otro Ubuntero más y otro ser conectado con el mundo.

---

