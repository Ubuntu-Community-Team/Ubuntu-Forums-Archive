---
title: "epson t24 no funciona en ubuntu 10.04"
date: 2010-05-05
forum: Hardware
---

### Post by sefsinalas on 2010-05-05
Hola gente. Espero que me puedan ayudar con problemon.
Tenia una HP D1660 y nunca pude hacer que imprima bien en Linux.
Fui y me compre una EPSON Stylus T24. En Ubuntu 10.04 no imprime. El controlador no esta disponible pero use el de T20 que supuestamente es el mismo.
Pero sigue sin imprimir.

Me fui a mi instalacion de Ubuntu 9.10 que tengo en la notebook y probe y si imprime re bien.

Me pueden ayudar a hacer andar la impresora en 10.04?

---

### Post by fedeavila on 2010-05-06
es una impresora o una multifunción?
yo tengo una multi epson tx115
me bajé lo necesario desde [_acá_]("http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do") y hace menos ruido que en windows

bajate [_este_]("http://linux.avasys.jp/drivers/pips/Epson_Stylus_S21/pips-ss21-ubuntu8.04-3.8.0-CG.tgz") archivo..
lo extraés.. abrís Terminal y ponés:
```
sudo bash ~/Descargas/pips-ss21-debian4.0-3.7.0-CG.install
```

espero que te sirva!

PD: fijate que la carpeta sea esa!

---

### Post by elhg27 on 2010-07-29
Hola mira yo como novato de ubuntu, instale el samba (ojo solo lo instale) y cuando fui a sistemas<administracion<impresoras, en esa ventana me fui a servidor<nueva<impresora ahi esocoji impresora de red y esocoji windows printer via samba, ahi le di browser y busque el nombre de la impresora (es decir el nombre que le puse en el equipo con windows que tiene la impresora epson tx115) y ahi me llevo al cuadro de controladores adicionales y luego habilita un cuadro donde escoges la marca de la impresora y ahi le di epson y como no encontre la tx 115 le instale uno que decia st115 o algo asi empezaba por sx115 creo que es no recuerdo que pena pero ahi funciono la impresora imprime bien ahora estoy mirando haber si puedo lograr que escanee en red si algo les comento mi experiencia espero te sirva de algo mi ayuda.

mmmmm ah y mi ubuntu es el 10.04 y estoy feliz de haber dejado windows en mi computador este es mas rapido y mejor aun no tiene virus que lo pongan lento como una chatarra bien ahora estoy buscando es un programa parceido al virtual dj de windows pero no lo encuentro si conocen alguno les agradezco juicio.

Es decir revisa alguno que coincida con el numero del modelo, ya que tienen la arquitectura parecida suerte con tu epson.

---

