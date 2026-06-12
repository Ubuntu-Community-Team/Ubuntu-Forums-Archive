---
title: "Problemas con audio CK804 AC'97 en Ubuntu 8.10"
date: 2009-04-16
forum: Hardware
---

### Post by fenandito on 2009-04-16
Hola a todos. Tengo problemas con el audio integrado de mi placa base. En el control de volúmen me aparece una x blanca con fondo rojo y cuando quiero poner "Abrir el control de volumen" me aparece un cartel de error que dice "No se han encontrado complementos o dispositivos control de volumen de GStreamer."
Esta es mi salida de lspci

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
05:06.0 Communication controller: Agere Systems Device 0620
05:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
05:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

El dispositivo 00:04.0 es mi controlador de audio.
Anda bien porque con el liveCD me lo detecta y anda perfecto. Pero se ve que en alguna actualización se desconfiguró. Saludos

---

### Post by faktorqm on 2009-04-17
Hola, antes que nada bienvenido al foro.

Te cuento el problema: no se cuanto sabes de gnu/linux, pero voy intentar ser lo mas claro posible. El problema esta en un modulo del kernel, el de sonido. El kernel es la interfaz entre los programas y los dispositivos fisicos de la compu. Un modulo miralo como una especie de driver para poder controlar un dispositvo en particular, en este caso es la placa de sonido. Ahora bien, cuando vos instalas el sistema operativo este coloca los drivers correspondientes en el kernel, y escuchas lo mas bien. Cuando actualizaste con el gestor de actualizaciones, se te actualizo el kernel, pero como tu placa no esta soportada por la configuracion por defecto, ahora no escuchas nada.
Para volver a escuchar, tenemos que "decirle" al kernel que vuelva a usar el modulo correspondiente a tu modelo de placa de sonido.
Si tenes alguna duda respecto de esto y/o alguna pregunta no dudes en consultar.

Te cuento la solución:

Vas a aplicaciones -> accesorios -> terminal y escribis (o copias y pegas como mas te guste)

```
sudo apt-get install module-assistant build-essential
```

Te va a pedir una contraseña, la contraseña que tenes que poner es la que usas cuando arrancas la compu. Eso te va a instalar dos programas, el primero es un asistente para modulos como su nombre lo indica y el otro son las herramientas para generar el modulo que necesitas.

```
sudo module-assistant prepare,update
```

Este comando te va a actualizar el asistente de modulos con tu configuracion.

```
sudo module-assistant build,install alsa
```

Este te va a crear el modulo que necesitas para tu placa. En gnu/linux existe ALSA (Advanced Linux Sound Architecture, arquitectura de sonido avanzada de linux). Este ALSA es el que se ocupa que el sonido vuelva a su lugar :P

```
sudo depmod
```

Este le dice al kernel que cargue el modulo que acabaste de crear en el paso anterior. A partir de ahora deberias tener sonido, no se si tendras que reiniciar. (no deberias, pero uno nunca sabe :P)

Si no te anduvo algo, postea por favor con la mayor cantidad de datos posibles, no importa si te parece que no agrega nada.

Una observacion, cuando recien prendes la computadora, te aparece el grub, un cargador de arranque de sistema operativo. Si tenes solo ubuntu quiza no lo veas, si tenes mas sistemas operativos si. Fijate que ahi te van a aparecer varias entradas, y si vos ingresas al sistema con una anterior a la ultima (fijate bien los numeros de version) vas a poder verificar que volves a tener sonido sin tocar nada. 

Una ultima observacion, a veces, no siempre, cada vez que actualices el kernel del sistema operativo vas a tener que repetir el proceso, hasta que la gente de alsa actualice su paquete y ya no tengas que hacer todo este proceso de vuelta. De hecho por lo general en cada version nueva de ubuntu solucionan todo este tipo de inconvenientes, y el 23 de abril sale 9.04, Jaunty Jackalope, que es la nueva version de Ubuntu. Podrias pensar en reinstalar (opcion NO recomendada) o simplemente en actualizar desde la instalacion que tenes ahora (opcion _MUY_ recomendada).

