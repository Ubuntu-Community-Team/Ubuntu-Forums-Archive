---
title: "Problema al instalar programas en Ubuntu 11.04"
date: 2011-05-02
forum: Instalación y Actualización
---

### Post by SSolid on 2011-05-02
Hola Amigos, Me presento, soy Bruno Diaz y soy nuevo en este mundo del software libre, acabo de actualizar mi S.O. a Ubuntu 11.04, pero al momento de intentar instalar un programa me envia el siguiente error:

Instale los siguientes archivos o paquetes: /usr/lib/gconv/UTF-16.so

No se que significa ni como solucionarlo, si alguno pudiera darme una mano se lo agradeceria mucho, de antemano gracias y Saludos !

---

### Post by rudyairlines on 2011-05-04
a mi me ocurre lo mismo

---

### Post by Raymar on 2011-05-16
> **SSolid said:**
> Hola Amigos, Me presento, soy Bruno Diaz y soy nuevo en este mundo del software libre, acabo de actualizar mi S.O. a Ubuntu 11.04, pero al momento de intentar instalar un programa me envia el siguiente error:

Instale los siguientes archivos o paquetes: /usr/lib/gconv/UTF-16.so

No se que significa ni como solucionarlo, si alguno pudiera darme una mano se lo agradeceria mucho, de antemano gracias y Saludos !

tenes que generar este link 


ln -s /usr/lib/i386-linux-gnu/gconv/ /usr/lib/gconv

en el caso que no tengas las librerías instalate el paquete python-hachoir-core con synaptic

con esas dos cosas sale andando 

Saludos

---

