---
title: "Problemas Sound Blaster Live! Value"
date: 2008-06-03
forum: Hardware
---

### Post by juanzilla on 2008-06-03
Hola gente, nuevo en esto de ubuntu y el tema es que lo tengo instalado y despues de luchar con la placa de video pude configurarla como queria, ahora el tema es que la placa de sonido (las dos que tengo) no me las toma...
la que me gustaria que tomara de las dos es la soundblaster live! Value el problema es que NO LA VE ni nada... por favor, que alguien me ayude que no aguanto mas el GUINDOUS....

El ubuntu es un 8.04 x64 y la placa como dije antes Sound Blaster Live! Value de las viejitas... cualquier otra info que necesiten, pregunten...
gracias!

---------------------------------------------------------------------
S O L U C I O N:
--------------------------------------------------------------------

Bueno gente, como bien dijo el capo total de Anarko (Juan para los amigos :P) el tema ya esta solucionado., asi que les cuento como fue el tema y la solucion:

1- Primero instalar los correspondientes modulos del respectivo Kernel:
(Ej: linux-ubuntu-modules-2.6.24-18-generic en mi caso)
2- tirar por consola el comando "sudo depmod -ae"
3- Reiniciar.
4- Una vez reiniciado, abrir una consola y tirar el comando:
"asoundconf set-default-card live"
5- En la misma consola y tirar el comando:
"alsamixer" y subir el volumen a todos...
6- Reiniciar y subir el volumen desde el parlantito de al lado de el reloj.

Listop!!

Quiero agradecer muchisimo a Anarko que se puso las reeee pilas para ayudarme y sobre todo por poner la mejor buena voluntad del mundo para ayudarme...

GRACIAS Anarko!!!!

---

### Post by anarko on 2008-06-03
Que raro, yo tengo la misma placa Sound Blaster Live Value y anda 10 puntos, podras poner la salida del comando lspci.
Abris una terminal ( Aplicaciones-> Accesorios -> Terminal ) y pone "lspci" sin las comillas y pega el resultado.
Deberias ver que una de las lineas dice "Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)" o algo parecido.

---

### Post by juanzilla on 2008-06-03
Efectivamente, me la reconoce... :

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
03:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)


el problema es que aun asi, cuando voy a el parlantito de al lado del reloj y le hago click dice:

"The volume control did not find any elements and/or devices to control. This means either that you dont have the right gstreamer plugins installed, or that yo dont habe a sound card configurated.
You can remove the volume control from the panel by right clicking the spacker ucon on the panel and select "remove from panel" from the menu"...

otro cartel que suele tirarme es "NO gstreamer plugns and/or diveces found"

Que puedo hacer, tendra algo que ver conque mi micro es x64 ?

---

### Post by anarko on 2008-06-04
No el micro x64 no tiene nada que ver, yo tambien tengo hardi x64 y anda bien.
Evidentemente la placa esta ahi, por lo que pones del gstreamer, proba instalar desde sinaptic los gstreamer plugins, y ya que estas fijate si tenes instalado el alsa, el oss o el pulse-audio.

---

### Post by juanzilla on 2008-06-04
bueno, instale todo lo de alsa, todo lo de gstreamer y nada... todo sigue =

no hay alguna "panel de control -> sistema " tipo guindous que te permita ver las cosas que tenes instalada? o algo asi.. la verdad estoy cada ves mas frustrado...

---

### Post by anarko on 2008-06-04
No te frustres, TODO tiene solucion en linux ( y nunca es resintalar o un fallback a windows )
Te conteste el pm.


Instala el lshw-gtk con el sinaptic y ejecutalo desde una consola "sudo lshw-gtk", eso te muestra todo el hardware que tenes en la Pc y si tiene cargado el modulo correspondiente cargado.
A mi la Sb Live me dice que el modulo que esta usando es "snd_emu10k1": 
```

product: SB Live! EMU10k1
vendor: Creative Labs
bus info: pci@0000:05:08.0
version: 08
width: 32 bits
clock: 33MHz
capabilities:
	Power Management,
	bus mastering,
	PCI capabilities listing
configuration:
	driver: EMU10K1_Audigy
	latency: 32
	maxlatency: 20
	mingnt: 2
	module: snd_emu10k1


```

Si tiene el modulo cargado el problema tiene que ver con la configuracion del manejador de sonido que tengas instalado, alsa, oss, pulse-audio

---

### Post by juanzilla on 2008-06-04
tal y como lo suponias... parece no tener el modulo...:

```
product: SB Live! EMU10k1
vendor: Creative Labs
bus info: pci@0000:03:06.0
version: 08
width: 32 bits
clock: 33MHz
capabilities:
	Power Management,
	bus mastering,
	PCI capabilities listing
configuration:
	latency: 64
	maxlatency: 20
	mingnt: 2
this device hasn't been claimed
```

Ahora el tema es, como sigo?...

---

### Post by juanzilla on 2008-06-04
Bueno, gracias a la ayuda de anarko pude identificar el problema y solucionarlo...