Espero haberte ayudado. Salu2!

---

### Post by equiman on 2009-07-21
Cundo aplico:

```
sudo module-assistant build,install alsa
```

Me da tres opciones a elegir en una pantalla azul:

```
&#9474; ¡Ha fallado la compilación del paquete alsa-source! ¿Qué      &#9474; 
&#9474; desea hacer?          

&#9474;  VIEW     Examinar el fichero del registro de la compilación  &#9474; 
&#9474;  CONTINUE Omitirlo y continuar con la operación siguiente     &#9474; 
&#9474;  STOP     Detener el procesamiento de órdenes de compilación  
```

Finalmente le doy continuar y me saca este error:


```
The source tarball could not be found!
Package alsa-source not installed?
Running "m-a -f get alsa-source" may help.
find: «/usr/src/modules/alsa*»: No existe el fichero ó directorio
```

Espero que me puedan ayudar pues ya me pase del todo a Ubuntu y es lo unico que me esta haciendo pemsar regresar a XP.

---

### Post by equiman on 2009-07-21
Definitivamnte si uno no lee no lo puede solucionar. El ultimo mensaje del post anterioir decia que habia que hacer:

```
sudo m-a -f get alsa-source
```

Luego de correr ese, ya si deja hacer el resto del proceso. A ver si despues de esto me funciona el sonido... reinicio y les cuento.

---

### Post by equiman on 2009-07-22
A la final si me dejo finalziar el proceso, pero igual no me dejeba escuchar nada. Reinicie y entre desde el menu con el kernel 2.26.28-11.

Cambie en las Preferencias -> Sonido todo a OSS y ya si me dejo reproducir.

Aproveche e hice tambien otra prueba y fue con el Live CD y vaya sorpresa me lleve que desde el Live CD si deja reproducir sonidos sin ningun problema. Verifique con "uname -r" y efectivamente el Live CD corre con el kernel 2.26.28-11.

Asi que esto si estaba bien extraño... reinstale entonces de nuevo y vi que el kernel con que queda instalado es el 2.26.28-11. Ingreso a Ubuntu, instalo todas las actulizaciones... y ya me queda con el kernel 2.26.28-13 con el cual de nuevo hay problema de sonido.

Reinicio y cargo de nuevo con el 2.26.28-11 y hay sonido, pero luego intento reiniciar y empezar con el 2.26.28-13 y se queda pegado en el inicio (no se en que pero comienzan a titilar las luces de indicadores del teclado intermitentemente).

Espero esta infromación le sirva a los demas. Yo por ahora como estaba limpiando todo y pasandome completamente a Linux y a EXT4, voy a reinstalar Ubuntu desde 0 y al actulizar lo dejare con el kernell 2.26.28-11.

---

### Post by guillermolisi on 2009-07-22
Para confirmar si el problema esta relacionado con los modulos de sonido de la placa, podrias iniciar con el kernel 2.6.28-13 y en una terminal/consola ingresar el comando ```
lsmod
``` para luego mostrarnos el resultado de su salida ?

Para saber que kernel estas usando, entre otras cosas, el comando se llama uname y no "aname". Comento para no confundir a otros.

---

### Post by equiman on 2009-07-23
Es muy extraño pero reinstale y todo esta funcionando perfecto con el Kernel 2.26.28-13 estoy reinstalando cada comando y reiniciando para ver si alguno de ellos los que esta probocando el fallo pero hasta ahora nada.

Si encuentro algo les cuento. Por ahora todo esto va bien:

```
MEDIBUNTU
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783 

sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude update

sudo aptitude install libdvdcss2
sudo aptitude install w32codecs
sudo aptitude install libdvdread3
sudo aptitude install ffmpeg
sudo aptitude install non-free-codecs
sudo aptitude install libamrnb3
sudo aptitude install libamrwb3
sudo aptitude install ubuntu-restricted-extras 
```

PD: Corregi tambien el uname en mi mensaje para evitar confusiones.

---

### Post by equiman on 2009-07-23
Creo que por fin encontre el causante del problema:

