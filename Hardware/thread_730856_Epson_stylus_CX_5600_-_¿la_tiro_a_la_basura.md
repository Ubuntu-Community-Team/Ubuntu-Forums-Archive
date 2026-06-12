---
title: "Epson stylus CX 5600 - ¿la tiro a la basura?"
date: 2008-03-21
forum: Hardware
---

### Post by GGsalas on 2008-03-21
Hola, acabo de comprarme una impresore multifunción EPSON  stylus CX 5600 y estoy agotado de hacer pruebas, de enviar mails al soporte técnico de EPSON y buscar en internet, les resumo las pruebas que hice:

- Con el driver para Epson Stylus D68 - CUPS+Gutenprint v5.0.1 Simplified, con URI del dispositivoi: epson:/dev/usb/lp0 y otra prueba con el que detecta de forma automatica.

- Con el driver para Epson Stylus CX3810 - CUPS+Gutenprint v5.0.1 Simplified,  con URI del dispositivoi: epson:/dev/usb/lp0 y otra prueba con el que detecta de forma automatica.

También hice muchas pruebas cambiando el colore de impresion que por defecto viene en rgb lo puse en CMYC y en CMY color (este último funcionó) y muchas otras pruebas de desesperado, sin sentido en la configuración. 
[B]
El error es claro, estpy enviando a imprimir 10 páginas desde un PDF (primero con evince probe y luego con adobe acrobat) la primer página la imprime, la segunda da error y se queda atascada la página. Para que se vaya el error de la memoria tengo que apagar y colver a encender la máquina.[/B]

Espero que alguien sepa como solucionar la verdad es que siento ganar de patearla, es la última prueba que se me ocurre.

Gracias,
saludos.

---

