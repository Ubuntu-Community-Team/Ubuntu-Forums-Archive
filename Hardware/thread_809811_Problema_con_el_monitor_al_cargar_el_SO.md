---
title: "Problema con el monitor al cargar el SO"
date: 2008-05-27
forum: Hardware
---

### Post by fedeavila on 2008-05-27
Buenas! 

Que tal les escribo para ver si me pueden ayudar con un pequeño inconveniente que estoy teniendo desde que me instale Ubuntu 7,10

Bueno empiezo...

Desde que me instale Ubuntu no tuve problemas en nada... Excepto en una pequeña cosa... 

Mi monitor...

Tengo un sencillo monitor Philips de 15''

El problema aparece cuando prendo la compu, me aparece lo normal hasta que se pone la pantalla en negro y aparece un cartelito (un mensaje del monitor) que dice 

ATTENTION: OUT OF RANGE

Espero... Y se inicia Ubuntu normalmente... Después se ve todo lo mas bien...

Pero después cuando la apago me vuelve a aparecer...

Tengo cero conocimientos sobre esto, pero estoy casi totalmente seguro de que se trata de la resolución...

Yo me acuerdo de que cuando tenia Windows XP esto se ajustaba automáticamente (en la parte donde aparece el logo de WINXP con una barra horizontal que se carga) En la misma parte pero en Ubuntu esa parte se ve que esta en mas de 1024x768 (que es lo máximo que aguanta mi monitor) o algo mal tiene...

Bueno ese es mi problema por ahora, si alguien me puede ayudar o decir desde donde podría configurar manualmente la resolución de la pantalla en “ese” preciso momento en el cual se esta cargando el Sistema Operativo o algo que lo pueda arreglar...

Ya intente buscando en Internet poner en el Terminal esto: 

sudo gedit /etc/X11/xorg.conf 

Pero eso afecta a la resolución de la pantalla pero cuando el Sistema Operativo ya esta cargado y funcionando.

Desde ya, muchas gracias!

:)

---

### Post by Mauro22 on 2008-05-27
Hola!!


Mirá lo encontre el ubuntu-es:

```

Gracias por su ayuda lo solucione, todo esta en realizar lo siguiente:
 - Editar el archivo usplash.conf, "sudo gedit /etc/usplash.conf" 
- Cambiar el valor que aparece, por la resolución correcta tu monitor, en mi caso 
 xres=1024 
yres=768 
 - Luego ejecutar el siguiente comando para que los cambios tengan efecto: "sudo update-initramfs -u" 
- reinicia. 


```

---

### Post by fedeavila on 2008-05-27
Se solucionoooooooooooooooooooooooo!!!!!!!!!!!!!!!!

GRACIAS 

:D:D:D:D:D:D

---

### Post by Mauro22 on 2008-05-27
Buenisimo!


No te olvides de "agradecerme" haciendo clic en la medalla que esta en la esquina inferior derecha de mi post. :D:D


Gracias :D

---

### Post by fedeavila on 2008-05-27
> **Mauro22 said:**
> Buenisimo!


No te olvides de "agradecerme" haciendo clic en la medalla que esta en la esquina inferior derecha de mi post. :D:D


Gracias :D
jaja OBVIO ahi lo hago ;)

---

