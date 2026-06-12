---
title: "Ubuntu 10 , No veo bien los video y tarda mucho en arrancar"
date: 2010-10-19
forum: Hardware
---

### Post by akiestudio on 2010-10-19
Hola buenos dias, decidi instalar Ubuntu 10 , y resulta que al arrancar , me sale la pantalla en negro con una raya en blanco y se queda hay durante mucho tiempo, mas de 10 minutos hasta que consigue arrancar, y despues no veo bien ni las peliculas con ningun reproductor de video , ni los videos de youtube, van dando saltitos...en administracion / controladores dehardware active los de mi tarjeta ati...
Un saludo

---

### Post by hectorivand on 2010-10-21
> **akiestudio said:**
> Hola buenos dias, decidi instalar Ubuntu 10 , y resulta que al arrancar , me sale la pantalla en negro con una raya en blanco y se queda hay durante mucho tiempo, mas de 10 minutos hasta que consigue arrancar, y despues no veo bien ni las peliculas con ningun reproductor de video , ni los videos de youtube, van dando saltitos...en administracion / controladores dehardware active los de mi tarjeta ati...
Un saludo

Hola Master, los controladores de ATI traen problemas en 10.04, el procesador se va a 100% y la memoria sube hasta el "infinito". Te recomiendo que lo desinstales y vuelvas a usar los que vienen con la distro que andan muy pero muy bien.

Te tiro otro dato, en 10.10 el problema de memoria y procesador con los drivers propietarios de ATI no se presenta pero, pero... andan muy mal, se ladean las ventanas al moverlas, tarda en arrancar, etc.

Otra cosa, con respecto a los vídeos, asegurate de tener instalado los codecs. Busca en el centro de software de ubuntu "extras restringidos de ubuntu"

Cualquier cosa, comentala, por acá ando.

Saludos
Nacho

---

### Post by akiestudio on 2010-10-22
Hola muchas gracias, parece que los videos han mejorado un poco pero  ha tardado mas de 5 minutos en arrancar.

Sigo con esos problemas de video y del arranque , aunque ahora hice un ctr + alt + F2, y cuando regrese con ctr  + alt + F7. salio lo siguientes datos:

con un astericos en rojo:
Speech-dispaytcher configured for user session.
PulseAudio configured for per-user session.

Y con check battery state. Da errores.
Iwl 3995 sw error detected restored 0x820000008

Error sending REPLY_TX_PWK_TABLE_CMD time out 500ms

Wait for START_ALIVE time out after 2000ms.

Yo se que mi bateria de mi portatil esta dañana porque el portatil con la bateria no dura mas de dos minutos. Es esto por lo que tarda tanto en arrancar?
Existe alguna manera de evitar que haga un checkeo de la bateria al arrancar.
Probare quiando la bateria del portatil definitivamente.

Un saludo

---

