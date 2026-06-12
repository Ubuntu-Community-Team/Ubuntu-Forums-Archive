---
title: "Presentacion y problemas"
date: 2009-06-19
forum: Hardware
---

### Post by juampi69 on 2009-06-19
Buenas, soy Juan Pablo, les cuento rapido, tengo una pentiumIV 512 de ram y 160Gb (la placa de sonido es intel IC_H5 y el chip es Realtek ALC202, al menos eso me aparecio buscando x la maquina) tenia todo en windows y varias veces instale ubuntu (dandole 2.5, 5 y 11Gb) en esa ultima instalacion paso q no me reproducia video (ya abilite los extras) me abria el programa y cuando pasaba el primer microsegundo se cerraba el programa (cualquiera q usara), si iba a Windows, sucedia q me decia q tenia un hardware nuevo (no me reconocia la placa de sonido) pero linux si.
   Me canse, formatie e instale windows en 20gb y el resto para ubuntu, sucede q ahora luego de hacer todas las primeras cosas q se recomiendan, no me anda el sonido ni puedo poner tildes, ya probe todas las opciones de teclados les pongo la prueba (´e `e) antes no pod´ia poner ni @ ni -_ y con lo q es sonido no encontre ningun foro q tubiera el mismo chip


   Desde ya muchas gracias
     Buenas vibras y dulces humos...!!!

---

### Post by Mauro22 on 2009-06-19
Hola!!


Postea la salida de:


lspci 



Ubuntu de 32 o 64 bits?? que version, 9.04 8.10 ?? 


saludos!

---

### Post by juampi69 on 2009-06-19
ubuntu 9.04, lo de los 32 o 64 no se (demas esta decir q soy ultra nuevo) lo q aprendi lo hice de leer foros y ponerlo en practica
si me decis donde lo busco ya t respondo

---

### Post by Mauro22 on 2009-06-19
Anda a Aplicaciones -> Accesorios -> Terminal

pone:

```
uname -a
```

y pega el resultado aca


despues hace:

```
lspci
```

y pegalo aca tambien.

---

### Post by juampi69 on 2009-06-20
2.6.28-13generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 200 9 i686 GNU/LINUX


y el segundo q me pusiste me pone un choclazo q necesitas de ahi?
tengo q ponerte todo?
y con lo del teclado?

---

### Post by alfplayer on 2009-06-20
Qué teclado elegiste en la instalación de Ubuntu? (yo con Ubuntu 9.04 lo puedo ver en: -> menú Sistema -> Preferencias -> Teclado -> pestaña Distribuciones). Yo estoy usando el modelo de teclado PC genérico 105 teclas (intl), y distribución España.

---

### Post by juampi69 on 2009-06-21
PC genérico 105 teclas (intl), latino con y sin letras muertas y tambien probe español y nada, les muestro (´o `o)

---

### Post by alfplayer on 2009-06-21
Lo del teclado puede ser este problema [https://bugs.launchpad.net/ubuntu/+bug/354466](https://bugs.launchpad.net/ubuntu/+bug/354466) ? En mi comentario (el segundo) se explica como resolverlo, que es deshabilitando el soporte para caracteres complejos (yo había tenido que hablitarlo porque tenía problemas con VirtualBox).

---

### Post by juampi69 on 2009-06-21
Lo tenía deshabilitado, lo acabo de habilitar, reinicio y les cuento

---

### Post by juampi69 on 2009-06-21
Listo, muchas gracias, lo habilité, no reinicié pero me funciona igual!!!!!!
   Ahora sólo queda el temita del sonido, pero como dirían los gallegos "vamos a por él!!!!"


Buenas vibras!!!

---

### Post by juampi69 on 2009-06-23
Mauro decime como puedo conseguir los datos q necesitas
o alguien q me diga si bajandome los driver funcionaria...
Porfaaa!!!

---

### Post by staar on 2009-06-23
los datos que necesitamos los obtenés corriendo los comandos que te pasó mauro en una Terminal (Aplicaciones > Accesorios > Terminal)

para resolver problemas de sonido, lo primero, aunque suene tonto (muchas veces es la causa), es verificar que nada esté con volumen 0 (mute), para eso ir al control de volumen, y subirle el volumen a todos los canales (activar los canales que están ocultos, desde las preferencias)

saludos

---

### Post by juampi69 on 2009-06-23
eso ya lo hice y no está ninguno en mute, los habilité todos
pero en lo de la terminal ya lo hice y la segunda opción que me da me sale una cantidad de texto impresionante como lo copio para ponérselos aquí? gracias por las respuetas

---

### Post by staar on 2009-06-23
bien...

corré ```
lspci
``` y pegá la salida acá, son varias líneas, pero no un choclo impresionante, a menos que tengas la motherboard más completa y extraña que exista, no vas a tener problemas en pegarla acá (es recomendado para una mejor lectura pegarlo como código o como quote)

saludos

---

### Post by juampi69 on 2009-06-23
les copio lo que me pone de multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) A  C'97 Audio Controller (rev 02)


