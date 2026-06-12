---
title: "duda con respecto tarjeta grafica"
date: 2009-09-01
forum: Hardware
---

### Post by arsos3 on 2009-09-01
hace poco me cambie a ubuntu y no tuve problemas de ningún tipo, me reconoció todo el sistema, pero me salta una duda con respecto a las gráficas. por ejemplo cuando veo un vídeo al "ampliar" la pantalla, el vídeo se ve a "saltos y lento" con relación al audio y cuando hay letras grandes se distorsionan las orillas. cosas que no ocurría en windows. seguramente debe ser algun problema con el driver o algo asi. ademas cuando entro a "controles de Hadware" en ubuntu no reconoce ningun problema.
Q HAGO?

PD: MODELO DE LA TARJETA GRAFICA. ni idea pq no se donde ver eso en ubuntu jojo, pero el laptop es DELL INSPIRION 6000 TAG BT81K81

---

### Post by Carlos C on 2009-09-01
Para ver tu modelo de tarjeta puedes escribir en el terminal:
```
lspci |grep VGA
```
Saludos.

---

### Post by themasterdark on 2009-09-22
otra forma para ver el modelo de todo tu hardware y obviamente tu tarjeta grafica

prueba en un terminal con:

.............................
sudo lshw
..............................

o si lo quieres en forma gráfica, instala primero lshw-gtk 
desde synaptic o en un terminal:

...............................
sudo aptitude install lshw-gtk
................................

y lo ejecutas:

.................................
sudo  lshw-gtk
..................................


asi puedes dar la información requerida para q la comunidad te ayude =)

Saludos

PD: se me olvido mencionar que el comando lo conoci hace poquisimo rato aqui mismo en el foro =), esta en los post de la semana creo...

---

### Post by Blackaiser on 2009-10-16
Excelente... 
me costo un poquito.. pero lo encontre... esta un poco escondida la info...
gracias por la aplicación

---

