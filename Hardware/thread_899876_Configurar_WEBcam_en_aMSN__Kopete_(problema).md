---
title: "Configurar WEBcam en aMSN / Kopete (problema)"
date: 2008-08-24
forum: Hardware
---

### Post by atari130xe on 2008-08-24
Foro, alguien sabe que deberia configurar para dejar la webcam funcionando bien en aMSN / Kopete? es una webcam con chip Microdia, bajé las fuentes del driver lo compilé y lo probé con Mplayer y funciona bastante bien, pero... al querer usarla con aMSN o Kopete y se vé lo que ven en la imagen que adjunté.

---

### Post by sergiom99 on 2008-08-24
postea la salida de lsusb y vemos si hay algun tip dando vueltas para hacer andar ese modelo en especial.

---

### Post by Hei Ku on 2008-08-24
Es la primer Microdia que veo funcionando, aunque se vea mal. Probaste el v4l, a ver que sale?

---

### Post by sherwoodinc on 2008-08-24
Si luego del amsn probás de nuevo el mplayer se ve bien, o sigue mal?
Podrías probar con el xawtv a ver cómo sale.

---

### Post by sherwoodinc on 2008-08-24
Perdón por el doble post, pero también estaría bueno que hagas un "dmesg" en un Terminal mientras estás usando la cámara con el amsn (a ver si el kernel tira algun error)

---

### Post by faktorqm on 2008-08-25
> **sherwoodinc said:**
> Perdón por el doble post

Tenes que usar el editar maestro! Salu2!

---

### Post by atari130xe on 2008-08-25
> **sergiom99 said:**
> postea la salida de lsusb y vemos si hay algun tip dando vueltas para hacer andar ese modelo en especial.

```
desktop:~$ lsusb
Bus 005 Device 002: ID 0c45:627b Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
desktop:~$ 

```

Hay un comando para configurar la salida de video y de audio (elegirlas) por consola pero no me acuerdo el comando y es MUY común. :confused:

---

### Post by atari130xe on 2008-08-25
> **Hei Ku said:**
> Es la primer Microdia que veo funcionando, aunque se vea mal. Probaste el v4l, a ver que sale?

San Google lo puede todo :lolflag:
este es el link con las instrucciones para compilar el driver, 
[http://www.64bitjungle.com/tech/microdia-webcam-0c54-experimental-drivers-installation-and-testing-part-1/]("http://www.64bitjungle.com/tech/microdia-webcam-0c54-experimental-drivers-installation-and-testing-part-1/")
con Mplayer sigue funcionando bien pero el problema es cuando lo quiero usar con los programas de mensajeria, en camorama sale esto:
> Could not connect to video device (/dev/video0). please check connection y el tema es que justamente quiero redireccionarlo a Video0 pero no recuerdo el bendito comando.

:lolflag: ahora con Mplayer tampoco funciona:
```
$ mplayer tv:// -tv noaudio:driver=v4l2:width=640:height=480:outfmt=yuy2:device=/dev/video0:fps=30
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: unable to open '/dev/video0': No such file or directory
v4l2: ioctl set mute failed: Bad file descriptor
v4l2: 0 frames successfully processed, 0 frames dropped.


Exiting... (End of file)

```

---

### Post by sherwoodinc on 2008-08-25
Hola!

Te fijaste si con la cámara conectada existe /dev/video0? En el tutorial del link que pasate dice que te puede llegar a tocar "/dev/video1", y calculo que podría ser incluso algún otro número.
Si ese es el caso, bastaría con probar con la línea de comando que pusiste arriba, reemplazando video0 con el que corresponda.

faktorqm:
> Tenes que usar el editar maestro! Salu2!
Apenas posteé me acordé del edit. Soy muy newbie en lo que a foros respecta, es la primera vez que me inscribo a uno en tantos años de webear :), ir a las Jornadas de Software Libre de la semana pasada me motivó a participar un poco más.

---

### Post by atari130xe on 2008-08-26
va dsmeg de la webcam (logré hacerla funcionar nuevamente con Mplayer pero sigo mal con aMSN y Kopete):

