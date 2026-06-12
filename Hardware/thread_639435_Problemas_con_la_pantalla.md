---
title: "Problemas con la pantalla"
date: 2007-12-13
forum: Hardware
---

### Post by soadfanatic on 2007-12-13
Hola ubuntu satisface mis expectativas ampliamente. tiene mejor rendimiento. y es editable casi por completo. aparte de su filosofia que le da otra sensacion al uso de la pc.
Este es post es porque tengo un problema con la pantalla. antes tenia como controlador en uso uno que se llamaba "intel experimental" pero lo cambie por el correspondiente a mi placa madre que es una M909G V5 y ahi comenzo el problema. cerre sesion y ya note los cambios de la resolucion ya que estaba en 2800x1024 y paso a 800x600. Pero cuando inicie sesion la pantalla estaba mas grande todabia. Osea estaba en 2800x1024 pero desde la perspectiva de 800x600. no cabe la pantalla en el monitor. y debo correrla con el mouse para llegar a las areas que nose ven. Ahora no puedo volver al controlador anterior. por mas que lo seleccione presiono aceptar y vuelve al controlador que me causa el problema. ademas cuando presiono el boton salir se cuelga la maquina y tengo que apagarla manualmente. hasta ahora no tube otro problema. agradeceria mucho su ayuda. hasta luego soadfanatic

---

### Post by User21 on 2007-12-13
Prometo ayudarte apenas llegue a mi casa! Tuve el mismo problema, de tener un escritorio mas grande que mi monitor! xD y debia moverlo con el mouse, jajaja, era frustrante y gracioso a la vez.

---

### Post by faktorqm on 2007-12-13
sobre el titulo del post: no tenes un problema en la pantalla, tenes un problema en la configuracion de la resolucion de la placa de video.

sobre el post: podes probar 2 cosas: ```
sudo dpkg-reconfigure xserver-xorg
```

para reconfigurar el X, o sino podes hacer desde una terminal:

primero hacemos un back-up para ke nada malo ocurra:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

ahora editamos el archivo:
```
sudo gedit /etc/X11/xorg.conf
```

y ahi ves el archivo directamente. 

si te mandas una macana y cuando arranca te muestra pantalla azul, te vas a la terminal, y escribis:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

y despues escribis ```
sudo /etc/init.d/gdm restart
```

y ahi te va a levantar otra vez con lo anterior.

SI TENES MAS DUDAS postea el contenido del archivo xorg.conf entre los tags de code POR FAVOR. salu2!

---

### Post by soadfanatic on 2007-12-17
muchas gracias por su ayuda. ya solucione mi problema

---

### Post by kligula on 2008-06-12
A mi no me funciona.. me sale lo siguiente

dpkg-query: parse error, in file `/var/lib/dpkg/status' near line 1:
 field name `
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

despues de eso utilizo el el comando sudo apt-get install xserver-xorg me sale que:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg is already the newest version.
The following packages were automatically installed and are no longer required:
  libmjpegtools0c2a libwxsvg0 netpbm mpgtx libnetpbm10 mjpegtools
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 135 not upgraded.

luego vuelvo a utilizar el comando de: sudo dpkg-reconfigure xserver-xorg y me sale que no esta instalado q puedo hacer.....

---

### Post by faktorqm on 2008-06-13
Esta solucion es vieja (para ubuntu 7.04; 7.10; ver fecha de los posts...) la solucion que te servira muy probablemente sea 

```
sudo displayconfig-gtk
```

Salu2!!

---

