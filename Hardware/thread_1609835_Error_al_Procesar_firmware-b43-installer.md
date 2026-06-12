---
title: "Error al Procesar firmware-b43-installer"
date: 2010-10-30
forum: Hardware
---

### Post by Pan0ramix on 2010-10-30
No encuentro la forma de arreglar este error recurrente en Maverick 10.10 instalado en una netbook. 

Cuando actualizo los controladores adicionales tal parece que los privativos para el wireless de Broadcom b43 estan faltando. Cuando lo activo da error de instalación (System error: InstallArchives() failed). Hasta aqui no tendría inconvenientes porque ya tengo funcionando el wireless con un controlador Broadcom STA.

Pero... cada vez que actualizo algun paquete o instalo una nueva aplicación ya sea desde el gestor de synaptic o del centro de software termina con el siguiente mensaje:

"Falló la operación con el paquete:
Error al procesar firmware-b43-installer (-configure). El subproceso script post installation devolvió el código de salida de error 1. "

Ajá. Y? Nada, que se instalan los paquetes y las apps pero siempre termina con este molesto mensaje. 

Un detalle: tuve que volver a instalar los "drivers" de la broadcom por cable ethernet porque el wireless no andaba a causa de estos faltantes. Ahora lo tengo funcionando pero siempre me tiró este error a pesar de haber chequeado nuevamente los controladores adicionales

Si alguno tiene alguna pista, agradecido.

---

### Post by benja22 on 2010-11-02
a mucha gente le ha pasado eso
mira esto:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111)
¿es tu error?

si no lo logras hacer funcionar, puedes probar instalar el driver de windows y usarlo con ndiswrapper en ubuntu ;)

---

### Post by asterix77 on 2010-11-04
En el siguiente foro, se trata un problema al parecer igual.

[http://ubuntuforums.org/showthread.php?t=1609861&page=2](http://ubuntuforums.org/showthread.php?t=1609861&page=2)

Podrías probar una posible solución.

Saludos

---

### Post by Pan0ramix on 2010-11-06
> **benja22 said:**
> a mucha gente le ha pasado eso
mira esto:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111)
¿es tu error?

si no lo logras hacer funcionar, puedes probar instalar el driver de windows y usarlo con ndiswrapper en ubuntu ;)

Exactamente, ese es el error.
Estoy siguiendo el log y me parece que ya han liberado un fix, pero siguen habiendo reportes.

Asterix77: estoy siguiendo el hilo que posteaste, el error en debian es similar pero no sé si aplica la solución. Definitivamente ha resultado ser un bug de 10.10. 

Mientras tanto probaré con la sugerencia de [https://launchpad.net/~magicfab](https://launchpad.net/~magicfab) donde indica:

"As a workaround you can: 

[COLOR="DarkRed"]**sudo apt-get remove --purge firmware-b43-installer **[/COLOR]

and then use the STA driver instead."

Lo interesante es que:

a) la tarjeta inalámbrica funciona correctamente sin problemas
b) las instalaciones/actualizaciones se llevan a cabo sin problema aparente

pero el molesto final de instalación sigue alli.

Veremos si se me da la solución.

---

### Post by Pan0ramix on 2010-11-07
RESUELTO!
Con la orden de remover y purgar el paquete se ha solucionado el problema del final de instalación.
Le solicito a quien corresponda y si es propicio modificar el título del post agregando que está solucionado.

gracias

---

### Post by benja22 on 2010-11-12
Me alegro :)

PD:Que alguien le ponga Resuelto al titulo

---

### Post by ferrueda on 2011-01-23
Muchas gracias, se me ha resuelto el problema, tengo una dell mini 10 con instalación limpia de ubuntu 10.10 y tenía el mismo problema, se me ha resuelto como lo indicaron:

sudo apt-get remove --purge firmware-b43-installer

and then use the STA driver instead."

Esta respuesta fue realizada con wifi. =)

Saludos
Ferrueda

---

