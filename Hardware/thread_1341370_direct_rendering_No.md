---
title: "direct rendering: No"
date: 2009-11-29
forum: Hardware
---

### Post by dirty fingers on 2009-11-29
A ver quien me saca del pozo. todo estaba bien hasta que empece a experimentar.... así se aprende se supone.

Tenia el driver 185 funcionando perfectamente.
Instale el 190 de un ppa y me trajo miles de conflictos.
Desde synaptic lo borre al 190  y volví a agregar el 185.
Con la herramienta que viene volvi a activarlos.
Todo quedo como esataba excepto que ahora tengo direct rendering: No  por lo cual un rendimiento espantoso.

Que hago ? leo leo y no llego a nada.


-----------------------------------------------------------------


dirtyfingers@dirtyfingers-desktop:~$ glxinfo | grep rendering
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

creo que por acá viene el problema. dicen que se corrige al agregar el usuario al grupo video.....lo cual no me dice nada.

---

### Post by Mauro22 on 2009-11-29
Usas compiz o algo asi?? 

glxgears que te devuelve?

---

### Post by dirty fingers on 2009-11-29
uso compiz y funciona. 
glxgears me muestra los engranajes girando leeeentoooo.

------------------------------------------------------------

Efectivamente era un tema de permisos. iniciando el sistema como root tenia direct rendering: Yes

La solución fue tan ridícula como el problema.
Tan solo desactive, reinicie, active, reinicie y ya andaba bien.

---

