---
title: "Ayuda!, como instalar fglrx"
date: 2009-06-19
forum: Hardware
---

### Post by Fistandantilus on 2009-06-19
Hola a Todos!, 

Ayer al fin pude instalar la ver 9.04 y ahora estaba configurando e instalando todo lo q necesito.
El problema q tengo es q no puedo instalar los controladores propietarios de ATI, los fglrx. 

No los necesito por para activar la aceleracion por hardware, xq por suerte ya la tenia habilitada desde el live-cd, si no para compara performance para juegos.

Tengo una ATI Radeon 9600Pro con 256Mb, el glxgears me tira 1300/1400 de fps mientras que en Ubuntu 7.10 me tiraba arriba de 1800 fps(con los libres)... 

Por otro lado los necesitaba xq juegos q quiero ejecutar con el wine(Lineage 2) y me dice q tengo mal instalada mi placa de video Nvidea (?)...

Probé de instalarlos desde Sistemas -> Administracion -> Controladores de Hardware, pero me dice que no estoy usando ningun controlador privativo... si ya se, eso es lo q quiero! :S :S :S

  También probé de descargarlo por mi cuenta el fglrx y de toquetear el xorg.conf, pero termino en un desastre que se me colgaba la maquina al iniciar el gdm y lo termine desinstalando en linea de comando...

Alguien tiene alguna idea de como tengo q hacer para levantar el fglrx???

Saludos!

---

### Post by Fistandantilus on 2009-06-20
Nadie tiene idea de como puedo hacer para instalar los fglrx??? U_U

---

### Post by Hei Ku on 2009-06-20
Los fglrx no sirven para tu modelo de placa. Tu unica opcion son los drivers libres. Al menos desde la version 9.04 en adelante.

---

### Post by Fistandantilus on 2009-06-20
Uy q bajon.... :(

Sabes con que opciones en el xorg.conf le puedo mandar para subir los fps?... me parece muy raro q de por si en el 7.10 me tire mas fps q en el 9.04(los 2 pelados sin tocar ninguna conf, directamente desde live-cd).

Saludos

---

### Post by Hei Ku on 2009-06-20
Posteá tu xorg.conf y lo vemos.

En este subforo hay un sticky sobre hardware en el que puse el link a la wiki del driver libre de ATI. Ahi tiene informacion sobre parametros para agregar que la pueden hacer mas rapida.

---

### Post by Fistandantilus on 2009-06-21
No pude encontrar tu styky sobre ati, pasame el link pliz.

este es mi xorg.conf:

```

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```Como se puede apreciar, es un xorg pelado.

Saludos.

---

### Post by Hei Ku on 2009-06-21
Esta es la wiki sobre el driver Radeon, el driver libre para placas ATI.

[https://wiki.ubuntu.com/RadeonDriverHowto](https://wiki.ubuntu.com/RadeonDriverHowto)

A lo ultimo tiene varios tips para aumentar la performance.

---