```
[ 4145.020687] microdia: Unknown symbol video_ioctl2
[ 4145.021105] microdia: Unknown symbol video_devdata
[ 4145.021562] microdia: Unknown symbol video_unregister_device
[ 4145.021707] microdia: Unknown symbol video_device_alloc
[ 4145.021776] microdia: Unknown symbol video_register_device
[ 4145.022110] microdia: Unknown symbol video_device_release
[ 4161.540717] Linux video capture interface: v2.00
[ 4183.570142] microdia: Microdia USB2.0 webcam driver startup
[ 4183.570192] microdia: Microdia USB2.0 Webcam - 0C45:627B found.
[ 4183.570197] microdia: Release: 0101
[ 4183.570199] microdia: Number of interfaces : 1
[ 4183.580991] microdia: Microdia USB2.0 Camera is now controlling video device /dev/video0
[ 4183.581045] usbcore: registered new interface driver usb_microdia_driver
[ 4183.581048] microdia: v0.0.0 : Microdia USB Video Camera
[ 4198.449844] microdia: Freeing 0 v4l2 buffers
[ 4198.451256] microdia: Buffers Allocated 2
[ 4198.691234] microdia: No EEPROM found
[ 4227.297990] microdia: Freeing 2 v4l2 buffers
[ 4244.523926] microdia: Freeing 0 v4l2 buffers
[ 4244.525051] microdia: Buffers Allocated 2
[ 4244.762920] microdia: No EEPROM found
[ 4266.260721] microdia: Freeing 2 v4l2 buffers
[ 4271.479919] microdia: Freeing 0 v4l2 buffers
[ 4271.480662] microdia: Buffers Allocated 2
[ 4271.537654] microdia: No EEPROM found
[ 4272.240831] microdia: Freeing 2 v4l2 buffers
[ 4272.983012] microdia: Freeing 0 v4l2 buffers
[ 4272.983671] microdia: Buffers Allocated 2
[ 4273.036781] microdia: No EEPROM found
[ 4343.188899] microdia: Freeing 2 v4l2 buffers
[ 4351.518110] microdia: Freeing 0 v4l2 buffers
[ 4358.503677] microdia: Freeing 0 v4l2 buffers
[ 4358.504323] microdia: Buffers Allocated 2
[ 4358.570533] microdia: No EEPROM found
[ 4359.370446] microdia: Freeing 2 v4l2 buffers
[ 4360.058939] microdia: Freeing 0 v4l2 buffers
[ 4360.059523] microdia: Buffers Allocated 2
[ 4360.120443] microdia: No EEPROM found
[ 4365.214600] microdia: Freeing 2 v4l2 buffers
[ 4390.600263] microdia: Freeing 0 v4l2 buffers
[ 4390.601191] microdia: Buffers Allocated 2
[ 4390.654896] microdia: No EEPROM found
[ 4448.368857] microdia: Freeing 2 v4l2 buffers
[ 4470.069888] microdia: Freeing 0 v4l2 buffers
[ 4470.084082] microdia: Freeing 0 v4l2 buffers
[ 4470.084660] microdia: Buffers Allocated 2
[ 4470.165961] microdia: No EEPROM found
[ 4498.988691] microdia: Freeing 2 v4l2 buffers
[ 5426.468592] microdia: Freeing 0 v4l2 buffers
[ 5426.469071] microdia: Buffers Allocated 2
[ 5426.525481] microdia: No EEPROM found
[ 5433.825214] microdia: Freeing 2 v4l2 buffers
[ 5433.829652] microdia: Freeing 0 v4l2 buffers
[ 5433.830872] microdia: Buffers Allocated 2
[ 5433.887599] microdia: No EEPROM found
[ 5436.542477] microdia: Freeing 2 v4l2 buffers
[ 5436.545862] microdia: Freeing 0 v4l2 buffers
[ 5436.546796] microdia: Buffers Allocated 2
[ 5436.602116] microdia: No EEPROM found
desktop:~$ 


```

---

### Post by kowal on 2008-09-24
Y si ejecutás desde consola Kopete o aMSN a ver que te dice?

---

