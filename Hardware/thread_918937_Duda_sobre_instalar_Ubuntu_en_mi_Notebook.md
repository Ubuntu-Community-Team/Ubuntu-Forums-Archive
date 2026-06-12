---
title: "Duda sobre instalar Ubuntu en mi Notebook"
date: 2008-09-13
forum: Hardware
---

### Post by santiagofrias on 2008-09-13
Amigos:se me presenta la duda sobre instalar o no Ubuntu en mi notebook (lo cual determinaría de pasarme totalmente a Linux), por el siguiente motivo: si bien en mi PC la instalación y todo el hardware funciona sin problemas con Ubuntu, incluída la conexión a Internet, el módem/router con el que me conecto a mi notebook (aún con el SO Windows XP intalado), la impresora, el pendrive, etc.,la pregunta se dirige a un Modem de Sony Ericsson provisto por Arnet (Arnet Go) con el que conecto la notebook cuando no tengo WiFi cercano (bar o similares).
Entrando a la página de Sony, leí que si bien dicho modem acepta todas las versiones de "Güindous", no hay drivers para Linux. Hay alguien que lo haya podido instalar o desarrollado alguna forma?.
El modem es un USB MD300 de Sony Ericsson. con chip de Arnet (Personal)
Gracias desde ya.

---