espero que sirva

---

### Post by staar on 2009-06-23
bien, eso era lo que necesitaba, ahora posteá la salida de ```
aplay -l
```

saludos

---

### Post by juampi69 on 2009-06-23
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)

```

Ahí fue todo, espero sirva

---

### Post by juampi69 on 2009-06-23
```
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: ICH5 [Intel ICH5], dispositivo 0: Intel ICH [Intel ICH5]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: ICH5 [Intel ICH5], dispositivo 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

---

### Post by staar on 2009-06-23
bien, la tarjeta es reconocida, ahora posteá la salida de ```
find /lib/modules/`uname -r` | grep snd
``` para ver si se cargaron los módulos...

saludos

---

### Post by juampi69 on 2009-06-23
```
/lib/modules/2.6.28-13-generic/kernel/sound/core/snd-timer.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/snd.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/oss/snd-pcm-oss.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/2.6.28-13-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/2.6.28-13-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/2.6.28-13-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/2.6.28-13-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/2.6.28-13-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/2.6.28-13-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/2.6.28-13-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/2.6.28-13-generic/kernel/sound/usb/snd-usb-lib.ko
/lib/modules/2.6.28-13-generic/kernel/sound/oss/msnd_pinnacle.ko
/lib/modules/2.6.28-13-generic/kernel/sound/oss/msnd.ko
/lib/modules/2.6.28-13-generic/kernel/sound/oss/msnd_classic.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/2.6.28-13-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/oxygen/snd-hifier.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-sis7019.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-adlib.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/sb/snd-es968.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-es18xx.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-dt019x.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/cs423x/snd-cs4232.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-sc6000.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-sscape.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-azt2320.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-als100.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/2.6.28-13-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/2.6.28-13-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/2.6.28-13-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/2.6.28-13-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/2.6.28-13-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/2.6.28-13-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/2.6.28-13-generic/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/2.6.28-13-generic/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/2.6.28-13-generic/kernel/sound/i2c/snd-cs8427.ko

```
Aprendí a copiar el code desde la terminal, gracias x la ayuda online:P:D

---

### Post by juampi69 on 2009-06-23
y, cargaron????!! me imagino q debe ser algo d todo eso!!!

---

### Post by alfplayer on 2009-06-23
Para ver si se cargaron los módulos de sonido lo que hay que ejecutar es:
```
lsmod | grep snd
```

---

### Post by juampi69 on 2009-06-23
```
snd_intel8x0           37532  5 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  5 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  20 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm

```


 ahora????!!!!

---

### Post by alfplayer on 2009-06-23
Con el comando "alsamixer" o "alsamixer -c 1" (según el que sea para el sonido integrado, no el del audio de la sintonizadora) hay que setear todo al 100 % y que nada esté en mudo (que no esté en MM). Puede ser que haya algunos que no se puedan modificar. Después se puede ejecutar "alsactl store" o "alsactl store 1" (igual a alsamixer: usar el 1 si el integrado está como dispositivo 1).

---

### Post by juampi69 on 2009-06-23
Hasta ahí había llegado (no sé como) y tengo el "3D control Switch" en cero y no pude moverlo hasta ahora...

Seguí viendo y tengo otros sin volúmen (mic boost, mic selec, IEC958, mono out y external) pero ni con la flecha para arriba, ni con ninguna tecla me ha dejado modificarlos

---

### Post by alfplayer on 2009-06-23
Probá con esto:
```
sudo adduser tu_nombre_de_usuario audio
```reemplazando tu_nombre_de_usuario por lo que corresponda y reiniciando Ubuntu.

---

### Post by juampi69 on 2009-06-23
cuando voy al alsctl me aparece "alsactl: save_state:1541: Cannot open /var/lib/alsa/asound.state for writing: Permission denied"
y cuando marco el otro me aparece lo mismo

---