Les cuento, el problema es que por alguna razon cuando instale el ubuntu no me instalo los modulos. ¿La solucion? bajar con el synaptic los modulos para mi kernel.
Es decir que busque en el sinaptyc "kernel + modules" y lo baje (esto lo pongo para el que esta mas perdido que yo) reinicie y listop.

Bueno, eso fue todo... gracias a anarko que se quedo hasta altas horas de la noche para ayudarme. CAPO!!!

---

### Post by pol666 on 2008-06-04
Yo tengo una Audigy y si bien me la tomaba me daba muchos problemas. Ahora tambien xD pero por suerte me la toma al toque lo que fue santo remedio fue desactivar el Chipset de sonido ON BOARD Intel que tiene la placa ASUS.

para eso reinicia la pc, pulsa Suprimir y bla bla bla, desactivas la placa on board y ahi vas a tener una vida mas placentera.... :)

---

### Post by xpelaox on 2008-06-04
Che, que raro! yo en mi otra compu tengo la misma placa y cuando instale Hardy no hizo problema... sera por que actualize de 7.10 a 8.04 ?

---

### Post by anarko on 2008-06-04
Jeje nos kedamos en el emesene hasta las 3:30 am pero quedo andando.
un adepto mas?

---

### Post by juanzilla on 2008-06-09
Bueno gente, como bien dijo el capo total de Anarko (Juan para los amigos :P) el tema ya esta solucionado., asi que les cuento como fue el tema y la solucion:

1- Primero instalar los correspondientes modulos del respectivo Kernel:
 (Ej: linux-ubuntu-modules-2.6.24-18-generic en mi caso)
2- tirar por consola el comando "sudo depmod -ae"
3- Reiniciar.
4- Una vez reiniciado, abrir una consola y tirar el comando:
   "asoundconf set-default-card live"
5- En la misma consola y tirar el comando:
   "alsamixer" y subir el volumen a todos...
6- Reiniciar y subir el volumen desde el parlantito de al lado de el reloj.

Listop!!

Quiero agradecer muchisimo a Anarko que se puso las reeee pilas para ayudarme y sobre todo por poner la mejor buena voluntad del mundo para ayudarme...

GRACIAS Anarko!!!!

---

### Post by berserk0015 on 2008-06-10
estoy teniendo el mismo problema. nada de audio. corri el comando "lspci" y lo q me da acerca de la sound card es "03:03.0 Multimedia audio controller: Creative Labs SB X-Fi". trate de seguir los pasos en el post anterior pero cuando llego a la parte de "alsamixer" me da un error q dice "alsamixer: function snd_ctl_open failed for default: No such device
berserk@berserk-desktop:~$ alsamixer". 

Me doy cuenta q la sound card no exactamente la misma y hay algo q estoy haciendo mal o halgo q no estoy haciendo. ayuda por favor!

---

### Post by ferreret on 2008-06-11
> **juanzilla said:**
> Bueno, gracias a la ayuda de anarko pude identificar el problema y solucionarlo...

Les cuento, el problema es que por alguna razon cuando instale el ubuntu no me instalo los modulos. ¿La solucion? bajar con el synaptic los modulos para mi kernel.
Es decir que busque en el sinaptyc "kernel + modules" y lo baje (esto lo pongo para el que esta mas perdido que yo) reinicie y listop.

Bueno, eso fue todo... gracias a anarko que se quedo hasta altas horas de la noche para ayudarme. CAPO!!!


Yo he instalado uno de los modulos y sigue sin funcionarme.

product: SB Live! EMU10k1
vendor: Creative Labs
bus info: pci@0000:00:0d.0
version: 0a
width: 32 bits
clock: 33MHz
capabilities:
	Power Management,
	bus mastering,
	PCI capabilities listing
configuration:
	driver: EMU10K1_Audigy
	latency: 64
	maxlatency: 20
	mingnt: 2
	module: snd_emu10k1

---

### Post by anarko on 2008-06-12
> **berserk0015 said:**
> estoy teniendo el mismo problema. nada de audio. corri el comando "lspci" y lo q me da acerca de la sound card es "03:03.0 Multimedia audio controller: Creative Labs SB X-Fi". trate de seguir los pasos en el post anterior pero cuando llego a la parte de "alsamixer" me da un error q dice "alsamixer: function snd_ctl_open failed for default: No such device
berserk@berserk-desktop:~$ alsamixer". 

Me doy cuenta q la sound card no exactamente la misma y hay algo q estoy haciendo mal o halgo q no estoy haciendo. ayuda por favor!

Fijate que lo que puso juan es solamente para SB Live.
En la parte donde hay que ejecutar el "asoundconf set-default-card Live" vos seguro tenes que poner otra cosa dependiendo de la placa que tenes, para eso ejecuar "asoundconf list" que te tira una lista de las placa reconocidas por el alsa.

Ej. En mi PC:
```
anarko@AnArKa:/$ asoundconf list
Names of available sound cards:
Live
CK804
UART
HDMI

```

---

