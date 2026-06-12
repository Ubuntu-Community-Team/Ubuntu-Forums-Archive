---
title: "Impresora canon PIXMA IP1000 en Karmic 64 bit"
date: 2009-12-04
forum: Hardware
---

### Post by asterix77 on 2009-12-04
He indagado un montón en internet buscando un controlador para mi notebook de esta impresora; canon PIXMA IP1000, pero solo he encontrado driver para arquitectura de 32 bit. Por favor si alguien me puede ayudar a buscar un driver de 64 bit, o si hay otra forma que se pueda hacer funcionar esta impresora.


Gracias de antemano

---

### Post by Carlos C on 2009-12-04
Prueba descargándolo de esta página:

[http://software.canon-europe.com/products/0010104.asp](http://software.canon-europe.com/products/0010104.asp)

Vas a tener que compilarlo, pero debiera funcionar.

---

### Post by asterix77 on 2009-12-04
Hola Carlos.

He descargado el archivo, pero no sé como compilarlo. El archivo descargado es un archivo comprimido (22414.tgz) que al extarerlo me genera  una carpeta (llamada 22414)que contiene dos archivos más; **guidepixmaip1000-2.50-1.tar.gz** y además** iP1000Linux.tar.gz**. El primero es como instalarlo pero en otras distribuciones no ubuntu, el segundo al extarerlo genera una carpeta llamada ip1000 que contiene 4 archivos rpm los cuales son: [B]
bjfilter-common-2.50-2.i386.rpm[/B]
**bjfilter-common-2.50-2.src.rpm**
[B]bjfilter-pixmaip1500-2.50-2.i386.rpm
bjfilter-pixmaip1500-lprng-2.50-2.i386.rpm[/B]

Y desde aquí no se que hacer**.**

Saludos

---

### Post by Carlos C on 2009-12-06
rpm son paquetes para otras distribuciones linux, como Suse, Red Hat, etc. Un opción es que los transformes en archivos deb, que es el tipo de paquetes que usa ubuntu. Se puede hacer con "alien". Te advierto que no es seguro que funcione. En internet está lleno de información al respecto. Te adjunto un par de ejemplos:

[http://www.guia-ubuntu.org/index.php?title=Añadir_aplicaciones#Convertir_paquetes_RPM_a_Deb](http://www.guia-ubuntu.org/index.php?title=Añadir_aplicaciones#Convertir_paquetes_RPM_a_Deb)

[http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/](http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/)


Saludos.

---

### Post by asterix77 on 2009-12-06
Carlos 

He tratado de pasar cada uno de los archivos rpm a deb con alien, pero no he podido con ninguno de ellos, aparece lo siguiente:

$sudo alien bjfilter-common-2.50-2.i386.rpm
error: incorrect format: unknown tag
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/bjfilter-common
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: aviso: debian/bjfilter-common/usr/local/bin/bjcups contains an unresolvable reference to symbol poptGetOptArg: it's probably a plugin.
dpkg-shlibdeps: aviso: se omitieron otros 3 avisos similares (use -v para verlos todos).
dpkg-shlibdeps: aviso: dependency on libpopt.so.0 could be avoided if "debian/bjfilter-common/usr/local/bin/bjcups debian/bjfilter-common/usr/lib/cups/filter/pstocanonbj" were not uselessly linked against it (they use none of its symbols).
dh_gencontrol
dpkg-gencontrol: error: la arquitectura del anfitrión 'amd64' no aparece en la lista de arquitectura de paquetes (i386)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Error 1
find: «bjfilter-common-2.50»: No existe el fichero ó directorio
$

El mensaje que me aparece es similar para los 4 archivos.

y al terminar todo el proceso, aparece solo una carpeta que en el ejemplo descrito es una carpeta llamada **bjfilter-common-2.50**.


Saludos

---

### Post by Patriciologico on 2009-12-06
Revisa estas soluciones

1.- por medio de un repositorio [http://eos87.blogspot.com/2008/06/instalar-canon-pixma-ip-1000-en-ubuntu.html](http://eos87.blogspot.com/2008/06/instalar-canon-pixma-ip-1000-en-ubuntu.html)

2.- Manual usando Alien [http://molinux.bravehost.com/canon_ip100.html](http://molinux.bravehost.com/canon_ip100.html)

Encontre dos soluciones mas que decian funcionar pero una apunta a un post borrado y la otra al antiguo foro ubuntu-cl :p

Saludos

---

### Post by Patriciologico on 2009-12-06
Revisa estas soluciones

1.- por medio de un repositorio [http://eos87.blogspot.com/2008/06/instalar-canon-pixma-ip-1000-en-ubuntu.html](http://eos87.blogspot.com/2008/06/instalar-canon-pixma-ip-1000-en-ubuntu.html)

2.- Manual usando Alien [http://molinux.bravehost.com/canon_ip100.html](http://molinux.bravehost.com/canon_ip100.html)

Encontre dos soluciones mas que decian funcionar pero una apunta a un post borrado y la otra al antiguo foro ubuntu-cl :p

Saludos

---

### Post by asterix77 on 2009-12-07
Patricio:

He intentado de las dos formas, primero

$ sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete libcnbj-2.5

con la segunda forma me sucede lo comentado anteriormente, es decir me arroja un error.
Además uso karmic de 64 bit; cuando usé intrepid de 32 bit no tuve ningún problema al instalar esta impresora ya que hay varios driver. El problema es que para 64 bit al parecer no los hay. No sé si siguiendo los pasos adecuados se pueda usar el código fuente, ya que gracias a Carlos, he descargado uno, pero no sé que hacer.


Saludos

---

### Post by nopersona on 2009-12-07
El problema es de una librería específica que es de 32 bits, y que hasta lo que sé (hasta la 8.10 era así) no estaba ni en planes de 64 bits.

---

### Post by Patriciologico on 2009-12-08
Encontre un deb [http://www.box.net/shared/4tbqjfit80](http://www.box.net/shared/4tbqjfit80)

Otra cosa, si el problema esta en una libreria que solo funciona en 32 bits, ¿no existe una forma de crear una jaula para hacerla funcionar? no lo he usado nunca espero opiniones [http://sherekan.com.ar/2008/11/19/que-es-y-como-crear-chroot/](http://sherekan.com.ar/2008/11/19/que-es-y-como-crear-chroot/)

Saludos

---

### Post by moreback on 2009-12-08
Debiera ser posible, por ejemplo el plugin de flash corre en 64 bits mediante unas bibliotecas llamadas ia32-libs.

Saludos.

---

### Post by nechus on 2009-12-08
Estee... no quiero ser simplista, ni derrotista, ni nada terminado en ista, pero yo tuve el mismito problema hace un tiempo y la custión sencillamente me cabrió. No hubo caso que la Canon Pixma funcionara como la gente en Ubuntu. No es culpa de Ubuntu. Los malditos de Canon y de Mocosoft tienen la culpa.

Lo que finalmente hice fue instalar XP en Virtualbox ( [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) ) y cada vez que tengo que imprimir me interno en el lado oscuro de la fuerza.

Por favor, no me odien. Eso me pasa por no probar el hardware antes de comprarlo. Cuando estudie programación a lo mejor voy a encontrar la forma de hacer funcionar la impresora desde Ubuntu.

---

### Post by asterix77 on 2009-12-08
Descargué el paquete sugerido por patriciologo, y lo instalé. Al tratar de configurar mi impresora (sistema-Administración- impresora), es detectada como ip1000, ahora aparece en la lista de canon, la susodicha impresora; me aparece un controlador recomendado el cual selecciono, y al finalizar y querer enviar una página de prueba aparece lo siguiente:
"Hubo un problema al imprimir el documento "Test Page". Stopping jobs because the scheduler could not execute a filter".

También me aparece este otro "cups-insecure-filter". En la siguiente dirección [http://www.cups.org/documentation.php/spec-ipp.html](http://www.cups.org/documentation.php/spec-ipp.html) aparece lo siguiente con respecto a este error: "

[LIST]
[*]cups-insecure-filter-warning - a filter or backend (or the 	directory containing the filter or backend) has insecure file 	permissions. CUPS will not execute programs with world write permissions 	or setuid programs. When run as root (the default), CUPS also does not 	execute programs that are not owned by root. 	CUPS 1.4/Mac OS X 10.6
[/LIST]
Por otro lado en [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/436544](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/436544) dice algunas cosas con respecto a este mensaje:

sudo chown root:root /usr/lib/cups/filter/pstocanonbj.
sudo chown -hR root /usr/lib/cups/filter
 sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend


He ejecutado todos ellos, pero sin éxito

---

### Post by Carlos C on 2009-12-08
Movido a "Hardware".

Saludos.

---

### Post by Carlos C on 2009-12-08
En ubuntu-es.org parecen resuelto:

[http://www.ubuntu-es.org/?q=node/33283#comment-339877](http://www.ubuntu-es.org/?q=node/33283#comment-339877)


Como es un sitio que muchas veces está caído copio lo que dicen:

> Enviado por lrenjifo el Vie, 30/10/2009 - 21:05
     Yo tambien tuve el mismo problema y fue un lio buscar los archivos asi que los junte e hize un pequeño manual de instalacion:
 [http://www.megaupload.com/?d=8GAVVZOH](http://www.megaupload.com/?d=8GAVVZOH)
(7 archivos: 3 rpm + 3 deb + manual)
Lo probe en Ubuntu 9.04
 #Instalamos alien para la convercion de paquetes
 Usuario@LinuxPc:~$ sudo su
root@LinuxPc:/home/Usuario# sudo apt-get update
root@LinuxPc:/home/Usuario# sudo apt-get install alien
 #En mi caso los paquetes se encuentran en el Escritorio en una carpeta llamada "Ip1000"
root@LinuxPc:/home/Usuario# cd Escritorio/
root@LinuxPc:/home/Usuario/Escritorio# cd Ip1000/
 #En caso tengamos paquetes rpm tendremos que convertirlo a .deb, para esto hacemos:
 root@LinuxPc:/home/Usuario/Escritorio/Ip1000# sudo alien -k bjfilter-common-2.50-2.i386.rpm
root@LinuxPc:/home/Usuario/Escritorio/Ip1000# sudo alien -k bjfilter-pixmaip1000-2.50-2.i386.rpm
root@LinuxPc:/home/Usuario/Escritorio/Ip1000# sudo alien -k bjfilter-pixmaip1000-lprng-2.50-2.i386.rpm 
 #Paquetes "deb" listo para instalar:
#Si ya teniamos los paquetes deb obviamos todo lo anterior
 root@LinuxPc:/home/Usuario/Escritorio/Ip1000# sudo dpkg -i bjfilter-common_2.50-2_i386.deb
root@LinuxPc:/home/Usuario/Escritorio/Ip1000# sudo dpkg -i bjfilter-pixmaip1000_2.50-2_i386.deb
root@LinuxPc:/home/Usuario/Escritorio/Ip1000# sudo dpkg -i bjfilter-pixmaip1000-lprng_2.50-2_i386.deb 
 #Abrimos el editor:
 root@LinuxPc:/home/Usuario/Escritorio/Ip1000# gedit /usr/share/cups/model/canonpixmaip1000.ppd
 #Añadimos lo siguiente:
    *OpenUI *CNQuality/Quality: PickOne
    *DefaultCNQuality: 3
    *CNQuality 2/High: "2"
    *CNQuality 3/Normal: "3"
    *CNQuality 4/Standard: "4"
    *CNQuality 5/Economy: "5"
    *CloseUI: *CNQualityE
 #Reemplazamos Esto:
    *OpenUI *Resolution/Output Resolution: PickOne
    *DefaultResolution: 600
    *Resolution 600/600 dpi: "setpagedevice"
    *CloseUI: *Resolution
 #Por:
    *OpenUI *Resolution/Output Resolution: PickOne
    *DefaultResolution: 600
    *Resolution 600/600 dpi: "setpagedevice"
    *Resolution 1200/1200 dpi: "setpagedevice"
    *Resolution 2400/2400 dpi: "setpagedevice"
    *CloseUI: *Resolution
 root@LinuxPc:/home/Usuario/Escritorio/Ip1000# ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
root@LinuxPc:/home/Usuario/Escritorio/Ip1000# ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
root@LinuxPc:/home/Usuario/Escritorio/Ip1000# ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
root@LinuxPc:/home/Usuario/Escritorio/Ip1000# /etc/init.d/cupsys restart
 root@LinuxPc:/home/Usuario/Escritorio/Ip1000# exit
 #Encendemos la impresora buscamos driver canon -> Ip1000 Ver.2.5
Saludos.

---

### Post by asterix77 on 2009-12-08
Carlos he descargado del enlace que me distes, los paquetes vienen en rpm y deb. Pero al tratar de instalarlos me arroja un error de arquitectura (son solo para 32 bit y no para 64 que es mi caso).

Ahora con el enlace que me pasó patricio (comentado anteriormente). He cambiado los permisos al archivo /usr/lib/cups/filter/pstocanonbj, Y ahora ya no me aparece ningún error. Al mandar una impresión de prueba (o cualquiera), aparece un mensaje de que se envió a la impresora, aparece el trabajo en la cola de impresión, y luego aparece como realizada la impresión, **pero no imprime nada**. No sé si esto es una mejora o no, pero sigo con el problema.

Lo peor de todo es que mi impresora está todavía buena, y no la puedo usar. De seguir sin solución, tendré que darme por vencido.

Saludos

---

### Post by nopersona on 2009-12-08
> **nechus said:**
> Estee... no quiero ser simplista, ni derrotista, ni nada terminado en ista, pero yo tuve el mismito problema hace un tiempo y la custión sencillamente me cabrió. No hubo caso que la Canon Pixma funcionara como la gente en Ubuntu. No es culpa de Ubuntu. Los malditos de Canon y de Mocosoft tienen la culpa.

Lo que finalmente hice fue instalar XP en Virtualbox ( [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) ) y cada vez que tengo que imprimir me interno en el lado oscuro de la fuerza.

Por favor, no me odien. Eso me pasa por no probar el hardware antes de comprarlo. Cuando estudie programación a lo mejor voy a encontrar la forma de hacer funcionar la impresora desde Ubuntu.

Ojo, que acá estamos hablando de un librería específica, las IP (PIXMA) SÍ FUNCIONAN EN 32 BITS, de hecho, desde la serie 1000 a la 2200 no hay ningún problema, incluso hay drivers de mantención. Bastante raro tu caso. 



> **asterix77 said:**
> Ahora con el enlace que me pasó patricio (comentado anteriormente). He cambiado los permisos al archivo /usr/lib/cups/filter/pstocanonbj, Y ahora ya no me aparece ningún error. Al mandar una impresión de prueba (o cualquiera), aparece un mensaje de que se envió a la impresora, aparece el trabajo en la cola de impresión, y luego aparece como realizada la impresión, **pero no imprime nada**. No sé si esto es una mejora o no, pero sigo con el problema.

Lo peor de todo es que mi impresora está todavía buena, y no la puedo usar. De seguir sin solución, tendré que darme por vencido.

Saludos

Sí, eso es un avance. Sería bueno ver la salida de cups y si está funcionando correctamente. Intenta ingresar desde el navegador, o reinciar el servicio. Así como lo veo, vale la pena sacrificar un correcto y estable funcionamiento de la impresora (si está buena y no cuentas con otra disponible) por querer mayor gestión de recursos? Alguien dijo 32 bits?

---

### Post by asterix77 on 2009-12-09
Nopersona, efectivamente esa impresora está bien sosportada para arquitecturas de 32 bit, de hecho yo la usaba perfectamente en intrepid; inclusive al ejecutar el live cd de 32 bit de karmic, puedo instalar el driver e imprimir sin problemas. El problema es en arquitecturas de 64 bit.

Como prueba he descargado el turboprint 2 desde su página oficial,y me imprime sin dificultad, excepto de que como es privativo, solo puedes descargar una prueba de evaluación que cuando imprimes, sale un tremendo logo del programa. Única solución, comprar la licencia, por lo que finalmente lo desinstalé.

Con respecto a ver algún tipo de error, al menos a mi no me aparece ninguno (o tal vez no sé como verlos). Al menos cuando mando algo a imprimir ya sea desde el entorno gráfico o desde la terminal, aparece como que el trabajo fue enviado y se imprimió cuando en realidad no imprime nada.

Saludos

---

### Post by asterix77 on 2009-12-13
Bueno, al fin logré solucionar mi problema en mi notebook. Dejo el como lo pude finalmente realizar.

a) Bajé el driver de la siguiente dirección proporcionada por patriciológico: [http://www.box.net/shared/4tbqjfit80](http://www.box.net/shared/4tbqjfit80).

Como es deb lo instalé fácilmente.

b) Después de instalarlo, me detectaba la impresora, y al pricipio me marcaba un tipo de error, que desapareció al cambiarle los permisos al archivo /usr/lib/cups/filter/pstocanonbj.

c) Después de esto dejó de mostrarme errores, pero seguía sin imprimir (a pesar de decirme que la impresión había sido correcta).

d) He aquí la solución: hice una búsqueda de todos los archivos "ip1000" en mi pc de escritorio (jaunty 32 bit, en el cual mi impresora funcionaba perfectamente), y los comparé con el listado en mi notebook (karmic 64 bit, donde tenía el problema), y me dí cuenta que en la ruta /usr/local/bin/ de mi notebook, no existía el archivo "bjfilterpixmaip1000" (que sí existía en mi pc con jaunty); luego simplemente copié dicho archivo a la misma ruta en karmic, dí los mismos permisos, y eurekas, funcionó sin problemas.

He realizado varias impresiones, he reiniciado y todo, y ha seguido funcionando.

Doy gracias a todos por sus aportes, y doy por cerrado el tema.

Saludos

---

### Post by Patriciologico on 2009-12-13
Excelente, me alegro. [Solved] now.

---

