---
title: "Consulta sobre Audio en Ubuntu 9.10"
date: 2010-03-07
forum: Hardware
---

### Post by xNeCrOx on 2010-03-07
Hola, buenas! les cuento.. tengo un notebook Acer Aspire 5738Z cuando instalé ubuntu 9.10 no tenía audio 5.1 y solo me sonaban dos parlantes, solucione eso recorriendo una infinidad de foros.. pero ahora surge otro problema, es que mientras suena por los parlantes del subwoofer al mismo tiempo suenan en los parlantes stereos del notebook... hay alguna forma de que al conectar el subwoofer deje de sonar los parlantes del notebook?....

Si necesitan alguna información extra porfa me dicen... 

Slds

---

### Post by Carlos C on 2010-03-08
Bueno, lo primero: publica tus consultas en el subforo que corresponde. Hay un thread publicado que te puede aclarar tus dudas:

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

Lo segundo es que necesitamos saber el modelo específico de tu tarjeta de sonido. Escribe en el terminal:
```
lspci|grep audio
```
Además, si modificaste la configuración del sistema debes decirnos exactamente lo que cambiaste. Seguramente editaste tu archivo etc/modprobe.d/alsa-base.conf, pero necesitamos saber qué has cambiado.

Saludos.

---

### Post by xNeCrOx on 2010-03-09
> **Carlos C said:**
> Bueno, lo primero: publica tus consultas en el subforo que corresponde. Hay un thread publicado que te puede aclarar tus dudas:

[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

Lo segundo es que necesitamos saber el modelo específico de tu tarjeta de sonido. Escribe en el terminal:
```
lspci|grep audio
```

Además, si modificaste la configuración del sistema debes decirnos exactamente lo que cambiaste. Seguramente editaste tu archivo etc/modprobe.d/alsa-base.conf, pero necesitamos saber qué has cambiado.

Saludos.

1) Con el comando no aparece nada. Pero con el alsamixer te puedo decir que tengo.

 [B]Card: HDA Intel                                                                                            
 Chip: Intel G45 DEVCTG[/B] 

2) Lo que modifique fue agregar al alsa-base.conf esta línea en options.

**options snd-hda-intel model=3stack-6ch**

Luego, simplemente reinicie, abri un terminal. Ingrese al alsamixer cambie la cantidad de canal de 2Ch a 6Ch, reinicie el pulseaudio... hize una prueba de sonido y me funcionó.

Pero ahora no solo suenan mis subwoofer 5.1, sino que al mismo tiempo también los stereos del laptop cosa que no deberia, siendo que tengo conectado el subwoofer.

Espero q me puedan ayudar.

Saludos y gracias

---

### Post by Carlos C on 2010-03-09
Hola. Te sugiero que instales [huuf]("http://ubuntuforums.org/showthread.php?t=1410952") y que nos copies lo que te reporta en "Audio".

Saludos.

---

### Post by CdK1 on 2010-03-10
El comando es:

Caturra:/# lspci -vv | grep Audio

Pega la salida acá...

---

### Post by xNeCrOx on 2010-03-11
> **CdK1 said:**
> El comando es:

Caturra:/# lspci -vv | grep Audio

Pega la salida acá...


cristian@skynet:~$ lspci -vv | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


Eso me sale.....

---

### Post by Carlos C on 2010-03-12
tengo la impresión de que esta opción:
```
options snd-hda-intel model=3stack-6ch
```

no es la que necesita esa tarjeta. Yo cambiaría "3stack-6ch" por otra configuración. Corre el comando "aplay -l" en el terminal y busca el modelo de tu tarjeta aquí:

[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

Así vas a poder escoger otra opción que funcione como quieres.

---

### Post by xNeCrOx on 2010-03-24
> **Carlos C said:**
> tengo la impresión de que esta opción:
```
options snd-hda-intel model=3stack-6ch
```

no es la que necesita esa tarjeta. Yo cambiaría "3stack-6ch" por otra configuración. Corre el comando "aplay -l" en el terminal y busca el modelo de tu tarjeta aquí:

[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

Así vas a poder escoger otra opción que funcione como quieres.

Hola, disculpa por la tardanza en responder... Veré lo que me señalas cualquier cosa estaré comentando ok? saludos

---

### Post by CdK1 on 2010-03-24
Tengo casi la misma tarjeta, uso alsa y no tengo dramas...

---

### Post by xNeCrOx on 2010-03-24
> **xNeCrOx said:**
> Hola, disculpa por la tardanza en responder... Veré lo que me señalas cualquier cosa estaré comentando ok? saludos

Bueno primeramente cuando hago el comando aplay -l me aparece esto

> cristian@skynet:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC888 Analog [ALC888 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 3: INTEL HDMI [INTEL HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


Buscando en la lista probe los que podrian funcionarme.. acer, auto y acer-aspire pero al reiniciar no tengo audio 5.1, cuando pongo el 3stack-6ch obtengo sonido 5.1, lamentablemente los stereos del notebook siguen sonando siendo que al conectar el subwoofer en el notebook (son 3 cables) este debería dejar de sonar (así sucede en winbugs :S).

La verdad no se que hacer, si bien es un tema menor. Me gustaría solucionarlo.

Saludos

---

### Post by Carlos C on 2010-03-24
Es extraño porque Cdk1 tiene la misma tarjeta y no hace ningún cambio a su configuración para que funcione correctamente.

---

### Post by xNeCrOx on 2010-03-25
> **Carlos C said:**
> Es extraño porque Cdk1 tiene la misma tarjeta y no hace ningún cambio a su configuración para que funcione correctamente.


No tiene LA MISMA, dice el que tiene una parecida. El punto esta en que si pongo la configuración auto (que debería tomarme la config. de la bios), acer, o acer-aspire. Pierdo el sonido 5.1 y solo se escuchan los stereos del notebook, y dos parlantes del subwoofer.

Si cambio a 3stack-6ch el sonido 5.1 funciona pero en el audio me sale como Analog Output, si pongo Analog 5.1 etc.. no me suenan todos los parlantes... a todo esto, tengo que cambiar en alsamixer de 2ch a 6ch cuando uso la opción de 3stack-6ch.

Se que es un tema menor, pues el sonido 5.1 con esa configuración está. Pero no debería seguir sonando los parlantes del notebook, en winbugs no me sucede eso pues probe... si conecto los 3 cables al notebook para el subwoofer, los parlantes propios del notebook deja de sonar y solo suenan los 5.1 del subwoofer...

A ver si luego pilló la solución

---

### Post by Carlos C on 2010-03-29
Veamos si algo de esto te sirve:

[http://ubuntuforums.org/showthread.php?t=1101993](http://ubuntuforums.org/showthread.php?t=1101993)

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Saludos.

---

