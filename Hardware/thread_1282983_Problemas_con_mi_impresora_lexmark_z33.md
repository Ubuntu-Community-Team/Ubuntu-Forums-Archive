---
title: "Problemas con mi impresora lexmark z33"
date: 2009-10-05
forum: Hardware
---

### Post by woody01 on 2009-10-05
Hola Gente de ubuntu:
Soy algo nuevo en el sistema operativo (ubuntu 9.04) y no puedo instalar mi impresora LEXMARK z33. Veo las alternativas del sistema y no aparece. Busco info en los demás foros de ubuntu "around the world" y NINGUNO entrega soluciones para lexmark z33. Uno entregó uno para lexmark z600 que andaba bien para las demás y el archivo que entrega es .sh que NO lo lee ubuntu (o debería decir MI ubuntu?? Hay algo más que instalar?)
Tuve anteriomente una EPSON EPL 6200L que imprimía bastante bien, pero cada vez que actualizaba el ubuntu tenía que instalarla otra vez. Un amigo que entiende de esto (usuario de debian) sabiamente me sugirió cambiar de impresora... Pero al cambiarla nuevamente tengo estos problemas... Hay solución para esto? Es decir, no es aceptable el tener que conseguirse una impresora para la que ubuntu tenga el controlador, pues es el SO el que debería adaptarse a mis necesidades y no al revés!

Alguien puede ayudarme? Alguien tiene alguna solución que no sea "hasta la nueva actualización"??

Saludos y agradezco de antemano su buena voluntad. :confused:

---

### Post by themasterdark on 2009-10-05
hola.. mira y no tengo esa impresora, pero encontre algo que quizas te sirva espero que si:

fuente: [http://www.ubuntu-es.org/index.php?q=node/18296](http://www.ubuntu-es.org/index.php?q=node/18296) (cambie un link, porque en la solución que plantean ahí ya no existe el archivo en la red)

Bueno, después de haber recorrido la red y haber consultado en diferentes listas de correo, por fin pude instalar mi impresora Lexmark Z705, en Ubuntu Linux 6.06 LTS (Dapper Drake). Lo siguiente es una traducción y adaptación del post original de Black Hole Sun.

Lo que haremos más adelante, se entiende que funcionará para los siguientes modelos de impresoras Lexmark:

Lexmark 5700 (black & white only)
Lexmark X1100
Lexmark X1110
Lexmark X1130
Lexmark X1140
Lexmark X1150
Lexmark X1180
Lexmark X1185
Lexmark Z513
Lexmark Z515
Lexmark Z715
Lexmark Z55
Lexmark Z615
Lexmark Z705
Lexmark Z605
Lexmark Z600
Lexmark Z25
Dell A920
Z65 (z65 driver)
Lexmark Z33 (z35 driver)
Lexmark Z33 (z35 driver)

En primer lugar deberemos bajar el driver desde la siguiente dirección:

[http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

No se preocupen ya que como les indicaba, si bien el drivers es CJLZ600LE-CUPS-1.0-1.TAR.gz, también nos será útil para nuestra Lexmark Z705.

Seguimos entonces....bueno una vez que hemos bajado el driver, lo movemos a un directorio que crearemos de nombre "lexmark", aunque no es inminentemente necesario que así se llame, pero yo lo hice de esa forma, así que si no les molesta, háganlo de igual modo. algooooo

Luego abrimos una consola y digitamos lo siguiente: (lo que está después de # son solo comentarios).

$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # movemos el paquete a la carpeta.
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extractamos el driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # Use`tail`para extractar la porción del binario.
$ tar -xvzf install.tar.gz # extractamos el contenido producido por tail.
$ alien -t z600cups-1.0-1.i386.rpm # convertimos el rpm a tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convertimos el rpm a tgz.
$ sudo tar xvzf z600llpddk-2.0.tgz -C / # extractamos el tgz / poniéndolos al lado derecho
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract los tgz's / poniéndolos al lado derecho
$ sudo ldconfig # NO OBVIAR ESTE PASO o la impresora no encontrará las librerías necesarias
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # descomprimir el ppd

Bueno, el driver ahora se encuentra instalado. Reiniciamos el demonio cups.

/etc/rc2.d/S19cupsys restart

Chequeamos si existe comunicación de la impresora y el puerto.

$ cd /usr/lib/cups/backend
$ ./z600

La salida del comando, debería ser similar a esta.

direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer"

Si no tenemos esa respuesta, entonces montamos usb.

Agrega esto a tu archivo /etc/fstab.

usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0

Luego solo tipeamos: sudo mount usbfs. Eso debería fijarlo.

Ahora simplemente seteamos nuestra impresora a través de: Sistema>Administración>Impresoras. Nos aseguramos de seleccionar el driver z600 driver y listo.

fuente: [http://www.ubuntu-es.org/index.php?q=node/18296](http://www.ubuntu-es.org/index.php?q=node/18296) (cambie un link, porque en la solución que plantean ahí ya no existe el archivo en la red)

Espero te sirva, es bastante antiguos pero espero funcione.

Atte.
Saludos =D

---

