---
title: "Huawei E160 Claro3G en Ubuntu"
date: 2009-09-06
forum: Hardware
---

### Post by Eurek on 2009-09-06
Hola acabo de instalar Ubuntu 9.04 en mi compu y estoy tratando de conectarme a internet, tengo el modem Huawei E160 Claro/CTI 3G y no logro conexión.
Siempre me salta un cartel que dice:

Introduzca la contraseña para desbloquear el anillo predeterminado:
La aplicación 'nm-connection-editor' (usr/bin/nm-connection-editor) quiere acceder al anillo de claves pedeterminado, pero está bloqueado.

Pongo mi contraseña y nada. Creo que es un problema de configuración. Saben si es necesario poner el PIN y el PUK de CTI? Porque los demás datos de Número, Usuario, Contraseña, Nombre del ap aparecen automáticamente. Sólo faltan los otros dos que no sé si son necesarios.

Si alguien tiene este modem y logró configurarlo por favor una mano.
Saludos.

---

### Post by staar on 2009-09-06
lo que te está pidiendo es la contraseña del gnome-keyring (el administrador de contraseñas del sistema), que puede ser diferente a la de tu usuario, depende de como la hayas creado, generalmente la primera vez que te querés conectar, después de que te pida (o no) la contraseña de claro, te dice que la va a alojar en el anillo de contraseñas, y, si es la primera vez que lo usas, te pide que le pongas una clave (o se puede dejar en blanco), ese es el password que tenés que poner...

saludos

---

### Post by Eurek on 2009-09-22
Hola, intenté y no pasa nada, gracias por la ayuda. Si alguien tiene este modem ayude please.
Saludos.

---

### Post by gmunioz on 2009-09-22
Hola eur...:

El modem, tiene muchas contras en GnuLinux,

pero en esto no tiene absolutamente nada que ver.

Los pasos que debes seguir son los siguientes:

1- Pulsa en Aplicaciones - Accesorios - Contraseñas y claves de cifrado 

2- Una vez allí pulsas en pestaña Contraseñas - opcion Contraseñas login

3- Pulsas el boton derecho y eliges cambiar la contraseña de desbloqueo

4- En la ventana emergente te pedirá la clave anterior y la clave nueva. 

Clave anterior la misma que siempre pones inicia el sistema

Clave nueva la misma que posee el usuario actual

Aceptar

---

### Post by lopulus on 2009-10-24
Hola gente: Yo no conozco mucho de linux y ademas me baje el beta de 9.10. No tengo la mas palida idea de como instalar dicho modem. Si alguien puede ayudarme...
Muchas gracias desde ya.

Lopulus

---

### Post by guillermolisi on 2009-10-24
> **lopulus said:**
> Hola gente: Yo no conozco mucho de linux y ademas me baje el beta de 9.10. No tengo la mas palida idea de como instalar dicho modem. Si alguien puede ayudarme...
Muchas gracias desde ya.

Lopulus
Mi recomendacion es que lo que intentes sobre ese modem 3G lo hagas con una version estable, ni con versiones alpha, beta o release candidate, asi trabajas sobre una base solida tipo la 9.04 o con la 9.10 que esta para ser liberada el 29/10, solo que esperaria un par de semana para que los ultimos arreglos se apliquen.

Hay varios tutoriales publicados, algunos para versiones anteriores de Ubuntu estan en el web site de Ubuntu-ar, Soporte - Tutoriales. Hay otros en el foro que podes buscar con la funcion Search this forum.

---

### Post by lopulus on 2009-10-24
Gracias guille: Ahora te pregunto, ¿Como hago para desinstalar esta version beta? Y ¿Que version me recomendarias instale?

---

### Post by guillermolisi on 2009-10-24
> **lopulus said:**
> Gracias guille: Ahora te pregunto, ¿Como hago para desinstalar esta version beta? Y ¿Que version me recomendarias instale?
No hay desinstalacion en Linux. Hay actualizaciones a versiones superiores o instalaciones nuevas (de la version que sea).

Como te dije, probaria con la 9.04 que esta muy estabilizada, te familiarizas con el contexto (eso te llevara algun tiempo) y mientras le das plazo a la 9.10 para que se libere y logre cierta estabilizacion como para que puedas concentrarte en el modem y no en otras cuestiones del entorno operativo.

---

### Post by lopulus on 2009-10-24
> **guillermolisi said:**
> No hay desinstalacion en Linux. Hay actualizaciones a versiones superiores o instalaciones nuevas (de la version que sea).

Como te dije, probaria con la 9.04 que esta muy estabilizada, te familiarizas con el contexto (eso te llevara algun tiempo) y mientras le das plazo a la 9.10 para que se libere y logre cierta estabilizacion como para que puedas concentrarte en el modem y no en otras cuestiones del entorno operativo.

Gracias guille nuevamente. Con la 9.04 es tan sencillo instalar como la 9.10?

---

### Post by guillermolisi on 2009-10-24
> **lopulus said:**
> Gracias guille nuevamente. Con la 9.04 es tan sencillo instalar como la 9.10?
En lineas generales te diria que si, que es tan facil una como otra. Si llegas a tener alguna duda, aqui estamos para ayudarte.

---

### Post by leonborgia on 2010-06-03
Alguien sabe como conectar el modemHuawei de Claro en el Ubuntu 10.4 net?

---

