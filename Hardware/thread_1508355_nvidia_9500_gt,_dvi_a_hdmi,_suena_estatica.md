---
title: "nvidia 9500 gt, dvi a hdmi, suena estatica"
date: 2010-06-12
forum: Hardware
---

### Post by xpipekunx on 2010-06-12
holas, ojala me ayuden
tengo mi pc con una placa de video nvidi 9500 gt, que tiene salida dvi, la cual conecto a mi lcd por medio de hdmi, la placa tambien tranasmite el sonido, lo malo es que lo unico que suena es estatica (muy fuerte y molesta por demas) y ya no se que hacer, alguna idea?

comando: aplay -l

**** Lista de PLAYBACK dispositivos hardware ****
Home directory /home/pipe not ours.
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: VT1708S Analog [VT1708S Analog]
  Subdispositivos: 2/2
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
tarjeta 0: NVidia [HDA NVidia], dispositivo 1: VT1708S Digital [VT1708S Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

si necesitan algun otro comando me avisan, ojla me ayuden

---

### Post by asterix77 on 2010-06-14
No comprendo muy bien tu problema:

Si pretendes sacar el sonido por el mismo cable, no se puede hasta donde yo sé, ya que si bien es cierto HDMI transmite tanto video como audio, DVI no lo hace ya que solo transmite video. La única forma sería entonces, HDMI en ambos extremos; cualquier otra forma, es necesario un cable alternativo.

Ahora si el sonido lo estás sacando aparte, eso es otra cosa. Por favor entrega más detalle de como estás haciendo tu conexión.

Saludos

---

### Post by xpipekunx on 2010-06-20
estuve averiguando y avance un poco, claro por defecto el puerto dvi no trasnmite sonido, ahora bien las tarjetas nvidia de esta serie (y otras) tiene una pequeña entrada de audio 2 pines (la cual ya encontre en mi placa :)) que sirve para que le conectes el audio de tu pc y la tecnologia nvidia hace el resto, la mayoria de las placas madre hoy en dia traen un puerto para audio opcional, extra o ponele como sea, segun lo que averigue, hay que conectar este puerto y deveria sonar por hdmi por dvi, suena raro pero voy a probar y aviso, el problema es donde consigo un cable de 2 pines XD

pd: explotara? ¬¬

---

### Post by xpipekunx on 2010-07-06
aplaudanme, felicitenme, jajajaja (mentira) aunque no hay mucha info sobre el tema en ni una parte (ni en la pagina de nvidia) me hice un cable parecido a este
[IMG]http://www.noticias3d.com/articulos/200803/zotac_9600gt/imagenes/cables3.jpg[/IMG]

claro el mio es mas feito y artesanal (pero funciona) la coneccion plana va a el conector sdpif de su placa madre respectivamente al puerto "gnd" y al "sdpif" (si es que la tiene, ver manueal de su propia placa madre) y la conexion cuadrada blanca va a la tarjeta nvidia y como arte de magia todo funcionara, pongan esta salida por defecto, habiliten sdpif y prueben, por lo menos a mi me funciono

[IMG]http://img340.imageshack.us/img340/3640/px8600gthdmiinstallspdi.jpg[/IMG]

lo dejo aqui para futuras referencias, no creo que para todos sea el mismo conector ni la misma habilitacion de software, pero de que funciona funciona y es bastante simple por lo demas

---

