---
title: "Problema con la conexión a internet (aparece conectado sin ninguna conexión)"
date: 2018-12-24
forum: Hardware
---

### Post by dimmetrix on 2018-12-24
Después de intentar hacer funcional a Clonezilla dentro de Ubuntu, comencé a tener problemas con la conexión a internet. Honestamente no sé que habrá modificado pero sé que es algo de la red porque había llegado a la opción de configuración y como al final me decidí por no usarlo de este modo debido a algunos errores, lo borré. Fue entonces que comenzaron los problemas.

Lo que ocurre es que al conectar a la red Wifi, la conexión se establece correctamente. Aún así, no hay conexión hacia internet.

Revisé las IP y son correctas. Hice ping hacia la puerta de enlace y funciona perfectamente. Sin embargo, cuando hago ping a google me aparece algo como From 192.168.120.1 y esta no es la dirección IP configurada. Además se pierden todos los paquetes.

Probé eliminando todas las conexiónes y aún así me aparece como conectado. Evidentemente algún archivo se modificó y no me permite salir hacia internet.

¿Qué archivos debo revisar para solucionar esto?

El sistema operativo es: Ubuntu 16.04 LTS (64 bits)

---

### Post by dimmetrix on 2018-12-24
Solucionado.

El archivo interfaces que se encuentra dentro de /etc/network contenía lo siguiente:

[PHP]# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo enp3s0
iface lo inet loopback

iface enp3s0 inet static
    address 192.168.120.1
    netmask 255.255.255.0
    
    gateway 192.168.120.254
[/PHP]

**Para solucionar el problema** se ha eliminado:

[PHP]iface enp3s0 inet static
    address 192.168.120.1
    netmask 255.255.255.0
    
    gateway 192.168.120.254[/PHP]

---

