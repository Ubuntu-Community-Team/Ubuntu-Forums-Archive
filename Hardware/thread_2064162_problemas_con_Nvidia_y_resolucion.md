---
title: "problemas con Nvidia y resolucion"
date: 2012-09-28
forum: Hardware
---

### Post by dree123 on 2012-09-28
Resulta que quiero aumentar mi resolucion, actualmente tengo 1366x768
me dijeron que tenia que hacerlo en Nvidia X sever settings. pero al abrirlo me sale:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Que puedo hacer para solucionar esto ??? probe bajando los driver de la pagina de Nvidia pero nose como instalarlos. Alguna solucion para aumentar mi resolucion de pantalla ???

SALUDOS.

---

### Post by dnovai on 2013-04-22
Hola dree123!
Para ayudarte se necesita saber:
- Modelo de la tarjeta nvidia
- Version de ubuntu
- y si x86 o 64 bits

Te dejo un link con una explicacion generica. Espero te sea de ayuda.  ([http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/](http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/))
Saludos!

---

### Post by daiku on 2013-04-22
por lo que tengo entendido la resolución máxima la da el monitor
yo poseo una tarjeta Nvidia y me arroja esa misma resolución como máxima pero cuando lo conecto a un televisor full HD mi resolución cambia a 1920 X 1080

---

### Post by papibe on 2013-04-22
Hi dree123.

Puedes por favor ejecutar los siguentes comandos y pegar aquí los resultados?
```
lspci -nnk | grep -iA3 vga

dpkg -l nvidia-* | grep ^ii

lsmod | grep -i nvidia

grep -i driver /etc/X11/xorg.conf
```
Saludos.

---

