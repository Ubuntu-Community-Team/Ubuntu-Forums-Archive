---
title: "[SOLVED] Montar Floppy"
date: 2008-12-14
forum: Hardware
---

### Post by Vero1 on 2008-12-14
Hola a todos,

Tengo dos problemas(pero empiezo por lo mas facil) que no supe ni supieron resolverme.

Estoy usando Intrepid Ibex. Mi disquetera ni aparece por ningun lado ni se puede montar, aunque me indicaron que pusiera la siguiente linea en el fstab:

/dev/fd0 /media/floppy/noauto rw,user, 0 0

cuando intento montar la unidad me contesta que no tiene punto de montaje.

Podría alguien indicarme qué debo hacer?

Gracias de antemano.

---

### Post by staar on 2008-12-14
me parece que el problema es que esta intentando montar la unidad en /media/floppy/noauto, existe esa carpeta en tu sistema? creo que el 'noauto' va despues del 'user', proba modificando eso...

saludos ;)

---

### Post by sajnox on 2008-12-14
Como dice el amigo staar, deja los espacios para que te quede asi

```
/dev/fd0 /media/floppy noauto rw,user,0 0
```

Y asegurate que exista la carpeta /media/floppy

Por las dudas creala con 

```
sudo mkdir /media/floppy
```

Y hace que la carpeta sea tuya

```
sudo chown "tu usuario" /media/floppy
```

---

### Post by Vero1 on 2008-12-14
hola y gracias por las prontas respuestas.

Bueno, así quedó el fstab:  /dev/fd0 /media/floppy rw,user,noauto, 0 0

La carpeta se creó en Sistema de Archivos/media. No aceptó el traslado a mi usuario. El floppy no aparece en Equipo, el CD sí.

Ustedes dirán.

Saludos :p

---

### Post by EnriqueK on 2008-12-15
Para montar la disquetera en 8.10 hay que hacer lo siguiente:

abrir un terminal y ejecutar:

sudo modprobe floppy

Y ya está, el problema es que al reiniciar se pierde la instrucción.

Para que se monte siempre:

sudo gedit /etc/modules
añadir una linea: floppy

quedará mas o menos así:

fuse
lp
floppy

Guardas los cambios y ya

---

### Post by faktorqm on 2008-12-15
Ya lo conteste hace poco eso con explicacion incluida
[http://ubuntuforums.org/showthread.php?t=984529](http://ubuntuforums.org/showthread.php?t=984529)

---

### Post by Vero1 on 2008-12-15
Muchas gracias a todos los que ayudaron.
Quedó montado el floppy por fin ):P

saludos.

---

