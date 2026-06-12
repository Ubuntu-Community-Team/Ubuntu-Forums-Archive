---
title: "Ipod Touch 4G en Ubuntu 10.04"
date: 2010-12-29
forum: Hardware
---

### Post by donmatas on 2010-12-29
Estimad@s:

le regalé a mi esposa un Ipod touch 4g. NO tengo ninguna experiencia en ese tipo de productos y no he podido hacer que se monte adecuadamente ni en mi 10.04 ni en 9.10 de mi esposa. Leí que en el 10.04 sería reconocido nativamente, pero no es así. Sólo monta la cámara fotográfica.

¿Alguien tiene idea de como hacerlo?

gracias
DM

---

### Post by bichopro on 2010-12-29
abre rhythmbox con el ipod conectado y deberias poder enviar los archivos. Si no prueba con banshee

---

### Post by 3nG3ndR0 on 2010-12-30
que firmware tiene yo tengo un ipod touch 2g y con el firmware 4.1 me lo reconoce sin problema en ubuntu 10.10, por ahí e leído que con  la 4.2 no lo reconoce no se aun no actualizo.

---

### Post by donmatas on 2010-12-31
> **3nG3ndR0 said:**
> que firmware tiene yo tengo un ipod touch 2g y con el firmware 4.1 me lo reconoce sin problema en ubuntu 10.10, por ahí e leído que con  la 4.2 no lo reconoce no se aun no actualizo.

No actualize compadre, le doy firmado que no le va a funcionar. ¿Alguien sabe como reestablecer la actualización anterior? No sirve con "restaurar" porque te ofrece "restaurar y actualizar" sin dar la posiblidad de sólo restaurar...

salud y gracias por las respuestas

DM

---

### Post by donmatas on 2010-12-31
> **bichopro said:**
> abre rhythmbox con el ipod conectado y deberias poder enviar los archivos. Si no prueba con banshee

Gracias compa, pero antes de escribir este post hice las cosas obvias y un poco más. Rhtymbox no sirve

saludos
DM

---

### Post by donmatas on 2010-12-31
En el foro en inglés encontré esto y lo ejecuté:
```

sudo add-apt-repository ppa:pmcenery/ppa

```
then update and upgrade your packages
```

sudo apt-get update
sudo apt-get upgrade

```

Reinicié la computadora y ahora sí reconoció el ipod. Hice doble click sobre el ícono del Ipod y se abre una ventana con los contenidos del mismo. En la barra de arriba apareció la opción, "abrir rhythmbox". Al apretarla se abre el reproductor de música y aparece el Ipod. Arrastro canciones y pareciera funcionar, aunque el Ipod no da señales de estar recibiendo nada. Después de traspasar canciones, las busco en el Ipod y no las puedo encontrar. ¿Alguien tiene idea de qué puede estar pasando?

gracias y felix año
DM

---

### Post by Carlos C on 2011-01-01
Quizás si nos dieras el link original de donde sacaste esos comandos podríamos ayudarte un poco más.

Saludos.

---

### Post by donmatas on 2011-01-01
> **Carlos C said:**
> Quizás si nos dieras el link original de donde sacaste esos comandos podríamos ayudarte un poco más.

Saludos.
 Gracias compa por la respueste. El hilo original está aquí:

[http://ubuntuforums.org/showthread.php?t=1654334](http://ubuntuforums.org/showthread.php?t=1654334)

salud y felix año!

DM

---

### Post by donmatas on 2012-01-23
En todo este tiempo, todavía no se resuelve el pinche problema?

---

