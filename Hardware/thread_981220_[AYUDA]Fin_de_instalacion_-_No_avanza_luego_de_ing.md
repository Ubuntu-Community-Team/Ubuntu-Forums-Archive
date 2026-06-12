---
title: "[AYUDA]Fin de instalacion - No avanza luego de ingresar el user/pwd"
date: 2008-11-13
forum: Hardware
---

### Post by PiolaBagio on 2008-11-13
Buenas tardes amigos linuxeros, este es mi segundo post que hago, pero en este post vengo un poco mas adelantado gracias a dios.
Voy a mi problema.

Pude instalar ubuntu al fin! Probe miles de veces y lo pude instalar. Ahora el problema es el siguiente.

Entro a Ubuntu, Carga, todo bien, pongo nombre de usuario y contraseña, apreto enter, y deja de cargar la pc, aparece un fondo naranja y el mouse y nada mas, queda ahi, puedo mover el mouse pero la pc no sigue cargando..

Algun motivo o idea y si puede ser arreglo?

PD: No aparece la barra de inicio ni nada, solo pongo el usuario y contraseña, y pasa a una pantalla naranja y ahi queda..

Cualquier pregunta diganme, hago lo imposible por tener ubuntu..

Saludos.-


Mi pc:

Intel Inside Celeron D 2.6
Memoria Kingstone 512mb (en 1 slot)
Disco duro de 80 Gb
Placa madre Asrock P4i45GV R.5
Placa de video GeForce 5500 128mb.

---

### Post by faktorqm on 2008-11-14
Hola, no tendras un problema con la placa de video? Es lo unico que se me ocurre... 

Arranca la compu, pone user, pass y cuando se te ""cuelgue"" apreta CTRL + ALT + F2.
Te tira a una pantalla negra que se llama terminal. Ahi solo podes escribir comandos, asi que no es grafico.

Ahi pone:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Entonces te abre una "ventana" en modo texto y ahi elegis el driver de la placa, le pones "vesa" (capaz te aparece nv, o nvidia) y listo. 

Despues cuando termina escribis:

```
sudo /etc/init.d/gdm restart
```

y eso te reinicia la parte grafica. Ahi deberias ver algo. Si no por las dudas reinicia. Si no llegas a ver nada, tambien puede ser un problema de resolucion. SIN poner usuario y contraseña, podes probar de apretar CTRL + ALT + + o CTRL + ALT + - para subir y bajar la resolucion al instante.

Espero que sea eso. Instalaste 8.10? sino proba de instalarte ubuntu 8.04 pero alternate cd. salu2!

---

