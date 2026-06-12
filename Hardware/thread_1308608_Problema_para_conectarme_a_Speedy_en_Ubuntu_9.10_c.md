---
title: "Problema para conectarme a Speedy en Ubuntu 9.10 con Modem Huawei"
date: 2009-10-31
forum: Hardware
---

### Post by darkside2009 on 2009-10-31
Hola,muchachos,escribo este post porque tengo problemas con la conexion a Speedy(Conexion ADSL).
El modem que estoy usando es el Huawei SmartAX MT880.Aca les dejo una foto para q lo ubiquen:

[IMG]http://tomsk.wstream.ru/karta/bz/huawei800.jpg[/IMG]

Lo raro es que en Ubuntu 9.04 me conectaba perfectamente y tambien que la conexion Auto Eth0 me la detecta,pero al crear la conexion ADSL de Speedy con contraseña y todo no me puedo conectar.

Bueno espero que alguien me ayude.Saludos

---

### Post by rubioo on 2009-10-31
Hola darkside2009, yo tengo el mismo problema que vos.
Lo pude solucionar conectandome con **pppoeconf**

Para eso, vas a Aplicaciones > Accesorios > Terminal y en la ventanita negra que te aparece escribis **sudo pppoeconf**, luego completas con los datos que te pregunta y cuando termine vas a tener internet.

Yo tambien quiero conectarme como lo hacia antes, pero por ahora no puedo :S

 Saludos y suerte

---

### Post by moreback on 2009-11-01
> **darkside2009 said:**
> Lo raro es que en Ubuntu 9.04 me conectaba perfectamente y tambien que la conexion Auto Eth0 me la detecta,pero al crear la conexion ADSL de Speedy con contraseña y todo no me puedo conectar.

A lo mejor la conexión **Auto eth0** está causando conflicto con la DSL que configuras. Bórrala e intenta configurar tu conexión ADSL nuevamente.

Saludos.

---

### Post by josecuervo86 on 2009-11-01
> **darkside2009 said:**
> Hola,muchachos,escribo este post porque tengo problemas con la conexion a Speedy(Conexion ADSL).
El modem que estoy usando es el Huawei SmartAX MT880.Aca les dejo una foto para q lo ubiquen:

Lo raro es que en Ubuntu 9.04 me conectaba perfectamente y tambien que la conexion Auto Eth0 me la detecta,pero al crear la conexion ADSL de Speedy con contraseña y todo no me puedo conectar.

Bueno espero que alguien me ayude.Saludos

Yo tengo el mismo modem, y el network-manager siempre me hizo renegar para conectarme. La solución:

```
sudo pppoeconf
```

---

### Post by darkside2009 on 2009-11-01
Bueno muchachos voy a probar las dos opciones que me dieron con el live cd,gracias por la ayuda.

Saludos

---

### Post by rubioo on 2009-11-02
Yo el sabado lo configure como router y ya no tengo que usar pppoeconf ni nada :)
De [acá]("http://ubuntuforums.org/showthread.php?t=779717&page=2#19") saque como hacerlo, sólo que no borre los nodos, edite el primero dejando los demas (sino no funcionaba)

    Saludos y suerte

---

### Post by darkside2009 on 2009-11-07
Hola,bueno estube probando configurarlo como router con el tutorial que dejó rubioo,pero llegué solo a la parte en la que hay que poner la direccion en el navegador.Cuando me pide el user y el password no se que poner,xq en el tutorial no dice,probe muchas cosas pero no pude

Haber si me pueden ayudar con el tutorial

---

### Post by josecuervo86 on 2009-11-07
darkside, los valores por defecto son username:**admin** password:**1234**

---

### Post by darkside2009 on 2009-11-07
Hola otra vez :p,bueno sigo sin poder conectarme,puse el user y el admin como me dijeron pero nada,me lo vuelve a pedir,nose que sera,pero por las dudas les pongo unas capturas
[IMG]http://i242.photobucket.com/albums/ff163/sanokenshin2/Pantallazo-7.png[/IMG]

[IMG]http://i242.photobucket.com/albums/ff163/sanokenshin2/Pantallazo-1-3.png[/IMG]

---

### Post by Mauro22 on 2009-11-07
Segun [esto]("http://www.taringa.net/posts/info/964944/Configurar-como-Router-Modem-Huawei-Smart-ax-MT-880.html")(una guia de T! ) el usuario es admin y la contraseña admin

---

### Post by rubioo on 2009-11-07
Segun el manual de usuario del SmartAX MT880, el usuario es **admin** y la contraseña **1234**

---

### Post by darkside2009 on 2009-11-07
Hola,bueno les traigo algunas noticias,la primera es que la contraseña era admin y el user admin,la segunda es que configure todo con el manual de taringa y sirvio,pero solo en mi windows 7 y no en ubuntu :S
Asi que despues voy a ver que hago


Saludos

---

### Post by josecuervo86 on 2009-11-07
Pero por lo menos con pppoeconf te podes conectar o no probaste??

---

### Post by darkside2009 on 2009-11-07
Si,tambien probe con el pppoeconf pero me tira errores al final:

[IMG]http://i242.photobucket.com/albums/ff163/sanokenshin2/pppoeconf1.png[/IMG]


[IMG]http://i242.photobucket.com/albums/ff163/sanokenshin2/pppoeconf2.png[/IMG]


[IMG]http://i242.photobucket.com/albums/ff163/sanokenshin2/pppoeconf3.png[/IMG]


[IMG]http://i242.photobucket.com/albums/ff163/sanokenshin2/pppoeconf4.png[/IMG]



Otra cosa rara que noté fue que ahora cuando hago click en el network manager en vez de mostrarme la conexion authoeth0 me dice:
Dispositivo no gestionado



Saludos

---

### Post by josecuervo86 on 2009-11-07
Yo te recomendaria que prubes de nuevo con pppoeconf, pero esta vez apaga el modem y volvelo a prender y espera a que aparezcan las dos luces naranjas. Cuando se prenden las dos proba. A veces se retoba y no quiere andar pero proba que despues anda. Yo me conecto de esa manera

---

### Post by guillermolisi on 2009-11-08
> **darkside2009 said:**
> 
Otra cosa rara que noté fue que ahora cuando hago click en el network manager en vez de mostrarme la conexion authoeth0 me dice:
Dispositivo no gestionado

Saludos
Es que cuando la interface la administra otro (vos mismos configurando sus valores directamente en /etc/network/interfaces o a traves de otro software) NM da esa advertencia.

---

### Post by darkside2009 on 2009-11-08
Buenas noticias,finalmente ya me pude conectar,eso si siempre teniendo que usar la terminal y poniendo ping mas la direccion.Alguien sabe si puedo hacer que la conexion sea automatica y sin usar la terminal.

Saludos

---

