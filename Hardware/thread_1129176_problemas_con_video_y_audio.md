---
title: "problemas con video y audio"
date: 2009-04-18
forum: Hardware
---

### Post by fortux on 2009-04-18
hola amigos!!

Bueno... hoy es mi primer dia usando Ubuntu, tengo el 8.04.02

Estoy muy ansioso con aprender a usarlo, pero estoy teniendo problemas con el video y el audio.

Instale el VLC pero cuando abro el video se pone muy lento, y la pantalla ( de reproduccion) Verde.

Y cuando escucho mp3 con el VLC, los escucho un poco cortado.

que puedo hacer???

Mi pc es un Dual core 3.20 Ghz, con 2 gb de ram

No se si tendra esto que ver o no.. pero cuando quiero que  modificar los efectos visuales tampoco me lo permite, supngo que algo con el video o la placa de video no anda bien.

desde ya muchas gracias!

---

### Post by josecuervo86 on 2009-04-18
Tenes placa de video integrada? Podrias poner lo que te sale con lspci en la terminal?
Abri la terminal (Aplicaciones > Accesorios > terminal) y escribi

```
lspci
```

y despues pega lo que te sale asi vemos que hardware tenes

---

### Post by fortux on 2009-04-18
me salio esto:

00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP [VIA P4M890 Chipset] (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)


como sigo?? si... la placa esta integrada, tanto de video como audio.

---

### Post by josecuervo86 on 2009-04-18
Bueno, ahora pone en la terminal:

```
glxgears
```

dejalo un ratito (30 segundos) y pega lo que te sale

---

### Post by fortux on 2009-04-18
gracias josecuervo!

aqui pego lo q me indicas

lo deje un poco mas de 30 segundos y luego lo cerre

fortux@fortux-desktop:~$ glxgears
5058 frames in 5.0 seconds = 1011.560 FPS
5137 frames in 5.0 seconds = 1027.398 FPS
5143 frames in 5.0 seconds = 1028.451 FPS
5143 frames in 5.0 seconds = 1028.540 FPS
5141 frames in 5.0 seconds = 1028.198 FPS
5141 frames in 5.0 seconds = 1028.053 FPS
5138 frames in 5.0 seconds = 1027.424 FPS
5137 frames in 5.0 seconds = 1027.205 FPS
5129 frames in 5.0 seconds = 1025.790 FPS
5082 frames in 5.0 seconds = 1016.370 FPS
5081 frames in 5.0 seconds = 1016.196 FPS
5085 frames in 5.0 seconds = 1016.965 FPS
5082 frames in 5.0 seconds = 1016.380 FPS
5089 frames in 5.0 seconds = 1017.599 FPS
5116 frames in 5.0 seconds = 1023.139 FPS
5084 frames in 5.0 seconds = 1016.766 FPS
5084 frames in 5.0 seconds = 1016.654 FPS
5084 frames in 5.0 seconds = 1016.721 FPS
5087 frames in 5.0 seconds = 1017.227 FPS
5066 frames in 5.0 seconds = 1013.196 FPS
5114 frames in 5.0 seconds = 1022.631 FPS
5122 frames in 5.0 seconds = 1024.343 FPS
5104 frames in 5.0 seconds = 1020.688 FPS
5081 frames in 5.0 seconds = 1016.013 FPS
5086 frames in 5.0 seconds = 1017.018 FPS
5097 frames in 5.0 seconds = 1019.325 FPS
5087 frames in 5.0 seconds = 1017.330 FPS
5087 frames in 5.0 seconds = 1017.315 FPS
5084 frames in 5.0 seconds = 1016.749 FPS
5084 frames in 5.0 seconds = 1016.639 FPS
5086 frames in 5.0 seconds = 1016.997 FPS
5077 frames in 5.0 seconds = 1015.357 FPS
5088 frames in 5.0 seconds = 1017.456 FPS
5087 frames in 5.0 seconds = 1017.210 FPS
5086 frames in 5.0 seconds = 1017.077 FPS
5085 frames in 5.0 seconds = 1016.908 FPS
5087 frames in 5.0 seconds = 1017.343 FPS
5084 frames in 5.0 seconds = 1016.747 FPS
5081 frames in 5.0 seconds = 1016.125 FPS
5087 frames in 5.0 seconds = 1017.315 FPS
5094 frames in 5.0 seconds = 1018.730 FPS
5095 frames in 5.0 seconds = 1018.897 FPS
5097 frames in 5.0 seconds = 1019.349 FPS
5081 frames in 5.0 seconds = 1016.101 FPS
5096 frames in 5.0 seconds = 1019.083 FPS
5095 frames in 5.0 seconds = 1018.997 FPS
5092 frames in 5.0 seconds = 1018.271 FPS
5114 frames in 5.0 seconds = 1022.714 FPS
5085 frames in 5.0 seconds = 1016.869 FPS
5085 frames in 5.0 seconds = 1016.954 FPS
5045 frames in 5.0 seconds = 1008.955 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 781344 requests (780203 known processed) with 0 events remaining.


