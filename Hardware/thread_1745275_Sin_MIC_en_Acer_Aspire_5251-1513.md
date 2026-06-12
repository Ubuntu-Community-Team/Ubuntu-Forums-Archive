---
title: "Sin MIC en Acer Aspire 5251-1513"
date: 2011-04-30
forum: Hardware
---

### Post by User21 on 2011-04-30
Estoy usando Ubuntu 11.04, en una laptop Acer Aspire 5251-1513 y tras varios intentos y chequear por los foros de Ubuntu y googlear, no he conseguido hacer funcionar el micrófono, ni el interno que viene con la maquina, ni la entrada para micrófono. Si alguien tiene idea de cómo ayudarme, soy todo ojos y oidos.

La salida de cat /proc/asound/card0/codec#* | grep Codec 
Codec: Realtek ALC272X

La salida de aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC272X Analog [ALC272X Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 1: HDMI [HDA ATI HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

La salida de lspci: 

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]

Cualquier otro dato que necesiten, me hacen saber y lo posteo de inmediato! :)
Gracias desde ya!

---

### Post by granjero on 2011-05-01
yo tuve un tema en el trabajo con una acer... hay que modificar un archivo...

el lunes si no lo pudiste resolver me fijo en la laptop. fue hace como un año y ni me acuerdo el nombre del archivo. creo era uno de la configuración de alsa.

había que agregar unas lineas...

salud!

---

### Post by User21 on 2011-05-01
He editado /etc/modprobe.d/alsa.conf una y otra vez, con los siguientes datos:

options snd-hda-intel model=auto
options snd-hda-intel model=acer
options snd-hda-intel model=acer-aspire
options snd-hda-intel model=acer-dmic 
options snd-hda-intel model=3stack
options snd-hda-intel model=3stack-dig

y chequeado niveles via alsamixer y no he logrado que funcione.

---

### Post by User21 on 2011-05-01
Acabo de hacerlo funcionar asi:
gksudo gedit /etc/modprobe.d/alsa-base.conf
y como última linea agrego:
options snd-hda-intel probe_mask=1

Espero sea la solución definitiva para mi Acer Aspire 5251-1513. Tanto la grabadora de sonido como Skype funcionan apropiadamente. Incluso el micrófono interno!

Reinicio y vuelvo a probar!

---

### Post by User21 on 2011-05-01
JAJAJA, nono! NO funciona otra vez! n_n!

---

### Post by granjero on 2011-05-01
por lo que me acuerdo había que agregar algo asi como una linea que decia 

blablabla laptop profile o algo asi blablabla

segui probando con los backups de los archivos correspondientes. el lunes cuando tenga la acer en mis manos me fijo

salud!

---

### Post by User21 on 2011-05-01
De acuerdo a [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") agregué a /etc/modprobe.d/alsa-base.conf al final:
options snd-hda-intel model=laptop position_fix=1 enable=yes

luego, reinicio alsa con:
sudo alsa force-reload

y sale andando todo. Solo basta con setear los niveles deseados de volumen de micrófono. Al parecer, todo funciona como debe ser!

Esperemos se repita después de los reinicios. n_n 
Gracias por las sugerencias... Espero volver con un [SOLVED]!

---

