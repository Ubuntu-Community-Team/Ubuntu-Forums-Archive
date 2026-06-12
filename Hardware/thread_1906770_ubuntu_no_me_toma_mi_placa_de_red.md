---
title: "ubuntu no me toma mi placa de red"
date: 2012-01-09
forum: Hardware
---

### Post by morthenx on 2012-01-09
mi ubuntu 11.10 no me toma mi placa de red, como puedo hacer para ponerle los controladores, tengo los que vinieron en el mother, pero son para windows, trate debuscar compatibles para linux pero no encontre, les comento que soy nuevo en esto asi que sepan disculpar mi ignorancia.
 
el mother que tengo es el z68x-ud3-b3 de gigabite
 
por favor ayuda :(

---

### Post by asterix77 on 2012-01-10
Sería bueno saber las caracteristicas de tu placa de red, para ello digita en la consola lo siguiente, y escribe la salida del comando.

$sudo lspci

Otro comando que deberías correr es  ifconfig y pegar su salida acá.


En todo caso encuentro raro que ubuntu no te reconozca tu placa de red, porque el soporte para este tipo de dispositivos es muy bueno.

Saludos

---

### Post by mama21mama on 2012-01-10
Por lo que veo [http://www.gigabyte.com/products/product-page.aspx?pid=3852#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3852#sp)

es una Realtek RTL8111E chip (10/100/1000 Mbit)

y segun este hilo esa ethernet se comporta raro  [http://ubuntuforums.org/showpost.php?p=10110574&postcount=5](http://ubuntuforums.org/showpost.php?p=10110574&postcount=5)

Posible solucion.

[http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)

Saludos

---

