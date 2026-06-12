---
title: "Recien nacido - Problema de video"
date: 2009-02-04
forum: Hardware
---

### Post by pablognz on 2009-02-04
Hola, Soy diseñador grafico y editorial con la idea de poder empezar a realizar mis trabajos en linux, se que los programas que hay son muy inferiores a los que ya existen en PC pero me imagino que estando en contacto con Uds me podran empapar mas del tema "Diseño" en este sistema operativo.
Ayer instale el Xubuntu en una PC que tengo, todo sin problemas durante la instalacion, pero cuando terminó y arranca el programa mi monitor no lo muestra, (sin señal) hace unas bandas de colores raras, como si no fueran compatibles la resolucion del monitos con el Xubuntu.
Es un monitor samsung LSD 19¨. Tuve la idea de iniciar a prueba de fallos (como Win) pero no veo la forma, tal vez porque no tiene fallas no existe esa funcion? ;) .
Aver si me dan una mano con el tema, agradeceria enormemente.
Abrazo, pablo
PD: perdon si este no es el lugar apropiado para exponer esto... error de principiante

---

### Post by Hei Ku on 2009-02-04
Apreta Ctrl+Alt+F1

Deberia aparecerte la consola, y ahi podes ingresar con el usuario y contraseña que pusiste durante la instalacion

una vez ingresado, pone:

sudo dpkg-reconfigure xserver-xorg -phigh

Te va a aparecer para ingresar, ponela, aunque no te aparezca ningun caracter al teclear, y apreta Enter

Despues pone:

sudo shutdown -r now

y eso te va a reiniciar la maquina

Y los programas de diseño, depende para que los uses, y que usabas antes.

---

### Post by sergiom99 on 2009-02-04
hola pablognz, bienvenido!
Una búsqueda rápida en Google me tiró esta página:
[http://es.wikibooks.org/wiki/Introducci%C3%B3n_a_Linux/Equivalencias_Windows_en_Linux](http://es.wikibooks.org/wiki/Introducci%C3%B3n_a_Linux/Equivalencias_Windows_en_Linux)

Espero te sirva.
Suerte!
Sergio

---