y ahora? ;)

---

### Post by josecuervo86 on 2009-04-18
y.. los frames estan en lo que esperaría para una placa on-board. Asique claculo que debe venir por el lado de soft.

Proba instalando este paquete (desde terminal o synaptic): **ubuntu-restricted-extras**
Te doy la forma por terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Despues proba reproducir un video y un mp3 y conta como te fue

---

### Post by fortux on 2009-04-18
muchas gracias jose!

mientras se baja todo...

podrias explicarme brevemente que fue lo que hice??
jaja

 quiero aprender... y a penas termine de bajar todo te comento los resultados...

---

### Post by josecuervo86 on 2009-04-18
> **fortux said:**
> muchas gracias jose!

mientras se baja todo...

podrias explicarme brevemente que fue lo que hice??
jaja

 quiero aprender... y a penas termine de bajar todo te comento los resultados...

Glxgears te dice cuantos FPS (frames per second = cuadros por segundo) esta dandote la placa de video. Yo con una 8400gs tengo alrededor de 1700fps, o sea que 1000fps estan bien para una placa on-board.

El comando lspci (list pci o listener pci, no me acuerdo ahora) te dice que hardware te reconoce el sistema. Otro es lsusb que te dice que dispositivos tenes conectados por usb.

Con apt-get te conectas a los repos de Ubuntu, y podes descargarte los paquetes que te hagan falta. 

Un usuario un poco mas tecnico seguramente te va a explicar mejor cada término, pero mas o menos eso es lo que acabas de hacer ;)

---

### Post by fortux on 2009-04-18
jose...

ya termino de instalar todo, pero me salio una pantalla azul que dice esto

mirar la foto


espero que salga la foto, que hago??

---

### Post by josecuervo86 on 2009-04-18
Nada, pone aceptar y listo. Por lo que vi te dice que bajo una tipografia de Debian. Es solo para avisarte si la queres usar, como tenes que hacer ;)

---

### Post by fortux on 2009-04-18
buenas!!

A pesar de haber instalado todo lo que se me dijo...

sigo teniendo problemas... la pantalla del video se ve verde como con lineas verticales

lo comico es que cuando tomo una captura lo verde desaparece, aca les dejo una captura,

alguna sugerencia??

muchas gracias!

---

### Post by josecuervo86 on 2009-04-18
En el vlc anda a tools > preferences > video y en donde dice output pone x11

En el hardware parecieras no tener problemas. Los mp3 se escuchan bien??

---

### Post by fortux on 2009-04-18
muchas gracias!!!

ahora se ve bien!

con respecto al audio se escucha bien, pero como con pequeños saltos... muy pequeños...

tanto cuando veo un video, como cuando escucho un mp3...

que reproductor me recomendas? o se puede solucionar eso?

---

### Post by josecuervo86 on 2009-04-18
Me alegro flaco! por lo menos pudimos sacar adelante el tema!

Te pido una cosita mas. Proba ver los videos en Totem (Aplicaciones > Sonido y video > Reproductor de películas Totem)

No tengo ni idea que puede llegar a ser lo del audio. Capaz que alguien con mas experiencia te puede llegar a tirar una data. Proba reproduciendolo con Rhythmbox (Aplicaciones > Sonido y video > Reproductor de musica Rhytmbox)

Sabes que pasa, es que estoy pensando que el culpable es vlc. Por eso, con esto lo vamos a descartar o ratificar.

Yo te recomiendo Songbird para musica, esta bastante bueno y esta hecho sobre el motor de mozilla (gecko) pero es medio pesadito. Para peliculas Totem anda bien, aunque vlc es uno de los que mas utilizo

---

### Post by fortux on 2009-04-18
muchas gracias jose!

te debo una...

el reproductor anda bien.. pero no me gusta mucho... ya me voy a buscar alguno jaja

que sigas muy bien!

saludos!

---

### Post by josecuervo86 on 2009-04-18
De nada capo! Es verdad, no son la joya del diseño las interfaces, pero lo bueno es que son livianitos y andan realmente bien!

Busca tranqui, que seguro alguno vas a encontrar. Para música Amarok anda muy bien tambien!

Saludos!

---

