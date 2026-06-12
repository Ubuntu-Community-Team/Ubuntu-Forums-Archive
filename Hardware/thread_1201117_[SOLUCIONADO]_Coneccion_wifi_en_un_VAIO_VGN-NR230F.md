---
title: "[SOLUCIONADO] Coneccion wifi en un VAIO VGN-NR230FE"
date: 2009-06-30
forum: Hardware
---

### Post by jorval on 2009-06-30
Poseo un Sony Vaio VGN-NR230FE en el que tengo instalado Ubuntu 8.04. Hace pocas horas estaba conectado a Internet via wifi cuando de improviso se desconectó, pensé que se trataba del modem, por lo que llamé a VTR y este me informó que todo estaba normal.
Esto me sucedía sólo cuando actualizaba a un nuevo kernel, pero lo solucionaba sin problemas siguiendo el procedimiento de conexión con tarjetas atheros, que es la que tiene mi equipo.
Mas datos:
```
jorval@jorval-laptop:~$ lspci | grep Wireless
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
jorval@jorval-laptop:~$ 

```

Agradeceré vuestra ayuda. Saludos.

---

### Post by Iced_R on 2009-06-30
Probaste con MADWiFI? Ese programa te permite cargar drivers de Atheros en Linux. Además, podrías chequear en Controladores de Hardware si es que están habilitados los controladores de tu tarjeta de red. Y por otro lado, si no te funciona eso, podrías probar con ndiswrapper, un programa que en base a los drivers de Windows, emula drivers para Linux.

Saludos.

---

### Post by jorval on 2009-06-30
Iced_R: Los drivers son de Madwifi. Los Controladores de Hardware están como te muestro

[[IMG]http://img30.imageshack.us/img30/3772/pantallazocontroladores.th.png[/IMG]](http://img30.imageshack.us/i/pantallazocontroladores.png/)

No tengo windows en mi equipo. Saludos

---

### Post by CdK1 on 2009-06-30
Claro, es necesario la "reinstalación" del driver en tú caso..., ahora se supone que está "funcionado", cuando tratas de conectarte, tira algún error?, cuando lo intentas haz visto lo que tira el comando "dmesg" en consola?.

Otra manera de hacer "funcionar" tu tarjeta es de la siguiente manera:

Deshabilita los controladores que tienes y reinicias, como root ejecutas;

apt-get install build-essential && cd /usr/local/src/ && mkdir Wifi  && cd Wifi

wget [http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz](http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz) && tar vxzf madwifi-0.9.4.tar.gz && cd madwifi-0.9.4

rm -rf /lib/modules/$(uname -r)/madwifi 

make && make install 

Los habilitas nuevamentes desde Sistema ==> Administracion ==> Controladores de hardware y reinicias.

Para conectar usando GUI, wicd es bastante bueno, liviano y bueno, además si quieres mantener al día tu driver, puedes instalarlo desde su repositorio "svn".-

---

### Post by CdK1 on 2009-06-30
Claro, es necesario la "reinstalación" del driver en tú caso..., ahora se supone que está "funcionado", cuando tratas de conectarte, tira algún error?, cuando lo intentas haz visto lo que tira el comando "dmesg" en consola?.

Otra manera de hacer "funcionar" tu tarjeta es de la siguiente manera:

Deshabilita los controladores que tienes y reinicias, como root ejecutas;

apt-get install build-essential && cd /usr/local/src/ && mkdir Wifi  && cd Wifi

wget [http://downloads.sourceforge.net/mad...i-0.9.4.tar.gz]("http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz") && tar vxzf madwifi-0.9.4.tar.gz && cd madwifi-0.9.4

rm -rf /lib/modules/$(uname -r)/madwifi 

make && make install 

Los habilitas nuevamentes desde Sistema ==> Administracion ==> Controladores de hardware y reinicias.

Para conectar usando GUI, wicd es bastante bueno, liviano y bueno, además si quieres mantener al día tu driver, puedes instalarlo desde su repositorio "svn".-

---

### Post by jorval on 2009-07-01
CdK1: Mi conección wifi estaba funcionando sin problemas y de improviso se desconectó.
Lo primero que hice después de llamar a VTR para verificar el modem fue reinstalar el driver siguiendo practicamente el mismo procedimiento que tu me indicas. El procedimiento que empleo siempre es el que aparece en este tema:
[http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/]("http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/")

con la única diferencia que mi driver actual es ```
/home/jorval/source-fuentes/madwifi-hal-0.10.5.6-r3861-20080903
```

¿Alguna otra sugerencia? Gracias.

---

### Post by CdK1 on 2009-07-01
Te recomiendo cambiar de Driver, debido a que el que postee es el último hasta ahora, además cuando tratas de conectarte, te da algún error? dmesg muestra algo?

---

### Post by jorval on 2009-07-01
CdK1: Sí, eso haré, aunque con mi driver estaba funcionando perfectamente. Hago en terminal dmesg y me sale una enoooooorme respuesta, pero en ninguna parte dice Error. No tengo idea para que es dmesg, me pondré a leer al respecto. Gracias.

---

### Post by CdK1 on 2009-07-01
Cuando trates de conectarte ejecuta ese comando, y pégame las últimas líneas, no necesariamente tiene que ser error...

---

### Post by jorval on 2009-07-01
CdK1: Estas son las últimas líneas del dmesg

 17
[   43.376923] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   43.377052] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   54.942078] NET: Registered protocol family 10
[   54.942649] lo: Disabled Privacy Extensions
[   54.944723] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   65.431513] ath0: no IPv6 routers present
[   67.448731] CPU0 attaching NULL sched-domain.
[   67.448745] CPU1 attaching NULL sched-domain.
[   67.462504] CPU0 attaching sched-domain:
[   67.462513]  domain 0: span 03
[   67.462517]   groups: 01 02
[   67.462524] CPU1 attaching sched-domain:
[   67.462528]  domain 0: span 03
[   67.462531]   groups: 02 01
[  122.568584] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  122.592300] NET: Registered protocol family 17
[  122.968786] ath0: no IPv6 routers present
jorval@jorval-laptop:~$


