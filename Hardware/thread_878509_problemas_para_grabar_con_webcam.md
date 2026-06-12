---
title: "problemas para grabar con webcam"
date: 2008-08-03
forum: Hardware
---

### Post by kekalizarazo on 2008-08-03
hola. tngo una dell 1420 con ubuntu hardy y la webcam viene integrada. Mi webcam funciona con el ekiga y con el amsn.
 He intendo grabar con Mplayer (mencoder) y me saca el siguiente error

yotas@dell-laptop:~$ mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
=================================================================
 WARNING: YOU ARE USING V4L DEMUXER WITH V4L2 DRIVERS!!!
 As the V4L1 compatibility layer is broken, this may not work.
 If you encounter any problems, use driver=v4l2 instead.
 Bugreports on driver=v4l with v4l2 drivers will be ignored.
=================================================================
Selected device: Laptop Integrated Webcam
 Capabilites: capture 
 Device type: 1
 Supported sizes: 48x32 => 1600x1200
 Inputs: 1
ioctl get channel failed: Invalid argument
Unable to open '/dev/dsp1': No such file or directory
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.
[/SIZE]
cambio el parametro v4l a v4l2 y le arreglo el dispostivo de audio y saca:
[SIZE="2"]yotas@dell-laptop:~$ mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: Laptop Integrated Webcam
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
Exepción de coma flotante[/SIZE]


con freej también me saca error
 engine running at 24 FPS
 v4l: size 320x240 not supported res: -1
 create_layer : V4L open failed
 [*] Closing video4linux grabber layer
 closing video4linux device 9
 can't create a layer with /dev/video0
 can't open captura.avi to create a Layer: No such file or directory
 
