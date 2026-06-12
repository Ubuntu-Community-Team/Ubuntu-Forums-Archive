---
title: "Problema con Xubuntu"
date: 2009-02-19
forum: Hardware
---

### Post by JUTGtgRB7z on 2009-02-19
Hola, estoy teniendo un problema con Xubuntu. Yo lo bajé, lo instalé, despues le actualicé todo (176 paquetes) y la reinicie. Despues de eso entraba al X pero se quedaba en la pantalla de carga en donde dice Cargando Gestor de ventanas y lo deje 5 minutos y seguia asi, la pantalla de carga se la puse yo, pero es una de las que trae el mismo sistema ¿Saben que puede ser? Mañana probaré reinstalar y ver si se soluciona. Espero sus respuestas, gracias.:)

---

### Post by guillermolisi on 2009-02-20
> **pmzerdan said:**
> Hola, estoy teniendo un problema con Xubuntu. Yo lo bajé, lo instalé, despues le actualicé todo (176 paquetes) y la reinicie. Despues de eso entraba al X pero se quedaba en la pantalla de carga en donde dice Cargando Gestor de ventanas y lo deje 5 minutos y seguia asi, la pantalla de carga se la puse yo, pero es una de las que trae el mismo sistema ¿Saben que puede ser? Mañana probaré reinstalar y ver si se soluciona. Espero sus respuestas, gracias.:)
Por que pensas que una reinstalacion solucionara el inconveniente ?
Sospechas de algo irregular que pudo haber afectado su funcionamiento ?

Que placa de video estas usando ?

---

### Post by JUTGtgRB7z on 2009-02-20
> **guillermolisi said:**
> Por que pensas que una reinstalacion solucionara el inconveniente ?
Sospechas de algo irregular que pudo haber afectado su funcionamiento ?

Que placa de video estas usando ?

No pienso :p soy bastante nuevo asi que me limito a probar, no hice nada raro ahora funciona bién afortunadamente pero me pasa algo raro. Ya instalé los drivers de Nvidia (tengo una GeForce 8400 GS) pero cada vez que inicia me aparece el administrador de hardware que me da las opciones para elegir el controlador.:( Instalé los que están por defecto en Xubuntu, la version 1.77. Estoy pensando en bajar la versión 1.8 de la página de Nvidia para ver si deja de molestar.:p

---

### Post by guillermolisi on 2009-02-20
> **pmzerdan said:**
> No pienso :p soy bastante nuevo asi que me limito a probar, no hice nada raro ahora funciona bién afortunadamente pero me pasa algo raro. Ya instalé los drivers de Nvidia (tengo una GeForce 8400 GS) pero cada vez que inicia me aparece el administrador de hardware que me da las opciones para elegir el controlador.:( Instalé los que están por defecto en Xubuntu, la version 1.77. Estoy pensando en bajar la versión 1.8 de la página de Nvidia para ver si deja de molestar.:p
Bueno, probar los controladores nuevos no es mala idea. Si no funcionan bien siempre podes volver a los anteriores.

---

### Post by JUTGtgRB7z on 2009-02-22
> **guillermolisi said:**
> Bueno, probar los controladores nuevos no es mala idea. Si no funcionan bien siempre podes volver a los anteriores.

He instalado los nuevos controladores y me aparecen como habilitados ¿Existe alguna forma de saber si la aceleración 3D está activa? De esta manera podría sacar el servicio de controladores del inicio.

---

### Post by totolinux on 2009-02-22
hola abrí un terminal y pone " glxgears " sin comillas y vas a ver dos engranajes girando en forma fluida. otro comando " glxinfo " y tiene que decir "direct rendering: Yes" en la parte superior.

---

