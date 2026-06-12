---
title: "problema con driver de video [SiS] 771/671 PCIE VGA"
date: 2009-12-25
forum: Hardware
---

### Post by habuca on 2009-12-25
buenas foro soy relamente nuevo aca y con respecto al tema de linux
la cosa es que instale ubuntu karmic koala en mi pc pero no se como instalar el driver de video en el mi notebook es un packard bell mx 35 agradeceria cualquier respuesta

sorry si publique mal 

saludos

---

### Post by Carlos C on 2009-12-25
Primero tenemos que saber qué modelo de tarjeta de video tienes. Por favor escribe en el terminal:

```
lspci |grep VGA
```Pega acá lo que te sale.


En el futuro, cuando tengas otras dudas, puedes usar [FUCH]("http://ubuntuforums.org/showthread.php?t=1211568") para darnos la información de tu equipo.


Movido a "Hardware".
Saludos.

---

### Post by habuca on 2009-12-25
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

eso salio

muchas gracias por tu atencion

saludos

---

### Post by Carlos C on 2009-12-26
Ese modelo de tarjeta funciona con los drivers open source que vienen instalados en Ubuntu por defecto. No necesitas instalar nada. ¿Por qué piensas que debes instalar algo? ¿No está funcionando el video? Te aviso que es un modelo de tarjeta que no da soporte para Linux, por lo que su rendimiento es bastante discreto. En general se recomienda no usarla.

Espero que puedas clarificar esas dudas.

Saludos.

---

### Post by habuca on 2009-12-26
muchas gracias por la respuesta la probelmatica es la siguiente resulta que cuando me voy a sistema>preferencias>pantalla solo me deja tomar la configuracion por pantalla de  800x600 entonces no me deja ocupar otra resolucion en mi equipo por ende como en windows tomaba esa resolucion por defecto cuando no estaba instalado el controlador de video pense que faltaba instalarlo

muchas gracias por tu respuesta ahora buscare la manera de cambiar la resolucion ya que tengo instalado el controlador


saludos

---

### Post by Carlos C on 2009-12-26
La resolución puedes configurarla en tu archivo /etc/X11/xorg.conf. Existe un thread en ubuntuforums dedicado a estas tarjetas. Te recomiendo mucho que lo veas:

[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

Es bastante largo, pero al final parece que alguien dio con un driver que mejora el desempeño de la tarjeta y permite una resolución adecuada:

[http://ubuntuforums.org/showpost.php?p=8549392&postcount=292](http://ubuntuforums.org/showpost.php?p=8549392&postcount=292)

Si no te resulta tendrás que leer toda la discusión ;) También puedes buscar información aquí:

[http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/)

Espero que te sirva de algo.

Saludos.

---

### Post by habuca on 2009-12-26
> **Carlos C said:**
> La resolución puedes configurarla en tu archivo /etc/X11/xorg.conf. Existe un thread en ubuntuforums dedicado a estas tarjetas. Te recomiendo mucho que lo veas:

[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

Es bastante largo, pero al final parece que alguien dio con un driver que mejora el desempeño de la tarjeta y permite una resolución adecuada:

[http://ubuntuforums.org/showpost.php?p=8549392&postcount=292](http://ubuntuforums.org/showpost.php?p=8549392&postcount=292)

Si no te resulta tendrás que leer toda la discusión ;) También puedes buscar información aquí:

[http://ncc-1701a.homelinux.net/~linux-sis/]("http://ncc-1701a.homelinux.net/%7Elinux-sis/")

Espero que te sirva de algo.

Saludos.
te agradesco de verdad por tu ayuda segui los pasos del seguno post reinicie y puede cambiar la resolucion de mi pantalla

de verdad estoy muy agradecido por tu ayuda y tu tiempo

muchas gracias saludos

---

