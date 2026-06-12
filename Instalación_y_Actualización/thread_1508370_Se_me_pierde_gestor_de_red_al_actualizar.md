---
title: "Se me pierde gestor de red al actualizar"
date: 2010-06-12
forum: Instalación y Actualización
---

### Post by flakojaime on 2010-06-12
Sres

Hice una actualizacion de algunos paquetes en ubuntu y se me perdio el gestor de red (ese que va en la barra al lado de la fecha)

Como lo puedo recuperar?

gracias!!!!:lolflag::lolflag:

---

### Post by asterix77 on 2010-06-14
¿te refieres a Network-manager?
(un antecedente: la ubicación de un ícono en Ubuntu es bastante relativa)

¿pero sigues con señal de red o desaparece tu conexión?. En algunos casos he hecho lo siguiente:

1)  Apreto la tecla Alt+F2 y ejecuto nm-applet

En caso de que no te funcione haz lo siguiente:


1)   Abre el monitor del sistema  Sistema ---->Administración ---->Monitor del sistema

2)   Ve a la pestaña de Procesos. Verifica si es que el Network-manager está o no activo. Si lo está finaliza el proceso.

3)  Apreto la tecla Alt+F2 y ejecuto nm-applet


Con esto debiera funcionar

Saludos

---

### Post by flakojaime on 2010-06-14
Ya.

Segui los pasos y sigue sin aparecer, 

[[IMG]http://www.imagengratis.org/thumbs/panifft8j.png[/IMG]]("http://www.imagengratis.org/?v=panifft8j.png")


te dejos un pantallazo...

En mi casa me puedo conectar, el problema se da cuando intento conectarme en otra red.

Instale un WIFI radar, pero el final solo me sirve para revisar que redes, ya que no puedo usar el programa para conectar.

gracias!

---

### Post by Carlos C on 2010-06-14
Existe un bug relacionado:

[https://bugs.launchpad.net/ubuntu/lucid/+source/network-manager-applet/+bug/456468](https://bugs.launchpad.net/ubuntu/lucid/+source/network-manager-applet/+bug/456468)

Supuestamente el problema se soluciona a partir de la versión 1:0.134.9 de update-manager.

Te recomiendo que mires tu archivo nm-system-settings.conf:
```

sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

Cambia donde dice "managed=false" a "managed=true". En el terminal luego ejecutas el comando:
```
killall nm-system-settings
```
y reinicias tu sesión. En caso de que no resulte puedes probar reiniciando el sistema.

Saludos.

---

### Post by flakojaime on 2010-06-15
Hola

Esto me sale

[[img]http://www.imagengratis.org/thumbs/pannggd5i.png[/img]](http://www.imagengratis.org/?v=pannggd5i.png)


Estoy leyendo el bug ahora...

gracias!

---

### Post by flakojaime on 2010-07-07
Hola,
bueno, al final y mientras se soluciona esto, instale otro gestor de red...

ahi esta la pagina por si quieren ver...


[http://www.noticiasubuntu.com/tag/lucid-lynx/](http://www.noticiasubuntu.com/tag/lucid-lynx/)


saludos y muchas gracias...!!!

---

### Post by flakojaime on 2010-07-10
> **flakojaime said:**
> Hola,
bueno, al final y mientras se soluciona esto, instale otro gestor de red...

ahi esta la pagina por si quieren ver...


[http://www.noticiasubuntu.com/tag/lucid-lynx/](http://www.noticiasubuntu.com/tag/lucid-lynx/)


saludos y muchas gracias...!!!



Lean esto tambien, no se me habia ocurrido

[http://ubuntuforums.org/showthread.php?t=1102271](http://ubuntuforums.org/showthread.php?t=1102271)


saludos!!!

---

### Post by doug182 on 2010-09-29
yo tenia el mismo error pero ejecute el comando nm-applet en una terminal y me dio el siguiente mensaje de error:
> root@douglas-desktop:#nm-applet
 ** (nm-applet:2560): WARNING **: <WARN>  bus_init(): Could not  get the session bus.  Make sure the message bus daemon is running!   Message: Did not receive a reply. Possible causes include: the remote  application did not send a reply, the message bus security policy  blocked the reply, the reply timeout expired, or the network connection  was broken.
 Falló en GConf: Falló al contactar con el servidor de  configuraciones; algunas de las posibles causas son que necesite activar  TCP/IP en ORBit, o que tiene bloqueos de NFS debidos a una caída de  sistema. Consulte [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/)  para más información. (Detalles -  1: Falló al obtener la conexión con  la sesión: Did not receive a reply. Possible causes include: the remote  application did not send a reply, the message bus security policy  blocked the reply, the reply timeout expired, or the network connection  was broken.)
Ya existe una instancia de nm-applet en ejecución.
 (nm-applet:2560): GConf-WARNING **: Directory `/system/networking/connections' was not being monitored by GConfClient 0x99626a8
 luego ejecute el comando: "service network-manager" 

> root@douglas-desktop:#service network-manager restart
network-manager start/running, process 2566
 y el icono de network-manager aparecio en el panel... 

espero le sirva esta info a alguien mas...

---

