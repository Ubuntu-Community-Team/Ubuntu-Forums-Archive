---
title: "Internet wifi lento"
date: 2011-09-10
forum: Hardware
---

### Post by capcabgue on 2011-09-10
Hola:

Les escribo referente a un problema que tengo con wifi.
Tengo un notebook dell inspiron 1525 (venía con vista y le hice un formateo). hasta la fecha tod había andado muy bien, pero hace un par de meses hice un upgrade a ubuntu 11.04 32 bits y el wifi casi no servía de nada hice le siguiente:
- Desactivé el protocolo IPV6 
   echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf
   echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
   echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
   echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf

Luego como casi no funsionó esto (abría páginas web muuuuy lento) cambié la antena que me entrega ubuntu con lo sgtes comandos:
   - sudo gedit /etc/modprobe.d/ath9k.conf
     Y añadí al final:
   - options ath9k nohwcrypt=1 

Estos 2 cambios me han dado un funcionamiento errático de internet, en ocasiones [www.google.cl](www.google.cl) se demora casi 2 minutos en abrir (no puedo ver esos dias youtube) y en otras ocasiones (como hoy) el funcionamiento es casi decente (siempre bastante más lento que con tarjeta ethernet).
Esto me da la impresión que a más de alguien les ha ocurrido y no solamente con este modelo de dell (es cosa de ver wifi lento con ubuntu 11.04). Les dejo el link por el cual hice mis cambios
[http://www.ubuntizandoelplaneta.com/2011/07/conexion-wifi-lenta-en-ubuntu-1104.html](http://www.ubuntizandoelplaneta.com/2011/07/conexion-wifi-lenta-en-ubuntu-1104.html)

Bueno mi pregunta es si alguien me puede decir que hacer para solucionar mi problema, ya que si listo mi HW no tengo idea de cual es la tarjeta wifi dentro de esta enorme lista. 
Además una vez que sepa cual es mi taarjeta wifi, que debo hacer, como hago que con ubuntu lo reconozca y funcione bien.

Saludos y gracias

---

### Post by bichopro on 2011-09-11
Te recomiendo devolver todos los parametros a como estaban y cambiar los dns a googleDNS u OpenDNS. Aca como hacerlo pero primero asegurate de volver a dejar los parametros como vienen de fabrica. [http://www.juarbo.com/cambiar-dns-en-ubuntu%E2%80%93opendns-ubuntu/](http://www.juarbo.com/cambiar-dns-en-ubuntu%E2%80%93opendns-ubuntu/)

---

### Post by capcabgue on 2011-09-12
> **bichopro said:**
> devolver todos los parametros a como estaban 

Ok, pero me puedes indicar como activar nuevamente el ipv6?

Gracias

---

### Post by capcabgue on 2011-10-01
> **bichopro said:**
> Te recomiendo devolver todos los parametros a como estaban y cambiar los dns a googleDNS u OpenDNS. Aca como hacerlo pero primero asegurate de volver a dejar los parametros como vienen de fabrica. [http://www.juarbo.com/cambiar-dns-en-ubuntu%E2%80%93opendns-ubuntu/](http://www.juarbo.com/cambiar-dns-en-ubuntu%E2%80%93opendns-ubuntu/)

He vuelto todo los paràmetros a fàbrica (reisntalè el ubuntu), hr instalé googleDNS, claro que lo hice en wireless y no en ethernet como dice el tutorial, y aún así esta muuuuuuy lento, una gran cantidad de páginas (como yahoo mail) me dice que se demora más de lo normal y que intente nuevamente o abra con versión sencilla de html.
El driver que tengo en la tarjeta wifi es [SIZE=3][SIZE=1]Dell Wireless 1505 Draft 802.11n WLAN Mini-Card[/SIZE]

[SIZE=1]Alguien sabe como puedo instalarla para que sea un notebook que pueda usar como tal y no solamente conectado.

Gracias

PD: de todas maneras funcionaba mejor con los cambios que había hecho


[/SIZE][/SIZE]

---

