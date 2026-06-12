---
title: "Ayuda: Placa Encore ENL TV-FM en Ubuntu 12.04"
date: 2012-05-13
forum: Hardware
---

### Post by pdfernandez on 2012-05-13
Que tal, soy nuevo en Ubuntu (tanto el foro como el software) y tengo una placa Encore capturadora de tv que me gustaría hacer andar, segui los pasos que encontre en la web pero no logre hacer que funcionara. Quería saber si hay algun buen tutorial para leer muchas gracias. Pongo el link de los pasos que realice por si sirve de algo.
Saludos
 
link: [http://www.taringa.net/posts/linux/12739350/solucion-enltv-fm3-linux-ubuntu-11_04.html](http://www.taringa.net/posts/linux/12739350/solucion-enltv-fm3-linux-ubuntu-11_04.html)

---

### Post by El Potro on 2012-05-23
Probá abriendo una terminal (consola, shell) y escribiendo esto

```
sudo modprobe saa7134 card=184 tuner=37 ir_debug=1
```

Abrí el tvtime, si no lo tenés instalado, instalalo así:

```
sudo apt-get install tvtime
```

Y lo ejecutás tipeando en la consola

```
tvtime
```

Ves la imagen así?

---

