---
title: "Problema con ATI video"
date: 2009-11-10
forum: Hardware
---

### Post by oscarenzo on 2009-11-10
Buenos días,

A ver si me pueden echar un cable, les comento mi problema: tengo una hp pavilion dv5.

he conectado mi monitor en mi portátil y automáticamente me a clonado las pantallas, tengo instalado la interfaz de ati catalyst para ubuntu, y después no puedo hacerlo, cuando trato de entrar en sistema -> preferencia -> pantalla, con el monitor conectado, no carga, se queda colgado, cuando entro sin el monitor conectado, carga bien, alguien puede echarme un cable de como conseguir mi pantalla extendida?

Gracias de antemano.
Saludos.

---

### Post by Tosh78 on 2009-11-10
Yo desde que actualice tengo problemas para clonar la pantalla, generalmente no lo hace, aunque algunas veces si a una resolucion mucho menor a lo que puede soportar.
Sin embargo, cuando quiero usarla como escritorio extendido, me sale un pop up preguntandome si quiero crear una resolucion virtual. Ese cartel sale solo la primera vez, una vez que ya esta creada la resolucion virtual no te pregunta mas. Quizas esa resolucion virtual no esta bien creada.
Tenes los ultimos drivers de Catalyst?

---

### Post by oscarenzo on 2009-11-11
Hola, bueno en mi caso por defecto, me clona la pantalla, pero despues desde consola, ejecute un parametro que vi desde aticonfig, y me dio un mensaje que no podia cambiar este parametro en la configuracion de xorg, mientras estaba la sesion inicado.

Lo que hice fue a traves de consola, modificar estos parametros, cerrar en iniciar sesion nuevamente, y listo. al parece la primera ves que reinicie el sistema se me desconfiguro, tuve que hacerlo nuevamente, pero al parecer ahora, esta todo bien, no se desconfigura, bueno creo que el tema ya esta solucionado.

Si alguien tiene algun problema parecido, avisarme quizá pueda exarle un cable.

Saludos a todos y gracias por su tiempo;)

---

### Post by guillermolisi on 2009-11-11
> **oscarenzo said:**
> Hola, bueno en mi caso por defecto, me clona la pantalla, pero despues desde consola, ejecute un parametro que vi desde aticonfig, y me dio un mensaje que no podia cambiar este parametro en la configuracion de xorg, mientras estaba la sesion inicado.

Lo que hice fue a traves de consola, modificar estos parametros, cerrar en iniciar sesion nuevamente, y listo. al parece la primera ves que reinicie el sistema se me desconfiguro, tuve que hacerlo nuevamente, pero al parecer ahora, esta todo bien, no se desconfigura, bueno creo que el tema ya esta solucionado.

Si alguien tiene algun problema parecido, avisarme quizá pueda exarle un cable.

Saludos a todos y gracias por su tiempo;)
Serias tan amable de ser algo mas explicito respecto de que parametro modificaste en el /etc/X11/xorg.conf ? Asi ya queda documentado para otros que puedan pasar por la misma o similar circunstancia.

---

### Post by oscarenzo on 2009-11-11
Si claro, sin problemas.

Lo que hice fue lo siguiente, primero abri en consola, y ejecute aticonfig.

me dio como resultado una seria de informacion y debajo habian ejemplos.

elegí la opción que me interesaba, decía que debería de ejecutar el siguiente comando.

 2. Setting up big desktop to horizontal and set overlay on secondary display.
                        aticonfig --dtop=horizontal --overlay-on=1

Entonces ejecute en consola:
aticonfig --dtop=horizontal --overlay-on=1

es aqui cuando me decia que no puede reescribir el fichero por que ya estaba en uso, sin embargo me creaba un backup, xorg.conf.fl1, algo parecido el nombre, no lo recuerdo.

Entonces procedi a entrar como root y copie el fichero antes mencionado, con xorg.conf, (lógico antes hice un backup de ésta), luego me fui a sistema -> administracion, pantallas, es aqui cuando elegi que no clone las pantallas, me dijo que iva a crear una pantalla virtual, pero antes tenia que cerrar la sesion he iniciarla de nuevo.

Lo hize, y listo ya furula.

Cualquier cosa estarñe por aquí saludos.

---

### Post by guillermolisi on 2009-11-11
Solucionado entonces. Gracias !

---

### Post by oscarenzo on 2009-11-11
Gracias a todos.

---

