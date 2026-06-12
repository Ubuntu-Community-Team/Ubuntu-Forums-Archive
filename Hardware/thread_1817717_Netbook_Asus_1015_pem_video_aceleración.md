---
title: "Netbook Asus 1015 pem video aceleración"
date: 2011-08-03
forum: Hardware
---

### Post by Guineapig1 on 2011-08-03
Hola, gente.
Tengo esa netbook con Ubuntu 10.10. Su procesador es un Intel Atom 550.
Mi problema es que cuando quiero activar los efectos de escritorio el sistema me dice que no tengo la aceleración activada. Puse en el terminal el comando que me indica si está activada y me responde que sí lo está.
¿Alguien sabe cómo puedo solucionar esto?

Gracias de antemano.

---

### Post by gmunioz on 2011-08-05
La solución podría ser utilizar un repositorio  ppa con los últimos drivers para la gráfica de esa netbook, el Asus Eee PC 1015PEM, si bien trae el nuevo procesador dual core Intel Atom N550 (1,5 GHz, trabaja con la unidad gráfica Intel GMA 3150  integrada, la cual no proporciona ganancia de rendimiento.
sudo su
add-apt-repository ppa:glasen/intel-driver 
apt-get update
apt-get upgrade

---

