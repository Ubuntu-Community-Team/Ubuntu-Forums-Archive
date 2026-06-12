---
title: "No Se Escuchan mis Altavoces en Ubuntu 10.04"
date: 2010-09-25
forum: Hardware
---

### Post by Sugusana on 2010-09-25
Hola, soy analfabeta informática y me hago un lío con todo. No sé dónde tengo  que poner mi pregunta. He buscado a ver si ya estaba respondida y aunque  sí he visto problemas similares no he conseguido encontrar la  respuesta. :sad:
La pongo aquí y si no es aquí, disculparme porque estoy más perdida que un pulpo en un garage.
Mis altavoces no se oyen. Tengo el ubuntu 10.04, actualizado desde la 9.10. Son altavoces nuevos, porque los viejos ya solo emitían ruidos. Con windows sí se oyen. (Los anteriores se oían pero muy malamente)
Creo que tengo todos los volumenes de todo a tope.
Cuando pongo en la terminal "lspci" me sale todo esto, de lo cual no entiendo ni papa: 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
02:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by RafaelG on 2010-09-27
Sugusana,

Efectivamente este Post no corresponde plantearlo en un Post ya existente con un problema diferente. Si no tienes muy clara la división que utilizamos puedes leer el siguiente post:

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

También te pido que leas las normas que intentamos aplicar en el foro para que tu experiencia en el mismo sea más efectiva:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)


Ahora en referencia al inconceniente con los altavoces de tu computador, podrias revisar con PULSEAUDIO si efectivamente tienes asignado los parlante como salida de tu audio, para poder acceder a pulseaudio solo tienes que ir a **Aplicaciones>sonido y video>Pulseaudio>control de volumen>Output Device** y asignar tus parlantes como salida de audio.

Saludos!

---

### Post by Sugusana on 2010-10-02
Ok. Gracias.
En Aplicaciones -Sonido y vídeo no me sale nada de lo que dices :(

---

### Post by asterix77 on 2010-10-02
Pulse
eaudio no viene integrado en el menú de lucid, para que aparezca primero debes instalarlo. En laterminal debes digitar

#sudo apt-get install pulseaudio

Tras lo cual debes hacer lo comentado en el post anterior.

Puedes verificar también como están tus controles escribiendo en la terminal 
#alsamixer
Y seguir las instrucciones.

Saludos

---

### Post by RafaelG on 2010-10-05
> **Sugusana said:**
> Ok. Gracias.
En Aplicaciones -Sonido y vídeo no me sale nada de lo que dices :(

Sugusana,

Efectivamente como indica Asterix77 PulseAudio no viene por defecto en Lucid que es la version 10.04 por lo que puedes intalarlo  segun lo indicado por Asterix77 o desde los repositorios oficiales de Ubuntu. 

Ahora tambien podriamos manejar mayores antecedentes si desde un terminal ingresas el siguiente codigo y pegas aca lo que arroje:

```
aplay -l
```Saludos!

---

### Post by Carlos C on 2010-10-06
Para que no se cree confusión: Pulse Audio es un servidor de sonido. Si no me equivoco, a partir de Ubuntu 8.10 ya viene instalado por defecto. Lo que debemos instalar, en caso de desearlo, es la aplicación "Control de Volumen de PulseAudio" o "PulseAudio Volume Control".
```
sudo apt-get install pavucontrol
```
Que en el fondo no es más que una interfaz gráfica (GUI). También podemos instalar "Preferencias de PulseAudio":
```
sudo apt-get install paprefs
```
La antigua GUI padevchooser entiendo que se considera obsoleta y no es necesario utilizarla.

Saludos!

---

