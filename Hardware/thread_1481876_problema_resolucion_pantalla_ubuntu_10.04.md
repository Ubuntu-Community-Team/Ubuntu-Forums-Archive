---
title: "problema resolucion pantalla ubuntu 10.04"
date: 2010-05-13
forum: Hardware
---

### Post by jcartagena on 2010-05-13
Estimados:

Acudo a uds nuevamente pk tengo un problema, luego de pasearme por google e probar varias opciones para poder aumentar la resolucion de mi pantalla, ya casi me di por vencido. Para ponerlos en contexto, luego de instalar LL mi pantalla solo soporta la resolucion 800x600, intente solucionar el problema usando varias guias, pero sin obtener resultados.

MI note es un toshiba satellite A25-S2792, algo antiguo, pero aperrador, tiene una tarjeta integrada trident microsystems (super chanta)

julio@neo-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

Bueno, como con las otras versiones no habia tenido este problema, comence a imporovisar y en google encontre unas mini guias pero para tarjeta ati, el asunto es que segui pasos como los sgtes:

como Primer Paso vamos a habilitar una Resolución  mas a nuestra Configuración de Monitores, primero verificamos la opción  que queremos tener con nuestro Monitor y nuestra Tarjeta gráfica(en este  caso una ATI Radeon X1300/Saphire), estos datos los obtenemos con esta  sintaxis:

$ gtf 1280 1024 70



 Esta linea de comando me arrojo algo parecido a lo siguiente:

# 1280×1024 @ 70.00 Hz (GTF) hsync: 63.00 kHz; pclk:  96.77 MHz
Modeline ?1280x1024_70.00? 96.77 1152 1224 1344 1536 864 865 868 900  -HSync +Vsync



Luego de Obtener los datos para agregar a los modos de Pantalla  procedemos a agregar este modo en el siguiente archivo: (**esto es solo  un ejemplo cada quien debe poner exactamente los datos que arroje la  linea del *gtf* según la resolución que escogieron**):

$ sudo gedit /etc/gdm/Init/Default



Luego de estar abierto agregaran las siguientes lineas justo antes de **exit  0**:


/usr/bin/xrandr --newmode 1280x1024  96.77 1152 1224 1344 1536 864 865  868 900 -HSync +Vsync

/usr/bin/xrandr --addmode DVI-0 1280x1024

/usr/bin/xrandr --output DVI-0 --mode 1280x1024




ya de esta manera tenemos la resolucion deseada de Nuestro Escritorio y  no hace falta estar ejecutando las lineas en cada reinicio...

**_Nota:_*** Cabe destacar que use DVI-0 ya que es el  dispositivo DVI el que tengo conectado al monitor, puede que ustedes  tengan que colocar VGA-0 o VGA1 o DVI-1, todo depende de cual sea su  caso...*

Luego de guardar el archivo simplemente con un:

$ sudo reboot



La nueva configuracion de pantalla estara agregada y habilitada en las  opciones de resolución de monitores de nuestro ubuntu (**Sistema >  Preferencias > Monitores**).

Bien es todo, de esta manera ya pueden agregar la Resolución que deseen a  su ubuntu sin problema alguno ya que es la solución definitiva a  cualquier Versión de Ubuntu y cabe destacar que sirve para cualquier  tipo de tarjeta de vídeo.

Para mi solucionar este inconveniente es lo mejor que puedo hacer porque  estoy acostumbrado a resoluciones altas en mi Equipo, y no podía  ganarme Ubuntu en esta nueva Versión.

***Espero que este Tutorial Ayude a muchos, hasta una próxima  oportunidad!***         


En fin, quien a tenido este problema, o mejor aun, quien me podria ayudar con esto


de antemano muchas gracias a la comunidad ubuntu.cl

jc

PS: algo que se habia olvidado contarles, alguien me puede decir si  es normal que no vea el archivo xorg.conf en /etc/X11 ????? pregunto porque al llegar a esa carpeta no veo a dicho archivo, pero si lo abro por consola usando
sudo gedit /etc/X11/xorg.conf 

se abre un archivo que no tiene nada escrito.......

---

### Post by Carlos C on 2010-05-25
> **jcartagena said:**
> Estimados:

PS: algo que se habia olvidado contarles, alguien me puede decir si  es normal que no vea el archivo xorg.conf en /etc/X11 ????? pregunto porque al llegar a esa carpeta no veo a dicho archivo, pero si lo abro por consola usando
sudo gedit /etc/X11/xorg.conf 

se abre un archivo que no tiene nada escrito.......
Efectivamente ese archivo ya no existe en Ubuntu. Únicamente cuando necesitas modificar la configuración por defecto es necesario crear ese archivo.

Saludos.

---

### Post by Carlos C on 2010-05-27
Para crear un nuevo xorg.conf pueden seguir estas instrucciones:

[http://ubuntuforums.org/showpost.php?p=8820771&postcount=7](http://ubuntuforums.org/showpost.php?p=8820771&postcount=7)

Saludos.

---