### Post by sergiom99 on 2008-09-13
Hola Santiago, bienvenido.
Que laptop tenes?
Lo mas rapido y facil es buscar en google. Es cierto que no anda en linux, segun lei.
Sin embargo vi resultados que dicen que pueden hacerlo andar. Seria cuestion de probarlo desde un LiveCD de Ubuntu asi no instalas linux en tu laptop si no podes hacerlo funcionar.
Otra opcion, semi-solucion en realidad, es usar una maquina virtual dentro de tu ubuntu en la laptop para navegar. no gran cosa en realidad.
te dejo dos links que discuten el tema.
Suerte!
(1) [http://www.ubuntu-es.org/index.php?q=node/94744](http://www.ubuntu-es.org/index.php?q=node/94744)
(2) [http://twilightlinuxzone.blogspot.com/2008/08/sony-ericsson-md300-en-linux.html](http://twilightlinuxzone.blogspot.com/2008/08/sony-ericsson-md300-en-linux.html)
Fuente> [http://www.google.com.ar/search?hl=es&q=USB+MD300+Sony+Ericsson+linux&btnG=Buscar+con+Google&meta=](http://www.google.com.ar/search?hl=es&q=USB+MD300+Sony+Ericsson+linux&btnG=Buscar+con+Google&meta=)

---

### Post by santiagofrias on 2008-09-13
Muchas gracias Sergio, te cuento mi Laptop es una Bangho Intel Core 2 Duo, 2 GB de ram y 120 mb de disco, tiene incorporada placa WiFi que utilizo para conectarme en red (doméstica con una PC con Ubuntu e Internet en bares, etc.); lo único que me faltaba era el tema del Modem de Arnet Go, que en realidad lo uso eventualmente cuando tengo que conectarme a Internet y no tengo antenas WiFi cerca. (Arnet Go tiene una amplia cobertura aquí); pero como dije, es eventual así que creo que no habra muchos problemas. De todas formas voy a revisar los links que me dejaste y si no dejo instalado lo mínimo del "Güindous" para utilizar el modem.
Gracias desde ya

---

### Post by ArgentinoGuy on 2008-09-20
estimado,

lo mejor es googlear bastante antes de pasarte del todo a linux, solo como para no pasar mucho tiempo sin que te ande el modem, que de seguro lo vas a hacer andar pero no en dos patadas. Al modemsito huawei lo hacen andar en ubuntu con un driver no oficial que anda con varias marcas, hay otro post abierto que te puede llegar a ser muy util, hechale un ojo.

Bue, espero te sirva de algo mi comentario, saludos che y suerte con eso!

---

### Post by fmsismo on 2008-09-20
Santiago muchas pruebas las podes hacer con el livecd.  Si podes hacer que todo te ande con el livecd estas más que seguro de que te va a andar cuando lo instales.

Saludos

---

### Post by vk-cdg on 2008-09-22
> **santiagofrias said:**
> Amigos:se me presenta la duda sobre instalar o no Ubuntu en mi notebook (lo cual determinaría de pasarme totalmente a Linux)...

Mi consejo sería... no te prives de las ganas de usar Ubuntu (o cualquier otra distro) por un modem, instalate Ubuntu en dual boot y listo. Cuando tengas que usar el modem levantá Windows y listo, el resto del tiempo Ubuntu. :)

Yo en mi notebook tengo el vista y ubuntu en dual boot. Ciertos softwares de la facultad corren solo bajo windows (Qlick View por ejemplo, es para Datawarehouse). 
El resto del tiempo, uso Ubuntu y estoy mas que satisfecho!

---

### Post by dropedrobarri on 2008-09-23
> **santiagofrias said:**
> Muchas gracias Sergio, te cuento mi Laptop es una Bangho Intel Core 2 Duo, 2 GB de ram y 120 mb de disco, tiene incorporada placa WiFi que utilizo para conectarme en red (doméstica con una PC con Ubuntu e Internet en bares, etc.); lo único que me faltaba era el tema del Modem de Arnet Go, que en realidad lo uso eventualmente cuando tengo que conectarme a Internet y no tengo antenas WiFi cerca. (Arnet Go tiene una amplia cobertura aquí); pero como dije, es eventual así que creo que no habra muchos problemas. De todas formas voy a revisar los links que me dejaste y si no dejo instalado lo mínimo del "Güindous" para utilizar el modem.
Gracias desde ya
Santiago:
Yo soy usuario de UBUNTU, y tengo también una banghó. El Problema es que, al menos mi laptop, tiene un chip VIA CN896, lo que me ha generado montón de problemas.... podes ver el siguienyte link: [http://ge.ubuntuforums.com/showthread.php?t=723493](http://ge.ubuntuforums.com/showthread.php?t=723493)
Allí como te darás cuenta posteamos pearlhead y yo algunas cosas para que te informes.
Hay cosas que debes saber:
1.- UBUNTU es una masa para detectar cualquier modem, sino te bajas el driver que necesitas.
2.- Con el tema wi-fi, con BACKTRACK3 [www.remote-exploit.org](www.remote-exploit.org) podes crackear cualquier clave wep o wap de cualquier red....
3.- Otra.... ubuntu tiene la virtud de no caerse cuando está funcionando el wi-fi, no así windows que es un desastre.
4.- Podés instalar los dos sistemas en tu laptop (GUINDOWS JA JA  y ubuntu, pero yo te aconsejo que te metas a full en linux.

Como verás, en el link de arriba, tuve varios problemas, ahora instalé el UBUNTUSTUDIO (por cd alternate).
Te sugiero que si no te anda tu laptop con el LIVE CD te bajes el UBUNTU ALTERNATE que eso si se instala sí o sí en tu laptop. Vas a saber si anda o no si no podes entrar al modo gráfico.
Ahora te cuento, que mandé un email a  la gente de VIA (el soporte) para mi chipset VIA. 
Y esto es lo que me contestó: 
[COLOR="Blue"]Hello Pedro:
    For CN896 and Ubuntu 8.04.1, please reuse the stable release driver. After that, please update the kernel follow the procedure listed as below:
1. Install the driver of CN896 for Ubuntu 8.04
2. chmod of via.ko, drm.ko, via_chrome9.ko and via-agp.ko to 744(in attached files)
3. copy the drm.ko, via.ko and via_chrom9.ko to /lib/modules/&#8217;uname &#8211;r&#8217;/kernel/drivers/char/drm
4. copy via-agp.ko to /lib/modules/&#8217;uname &#8211;r&#8217;/kernel/drivers/char/agp
5. run depmod with root.
Regarding the Raid, do you have 2 disk for backup? Is there any special application for Latop to use Raid function? No extra driver is required for Ubuntu 8.04 if you are looking for VIA storage driver. It's in mainline since 2.6.23.
 
Thanks and Best Regards
Bruce C. Chang
[/COLOR]
y también me mandó un ZIP de UBUNTU 8.04... para hacer todo el laburo y solucionar todo.
Espero que te sirva la info. 
Para la comunidad veo como adjuntar el archivo que me mandó el Sr. CHANG de VIA, así vemos todos si funciona.

---

### Post by santiagofrias on 2008-10-06
> **dropedrobarri said:**
> Santiago:
Yo soy usuario de UBUNTU, y tengo también una banghó. El Problema es que, al menos mi laptop, tiene un chip VIA CN896, lo que me ha generado montón de problemas.... podes ver el siguienyte link: [http://ge.ubuntuforums.com/showthread.php?t=723493](http://ge.ubuntuforums.com/showthread.php?t=723493)

[/COLOR]
y también me mandó un ZIP de UBUNTU 8.04... para hacer todo el laburo y solucionar todo.
Espero que te sirva la info. 
Para la comunidad veo como adjuntar el archivo que me mandó el Sr. CHANG de VIA, así vemos todos si funciona.

dropedrobarri, gracias por la info, finalmente instalé Ubuntu en la Laptop y todo funcionó perfecto, hasta la red en la que pude compartir archivos entre una y otra máquina por Wi-Fi.
El problema que se me presentó fue cuando se cortó literalmente el cable telefónico de mi edificio; aparte de perder internet, las máquinas ya no se veían entre ellas en Ubuntu pero sí en Windows (o sea, iniciando la laptop con WinXp, podía ver la pc que estaba con Ubuntu)
Pregunta: ¿Tiene algo que ver la falta de conexion ADSL que no permita ver la red en Ubuntu o es casualidad?
Pregunta 2: Mi laptop tambien tiene chip VIA ¿pudiste subirlo a la comunidad al que te enviaron?
Gracias desde ya

---

