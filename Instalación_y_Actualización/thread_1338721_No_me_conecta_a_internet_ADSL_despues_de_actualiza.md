---
title: "No me conecta a internet ADSL despues de actualizar"
date: 2009-11-26
forum: Instalación y Actualización
---

### Post by dcorrea on 2009-11-26
Hola a todos...
..no aguante y actualice mi ubuntu 9.4, que funcionaba perfecto, a la version 9.10 y ahora no puedo conectarme a internet por ADSL.Configure la cuenta con nombre de usuario, contraseña...
pero no conecta :(
Agradecere su ayuda.

---

### Post by Patriciologico on 2009-11-27
Hola dcorrea, 

¿como te conectas por pppoeconf o por network-manager?

---

### Post by Patriciologico on 2009-11-27
Hola dcorrea, 

¿como te conectas por pppoeconf o por network-manager?

---

### Post by dcorrea on 2009-11-27
> **Patriciologico said:**
> Hola dcorrea, 

¿como te conectas por pppoeconf o por network-manager?

hola !!!
me conecto por pppoeconf.

finalmente me logre conectar al ejecutar el comando pppoeconf desde una consola, segui las instrucciones y logre conexion.
aunque el icono del gestor de red aparece como desconectado...

lo malo es que tengo que hacer todo este proceso cada vez que me conecto.
como es eso del network-manager? conexion cuando estoy en una LAN?

Saludos!

---

### Post by Patriciologico on 2009-12-08
El icono que vez es nm-applet y trabaja con network-manager, pppoeconf reescribe datos del network-manager y por eso deja de funcionar (te aparece desconectado), yo desintalo el network-manager y solo trabajo con pppoeconf y lo configuro para que se conecte al iniciar (es la ultima opcion) esto por que no cambio de lan y solo uso pppoe. (esto en intrepid y adelante, ahora estoy usando 8.04 y no trae nm-applet)

El fichero que se sobreescribe al ejecutar pppoeconf no recuerdo cual es, pero Moreback lo menciono una vez, esperemos que se de una vuelta por aca. Si borras lo sobreescrito, te volvera a funcionar el nm-applet.

Saludos!

---

### Post by moreback on 2009-12-08
El archivo mencionado es el** /etc/network/interfaces** y se supone que para que funcione todo con NM ese archivo debiera tener sólo la configuración de la interfaz local, o sea:

```
auto lo
iface lo inet loopback
```

---

### Post by themasterdark on 2009-12-10
quizas esto te sirva, para que puedas controlar una interface automatica ethernet o una pppoe sin problemas con network-manager...

[http://ubuntuforums.org/showthread.php?t=1340962](http://ubuntuforums.org/showthread.php?t=1340962)

(la escribi yo mismo eso como hacerlo, buscando de otras fuentes claro.. y te aseguro funciona ya que tuve q arreglar eelo en mi sistema)

Saludos

---