### Post by juampi69 on 2009-06-23
estoy haciendo eso play, gracias, ahora les digo

---

### Post by alfplayer on 2009-06-23
Esos se ejecutan como root después de dejar todo bien con alsamixer, para ejecutar como root: sudo alsactl store y sudo alsactl store 1 (son para grabar lo que se cambia con alsamixer en el dispositivo 0 y 1 respectivamente)

---

### Post by juampi69 on 2009-06-23
puse lo q dijiste, me dijo q se creo el ususario para sonido, reinicié, entré al alsamixer y tampoco me dejó hacer nada

---

### Post by alfplayer on 2009-06-23
Cómo que no deja hacer nada? No se puede cambiar ninguna barra con alsamixer? El audio integrado es el dispositivo 0 o el 1? (el nombre del dispositivo aparece arriba a la izquierda en alsamixer)

---

### Post by juampi69 on 2009-06-23
los que si tienen sonido me los deja subir y bajar bien
El q dice arriba a la izquierda es el chip realtek ALC202 rev 0

---

### Post by alfplayer on 2009-06-23
Te aviso que no se si voy a poder resolver esto.

En Sistema -> Preferencias -> Sonido posteá cuáles son los cinco valores que están configurados. Si hay algunos con Autodetectar probá si hay sonido cambiándolos a PulseAudio Sound Server.

---

### Post by juampi69 on 2009-06-23
A todos los que estaban en automático los cambié a PulseAudio Sound Server y no tengo sonido tampoco

