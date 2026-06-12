---
title: "Otra vez, ayuda con interfaz grafica"
date: 2009-06-17
forum: Hardware
---

### Post by Plastiko on 2009-06-17
instale xserver-xorg-core por "querer" arreglar un problema grafico y resulto peor.

cuando reincie no arranca gnome y sale a modo texto.

el fallo:

Usplash: Setting mode 1152x864 failed

que puedo hacer?

saludos.

---

### Post by gmunioz on 2009-06-17
Hola pla....:

¿Qué distribución?  ¿Qué tarjeta de video? 

A ciegas dos opciones:

1- Ejecuta en la consola en que quedas:

sudo apt-get purge xserver-xorg-core

Para eliminar el paquete que dices causó el problema.

2- Al iniciar el ordenador pulsa escape.

En el menu del Grub elige recuperación

En el submenu emergente elige fix de las gráficas

Reinicia.

---

### Post by Plastiko on 2009-06-17
> **gmunioz said:**
> Hola pla....:

¿Qué distribución?  ¿Qué tarjeta de video? 

A ciegas dos opciones:

1- Ejecuta en la consola en que quedas:

sudo apt-get purge xserver-xorg-core

Para eliminar el paquete que dices causó el problema.

2- Al iniciar el ordenador pulsa escape.

En el menu del Grub elige recuperación

En el submenu emergente elige fix de las gráficas

Reinicia.

OK ya hice lo que me mencionaste y no funciono.

Te comento que uso Ubuntu 9.4 y la tarjeta es una Nvidia Geforce 440 Mx 64mb.

Este es el mensaje que me sale.

Gracias y saludos.

---

### Post by pablo.s on 2009-06-17
No debes desinstalar el
paquete xserver-xorg-core
porque como lo dice en el
nombre, es el "corazon" del
servidor X. De hecho, lo
vas a tener que instalar si
queres que funcione.
El problema de Usplash se
debe a una resolucion que muy
probablemente no soporte
tu monitor, porque es una
resolucion de tipo wide y
por lo que se ve tu monitor
es CRT (de tubo).

---

### Post by Plastiko on 2009-06-17
> **pablo.s said:**
> No debes desinstalar el
paquete xserver-xorg-core
porque como lo dice en el
nombre, es el "corazon" del
servidor X. De hecho, lo
vas a tener que instalar si
queres que funcione.
El problema de Usplash se
debe a una resolucion que muy
probablemente no soporte
tu monitor, porque es una
resolucion de tipo wide y
por lo que se ve tu monitor
es CRT (de tubo).

Ya veo, pero como vuelvo a instalar este paquete? 

Hice esto porque tenia el problema de la terminal se ve en blanco y la barra de minizar, maximizar y cerrar ventanas desaparecia.

---

### Post by pablo.s on 2009-06-17
> **Plastiko said:**
> Ya veo, pero como vuelvo a instalar este paquete? 

Depende. Veo que has instalado
hace un par de dias. Si no te
ha quedado mucha información que
no puedas guardar, te recomiendo
reinstalación. Es uno de los pocos
casos que diria de reinstalar.
Si tienes conectividad, puedes
instalarlo con

[COLOR="DarkGreen"]**sudo apt-get install xserver-xorg-core**[/COLOR]

---

### Post by Plastiko on 2009-06-17
> **pablo.s said:**
> Depende. Veo que has instalado
hace un par de dias. Si no te
ha quedado mucha información que
no puedas guardar, te recomiendo
reinstalación. Es uno de los pocos
casos que diria de reinstalar.
Si tienes conectividad, puedes
instalarlo con

[COLOR=DarkGreen]**sudo apt-get install xserver-xorg-core**[/COLOR]


Perfecto te agradezco la ayuda ya arranca Gnome, pero ahora, como te decía en el post anterior sigo teniendo el problema de los bordes de las ventanas que no se muestran y la terminal se ve en blanco, tengo la configuración de la apariencia con efectos en normal, como podria resolverlo?

Saludos.

---

### Post by pablo.s on 2009-06-17
Los bordes de arriba?
Te puede estar faltando
el complemento Emerald.
Fijate en Synaptic todos los
paquetes que se llamen
asi.
Que significa que la terminal
se ve en blanco? Que no está
transparente?

---

### Post by Plastiko on 2009-06-17
> **pablo.s said:**
> Los bordes de arriba?
Te puede estar faltando
el complemento Emerald.
Fijate en Synaptic todos los
paquetes que se llamen
asi.
Que significa que la terminal
se ve en blanco? Que no está
transparente?

OK, buscare, el compiz esta configurado pero faltan por agregar y no se si sean necesario agregar por ejemplo el compizconfig settings manager.

si toda la terminal se ve en blanco mira.

Ni bordes ni terminal-

---

### Post by pablo.s on 2009-06-17
Cuando configures Compiz
fijate de utilizar Metacity o
Emerald.
La terminal la puedes poner
transparente desde el menú
Editar -> Preferencias del perfil
->Fondo -> Fondo transparente

y le das el porcentaje de
transparencia que quieras.

---

### Post by Plastiko on 2009-06-18
> **pablo.s said:**
> Cuando configures Compiz
fijate de utilizar Metacity o
Emerald.
La terminal la puedes poner
transparente desde el menú
Editar -> Preferencias del perfil
->Fondo -> Fondo transparente

y le das el porcentaje de
transparencia que quieras.

No, sigue sin aparecerme el bordo y la terminal.

Si no uso los efectos si me los muestra pero si le pongo efectos visuales en normal o extra es cuando desaparece los bordes y la terminal en blanco.

seguiré leyendo y gracias una vez mas por la ayuda.

Saludos.

---

### Post by staar on 2009-06-18
la forma más fácil de tener los bordes de ventanas de nuevo, es instalando el paquete fusion-icon y seleccionando en sus opciones, Metacity como decorador de ventanas...

saludos

---

### Post by Plastiko on 2009-06-20
> **staar said:**
> la forma más fácil de tener los bordes de ventanas de nuevo, es instalando el paquete fusion-icon y seleccionando en sus opciones, Metacity como decorador de ventanas...

saludos

Por fin! gracias ya instale el fusion-icon y ya puedo visualizar los efectos y la terminal, gracias a todos.

Saludos.

---

