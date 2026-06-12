---
title: "problema de audio kubuntu"
date: 2011-03-25
forum: Instalación y Actualización
---

### Post by granmomox on 2011-03-25
resulta que instale kubuntu 10.10 y kedo mudo luego lo formatie pensando que lo instale mal le dije que hiciera las actualizaciones (se demoro un montón)
pero quedo con audio luego instal elos programas que me gustan tales como opera gimp etc 

durante esta semana me salio una actulisacion de flash y se callo el audio 

tengo un asus k52dr(x52d)
con amd turion II x2 de 2.3 
tajeto de video ati radeon mobility hd 5470 1gb tambien se ocupa de del audio 

[http://www.bip.cl/ecommerce/index.php?modulo=busca&id_producto=8464](http://www.bip.cl/ecommerce/index.php?modulo=busca&id_producto=8464)
espero no hacer propaganda pero ese es 

e tratado con actualizar el alza mixer pero sigo igual

seria bueno un poco de ayuda

---

### Post by granmomox on 2011-03-28
actualizo mi situacion re instale linux (formatie) y a los 2 dias se me volvio a desistalar el audio (sin realisar actualisaciones)

si alguien me pudiera guiar en algo se lo agredeceria

---

### Post by RafaelG on 2011-03-29
Granmomox;

Favor podrias indicar que distribucion de Linux estas utilizando en este momento?

Saludos,

---

### Post by granmomox on 2011-03-29
kubuntu 10.10

---

### Post by RafaelG on 2011-03-30
Granmomox,

Antes de haber formatiado (Reinstalar) Linux probaste en instalar solamente ALSA desde el codigo fuente sin necesidad de reinstalar todo Linux. La actualizacion de ALSA no necesariamente resuelve problemas con el kernel. 

Tengo varias consultas: 

Instalaste directamente Kubuntu desde un ISO o lo instalaste desde Ubuntu?,

El problema afecta todo el sistema operativo o solo estan afectados algunos programas y aplicaciones?

Favor podrias ejecutar en un terminal  "**alsamixer**" y verificar si los master se encuentra con nivel?

saludos,

---

### Post by granmomox on 2011-03-30
> **RafaelG said:**
> Granmomox,

1 Antes de haber formatiado (Reinstalar) Linux probaste en instalar solamente ALSA desde el codigo fuente sin necesidad de reinstalar todo Linux. La actualizacion de ALSA no necesariamente resuelve problemas con el kernel. 

Tengo varias consultas: 

2 Instalaste directamente Kubuntu desde un ISO o lo instalaste desde Ubuntu?,

3 El problema afecta todo el sistema operativo o solo estan afectados algunos programas y aplicaciones?

4 Favor podrias ejecutar en un terminal  "**alsamixer**" y verificar si los master se encuentra con nivel?

saludos,

2 queme un cd con el iso oficial

3 afecta a todo el so (en win funca)

4 no soy tan noob eso es lo primero que hice y si tienen el volumen y al max

1 reistale alsa antes con un apt o un repositorio (supongo que a eso te refieres)

una actualisacion durante un momento me arojo un error de kde4-window-decorator PID: 2190 Señal: 11 y kedo con audio de nuevo pero, con la cagada (se actibo el cubo) en el escritorio y interfas grafrica despues se salio solo

---

### Post by RafaelG on 2011-04-01
> **granmomox said:**
> queme un cd con el iso oficial

Granmomox,

Bueno no me quedo muy claro si quemaste un CD Ubuntu o Kubuntu? pero bueno verifiquemos mejor lo que nos interesa. Podrias ejecutar en un terminal los siguientes comandos y despues pegar lo que arroja cada uno de los comandos por favor.

```
sudo aplay -l
``````
find /lib/modules/`uname -r` | grep snd
```

Saludos cordiales,

---

### Post by granmomox on 2011-04-01
queme uno de kubuntu

*** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC259 Analog [ALC259 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Generic [HD-Audio Generic], dispositivo 3: ATI HDMI [ATI HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

y en el otro me sale una lista guigate de casi puros (o puros .ko)

buscas uno en especial o todos?

---

### Post by RafaelG on 2011-04-01
Granmomox;

Prueba con lo siguiente ejecuta desde un terminal el siguiente comando: 
```
sudo nano /etc/modprobe.d/alsa-base.conf
```Al final del file ingresa lo siguiente:
> options snd-hda_intel index=0
options snd-hda_intel index=1Guarda los cambios realizados, cierra y reinicia. Cuentame como te fue?

saludos,

---

