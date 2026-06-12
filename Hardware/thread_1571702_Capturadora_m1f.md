---
title: "Capturadora m1f"
date: 2010-09-10
forum: Hardware
---

### Post by ishared on 2010-09-10
Hola compañeros, recien salido del horno tengo mi primer distribucion de linux en mi PC :D (Ubuntu ovbio :P)
Todo va ien meno mi capturadora de tv, una compro m1f VideoMate.
Como puedo hacer para instalar los driver que solo vienen para windows y que programa utilizo para ver la tv y grabar.

Muchas gracias! (Soy re bicho raro en linux :roll:)

---

### Post by juancarlospaco on 2010-09-10
Programas para TV:
TVTime
XawTV

Los controladores probablemente ya los tiene, asumo que es PCI *(no USB)*,
Aplicaciones--->Accesorios--->Terminal, copia, pega y dale Enter:

lspci | grep ideo

pega aca lo que te sale de ese comando.

---

### Post by ishared on 2010-09-10
Exacto, la placa es interna y se conecta en el pci express.

¿Con esos programas (XawTv y tvtime) podre grabar la tv sin ningun problema con los formatos que grababa con el soft original?
¿Me debo despedir del control remoto no?

Y ultima, hay un programa de windows que lo nesecito se llama "xilisoft video converter" ¿lo podre instalar con el wine u otro emulador?

Muchas Gracias, ahora me fijo lo del terminal ):P

---

### Post by guillermolisi on 2010-09-10
> **ishared said:**
> 
Y ultima, hay un programa de windows que lo nesecito se llama "xilisoft video converter" ¿lo podre instalar con el wine u otro emulador?

Muchas Gracias, ahora me fijo lo del terminal ):P
Fijate en la base de aplicaciones de WineHQ para ver si figura y con grado de compatibilidad. Que no figure indica solamente que aun no hubo pruebas de instalacion y uso, por lo menos que hayan registrado su experiencia.

---

### Post by ishared on 2010-09-10
Chicos les dejo el mensaje que me salio:


>  Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)


---

### Post by juancarlospaco on 2010-09-11
Si con ese chip anda, aunque debo decir que no es de lo mejorcito.

El control remoto creo que no funciona el de la placa, 
pero se puede instalar uno en el puerto Serie DB9, se compra aparte,
fijate el proyecto LIRC.

Convertidores de formato de Video hay un monton, te sugiero usar uno nativo.

---

### Post by ishared on 2010-09-11
Mira eh probado de todo para hacer funcionar la sintonizadora y no eh podido.
Realmente es muy importante que funcione por eso te pregunto ¿Si instalo VMware y creo una maquina virtual con windows me reconocerá la sintonizadora?
):P

Saludos y gracias por todo!

---

