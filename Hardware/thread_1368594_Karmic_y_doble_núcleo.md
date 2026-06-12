---
title: "Karmic y doble núcleo"
date: 2009-12-30
forum: Hardware
---

### Post by nechus on 2009-12-30
Tengo un Acer Aspire 5738, y según Sysinfo la CPU es Intel Core 2 Duo T6500 @ 2.10GHz, pero a veces siento que las cosas en mi notebook no andan más rápido que en mi antiguo Compaq C700, que tenía un Celeron común y corriente.

¿Cómo puedo saber si Ubuntu está realmente sacando provecho de los dos núcleos y todo eso?

---

### Post by Carlos C on 2009-12-30
¿instalaste ubuntu 32 o 64 bit?

---

### Post by moreback on 2009-12-30
Los Core 2 Duo tienen arquitectura de 64 bits, por lo que lo mejor es instalarles Ubuntu 64 bits ya que [el rendimiento es mucho mejor que en 32 bits]("http://www.omgubuntu.co.uk/2009/12/ubuntu-64bit-really-is-faster-than.html").

Si quieres ver cómo Linux administra tus núcleos, puedes mirar un buen rato el Monitor del sistema (**Sistema -> Administración -> Monitor del sistema**) para que veas cómo distribuye la carga entre los dos núcleos (se nota más cuando tienes una aplicación al 100% de CPU).

Saludos.

---

### Post by nechus on 2009-12-30
:shock: ¿64 bits?  ¿Me lo juran?  Lo sospechaba, pero descarté la idea cuando cuando quise instalar una versión de Windows de 64 bits en VirtualBox y me la rechazó. Pero ya que lo mencionan, voy a probar.  Gracias

---

### Post by bichopro on 2009-12-30
Ademas que normalmente trabaja con el procesador ondemand, eso quiere decir que a
esta al minimo de su capacidad hasta que le exiges mas, o cual conlleva un pequeño (no se si es la palabra correcta) delay o desfaz al pedir velocidad al procesador.
boton derecho sobre el panel, luego añadir al panel, luego agregas el Monitor de frecuencia de la CPU y ahi ajustas la velocidad de acuerdo a tus necesidades

---

### Post by moreback on 2009-12-31
> **bichopro said:**
> Ademas que normalmente trabaja con el procesador ondemand, eso quiere decir que a
esta al minimo de su capacidad hasta que le exiges mas, o cual conlleva un pequeño (no se si es la palabra correcta) delay o desfaz al pedir velocidad al procesador.
boton derecho sobre el panel, luego añadir al panel, luego agregas el Monitor de frecuencia de la CPU y ahi ajustas la velocidad de acuerdo a tus necesidades

Y si quieres puedes remover el script que te cambia el gobernador a OnDemand para que quede siempre en Performance: [http://pcarmona.wordpress.com/2009/06/15/%c2%a1maldito-script/]("http://pcarmona.wordpress.com/2009/06/15/%c2%a1maldito-script/")

Saludos.

---

### Post by nechus on 2009-12-31
:mrgreen: ¡ERA CIERTO!  Tengo un computador de 64 bits... ¡y no tenía ni idea! Pero es que no sale escrito en ninguna parte. En fin, voy a tener que darme la pega de instalar el sistema de nuevo, a ver si Compiz ahora funciona suavecito. Ahora estoy escribiendo desde el LiveCD de 64 bits y Compiz funciona mejor que en el sistema de 32 bits que tengo instalado.

Gracias por las sugerencias!!! \\:D/

---

### Post by Carlos C on 2010-01-04
¿Lo damos por resuelto entonces?

---

### Post by nechus on 2010-01-26
Sí. Hay que darlo por resuelto. Esta cosa vuela ahora!!!!!

---

