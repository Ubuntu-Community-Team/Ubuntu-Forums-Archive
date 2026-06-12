---
title: "Problemas al instalar impresora Canon iP1300"
date: 2009-10-31
forum: Hardware
---

### Post by maxialva on 2009-10-31
Hola:

Soy bastante nuevo en ubuntu 9.10 karmic y he querido instala mi impresora canon ip1300 siguiendo el siguiente instructivo:

sudo aptitude install build-essential
  
[LIST]
[*]Actualizamos los paquetes escribiendo:
[/LIST]
  sudo apt-get update
  
[LIST]
[*]Ahora tenemos que instalar el paquete que nos ayudara a convertir los archivos binarios a .deb y algunas librerías necesarias.  Escribimos lo siguiente:
[/LIST]
  sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common
  
[LIST]
[*]Es momento de descargar los drivers de la impresora.  Para propósitos de este tutorial vamos a asumir que te encuentras en el directorio /home/tu-nombre/obux.  Los drivers que vamos a utilizar son los de la impresora iP2200, por lo cual escribimos en un terminal :
[/LIST]
  mkdir obux
cd obux
wget [http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz](http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz)
  
[LIST]
[*]Después de descargar el archivo lo descomprimimos escribiendo la siguiente instrucción:
[/LIST]
  tar -xvzf iP2200_Linux_260.tar.gz
  
[LIST]
[*]Ahora convertimos los paquetes RPM a paquetes especiales para Ubuntu, osea a paquetes DEB (Fue por ello que al inicio instalamos la utilidad Alien):
[/LIST]
  sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip2200-2.60-1.i386.rpm
      [B]Instalando nuestra impresora ip1700
[/B]     
[LIST]
[*]Bueno, después de tanto paso previo procedemos a instalar los archivos que generamos para lo cual tecleamos en el terminal:
[/LIST]
  sudo dpkg -i *.deb
  
[LIST]
[*]Ahora creamos los enlaces simbólicos para las librerías por si estos no funcionan de manera correcta. Esto es debido a que el archivo libtiff.so.3 es una versión antigua y es la que utiliza el driver que instalamos, por lo cual para corregirlo escribimos:
[/LIST]
  sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3
sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
  
[LIST]
[*]Ahora hacemos que el sistema se de cuenta de los cambios hechos:
[/LIST]
  sudo ldconfig
  
[LIST]
[*]También reiniciamos Cups (El sistema que administra las impresoras en Linux)
[/LIST]
  sudo /etc/init.d/cupsys restart
  
