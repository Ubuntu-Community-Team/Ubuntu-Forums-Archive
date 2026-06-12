---
title: "Problema con la conexión por wifi con mi tarjeta broadcom b43"
date: 2010-08-13
forum: Hardware
---

### Post by pelaolinux on 2010-08-13
Hola! 

bueno mi problema es el siguiente: 

tengo un notebook COMPAQ Presario V2000 el cual me función perfectamente en ubuntu 10.04, pero tuve un problema al momento de conectarme por wifi que al entrar a la red wifi de mi casa me pide la contraseña luego empieza a conectarse y luego me regresa a pedir la contraseña y asi sucesivamente… la forma que configure la tarjeta fue de la misma forma que sale en este video. (la única diferencia que a mí me reconoce solo la opción b43)
   
  [http://www.youtube.com/watch?v=T0ovUDP-1NU](http://www.youtube.com/watch?v=T0ovUDP-1NU)
   
   
   
  Saludos y espero que se puedan dar un tiempo para que ayuden! 


se me olvidaba algo … desde Windows me puedo conectar normal mente a si que descarto que sea problema del MODEM …

---

### Post by asterix77 on 2010-08-13
¿Que usas para conectarte? Network Manager o Wicd?. En lo personal prefiero el wicd, sobretodo para redes wifi, ya que con el NM he tenido problemas similares a los descritos por ti.

Escribe en consola lo siguiente y pegalo acá para saber el modelo exacto de tu tarjeta.

#sudo lspci | grep BCM

#iwconfig

#ifconfig


Saludos

---

### Post by pelaolinux on 2010-08-14
> **asterix77 said:**
> ¿Que usas para conectarte? Network Manager o Wicd?. En lo personal prefiero el wicd, sobretodo para redes wifi, ya que con el NM he tenido problemas similares a los descritos por ti.

Escribe en consola lo siguiente y pegalo acá para saber el modelo exacto de tu tarjeta.

#sudo lspci | grep BCM

#iwconfig

#ifconfig


Saludos


muchas gracias por intentar de ayudarme pero el problema era solo configurar el tipo de contraseña WEP ... 

saludos que estés excelente!:D

---

