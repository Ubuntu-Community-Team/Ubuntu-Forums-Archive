---
title: "Vaio sin sonido ni touchpad"
date: 2010-11-23
forum: Hardware
---

### Post by ma_chro on 2010-11-23
Buenas, mis amigos.
Acabo de comprar una Vaio para actualizarme un poco.
Instalé Ubuntu 10.04 y lo único que no me quedó funcionando fue el sonido y el touchpad.
El touchpad ni siquiera lo reconoce.
¿me podrán ayudar por favor?
Les dejo los datos de la máquina:

Vaio VPCEE33EL
Gráficos: Ati Radeon 4200
Procesador: Athlon
Chipset: 880G

Desde ya les agradezco cualquier tipo de ayuda.
Saludos

Mario

Encontré en el foro de EEUU que hicieron lo siguiente para solucionarlo:

Originally Posted by Oaty View Post
Here’s the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX=”i8042.nopnp”
2. Run: sudo update-grub
3. Reboot.

¿esto implica que debo escribir en una terminal: edit /etc/defa.......................   ?
Desde ya muchas gracias por la ayuda.


Nueva actualización:
Finalmente me dí cuenta como ingresar la línea GRUB_CMD....   pero no me dió resultado. Continuo sin Touchpad.

Pude hacer que funcione el sonido.
La solución fue actualizar a 10.10  
Luego de bootear un par de veces el sonido comenzó a funcionar.

Tan pronto encuentre solución para el touchpad, lo comento aquí mismo.

---

### Post by magocsw on 2010-12-05
te queria consultar yo hace un mes compre esta notebook .. necesito instalarle ubuntu para la uni.. queria saber si pudiste solucionar lo del touch pad ? y como ... mi mail es . [email]otrapersona_mas@hotmail.com[/email]

---

### Post by ma_chro on 2010-12-06
Buenos días Magocsw, estuve investigando en un par de foros de EEUU.
Recopilé un conjunto de soluciones que todavía por cuestiones de tiempo no pude ponerme a probar.
Tan pronto las pruebe, si sale bien cuelgo la misma, sino te aviso y seguimos buscando.

Saludos

PD: Les dejo las web que recopilé por si alguien desea o tiene tiempo para probarlas.
Yo recién lo haré durante esta semana:

web:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

