---
title: "Zyxel P-660-c1"
date: 2008-11-30
forum: Hardware
---

### Post by Nico_Cavs on 2008-11-30
Hola tengo este modem de speedy telefonica argentina, y bueno siguiendo guias y demas creo que llegue a un punto en el que no puedo seguir más

logré que el modem sincronize es decir que tenga las dos luces encendidas al mismo tiempo.

y luego cree un archivo llamado "inciarmodem" con el cual supuestamente me tengo q poder conectar a internet :S

> #!/bin/bash
VPI=8
VCI=35
COUNT=0
ISP=dsl-provider
modprobe ppp_generic
modprobe pppoatm
modprobe pppoe
modprobe br2684
while [[ $((COUNT++)) -lt 40 ]]
do
  SYNC=$(dmesg | grep 'ADSL line: up')
  if [ ! -z "$SYNC" ]
  then
    br2684ctl -b -c0 -a $VPI.$VCI
    sleep 3
    ifconfig nas0 up
    sleep 10
    pon $ISP
    exit 0
  fi
  sleep 5
done
echo "The SpeedTouch firmware did not load"

y el otro es dsl-provider

> noipdefault
defaultroute
replacedefaultroute
hide-password
noauth
persist
usepeerdns
plugin rp-pppoe.so nas0
user "44580632@speedy"
password "123456" 

la cosa es que cuando ejecuto el primer archivo, la consola se queda en espera y no pasa nada .. :S

es como q se tilda y la verdad no se que puede hacer


otra cosa uqe les queria preguntar, en caso de cambiar el modem por un que tenga ficha de red y no sea usb, cual me aconsejan?

---

### Post by luks911 on 2008-11-30
Hola Nico_Cavs,

La verdad es que, a pesar de que no es lo que preguntás, iba a recomendarte que lo configuraras como router. Es lo mejor para cualquier sistema operativo, es mucho más sencillo y te olvidás de tener que conectar cada vez. Pero cuando llegué al final del post veo que preguntás por otro modem con conexión ethernet. ¿Ese Zyxel no tiene? Usé dos, ambos provistos por telefónica, y los dos tenían. Y no pude encontrar tu modelo en la página de Zyxel.

Por si las dudas, te dejo un link[0] que explica cómo configurar como router un modelo similar a través del configurador web. Tendrás que cambiar tus datos de conexión y tal vez la puerta de enlace.
Y también un link a un instructivo para hacerlo por telnet[1] (es un pdf).

Cualquier cosa avisá y disculpá si no fue de mucha ayuda.

[0] [http://www.adslzone.net/tutorial-20.11.html](http://www.adslzone.net/tutorial-20.11.html)
[1] [http://rapidshare.com/files/129251750/INSTRUCTIVO_ZYXEL660.pdf.html](http://rapidshare.com/files/129251750/INSTRUCTIVO_ZYXEL660.pdf.html)

---

### Post by faktorqm on 2008-12-01
Es ethernet el router? Si es ethernet lee aca: [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132)
y si es usb, postea. salu2!

---

### Post by marianom on 2008-12-29
Yo tengo una duda con respecto a este tema. Ando por mis pagos y me vine a la casa de mi tía para usar internet (y para saludar obvio). Tiene un Zyxel p-600 con Speedy. Puedo conectarme por ethernet pero mi duda es que si sigo el proc que viene en la página de Speedy y reconfiguro el router si luego ellos van a poder seguir usando el servicio sin modificaciones con XP y Vista. No quiero dejarles un problema por solo un par de minutos de internet. ¿Alguien sabría decirme?

---

### Post by luks911 on 2008-12-29
Ellos tienen el router en modo bridge y vos lo vas a pasar a modo router, ¿verdad? Si es así, no van a tener problemas. De hecho, les evitás que después para conectarse tengan que marcar la conexión. 
Y puesto en modo router el modem se conecta solo independientemente del SO de las máquinas a las que lo conectes.
Y en el peor de los casos lo reseteas con el boton que tiene atrás y vuelve a como está ahora.

---

### Post by marianom on 2008-12-29
Vamos a hacerle un tiro entonces. Wish me luck.

---

### Post by marianom on 2008-12-29
Resulta que el modem ya tiene dos opciones habilitadas: una standard de speedy y una tipo router como se describía en el tuto de la pagina (aunque con diferente nombre). Me aseguré de los datos de la modem-type (cambiando user y pass) y deshabilite la otra pero la PPPoE no quiere arrancar cuando hago la verificación de estado así que no lo pude hacer andar. Vaya a saber que diablos le pasa.

---

### Post by luks911 on 2008-12-29
¿Verificaste que sean correctos los datos de usuario y contraseña de la opción en modo router (me reiero a los que usás para conectarte al ISP, aparecen en el menú 11.1 como My Login y My Password)? Otra cosa no se me ocurre :confused:

---

### Post by marianom on 2008-12-29
100% seguro. Lo unico que es diferente del tuto y lo que tengo yo (además del nombre de la conexión) es que "Edit ATM options" no queda en Yes, cuando lo pongo y paso a la siguiente pantalla (donde ya estaba definido VCI 35), cuando vuelvo quedo en "no" y no hay forma que se cambie. Por lo demás todo parece lo mismo, pero el PPPoE se niega a levantarse.

---

### Post by luks911 on 2008-12-29
Sí, entiendo que lo de ATM se cambia para poder editarlo y después vuelve a No. 
Ah, otra cosa: verificaste qué pasa saliendo del entorno de configuración y tratando de navegar, o entrando al configurador web (192.168.1.1).

---

### Post by marianom on 2008-12-29
Nevermind, ya me estoy yendo. Saldré a robar wireless por el barrio o me tomaré una cerveza en algún café sobre el bulevar peralta ramos mientras navego con mi ubuntu ;)
Gracias por tu ayuda.

---

### Post by luks911 on 2008-12-29
De nada, mandá aire de mar, que hace falta acá en Buenos Aires.

Saludos

---

### Post by Nikolopulus on 2010-09-12
Buenas, tengo un modem zyxel p600 y no pude hacer que ubuntu lo reconozca, intenté con pppoeconf pero no hay caso
Creo que no está configurado como router, pero no se como cambiarlo. Entré al tutorial de speedy que recomendaron por ahí pero la sesion telnet me abre un consola tipo DOS y ni idea que hacer
¿Alguien tiene idea como lo hago?
Gracias

---

### Post by josecuervo86 on 2010-09-12
No es muy ortodoxo, pero encontre esto en taringa, donde colgaron el archivo de configuración de fábrica para poder hacerlo router. **No lo probe, pero parece que anda, corre bajo riesgo tuyo probarlo**, jeje. El archivo tiene un par de fotos mostrando paso a paso que haces, ademas del archivo .rom con la configuración,

Enlace: [http://www.taringa.net/posts/downloads/1670112/Zyxel-p600-Speedy-Solucion-Telnet.html](http://www.taringa.net/posts/downloads/1670112/Zyxel-p600-Speedy-Solucion-Telnet.html)

---

