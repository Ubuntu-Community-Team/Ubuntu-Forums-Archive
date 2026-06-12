---
title: "Problemas con sonido en Ubuntu 9.04"
date: 2009-06-07
forum: Hardware
---

### Post by salamanca2009 on 2009-06-07
Hola a todos, os envio este correo porque estoy harto de buscar en google y no soy capaz de configurar el sonido en mi equipo.
La placa que tengo es una gigabyte GA-P31-DS3L
La tarjeta grafica es una Radeon HD 2400 PRO tambien de gigabyte
Otra tarjeta de sonido Sound Blaster 128
Tarjeta de TV/Radio con chip BT

Necesito configurar el audio en condiciones, ya que no puedo usar videoconferencia ya que no puedo usar el microfono, en gnomeradio no puedo grabar los programas de la radio que me interesan.

                             Un saludo .......................... Miguel

---

### Post by Carlos C on 2009-06-07
¿Tienes audio? Sé que tienes problemas, pero quisiera saber si tienes audio o el problema incluye que no reproduces sonido en lo absoluto. Si tienes dos tarjetas sería importante saber cuál de las dos estás usando. Si te parece bien partamos por lo básico y pega acá lo que te aparece cuando escribes en el terminal:
```
lspci
```
Saludos.

---

### Post by moreback on 2009-06-07
El comando **aplay -l** también entrega información útil!

---

### Post by salamanca2009 on 2009-06-07
Hola a los dos y gracias por contestar.
os pongo los dos resultados
miguel@pizca2009:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
03:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
03:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
03:01.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)

miguel@pizca2009:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC888 Analog [ALC888 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC888 Digital [ALC888 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: HDMI [HDA ATI HDMI], dispositivo 3: ATI HDMI [ATI HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


                          Saludos .............................. Miguel

---

### Post by Carlos C on 2009-06-09
Por lo que veo tienes una tarjeta ATI y otra Intel, ¿es un notebook? ¿usas una tarjeta usb? Ojalá pudieras explicar más las características de tu equipo.

Saludos.

---

### Post by CdK1 on 2009-06-09
Alabado sea sudo alsaconf

---

### Post by salamanca2009 on 2009-06-29
Perdon por el retraso en contestar, pero problemas con el equipo y por motivos del laboro, me han impedido contestar antes.
Como Ubuntu no trae las ALSA completas, me las descargue de su pagina y las recompile, ejecute San Alsaconf et voila, reinicio el equipo y el sonido va perfecto hasta que..... ejecuto TOTEM, me da un error de salida y a partir de ese momento, VLC no reproduce sonido. Ademas de la posible solucion, me gustaria saber porque pasa esto, ya que quiero aprender a manejar el sistema y el porque de las cosas.

                                      Salu2.......   Miguel

---

### Post by Carlos C on 2009-06-29
> **salamanca2009 said:**
> ejecuto TOTEM, me da un error de salida y a partir de ese momento, VLC no reproduce sonido. 
¿qué error de salida?

---

### Post by moreback on 2009-06-29
Yo pondría primero todo a PulseAudio en Sistema -> Preferencias -> Sonido.

---

### Post by RafaelG on 2009-06-29
> **moreback said:**
> Yo pondría primero todo a PulseAudio en Sistema -> Preferencias -> Sonido.


Yo apoyo la mocion de Moreback con PulseAudio, Tambien te recomiendo si te gusta ver videos, escuchar musica, ver fotos, etc... utilizes **Moovida **es una interface muy interesante

**Moovida**
[http://www.moovida.com/](http://www.moovida.com/)

Saludos

---

### Post by salamanca2009 on 2009-06-29
Hola, el mensaje es el siguiente:
[IMG]file:///tmp/moz-screenshot-2.jpg[/IMG][IMG]file:///tmp/moz-screenshot-3.jpg[/IMG][ATTACH]119394[/ATTACH]

---

### Post by RafaelG on 2009-06-29
> **salamanca2009 said:**
> Hola, el mensaje es el siguiente:
[IMG]file:///tmp/moz-screenshot-2.jpg[/IMG][IMG]file:///tmp/moz-screenshot-3.jpg[/IMG][ATTACH]119394[/ATTACH]


Abre el Selector de Sistemas Multimedia con:

```
gstreamer-properties
```revisa que tengas bien configurado las salidas.

---

### Post by salamanca2009 on 2009-06-30
Hola, ya lo he hecho y el problema con Totem y VLC ya no existe.
Bueno siguiendo con el principio de los mensajes, mi tema es que queria poder grabar en GNOMERADIO, en la parte de configuracion me sale ...... (Ver archivo adjunto), no me sale line por ningun lado por lo cual, no puedo grabar.


Alguna idea..........





                          Salu2 .......................... Miguel

---

### Post by moreback on 2009-06-30
¿Y el Grabador de sonidos no te sirve para grabar desde la entrada en línea? Tendrías que configurar las opciones de Sonido para elegir Line como entrada.

---

### Post by RafaelG on 2009-06-30
Hola Salamanca creo que si tienes otras dudas deberias abrir otro Thread aludiendo tu otra consulta ya que se puede confundir la solucion de tu problema con Totem y VLC, recuerda que este Thread puede servir de ayuda para otras personas que puedan presentar el mismo problema por eso te recomiendo abrir otro thread cuando sean otras consultas o dudas. 

Saludos

---

