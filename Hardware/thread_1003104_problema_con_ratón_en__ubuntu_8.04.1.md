---
title: "problema con ratón en  ubuntu 8.04.1"
date: 2008-12-05
forum: Hardware
---

### Post by lucasfava on 2008-12-05
Hola 
Mi problema es el siguiente, yo tengo un ratón a bolita con la ficha trapesoidal (creo que son los de puente), pero no me lo detecta, y no se si halla algun problema con el teclado, porque quise usar la tecla tab para poder apagar pero no habia respuesta.[-o<

P.D: Soy primeriso en Ubuntu, y este es mi primer mensaje aca \\:D/, ademas habia pedido el LiveCd y tube que esperar que me trajeran la Pc del tecnico q la tenia desde hace 6 meses hay tirada

---

### Post by Hei Ku on 2008-12-05
No entiendo cuál es tu problema exactamente. 
No te anda el mouse? 
No te anda el teclado? 
Te arranca el LiveCD? 
Te aparece algún mensaje?

---

### Post by c4d0rn4 on 2008-12-05
> **lucasfava said:**
> Hola 
Mi problema es el siguiente, yo tengo un ratón a bolita con la ficha trapesoidal (creo que son los de puente), pero no me lo detecta, y no se si halla algun problema con el teclado, porque quise usar la tecla tab para poder apagar pero no habia respuesta.[-o<
En windows anda todo?

Qué es lo que haces con el teclado?
Siendo nuevo en ubuntu sabes usarlo sin mouse la interfaz de gnome? (implicaría conocer una par de atajos como mínimo).
=S :???:


> P.D: Soy primeriso en Ubuntu, y este es mi primer mensaje aca \\:D/, ademas habia pedido el LiveCd y tube que esperar que me trajeran la Pc del tecnico q la tenia desde hace 6 meses hay tirada

Uno, usualmente, cuando pide un livecd por correo, suele esperar el livecd, no la pc que venga del técnico :lolflag:

Lo de tener la pc tirada en el técnico 6 meses, no suena lindo, por eso pregunto si funciona en windows.

y esto todavía no lo entiendo jajaja xD
> quise usar la tecla tab para poder apagar pero no habia respuesta.
Que pensabas hacer con el tab? ajja xD

---

### Post by guillermolisi on 2008-12-06
> **lucasfava said:**
> Hola 
Mi problema es el siguiente, yo tengo un ratón a bolita con la ficha trapesoidal (creo que son los de puente), pero no me lo detecta, y no se si halla algun problema con el teclado, porque quise usar la tecla tab para poder apagar pero no habia respuesta.[-o<

P.D: Soy primeriso en Ubuntu, y este es mi primer mensaje aca \\:D/, ademas habia pedido el LiveCd y tube que esperar que me trajeran la Pc del tecnico q la tenia desde hace 6 meses hay tirada
Dado que no tenemos informacion sobre la maquina salvo que estuvo durante un tiempo considerable en el servicio tecnico y no especificas que arreglos/reparaciones/mantenimiento se le hcieron, mi recomendacion es:

Revisar que los conectores que no esten montados sobre la motherboard, que se conecten a traves de cables, esten correctamente conectados.

La prueba con otro sistema operativo puede ayudar a determinar si la causa es hardware o software. Lo mismo si tenes la posibilidad de probar con otro mouse, tal vez mas moderno.

Iniciar con LiveCD tambien puede ayudar a determinar si es algun problema de instalacion de Ubuntu.

Si el conector del mouse es trapezoidal, y no es un adaptador, posiblemente el mouse sea serial (RS-232) y no PS/2.

---

### Post by lucasfava on 2008-12-06
Perdon por lo bruto :lol:
me fije bien y anda el teclado, de bruto no más :D, el problema es con el ratón, pero andaba con el liveCd cuando lo probe.
Con respecto al servicio tecnico es otra historia.

Una consulta más, cuando apago el S.O queda sistem no se que :-?, se queda hay y no se apaga automaticamente, como lo hacia con el LiveCd.
El S.O lo tengo junto con Xp, lo raro es que el Xp no me lee el Mp3 pero si Ubuntu

---

### Post by rojojuan on 2008-12-06
Si es un ratón serial hay que tocar el xorg y cambiar el ttYs según sea el puerto serie.
Probá colocar ttYs 1 después 2 o bien cero.
Me parece que tiene que andar.
Si necesitás más ayuda posteá y dentro de lo que pueda te ayudo.

---

### Post by lucasfava on 2008-12-06
me vas a tener que explicar los pasos que tengo que hacer para probar los cambios :p

---

### Post by z37a on 2008-12-06
> **lucasfava said:**
> 
Una consulta más, cuando apago el S.O queda sistem no se que :-?, se queda hay y no se apaga automaticamente, como lo hacia con el LiveCd.
El S.O lo tengo junto con Xp, lo raro es que el Xp no me lee el Mp3 pero si Ubuntu

Consulta, en ese momento te titilan las 3 luces del teclado(caps look, bloq myus, etc...)???

Ahora si no es lo que te pregunte puede ser por el ACPI que no sea compatible con Ubuntu, con el driver que trae, fijate si podes poner todo lo que te arroja el mensaje ese al apagar, así seria mas fácil ver exactamente que es.

---

### Post by rojojuan on 2008-12-07
Te dejo este link:

[http://eluneg.wordpress.com/2008/05/20/configurar-un-mouse-serial-para-ubuntu/](http://eluneg.wordpress.com/2008/05/20/configurar-un-mouse-serial-para-ubuntu/)

Fijate bien que que S0 no es ese o, sino ese cero. Aquí tenés que probar si tu mouse es cero, uno o dos. Lo cambas, reinicias y probás otra vez, hasta que arranque.

---

### Post by lucasfava on 2008-12-08
Hola [COLOR="Red"]**rojojuan**[/COLOR]
Como soy primeriso,na de experiencia tengo :rolleyes:, entro a la terminal, donde está el Signo $ pongo lo que indica el blog

$ sudo gedit/etc/X11/xorg.conf (para ubuntu) [COLOR="red"]enter[/COLOR]
Pero luego me manda 
orden no registrada
y me pide el password, pero no lo puedo escribir

Algo estoy haciendo mal :confused:

---

### Post by Hei Ku on 2008-12-08
No, lo estas haciendo bien.
Cuando te pide que ingreses el password no te aparece nada a proposito. 

Escribi tu password y apreta Enter. Ahí te va a ejecutar el comando.

---

### Post by lucasfava on 2008-12-08
Ese es el problema es que veo que elcursor no se mueve. Lo escribo pero siempre me está pidiendo el password

---

### Post by c4d0rn4 on 2008-12-08
te acordas tu password?
cuando te pida el password mirá fijamente el teclado, ovlidate de TODO. Escribí el pass y apretá enter.

El comando que debes ejecutar es 

```
sudo gedit/etc/X11/xorg.conf
```

el simbolo peso no debés ponerlo.

---

### Post by rojojuan on 2008-12-08
Así es, cuando te pide el pass vos lo escribís pero en pantalla no vas a ver nada. El sistema lo hace a propósito para que nadie pueda leerlo.
Escribis el pass y le das enter y te aparece el programa para editar.
Si tenés dudas volvé a preguntar, ok?

---

### Post by lucasfava on 2008-12-08
El password me lo acuerdo bien :p

Haber sacame la duda entonces lo que dice en la terminal lo borro y pongo la orden sola 

[COLOR="red"]~$ sudo[/COLOR] como lo escribi en la terminal

lo escribo como

[COLOR="Red"]sudo[/COLOR] y todo lo demas

perdon por mi completa ignorancia :confused:, no se como pasar usando el teclado una captura que hice de lo q pasa

---

### Post by hictio on 2008-12-08
> **lucasfava said:**
> El password me lo acuerdo bien :p

Haber sacame la duda entonces lo que dice en la terminal lo borro y pongo la orden sola 

[COLOR="red"]~$ sudo[/COLOR] como lo escribi en la terminal

lo escribo como

[COLOR="Red"]sudo[/COLOR] y todo lo demas

perdon por mi completa ignorancia :confused:, no se como pasar usando el teclado una captura que hice de lo q pasa

Tenes que escribir todo, lo que estas haciendo es decirle a tu maquina Ubunut que queres abrir el programa gedit sobre el archivo /etc/X11/xorg.conf, y ademas, que lo queres abrir con los privilegios del usuario root, equvalente al Administrator de Windows.

Es asi:

sudo ESPACIO gedit ESPACIO /etc/X11/xorg.conf (ENTER)

```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by lucasfava on 2008-12-08
Gracias [COLOR="Red"]**hictio**[/COLOR] por corregir mi error, funciono perfectamente, tuve que poner ttyS0 y funciono a la primera.

Gracias a todos :lolflag::p
Solo habra que ver porque no se apaga automáticamente y el asunto de la hora, porque parece que afecta al xp

---