```
sudo aptitude install mpd mpc ario
```

Este es el mensaje que saca en la instalación y hay unos errores que se pueden ver en el momento de la instalacion:

```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Se instalarán los siguiente paquetes NUEVOS:
  ario ario-common{a} libao2{a} mpc mpd 
0 paquetes actualizados, 5 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B/619kB de ficheros. Después de desempaquetar se usarán 2671kB.
¿Quiere continuar? [Y/n/?] y
Escribiendo información de estado extendido... Hecho
Seleccionando el paquete ario-common previamente no seleccionado.
(Leyendo la base de datos ...  
137476 ficheros y directorios instalados actualmente.)
Desempaquetando ario-common (de .../ario-common_1.2.2-1_all.deb) ...
Seleccionando el paquete ario previamente no seleccionado.
Desempaquetando ario (de .../archives/ario_1.2.2-1_i386.deb) ...
Seleccionando el paquete libao2 previamente no seleccionado.
Desempaquetando libao2 (de .../libao2_0.8.8-4ubuntu1_i386.deb) ...
Seleccionando el paquete mpc previamente no seleccionado.
Desempaquetando mpc (de .../archives/mpc_0.14-1_i386.deb) ...
Seleccionando el paquete mpd previamente no seleccionado.
Desempaquetando mpd (de .../mpd_0.14.2-3ubuntu2_i386.deb) ...
Procesando disparadores para man-db ...
Configurando ario-common (1.2.2-1) ...

Configurando ario (1.2.2-1) ...

Configurando libao2 (0.8.8-4ubuntu1) ...

Configurando mpc (0.14-1) ...
Configurando mpd (0.14.2-3ubuntu2) ...
 * Starting Music Player Daemon mpd                                             No "audio_output" defined in config file
Attempt to detect audio output device
Attempting to detect a alsa audio device
No protocol specified
E: client-conf-x11.c: [COLOR="Red"]XOpenDisplay() failed[/COLOR]
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN  7311] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: [COLOR="Red"]XOpenDisplay() faile[/COLOR]d
Successfully detected a alsa audio device
                                                                         [ OK ]

Procesando disparadores para libc6 ...
ldconfig deferred processing now taking place
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
```



Debe ser uno de estos 3, pues despues de esto me quede sin sonido.

El comando lsmode me regresa lo siguiente:
```
Module                  Size  Used by
isofs                  39844  1 
udf                    87716  0 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
saa7134_alsa           20000  0 
snd_intel8x0           37532  1 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
saa7134               152020  1 saa7134_alsa
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
nvidia               7233756  26 
ir_common              52228  1 saa7134
ppdev                  15620  0 
psmouse                61972  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               41600  1 saa7134
v4l1_compat            21764  1 videodev
compat_ioctl32          9344  1 saa7134
v4l2_common            20992  1 saa7134
videobuf_dma_sg        20484  2 saa7134_alsa,saa7134
videobuf_core          26500  2 saa7134,videobuf_dma_sg
tveeprom               20100  1 saa7134
pcspkr                 10496  0 
k8temp                 12416  0 
serio_raw              13316  0 
agpgart                42696  1 nvidia
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
i2c_nforce2            14980  0 
snd                    62628  13 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
sky2                   54916  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
forcedeth              61712  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

---

### Post by staar on 2009-07-23
te quedás sin sonido al instalar mpd??? sabés usarlo?? requiere algo de configuración a mano...

saludos

---

### Post by equiman on 2009-07-23
Si, lo vengo utilizando desde la 8.10 combinado con Conky. Al menos ya se que eso es el causante.

Lo que no he podido entender es el error ue saca en la inmstalacion... pues despues de ello es que se me anula por completo el sonido.

Entiendo que para funcionar el mpd hay que hacer configuraciones a manos, pero no entiendo porque anula el resto de sonidos.

---

### Post by staar on 2009-07-23
mpd es algo especial, porque es un servidor más que nada y a veces se lleva mal (bastante) con pulseaudio, por lios de permisos o del orden de inicio de cada uno...

saludos

---

