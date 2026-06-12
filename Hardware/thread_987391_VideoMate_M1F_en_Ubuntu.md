---
title: "VideoMate M1F en Ubuntu"
date: 2008-11-19
forum: Hardware
---

### Post by Josecanalla on 2008-11-19
Hola, me compré una placa sintonizadora, la VIDEOMATE VISTA M1F.

Obviamente sus drivers son para Windows, ¿hay alguna forma de hacerla funcionar en Ubuntu? 

Muchas gracias, saludos. 

José.

---

### Post by Hei Ku on 2008-11-19
Postea el resultado del comando lspci

---

### Post by Josecanalla on 2008-11-24
Hace poco que tengo Linux, es decir, mucho no entiendo todavía.

¿Cómo hago eso?

---

### Post by sajnox on 2008-11-24
Apretas alt + f2 y escribis gnome-terminal se te abre una pantalla como la del viejo DOS y ahi escribis 

```
lspci
```

Lo que responder por ingresar ese comando  lo copias y pegas aca en tu respuesta.

Importante: Desde la terminal (pantalla DOS) no para copiar y pegar lo podes hacer con click derecho del mouse o usando shift + ctrl + c para copiar y shift + ctrl + v para pegar

---

### Post by Josecanalla on 2008-12-03
administrador@administrador-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:07.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
00:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Intenté eso de copiar y pegar como dijiste vos, pero no pude. Bah no me salía nada, si querés decime de nuevo como es y lo hago como decís vos.

---

### Post by faktorqm on 2008-12-04
Está soportada por lo general este tipo de placas capturadoras, buscando en google el resultado con fecha mas reciente ... [http://chrisyagami.blogspot.com/2008/08/instalar-capturadora-saa7133saa7135.html](http://chrisyagami.blogspot.com/2008/08/instalar-capturadora-saa7133saa7135.html)

Lo de copiar y pegar, no te funciona por que no seleccionaste (algunos lo llaman "pintar") con el mouse lo que queres copiar. Si no podes ir a edicion -> copiar o edicion -> pegar y ahi vas a ver las teclas de acceso rapido.

Salu2!

---

### Post by Josecanalla on 2008-12-20
Ahora voy a probar lo que dice en esa página y después te cuento.

Gracias che!

---

### Post by c4d0rn4 on 2008-12-21
> **sajnox said:**
> Apretas alt + f2 y escribis gnome-terminal se te abre una pantalla como la del viejo DOS y ahi escribis 

lspci

Lo que responder por ingresar ese comando  lo copias y pegas aca en tu respuesta.

Importante: Desde la terminal (pantalla DOS) no para copiar y pegar lo podes hacer con click derecho del mouse o usando shift + ctrl + c para copiar y shift + ctrl + v para pegar

En mi opinión lo MÁS cómodo a la hora de seguir guías o copiar y pegar en ubuntu es usar el tercer botón del mouse.

Cuesta un poquitin acostumbrarse pero es genial.

[B]_1._ subrayan lo que necesitan copiar y pegar
_2._ van a donde necesitan pegar el texto y dan click con la ruedita (tercer botón)
[/B]
FIN!

Lo importante es que solo se va a pegar lo _último_ seleccionado. También hay que tener en cuenta que solo lee lo último seleccionado.
Ejemplo, en un tab de firefox selecciono ddd, luego en pidgin selecciono fff, cuando doy click con el botón del medio aparece fff aunque en firefox siga seleccionado también ddd.

espero una tonelada de thanks por este dato ajaj xD :lolflag:

*_tip extra_: si se selecciona una linea y el inicio de la otra (o sea el enter que hace el salto de la línea) cuando lo ponen en la terminal, se pega el comando y se ejecuta (por el enter al final). De ese modo se puede hacer una guía usando solo el mouse sin meter mano en el teclado jajaj xD*

---

### Post by Josecanalla on 2008-12-22
Ya fue el primer thank mío jajaja. La verdad muy copado, eh.

---

### Post by DumLoco on 2009-05-10
Hola! Leí ese tutorial que me postearon y lo seguí, pero cuando llega el momento de hacer que tvtime use la placa, pongo

sudo modprobe card=65 tuner=54 

Y me tira

FATAL: Module card=65 not found.


Es una Compro Videomate M1F.
Qué numeros tendría que poner ahi? 

Gracias!

---

### Post by Hei Ku on 2009-05-10
Te falto poner el modulo.

sudo modprobe saa7135 card=65 tuner=54

---

### Post by DumLoco on 2009-05-10
FATAL: Module saa7135 not found.

=s

---

### Post by Hei Ku on 2009-05-11
Proba con saa7134. Si no, no sé.

---

### Post by DumLoco on 2009-05-11
Con 7134 no tira error, pero tampoco pasa nada... Es como si se quedara haciendo algo para siempre (si quiero cerrar la terminal me dice que hay un proceso activo :()

---

### Post by Hei Ku on 2009-05-11
Me parece que deberías fijarte en este foro que hay varios threads sobre sintonizadoras, y estan mas explicados que el blog que usaste vos, que tiene varios errores chapuceros.

---

### Post by gThumb on 2010-11-13
Linux kernel does not correct support this device. 
My Linux is Ubuntu.
Today, this device works only TV or only radio (Or you must patch your Linux kernel).

[http://www.comprousa.com/forums/viewtopic.php?p=10641#p10641](http://www.comprousa.com/forums/viewtopic.php?p=10641#p10641)

---

