---
title: "[SOLUCIONADO] No puedo poner la resolucion de mi monitor a 1280x1024"
date: 2009-06-27
forum: Hardware
---

### Post by F.Y.N. on 2009-06-27
Holanda, despues de que en otro tema me recomendaran actualizar mis drivers de nvidia a la ultima version, el monitor se me ve a 1024x768 y **no lo puedo hacer andar a 1280x1024 como lo he tenido siempre**.

Mi tarjeta de video es una **GeForce 6200** (los drives funcionan bien; en nvidia X Server Settings no tengo errores, pero la resolucion maxima es 1024x768 ).
Mi monitor es un **ViewSonic VE710b**

He estado editando el xorg.conf (con como 20 guias distintas) pero sigo igual, aca esta por si acaso:

> Section "Device"
Identifier    "Configured Video Device"
Driver        "nvidia"
EndSection

Section "Monitor"
Identifier    "Configured Monitor"
Option        "DPMS"
EndSection

Section "Screen"
Identifier    "Default Screen"
Device        "Configured Video Device"    
Monitor        "Configured Monitor"
DefaultDepth    24
SubSection    "Display"
Depth        24
Modes        "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Con "dpkg-reconfigure xserver-xorg" tampoco me funciono.

Salu1+1

---

### Post by gmunioz on 2009-06-27
Hola fyn....:

Hasta donde recuerdo, la estructura de /etc/X11/xorg.conf

respecto de los modes que soporta un monitor se determinan

con estas líneas:


```
Section "Screen"
         Identifier "Default Screen"
         Device "Configured Video Device"
         Monitor "Configured Monitor"
         DefaultDepth 24

	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" 
	EndSubSection
EndSection

```

Poniendo únicamente la que quieres por defecto no le das opción

de cambio, eso estate seguro de que es la correcta, pues no solo

puedes perder las gráficas, algo solucionable con el fix de ellas,

sino que se puede dañar el monitor al forzarlo.

Tambien sería conveniente que aclares las frecuencias que soporta

tu monitor, estan en la parte trasera o en su sitio web, para dejar

la sección así:

```
Section "Monitor"
         Identifier "Configured Monitor"
         HorizSync   30-111
         VertRefresh 50-160
         Option "DPMS"
EndSection
```

---

### Post by nopersona on 2009-06-27
Y qué dice el X Sever display configuration? extraño tu caso, yo tengo nvidia y el xserver de nvidia se encarga de todo. 

A todo esto, cuál versión de driver estas usando, la 180 o la 185?

---

### Post by F.Y.N. on 2009-06-27
Tranquilo, ya lo arregle poniendo HorizSync y VertRefresh, lo demas de modes lo deje tal cual.


Salu1+1

---

### Post by nopersona on 2009-06-28
> **F.Y.N. said:**
> Tranquilo, ya lo arregle poniendo HorizSync y VertRefresh, lo demas de modes lo deje tal cual.


Salu1+1

Entonces un lindo (SOLUCIONADO) espera en el titulo.

Saludos.

---

