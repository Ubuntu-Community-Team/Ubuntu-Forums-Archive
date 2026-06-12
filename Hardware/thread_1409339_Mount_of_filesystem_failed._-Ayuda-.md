---
title: "Mount of filesystem failed. -Ayuda-"
date: 2010-02-17
forum: Hardware
---

### Post by atari130xe on 2010-02-17
```
Mount of filesystem failed. a8d932-6c28-4c09-8b0e-23a20e8c5a9d
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.

```

Algo similar a esto le ocurre a la pc de unos amigos a los cuales le acabo de instalar Linux Mint 8 Helena. No importa que escritorio (probé con la edición Gnome y la de KDE). Se las dejo funcionando perfectamente, inclusive la apago y la enciendo y sigue igual, hasta que al otro dia (como hoy) suena mi tel y era mi amigo diciendome que le salió el "cartel" nuevamente y que no pueden usar la PC:

Apliqué en un principio la "solución" de insertar el livecd y entrar una vez cargado a gparted, marcar las particiones (todas) como "check" y luego aplicar con eso parecia que se arreglaba pero luego volvia a pasar lo mismo (esto con el disco de 80 gigas que tenia y que supuse era el problema), pero ahora con el nuevo disco hace lo mismo, estoy desorientado.

Le agregé más ram 1GB y les cambié el HD le puse uno de 300Gigas NUEVO (UltraAta), todo parecía bien hasta que empezó con esto, alguien sabe como solucionar este problema de manera permanente? Nunca me habia pasado con otras versiones de ubuntu. Lo malo es que creen ellos que Linux no funciona. Agradeceria mucho su ayuda.

PD: formateé con Ext4 en 3 particiones "/", "/home" y "swap"

---

### Post by guillermolisi on 2010-02-17
> **atari130xe said:**
> ```
Mount of filesystem failed. a8d932-6c28-4c09-8b0e-23a20e8c5a9d
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.

```

Algo similar a esto le ocurre a la pc de unos amigos a los cuales le acabo de instalar Linux Mint 8 Helena. No importa que escritorio (probé con la edición Gnome y la de KDE). Se las dejo funcionando perfectamente, inclusive la apago y la enciendo y sigue igual, hasta que al otro dia (como hoy) suena mi tel y era mi amigo diciendome que le salió el "cartel" nuevamente y que no pueden usar la PC:

Apliqué en un principio la "solución" de insertar el livecd y entrar una vez cargado a gparted, marcar las particiones (todas) como "check" y luego aplicar con eso parecia que se arreglaba pero luego volvia a pasar lo mismo (esto con el disco de 80 gigas que tenia y que supuse era el problema), pero ahora con el nuevo disco hace lo mismo, estoy desorientado.

Le agregé más ram 1GB y les cambié el HD le puse uno de 300Gigas NUEVO (UltraAta), todo parecía bien hasta que empezó con esto, alguien sabe como solucionar este problema de manera permanente? Nunca me habia pasado con otras versiones de ubuntu. Lo malo es que creen ellos que Linux no funciona. Agradeceria mucho su ayuda.

PD: formateé con Ext4 en 3 particiones "/", "/home" y "swap"
Esta usando Grub 2 ? Si es asi revisa el archivo de configuracion del Grub (el que reemplaza a menu.lst) porque me parece que ahi registra el UUID del disco.

Por otra parte, tal vez sea de ayuda darle una leida a [este tutorial sobre el tema UUID]("http://ubuntu-ar.org/node/214").

---

### Post by atari130xe on 2010-02-18
Muchas gracias Guillermo como de costumbre siempre dispuesto a dar una mano, veo si hoy puedo acercarme hasta la casa de mis amigos e intentar arreglar el tema. Te hago una pregunta: Es un Bug de la versión 9.10 de ubuntu? si es así, porque no hay un parche para eso aún?

Veo un post de Diciembre con un problema idéntico [http://ubuntuforums.org/showthread.php?t=1362602&highlight=mount+filesystem]("http://ubuntuforums.org/showthread.php?t=1362602&highlight=mount+filesystem") aparentemente solucionó el problema de manera definitiva, espero poder tener el mismo resultado.

Edito el post: estoy viendo que hay un problema con la fecha y la hora de la pc, y buscando en internet apareció que esto es una posible causa de ese fallo al inicio. (se le agotó la pila al mother) queda al encenderla en 01/01/2002 y cualquier hora, es probable que cambiarle la pila solucione este inconveniente.

---

### Post by atari130xe on 2010-02-18
Bueno... luego de intentar infructuosamente con comandos no hubo caso. En lugar de Linux Mint 8 instalé enci a Ubuntu Karmic "original" todo se instalo perfecto al iniciar por 1ra vez, entro en modo terminal tty1 titilando en el login del usuario siendo imposible escribir algo. Complicado el tema, con Mint al menos podia iniciar normalmente antes de que se "corrompa" el sistema, pero sorprendentemente ni siquiera inicia el Grub con Karmic. Ahora vuelvo a tratar de instalar Mint a ver si al menos logro hacer funcionar esta PC normalmente. (Cambio la pila del mother) estoy agotando los recursos.

PD: lo que aparecia al iniciar la PC con Karmic recien instalado es algo asi como lo siguiente:

> Ubuntu 9.10 fabio-desktop tty1
fabio-desktop login:

---

