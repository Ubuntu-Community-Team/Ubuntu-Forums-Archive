---
title: "Problema con actualizacion"
date: 2009-09-12
forum: Instalación y Actualización
---

### Post by bichopro on 2009-09-12
Al intentar actualizar me sale esto:

> W: Imposible obtener [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg)  No pude conectarme a archive.canonical.com:80 (91.189.90.142), expiró tiempo para conexión

W: Imposible obtener [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-es.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-es.bz2)  No pude conectarme a archive.canonical.com http:

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

es el repositorio el que se cayo supongo..
a alguien mas le pasa?

---

### Post by bichopro on 2009-09-16
bump

---

### Post by por100pre1 on 2009-09-16
Ve a:

**Sistema > Administración > Orígenes del Software**

En la pestaña **Software de Ubuntu** En **Descargar desde** elige otro repositorio. Si el problema persiste el problema es en el ordenador.

---

### Post by bichopro on 2009-09-17
siempre uso el servidor principal, ahora lo cambie a el de chile y sigue igual por que es repositorio partner el que no conecta.
Lo extraño es que si le hago ping en la consola me toma ($ping 91.189.90.142)

por ahora lo saque por que la unica actualizacion que viene de ahi es el flash y no creo que exista alguna fallo grave de seguridad por ahora.

Cualquier idea se agradece

---

### Post by nopersona on 2009-09-17
Hace 2 días que me sucede algo similar, con el 91.189.90.217 y con unos PPA de launchpad. No tiene nada que ver cambiar las rutas de los servidores, en mi caso son los de launchpad que simplemente no contestan, lo más extraño es que los ping's están en regla

```
PING 91.189.90.217 (91.189.90.217) 56(84) bytes of data.
64 bytes from 91.189.90.217: icmp_seq=1 ttl=40 time=238 ms
64 bytes from 91.189.90.217: icmp_seq=2 ttl=39 time=236 ms
```

```
--- 91.189.90.217 ping statistics ---
31 packets transmitted, 31 received, 0% packet loss, time 30006ms
rtt min/avg/max/mdev = 236.459/237.540/238.985/0.816 ms

```

Es más, el script que tengo de actualización de GPG para las llaves de launchpad, se congela, puede estar más de una hora, y nada. No quiero pensar que sea un problema más grave. 

Voy a buscar má sinfo a ver qué pillo. Ideas?

---

### Post by AlexDDR on 2009-09-18
de hecho yo he tenido una gran inestabilidad en internet en general estos dos dias, no podia meterme a ubuntu forums, y algunos repositoios no funcionan. Parece como una mezcla de internet y problemas en los servidores

espero se solucione luego o será que en visperas del 18 estan todos bajando cuecas??? jajaja

saludos

---

### Post by moreback on 2009-09-18
> **nopersona said:**
> Hace 2 días que me sucede algo similar, con el 91.189.90.217 y con unos PPA de launchpad. No tiene nada que ver cambiar las rutas de los servidores, en mi caso son los de launchpad que simplemente no contestan, lo más extraño es que los ping's están en regla

El ping usa un tipo de paquete ICMP que no está asociado a ningún servicio como HTTP, es decir que te sirve sólo para saber si el otro equipo está encendido o no. Si quieres saber el estado del servicio HTTP tendrías que usar otra herramienta que se conecte al puerto 80 y vea si recibe respuesta.

Me acuerdo de tcptraceroute, disponible en Ubuntu: **[apt:tcptraceroute](apt:tcptraceroute)**, pero puede ser que exista otra que lo haga directamente (nmap, etc.).

Saludos.

---

