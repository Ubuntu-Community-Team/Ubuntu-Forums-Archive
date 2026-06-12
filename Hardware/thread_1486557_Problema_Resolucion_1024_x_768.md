---
title: "Problema Resolucion 1024 x 768"
date: 2010-05-18
forum: Hardware
---

### Post by warmen on 2010-05-18
[SIZE=2]Hola soy nuevo en ubuntu

y tengo un problema

resulta que tengo una tarjeta nvidia geforce fx 5200 y quiero configurar la resolucion 1024 x 768
sin driver de video tengo esa resolucion pero cuando instalo los controladores version 173 son los que me recomienda ubuntu que instale. cuando instalo estos driver la resolucion de mi pantalla baja a 600 x 400

la version del ubuntu que ocupo es la 10.04

ojala me puedan ayudar con mi problema porque quiero ocupar la resolucion 1024 x 768 en mi pc


este mi xorg creo q se yama asi XD
sorry pero solo llevo una semana con linux perdonen mi novatez

[/SIZE]   	 	 	 	 	 	  [SIZE=2]Section "Screen"  [/SIZE]
 [SIZE=2]        Identifier      "Default Screen"  [/SIZE]
 [SIZE=2]        DefaultDepth    24  [/SIZE]
 [SIZE=2]EndSection  [/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Section "Module"  [/SIZE]
 [SIZE=2]        Load    "glx"  [/SIZE]
 [SIZE=2]EndSection  [/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Section "Device"  [/SIZE]
 [SIZE=2]        Identifier      "Default Device"  [/SIZE]
 [SIZE=2]        Driver  "nvidia"  [/SIZE]
 [SIZE=2]        Option  "NoLogo"        "True"  [/SIZE]
 [SIZE=2]EndSection[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Section "Screen"  [/SIZE]
 [SIZE=2]	Identifier	"Default Screen"  [/SIZE]
 [SIZE=2]	DefaultDepth	24  [/SIZE]
 [SIZE=2]EndSection  [/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Section "Module"  [/SIZE]
 [SIZE=2]	Load	"glx"  [/SIZE]
 [SIZE=2]EndSection  [/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Section "Device"  [/SIZE]
 [SIZE=2]	Identifier	"Default Device"  [/SIZE]
 [SIZE=2]	Driver	"nvidia"  [/SIZE]
 [SIZE=2]	Option	"NoLogo"	"True" [/SIZE]
 [SIZE=2]EndSection  [/SIZE]
 [SIZE=2]

bueno ojala me puedar ayudar con al tuto para solucionar mi problema

grax a todos ^^
[/SIZE]

---

### Post by bichopro on 2010-05-18
El recomendado en 10.04 no es la version 173, mas abajo esta la recomendada que no dice el numero pero es la version 195.36.15
intenta isntalar esa primero y avisa si siguen los problemas

---

### Post by warmen on 2010-05-18
> **bichopro said:**
> El recomendado en 10.04 no es la version 173, mas abajo esta la recomendada que no dice el numero pero es la version 195.36.15
intenta isntalar esa primero y avisa si siguen los problemas

[SIZE=2]
ese controlador no es compatible con la nvidia geforce 5200[/SIZE]

---