he probado también con el cheese y cuando me graba el video no sale en la parte de abajo (donde aparecen las fotos) y cuando uno cierra el programa desaparece de la carpeta donde se guardó. No tiene sonido y corre muy rápido.
con el vlc probé y jugando con la configuración (de acuerdo a un post de esta misma pagina: [http://ubuntuforums.org/showthread.php?t=143732](http://ubuntuforums.org/showthread.php?t=143732)) me saca audio pero nunca video, (pero al iniciar la grabación si se prende la luz de mi webcam)

con el wxcam nunca logré configurarlo para que se viera adecuadamente el video, se ve la mitad de mi cara y la pantalla dividida en varias partes. El video resultante tampoco tiene audio. 

Ya estoy cansada de probar configuraciones y configuraciones.
me pueden ayudar por favor?

---

### Post by pol666 on 2008-08-03
no quiero ser pesimista pero agradece que te reconocio la cmarita

---

### Post by faktorqm on 2008-08-04
Hola, bueno veo lo del wxcam lleva tiempo, pero sale andando de una, es cuestion de paciencia... yo tarde algo asi como 15 minutos la primera vez y si, debo admitirlo, me puse nervioso :lolflag:

Para wxcam tenes que elegir YUYV y v4l, si no te anda, YUYV y v4l2, si no te anda, proba con v4l2 todos los modos, YUYV, RGB, etcetc, alguna anda, yo probe todos hasta que uno anduvo :P
Cuando encontras la configuracion, elegi el script de abajo segun driver. 

Proba estos scripts a ver que pasa, y posteá las salidas obviamente. Tambien asegurate de que la webcam esta en /dev/video0, y nada, suerte! :P

```
mencoder tv:// -tv driver=v4l:device=/dev/video0:width=320:height=240:brightness=90:forceaudio:alsa:volume=35000 -o webcam.avi -ovc lavc -lavcopts vcodec=mjpeg -oac mp3lame -lameopts cbr:br=64:mode=3
```

si no:

```
mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1:brightness=90:volume=35000 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
```

Espero que te haya servido, salu2!

---

### Post by kekalizarazo on 2008-08-04
Hola probé otra vez con el wxcam como dijiste cone v4l2 con todas las combinaciones y en ninguna anda. cuando pruebo con el v4l dice que hay un error y que chequee la configuracion del fotograma.

con mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1:brightness=90:volume=35000 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi


me tira el siguiente error
yotas@dell-laptop:~$ mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1:brightness=90:volume=35000 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: Laptop Integrated Webcam
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Unable to open '/dev/dsp1': No such file or directory
Unable to open '/dev/dsp1': No such file or directory
Unable to open '/dev/dsp1': No such file or directory
v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.
Fallo de segmentación


le arreglé el /dev/dspl y me esto me sale
yotas@dell-laptop:~$ mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp:brightness=90:volume=35000 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: Laptop Integrated Webcam
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
Exepción de coma flotante

yotas@dell-laptop:~$ mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp:brightness=90:volume=35000 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: Laptop Integrated Webcam
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
Exepción de coma flotante

q será lo que pasa?

---

### Post by faktorqm on 2008-08-05
Me parece que te topaste con un bug del mencoder.... tira fallo de segmentacion... (eso es un error en el programa). Lo que podes hacer por ahora es postear la salida del comando "lspci", "lsusb" y "dmesg | grep webcam" para ver como seguimos. Salu2!

---

### Post by kekalizarazo on 2008-08-05
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 15ca:00c3  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

y en el ultimo: dmesg | grep webcam
no me salio nada

:S

---

### Post by faktorqm on 2008-08-06
Bueno la webcam es la 05a9:2640 que aparece en el lsusb y es algo asi como una OmniVision OV2640 (incluida en notebooks Dell Inspiron 1420/1720 y algunos modelos de HP) de la marca OmniVision.
Aca: [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) dice que anda con driver, que esta aca: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) pero la verdad que no estaba ahi y tuve que hacer un poco de magia..... 

La cosa es que vas a tener que compilar, yo ya probé en mi sistema asi q no te va a dar ningun dolor de cabeza, y anda bien. (obviamente no tengo la webcam, que el proceso de instalacion termine bien, no significa que ande el dispositivo).

Tenes que descomprimir el archivo este que te paso acá (click derecho -> extraer...) y abrir una terminal. Ahi entras al directorio que creaste con la descompresion y escribis:

```
make
```

```
sudo make install
```

y lo que se ve es esto:

```

faktorqm@the-edge:~/Documentos/uvc$ make
Building USB Video Class driver...
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/faktorqm/Documentos/uvc/uvc_driver.o
  CC [M]  /home/faktorqm/Documentos/uvc/uvc_queue.o
  CC [M]  /home/faktorqm/Documentos/uvc/uvc_v4l2.o
  CC [M]  /home/faktorqm/Documentos/uvc/uvc_video.o
  CC [M]  /home/faktorqm/Documentos/uvc/uvc_ctrl.o
  LD [M]  /home/faktorqm/Documentos/uvc/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/faktorqm/Documentos/uvc/uvcvideo.mod.o
  LD [M]  /home/faktorqm/Documentos/uvc/uvcvideo.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'
faktorqm@the-edge:~/Documentos/uvc$  sudo make install
[sudo] password for faktorqm: 
Installing USB Video Class driver...
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'
  INSTALL /home/faktorqm/Documentos/uvc/uvcvideo.ko
  DEPMOD  2.6.24-19-generic
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'
depmod -ae
faktorqm@the-edge:~/Documentos/uvc$ 

```

si tenes una salida parecida a esta, quiere decir que todo termino bien. Este driver es para v4l2, asi que no te gastes en probar nada con v4l. Proba con todos los programas de vuelta :P mientras yo me fijo como desinstalar el driver de la webcam de mi sistema :lolflag: Salu2!!!

---

### Post by kekalizarazo on 2008-10-09
:s la verdad me cansé de andar molestando con eso. finalmente decidí grabar con mi cámara normalita. Pero muchas gracias por ayudar... y como hago para dar las gracias oficialmente?

---

### Post by faktorqm on 2008-10-10
Tenes que apretar la medallita que está abajo a la derecha del post que te sirvió. Salu2!

---

