---
title: "Sintonizadora lg ltt-200"
date: 2008-07-14
forum: Hardware
---

### Post by FlyerDie on 2008-07-14
Estimados,
Poseo una sintonizadora/capturadora LG LTT-200 que en la maquina que tenia window$ funcionaba perfecto tanto sintonizando como capturando.

Ahora recupere esa plaquita y la puse en una maquina que tengo Ubuntu 8.04, pero no tengo ni idea como hacerla levantar tanto para sintonizar como para capturar ;)

El chip que trae es un Philips SAA7135HL...(saa7134)

Quien pueda darme una mano tendra mi total agradecimiento:lolflag::lolflag:

---

### Post by Mauro22 on 2008-07-14
Abri la consola y hace:

sudo rmmod saa7134_alsa saa7134_dvb saa7134

No importa si te da error

sudo modprobe saa7134 card=3

Si tenes un programa para ver tv, como el tvtime, ya deberia funcionar.

---

### Post by FlyerDie on 2008-07-14
> **Mauro22 said:**
> Abri la consola y hace:

sudo rmmod saa7134_alsa saa7134_dvb saa7134

No importa si te da error

sudo modprobe saa7134 card=3

Si tenes un programa para ver tv, como el tvtime, ya deberia funcionar.

wow..sinceramente no esperaba una respuesta tan precisa :KS
Ni bien llego a casa hago la prueba y te comento..
Mil gracias!

---

### Post by FlyerDie on 2008-07-14
bueno, he ejecutado como me dijiste y obtuve el siguiente error:

```
$ sudo modprobe saa7134 card=3
WARNING: Error inserting video_buf (/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/video-buf.ko): Invalid module format
WARNING: Error inserting video_buf (/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/video-buf.ko): Invalid module format

```
:(

ahora si tiro:

```
$sudo lshw
```

me da

     ```
*-multimedia
                description: Multimedia controller
                product: **SAA7133/SAA7135 Video Broadcast Decoder**
                vendor: **Philips Semiconductors**
                physical id: 9
                bus info: pci@0000:01:09.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=32 maxlatency=38 mingnt=15 module=saa7134

```

---

### Post by faktorqm on 2008-07-15
Antes de tocar los modulos, proba el tvtime o alguno para ver tv. Yo tengo la misma placa y no tuve que tocar absolutamente nada, hasta el sonido me reconoce. Ahora justo la saque por que queria ver de venderla a ver si me actualizo un poco y ya que era compatible con ubuntu no la queria vender xD Salu2!!

---

### Post by FlyerDie on 2008-07-15
> **faktorqm said:**
> Antes de tocar los modulos, proba el tvtime o alguno para ver tv. Yo tengo la misma placa y no tuve que tocar absolutamente nada, hasta el sonido me reconoce. Ahora justo la saque por que queria ver de venderla a ver si me actualizo un poco y ya que era compatible con ubuntu no la queria vender xD Salu2!!

Tenes la misma placa LG LTT-200 o tenes una placa con el mismo chip?
En linux no me funciono nunca, y justo habia probado con el tvtime antes de poner el thread...ya que me las veia negras, ya que veia que el hard era detectado haciendo un **lshw** pero despues no pasaba naranja.

---

### Post by Mauro22 on 2008-07-15
Tu ubuntu es de 64 bits?

---

### Post by FlyerDie on 2008-07-15
> **Mauro22 said:**
> Tu ubuntu es de 64 bits?

nop...es el de 32, en otra maquina SI tengo pensado poner el de 64 bits, pero no tiene capturadora.

---

### Post by FlyerDie on 2008-07-16
Creo que estoy destinado al fracaso con esta placa....:(:(

Cual recomiendan...marca y modelo, que funcione sin dar vueltas? la kozumi? la encore? que modelos?

Yo la quiero para ver algo de TV y capturar...nada profesional, pero si algo en 640*480 ;)

como siempre GRACIAS!!!

---

### Post by Mauro22 on 2008-07-16
La tuya dice saa7133/7135 :s

La mia dice saa7134...


Probaste cargar los modulos pero con tu numeros? o sea 7133 y 7135 ??

---

### Post by FlyerDie on 2008-07-16
> **Mauro22 said:**
> La tuya dice saa7133/7135 :s

La mia dice saa7134...


Probaste cargar los modulos pero con tu numeros? o sea 7133 y 7135 ??

los unicos que me aparecen son los siguientes:

```
$ sudo modprobe saa
saa5246a         saa7111          saa7134-alsa     saa7185
saa5249          saa7114          saa7134-dvb      saa7191
saa6588          saa7115          saa7134-empress  
saa6752hs        saa7127          saa7146          
saa7110          saa7134          saa7146_vv       

```

---

### Post by alejar on 2009-06-09
hola, vi que tenes un ltt-200. yo tambien, y perdi el cd de instalacion, vos lo tenes?

en caso afirmativo podrias darme una copia del lmismo.

te lo agradezco infinitamente

alejar.

> **FlyerDie said:**
> Estimados,
Poseo una sintonizadora/capturadora LG LTT-200 que en la maquina que tenia window$ funcionaba perfecto tanto sintonizando como capturando.

Ahora recupere esa plaquita y la puse en una maquina que tengo Ubuntu 8.04, pero no tengo ni idea como hacerla levantar tanto para sintonizar como para capturar ;)

El chip que trae es un Philips SAA7135HL...(saa7134)

Quien pueda darme una mano tendra mi total agradecimiento:lolflag::lolflag:

---

### Post by dantiags on 2010-02-18
Buenas!!

Soy nuevo y no estoy pudiendo instalar la LG LTT-200

Pudieron avanzar sobre el tema?

Cualquier ayuda es bienvenida!
:)

---

### Post by dantiags on 2010-02-19
Bueno al que le sirva este post me soluciono el problema!!

[http://mstr.ueuo.com/saa/instalar.php?id=saa7134&c=78&i=b](http://mstr.ueuo.com/saa/instalar.php?id=saa7134&c=78&i=b)

---

