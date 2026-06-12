---
title: "[SOLVED] Bluetooth 2da edicion Xubuntu 8.10"
date: 2008-11-09
forum: Hardware
---

### Post by andy_91 on 2008-11-09
disculpen las molestias, pero es que otra vez tengo problemas con el bluetooth .
 es que ahoro el telefono no encuentra la pc y cuendo envio un archivo del pc al teefono me sale este error:


[[IMG]http://www.imaxenes.com/mini/bluetooth_error1la64pm.png[/IMG]](http://www.imaxenes.com/imagen/bluetooth_error1la64pm.png.html)

desde ya gracias

---

### Post by santiagoward2000 on 2008-11-09
Bienvenido de vuelta Andy! :)
Mirá, te cuento lo que yo hice para que ande.
[LIST]
[*]Primero, abrí **bluetooth-properties** y en la primera tab (la que tiene tu nombre) elegís que esté visible (o por un tiempo, como quieras) para poder verlo desde tu cel.
[*]Después instalé el **Bluetooth File Sharing** desde Add/Remove... (la verdad que no sé como se llama el paquete en Synaptic).
[*]Lo abrí desde **Applications > Accessories**
[*]LISTO!
[/LIST]
Ahora si tratás de mandar algo desde tu cel vas a ver un cartel que te pregunta si lo aceptás y si querés aceptar siempre que venga desde tu cel. Los archivos se copian al escritorio.
El error que te aparece cuando tratás de enviar no tengo idea de que es. Fijate si sigue apareciendo después de que instales **Bluetooth File Sharing**.
Saludos!

_EDIT:_
Preguntonta: Acabo de probar mandar algo, pero me había olvidado de prender el bluetooth de mi cel, y me apareció el mismo error. ¿No lo tendrás apagado vos también?

---

### Post by andy_91 on 2008-11-10
no el BT del celu estaba prendidio, por que primero probe enviar un archivo del movil al pc, pero voy a probar lo que me dijiste

---

### Post by andy_91 on 2008-11-10
gracias, pero al pareser es problema del adaptador por que envio un soloarchivo y despues no mando ni recibio nada mas

---

### Post by santiagoward2000 on 2008-11-10
> **andy_91 said:**
> gracias, pero al pareser es problema del adaptador por que envio un soloarchivo y despues no mando ni recibio nada mas

Hmmm, ¿podés probar desde un LiveCD a ver si manda bien? Tal vez haya algo mal configurado...

---

### Post by andy_91 on 2008-11-10
bueno el livecd que yo tengo tiene un archivo corrupto :p

talvez sea eso....

---

### Post by andy_91 on 2008-12-07
El problema era de la distro (Xubuntu 8.10), lo solucione instalando Ubuntu 8.04.1 alternate cd

---

