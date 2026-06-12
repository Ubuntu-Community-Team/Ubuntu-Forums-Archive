---
title: "no logro hacer andar el scanner de la epson cx5600"
date: 2010-05-28
forum: Hardware
---

### Post by FB91 on 2010-05-28
probé muchas guías que están dando vueltas, como estas:
[http://www.ubuntu-es.org/?q=node/69308](http://www.ubuntu-es.org/?q=node/69308)
[http://www.taringa.net/posts/linux/2500818/Ubuntu-Configurar-Scanner_impresora-EPSON-CX5600.html](http://www.taringa.net/posts/linux/2500818/Ubuntu-Configurar-Scanner_impresora-EPSON-CX5600.html)

Hice lo que dicen esas guías, pero con ninguna logro hacer andar el scanner. Les cuento que por ejemplo con el Simple Scan (por defecto en ubuntu 10.04) cuando clickeo en scannear se queda unos 5 segundos trabajando y después el programa se cierra y la multifunción se apaga.

Les dejo algunas salidas por si son de utilidad

```
fb91@fb91-desktop:~$ lsusb
Bus 002 Device 006: ID 04b8:083f Seiko Epson Corp. Stylus DX4450


fb91@fb91-desktop:~$ ls -l /dev/bus/usb/002/006
crw-rw-r--+ 1 root saned 189, 133 2010-05-28 10:39 /dev/bus/usb/002/006
```

---

### Post by faustileon on 2010-07-08
Me pasa lo mismo. ¿Nadie sabe cómo resolverlo? Probé de todo. Tengo problemas con la impresora, también, hace un ruido raro, se clava y se apaga.¡Gracias!

> **FB91 said:**
> probé muchas guías que están dando vueltas, como estas:
[http://www.ubuntu-es.org/?q=node/69308](http://www.ubuntu-es.org/?q=node/69308)
[http://www.taringa.net/posts/linux/2500818/Ubuntu-Configurar-Scanner_impresora-EPSON-CX5600.html](http://www.taringa.net/posts/linux/2500818/Ubuntu-Configurar-Scanner_impresora-EPSON-CX5600.html)

Hice lo que dicen esas guías, pero con ninguna logro hacer andar el scanner. Les cuento que por ejemplo con el Simple Scan (por defecto en ubuntu 10.04) cuando clickeo en scannear se queda unos 5 segundos trabajando y después el programa se cierra y la multifunción se apaga.

Les dejo algunas salidas por si son de utilidad

```
fb91@fb91-desktop:~$ lsusb
Bus 002 Device 006: ID 04b8:083f Seiko Epson Corp. Stylus DX4450


fb91@fb91-desktop:~$ ls -l /dev/bus/usb/002/006
crw-rw-r--+ 1 root saned 189, 133 2010-05-28 10:39 /dev/bus/usb/002/006
```

---

### Post by euzkoarima on 2010-07-09
Están un poco desactualizados, pero prueben con:

[http://ubuntu-ar.org/soporte/comos/driver-epson-styles-cx5600-cx4400-cx4450](http://ubuntu-ar.org/soporte/comos/driver-epson-styles-cx5600-cx4400-cx4450)

y 

[http://ubuntu-ar.org/tutoriales/scannercx5600](http://ubuntu-ar.org/tutoriales/scannercx5600)

Yo la había hecho andar (pc de un pariente en otra ciudad) tomando como base esos tutos, pero ya era una versión más nueva de ubuntu y algo tuve que hacer distinto, lamentablemente, no recuerdo que.

Saludos,
Eduardo

---

