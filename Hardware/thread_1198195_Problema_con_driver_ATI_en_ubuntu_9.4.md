---
title: "Problema con driver ATI en ubuntu 9.4"
date: 2009-06-27
forum: Hardware
---

### Post by Gmmex on 2009-06-27
Intente modificar el archivo x.org o algo asi, pero después de que se cargara la barra de ubuntu me salian unos pantallazos de colores, unos 4 y se quedo congelada la imagen, total tuve que reisntalar el sistema porque no supe como entrar en modo consola, y despues me entere que el driver de ati 9.4 no tiene soporte para tarjetas antiguas (la mia es una radeon 200M), entonces me gustaria instalar el driver de ati 8.12, pero no tengo ni idea, y por si algo saliera mal, tambien expliquenme como se entra a modo consolas.

---

### Post by redvilla on 2009-06-27
Me sumo a la peticiòn.... soy un novato en el tema pero tengo claro que quiero safarme de window$.

---

### Post by radixs on 2009-06-27
> **Gmmex said:**
> Intente modificar el archivo x.org o algo asi, pero después de que se cargara la barra de ubuntu me salian unos pantallazos de colores, unos 4 y se quedo congelada la imagen, total tuve que reisntalar el sistema porque no supe como entrar en modo consola, y despues me entere que el driver de ati 9.4 no tiene soporte para tarjetas antiguas (la mia es una radeon 200M), entonces me gustaria instalar el driver de ati 8.12, pero no tengo ni idea, y por si algo saliera mal, tambien expliquenme como se entra a modo consolas.

Hola cuando tines levantado el entorno grafico solo basta con crtl+alt+F2 y entras y para volver al entorno, crtl+alt+F7, Tabien puedes escoger la opcion en el menu del grub para entrar solo en cosola.

Con respecto a los driver de ati, los driver libres tengo entendido que van bien, ojo el driver 8.12 no deberia funcinar en ubuntu 9.04 ya que cambiaron la version xorg (si me equivo favor corregir). En lo personal yo tengo un Ati Raedon S. x1650Pro. con driver libres y va de maravilla.

Ahora como consejo cuando vayas a modificar tu xorg.conf siempre haz un archivo de respaldo de este, como:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.cong.backup
```Y para restaurar tu xorg.

```
cp /etc/X11/xorg.cong.backup /etc/X11/xorg.conf
```Muy facil no. asi evitamos muchos dolores de cabeza ;)

PS: Si eres nuevo pasate por [***aqui***]("https://wiki.ubuntu.com/ChileanTeam/ManualUbuntero")

---

### Post by Carlos C on 2009-06-28
Hola, ¿tu tarjeta es una  ATI Radeon Express 200M? Si es así asumo que tu equipo es un laptop, ¿no es así? ¿Qué modelo es?

Por favor dinos qué te sale si escribes en el terminal:
```
lspci| grep VGA
```
Por otro lado no me queda claro si puedes levantar el sistema con los drivers libres. Yo tengo una ATI 200M y puedo usar los drivers libres, con direct rendering, sin problemas en Ubuntu Jaunty.

Saludos.

---

