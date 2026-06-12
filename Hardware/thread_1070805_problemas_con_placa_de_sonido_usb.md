---
title: "problemas con placa de sonido usb"
date: 2009-02-15
forum: Hardware
---

### Post by sirkurt on 2009-02-15
hola soy nuevo en todo esto de ubuntu y tengo un problema.
en mi maquina uso ademas de la placa de sonido incorporada, una placa usb behringer u-contro uca202.
el problema es con esta placa solamente en algunas aplicaciones no tengo sonido y en otras se escucha mal, por ejemplo  ala hora de reproducir video, musica me pasa esto.

saludos

---

### Post by Hei Ku on 2009-02-15
Postea el resultado del comando lsusb. Que sistema de sonido usas? ALSA, OSS, etc?

---

### Post by sirkurt on 2009-02-15
Bus 002 Device 003: ID 0e8f:0003  
Bus 002 Device 002: ID 08bb:2902 Texas Instruments Japan 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

ese es el resultado del comando tal cual me aparecia, con respecto al sistema de sonido es el ALSA el que podia usar para esa placa con la placa integrada uso OSS pero este sistema no esta habilitado para la placa usb

---

### Post by Hei Ku on 2009-02-15
Poné el resultado de:

cat /proc/asound/cards


Justamente hay una explicación sobre configuracion de estas placas, justo con ese modelo en [https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)
Tiene bastantes vueltas, pero vamos de a poco.

En principio la placa te anda, pero no con todos los programas. Es eso, no?

---

### Post by sirkurt on 2009-02-15
0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdbf78000 irq 22
 1 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:02.0-3, full s

ahi esta el resultado XD

---

### Post by Hei Ku on 2009-02-15
Siguiendo con el tutorial que te pasé, postea el contenido del archivo /etc/modprobe.d/alsa-base
Vamos a tener que modificarlo, probablemente.

---

### Post by sirkurt on 2009-02-24
disculpa por colgarme en este tema, lo que pasa es que pense que no iva a tener que usar mas esta placa asi que le dedique atencion a otras cosas.

Pero soy musico y uso esta placa para grabar mis composiciones y los temas de mi banda. Entonces voy a tener que tratar de solucionarlo porque me parece que se viene una mini secion de grabacion con la banda.

bueno en fin ahi te va el contenido completo del archivo que me pediste 

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

---