:( Q será???!!! xq como expliqué antes las veces q instalé ubuntu con menos espacio me funcionó bárbaro...!!!

---

### Post by alfplayer on 2009-06-23
El sonido es un gran problema en Jaunty.

No hiciste lo que dije en el post anterior: decime cuáles son los cinco valores en Sistema -> Preferencias -> Sonido

Otra pregunta: Funciona/funcionó la salida de audio en windows? Seguro que los parlantes/auriculares funcionan y están bien conectados en la salida que corresponde?

Ejecutá lo siguiente:
```
wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && bash alsa-info.sh
```Cuando pregunta "Do you want to run this script? [y/n]" apretá la tecla Y.

Copiá y pegá para que veamos la salida de todo el comando (es largo).

---

### Post by juampi69 on 2009-06-23
Eventos de sonido:
   reproducción de sonido
Música y peliculas:
   reproducción de sonido: Auto
Conferencia de sonido:
   reproducción de sonido: Auto
   captura de sonido: ALSA, advance linux soun architecture
Pistas predeterminadas del mezclador: auto
   dispositivo: Capture: Intel ICH5 - Intel ICH5 Pulse audio mixer


perdón, me faltaba eso

---

### Post by juampi69 on 2009-06-23
```
Your ALSA information is located at [http://www.alsa-project.org/db/?f=6ad4bbe39a7ecbe71fe8b525f11e0cb4d242e5e8](http://www.alsa-project.org/db/?f=6ad4bbe39a7ecbe71fe8b525f11e0cb4d242e5e8)

Please inform the person helping you.
```

esto solo me puso, antes de la pegunta me había escrito otras cosas

---

### Post by alfplayer on 2009-06-23
Quedó un poco mezclado. Voy a adivinar un poco:

De arriba a abajo: Auto, Auto, Auto, ALSA, advanced linux sound architecture, Intel ICH5 - Intel ICH5 Pulse audio mixer
Si es asi mejor para probar dejá los primeros 3 en PulseAudio Sound Server y los otros como están.

Está bien, no era largo. En ese link que me mandaste está la información que quería. Lo voy a revisar a ver si encuento un problema.

---

### Post by juampi69 on 2009-06-23
Ya cambié los tres primeros como dijiste

---

### Post by alfplayer on 2009-06-23
Otra cosa para probar: probaste o podés probar sacando la sintonizadora?

No respondiste esto:
> Funciona/funcionó la salida de audio en windows? Seguro que los parlantes/auriculares funcionan y están bien conectados en la salida que corresponde?

No veo problemas con la salida de alsa-info.sh

---

### Post by juampi69 on 2009-06-23
el tema es el siguiente, primero funcionaba en ambos, después funcionaba sólo en linux y window$ me dice q hay un hardware nuevo y me pide q instale el sonido y ahora q no me funca en ninguno de los dos (en W me pide q instale el hard)
   Los parlantes están bien enchufados y andaba todo bien, si los enchufo en las otras entradas y hace ruidos, zumbidos y demás
la sintonizadora encore decís? q la desconecte del mother? antes me funcionó bien el sonido, eso es lo q me llama la atención

---

### Post by staar on 2009-06-23
haberlo dicho antes, si no funciona en otro SO es un problema de hardware probablemente, no de ubuntu, tocaste algo en la BIOS? con el livecd de ubuntu u otra distro anda?

saludos

---

### Post by juampi69 on 2009-06-24
habíamos tocado la bios pero el tema del booteo nomás, lo del sonido no tocamos nada, lo del live cd no probé

---

### Post by alfplayer on 2009-06-24
Instalaste la 9.04 o es actualizada de una versión más vieja?

Qué pasó para que deje de funcionar en windows y en linux?
> window$ me dice q hay un hardware nuevoCuando aparece este mensaje hay que instalar los drivers.

Mostrá la salida del comando
```
grep audio /etc/group
```Cómo estás probando si funciona el sonido? Con un MP3? Con un video de YouTube? Cómo?

De ahora en adelante, lo mejor para probar es con los primeros 3 botones "Probar" en Sistema -> Preferencias -> Sonido

> la sintonizadora encore decís? q la desconecte del mother?Sí, eso quiero decir. Sacar del mother la sintonizadora de tv (yo no se la marca).

Sería bueno para encontrar el problema tratar de hacerla funcionar en windows.

---

### Post by juampi69 on 2009-06-24
```
audio:x:29:pulse,juampi
```
Ahí va lo q sale con lo q me dijiste, ahora pruebo con el live cd
no encuentro los drivers online, y nop se donde están los cds :(

---

### Post by juampi69 on 2009-06-24
Cuando puse el live cd no me arrancó, encima instalé el Vlc Player y volvieron a cerrarse los programas de video cada vez q intento ver un video. Acabo de desinstalar el vcl again y no se arregló (q nabo, quería ver un video, pero para q lo instalé si no tengo sonido...)

---

### Post by juampi69 on 2009-06-25
Alguna idea???!!!

---

### Post by staar on 2009-06-25
si no anda ni en el livecd, ni en windos, ni en ubuntu, creo que estaríamos ante un problema de hardware, es lo más lógico que se me ocurre...

algo que no se si hiciste, corriste un alsaconf? ```
sudo alsaconf
```

saludos

---

### Post by juampi69 on 2009-06-26
me sale "command not found"

---

### Post by staar on 2009-06-26
aaarrgh, estas son las cosas que no me gustan de ubuntu, me acabo de enterar que alsaconf no existe en ubuntu, cosa rara che...

bueno, igual era el último intento de mi parte, si la placa no te funciona en ningún SO, lo más probable es que tengas un problema de hardware, lo siento...

saludos

---

### Post by juampi69 on 2009-07-15
Holas, les cuento q hoy conseguí los drivers del mother (xq me lo cambiaron hace unos meses y no tenía nada) vamos a ver q puedo hacer...
   El archivo dice intel8x0-alsa-1.0.1.sh
me sirve este o me dio cualquiera?xq no sabía él si me servía para ubuntu, no sabe de linux 
   Me dijo q tengo un mother "intel865 3vhc", él bajó el driver de la página de intel, yo me metí y nunca lo pude ver, no sé de donde lo sacó.

   Espero su respuesta, y si pueden explíquenme como lo hago!!!!

---

### Post by staar on 2009-07-15
??? no entendí nada, quién es 'él'?

eso que bajaste supongo es un script, y tiene que ver con alsa (el sistema de sonido), de donde lo bajaste? por las dudas, no lo corras...

te pareceré terco, pero te repito que si no te anda en ninguno de los dos SO, lo más probable es que sea un tema de hardware, y que no lo puedas arreglar cambiando un driver...

saludos

---

### Post by juampi69 on 2009-07-15
Perdón, cuando digo él, me refiero al tipo q tiene la casa de computación, y el tema q contaba antes es xq tenía un pentiumIV y no sé q se le c**ó y este chango me puso otro mother empeorándole la placa de video a onboard (antes tenía una gforce)no tiene pci para la placa de video, por eso no tenía los drivers del mother.
   Lo q no entiendo es como pùdo ser q las primeras veces q lo instale funcionaba todo, y nunca toqué nada del hard, sólo cuando formatié!!!

---

### Post by Soushiro on 2009-07-27
Podrian explicar un poco mejor el problema, para ver si es posible ayudar.

---