### Post by Apokalyptica79 on 2008-03-21
Hola encontré un enlace te dejo a ver si alguno te sirve:
[http://jrballesteros05.blogspot.com/]("http://jrballesteros05.blogspot.com/")
Saludos y espero te sirva.

---

### Post by GGsalas on 2008-03-21
Gracias Apokalyptica79, por lo que veo el tutorial es para hacer funcionar el scanner, mi problema es aún más básico, pero no he leído completamente el post, asi que me dispongo a hacerlo. 

Muchas gracias por la ayuda, luego te cuento si me sirvió: espero que no haya caído mal el tono de mi pedido de ayuda, ahora que lo vuelvo a leer parece medio agresivo, pero obviamente es mi propia calentura por no poder hacer funcionar esta impresora.  

Nada mas, saludos.

---

### Post by Apokalyptica79 on 2008-03-21
Hola acá encontré otro enlace a ver si este es más útil que el anterior.
[http://forums.linux-foundation.org/read.php?26,2974,3204]("http://forums.linux-foundation.org/read.php?26,2974,3204")
Suerte con este.

---

### Post by rojojuan on 2008-03-21
Por lo que leí, todavía no está soportado.
Alguien la hizo funcionar con otro driver.
Te dejo el enlace por si te sirve:

[http://forums.linux-foundation.org/read.php?26,2974](http://forums.linux-foundation.org/read.php?26,2974)

---

### Post by GGsalas on 2008-03-21
rojojuan y Apokalyptica79 la página que me pasaron la habia encontrado en una de mis búsquedas, sin embargo hago lo que dicen, de probar con el driver de 3810 y de la D68 pero con ninguno funciona. Lo raro es que o encuentro que les de el mismo error que a mi, que se traba en la segunda hoja, porque a mi la primera la imprime bien.

Apokalyptica79 la página de el Scanner de la impresora sólo habla de eso, por lo cual, hasta no hacer que imprima bien no voy a hacer nada, igual la agendo por si necesito escanear. Gracias.

Saudos.

---

### Post by faustileon on 2008-04-07
Hola GGsalas.  Tengo el mismo multifunción que vos andando perfectamente la impresora y el scanner en Gutsy Gibbon.  Busqué mucho en Internet, usé un par de tutoriales hasta que el tercerop me funcionó, bajando drivers de una página de EPSON (no exactamente de EPSON, sino de una subsidiaria que se encarga del tema).  Esta noche te paso los datos.  Saludos y no pierdas la fe, porque en los últimos dos años Ubuntu me demostró que prácticamente todo se puede.

---

### Post by faustileon on 2008-04-07
Bien.  Ahora estoy en casa.  Lo que bajé (pero no instalé) es el Photo Image Print System (PIPS) de Avasys para RedHat que, aparentemente funciona en Debian y Ubuntu.  No lo instalé porque me funciona OK así:
Epson Stylus D68 - CUPS+Gutenprint v5.0.1 Simplified
Imprimo perfecto.  Claro que, hasta hoy no había probado con PDF's.  Pero lo acabo de hacer perfecto con el Evince 2.20.1 usando poppler 0.6.2, en RGB, en calidad Standard y tambien en calidad Best.  Se me clavó una vez en calidad Economy, pero después no pasó nada.
Configuración:
En Estado, todo tildado, en Políticas de error retry-job y en las de operación default.  Mensajes none los dos.
No sé qué más decirte (¿seguro que tus puertos USB son 2.0? supongo que sí, sobre todo si la máquina tiene menos de 3 ó 4 años, pero...)
Te dejo el link para descargar el PIPS (hay varios HOW-TO's apenas googleando acerca de cómo instalarlo en UBUNTU).  En esta página podés descargarte, además, drivers para el scanner que sí instalé y me andan bárbaro.
Un abrazo y espero no haberte generado muchas expectativas, es que me acordaba falsamente haber instalado el PIPS, pero no, había instalado Image Scan! for Linux (Iscan que funciona OK con Xsane). 

El link para bajar PIPS e Iscan
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

link sacado de:
[http://ohioloco.ubuntuforums.org/showthread.php?t=627471](http://ohioloco.ubuntuforums.org/showthread.php?t=627471)

---

### Post by GGsalas on 2008-05-15
Con la actualización a Ubuntu 8.04 me encontré con la excelente noticia que **¡la impresora se instala solita en el sistema y funciona bien!**

Una vez logrado mi mayor objetivo voy por más: ahora quiero que funcione el scanner (es multifunción), para esto seguí unos tutoriales que encontré, dicen un procedimiento parecido, que lamentablemente no me funcionó:

[http://ubuntuforums.org/showthread.php?t=627471&highlight=dx4450](http://ubuntuforums.org/showthread.php?t=627471&highlight=dx4450)
[http://www.ceportela.com.ar/2008/04/21/configurando-una-epson-stylus-cx5600-en-ubuntu-710-%E2%80%9Cgusty-gibbon%E2%80%9D/](http://www.ceportela.com.ar/2008/04/21/configurando-una-epson-stylus-cx5600-en-ubuntu-710-%E2%80%9Cgusty-gibbon%E2%80%9D/)

Ahora estoy viendo que hay una página donde dice que hay un driver nuevo para el scanner de la impresora epson cx5600 pero no tiene un link de descarga: [http://actualizaci-n-del-driver-del-esc-ner-eps.software.informer.com/](http://actualizaci-n-del-driver-del-esc-ner-eps.software.informer.com/)

Por último, sin haber logrado hacer funcionar el scanner veo encendida la luz roja en la impresora que indica el faltante de tinta y me pregunto ¿cual de los 4 cartuchos deberé reemplazar? Ubuntu no dice nada :/

Saludos, y disculpas por llevar mi largo suplicio con esta impresora al foro, pero es por lo que tengo que pasar en este momento.

---

### Post by faktorqm on 2008-05-16
Hola, a mi me encantan las cosas dificiles, asi que te voy a intentar hacer funcionar tu ""aparato"" :P

**[COLOR="Red"]AVISO: NO ANDA PARA 64 BITS[/COLOR]**

Voy a hacer una fusión de los tutoriales que pasaste y algunas consideraciones que la verdad me parecen razonables dentro del entorno.

Primero, hay que conectar el scanner y tenerlo prendido y saber que realmente lo está. Tirá el comando "lsusb" para ver si te lo muestra.

Luego, hay que desinstalar el paquete libsane-extras por que definitivamente no anda.

```
sudo apt-get remove libsane-extras-dbg libsane-extras-dev libsane-extras
```

Ahora instalamos el sane, sus utilidades y las herramientas de compilación del driver:

```
sudo apt-get install sane sane-utils xsane build-essential gcc binutils automake
```

Ahora, nos bajamos el driver de la siguiente pagina:

```
wget http://lx1.avasys.jp/iscan/2.10.0/iscan_2.10.0-1.tar.gz
```

Ahora lo descomprimimos:

```
tar xvzf iscan_2.10.0-1.tar.gz
```

Ahora nos metemos en el directorio del driver y lo compilamos

```
cd iscan_2.10.0-1
```
```
./configure --prefix=/usr
```
```
make
```
```
sudo make install
```

Ésta parte es la más crucial, la más importante. Si falla esto no pasa nada. Si te tira error no dudes en postear toda las salida de comandos completa para ver que paso en el medio y asi terminar la compilacion.
Si no está completa la compilación, lamentablemente no podemos seguir.

Si todo salió bien, ahora deberemos editar un par de archivos:

```
sudo gedit /etc/sane.d/dll.conf
```

Una vez abierto el archivo, comentamos la linea "epson" y agregamos abajo "epkowa". Debe quedar asi:

```
#epson
epkowa
```

Guardamos y editamos otro:

```
sudo gedit /etc/sane.d/epkowa.conf
```

Una vez abierto el archivo, comentamos la linea "scsi EPSON" y debe quedar asi:

```
#scsi EPSON
```

Y TAMBIEN DEBEMOS DESCOMENTAR LA LINEA USB:

antes: ```
#usb
```

debe quedar: ```
usb
```

Guardamos.

Bueno entonces hasta acá, instalamos el sane, instalamos el driver, y le dijimos que se conecta por usb. Ahora vamos a agregar el scanner al sistema. Para esto editamos:

```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```

y agregamos la siguiente linea:

```
# Epson Stylus CX-4300 CX-4400 CX-4450 CX-5500 CX-5600 DX-4400 DX-4450
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="083f", MODE="664", GROUP="scanner"
```

0x04b8 es el numero en hexadecimal del vendedor, o sea, Epson.
0x083f es el numero en hezadecimal del modelo del equipo, o sea, cx-5600.

Guardamos y salimos. Ahora vamos a ver si sane """lo ve""":

```
sane-find-scanner -q
```

Te tiene que tirar algo parecido a esto:

```
found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error] at libusb:001:003
```

Bueno, ahora volvemos a editar el archivo:

```
sudo gedit /etc/sane.d/epkowa.conf
```

EN TODAS LAS LINEAS QUE COMIENCEN CON **USB** LES DEBEMOS PONER EL SIMBOLO "#" (numeral) ADELANTE y luego en otra linea agregar:

```
usb 0x04b8 0x083f
```

Guardamos y salimos. 

Ahora vamos a &#8220;Aplicaciones -> Gráficos -> Escáner de imágenes Xsane&#8221; y debería funcionar todo a la perfección.

Capaz podes tener problemas de permisos sobre las cosas. Si no llegas a tener permisos por algo en especial lo que podemos probar es lo siguiente:

```
sudo chmod 0755 /usr/bin/xsane
```

AUNQUE NO DEBERIAMOS TOCAR COSAS DE /usr/bin, lo que pasa es que si lo queremos hacer "bien" deberiamos crear un grupo "escaner", meter al usuario, y es mas lio, pero seria una solucion muchisimo mas segura y sensata, poniendole 755 cualquiera viene y escanea.

Aparte también podemos probar sobre el dispositivo en si, para ello si la salida del comando:

```
sane-find-scanner -q
```

fue:

```
found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error] at libusb:001:003
```

Debemos correr:

```
sudo chmod 0755 /proc/bus/usb/001/003
```

EN CAMBIO si la salida fue : 

```
found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error] at libusb:001:002
```

Debemos correr:

```
sudo chmod 0755 /proc/bus/usb/001/002
```

Y asi según nos devuelva el comando la información.

Bueno, espero que te haya servido, postea tus dudas, tus comentarios, tus agregados, tus salidas de compilación erróneas :P:P:P.
Salu2!!!!

---

### Post by sajnox on 2008-05-16
Lo leo y se me cae un lagrimon, demasiada bondad....

Te mereces cinco medallas.

---

### Post by GGsalas on 2008-05-18
> **faktorqm said:**
> 

Ahora nos metemos en el directorio del driver y lo compilamos

```
cd iscan_2.10.0-1
```
```
./configure --prefix=/usr
```
```
make
```
```
sudo make install
```

Ésta parte es la más crucial, la más importante. Si falla esto no pasa nada. Si te tira error no dudes en postear toda las salida de comandos completa para ver que paso en el medio y asi terminar la compilacion.
Si no está completa la compilación, lamentablemente no podemos seguir.



Hasta bajar el archivo e ir dentro de la carpeta, pude, a continuación muestro el error que tengo para instalar:

```
$ ./configure --prefix=/usr
checking[COLOR="DarkOrange"] ... 
... múchas líneas de checking ... a continuación la única que da error:[/COLOR]
checking for GDK_IMLIB... configure: error: Package requirements (imlibgdk) were not met:

No package 'imlibgdk' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDK_IMLIB_CFLAGS
and GDK_IMLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

```
$ make
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
```

```
$ sudo make install
[sudo] password for gabi: 
make: *** No hay ninguna regla para construir el objetivo `install'.  Alto.
```

Te agradezco muchísimo tu dedicación por ayudarme.

Un saludo.

---

### Post by faktorqm on 2008-05-18
hola, intentaste darle make y make install a algo que no existe... jijijiji :D

Bien, empecemos por instalar estos paquetes que creo son los que te faltan en tu sistema:

```
sudo apt-get install libgtk-dev gdk-imlib gdk-imlib-dev gdk-imlib1 gdk-imlib1-dev gdk-imlib11 gdk-imlib11-dev libltdl3 libltdl3-dev
```

Luego le das de vuelta a 
```
./configure --prefix=/usr
```
y te fijas que onda.
Si por alguna de esas cosas te tira el mismo cartel, tranquilamente podes probar con 

```
./configure --prefix=/usr/bin
```
y te fijas que onda.

SI TE TIRA EL MISMO CARTEL QUE ANTES, hace esto:

Primero, preguntamos a donde esta la configuracion de paquetes:

```
locate pkg-config
```

Debria dar una salida mas o menos parecida a esta:

```

faktorqm@the-edge:~$ locate pkg-config
/usr/bin/pkg-config
/usr/lib/ruby/1.8/pkg-config.rb
/usr/share/doc/pkg-config
/usr/share/doc/pkg-config/AUTHORS
/usr/share/doc/pkg-config/NEWS.gz
/usr/share/doc/pkg-config/README
/usr/share/doc/pkg-config/changelog.Debian.gz
/usr/share/doc/pkg-config/changelog.gz
/usr/share/doc/pkg-config/copyright
/usr/share/man/man1/pkg-config.1.gz
/var/lib/dpkg/info/pkg-config.list
/var/lib/dpkg/info/pkg-config.md5sums
faktorqm@the-edge:~$

```

y ahora le ponemos a la variable esa que supuestamente no esta configurada lo que nos tiro el comando de arriba:

```
export PKG_CONFIG_PATH=/usr/bin/pkg-config
```

y ahi le damos de vuelta a ./configure blabla.

Por supuesto que si no te anduvo tenes que postear la salida y comentarlo aca y nunca bajar los brazos ok? Espero que haya compilado aunque sea. Salu2!!

EDITO: Me habia olvidado, pero la variable LD_LIBRARY_PATH tiene precedencia antes que PKG_CONFIG_PATH al momento de compilar.

Para ver en que tenemos esto, hacemos (TE ADJUNTO IGUAL MIS SALIDAS ABAJO):

```
echo $LD_LIBRARY_PATH
```

Si no te muestra nada, haces 

```
locate ld.so.conf
```

y te tiene que mostrar algo precido a esto:

```

faktorqm@the-edge:~$ locate ld.so.conf
/etc/ld.so.conf
/etc/ld.so.conf.d
/etc/ld.so.conf.d/i486-linux-gnu.conf
/etc/ld.so.conf.d/kde4.conf
/etc/ld.so.conf.d/libc.conf
faktorqm@the-edge:~$ 

```

Entonces hacemos:

```
export LD_LIBRARY_PATH=/etc/ld.so.conf
```

y de vuelta le damos ./configure blabla.

Te adjunto aca mi salida de comandos todo en uno (el ultimo echo es para ver si realmente te tomo el cambio y no le pifiaste en algo, lo mismo lo podes usar para la variable del pkg config):

```

faktorqm@the-edge:~$ echo $LD_LIBRARY_PATH

faktorqm@the-edge:~$ locate ld.so.conf
/etc/ld.so.conf
/etc/ld.so.conf.d
/etc/ld.so.conf.d/i486-linux-gnu.conf
/etc/ld.so.conf.d/kde4.conf
/etc/ld.so.conf.d/libc.conf
faktorqm@the-edge:~$ export LD_LIBRARY_PATH=/etc/ld.so.conf
faktorqm@the-edge:~$ echo $LD_LIBRARY_PATH
/etc/ld.so.conf
faktorqm@the-edge:~$ echo $PKG_CONFIG_PATH
/usr/bin/pkg-config
faktorqm@the-edge:~$ 

```

Salu2!! :KS

---

### Post by GGsalas on 2008-05-18
Uf, os un Genio, aunque yo sigo con problemas.

Para mi, haber seguido tu paso a paso y ahora ver que Ubuntu reconoce el escáner es casi un acto de magia, no lo puedo creer. Sin embargo cuando pongo vista previa o escanear dice "Falló al encender el escaner: Argumento no válido. A pesar de que no se que significa ese cartel, como veo la luz roja en el escaner se que le falta tinta a la impresora, por eso mañana compro cartuchos y los cambio, aunque tendré que adivinar cual es el que se quedó sin tinta, seguro que es uno de los 3 colores.

Mañana pruebo y te cuento,
Saludos.

---

### Post by faktorqm on 2008-05-18
grosso!! proba a ver que pasa con eso de los cartuchos, pero interfiere con la escaneada? no deberia, si es asi los de epson son de terror...
Bueno, te recuerdo que para "ver mejor el error" siempre ayuda ejecutar el sane desde la consola y cuando te tira ese cartel revisar la consola a ver que errores te tiro, vos postealos tranquilo que el espacio es gratis :P:P
Salu2!

---

### Post by GGsalas on 2008-05-20
faktorqm, te cuento. Compré los cartuchos nuevos y seguía sin funcionar, asi que hice una prueba que es la de conectarla con un cable corto (la tenía conectada con un cable de 4 metros aprox. ¡¡¡Ahora el Escanner funciona!!!

Como no podía ser de otra manera tengo un nuevo problema: la impresora ha dejado de funcionar :P  El cartel que muestra cuando intento imprimir es que la impresora está conectada y esto no es posible porque estan los cartuchos nuevos, reconoce el scanner y además probé de utilizar la impresora como fotocopiadora y funcionó bien. A continuación transcribo el error que muestra cuando voy a "solucionar problemas":

```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x964c5e0>,
 'cups_instance': None,
 'cups_queue': 'Stylus_CX5600',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://EPSON/Stylus%20CX5600',
                       'printer-info': u'EPSON Stylus CX5600',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Epson Stylus CX5600 - CUPS+Gutenprint v5.0.2 Simplified',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'connecting-to-device'],
                       'printer-type': 8556556,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Stylus_CX5600'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'connecting-to-device'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [16],
 'test_page_job_status': [(16, 'Stylus_CX5600', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': 'Gutenprint Printing page 1, 31%',
 'printer-state-reasons': 'connecting-to-device'}
```

Saludos y gracias.

---

### Post by djthree on 2008-05-21
Che que grosso este thread.... tengo esa impresora y me anda ok la parte de impresion en Ubuntu 8.04 HARDY, pero el scnaer nunca lo use todavía, así espero que logren hacerlo andar, así me ahorran un par de pasos cuando me toque usarlo.
SALUDOS y gracias de antemano!

---

### Post by faktorqm on 2008-05-21
djthree y rretamar: les pido a los dos por favor que si tienen este modelo de multifuncion por favor hagan feedback, esto es, probar la guia y comentar si siguieron la guia paso a paso y sin tocar nada, o si tuvieron problemas y como los resolvieron, o si faltan pasos que tuvieron que hacer ustedes a mano, o si omitieron y les anduvo igual. 
Desde ya mis guias distan de ser perfectas, por lo tanto les agradeceria mucho que dieran su opinion al respecto. Salu2!

---

### Post by GGsalas on 2008-05-22
Hola, sigo intentando. Mi problema es que no funciona mi impresora, el scanner funciona a la perfección gracias al tutorial de faktorqm. 

No se si modifiqué algo mientas intentaba configurar el scanner o si fue un error inevitable del sistema, pero aunque pude imprimir una vez, ahora no. 

He ingresado a la configuración de CUPS en: [http://localhost:631/printers/](http://localhost:631/printers/) y encontré para mi impresora Epson Stylus CX5600 el siguiente error: "/usr/lib/cups/filter/pstoraster failed" (en la captura de pantalla se puede ver. 

También revisé el registro de errores y veo la siguiente lista (claro que hay varias líneas porque probé varias veces imprimir):

```
E [22/May/2008:09:04:12 -0300] PID 5913 (/usr/lib/cups/backend/usb) crashed on signal 9!
E [22/May/2008:12:57:18 -0300] Pause-Printer: Unauthorized
E [22/May/2008:12:57:32 -0300] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [22/May/2008:12:57:32 -0300] Pause-Printer: Unauthorized
E [22/May/2008:12:58:03 -0300] cupsdAuthorize: pam_authenticate() returned 10 (User not known to the underlying authentication module)!
E [22/May/2008:12:58:03 -0300] Pause-Printer: Unauthorized
E [22/May/2008:12:58:07 -0300] cupsdAuthorize: pam_authenticate() returned 10 (User not known to the underlying authentication module)!
E [22/May/2008:12:58:07 -0300] Pause-Printer: Unauthorized
E [22/May/2008:12:58:14 -0300] cupsdAuthorize: pam_authenticate() returned 10 (User not known to the underlying authentication module)!
E [22/May/2008:12:58:14 -0300] Pause-Printer: Unauthorized
E [22/May/2008:12:58:26 -0300] cupsdAuthorize: pam_authenticate() returned 10 (User not known to the underlying authentication module)!
E [22/May/2008:12:58:26 -0300] Pause-Printer: Unauthorized
E [22/May/2008:12:58:32 -0300] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [22/May/2008:12:58:32 -0300] Pause-Printer: Unauthorized
E [22/May/2008:12:58:42 -0300] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [22/May/2008:12:58:42 -0300] Pause-Printer: Unauthorized
E [22/May/2008:12:58:46 -0300] Pause-Printer: Unauthorized
E [22/May/2008:12:58:51 -0300] Resume-Printer: Unauthorized
E [22/May/2008:13:00:03 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:00:03 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:00:51 -0300] PID 6093 (/usr/lib/cups/filter/pstoraster) stopped with status 1!
E [22/May/2008:13:06:22 -0300] PID 6185 (/usr/lib/cups/filter/pstoraster) stopped with status 1!
E [22/May/2008:13:09:34 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:09:44 -0300] PID 6241 (/usr/lib/cups/filter/pstoraster) stopped with status 1!
E [22/May/2008:13:32:01 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:32:16 -0300] CUPS-Delete-Printer: Unauthorized
E [22/May/2008:13:32:22 -0300] [Job 29] Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4b8_83f_B08120712201114001_if1_printer_noserial": Permission denied
E [22/May/2008:13:32:22 -0300] PID 6382 (/usr/lib/cups/backend/hal) stopped with status 1!
E [22/May/2008:13:32:22 -0300] PID 6379 (/usr/lib/cups/filter/pstoraster) stopped with status 1!
E [22/May/2008:13:32:43 -0300] Purge-Jobs: Unauthorized
E [22/May/2008:13:33:30 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:33:56 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:34:13 -0300] PID 6462 (/usr/lib/cups/backend/epson) stopped with status 1!
E [22/May/2008:13:34:13 -0300] [Job 30] Unable to open parallel port device file: Permission denied
E [22/May/2008:13:34:14 -0300] PID 6459 (/usr/lib/cups/filter/pstoraster) stopped with status 1!
E [22/May/2008:13:34:24 -0300] Purge-Jobs: Unauthorized
E [22/May/2008:13:35:14 -0300] PID 6566 (/usr/lib/cups/backend/epson) stopped with status 1!
E [22/May/2008:13:35:14 -0300] [Job 31] Unable to open parallel port device file: Permission denied
E [22/May/2008:13:35:50 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:35:57 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:36:39 -0300] CUPS-Delete-Printer: Unauthorized
E [22/May/2008:13:36:48 -0300] CUPS-Delete-Printer: Unauthorized
E [22/May/2008:13:37:51 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:38:09 -0300] PID 6682 (/usr/lib/cups/filter/pstoraster) stopped with status 1!
E [22/May/2008:13:45:53 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:46:36 -0300] CUPS-Add-Modify-Printer: Unauthorized
E [22/May/2008:13:46:45 -0300] CUPS-Add-Modify-Printer: Unauthorized

```

Saludos.

---

### Post by faktorqm on 2008-05-22
Ahi tenes un problema de permisos, no se por que, pero algo que podrias probar es darle permisos al archivo y ver que hace. Esto lo hacemos con

```
sudo chmod 755 /usr/lib/cups/filter/pstoraster
```

La verdad es lo primero que se me ocurre. Ese archivo me parece que sirve para purgar los trabajos de la impresora, no lo puede ejecutar por que no tiene permisos, por lo tanto devuelve un error. Si no esto debe andar cerca. Proba y nos seguimos fijando si no funciona. Salu2!

---

### Post by GGsalas on 2008-05-22
Estoy _desde el live-cd de Ubuntu 8.04 _y ¡¡¡he logrado imprimir 4 páginas!!!

En mi instalación de Ubuntu, probé enchufando una impresora HP y la reconoció al instante y pude imprimir, sin embargo la ePSON cx5600 la desinstalé y reinstalé de todas las formas posibles y siempre da el mismo error que mencioné. 

Desde el live CD no encuentro ninguna configuración diferente a la que tengo en mi instalación.

faktorqm, es posible que sea un problema de permisos, pero no he tenido éxito con tu consejo. ¿Se te ocure algo menos agresivo que reinstalar Ubuntu?. A mi no :P por eso pregunto, justo ahora que tengo todo configurado y recién instalado me da pena borrarlo.

Saludos. Gracias.

---

### Post by GGsalas on 2008-05-23
Encontré un reporte de BUG para "pstoraster failed" pero parece que no se solucionó. 

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/130871](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/130871)

---

### Post by faktorqm on 2008-05-25
Mirá, a lo último de todo un chabon dice que lo soluciono poniendole permisos a todo el directorio.... yo te diria que pruebes y que de ultima despues lo vamos cambiando.

```
sudo chmod 755 -R /usr/lib/cups/filter/
```

Con eso le ponemos 755 a todos los archivos contenidos en ese directorio. Esperemos que funcione!! Salu2!

---

### Post by GGsalas on 2008-05-25
No funcionó. También (entiendo que con riesgo de seguridad) probé:
```
sudo chmod 755 -R /usr/lib/cups
```
y probé agregando mi usuario a todos los grupos :P Nada funcionó.

Encontré que mi error puede ser un BUG reportado en :

[https://bugzilla.redhat.com/show_bug.cgi?id=243038](https://bugzilla.redhat.com/show_bug.cgi?id=243038)

y en:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85488)

Ahora sucede que no se que hacer ¿si se soluciona este error va a haber un parche que deba aplicar o el sistema se actualizará solo?

Gracias

---

### Post by faktorqm on 2008-05-25
Bueno me pase leyendo lo que posteaste, parece que hay bardo grosso con eso, lo que yo no entiendo es como despues de haber instalado el scanner no te anda mas la impresora... habremos tocado algo que no debiamos? a otros con el mismo modelo y siguiendo mi tuto tuvieron problemaS?

Vamos a hacer algo, los permisos por ahora dejalos asi despues lo volvemos a poner como estaba. 

Proba esta solucion que uno dice que le sirvio:

```

chcon system_u:object_r:bin_t /usr/lib/cups/filter/pstoraster*
chown root:root /usr/lib/cups/filter/pstoraster*

```

Ahora, (sin hacer eso) mi directorio se ve asi:

```

faktorqm@the-edge:/usr/lib/cups/filter$ ls -la
total 500
drwxr-xr-x  2 root root  4096 2008-05-12 00:03 .
drwxr-xr-x 10 root root  4096 2008-04-29 21:12 ..
-rwxr-xr-x  1 root root  5824 2008-01-24 09:55 commandtocanon
-rwxr-xr-x  1 root root  5832 2008-01-24 09:55 commandtoepson
-rwxr-xr-x  1 root root  5848 2007-08-15 08:23 commandtoescpx
-rwxr-xr-x  1 root root  4816 2007-08-15 08:23 commandtopclx
lrwxrwxrwx  1 root root    12 2008-05-12 00:03 cupsomatic -> foomatic-rip
lrwxrwxrwx  1 root root    25 2008-05-12 00:03 foomatic-rip -> ../../../bin/foomatic-rip
-rwxr-xr-x  1 root root  4680 2008-04-21 17:18 gziptoany
-rwxr-xr-x  1 root root 43580 2008-04-21 17:18 hpgltops
-rwxr-xr-x  1 root root 26548 2008-04-21 17:18 imagetops
-rwxr-xr-x  1 root root 56608 2008-04-21 17:18 imagetoraster
-rwxr-xr-x  1 root root  4316 2008-04-21 17:15 oopstops
-rwxr-xr-x  1 root root 13252 2008-04-21 17:18 pdftops
-rwxr-xr-x  1 root root 43420 2008-04-21 17:18 pstops
-rwxr-xr-x  1 root root  1914 2008-04-09 11:11 pstopxl
-rwxr-xr-x  1 root root  1882 2008-04-09 11:11 pstoraster
lrwxrwxrwx  1 root root    13 2008-04-29 21:12 rastertodymo -> rastertolabel
-rwxr-xr-x  1 root root 14076 2008-04-21 17:18 rastertoepson
-rwxr-xr-x  1 root root 39312 2007-08-15 08:23 rastertoescpx
-rwxr-xr-x  1 root root 33736 2008-01-24 09:55 rastertogutenprint.5.0
-rwxr-xr-x  1 root root 13048 2008-04-21 17:18 rastertohp
-rwxr-xr-x  1 root root 16556 2008-04-21 17:18 rastertolabel
-rwxr-xr-x  1 root root 39832 2007-08-15 08:23 rastertopclx
-rwxr-xr-x  1 root root 28964 2008-02-12 13:45 rastertospl2
-rwxr-xr-x  1 root root  3560 2008-04-21 17:15 textonly
-rwxr-xr-x  1 root root 36928 2008-04-21 17:18 texttops
faktorqm@the-edge:/usr/lib/cups/filter$ 

```

Ahora si sigue sin andar, vamos a probar otra solucion:

Edita el archivo de blacklists con:

```
sudo gedit /etc/modprobe.d/blacklist
```

y agregale al final del archivo "blacklist ppdev" (sin comillas)

IMPORTANTE: EL ARCHIVO AL FINAL DEBE TENER UN ENTER. Exactamente despues de la "v" apretas enter, y lo guardas.

Este modulo sirve para cuando conectas una impresora por puerto paralelo, te la detecte automaticamente, pero lei entre todos esos bugs que traia problemas, asi que la desactivamos al inicio.

Para desactivarla ahora sin reiniciar hacemos:

```
sudo rmmod ppdev
```

Ahora editamos el grub para que el kernel arranque con una opcion nueva:

```
sudo gedit /boot/grub/menu.lst
```

la opcion es "usbcore.autosuspend=0" y lo vamos a gregar en la linea que bootea, esto es, (te pongo de ejemplo el mio)

```

title		Ubuntu 8.04
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9a4b9f99-b82a-4037-a734-f3e78ee9b8b4 ro quiet nosplash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

```

y queda asi:

```

title		Ubuntu 8.04
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9a4b9f99-b82a-4037-a734-f3e78ee9b8b4 ro quiet nosplash usbcore.autosuspend=0
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

```

Ahora si debemos reiniciar si o si para que tome los cambios. y proba a ver que pinta. :D
Espero haber sido de ayuda. Salu2!!!!

---

### Post by GGsalas on 2008-05-26
Probé gregando la opción usbcore.autosuspend=0 y cuando inicia la máquina aparece una opción nueva "Ubuntu 8.04" la selecciono y doceque no entiende la opción "usbcore.autosuspend=0" que la va a ignorar, luego se queda sin gacer nada.

Inicio con la opción habitual y pruebo imprimir una página de prueba. En [http://localhost:631/printers/Stylus_CX5600](http://localhost:631/printers/Stylus_CX5600) ya no da error, dice "Gutenprint Printing page 1, 3%" sin embargo no mprime y al rato el sistema muestra un cartel que dice que la impresora puede estar desconcetada. 

Otra: parece que yo no tengo el directorio /usr/lib/cups/filter$

```
gabi@gabi-desktop:~$  /usr/lib/cups/filter$ ls -la
bash: /usr/lib/cups/filter$: No existe el fichero ó directorio
gabi@gabi-desktop:~$ 
```

Una más: no te compliques pensando si algo de la configuración del Escáner dio error, tal vez no, sino todas las personas que detectaron el BUG deberían haber hecho lo mismo, al parecer es un error de Ubuntu 8.04 que todavía está vigente (hoy aparecieron muchas actualizaciones)

Gracias, saludos.

---

### Post by faktorqm on 2008-05-26
El comando correcto es:

```

faktorqm@the-edge:~$ ls -la /usr/lib/cups/filter
total 500
drwxr-xr-x  2 root root  4096 2008-05-15 08:14 .
drwxr-xr-x 10 root root  4096 2008-04-22 14:51 ..
-rwxr-xr-x  1 root root  5824 2008-01-24 09:55 commandtocanon
-rwxr-xr-x  1 root root  5832 2008-01-24 09:55 commandtoepson
-rwxr-xr-x  1 root root  5848 2007-08-15 08:23 commandtoescpx
-rwxr-xr-x  1 root root  4816 2007-08-15 08:23 commandtopclx
lrwxrwxrwx  1 root root    12 2008-05-15 08:14 cupsomatic -> foomatic-rip
lrwxrwxrwx  1 root root    25 2008-05-15 08:14 foomatic-rip -> ../../../bin/foomatic-rip
-rwxr-xr-x  1 root root  4680 2008-04-21 17:18 gziptoany
-rwxr-xr-x  1 root root 43580 2008-04-21 17:18 hpgltops
-rwxr-xr-x  1 root root 26548 2008-04-21 17:18 imagetops
-rwxr-xr-x  1 root root 56608 2008-04-21 17:18 imagetoraster
-rwxr-xr-x  1 root root  4316 2008-04-21 17:15 oopstops
-rwxr-xr-x  1 root root 13252 2008-04-21 17:18 pdftops
-rwxr-xr-x  1 root root 43420 2008-04-21 17:18 pstops
-rwxr-xr-x  1 root root  1914 2008-04-09 11:11 pstopxl
-rwxr-xr-x  1 root root  1882 2008-04-09 11:11 pstoraster
lrwxrwxrwx  1 root root    13 2008-04-29 05:19 rastertodymo -> rastertolabel
-rwxr-xr-x  1 root root 14076 2008-04-21 17:18 rastertoepson
-rwxr-xr-x  1 root root 39312 2007-08-15 08:23 rastertoescpx
-rwxr-xr-x  1 root root 33736 2008-01-24 09:55 rastertogutenprint.5.0
-rwxr-xr-x  1 root root 13048 2008-04-21 17:18 rastertohp
-rwxr-xr-x  1 root root 16556 2008-04-21 17:18 rastertolabel
-rwxr-xr-x  1 root root 39832 2007-08-15 08:23 rastertopclx
-rwxr-xr-x  1 root root 28964 2008-02-12 13:45 rastertospl2
-rwxr-xr-x  1 root root  3560 2008-04-21 17:15 textonly
-rwxr-xr-x  1 root root 36928 2008-04-21 17:18 texttops
faktorqm@the-edge:~$ 

```

Y otra cosa, siempre sueño con solucionar un problema "grosso grosso". Asi que no me voy a dar por vencido y voy a probar todas las cosas que probaria yo si el problema fuera mio. 

La solucion, que tambien encontre, es recompilar el kernel entero y desactivarle las funciones de suspension al usb. Pero no te queria meter en un bardo, asi que si armamos con meduza y wanderknight alguna guia de como se hace en ubuntu lo podemos llegar a considerar. Salu2!!
Salu2!!

---

### Post by GGsalas on 2008-05-26
faktorqm, te muestro mis directorios, aparentemente tengo 4 archivos más que vos

```
gabi@gabi-desktop:~$ ls -la /usr/lib/cups/filter
total 504
drwxr-xr-x   2 root root  4096 2008-05-15 15:07 .
drwxr-xr-x  10 root root  4096 2008-04-22 14:51 ..
-rwxr-xr-x   1 root root  5824 2008-01-24 09:55 commandtocanon
-rwxr-xr-x   1 root root  5832 2008-01-24 09:55 commandtoepson
-rwxr-xr-x   1 root root  5848 2007-08-15 08:23 commandtoescpx
-rwxr-xr-x   1 root root  4816 2007-08-15 08:23 commandtopclx
lrwxrwxrwx   1 root root    12 2008-05-15 15:07 cupsomatic -> foomatic-rip
lrwxrwxrwx   1 root root    25 2008-05-15 15:07 foomatic-rip -> ../../../bin/foomatic-rip
-rwxr-xr-x   1 root root  4680 2008-04-21 17:18 gziptoany
-rwxr-xr-x   1 root root 43580 2008-04-21 17:18 hpgltops
-rwxr-xr-x   1 root root 26548 2008-04-21 17:18 imagetops
-rwxr-xr-x   1 root root 56608 2008-04-21 17:18 imagetoraster
-rwxr-xr-x   1 root root  4316 2008-04-21 17:15 oopstops
-rwxr-xr-x   1 root root 13252 2008-04-21 17:18 pdftops
-rwxr-xr-x   1 root root 43420 2008-04-21 17:18 pstops
-rwxr-xr-x   1 root root  1914 2008-04-09 11:11 pstopxl
-rwxr-xr-x+  1 root root  1882 2008-04-09 11:11 pstoraster
lrwxrwxrwx   1 root root    13 2008-05-15 10:41 rastertodymo -> rastertolabel
-rwxr-xr-x   1 root root 14076 2008-04-21 17:18 rastertoepson
-rwxr-xr-x   1 root root 39312 2007-08-15 08:23 rastertoescpx
-rwxr-xr-x   1 root root 33736 2008-01-24 09:55 rastertogutenprint.5.0
-rwxr-xr-x   1 root root 13048 2008-04-21 17:18 rastertohp
-rwxr-xr-x   1 root root 16556 2008-04-21 17:18 rastertolabel
-rwxr-xr-x   1 root root 39832 2007-08-15 08:23 rastertopclx
-rwxr-xr-x   1 root root 28964 2008-02-12 13:45 rastertospl2
-rwxr-xr-x   1 root root  3560 2008-04-21 17:15 textonly
-rwxr-xr-x   1 root root 36928 2008-04-21 17:18 texttops
```

pstoraster lo tengo como -rwxr-xr-x+  y veo que vos no tenés el + al final, no se si eso influye en el error que tengo.

Te agradezco mucho la ayuda, sucede que como vi que es un BUG, no se si tendrá una solución simple excepto que se trabaje en solucionar al bug directamente. Yo hago las pruebas que me indiques, sino ya se que tendré que reinstalar todo el sistema, pasa que además del trabajo me quedo con la duda si el error volverá a aparecer.

---

### Post by picaeta on 2008-05-29
Hola yo tengo una DX6000, el mismo problema todo iba bien hasta que configure el scaner con la guia de esta pagina:
[http://www.p2pforum.it/forum/showthread.php?t=191034](http://www.p2pforum.it/forum/showthread.php?t=191034)
Escanea perfecto pero no hay quien imprima :(

---

### Post by faktorqm on 2008-05-29
Para mi hay una movida con el tema del grupo, viste que en una le mandas gas con ```
 SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082e", MODE="664", GROUP="scanner"
```, bueno para mi hay algo ahi, pero todavia no encontre nada.

Lo del signo + todavia es un misterio, me lei la documentacion entera del ls y todavia no encontre nada, voy a cambiar el metodo de busqueda por que algo evidentemente estoy haciendo mal. Los mantengo al tanto si tengo novedades, salu2!

---

### Post by GGsalas on 2008-05-29
El grupo escáner lo tengo asignado a mi usuario y a root. 

¿El + es un misterio? jaja, te he complicado la vida.. mira vos lo que puede hacer una multifunción, si me hubiera comprado un escáner e impresora separado hubiera sido más fácil aún que en Win o Mac con el driver de la empresa.

picaeta, ¿estas seguro que justo antes de configurar el escáner imprimía bien? A mi me quedó esa duda. 

Gracias faktorqm por preocuparte,

Saludos.

---

### Post by GGsalas on 2008-05-29
:guitar: [SIZE="3"]¡¡¡Funciona!!![/SIZE]

faktorqm, ¿tenés razón?

La pregunta la vas a comprender cuando te cuente lo que hice:

Me quedé pensando en tu idea de que el problema está en algo relacionado al grupo. Ese código está dentro del archivo  /etc/udev/rules.d/45-libsane.rules, ahora bien ¿que pruebas puede hacer alguien como yo, sin ningún conocimiento? 

Respuesta: borrar todo y reiniciar. Eso es lo que hice y ¡ha funcionado!. 

En la captura de pantalla se puede ver que la impresora no da error (ha impreso una página de prueba) y que sigo pudiendo escanear. Además se ve el archivo  45-libsane.rules vacío. 

Tal vez alguien pueda explicar por que, pero la buena noticia es que ahora está funcionando :D

Saludos y gracias.

---

### Post by sajnox on 2008-05-29
Muy bueno!!! 

Si te copas estaria bueno que dejes un tuto en limpio de como es que finalmente se configura, tambien te puede servir a vos en un futuro (nunca se sabe)

Saludos

---

### Post by GGsalas on 2008-05-29
Tengo miedo de equivocarme, porque no estoy seguro por que ahora funciona, pero mañana con tiempo lo haré y espero que si me equivoco me corrijan.

---

### Post by picaeta on 2008-05-30
Confirmado si se borra el contenido del archivo funciona a la perfeccion.
Muchas gracias :guitar:

---

### Post by faktorqm on 2008-05-30
grosso!! al final estaba en la pista. despues lo paso en limpio el tuto no hay drama, aunque lo unico seria sacar esa parte. el scanner y la impresora te andan bien, o sea, te andan bien las dos cosaS? salu2!

---

### Post by GGsalas on 2008-05-30
Hasta ahora funciona todo bien, y parece que no soy el único :)

Habría que sacar esa parte y poner instalar lo que me falló al comienzo que no podía compilar. 

Saludos.

---

### Post by GGsalas on 2008-05-31
*[COLOR="DarkGreen"]Lo prometido es deuda, voy a colocar todos los pasos que me indicó faktorqm hacer agregando la instalación de programas para compilar que necesité y eliminando la configuración del archivo libsane que es lo que finalmente permitió que el escáner y la impresora funcionen.[/COLOR]*

Hola, a mi me encantan las cosas dificiles, asi que te voy a intentar hacer funcionar tu ""aparato"" :P

**[COLOR="Red"]AVISO: NO ANDA PARA 64 BITS[/COLOR]**

Primero, hay que conectar el scanner y tenerlo prendido y saber que realmente lo está. Tirá el comando "lsusb" para ver si te lo muestra.

Ahora instalamos el sane, sus utilidades y las herramientas de compilación del driver:

```
sudo apt-get install sane sane-utils xsane build-essential gcc binutils automake
```

[I][COLOR="DarkGreen"]Si el sistema no lo tiene debemos instalar estos paquetes que creo son los que te faltan en tu sistema (lo agrego porque sin esto me dió error):

```
sudo apt-get install libgtk-dev gdk-imlib gdk-imlib-dev gdk-imlib1 gdk-imlib1-dev gdk-imlib11 gdk-imlib11-dev libltdl3 libltdl3-dev
```[/COLOR][/I]

Ahora, nos bajamos el driver de la siguiente pagina:

```
wget http://lx1.avasys.jp/iscan/2.10.0/iscan_2.10.0-1.tar.gz
```

Ahora lo descomprimimos:

```
tar xvzf iscan_2.10.0-1.tar.gz
```

Ahora nos metemos en el directorio del driver y lo compilamos

```
cd iscan_2.10.0-1
```
```
./configure --prefix=/usr
```
```
make
```
```
sudo make install
```

Ésta parte es la más crucial, la más importante. Si falla esto no pasa nada. Si te tira error no dudes en postear toda las salida de comandos completa para ver que paso en el medio y asi terminar la compilacion.
Si no está completa la compilación, lamentablemente no podemos seguir.

Si todo salió bien, ahora deberemos editar un par de archivos:

```
sudo gedit /etc/sane.d/dll.conf
```

Una vez abierto el archivo, comentamos la linea "epson" y agregamos abajo "epkowa". Debe quedar asi:

```
#epson
epkowa
```

Guardamos y editamos otro:

```
sudo gedit /etc/sane.d/epkowa.conf
```

Una vez abierto el archivo, comentamos la linea "scsi EPSON" y debe quedar asi:

```
#scsi EPSON
```

Y TAMBIEN DEBEMOS DESCOMENTAR LA LINEA USB:

antes: ```
#usb
```

debe quedar: ```
usb
```

Guardamos.

Ahora vamos a ver si sane """lo ve""":

```
sane-find-scanner -q
```

Te tiene que tirar algo parecido a esto:

```
found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error] at libusb:001:003
```

Bueno, ahora volvemos a editar el archivo:

```
sudo gedit /etc/sane.d/epkowa.conf
```

EN TODAS LAS LINEAS QUE COMIENCEN CON **USB** LES DEBEMOS PONER EL SIMBOLO "#" (numeral) ADELANTE y luego en otra linea agregar:

```
usb 0x04b8 0x083f
```

Guardamos y salimos. 

Ahora vamos a “Aplicaciones -> Gráficos -> Escáner de imágenes Xsane” y debería funcionar todo a la perfección.

Capaz podes tener problemas de permisos sobre las cosas. Si no llegas a tener permisos por algo en especial lo que podemos probar es lo siguiente:

```
sudo chmod 0755 /usr/bin/xsane
```

AUNQUE NO DEBERIAMOS TOCAR COSAS DE /usr/bin, lo que pasa es que si lo queremos hacer "bien" deberiamos crear un grupo "escaner", meter al usuario, y es mas lio, pero seria una solucion muchisimo mas segura y sensata, poniendole 755 cualquiera viene y escanea.

Aparte también podemos probar sobre el dispositivo en si, para ello si la salida del comando:

```
sane-find-scanner -q
```

fue:

```
found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error] at libusb:001:003
```

Debemos correr:

```
sudo chmod 0755 /proc/bus/usb/001/003
```

EN CAMBIO si la salida fue : 

```
found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error] at libusb:001:002
```

Debemos correr:

```
sudo chmod 0755 /proc/bus/usb/001/002
```

Y asi según nos devuelva el comando la información.

Bueno, espero que te haya servido, postea tus dudas, tus comentarios, tus agregados, tus salidas de compilación erróneas :P:P:P.
Salu2!!!!
[COLOR="DarkGreen"][I]
Eso es todo, gracias de nuevo a faktorqm, y espero haber hecho bien el resumen. Si alguien lo utiliza avise si tuvo algún inconveniente.

Saludos.[/I][/COLOR]

---

### Post by LaHire on 2008-06-10
Well...damm

me tira una ENORME cantidad de errores al hacer el make y el make install

```

lahire@tardis:~/iscan-2.10.0$ sudo make
make  all-recursive
make[1]: se ingresa al directorio `/home/lahire/iscan-2.10.0'
Making all in include
make[2]: se ingresa al directorio `/home/lahire/iscan-2.10.0/include'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/lahire/iscan-2.10.0/include'
Making all in libltdl
make[2]: se ingresa al directorio `/home/lahire/iscan-2.10.0/libltdl'
make  all-am
make[3]: se ingresa al directorio `/home/lahire/iscan-2.10.0/libltdl'
/bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c -o ltdl.lo ltdl.c
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c  -fPIC -DPIC -o .libs/ltdl.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c -o ltdl.o >/dev/null 2>&1
/bin/bash ./libtool --tag=CC --mode=link gcc  -g -O2   -o libltdlc.la   ltdl.lo -ldl 
rm -fr  .libs/libltdlc.a .libs/libltdlc.la
ar cru .libs/libltdlc.a .libs/ltdl.o
ranlib .libs/libltdlc.a
creating libltdlc.la
(cd .libs && rm -f libltdlc.la && ln -s ../libltdlc.la libltdlc.la)
make[3]: se sale del directorio `/home/lahire/iscan-2.10.0/libltdl'
make[2]: se sale del directorio `/home/lahire/iscan-2.10.0/libltdl'
Making all in lib
make[2]: se ingresa al directorio `/home/lahire/iscan-2.10.0/lib'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/lahire/iscan-2.10.0/lib'
Making all in sanei
make[2]: se ingresa al directorio `/home/lahire/iscan-2.10.0/sanei'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane  -DSYSCONFDIR=\"/usr/etc\" -I../include -I../include   -g -O2 -MT libsanei_la-sanei_config.lo -MD -MP -MF ".deps/libsanei_la-sanei_config.Tpo" -c -o libsanei_la-sanei_config.lo `test -f 'sanei_config.c' || echo './'`sanei_config.c; \
    then mv -f ".deps/libsanei_la-sanei_config.Tpo" ".deps/libsanei_la-sanei_config.Plo"; else rm -f ".deps/libsanei_la-sanei_config.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane -DSYSCONFDIR=\"/usr/etc\" -I../include -I../include -g -O2 -MT libsanei_la-sanei_config.lo -MD -MP -MF .deps/libsanei_la-sanei_config.Tpo -c sanei_config.c  -fPIC -DPIC -o .libs/libsanei_la-sanei_config.o
In file included from sanei_config.c:52:
../include/sane/sanei.h:89:23: error: sane/sane.h: No such file or directory
In file included from sanei_config.c:52:
../include/sane/sanei.h:163: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sanei_check_value'
../include/sane/sanei.h:166: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sanei_constrain_value'
In file included from sanei_config.c:53:
../include/sane/sanei_config.h:124: error: expected declaration specifiers or '...' before 'SANE_Status'
sanei_config.c: In function 'sanei_config_get_string':
sanei_config.c:170: warning: incompatible implicit declaration of built-in function 'strndup'
make[2]: *** [libsanei_la-sanei_config.lo] Error 1
make[2]: se sale del directorio `/home/lahire/iscan-2.10.0/sanei'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/lahire/iscan-2.10.0'
make: *** [all] Error 2


```

en el Make Install pasa algo similar, pero si no anda el make...mucho no puedo hacer :(

---

### Post by faktorqm on 2008-06-10
Hola,

1) tenes ubuntu de 64 bits? 
2) tenes 8.04?
3) le falto agregar a ggsalas un comandito:

```
sudo apt-get remove libsane-extras-dbg libsane-extras-dev libsane-extras
```

si obteniendo esto te funca todo bien, lo arreglo asi queda la super guia. Si no, volvé a postear, cuanto mas probado esté el tutorial mas efectivo es. Espero que te sirva. Salu2!!

---

### Post by LaHire on 2008-06-10
> **faktorqm said:**
> Hola,

1) tenes ubuntu de 64 bits? 
2) tenes 8.04?
3) le falto agregar a ggsalas un comandito:

```
sudo apt-get remove libsane-extras-dbg libsane-extras-dev libsane-extras
```si obteniendo esto te funca todo bien, lo arreglo asi queda la super guia. Si no, volvé a postear, cuanto mas probado esté el tutorial mas efectivo es. Espero que te sirva. Salu2!!

1) no. tengo un Turion 64, pero uso Ubuntu 8.04 de 32 bits
2) ver arriba :-)
3) Cuándo se implementa ese apt? antes del make? despues?

ahi estoy probando...

**EDIT:**

ehm, probé hacer un apt-get INSTALL de esa línea de comandos que me pasaste y funcionó, o al menos el make y el make install no me sale con errores, aparentemente. Ahora sigo con la instalación- Si explota, bueno, diganle a Internet que lo quiero

[B]EDIT 2:

[/B]sudo gedit /etc/sane.d/epkowa.conf


Me clavé ahi. la línea "usb" estaba descomentada de por si, y el resto del archivo esta, en teoría (por lo que entiendo de la explicación), bien hecho, de todas formas, el scanner no aparece :-(

---

### Post by faktorqm on 2008-06-11
Hola, buenisimo que vas avanzando.

La linea que te pasé va primero que nada. Pero bueno, ya esta. 

Hiciste apt-get INSTALL o remove como te puse ahi? si pusiste install esta mal, no te va a funcionar.

¿A donde no te lo muestra? Llegaste hasta la parte de "usb 0x04b8 0x083f"?

Lo que podés probar es saltearte un paso si ya esta hecho y hacer "sane-find-scanner -q" directamente y seguir. 

Comentame como te fue. Salu2!!

---

### Post by LaHire on 2008-06-11
> **faktorqm said:**
> Hola, buenisimo que vas avanzando.

La linea que te pasé va primero que nada. Pero bueno, ya esta. 

Hiciste apt-get INSTALL o remove como te puse ahi? si pusiste install esta mal, no te va a funcionar.

¿A donde no te lo muestra? Llegaste hasta la parte de "usb 0x04b8 0x083f"?

Lo que podés probar es saltearte un paso si ya esta hecho y hacer "sane-find-scanner -q" directamente y seguir. 

Comentame como te fue. Salu2!!

Si, había puesto install, pero ahi quité todo; y luego volví a hacer ./configure , make y make install de nuevo, por las dudas.

luego, el  /etc/sane.d/epkowa.conf :

comenté (lo que yo entiendo por poner el # adelante)
las líneas:

usb
usb 0x04b8 0x0110 (que ya estaba comentada, creo que era parte de la documentación)
usb /dev/usb/scanner0
usb /dev/usbscanner0
usb /dev/uscanner0 (también pre-comentadas, parte de la documentación)

y al final de todo, puse:
usb 0x04b8 0x083f


luego de salvar: el 

```

lahire@tardis:~/iscan-2.10.0$ sane-find-scanner -q
found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error]) at libusb:001:003

```

pensaba hacer el chmod...pero
/proc/bus/usb/
 no tiene ningúna carpeta 001/2/3
(de hecho, no tiene nada)

y tengo los 3 puertos usb ocupados, puede haber algo mal en el proc? :3

de paso, el xsane me tira un error:
"fallo al abrir dispositivo v4l::/dev/video0:"
"argumento no válido"

tenés idea de que puede ser?

(de paso, tengo webcam incorporada, quizá sea eso)

---

### Post by faktorqm on 2008-06-12
Pará, supuestamente cuando seteaste lo del usb bla bla en el archivo ya esta. tenes que abrir el sane y fijarte si te aparece el escanner como dispositivo, obviamente te va a mostrar todos los que tiene en el sistema para "tomar" imagenes desde ahi... eso que puse abajo de todo, es por si no funciona, no si no te lo muestra.

v4l significa "video for linux",y si, efectivamente es tu camara web o tu capturadora de video. "decile" al sane que el dispositivo es otro y no ese.

lo del /proc/bus/usb/ es imposible, seguro no tenes permisos para ver, o alguna otra cosa. Pero no te metas con eso, primero hacé que el sane ande.

Salu2!!

---

### Post by LaHire on 2008-07-04
> **faktorqm said:**
> Pará, supuestamente cuando seteaste lo del usb bla bla en el archivo ya esta. tenes que abrir el sane y fijarte si te aparece el escanner como dispositivo, obviamente te va a mostrar todos los que tiene en el sistema para "tomar" imagenes desde ahi... eso que puse abajo de todo, es por si no funciona, no si no te lo muestra.

v4l significa "video for linux",y si, efectivamente es tu camara web o tu capturadora de video. "decile" al sane que el dispositivo es otro y no ese.

lo del /proc/bus/usb/ es imposible, seguro no tenes permisos para ver, o alguna otra cosa. Pero no te metas con eso, primero hacé que el sane ande.

Salu2!!

Cuando abro el sane me tira "Falló al abrir el dispositivo 'v4l:/dev/video0' \n Argumento no válido." y luego se cierra.

y la impresora en si no anda.

voy a tirarla a la basura :(

---

### Post by ruizse01 on 2008-09-17
Hola yo tengo ubuntu amd64 se pude hacer funcionar el scanner tambien. La impresora funciona.
Pero el scaner no :(

Bueno desde mugchas gracias por la ayuda.
Lo único lo único que no he podido configurar es el scanner.

---

### Post by vampichoke on 2008-09-17
**yo recien me entero q no anda el scanner (la tengo. la cx5600) imprimi desde ubuntu y anda como trompada. pero nunca scanee siempre por esas casualidades lo hice desde guin2.. a ver voy a probar =O**

---

### Post by GGsalas on 2008-09-18
En [este mensaje]("http://ubuntuforums.org/showpost.php?p=5085446&postcount=38") dejé todos los pasos necesarios para hacer funcionar el Scanner, espero que sirva. Saludos.

---

### Post by euzkoarima on 2008-12-27
Buenas, revivo este hilo porque estoy instalando ubuntu 8.10 en la pc de mi viejo, y tiene esta impresora.
La impresora funcionó de una, nada que configurar. El scanner por ahora no lo puedo hacer andar.
Seguí las instrucciones, salvo en dos partes a saber:

1) en vez de compilar el fuente e instalarlo hice, parado en el directorio donde baje el driver (rpm)
fakeroot alien iscan-2.10.0-1.c2.i386.rpm
sudo dpkg -i iscan*.deb

2) NO TENGO NADA en /proc/bus/usb, lo que hablaba de eso lo hice con (parece ser el reemplazo) /dev/bus/usb

Paso algunos comandos para que se sepa el estado en que se encuentra el asunto

```

martin@martin-desktop:~$ sane-find-scanner -q
found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error]) at libusb:001:003
martin@martin-desktop:~$ ls -al /proc/bus/usb
total 0
dr-xr-xr-x 2 root root 0 2008-12-27 14:34 .
dr-xr-xr-x 5 root root 0 2008-12-27 14:34 ..
martin@martin-desktop:~$ ls -al /dev/bus/usb
total 0
drwxr-xr-x 4 root root 80 2008-12-27 12:18 .
drwxr-xr-x 3 root root 60 2008-12-27 12:18 ..
drwxr-xr-x 2 root root 80 2008-12-27 12:18 001
drwxr-xr-x 2 root root 80 2008-12-27 12:18 002
martin@martin-desktop:~$ ls -al /dev/bus/usb/001
total 0
drwxr-xr-x  2 root root        80 2008-12-27 12:18 .
drwxr-xr-x  4 root root        80 2008-12-27 12:18 ..
crw-rw-r--  1 root root    189, 0 2008-12-27 12:18 001
crw-rw-r--+ 1 root scanner 189, 2 2008-12-27 14:33 003
martin@martin-desktop:~$ lsusb
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04b8:083f Seiko Epson Corp. Stylus DX4450
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
martin@martin-desktop:~$ sudo iscan
martin@martin-desktop:~$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

Comentario, el iscan lo tiré con sudo para evitar dudas de si es un problema de permisos, ejecuta y da el error que muestra el adjunto

Alguna sugerencia??
lo que puse del punto 1 (instalar con alien) tendrá que ver??

Saludos,
Eduardo

---

### Post by euzkoarima on 2009-01-02
Buenas, cuento como sigue esto. Encontré [Este tutorial]("http://reformedmusings.wordpress.com/2008/12/13/fixing-epson-scanners-in-ubuntu-810-intrepid-linux/") que dice que con 8.10 no hace falta instalar el iscan a mano y que con algunos pasos más la cosa sale andando. Así que borre el paquete que había instalado y seguí el tuto, pero tampoco anduvo.

El asunto es que ya no tengo acceso físico a esa pc (esta a 400 km) pero deje ssh como seguir probando cuando tenga algo de tiempo. Cuando esto ocurra voy a:

1) borrar y reinstalar todos los paquetes que nombra ese tutorial a ver si tengo suerte

2) si no funciona voy a seguir "al pie de la letra" las instrucciones de este post, o sea, compilando desde el fuente.

Cuando lo haga cuento como me fue.

Saludos,
Eduardo

---

### Post by faktorqm on 2009-01-03
Te fijaste los comentarios abajo del tuto ese? Dicen que todo muy lindo pero que hay un bug en el paquete libsane-extras que le falta el archivo epkowa.conf... un flaco reporto el bug aca [https://bugs.launchpad.net/ubuntu/+source/sane-backends-extras/+bug/307991](https://bugs.launchpad.net/ubuntu/+source/sane-backends-extras/+bug/307991)

Si no te anda avisa, salu2!!

---

### Post by euzkoarima on 2009-01-03
Si lo vi, el bug es que en el paquete libsane-extras para intrepid se olvidaron de poner los archivos de configuración, no solo el de epkowa, sino todos, con lo cual había que ponerlo a mano (lo hice).

Bueno, cuando pueda probar, como ya dije, posteo como me fue.

Gracias y saludos.
Eduardo

---

### Post by usachin on 2009-11-21
amigos, estoy reviviendo este hilo porq no hay caso q pueda hacer funcionar esto...intento intento  nada :(

tengo el ultimo ubunto desktop de 32 bits 9.10

he hecho todo los pasos que se han indicado en post anteriores...les muestro lo que me sale en la consola...les agradeceria muchisimo si me pudieran indicar por donde podria venir el problema...

al ejecutar : ./configure --prefix=/usr

obtengo lo siguiente:

............
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib /usr/lib /lib/i486-linux-gnu /usr/lib/i486-linux-gnu /usr/lib/alsa-lib /usr/local/lib 
checking for objdir... .libs
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen in -ldl... yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... yes
checking for strrchr... yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands


luego al darle MAKE:

checking for stdint.h... (cached) yes
checking for SIZE_MAX... yes
checking for stdint.h... (cached) yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for ptrdiff_t... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for limits.h... (cached) yes
checking for locale.h... (cached) yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for stddef.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for asprintf... yes
checking for fwprintf... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for snprintf... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for wcslen... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... no
checking whether getc_unlocked is declared... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking whether closedir returns void... no
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for working strtod... yes
checking for vprintf... yes
checking for _doprnt... no
checking for alarm... yes
checking for atexit... yes
checking for bzero... yes
checking for floor... no
checking for memset... yes
checking for regcomp... yes
checking for select... yes
checking for setenv... (cached) yes
checking for setlocale... (cached) yes
checking for strcasecmp... (cached) yes
checking for strncasecmp... yes
checking for strchr... yes
checking for strdup... (cached) yes
checking for strerror... yes
checking for strndup... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtol... yes
checking for strtoul... (cached) yes
checking for a sed that does not truncate output... /bin/sed
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib /usr/lib /lib/i486-linux-gnu /usr/lib/i486-linux-gnu /usr/lib/alsa-lib /usr/local/lib 
checking for objdir... .libs
checking for BSD-compatible nm... /usr/bin/nm -B
checking command to parse /usr/bin/nm -B output from  object... ok
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen in -ldl... yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking for argz.h... (cached) yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for malloc.h... (cached) yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... (cached) yes
checking for strrchr... (cached) yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognise dependent libraries... pass_all
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... (cached) ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... (cached) ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking whether to build the frontend application... yes
checking for sigprocmask... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating backend/Makefile
config.status: creating doc/Makefile
config.status: creating frontend/Makefile
config.status: creating include/Makefile
config.status: creating intl/Makefile
config.status: WARNING:  intl/Makefile.in seems to ignore the --datarootdir setting
config.status: creating lib/Makefile
config.status: creating non-free/Makefile
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating sanei/Makefile
config.status: creating utils/Makefile
config.status: creating iscan.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: creating include/sane/config.h
config.status: include/sane/config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
=== configuring in libltdl (/home/javiera/Escritorio/iscan-2.10.0/libltdl)
configure: running /bin/bash ./configure '--prefix=/usr'  '--enable-ltdl-convenience' --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib /usr/lib /lib/i486-linux-gnu /usr/lib/i486-linux-gnu /usr/lib/alsa-lib /usr/local/lib 
checking for objdir... .libs
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen in -ldl... yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... yes
checking for strrchr... yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
javiera@javiera-desktop:~/Escritorio/iscan-2.10.0$ clear

javiera@javiera-desktop:~/Escritorio/iscan-2.10.0$ make
make  all-recursive
make[1]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0'
Making all in include
make[2]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/include'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/include'
Making all in libltdl
make[2]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
make  all-am
make[3]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
/bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c -o ltdl.lo ltdl.c
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c  -fPIC -DPIC -o .libs/ltdl.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c -o ltdl.o >/dev/null 2>&1
/bin/bash ./libtool --tag=CC --mode=link gcc  -g -O2   -o libltdlc.la   ltdl.lo -ldl 
rm -fr  .libs/libltdlc.a .libs/libltdlc.la
ar cru .libs/libltdlc.a .libs/ltdl.o
ranlib .libs/libltdlc.a
creating libltdlc.la
(cd .libs && rm -f libltdlc.la && ln -s ../libltdlc.la libltdlc.la)
make[3]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
make[2]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
Making all in lib
make[2]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/lib'
if /bin/bash ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane  -I../include   -g -O2 -MT libimage_stream_la-imgstream.lo -MD -MP -MF ".deps/libimage_stream_la-imgstream.Tpo" -c -o libimage_stream_la-imgstream.lo `test -f 'imgstream.cc' || echo './'`imgstream.cc; \
    then mv -f ".deps/libimage_stream_la-imgstream.Tpo" ".deps/libimage_stream_la-imgstream.Plo"; else rm -f ".deps/libimage_stream_la-imgstream.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane -I../include -g -O2 -MT libimage_stream_la-imgstream.lo -MD -MP -MF .deps/libimage_stream_la-imgstream.Tpo -c imgstream.cc  -fPIC -DPIC -o .libs/libimage_stream_la-imgstream.o
In file included from imgstream.cc:31:
imgstream.hh:46:18: error: ltdl.h: No such file or directory
In file included from imgstream.cc:31:
imgstream.hh:115: error: 'lt_dlhandle' does not name a type
imgstream.hh:116: error: 'lt_ptr' does not name a type
imgstream.hh:118: error: 'dl_handle' does not name a type
imgstream.hh:120: error: 'dl_ptr' does not name a type
imgstream.hh:121: error: 'dl_handle' has not been declared
imgstream.hh:124: error: 'dl_handle' does not name a type
imgstream.cc:155: error: 'dl_handle' in class 'iscan::imgstream' does not name a type
imgstream.cc:174: error: 'dl_ptr' in class 'iscan::imgstream' does not name a type
imgstream.cc:181: error: 'int iscan::imgstream::dlclose' is not a static member of 'class iscan::imgstream'
imgstream.cc:181: error: 'dl_handle' was not declared in this scope
imgstream.cc:182: error: expected ',' or ';' before '{' token
imgstream.cc:211: error: 'dl_handle' in class 'iscan::imgstream' does not name a type
imgstream.cc: In function 'int iscan::reversionsort(const void*, const void*)':
imgstream.cc:313: error: invalid conversion from 'const void*' to 'const dirent**'
imgstream.cc:313: error:   initializing argument 1 of 'int versionsort(const dirent**, const dirent**)'
imgstream.cc:313: error: invalid conversion from 'const void*' to 'const dirent**'
imgstream.cc:313: error:   initializing argument 2 of 'int versionsort(const dirent**, const dirent**)'
make[2]: *** [libimage_stream_la-imgstream.lo] Error 1
make[2]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/lib'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0'
make: *** [all] Error 2

y luego al darle SUDO MAKE INSTALL:

checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking whether closedir returns void... no
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for working strtod... yes
checking for vprintf... yes
checking for _doprnt... no
checking for alarm... yes
checking for atexit... yes
checking for bzero... yes
checking for floor... no
checking for memset... yes
checking for regcomp... yes
checking for select... yes
checking for setenv... (cached) yes
checking for setlocale... (cached) yes
checking for strcasecmp... (cached) yes
checking for strncasecmp... yes
checking for strchr... yes
checking for strdup... (cached) yes
checking for strerror... yes
checking for strndup... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtol... yes
checking for strtoul... (cached) yes
checking for a sed that does not truncate output... /bin/sed
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib /usr/lib /lib/i486-linux-gnu /usr/lib/i486-linux-gnu /usr/lib/alsa-lib /usr/local/lib 
checking for objdir... .libs
checking for BSD-compatible nm... /usr/bin/nm -B
checking command to parse /usr/bin/nm -B output from  object... ok
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen in -ldl... yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking for argz.h... (cached) yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for malloc.h... (cached) yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... (cached) yes
checking for strrchr... (cached) yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognise dependent libraries... pass_all
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... (cached) ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... (cached) ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking whether to build the frontend application... yes
checking for sigprocmask... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating backend/Makefile
config.status: creating doc/Makefile
config.status: creating frontend/Makefile
config.status: creating include/Makefile
config.status: creating intl/Makefile
config.status: WARNING:  intl/Makefile.in seems to ignore the --datarootdir setting
config.status: creating lib/Makefile
config.status: creating non-free/Makefile
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating sanei/Makefile
config.status: creating utils/Makefile
config.status: creating iscan.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: creating include/sane/config.h
config.status: include/sane/config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
=== configuring in libltdl (/home/javiera/Escritorio/iscan-2.10.0/libltdl)
configure: running /bin/bash ./configure '--prefix=/usr'  '--enable-ltdl-convenience' --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib /usr/lib /lib/i486-linux-gnu /usr/lib/i486-linux-gnu /usr/lib/alsa-lib /usr/local/lib 
checking for objdir... .libs
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen in -ldl... yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... yes
checking for strrchr... yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
javiera@javiera-desktop:~/Escritorio/iscan-2.10.0$ clear

javiera@javiera-desktop:~/Escritorio/iscan-2.10.0$ make
make  all-recursive
make[1]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0'
Making all in include
make[2]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/include'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/include'
Making all in libltdl
make[2]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
make  all-am
make[3]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
/bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c -o ltdl.lo ltdl.c
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c  -fPIC -DPIC -o .libs/ltdl.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c -o ltdl.o >/dev/null 2>&1
/bin/bash ./libtool --tag=CC --mode=link gcc  -g -O2   -o libltdlc.la   ltdl.lo -ldl 
rm -fr  .libs/libltdlc.a .libs/libltdlc.la
ar cru .libs/libltdlc.a .libs/ltdl.o
ranlib .libs/libltdlc.a
creating libltdlc.la
(cd .libs && rm -f libltdlc.la && ln -s ../libltdlc.la libltdlc.la)
make[3]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
make[2]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
Making all in lib
make[2]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/lib'
if /bin/bash ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane  -I../include   -g -O2 -MT libimage_stream_la-imgstream.lo -MD -MP -MF ".deps/libimage_stream_la-imgstream.Tpo" -c -o libimage_stream_la-imgstream.lo `test -f 'imgstream.cc' || echo './'`imgstream.cc; \
    then mv -f ".deps/libimage_stream_la-imgstream.Tpo" ".deps/libimage_stream_la-imgstream.Plo"; else rm -f ".deps/libimage_stream_la-imgstream.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane -I../include -g -O2 -MT libimage_stream_la-imgstream.lo -MD -MP -MF .deps/libimage_stream_la-imgstream.Tpo -c imgstream.cc  -fPIC -DPIC -o .libs/libimage_stream_la-imgstream.o
In file included from imgstream.cc:31:
imgstream.hh:46:18: error: ltdl.h: No such file or directory
In file included from imgstream.cc:31:
imgstream.hh:115: error: 'lt_dlhandle' does not name a type
imgstream.hh:116: error: 'lt_ptr' does not name a type
imgstream.hh:118: error: 'dl_handle' does not name a type
imgstream.hh:120: error: 'dl_ptr' does not name a type
imgstream.hh:121: error: 'dl_handle' has not been declared
imgstream.hh:124: error: 'dl_handle' does not name a type
imgstream.cc:155: error: 'dl_handle' in class 'iscan::imgstream' does not name a type
imgstream.cc:174: error: 'dl_ptr' in class 'iscan::imgstream' does not name a type
imgstream.cc:181: error: 'int iscan::imgstream::dlclose' is not a static member of 'class iscan::imgstream'
imgstream.cc:181: error: 'dl_handle' was not declared in this scope
imgstream.cc:182: error: expected ',' or ';' before '{' token
imgstream.cc:211: error: 'dl_handle' in class 'iscan::imgstream' does not name a type
imgstream.cc: In function 'int iscan::reversionsort(const void*, const void*)':
imgstream.cc:313: error: invalid conversion from 'const void*' to 'const dirent**'
imgstream.cc:313: error:   initializing argument 1 of 'int versionsort(const dirent**, const dirent**)'
imgstream.cc:313: error: invalid conversion from 'const void*' to 'const dirent**'
imgstream.cc:313: error:   initializing argument 2 of 'int versionsort(const dirent**, const dirent**)'
make[2]: *** [libimage_stream_la-imgstream.lo] Error 1
make[2]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/lib'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0'
make: *** [all] Error 2
javiera@javiera-desktop:~/Escritorio/iscan-2.10.0$ CLEAR
CLEAR: command not found
javiera@javiera-desktop:~/Escritorio/iscan-2.10.0$ clear

javiera@javiera-desktop:~/Escritorio/iscan-2.10.0$ sudo make install
Making install in include
make[1]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/include'
make[2]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/include'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/include'
make[1]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/include'
Making install in libltdl
make[1]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
make[2]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
test -z "/usr/include" || mkdir -p -- "/usr/include"
make[2]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
make[1]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/libltdl'
Making install in lib
make[1]: se ingresa al directorio `/home/javiera/Escritorio/iscan-2.10.0/lib'
if /bin/bash ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane  -I../include   -g -O2 -MT libimage_stream_la-imgstream.lo -MD -MP -MF ".deps/libimage_stream_la-imgstream.Tpo" -c -o libimage_stream_la-imgstream.lo `test -f 'imgstream.cc' || echo './'`imgstream.cc; \
    then mv -f ".deps/libimage_stream_la-imgstream.Tpo" ".deps/libimage_stream_la-imgstream.Plo"; else rm -f ".deps/libimage_stream_la-imgstream.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane -I../include -g -O2 -MT libimage_stream_la-imgstream.lo -MD -MP -MF .deps/libimage_stream_la-imgstream.Tpo -c imgstream.cc  -fPIC -DPIC -o .libs/libimage_stream_la-imgstream.o
In file included from imgstream.cc:31:
imgstream.hh:46:18: error: ltdl.h: No such file or directory
In file included from imgstream.cc:31:
imgstream.hh:115: error: 'lt_dlhandle' does not name a type
imgstream.hh:116: error: 'lt_ptr' does not name a type
imgstream.hh:118: error: 'dl_handle' does not name a type
imgstream.hh:120: error: 'dl_ptr' does not name a type
imgstream.hh:121: error: 'dl_handle' has not been declared
imgstream.hh:124: error: 'dl_handle' does not name a type
imgstream.cc:155: error: 'dl_handle' in class 'iscan::imgstream' does not name a type
imgstream.cc:174: error: 'dl_ptr' in class 'iscan::imgstream' does not name a type
imgstream.cc:181: error: 'int iscan::imgstream::dlclose' is not a static member of 'class iscan::imgstream'
imgstream.cc:181: error: 'dl_handle' was not declared in this scope
imgstream.cc:182: error: expected ',' or ';' before '{' token
imgstream.cc:211: error: 'dl_handle' in class 'iscan::imgstream' does not name a type
imgstream.cc: In function 'int iscan::reversionsort(const void*, const void*)':
imgstream.cc:313: error: invalid conversion from 'const void*' to 'const dirent**'
imgstream.cc:313: error:   initializing argument 1 of 'int versionsort(const dirent**, const dirent**)'
imgstream.cc:313: error: invalid conversion from 'const void*' to 'const dirent**'
imgstream.cc:313: error:   initializing argument 2 of 'int versionsort(const dirent**, const dirent**)'
make[1]: *** [libimage_stream_la-imgstream.lo] Error 1
make[1]: se sale del directorio `/home/javiera/Escritorio/iscan-2.10.0/lib'
make: *** [install-recursive] Error 1


FAVOR AYUDAR!!!!


[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by Tom Locke on 2009-11-22
> **euzkoarima said:**
> Si lo vi, el bug es que en el paquete libsane-extras para intrepid se olvidaron de poner los archivos de configuración, no solo el de epkowa, sino todos, con lo cual había que ponerlo a mano (lo hice).

Bueno, cuando pueda probar, como ya dije, posteo como me fue.

Gracias y saludos.
Eduardo


todos los que tienen problemas con esta impresora, yo la tengo, y me funciona de primera, puedo escanear e imprimir, les digo cual es el secreto, tienen que bajarse este archivo (confien)

[http://rapidshare.com/files/206649867/debs_cx5600.tar.gz](http://rapidshare.com/files/206649867/debs_cx5600.tar.gz)

descarguen ese archivo

descomprimanlo

luego hagan doble click y les apareceran 2 carpetas tienen que instalar esas 2 COSAS que hay dentro de la carpeta, y ya esta, simplemente veran que si van a XSCAN ya la reconoce y podes escanear
e imprimir


espero que les haya servido

este es mi primer aporte


SALUDOS

---

### Post by guillermolisi on 2009-11-23
Por favor, si alguien probo la solucion sugerida por Tom Locke comente que resultados obtuvo.
Gracias

---

### Post by GGsalas on 2009-11-23
> **Tom Locke said:**
> todos los que tienen problemas con esta impresora, yo la tengo, y me funciona de primera, puedo escanear e imprimir, les digo cual es el secreto, tienen que bajarse este archivo (confien)

[http://rapidshare.com/files/206649867/debs_cx5600.tar.gz](http://rapidshare.com/files/206649867/debs_cx5600.tar.gz)



No puedo descargar el archivo, pide que sea un usuario premium :(

---

### Post by Mauro22 on 2009-11-23
No se si ya lo bajaste. Lo dejo adjunto a este post.


[COLOR="Red"]**NOTA: No es el mismo de ese link. Este estaba en Megaupload. Tienen el mismo peso, no creo que sea nada raro.**[/COLOR]

Otra cosa:

La guia que hace referencia a ese archivo, viene de aca

[http://miubuntuyyo.wordpress.com/2009/03/06/configurar-multifuncion-epson-cx5600-en-ubuntu/](http://miubuntuyyo.wordpress.com/2009/03/06/configurar-multifuncion-epson-cx5600-en-ubuntu/)


:popcorn:

---

### Post by usachin on 2009-11-24
> **guillermolisi said:**
> Por favor, si alguien probo la solucion sugerida por Tom Locke comente que resultados obtuvo.
Gracias

A mi no me funcionó... el XSANE sigue sin encontrar el dispositivo... :(

y eso que cuando le doy "sane-find-scanner -q" sí la encuentra..

found USB scanner (vendor=0x04b8 [Language Error], product=0x083f [Language Error] at libusb:001:003

ayudaaa!!! será la solución usarla por virtualbox nomás??

---

### Post by GGsalas on 2010-05-01
Acabo de explicar como uso, cambio los cartuchos y limpio los cabezales sin ningún driver (solo hablo de la impresora, no del scanner): [http://www.ggsalas.com.ar/limpiar-cabezales-y-probar-inyectores-de-epson-cx5600-sin-instalar-driver/](http://www.ggsalas.com.ar/limpiar-cabezales-y-probar-inyectores-de-epson-cx5600-sin-instalar-driver/)

Saludos.

---

### Post by iuserneim on 2011-05-23
Alguna forma de que pueda hacer bien la compilacion? probe con tutti no me funca nada.



> iscan-2.10.0/frontend/Makefile.in
iscan-2.10.0/frontend/file-selector.cc
iscan-2.10.0/frontend/file-selector.h
iscan-2.10.0/frontend/gimp-plugin.h
iscan-2.10.0/frontend/pisa_aleart_dialog.cc
iscan-2.10.0/frontend/pisa_aleart_dialog.h
iscan-2.10.0/frontend/pisa_change_unit.cc
iscan-2.10.0/frontend/pisa_change_unit.h
iscan-2.10.0/frontend/pisa_configuration.cc
iscan-2.10.0/frontend/pisa_configuration.h
iscan-2.10.0/frontend/pisa_default_val.h
iscan-2.10.0/frontend/pisa_enums.h
iscan-2.10.0/frontend/pisa_error.cc
iscan-2.10.0/frontend/pisa_error.h
iscan-2.10.0/frontend/pisa_esmod_structs.h
iscan-2.10.0/frontend/pisa_gamma_correction.cc
iscan-2.10.0/frontend/pisa_gamma_correction.h
iscan-2.10.0/frontend/pisa_gimp.cc
iscan-2.10.0/frontend/pisa_gimp.h
iscan-2.10.0/frontend/pisa_gimp_1_0_patch.h
iscan-2.10.0/frontend/pisa_image_controls.cc
iscan-2.10.0/frontend/pisa_image_controls.h
iscan-2.10.0/frontend/pisa_img_converter.cc
iscan-2.10.0/frontend/pisa_img_converter.h
iscan-2.10.0/frontend/pisa_main.cc
iscan-2.10.0/frontend/pisa_main.h
iscan-2.10.0/frontend/pisa_main_window.cc
iscan-2.10.0/frontend/pisa_main_window.h
iscan-2.10.0/frontend/pisa_marquee.cc
iscan-2.10.0/frontend/pisa_marquee.h
iscan-2.10.0/frontend/pisa_preference.cc
iscan-2.10.0/frontend/pisa_preference.h
iscan-2.10.0/frontend/pisa_preview_window.cc
iscan-2.10.0/frontend/pisa_preview_window.h
iscan-2.10.0/frontend/pisa_progress_window.cc
iscan-2.10.0/frontend/pisa_progress_window.h
iscan-2.10.0/frontend/pisa_sane_scan.cc
iscan-2.10.0/frontend/pisa_sane_scan.h
iscan-2.10.0/frontend/pisa_scan_manager.cc
iscan-2.10.0/frontend/pisa_scan_manager.h
iscan-2.10.0/frontend/pisa_scan_selector.cc
iscan-2.10.0/frontend/pisa_scan_selector.h
iscan-2.10.0/frontend/pisa_scan_tool.cc
iscan-2.10.0/frontend/pisa_scan_tool.h
iscan-2.10.0/frontend/pisa_settings.cc
iscan-2.10.0/frontend/pisa_settings.h
iscan-2.10.0/frontend/pisa_structs.h
iscan-2.10.0/frontend/pisa_tool.cc
iscan-2.10.0/frontend/pisa_tool.h
iscan-2.10.0/frontend/pisa_view_manager.cc
iscan-2.10.0/frontend/pisa_view_manager.h
iscan-2.10.0/frontend/xpm_data.cc
iscan-2.10.0/frontend/xpm_data.h
iscan-2.10.0/frontend/test-file-selector.cc
iscan-2.10.0/utils/
iscan-2.10.0/utils/hotplug/
iscan-2.10.0/utils/hotplug/iscan.usermap
iscan-2.10.0/utils/hotplug/iscan-device
iscan-2.10.0/utils/make-udev-rules
iscan-2.10.0/utils/Makefile.am
iscan-2.10.0/utils/Makefile.in
iscan-2.10.0/utils/bootstrap
iscan-2.10.0/doc/
iscan-2.10.0/doc/Makefile.am
iscan-2.10.0/doc/Makefile.in
iscan-2.10.0/doc/sane-epkowa.man
iscan-2.10.0/doc/iscan.man
iscan-2.10.0/doc/epkowa.desc
iscan-2.10.0/doc/xinetd.sane
paula@alejandra-desktop:~$ cd iscan_2.10.0-1
bash: cd: iscan_2.10.0-1: No existe el fichero o el directorio
paula@alejandra-desktop:~$ ./configure --prefix=/usr
bash: ./configure: No existe el fichero o el directorio
paula@alejandra-desktop:~$ cd iscan_2.10.0-1./configure --prefix=/usr make sudo make install
bash: cd: iscan_2.10.0-1./configure: No existe el fichero o el directorio
paula@alejandra-desktop:~$ cd iscan_2.10.0-1./configure --prefix=/usrmake sudo make install
bash: cd: iscan_2.10.0-1./configure: No existe el fichero o el directorio
paula@alejandra-desktop:~$ sudo apt-get install libgtk-dev gdk-imlib gdk-imlib-dev gdk-imlib1 gdk-imlib1-dev gdk-imlib11 gdk-imlib11-dev libltdl3 libltdl3-dev
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete libgtk-dev
paula@alejandra-desktop:~$ cd iscan_2.10.0-1./configure --prefix=/ usr make sudo make install
bash: cd: iscan_2.10.0-1./configure: No existe el fichero o el directorio
paula@alejandra-desktop:~$ cd iscan
bash: cd: iscan: No existe el fichero o el directorio
paula@alejandra-desktop:~$ cd iscan-2
bash: cd: iscan-2: No existe el fichero o el directorio
paula@alejandra-desktop:~$ sudo apt-get remove libsane-extras-dbg libsane-extras-dev libsane-extras
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete libsane-extras-dbg no esta instalado, no se eliminará
El paquete libsane-extras-dev no esta instalado, no se eliminará
El paquete libsane-extras no esta instalado, no se eliminará
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
paula@alejandra-desktop:~$ cd iscan_2.10.0-1
bash: cd: iscan_2.10.0-1: No existe el fichero o el directorio
paula@alejandra-desktop:~$ 

Se agradece la ayuda que diste previamente.

---

### Post by leonborges on 2011-06-08
para instalar el scanner de mi epson stylus cx5600 tengo un problemita al dar make



make  all-recursive
make[1]: se ingresa al directorio «/home/leonborges/Descargas/iscan-2.10.0»
Making all in include
make[2]: se ingresa al directorio «/home/leonborges/Descargas/iscan-2.10.0/include»
make[2]: No se hace nada para «all».
make[2]: se sale del directorio «/home/leonborges/Descargas/iscan-2.10.0/include»
Making all in libltdl
make[2]: se ingresa al directorio «/home/leonborges/Descargas/iscan-2.10.0/libltdl»
make  all-am
make[3]: se ingresa al directorio «/home/leonborges/Descargas/iscan-2.10.0/libltdl»
/bin/bash ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c -o ltdl.lo ltdl.c
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c  -fPIC -DPIC -o .libs/ltdl.o
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c ltdl.c -o ltdl.o >/dev/null 2>&1
/bin/bash ./libtool --tag=CC --mode=link gcc  -g -O2   -o libltdlc.la   ltdl.lo -ldl 
rm -fr  .libs/libltdlc.a .libs/libltdlc.la
ar cru .libs/libltdlc.a .libs/ltdl.o
ranlib .libs/libltdlc.a
creating libltdlc.la
(cd .libs && rm -f libltdlc.la && ln -s ../libltdlc.la libltdlc.la)
make[3]: se sale del directorio «/home/leonborges/Descargas/iscan-2.10.0/libltdl»
make[2]: se sale del directorio «/home/leonborges/Descargas/iscan-2.10.0/libltdl»
Making all in lib
make[2]: se ingresa al directorio «/home/leonborges/Descargas/iscan-2.10.0/lib»
if /bin/bash ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane  -I../include   -g -O2 -MT libimage_stream_la-imgstream.lo -MD -MP -MF ".deps/libimage_stream_la-imgstream.Tpo" -c -o libimage_stream_la-imgstream.lo `test -f 'imgstream.cc' || echo './'`imgstream.cc; \
    then mv -f ".deps/libimage_stream_la-imgstream.Tpo" ".deps/libimage_stream_la-imgstream.Plo"; else rm -f ".deps/libimage_stream_la-imgstream.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../include/sane -I../include -g -O2 -MT libimage_stream_la-imgstream.lo -MD -MP -MF .deps/libimage_stream_la-imgstream.Tpo -c imgstream.cc  -fPIC -DPIC -o .libs/libimage_stream_la-imgstream.o
imgstream.cc: In static member function 'static lt__handle* iscan::imgstream::find_dlopen(const char*)':
imgstream.cc:262: error: invalid conversion from 'int (*)(const void*, const void*)' to 'int (*)(const dirent**, const dirent**)'
imgstream.cc:262: error:   initializing argument 4 of 'int scandir(const char*, dirent***, int (*)(const dirent*), int (*)(const dirent**, const dirent**))'
imgstream.cc: In function 'int iscan::reversionsort(const void*, const void*)':
imgstream.cc:313: error: invalid conversion from 'const void*' to 'const dirent**'
imgstream.cc:313: error:   initializing argument 1 of 'int versionsort(const dirent**, const dirent**)'
imgstream.cc:313: error: invalid conversion from 'const void*' to 'const dirent**'
imgstream.cc:313: error:   initializing argument 2 of 'int versionsort(const dirent**, const dirent**)'
imgstream.cc: At global scope:
imgstream.cc:316: fatal error: opening dependency file .deps/libimage_stream_la-imgstream.Tpo: Permission denied
compilation terminated.
make[2]: *** [libimage_stream_la-imgstream.lo] Error 1
make[2]: se sale del directorio «/home/leonborges/Descargas/iscan-2.10.0/lib»
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio «/home/leonborges/Descargas/iscan-2.10.0»
make: *** [all] Error 2

alguien me puede ayudar....
en el ./configure me da 

configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands



ayuda!!!

---

### Post by leonborges on 2011-06-09
aviso que hice los pasos y funcionó!!!!

pude escanear por fin!!!   

pero..... el XSane 0.996 tiene falla,  "Falló al iniciar el escáner: Argumento incorrecto" 

aveces no detecta.... entonces desconecto por el usb la impresora Epson Stylus CX5600 yvuelvo a conectar, escaneo de nuevo....


Saludos!!! y Gracias por esta guía que me ha servido mucho.

---

### Post by 51b0r6 on 2013-05-02
Parece que ya no funciona en ubuntu 13.04. Hice todos los pasos, probé con todos los drivers habidos y por haber (la página de descargas se ha modificado y de hecho relinkea, pero he bajado drivers viejos), inclusive he seguido las instrucciones de otros tutoriales y sigo sin poder hacerla funcionar. Tengo la misma impresora. ¿Se les ocurre cuál puede ser el problema?

---

### Post by pepperoni2 on 2013-09-12
Hello, I have a problem at this step:
```
[FONT=Ubuntu Mono]sudo chmod 0755 /proc/bus/usb/004/002[/FONT]
```

I don't have that directory
at  /proc/bus/  I only have the following directories:

input    pci

---

