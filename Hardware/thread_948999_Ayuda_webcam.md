---
title: "Ayuda webcam"
date: 2008-10-15
forum: Hardware
---

### Post by beatlina on 2008-10-15
Hola gente... aca les traigo mi inquietud... por supuesto, no puedo hacer andar mi camara web en ubuntu hardy.
les dejo el dato del lsusb
 0ac8:307b Z-Star Microelectronics Corp.  

La marca es satellite y la pagina web de la misma dice que tiene soporte para LINUX les dejo la dirreción de la página: [http://www.satelliteargentina.com/esp/asp_produtos.asp?key=372&tipo=WB-C11&bkey=2]("http://www.satelliteargentina.com/esp/asp_produtos.asp?key=372&tipo=WB-C11&bkey=2")

Bien ademas les dejo unos links que contienen info de gente que hizo andar la web cam esta y yo cumpli con tuti lo que alli decia pero no puedo!!

[http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon/]("http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon/")

[http://ph.ubuntuforums.com/showpost.php?p=5435670&postcount=9]("http://ph.ubuntuforums.com/showpost.php?p=5435670&postcount=9")

Aún no he pagado la webcam, y me la prestan por el finde a ver si logre algo... yo me pregunto.. por qué es tan dificil conseguir una que funcione el linux???

---

### Post by faktorqm on 2008-10-15
Hola, cual hiciste de los dos? El segundo que crea un usuario pero despues le asigna 777 a /dev/video0 esta mal.... con 777 le asigna permisos a TODO EL MUNDO, asi que para que crea un usuario? no se. en segundo lugar no se le pone 777 a los dispositivos.... 

Aca te armo, segun toooodos los que vi dando vueltas por ahi, otro tuto de cero.

Vas a aplicaciones -> accesorios -> terminal.

Instalamos lo necesario para poder compilar y que luego funcione el driver:

```
sudo apt-get install linux-headers-$(uname -r) build-essential autoconf automake binutils libsdl-ocaml libsdl-ocaml-dev libsdl1.2debian  libsdl1.2debian-alsa libsdl-image1.2-dev libsdl-dev -y
```

Bajamos el codigo fuente del driver:

```
wget -c http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
```

Lo descomprimimos:

```
tar xvfz gspcav1-20071224.tar.gz
```

Ingresamos dentro de la carpeta:

```
cd gspcav1-20071224/
```

Ahora compilamos:

```
make
```

Lo instalamos:

```
sudo make install
```

Lo activamos:

```
sudo modprobe gspca
```

Y a partir de ahora, podemos instalar el programa para manejar la webcam, la cosa es que no todos los programas funcionan como deberian, no se por que. Yo uso wxcam, cheese, o el que aparezca primero, ahora probe este que te voy a pasar ahora y tambien anda, asi que ¡a probar!

Instalamos: ```
sudo apt-get install camstream -y
```
Ejecutamos: ```
camstream
```

Ahora, ir a File -> Open viewer... y ahi te aparece una ventana, teoricamente te tendria que aparecer algo y cuando le des ok tenes que verte, aunque sea chiquito, pero tener algo de imagen.
Una vez ahi, apretas sobre el icono cuadrado (parece un reloj...) negro arriba a la izquierda, y ahi nos abre una nueva pagina de configuracion para tocar la resolucion, balance de colores, etcetc.

Te dejo la salida de comandos mía (si, me tome el trabajo de hacerlo yo...) para que te quedes tranquila comparandola con la tuya asi ves que pasa en cada momento.

```

[COLOR="Red"]faktorqm@the-edge:~$[/COLOR] wget http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
--21:11:06--  http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
           => `gspcav1-20071224.tar.gz'
Resolviendo mxhaard.free.fr... 212.27.63.150
Conectando a mxhaard.free.fr|212.27.63.150|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 214.717 (210K) [application/x-gzip]

100%[====================================>] 214.717       11.86K/s    ETA 00:00

21:11:38 (6.79 KB/s) - `gspcav1-20071224.tar.gz' guardado [214717/214717]

[COLOR="Red"]faktorqm@the-edge:~$[/COLOR] tar xvfz gspcav1-20071224.tar.gz 
gspcav1-20071224/
gspcav1-20071224/decoder/
gspcav1-20071224/decoder/gspcadecoder.c
gspcav1-20071224/decoder/gspcadecoder.h
gspcav1-20071224/decoder/gspcadecoder-OSX.c
gspcav1-20071224/decoder/gspcadecoder-OSX.h
gspcav1-20071224/Makefile
gspcav1-20071224/Vimicro/
gspcav1-20071224/Vimicro/vc032x_sensor.h
gspcav1-20071224/Vimicro/zc3xx.h
gspcav1-20071224/Vimicro/cs2102.h
gspcav1-20071224/Vimicro/vc032x.h
gspcav1-20071224/Vimicro/pas106b.h
gspcav1-20071224/Vimicro/icm105a.h
gspcav1-20071224/Vimicro/hv7131b.h
gspcav1-20071224/Vimicro/hv7131c.h
gspcav1-20071224/Vimicro/pb0330.h
gspcav1-20071224/Vimicro/ov7630c.h
gspcav1-20071224/Vimicro/mc501cb.h
gspcav1-20071224/Vimicro/tas5130c_vf0250.h
gspcav1-20071224/Vimicro/ov7620.h
gspcav1-20071224/Vimicro/tas5130c.h
gspcav1-20071224/Vimicro/hdcs2020.h
gspcav1-20071224/Etoms/
gspcav1-20071224/Etoms/et61xx51.h
gspcav1-20071224/Sonix/
gspcav1-20071224/Sonix/sn9cxxx.h
gspcav1-20071224/Sonix/sonix.h
gspcav1-20071224/utils/
gspcav1-20071224/utils/spcagamma.h
gspcav1-20071224/utils/spcausb.h
gspcav1-20071224/utils/spcaCompat.h
gspcav1-20071224/Conexant/
gspcav1-20071224/Conexant/cx11646.h
gspcav1-20071224/Conexant/cxlib.h
gspcav1-20071224/Pixart/
gspcav1-20071224/Pixart/pac207-OSX.h
gspcav1-20071224/Pixart/pac7311.h
gspcav1-20071224/Pixart/pac207.h
gspcav1-20071224/changelog
gspcav1-20071224/license
gspcav1-20071224/gspca_core.c
gspcav1-20071224/Transvision/
gspcav1-20071224/Transvision/tv8532.h
gspcav1-20071224/Makefile.kld
gspcav1-20071224/gspca.h
gspcav1-20071224/Sunplus/
gspcav1-20071224/Sunplus/spca501.dat
gspcav1-20071224/Sunplus/spca505.dat
gspcav1-20071224/Sunplus/spca508.dat
gspcav1-20071224/Sunplus/spca561-OSX.h
gspcav1-20071224/Sunplus/spca506.h
gspcav1-20071224/Sunplus/spca561.h
gspcav1-20071224/Sunplus/spca501_init.h
gspcav1-20071224/Sunplus/spca508_init-OSX.h
gspcav1-20071224/Sunplus/spca508_init.h
gspcav1-20071224/Sunplus/spca501_init-OSX.h
gspcav1-20071224/Sunplus/spca505_init.h
gspcav1-20071224/Sunplus-jpeg/
gspcav1-20071224/Sunplus-jpeg/spca500.dat
gspcav1-20071224/Sunplus-jpeg/jpeg_qtables.h
gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.h
gspcav1-20071224/Sunplus-jpeg/sp5xxfw2.dat
gspcav1-20071224/Sunplus-jpeg/spca500_init.h
gspcav1-20071224/gspca_build
gspcav1-20071224/READ_AND_INSTALL
gspcav1-20071224/Mars-Semi/
gspcav1-20071224/Mars-Semi/mr97311.h
gspcav1-20071224/cutlog.py
[COLOR="Red"]faktorqm@the-edge:~$[/COLOR] cd gspcav1-20071224/
[COLOR="Red"]faktorqm@the-edge:~/gspcav1-20071224$[/COLOR]  make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/faktorqm/gspcav1-20071224 CC=cc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/faktorqm/gspcav1-20071224/gspca_core.o
  CC [M]  /home/faktorqm/gspcav1-20071224/decoder/gspcadecoder.o
  LD [M]  /home/faktorqm/gspcav1-20071224/gspca.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/faktorqm/gspcav1-20071224/gspca.mod.o
  LD [M]  /home/faktorqm/gspcav1-20071224/gspca.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'
[COLOR="Red"]faktorqm@the-edge:~/gspcav1-20071224$[/COLOR] sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
[COLOR="Red"]faktorqm@the-edge:~/gspcav1-20071224$[/COLOR] sudo modprobe gspca
[COLOR="Red"]faktorqm@the-edge:~/gspcav1-20071224$[/COLOR] lsmod | grep gsp
gspca                 643920  0 
videodev               29440  2 gspca,ov511
usbcore               146028  5 gspca,ov511,ehci_hcd,ohci_hcd
[COLOR="Red"]faktorqm@the-edge:~/gspcav1-20071224$ [/COLOR]

```

Hasta aca compilé y levante el modulo, el 0v511 es mi camara web...

```
[COLOR="Red"]faktorqm@the-edge:~/gspcav1-20071224$[/COLOR] sudo apt-get install camstream -y
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Paquetes recomendados
  camstream-doc
Se instalarán los siguientes paquetes NUEVOS:
  camstream
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 367kB de archivos.
Se utilizarán 1159kB de espacio de disco adicional después de desempaquetar.
Des:1 http://ar.archive.ubuntu.com hardy/universe camstream 0.27+dfsg-1 [367kB]
Descargados 367kB en 7s (50,8kB/s)                                             
Seleccionando el paquete camstream previamente no seleccionado.
(Leyendo la base de datos ...  
255350 ficheros y directorios instalados actualmente.)
Desempaquetando camstream (de .../camstream_0.27+dfsg-1_i386.deb) ...
Configurando camstream (0.27+dfsg-1) ...
Creating video4linux (/dev/video*) special files...
udev active, devices will be created in /dev/.static/dev/

[COLOR="Red"]faktorqm@the-edge:~/gspcav1-20071224$[/COLOR] camstream 
W: CamStream version 0.27 starting.
>> void CCamStreamApp::ReadConfigFile()
  W: Failed to open configuration file '/home/faktorqm/.camstream/config.xml' for reading.
  D: creating <defaults> node
  D: creating <videodevices> node
  D: creating <audiodevices> node
<< void CCamStreamApp::ReadConfigFile()
[COLOR="Red"]...[/COLOR]
>> void CCamStreamApp::SaveConfigFile()
<< void CCamStreamApp::SaveConfigFile()
[COLOR="Red"]faktorqm@the-edge:~/gspcav1-20071224$ [/COLOR]

```

Espero que te haya servido de algo, y no te preocupes si no te anda, postea aca y lo vamos viendo. Salu2!!!

---

### Post by beatlina on 2008-10-15
Hola amigo, ya es como la tercera vez que me ayudas así que me tomo el atrevimiento de llamarte así.
Te cuento hasta la instalacion y llamada del camstream estuvo todo perfecto. La 1º vez que ejecuté desde la consola el camstren me dejo lo siguiente

```
root@ubuntu:/home/betina/gspcav1-20071224# camstream
W: Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
W: CamStream version 0.27 starting.
>> void CCamStreamApp::ReadConfigFile()
<< void CCamStreamApp::ReadConfigFile()
D: CVideoCollector::VideoCollector()
D: >> CVideoDevice::CVideoDevice()
D: << CVideoDevice::CVideoDevice()
D: >> CVideoDeviceLinux::CVideoDeviceLinux(/dev/video0)
D: << CVideoDeviceLinux::CVideoDeviceLinux()
>> CCamWindow::CCamWindow(QWidget*, const char*)
<< CCamWindow::CCamWindow(QWidget*, const char*)
>> CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
  >> QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
    Trying to find video options for LDLC OV7620+VC302@/dev/video0
    D: Creating new node for LDLC OV7620+VC302@/dev/video0
  << QDomNode CCamStreamApp::FindVideoDeviceConfig(const QString&, const QString&, bool)
  >> CVideoOptions::CVideoOptions()
    >> virtual void CVideoOptions::DeclareVariables()
    << virtual void CVideoOptions::DeclareVariables()
  << CVideoOptions::CVideoOptions()
  D: CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
  W: QFont::setWeight: Value out of range (100)
  D: >> CVideoDeviceLinux::Init()
  W: Cannot query audio capabilities of video device.
  D: Using mmap(), size = 2457616
  D: mmap()ed 2 buffers.
  D: Initial image size = (176, 144)
  D: << CVideoDeviceLinux::Init()
  D: CVideoSettingsDlg::SizeChanged(176x144)
  D: CVideoSettingsDlg::FramerateChanged(10)
  D: No Philips webcam detected, removing extension tab
  D: CCamPanel::SetSize(176x144)
  D: CCamPanel::SetImageSize(176x144)
  D: CCamPanel::SetVisibleSize(176x144)
  D: CCamPanel::SetSize(176x144)
  D: CCamPanel::SetImageSize(176x144)
  D: CCamPanel::SetVisibleSize(176x144)
  >> void CWebCamViewer::RecalcTotalViewSize()
  << void CWebCamViewer::RecalcTotalViewSize()
<< CWebCamViewer::CWebCamViewer(CVideoDevice*, QWidget*, const char*)
D: >> CVideoDevice::IncrementPalette(0)
D: >> CVideoDeviceLinux::StartCapture()
D: CVideoDeviceLinux::SetPalette picked palette 5 [rgb32]
D: >> CVideoDeviceLinux::CreateImagesRGB()
D: << CVideoDeviceLinux::CreateImagesRGB()
D: >> CVideoDeviceLinux::run()...
D: << CVideoDeviceLinux::StartCapture()
D: << CVideoDevice::IncrementPalette()
>> virtual void CCamStreamMainWindow::closeEvent(QCloseEvent*)
  >> void CCamStreamMainWindow::CloseAll()
    >> virtual CWebCamViewer::~CWebCamViewer()
      >> void CWebCamViewer::StopTimeSnap()
        >> void CWebCamViewer::StopFTP()
        << void CWebCamViewer::StopFTP()
      << void CWebCamViewer::StopTimeSnap()
      D: >> CVideoDeviceLinux::StopCapture()
      D: Waiting for capture thread to stop...
```

Llegué al ver el cuadradito negro que me decis, pero una imágen totalmente negra, luego estuvo todo congelado un par de minutos, COLGOSE... tuve que cerrar.
Cuando regresé no pude volver a ver ese cuadradito del que me hablas.

te dejo también la salida de:

```
betina@ubuntu:~$ lsmod | grep gsp
gspca                 643792  1 
videodev               29440  2 gspca
usbcore               146412  4 gspca,ehci_hcd,uhci_hcd
betina@ubuntu:~$ 
```

por lo que vos me decis acerca de tu 0v511, yo no tengo nada que se le parezca. Tal vez esto pueda tener que ver...

Mil gracias por todo el laburo que te tomaste en armarme todo tan pedagógicamente, creo que estoy empezando a entender más acerca de UBUNTU. :)

---

### Post by beatlina on 2008-10-15
QUE BRUTA SOY 

> por lo que vos me decis acerca de tu 0v511, yo no tengo nada que se le parezca. Tal vez esto pueda tener que ver...

ahora entiendo el gspca es el que me corresponde a mi y vos instalaste para ayudarme.

Te cuento que reinicie la pc,  logre ver el cuadradito negro nuevamente, te dejo dos pantallazos (perdón no los acomodé bien, porque me estoy amigando con el GIMP). En el 1º veras el famoso cuadradito y aunque voy a cambiar la resolucion de colores y eso, queda igual... en el 2º intente cambiar otra cosa y colgose nuevamente...:confused:

---

### Post by faktorqm on 2008-10-15
Hola, no uses el usuario root por favor, no es que soy un maniatico, pero podes romper mucho el sistema si te mandas alguna macana. En cambio sudo, si bien tiene permisos, no tiene TODOS los de root.

EDITO: antes de hacer algo: probá de poner modo VGA como estan en las fotos de abajo. Capaz es eso.

Y si, la Ov511 es el modulo para mi webcam, y levante el tuyo, total como no la tengo enchufada es lo mismo. Bueno, por lo que veo la cosa es que la detecta bien, pero no muestra imagen. Probemos algo:

Vamos a desactivar el modulo: ```
sudo modprobe -r gspca
```

Luego lo activamos pero con la siguiente opcion:

```
sudo modprobe gspca force_rgb=1
```

Y volvé a probar con el camstream. Te dejo 2 capturas de pantalla de otro usuario que lo probó y le anduvo. (e intenta ejecutar camstream como usuario y NO COMO ROOT)

[http://farm3.static.flickr.com/2240/2301195896_cc96e0affb_o.png](http://farm3.static.flickr.com/2240/2301195896_cc96e0affb_o.png)
[http://farm3.static.flickr.com/2218/2301196578_2309094910_o.png](http://farm3.static.flickr.com/2218/2301196578_2309094910_o.png)

Para descartar problemas de permisos, pegá la salida de este comando:

```
ls -l /dev/video*
```

Salu2!!!!

---

### Post by beatlina on 2008-10-15
> Hola, no uses el usuario root por favor, no es que soy un maniatico, pero podes romper mucho el sistema si te mandas alguna macana. En cambio sudo, si bien tiene permisos, no tiene TODOS los de root.

Tenes razon pero yo no lo sabia... gracias por la advertencia 

Intenté con lo de VGA pero se quedá tildado todo...

También hice lo de:

```
sudo modprobe gspca force_rgb=1
```

pero nada... sigue todo negro 

te dejo la salida que me pedis:

```

betina@ubuntu:~$ ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 2008-10-16 00:15 /dev/video0
betina@ubuntu:~$ 
```

Continua mi pena...

---

### Post by beatlina on 2008-10-19
Che no me dejen sola... tengo un día más con la camara, sino la tengo que devoler, y nunca voy a poder verme con mi prima de córdoba!!! PLEASE HELP

---

### Post by faktorqm on 2008-10-20
Perdón, es que los findes no miro el foro...
Y no se que decirte, me parece que por algun otro motivo que desconozco no te anda, podrias probar como ultima opcion antes de devolverla hacer:

```
sudo gedit /etc/modprobe.d/options
```

y agregar esta linea:

```
options gspca force_rgb=1
```

Guardas y salis. Ahora abrimos este otro:

```
sudo gedit /etc/modules
```

y ahi agrega la palabra "gspca" (sin comillas) y guarda el archivo.

Despues abri ```
sudo gedit /etc/modprobe.d/blacklist
```
y agrega:

```
blacklist zc0301
```

Y reinicia la compu. Ahi teoricamente tambien te deberia andar. Si sigue sin andar, o anda pero se cuelga, hace:

```
sudo chmod 777 /dev/video0
```

para descartar problemas de permisos, total no perdemos nada...

Y sino tambien podes probar con otros programas aparte del camstream. Tenes cheese, wxcam, camorama, kopete, amsn, vlc, ekiga, skype, etc. aunque sea para ver si se ve... Salu2!

---

### Post by beatlina on 2008-10-20
Nada de nada faktorqm, probé amns, vlc, cheese, y camorama y nada... creo que estoy al horno....

No te preocupes la devolveré mañana y vere con otra, un amigo me presto una y salió de una andando esa en la caja tenía a nuestro amigo el pinguino impreso, pero no puedo conseguirla me dijeron que está agotada... 

Tirame una marca de alguna que sepas que anda y me compro esa... si??

Gracias por toda tu ayuda!!!

---

### Post by Hei Ku on 2008-10-20
Genius y Logitech.

---

### Post by beatlina on 2008-10-20
Hei Ku, no creo que cualquier Genius funcione, tuve en mis manos uno 316 que salió de toque andando (no era mia y no pude conseguir la misma) también tuvo una 312 y me fue imposible ponerla en funcionamiento.

---

### Post by sartrejp on 2008-10-22
Probá con un live cd de intrepid ibex,  a ver que pasa. Yo tuve que seguir 100 tutoriales para hacer andar mi webcam genius, y en ibex, anduvo directamente, solo abrí el amsn y estaba lista para funcionar, por ahí en cuanto actualices te olvidás del problema.

---

