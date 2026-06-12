---
title: "Problemas para instalar Karmic Koala"
date: 2009-12-08
forum: Hardware
---

### Post by mig65 on 2009-12-08
Soy nuevo en Linux y Ubuntu. Instalé con éxito las versiones 9.04 y 9.10 en sistemas en que Windows estaba previamente instalado y todo funciona OK. Ahora bien, con el mismo CD traté de instalar la versión 9.10 en un sistema sin SO instalado y obtengo la leyenda: "unable to find a medium containing a live file system" con las versiones 8.04, 9.04 y 9.10.
El HDD es de 10 Gb. y sólo tiene la partición habilitada sin formateo de ningún tipo (estaba con Windows y recibía el mismo mensaje, así que lo formateé). Lo curioso es que intentando "hacerme de Linux" sí o sí, bajé y traté de instalar el Fedora 12 con resultado similar (no se puede instalar, cambia sólo la leyenda).
Es un tema de hardware? Es una PC con un AMD Sempron 2200 y 384 Mb. de RAM aparte del disco de 10 Gb. que ya mencioné. No es un monstruo actual, de hecho es una maquinita de 2da. línea con la que pretendía ingresar el mundo antes de pasarme "con todo", ya que lo vengo probando con mucho éxito y entusiasmo en el laburo.
Agradeceré cualquier info para lograr instalar LINUX (cualquiera, aunque preferentemente Ubuntu).

---

### Post by guillermolisi on 2009-12-08
No termino de entender si el problema con esa maquina que mencionas es que no inicia con Live CD o que despues de instalar te dice que no puede iniciar porque no encuentra una particion activa o archivos para el boot.

Por las dudas, revisa que el disco rigido este conectado como Master en el canal IDE primario y que no tenga conflicto con la configuracion de la unidad de CD (que deberia estar como Master del canal secundario - preferentemente - o como Slave del canal primario).

---

