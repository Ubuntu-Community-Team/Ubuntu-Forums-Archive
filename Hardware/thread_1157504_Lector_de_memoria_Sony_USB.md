---
title: "Lector de memoria Sony USB"
date: 2009-05-12
forum: Hardware
---

### Post by z37a on 2009-05-12
Gente, tal vez esto sea molesto, pero encontre hace un tiempo un posible bug en jaunty, desde la salida del kernel version 2.6.28-11, y es que el lector de memorias Sony USB no me lee ninguna SD, no probe con otro tipo de memoria por que no tengo otras, lo mas raro es que una de las memorias que probe la probe con el kernel 10 y me funciono de 10, pero al actualizar al 11 ya no me leia mas la memoria ni ningun otra!!!

Esto yo lo publique en launchpad, peor por lo visto nadie le presto interes, y ya tengo bastante tiempo esperando saber si a alguien mas le sucede. A alguno de aca le pasa lo mismo, o tiene idea de que puede ser?

Les dejo el link a launchpad: [https://bugs.launchpad.net/ubuntu/+bug/347042](https://bugs.launchpad.net/ubuntu/+bug/347042)

---

### Post by marianom on 2009-05-12
Mi máquina nunca leyó memoria de Sony: ni en HH, ni en II ni ahora en JJ. Igual tampoco me leyo el contenido de mi reproductor mp3  salvo que usara el cable conector que traía el equipo. Siempre le eché la culpa a Sony por todo ello y definitivamente no a Linux, ¿vos decís que estuve equivocado todo este tiempo?

---

### Post by z37a on 2009-05-12
> **marianom said:**
> Mi máquina nunca leyó memoria de Sony: ni en HH, ni en II ni ahora en JJ. Igual tampoco me leyo el contenido de mi reproductor mp3  salvo que usara el cable conector que traía el equipo. Siempre le eché la culpa a Sony por todo ello y definitivamente no a Linux, ¿vos decís que estuve equivocado todo este tiempo?

Se muy bien que a sony no le cae linux, pero la verdad es que es un lector USB Interno, no uno externo, y es lector de memorias SD(y SDHC)/MMC(obviamente)/MS/CF el tema es que al ponerle memorias SD con la version 10 me lo leia, un cambio en el kernel 11 haze que no la lea, estoy seguro!!!!

---

### Post by z37a on 2009-05-13
Perdón por el doble post pero quería avisar:

Solucione el problema, la solución fue reemplazar al kernel, en mi caso lo reemplace por el kernel 2.6.29.3 del sitio de kernels de ubuntu:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Igualmente no creo que sea para recomendar ya que estos kernles, algunos, no están bien testeados al parecer y posiblemente no funcionen bien(por lo cual no desinstalar el viejo kernel).

---

