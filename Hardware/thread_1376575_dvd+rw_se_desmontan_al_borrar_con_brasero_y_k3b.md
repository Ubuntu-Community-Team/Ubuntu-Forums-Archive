---
title: "dvd+rw :se desmontan al borrar con brasero y k3b"
date: 2010-01-09
forum: Hardware
---

### Post by paulita78 on 2010-01-09
Saludos amigos chilenos!ya hacia tiempo que no me daba una vuelta por aqui...
Verán,tengo un problema cuando intento borrar un dvd+rw desde cualquiera de estos dos programas.Obtengo como mensaje de error lo siguiente:
No se pudo montar Disco óptico virgen
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found
El disco se me borra correctamente,pero la unidad desaparece.Eso si,ocurre mientras tengo ese disco borrado en la disquera,porque al expulsarlo vuelve a aparecer.Esto me ocurre desde que instalé Karmic,que tuve que hacerlo en limpio porque la actualización desde jaunty no me fué del todo bien.Es el único problema que no he podido resolver,asi que si pueden ayudarme les estaré muy agradecida.
Por cierto,manejo la versión 64 de Karmic,y si necesitan algun dato más acerca de mi hardware se lo facilitaré gustosamente.
Un saludo a todos y aunque sea un poco tarde,feliz año 2010

---

### Post by Carlos C on 2010-01-10
¿Qué versión de kernel tienes instalada? Puedes verlo con:
```
uname -a
```
Al parecer hubo problemas con la versión anterior del kernel, por lo que te recomiendo actualizar en caso de que no lo hayas hecho.

Saludos.

---

### Post by CdK1 on 2010-01-10
Parece ser un error de gvfs..., te ecomiendo actualziar y leer en launchpad sobre algún bug similar...;

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/251991](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/251991)
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/504455](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/504455)

---

### Post by paulita78 on 2010-01-11
Hola! En primer lugar gracias por responderme.Mira Carlos,esta es la versión de kernel que tengo: 2.6.31-17 .Se me actualizó la pasada semana si mal no recuerdo,así que debe ser la última.En cuanto a lo que me indicas CdK1,leí algo en un foro alemán,pero como de alemán no tengo mucha idea y los traductores no lo hacen como a una le gustaría tampoco me enteré de mucho,excepto que algo tenia que ver con gvfs.El problema que más se parece al mio,bueno,que es exactamente el mismo,es el del segundo enlace,que es lo mas parecido que he encontrado a mi problema y como puede ver no hay respuesta.Con ningún otro dispositivo tengo ese problema,incluso con dvd+r y -r o cd-r vírgenes,los monta al momento,y el disco duro externo o los pen drive también.En fin,tendré que esperar a una nueva versión o a que reparen el bug,que se le va a hacer...
Muchas gracias por vuestro interés y un saludo desde España

---

### Post by CdK1 on 2010-01-14
Es lo más recomendable, esperar que solucionen el problema... deberías revisar el segundo enlace cada cierto tiempo para ver si está solucionado o tienen alguna manera de hacerlo....

---

