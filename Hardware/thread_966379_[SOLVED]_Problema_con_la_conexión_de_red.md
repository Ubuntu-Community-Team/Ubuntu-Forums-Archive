---
title: "[SOLVED] Problema con la conexión de red"
date: 2008-11-01
forum: Hardware
---

### Post by eduf on 2008-11-01
Actualicé ubuntu de 8.04 a 8.10 final, en estos días, el tema es que al iniciar busca la conexión de red y luego me da este mensaje, "Desconectado, La conexión de red ha sido desconectada", tengo un mother asus av8 con una red incluida en la placa, mas otra placa de red de encore, el modem está conectado a la placa madre, el mayor problema es que no tengo internet, trate de acceder a modem desde el firefox pero tampoco puede hacerlo. Espero que alguien me de alguna solución ya que con la anterior versión 8.04, no tenia este problema, desde muchas gracias.

---

### Post by ombzzz on 2008-11-01
> **eduf said:**
> Actualicé ubuntu de 8.04 a 8.10 final, en estos días, el tema es que al iniciar busca la conexión de red y luego me da este mensaje, "Desconectado, La conexión de red ha sido desconectada",

Te comento el problema que tuve yo, por ahi es el mismo:

Despues de actualizar, me dejo de funcionar el DHCP. Es decir, tenia la intefaz eth0 levantada pero sin el IP asignado por el modem/router.

Entonces fui a la terminal y tire un 

$sudo dhclient

y oh sorpresa, no funcionaba sino que tiraba el siguiente error

SIOCSIFADDR: No buffer space available

Google y aparecieron bastantes resultados referidos a ese error y Ubuntu 8.10. Me parece que alguien se mando una cag.... 

El thread de ayuda que me resulto util fue el siguiente:

[http://ubuntuforums.org/showthread.php?t=963335](http://ubuntuforums.org/showthread.php?t=963335)

Despues de leer lo que indicaban en ese thread lo que hice para solucionar mi problema fue:

i) remover el NetworkManager 
ii) reconfigurar la interfaz eth0 editando el archivo /etc/network/interfaces agregandole las lineas:

auto eth0
iface eth0 inet dchp

iii) reiniciar ( quizas no sea necesario y baste con sudo /etc/init.d/networking restart )

Luego de eso anduvo bien internet ( el modem/router me asigno la habitual direccion 10.0.0.3 , y el DNS y rutas apuntaron a 10.0.0.2 como es habitual ).

Otra alternativa es hacer lo que indica 

[http://ubuntuforums.org/showpost.php?p=6075466&postcount=25](http://ubuntuforums.org/showpost.php?p=6075466&postcount=25)

Ojo, el NetworkManager quedo desinstalado... por ahi vos queres que este instalado... a mi por ahora no me hace falta, ya que no toco casi la configuracion de red....

Saludos

      orlando

---

### Post by eduf on 2008-11-02
Muchas gracias ombzzz, ya lo pude solucionar lo hice con las indicaciones de este post [http://ubuntuforums.org/showpost.php?p=6075466&postcount=25](http://ubuntuforums.org/showpost.php?p=6075466&postcount=25)
eso si tuve que ingresar en modo gráfico como root, ya que el paso 4 no me parmitia hacerlo, le agregue a lo que dice sudo, pero igual no me permitia, así que de este otra página vi como ingresar como root desde inicio de sesión [http://www.ubuntu-es.org/index.php?q=node/30124](http://www.ubuntu-es.org/index.php?q=node/30124)

Y listo ya tengo internet

Nuevamente muchas gracias


:):):):)

---

