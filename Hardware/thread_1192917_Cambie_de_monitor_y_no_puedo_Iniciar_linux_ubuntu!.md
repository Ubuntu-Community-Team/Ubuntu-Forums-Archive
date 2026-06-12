---
title: "Cambie de monitor y no puedo Iniciar linux ubuntu!"
date: 2009-06-20
forum: Hardware
---

### Post by migga on 2009-06-20
Hola gente, Soy nuevo en esto,
 Todo venia funcionando joya, hasta que cambie el monitor. Tenia un monitor muy viejo Samsung de 17' y cuando le puse un LCD View Sonic de 19' cargaba todo bien, pero no me a la parte donde pongo mi usuario y contraseña.... me tiraba una pantalla, como que la configuracion de pantalla habia cambiado, y no podia entrar...

Me daba varias opciones, pero intente todo y nada funciono.

Cuando me resigne, volvi a enchufar el monitor viejo Y ME TIRABA EL MISMO PROBLEMA.
reinstale la ultima version de linux, pero de vuelta con el monitor viejo. 

El problema es que en un par de dias me voy a comprar un monitor LCD y no quiero que me pase lo mismo,
 ¡¿¿¿¿¿Qué puedo hacer cuando me pase eso de vuelta????!

Gracias!

---

### Post by pablo.s on 2009-06-20
El problema consiste en que
las resoluciones de pantalla
y tasa de refresco de los
monitores se guardan en un
archivo que se llama xorg.conf
y suelen ser datos fijos, porque
el 99 por ciento de la gente no
cambia de monitor seguido, sino
que pasan varios años hasta que
un monitor se agota y 
eventualmente estira su pata.

Lo que va a tener que hacer va
a ser modificar este archivo 
colocandole los datos de la resolución
y tasa de refresco a mano o
invocando un comando que te
reconfigura todo:

sudo dpkg-reconfigure xserver-xorg -phigh

---

### Post by migga on 2009-06-20
Joya. Pero lo tengo que hacer antes de enchufar el nuevo monitor?, porque sino al no poder entrar tmp puedo usar el terminal...

Gracias!

---

### Post by pablo.s on 2009-06-20
Hay formas para hacerlo
antes y hay formas para 
hacerlo después.
Sin que inicie el servidor
X tambien se puede hacer.
Cuando llegue el momento
y tengas a mano el manual
del monitor, te vamos a 
ayudar con la tarea.

---

### Post by gmunioz on 2009-06-21
Hola mig...:

Al iniciar el ordenador pulsa escape.

Aparecerá el menu del Grub.

Elige una opción que diga al final (Recovery Mode)

En el submenu emergente, elige fix de las graficas.

Esto con el monitor nuevo colocado, te corregirá las

gráficas al nuevo monitor y tarjeta gráfica, que se

pudieran haber cambiado.

Luego reinicia, y todo tendría que funcionar correctamente.

---

### Post by migga on 2009-06-25
Joyaaaaaaa che, buenisimo, logre entrar, el GRAN PROBLEMA AHORA, es que no puedo cambiar la configuaracion de pantalla,... y que cada vez que renicio me tira otra vez la ventana esa de que la configuaracion cambió (Ubuntu is running in low.graphics mode), pero metiendo mano puedo entrar.

EL tema es que intenté todo lo que vi en internet,
intentar cambiar  mi xorg.conf
puse algunos otros parametros en el Terminal que decian que te lo configuraba automaticamente...
Cambié el Gestor de paquetes Synaptic para que me tire otras actualizaciones, y nada. (dsp lo puse todo como estaba....

La verdad ya no se mas que hacer.
Un amigo me dijo de reinstalar Ubuntu, pero no me funciona bien la lectora y me robaron el pen drive... malísimo... 

EN fin si sabes/en alguna forma de ayudarme Bienvenido sea!

Muchas gracias por la ayuda hasta el momento!

Miguel

---

### Post by gmunioz on 2009-06-26
Hola mig...:

1- "...Un amigo me dijo de reinstalar Ubuntu..."

¿Quién, Guillermo Puertas? en GnuLinux las cosas se

arreglan, no se reinstala el sistema como en Windows.

2- "..(Ubuntu is running in low.graphics mode)..."

Esto significa que tienes una placa de video, que 

aparentemente requiere drivers privativos para funcionar

a pleno.

3- Sería conveniente que informes:

a- La versión de Ubuntu que usas.

b- Tarjeta gráfica, marca y modelo

c- Frecuencias de trabajo y resolusión del monitor

---

### Post by migga on 2009-06-27
a- La versión de Ubuntu que usas: Ubuntu Desktop Edition 9.04

b- Tarjeta gráfica, marca y modelo: Es Onboard y el mother es un **ASus P5KPL-AM SE, **No se como fijarte que modelo es.

c- Frecuencias de trabajo y resolución del monitor: No tengo idea a que te referis con frecuencia de trabajo, pero la resolución me deja 800x600 y una mas chica, pero como es un **LCD View Sonic de 19' **La resolución que le pondría es 1024 x 700 y pico, o alguna mas. 

Mañana me traen el pendrive y reinstalo ubuntu. Ya fue, mucho bardo al ****.

Gracias por la buena onda.

Saludos

---

### Post by gmunioz on 2009-06-27
Hola mig....:

Tu Tarjeta de video es:

```
VGA Integrated Intel Graphics Media Accelerator (Intel® GMA 3100)
Max. resolution:2048x1536X32bpp, Horizontal:127.5KHz Vertical:85Hz
```

Tu Monitor tiene estas características:

```
LCD 	Tipo 	LCD WSXGA de matriz activa TFT a color de19"
Área visual 	16,1" horizontal x 10,0" vertical; 19,0" diagonal
Resolución óptima 	1440x900
Análoga  	RGB análoga (75 ohms, 0,7 Vp-p)
Digital 	Fh: 30~82kHz, Fv: 50~75Hz
Sincronización 	H/V separada (TTL)
```

De acuerdo con estos datos en tu archivo /etc/X11/xorg.conf

tendrías que tener:

En la sección: Screen

 ```
Section "Screen"
	Identifier	"tus datos"
	Device		"tus datos"
	Monitor		"tus datos"
	[B]DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" 
	EndSubSection
EndSection[/B]
```

En la seccion monitor:

```
Section "Monitor"
	Identifier	"tus datos"
        [B]HorizSync   30-82
        VertRefresh 50-75[/B]
	Option		"tus datos"
EndSection
```

Y con esto tendrías que tener tus graficas funcionando.

---

