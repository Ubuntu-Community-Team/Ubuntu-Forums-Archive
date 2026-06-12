---
title: "Resolucion de pantalla en hardy"
date: 2008-05-26
forum: Hardware
---

### Post by ramiro_md on 2008-05-26
Hola amigos, esta tarde estaba con tiempo (cuando no :P) y decidi migrar a ubuntu 8.04. El tema es el siguiente, una vez instalado las unicas resoluciones de pantalla q me figuran son: 640x480 y 600x800..un desastre..ya que uso la 1024x780 (creo q es 780), ya tengo los controloradores de mi nvidia 6100 instalados, y desde el nvidia settings no puedo hacer mucho, xq no me deja cambiar nada.
Si alguien sabe de como solucionarlo, se lo agradceeria, ya que quiero usar ubuntu 8.04 para compararlo con el viejo 7.10 que nunca me trajo inconvenientes jejeje.

Si le sisrve de algo tengo un monitor lg 710E se 17 pulgadas..

---

### Post by ramiro_md on 2008-05-26
Este es mi xorg.conf x si les sirve de algo...


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by faktorqm on 2008-05-26
```
sudo displayconfig-gtk
```

---

### Post by ramiro_md on 2008-05-26
Bueno capo, un par de cosas para decirte...
1) IDOLO, siempre salvandome las papas xD
2) anduvo perfecto puse esa linea de comandos y configure mi monitor, y el refresco. Anda joya ahora.
3)Hay algun curso u algo donde capaciten para operador de linux ?...xq realmente yo leo algunos threads y las respuestas que dan, gente que realmente la tiene muy clara..y me gustaria aprender algo ya que soy algo novato con linux. (en la plata obvio)
Bueno desde ya muchisimas gracias capo.


Pincha te llevo en el alma y cada dia te quiero mas !

---

### Post by ramiro_md on 2008-05-26
Bueno capo, un par de cosas para decirte...
1) IDOLO, siempre salvandome las papas xD
2) anduvo perfecto puse esa linea de comandos y configure mi monitor, y el refresco. Anda joya ahora.
3)Hay algun curso u algo donde capaciten para operador de linux ?...xq realmente yo leo algunos threads y las respuestas que dan, gente que realmente la tiene muy clara..y me gustaria aprender algo ya que soy algo novato con linux. (en la plata obvio)
Bueno desde ya muchisimas gracias capo.


Pincha te llevo en el alma y cada dia te quiero mas !

---

### Post by faktorqm on 2008-05-27
La verdad desconozco si existe, y aparte no vivo en la plata :P, de todas maneras para mi no tiene mucho sentido. Yo no fui a ningún lado, y uso ubuntu desde 2005 mas o menos, y antes usaba red hat. (6.2, luego 7, luego 9.0) tambien pasé por mandrake...
y la verdad no hay nada mas interesante que sentarte y leer la documentacion de las cosas. Asi es la manera mas "dura" de aprender, y la mas larga, y despues aprendes "mirando", y aparte creo que te tiene que gustar mucho para aprender mucho. Sino siempre terminas diciendo " uhh esto es un bardo nuevo..."
Aparte primero siempre sirve aprender "gnu/linux" digamos, no nos olvidemos que ubuntu solo es una distribucion, con esto quiero decir, por ejemplo, el tar, no solo esta en ubuntu, sino en todas. o el sudo, o el directorio /etc. 

[COLOR="Red"]Somo' campeones del[/COLOR] mundo, somo' el orgullo[COLOR="#ff0000"] de la Ciudad!![/COLOR]
[COLOR="#ff0000"]Pincha te llevo en[/COLOR] el alma y cada día [COLOR="#ff0000"]te quiero más!![/COLOR]

---

### Post by faktorqm on 2008-05-27
che anda pa' atras el foro este.... doble post todo las veces...

---

### Post by Simbiosys on 2008-05-28
> **faktorqm said:**
> ```
sudo displayconfig-gtk
```

1- Buenas, tengo algunas consultas porque cuando leí este thread me entró la duda y ejecuté el comando a ver que pasaba... se abrió la pantalla de configuraciones y elegí un monitor de Dell (probé varios y la mayoría traian problemas, actualmente estoy trabajando con monitor plug `n play)
Mi idea es poder configurar el monitor que tiene mi laptop (inspiron 1525) para que me figuren los modos de pantalla que sí puedo utilizar y poder elegir.

2- Consultando con otro compañero de trabajo que tiene ubuntu en su equipo, nos dimos cuenta que el tiene en el menú Sistema -> Administración -> Pantallas y gráficos.. (yo no lo tengo y edité el menú pero tampoco figura para activarlo) -> las diferencias es que yo tengo ubuntu 8.04 HH y la versión 7.10 GG

Me dijeron que lo mejor es editar un archivo xorg.conf (o algo así) y ahí mismo parametrizar el monitor según corresponda. Las especificaciones técnicas las tengo en el manual... de ser necesario las posteo.

Muchas gracias!!!

---

### Post by faktorqm on 2008-05-29
Bueno, no entendi que queres hacer. casi no termino el primario por castellano, al final aprobe, despues me lleve a marzo directo castellano de segundo y tercero, y a diciembre la de primero, pero tu redaccion me supero :lolflag: (cabe destacar que ocurria lo contrario en matematica y afines, no sea que piensen que soy un burro :KS)

Si tenes 7.10, tenes que tocar el xorg.conf y agregar dos lineas a la seccion monitor, pero cuando me confirmes lo vemos bien.

Si tenes 8.04, tenes que morir en el displayconfig-gtk, pero que a su vez tambien te deja poner las frecuencias que se te cantan, y hasta te deja poner el .inf del monitor si es que no tiraste el cd que acompaña al monitor.... :P

Cualquiera sean los dos casos, confirma. Salu2!!!!

---

### Post by Simbiosys on 2008-05-29
Tengo 8.04 HH, pero intenté con el displayconfig-gtk y siempre la termino arruinando. (eligiendo monitores)

Las resoluciones me las deja modificar joya, se ve perfecto... (pero con monitor plug and play) lo que quería yo era configurar mi monitor... pero se ve que no le gusta.

Mi portatil es Dell inspiron 1525. (no es que se vea mal, solo que quería configurar el monitor que corresponda...) perdón la mala redacción.

---

### Post by faktorqm on 2008-05-30
Hacé una cosa, dejalo en plug and play, pero ponele las frecuencias a mano vos y listo, es lo mismo. la horizontal y la vertical. Recien ahi elegis la resolucion. Salu2!!

---