[LIST]
[*]Por ultimo añadimos la nueva impresora.  Nos vamos a *Sistema&#8594;Administración&#8594;Impresoras. *Si ya nos aparece una impresora con el nombre iP1700 la **borramos** (Ya que el sistema la detecto al inicio pero no la instalo).
[*]Ahora damos clic en “*Impresora Nueva*” y seleccionamos la opción “*Canon iP1700 USB #1*” y damos clic en “Adelante”.
[*]Ahora damos clic en la opción “Proporciona Archivo PPD” y se activara una opción donde dice “Ninguno” Ahí damos clic y nos dirigimos a la siguiente ubicación: */usr/share/cups/model/*
[*]Ya estando allí seleccionamos el driver **canonip2200.ppd**.
[*]Ahora damos clic en “Adelante” y por ultimo damos clic en “Aplicar”.
[/LIST]
 Y en un paso intermedio, para instalar los paquetes me lanza el pirmer problema en la consola:

(Leyendo la base de datos ...  00%
242110 ficheros y directorios instalados actualmente.)
Preparando para reemplazar cnijfilter-common 2.60-2 (usando cnijfilter-common_2.60-2_i386.deb) ...
Desempaquetando el reemplazo de cnijfilter-common ...
Desempaquetando cnijfilter-ip2200 (de cnijfilter-ip2200_2.60-2_i386.deb) ...
dpkg: error al procesar cnijfilter-ip2200_2.60-2_i386.deb (--install):
 intentando sobreescribir «/usr/lib/libcnbpcmcm256.so.6.31.1», que está también en el paquete libcnbj-2.6 0:0-1
dpkg-deb: el subproceso pegar fue terminado por la señal (Tubería rota)
Configurando cnijfilter-common (2.60-2) ...
Se encontraron errores al procesar:
 cnijfilter-ip2200_2.60-2_i386.deb
 

Y luego al seguir aparecen mas. Llevo bastante tiempo tratando de instalar y no he podido. Ojala me puedan ayudar para seguir en este sistema operativo y no tener que cambiarme.

De antemano gracias.

---

### Post by moreback on 2009-11-01
El error que te da al instalar el paquete puede deberse a que ya viene instalado el filtro para ese tipo de impresoras, yo creo que bastaría con agregar la impresora, indicar el archivo ppd y luego probar.

¿Probaste eso?

---

### Post by maxialva on 2009-11-01
> **moreback said:**
> El error que te da al instalar el paquete puede deberse a que ya viene instalado el filtro para ese tipo de impresoras, yo creo que bastaría con agregar la impresora, indicar el archivo ppd y luego probar.

¿Probaste eso?

He probado eso, pero al momento de indicar el archivo ppd no encuentro el ip2200?

Por fa ayuda, necesito urgente la impresora.

Saludos y gracias

---

### Post by Patriciologico on 2009-11-02
Hola Bienvenido, tu post fue movido por no publicar en el lugar correcto, por favor [lee las normas]("http://ubuntuforums.org/showthread.php?t=1162750")

Saludos

---

### Post by Carlos C on 2009-11-02
Tengo la impresión de que estás hablando de [este]("http://obux.wordpress.com/2008/08/10/instalar-canon-pixma-ip1700-ip1600-1p1300-en-ubuntu/") how-to. Por lo que veo dice que no funciona para Ubuntu 64 bits ¿Qué versión tienes instalada?

Por otro lado, esos no son los últimos drivers, los que debes bajar son los que actualmente dispone canon en su sitio:

[http://software.canon-europe.com/software/0024301.asp](http://software.canon-europe.com/software/0024301.asp)

Prueba realizando el mismo procedimiento, pero esta vez con los drivers actualizados, creo que tu problema puede ser ese.

Saludos.

---

### Post by tatadeluxe on 2009-11-07
Hola maxialva como dice Carlos C, al parecer estas siguiendo el procedimiento recomendado por la comunidad.
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)
¿Estas usando una version 64bits?
# Para saber que version de ubuntu estas usando pon en consola:
```
echo `lsb_release -ds`"("`lsb_release -cs`")"`uname -m`
```
Pero dado que estas usando Karmic debiera funcionarte **la forma fácil**:
Ir en el menú a Sistema>Administracion>Impresoras
Hacer click en Nueva
Elije la impresora IP2200 (suponiendo que ya la tienes encendida y conectada)
Haz click en adelante e instala las opciones por defecto.
Cuando ya tengas creada la impresora, haz click botón derecho sobre ella
Elije propiedades
Elige cambiar Marca y Modelo
Elige proporciona archivo PPD
Elige la ruta /usr/share/cups/model/canonip2200.ppd
Aplica los cambios y tu impresora ya debiera funcionar.

Existe la posibilidad que cuando creaste esos enlaces simbólicos e instalaste esos paquetes deb hayas estropeado algo de la configuración original.
> intentando sobreescribir «/usr/lib/libcnbpcmcm256.so.6.31.1», que está también en el paquete libcnbj-2.6 0:0-1
dpkg-deb: el subproceso pegar fue terminado por la señal (Tubería rota)
En caso que no funcione **la forma fácil**, te recomiendo que pruebes con el liveCD de Karmic 64bit y el liveCD normal, si la forma fácil funciona, está la opción de reinstalar (porque ponerse a reparar paquetes rotos es una opción que puede complicarse más de lo necesario), si te complica bajar los liveCD, yo se los podría pasar al Jecho, que me pidió que te ayudara con tu problema.

Saludos

---

### Post by charlie-tahn on 2009-11-17
Maxialba,
Creo tener tu mismo problema.
Siempre instalé los drivers de mi impresora ip1300 transformando los paquetes rpm con alien. Y haciendo lo de ese tutorial. Eso me funcionó hasta hace poco.
Incluso pude actualizar a karmic y aún funcionó por un tiempo. Todo se transfiguró con la última actualización que le he hecho donde se actualizaba también CUPS. Desde ahora cada vez que le pido imprimir la cpu se sobrecarga y no imprime nada.
Lamentablemente no hay drivers actualizados ni soporte para esta impresora.
He leído por ahí que también puede deberse a la dependencia de estos paquetes de drivers con libgtk1.2 que está fuera de 9.10. (Que lo hayan sacado me sienta bien mal ya que también este paquete me ayudaba a reconocer mi joystick y jugar, ahora lo reconoce rara vez.... y si a eso le sumamos los problemas de sonido de pulseaudio jugar en karmic está peliagudo)

---