### Post by Applelnx on 2010-09-12
Hola ishared, de lo que encontre en Google, me parece que esto es lo que te podria servir:
[http://www.comprousa.com/forums/viewtopic.php?f=8&t=1569](http://www.comprousa.com/forums/viewtopic.php?f=8&t=1569)

Crea el archivo saa7134.conf en el directorio /etc/modprobe.d
Para eso abri la terminal y pone:

```
sudo gedit /etc/modprobe.d/saa7134.conf
```

Ahi te va a aparecer un editor de textos, donde le tenes que pegar lo siguiente:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options i2c-algo-bit bit_test=1
options saa7134 card=99 tuner=59 secam=dk
options tuner secam=d
```

Despues guardas el documento y reinicias la maquina.
Abri el Tvtime y avisanos como te fue.
Saludos

---

### Post by mdqman on 2010-09-12
Hola ishared, mira yo hace un mes me compre una placa marca Encore que tiene el mismo chip que la tuya, phillips saa7131, y hace un mes que estoy tratando de hacerla funcionar en Ubuntu, en Mandriva y hasta en Tuquito4, y no hay manera. Hay gente que dice que lo ha logrado, aquí te dejo algunos links que pueden ayudarte, lo que es yo no pude. Si logras hacerla funcionar, por favos postea el resultado. 

[http://miblockdenotix.wordpress.com/2008/07/13/capturadora-philips-saa713-compro-videomate-ubuntu/](http://miblockdenotix.wordpress.com/2008/07/13/capturadora-philips-saa713-compro-videomate-ubuntu/)

[http://www.ubuntu-es.org/index.php?q=node/92224](http://www.ubuntu-es.org/index.php?q=node/92224)

[http://www.ubuntu-es.org/index.php?q=node/8790](http://www.ubuntu-es.org/index.php?q=node/8790)

[http://www.linuxmint-hispano.com/foro/index.php/topic,1094.0.html](http://www.linuxmint-hispano.com/foro/index.php/topic,1094.0.html)
 saludos

---

### Post by Applelnx on 2010-09-12
Hola mdqman, tengo entendido que para hacer funcionar tu placa deberías hacer lo siguiente:

```
sudo rmmod saa7143
sudo modprobe saa7134 card=**[COLOR="Red"]XX[/COLOR]**
tvtime
```

siendo XX el numero de tu placa de acuerdo a este listado (hay varios modelos de encore 106, 107 y 148, fijate si el tuyo esta ahi):
[http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134)

Lo que haces ahi es sacar el modulo saa7134 que se carga por defecto al iniciarse ubuntu y le indicas el correcto.

Saludos

---

### Post by mdqman on 2010-09-13
Lo que tu dices es correcto aplelnx, y ya lo vi en algunos tutoriales, pero cuando yo pongo el comando que me decis, la salida es esta: 

daniel@daniel-desktop:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa
daniel@daniel-desktop:~$ 

y ahi ya me quedo. 
El numero que corresponde a mi placa Encore ENLTV FM3 es efectivamente el 148.

Si sabes porque me tira ese ERROR y como seguir adelante te agradeceria.
El kernell en uso es el 2.6.32-24-generic
Saludos y gracias

---

### Post by mdqman on 2010-09-13
cancelado

---

### Post by Applelnx on 2010-09-13
> **mdqman said:**
> Lo que tu dices es correcto aplelnx, y ya lo vi en algunos tutoriales, pero cuando yo pongo el comando que me decis, la salida es esta: 

daniel@daniel-desktop:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa
daniel@daniel-desktop:~$ 

y ahi ya me quedo. 
El numero que corresponde a mi placa Encore ENLTV FM3 es efectivamente el 148.

Si sabes porque me tira ese ERROR y como seguir adelante te agradeceria.
El kernell en uso es el 2.6.32-24-generic
Saludos y gracias

Proba sacando el modulo saa7134_alsa antes:

$ sudo rmmod sudo saa7134_alsa
$ sudo rmmod sudo saa7134
$ sudo modprobe saa7134 card=148
$ tvtime

Saludos

---

### Post by mdqman on 2010-09-15
Bueno, estoy en lo mismo, al tratar de borrar el modulo saa7134_alsa,  la respuesta es esta: 

daniel@daniel-desktop:~$ sudo rmmod saa7134_alsa
[sudo] password for daniel: 
ERROR: Module saa7134_alsa is in use
daniel@daniel-desktop:~$

Si no me equivoco el modulo alsa es el que maneja el sonido en el sistema. La verdad que no quiero tocar demasiado sin saber.  Igual agradezco el intento y la ayuda.
Saludos

---

### Post by Applelnx on 2010-09-16
> **mdqman said:**
> Bueno, estoy en lo mismo, al tratar de borrar el modulo saa7134_alsa,  la respuesta es esta: 

daniel@daniel-desktop:~$ sudo rmmod saa7134_alsa
[sudo] password for daniel: 
ERROR: Module saa7134_alsa is in use
daniel@daniel-desktop:~$

Si no me equivoco el modulo alsa es el que maneja el sonido en el sistema. La verdad que no quiero tocar demasiado sin saber.  Igual agradezco el intento y la ayuda.
Saludos

Si, yo hasta aca llego, no me quiero meter mas. Quizas otro te pueda decir mejor que hacer. Saludos

---

### Post by guillermolisi on 2010-09-16
El modulo que esta en uso no es precisamente el Alsa mismo sino el que oficia conectando la placa capturadora con Alsa.

Para saber quien lo esta usando intentaria con lsmod en una consola/terminal.

---

### Post by gThumb on 2010-11-13
Kernel patch is correct action. (!!!)
TV, radio and remote control every time. Checked - it works!
To download the patch you need register here:
[http://forum.ubuntu.ru/index.php?topic=122493.0](http://forum.ubuntu.ru/index.php?topic=122493.0)
[http://www.ubuntu.vrn.ru/index.php?topic=84.msg1564#msg1564](http://www.ubuntu.vrn.ru/index.php?topic=84.msg1564#msg1564)

Kernel for Ubuntu 10.10 - i386 with support Compro VideoMate M1F:
[http://forum.ubuntu.ru/index.php?topic=122493.msg908127#msg908127](http://forum.ubuntu.ru/index.php?topic=122493.msg908127#msg908127)
(Linux kernel 2.6.35.7 for Compro VideoMate M1F in Ubuntu 10.10, options saa7134 card=181 tuner=59)

---

