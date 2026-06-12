---
title: "problema con nvidea 5200 necesito ayuda!"
date: 2008-08-21
forum: Hardware
---

### Post by ezemillo on 2008-08-21
hola!
hoy llegue al dia que dije, ya esta me paso a linux no aguanto mas la inestabilidad de windows. ahora bien, me baje de la pagina el iso lo instale todo, cuando entre a ubuntu me fui a ver los estilos visuales y eso. decia q estaban deshabilitados, entonces los quize subir a medios.
ahi salto un cartelito que decia q necesitaba descargar los drivers.. tngo una gforce4 5200.. lo instalo, i me pidio que lo reinicie para q se acepten los cambios.. pero cuando la reinicie,me muestra la pantalla de bienvenida pero despues se va de rango el monitor y no se ve nada.. aparece un cartelito diciendo out of range, como q esta configurado a 75k y el monitor acepta hasta 70.. yy nose que hacer :S como puedo solucionar este problema? soi re noob en linux es la primera vez q lo uso!
muchas graciass x todo! :D

---

### Post by feche_mza on 2008-08-22
***mmmmm si logras abrir terminal teclea esto ***> gksu displayconfig-gtk***te va a brir una ventanita donde podes cambiar la resolucion (por defecto creo que es 1280x1024 en 50) me parece raro que este en 75 la tuya, o cuando arranque el grub en lugar de poner el kernel generico pone el modo de recuperacion, ahi te va a dar varias opciones, hay una que es ejecutar terminal como root, elejis esa y pones esto***> sudo dpkg-reconfigure -phigh xserver-xorg***eso te resetea la configuracion de las x, y si nada de eso funciona esperate unos dias que alguien mas aca te va a saber decir que hacer y como:) ***

---

### Post by faktorqm on 2008-08-22
mira yo no se que paso, yo anoche tipo 11 te habia respondido el post... pero ahora que no lo veo no se si lo soñe, si no lo postie, o si lo postie en otro thread... 
bue, te decia que arranques la compu, esperes a que se te salga de frecuencia y apretes la combinacion de teclas CTRL + ALT + + (tecla MAS) y/o CTRL + ALT + - (tecla MENOS) para subir y bajar la resolucion respectivamente. no importa que te quede en 800x600 la primera vez, una vez que entras apretas ALT + F2 y te va a aparecer una ventana de ejecutar, ahi pegas este comando:

```
gksu displayconfig-gtk
```

y te pide contraseña y te aparece un configurador de video como perfectamente dijo fede. Lo del dpkg--reconfigure blablabla no corre mas muchachos, o al menos con nvidia no anda. Salu2!

---

### Post by fgl82 on 2008-08-22
+1 @faktor, con lo de que que el reconfigure no funca

---

