---
title: "Resolucion de pantalla pesima"
date: 2010-04-02
forum: Hardware
---

### Post by darkimedez on 2010-04-02
Hola a todos.

Les cuento que tengo un notebook de un amigo al cual le prometi no decepcionarse con esto de linux y le formatié todo el aparato para dejarselo con ubuntu.

La cosa es que si bien todo marcha de perilla, la resolucion mas alta q acepta es de 800x600, muy mala, sale todo ultra grande y molesta nada mas un rato de verla.

He intentado un millon de formas para arreglar eso, pero nada me resulta.

les cuento que el notebook es olidata y la tarjeta de video es SiS 671.

he instalado mint 8 q es lo mismo que ubuntu 9.10 solo que un poco diferente en el entorno grafico. de todas formas con karmic tenia el mismo problema.

ademas, antes de todo eso, cuando el compu gozaba de xp, la resolucion era la adecuada, de 1024xalgo, asi que no creo que esté en el tope de su posibilidad

espero puedan ayudarme. Saludos, Dario

---

### Post by Carlos C on 2010-04-03
[http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads](http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads)

---

### Post by CdK1 on 2010-04-03
Has configurado el xorg.conf correctamente?

---

### Post by darkimedez on 2010-04-03
Gracias Carlos C por tu link, solo que no tengo idea cual de todos descargar para que el compu reconozca la pantalla. 

CdK1 en ubuntu 9.10 no existe el archivo Xorg :( por eso me ha costado tanto arreglar esto.

---

### Post by CdK1 on 2010-04-03
Claro, se supone que hal hace la pega, pero créalo tú mismo;

nano /etc/X11/xorg.conf

Copia uno que ande por la red... y en "Driver" pones "sis", y pruebas con otra resolución...

---

### Post by darkimedez on 2010-04-03
Perdon CdK por lo patudo, pero según mis datos del computador, qué codigo me recomiendas pegar?

Saludos, Darío.

---

### Post by Carlos C on 2010-04-04
Parte por generar un xorg.conf básico. Lo puedes hacer con este comando:
```
sudo X :1 -configure
```Eso te va a generar un archivo xorg.conf.new en tu home que debes copiar donde corresponde:
```
sudo cp xorg.conf.new /etc/X11/xorg.conf
```Saludos.

---

### Post by darkimedez on 2010-04-04
Carlos C creo que es la quinta vez que me salvas de una bien gorda. Te lo agradezco un montón.

---