[http://krankeshirn.blogspot.com/2007/04/configurar-touchpad-en-ubuntu.html](http://krankeshirn.blogspot.com/2007/04/configurar-touchpad-en-ubuntu.html)

[http://www.ubuntu-es.org/node/1746](http://www.ubuntu-es.org/node/1746)

[http://www.ubuntu-es.org/?q=node/130246](http://www.ubuntu-es.org/?q=node/130246)

[http://tecnoloxiaxa.blogspot.com/2009/10/habilitar-y-configurar-el-touchpad-en.html](http://tecnoloxiaxa.blogspot.com/2009/10/habilitar-y-configurar-el-touchpad-en.html)

---

### Post by magocsw on 2010-12-07
hola como estas.. probe jejeje casi todo lo de los link's y ninguna solucion... no me lo detecta la unica manera que anda es con mouse usb..
al tirar : xinput list ( para ver los perisfericos )
           &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech                                	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sony Vaio Keys                          	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sony Visual Communication Camer         	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

el Audio tampoco me funciona como lo solucionaste vos?

---

### Post by magocsw on 2010-12-07
Hola hace un mes compre esta notebook , sony vaio vpcee33el.. al instalar ubuntu resulta que no me funciona para nada el touchpad , tengo que usar un mouse usb , si alquien pudiera ayudar..con alguna solucion , uso ubuntu para la universidad y me lleve una gran sorpresa... 
Probe algunas soluciones que lei por internet al tirarle.

sony@sony-VPCEE33EL:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech                                	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sony Vaio Keys                          	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sony Visual Communication Camer         	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

nose si me detecta o no el tocuhpad... me es de suma urgencia .. gracias

---

### Post by hectorivand on 2010-12-07
Hola Mago, acá viene un mago de verdad :P

Tema Touchpad primero.

abrí el archivo de configuración de grub: sudo gedit /etc/default/grub

En dicho archivo, incluí la siguiente línea: GRUB_CMDLINE_LINUX="i8042.nopnp"

Cerralo y actualiza el grub: sudo update-grub

Es una "borrachera" que no tiene razón aparente siendo que es un Touchpad Alps y usa los controladores Synaptics.

Contame como te fue.

Saludos
Nacho

---

### Post by hectorivand on 2010-12-07
Para ver el tema del audio alguno de los usuarios de las Vaio puede postear la salida de  los siguientes comandos.:

```
lsusb
```

```
lspci
```

Saludos
Nacho

---

### Post by magocsw on 2010-12-08
Hola Hector , super agradecido ahora me funciona perfectamente...a excepción de que cuando quiero dezplazar con el borde lateral derecho hacia arriba o abajo no funciona...y respectivamente con el borde inferior.. luego y descartando eso funciona bin El touchPad ... sos un genio ...

---- gracias ----:D

---

### Post by hectorivand on 2010-12-08
> **magocsw said:**
> Hola Hector , super agradecido ahora me funciona perfectamente...a excepción de que cuando quiero dezplazar con el borde lateral derecho hacia arriba o abajo no funciona...y respectivamente con el borde inferior.. luego y descartando eso funciona bin El touchPad ... sos un genio ...

---- gracias ----:D

Bueno ahora que te lo reconoció es más fácil, corre en la consola lo siguiente.:

```
sudo apt-get install gpointing-device-settings
```

Desde ahí vas a poder configurar lo que resta del touchpad, incluso el scrolling.

Saludos
Nacho

---

### Post by magocsw on 2010-12-09
hola hector no logro hacerlo funcionar ya probe con lo que me dijiste ... pero no logro.. alguna otra manera? desde ya muchas gracias

---

### Post by magocsw on 2010-12-09
Ma_chro paso a comentar como solucione lo del audio ...

hace click sobre sonido -> preferencias de sonido -> Hardware -> seleccione radeon HD 4200 -> perfil -> apagado -> y listo 

Asi me andubo el auido ... a mi no me funcionaba ponia youtube y cero sonido.. hice eso y funciono.. espero que te sirva..

-> HEctor respecto a lo de la configuracion del touchpad para el desplazamiento lateral vertical e inferior horizontal .. no e podido ... desde ya muchisimas gracias.. :D

---

### Post by magocsw on 2010-12-10
> **hectorivand said:**
> Para ver el tema del audio alguno de los usuarios de las Vaio puede postear la salida de  los siguientes comandos.:

```
lsusb
```

```
lspci
```

Saludos
Nacho

Porque puede ser que no me aparece la pestaña de touchpad en:
Sistema -> Preferencias -> raton -> y hay no me aparece touchpad.

no puedo configurarlo para el desplazamiento vertical y horizontal.

gracias!!!

---

### Post by ma_chro on 2010-12-13
> **hectorivand said:**
> Hola Mago, acá viene un mago de verdad :P

Tema Touchpad primero.

abrí el archivo de configuración de grub: sudo gedit /etc/default/grub

En dicho archivo, incluí la siguiente línea: GRUB_CMDLINE_LINUX="i8042.nopnp"

Cerralo y actualiza el grub: sudo update-grub

Es una "borrachera" que no tiene razón aparente siendo que es un Touchpad Alps y usa los controladores Synaptics.

Contame como te fue.

Saludos
Nacho

Buenos días Nacho, te copio parte del archivo que comentaste para ver si está bien.
Igualmente no me lo reconoce.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="i8042.nopnp"
GRUB_CMDLINE_LINUX=""

¿me podrás dar otra idea al respecto?

Desde ya muchas gracias.

Saludos

---

### Post by ma_chro on 2010-12-13
Muchas gracias por la ayuda. Ya tengo sonido.

Ahora estoy con el tema del touchpad.
Hice lo que indicó Nacho, pero por ahora no tengo solución.

Abrazo y si sabés algo avisá.

---

### Post by ma_chro on 2010-12-13
> **magocsw said:**
> Hola Hector , super agradecido ahora me funciona perfectamente...a excepción de que cuando quiero dezplazar con el borde lateral derecho hacia arriba o abajo no funciona...y respectivamente con el borde inferior.. luego y descartando eso funciona bin El touchPad ... sos un genio ...

---- gracias ----:D

Hola, continuo con el tema del touchpad.
¿La fila que te hizo incluir el otro Mago, donde la pusiste exactamente?
Porque a mí no me da resultado.

Saludos y gracias

---

### Post by ma_chro on 2010-12-13
> **ma_chro said:**
> Hola, continuo con el tema del touchpad.
¿La fila que te hizo incluir el otro Mago, donde la pusiste exactamente?
Porque a mí no me da resultado.

Saludos y gracias

Ya está el touchpad magocsw.
Ahora quedé igual que vos. No me funciona el desplazamiento lateral.
Tampoco me aparece la pestaña de touchpad en el menú "Ratón".
Si encontrás algo avisá.

Desde ya muchas gracias.

Les dejo como me quedó el archivo grub.
Lo único que hice fue bajar la línea que decía Nacho, 2 renglones más abajo.
Ahora funciona, no tengo idea porque no antes.

Abrazo


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="i8042.nopnp"

---

### Post by magocsw on 2010-12-14
> **ma_chro said:**
> Ya está el touchpad magocsw.
Ahora quedé igual que vos. No me funciona el desplazamiento lateral.
Tampoco me aparece la pestaña de touchpad en el menú "Ratón".
Si encontrás algo avisá.

Desde ya muchas gracias.

Les dejo como me quedó el archivo grub.
Lo único que hice fue bajar la línea que decía Nacho, 2 renglones más abajo.
Ahora funciona, no tengo idea porque no antes.

Abrazo


Hola disculpa que no conteste ... pasa que con visperas de fiestas... paso a comentarte que yo me encuentro en la misma situacion... estoy revisando esto

[http://vagos.es/showthread.php?t=1108901&page=3](http://vagos.es/showthread.php?t=1108901&page=3)

"no me a Funcionado "

Así que sigo esperando una posible solucion.. al menos ya me anda el TouchPad..

te mantendre informado!!:D

---

### Post by ma_chro on 2010-12-15
Pude averiguar que existe un problema con los touchpad ALPS.
Encontré en esta web que mucha gente del mundo tiene el mismo problema. En este sitio se reportan bugs y si buscás, encontrarás a muchos en la misma que nosotros.
Les dejo la web principal de los bugs:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux](https://bugs.edge.launchpad.net/ubuntu/+source/linux)

Pude leer también que están trabajando para solucionarlo.
Así que, paciencia :popcorn:

Abrazo

---

### Post by ma_chro on 2010-12-18
Y aquí les dejo la web donde creo que está mejor desarrollado el problema, donde puse el post con nuestro problema, inclusive se ve a mucha gente investigando el tema. Tanto usuarios como desarrolladores:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/565543)

Saludos

---