Mira este mejor:

jorval@jorval-laptop:~$ dmesg | tail
[   67.462524] CPU1 attaching sched-domain:
[   67.462528]  domain 0: span 03
[   67.462531]   groups: 02 01
[  122.568584] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  122.592300] NET: Registered protocol family 17
[  122.968786] ath0: no IPv6 routers present
[  142.909729] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  142.914074] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  143.283497] eth0: no IPv6 routers present
[  150.970432] eth0: no IPv6 routers present
jorval@jorval-laptop:~$ 

Parece que sucede algo con ese no IPv6 routers present

---

### Post by jorval on 2009-07-02
Hola amigos. Resulta que bajé un driver que no era el correcto, me di cuenta después de instalarlo y por supuesto no me funciona el wifi. Mi consulta es cómo lo desintalo por completo. Desde ya muchas gracias. 

Bajé este driver: madwifi-0.9.4-r4063-20090627 en lugar de madwifi-hal-0.10.5.6-current.tar.gz

También quiero desintalar y borrar el driver anterior, que era con el que estaba funcionando hasta ayer: madwifi-hal-0.10.5.6-r3861-20080903

Saludos.

---

### Post by CdK1 on 2009-07-02
Desintala los privativos; hostapd y madwifi-tools

Para los que bajaste;

Vas al directorio donde hiciste "make install" y haces;
sudo make uninstall

---

### Post by jorval on 2009-07-03
CdK1. Hostpad y madwifi-tools no los tengo instalados. Hice lo que me indicaste con los dos drivers que tengo. En el terminal el comando uninstall actuó correctamente pero en mi /home siguen apareciendo ambos directorios (carpetas). ¿Podrías explicarme como funciona esto? ¿Ahora qué hago con esos directorios? ¿los elimino enviándolos a la papelera? Gracias por tu paciencia.:oops:

---

### Post by moreback on 2009-07-03
El sudo make uninstall te desintala los archivos que te copió en el sistema (/lib, /usr, /etc), pero no borra los archivos del código que están en tu /home, esos los tienes que borrar manualmente.

Saludos.

---

### Post by jorval on 2009-07-03
Moreback. Gracias, era lo que suponía pero quería estar seguro.

Bueno, les cuento que estoy conectado a Internet por wifi. Muchas gracias a todos por la ayuda. Saludos.

---

### Post by jorval on 2009-07-04
Hola amigos. Me superó. Estoy tratando de editar el título del tema para ponerle "Solucionado". He tratado de diversas formas pero no aparece el cambio en el título del subforo. ¿Cómo se hace? Gracias.

---

### Post by Carlos C on 2009-07-04
Editado Jorval. Lo que pasa es que tú puedes editar tus entradas (respuestas, posts) pero no editas el título del thread (el hilo de discusión en donde se agrupan las entradas relacionadas).

Saludos.

---

