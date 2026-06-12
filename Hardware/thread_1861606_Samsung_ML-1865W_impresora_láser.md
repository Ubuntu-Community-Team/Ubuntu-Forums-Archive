---
title: "Samsung ML-1865W impresora láser"
date: 2011-10-15
forum: Hardware
---

### Post by Killer Jacker on 2011-10-15
Estimados, ¿alguien ha podido instalar esta impresora? y mejor aún, dejarla funcionando por wi-fi?
Trato y trato, incluso logré instalar completo el driver, pero no pasa nada. Trato de imprimir y me pide una contraseña.
Alguien que me ayude porfa!!

:(

---

### Post by boingo_ on 2011-10-15
El lunes tengo que ir a una oficina a instalar esa misma impresora (estoy casi seguro), ellos usan windows, pero voy a llevar mi notebook, con ubuntu por supuesto, y trato de instalarla. asi que el lunes en la noche o el martes en la mañana puede que tenga noticias...

saludos

---

### Post by Killer Jacker on 2011-10-16
> **boingo_ said:**
> El lunes tengo que ir a una oficina a instalar esa misma impresora (estoy casi seguro), ellos usan windows, pero voy a llevar mi notebook, con ubuntu por supuesto, y trato de instalarla. asi que el lunes en la noche o el martes en la mañana puede que tenga noticias...

saludos
Muchas gracias Boingo_
Espero entonces. :redface:

---

### Post by boingo_ on 2011-10-18
hola, te cuento que instalé la impresora sin problemas, aquí va como lo hice:

1º conecté la impresora a la red wi-fi... para nada complicado, presionar el botón de conexión de la impresora y después el botón wps del router y listo!

2º instalé los driver en los equipos windows, poner el disco y siguiente, siguiente...

3º mientras tanto, descargué el controlador unificado desde el sitio de [samsung]("http://www.samsung.com/cl/consumer/pc-peripherals-printer/printers/mono-laser/ML-1865W/XBH/index.idx?pagetype=prd_detail&tab=support"), lo descomprimí, y desde la terminal ejecute como superusuario el archivo autorun. de ahi fue seguir las instrucciones basicamente: siguiente, siguiente... en un momento pregunta si la impresora esta conectada por usb o en red, yo le puse en red y la detectó altiro. me imagino que si no conectas la impresora a la red al principio, en este paso puedes instalarla por usb y luego configurar la conexion wifi.

y listo.

tengo instalado oneiric

espero que te sirva. 

saludos

---

### Post by Killer Jacker on 2011-10-19
> **boingo_ said:**
> hola, te cuento que instalé la impresora sin problemas, aquí va como lo hice:

1º conecté la impresora a la red wi-fi... para nada complicado, presionar el botón de conexión de la impresora y después el botón wps del router y listo!

2º instalé los driver en los equipos windows, poner el disco y siguiente, siguiente...

3º mientras tanto, descargué el controlador unificado desde el sitio de [samsung]("http://www.samsung.com/cl/consumer/pc-peripherals-printer/printers/mono-laser/ML-1865W/XBH/index.idx?pagetype=prd_detail&tab=support"), lo descomprimí, y desde la terminal ejecute como superusuario el archivo autorun. de ahi fue seguir las instrucciones basicamente: siguiente, siguiente... en un momento pregunta si la impresora esta conectada por usb o en red, yo le puse en red y la detectó altiro. me imagino que si no conectas la impresora a la red al principio, en este paso puedes instalarla por usb y luego configurar la conexion wifi.

y listo.

tengo instalado oneiric

espero que te sirva. 

saludos
Hola boingo_. Gracias por tu post.
Te comento que tengo, principalmente, 2 inconvenientes:

1. Mi router no tiene WPS
2. Cuando trato de  instalar el controlador, se me cierra la sesión antes de que termine la instalación.

:(

De todos modos ayer el Ubuntu hizo unas actualizaciones en la mañana entre las que creo que había algo relativo al CUPS, que era donde se me cerraba la sesión en el instalador.

Ahora voy a tratar de hacer algo más. Les cuento a ver qué pasa... ;)

---

### Post by Killer Jacker on 2011-10-20
Bueno, les comento que logré hacer funcionar la impresora, pero sólo por USB. Les cuento...:popcorn:

Lo que hice fue iniciar sesión, pero no en X, sólo en consola. Entonces instalé los drivers, el Panel y la herramienta para  configurar, tal como se indica en las instrucciones.

Se instaló todo correctamente.

El detalle esencial, es que, después de arrancar sesión normalmente (en Gnome), se debe abrir el Samsung Unified Driver Configurator. Si no lo encuentran en el escritorio (que es lo más probable) está en /opt/Samsung/mfp/bin/Configurator. Se darán cuenta que ya hay una impresora instalada como default. Luego, con ese programa abierto y la impresora prendida, desconecten la impresora del USB. Esperen unos segundos y conéctenla denuevo. Saldrá el mensaje de "Instalando nueva impresora". Esperen unos instantes a que salga el mensaje "Nueva impresora instalada correctamente" y verán que en el SUDC aparecerá otra impresora ML-1865W, pero con una ruta distinta. Esta nueva impresora déjenla como default ya que es la que funciona correctamente. La otra se puede eliminar.:KS

Si logro hacerla funcionar por Wi-Fi, también les cuento acá.

Saludos.

---

