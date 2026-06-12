---
title: "HOW-TO. Pad de PSX como mouse en GNU/linux"
date: 2011-04-26
forum: Hardware
---

### Post by josecuervo86 on 2011-04-26
Hola a Todos!! Tanto tiempo!!

Hoy les traigo un sencillo "How To" para aquellos que tengan un pad de playstation y quieran usarlo como mouse. No creo que sean muchos, pero bueno, tengan en cuenta que si siguen el tutorial "a medias" les va a servir como Joystick, asi que tal vez a los gamaers les sirva =).

Bueno, empecemos.

**1.- Conseguirse un adaptador de psx a usb**

Hay bastantes en el mercado, yo consegui uno por $45 que tiene la posibilidad de adaptarle 2 joystick.

**2.- Haciendo que GNU/Linux reconozca el joystick**
Para eso, lo primero que hay que hacer es hacer que cargue automaticamente los modulos necesarios para que lo reconozca. Estos modulos son:

[B]joydev
gamecon[/B]

Para esto, lo que hay que hacer es como primer paso agregar los modulos al arranque:

```
sudo gedit /etc/modules
```

y agregamos los dos modulos uno por linea. Tambien deberemos quitar el modulo **lp** para lo cual basta con borrarlo de ese mismo fichero.

deberia quedar mas o menos asi:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

rtc
[B]joydev
gamecon[/B]

```

A continuación lo que haremos es "blacklistear" al modulo lp

```
sudo gedit /etc/modprobe.d/blacklist
```

Y agregamos una linea que diga

```
blacklist lp
```


Por último, nos queda decirle al modulo que tipo de joystick le vamos a conectar:

```
sudo gedit /etc/modprobe.d/options
```

Tenemos que escribir lo siguiente:

```
options gamecon map=0,7
```

Lo que indica el 7 es el tipo de joystick que en este caso es el de psx. Si queres conectar los dos como en mi caso deberia ser 

```
options gamecon map=0,7,7
```

Con esto, ya tendria que reconocer de movida al joystick. Para comprobarlo, conectamos el joystick y con

```
dmesg
```

deberia detectarlo mas o menos de la siguiente manera:

```
input: PSX controller as /devices/virtual/input/input6
```

Bueno, hasta aca la primer parte. El Joystick ya deberia funcionar como tal, pero para comprobarlo necesitamos instalar un simple paquete que se llama **joystick**

```
sudo apt-get install joystick
```

Cuando conectamos un joystick, se le asigna una posición en /dev/input/jsX, donde X es la posición que toma, siendo el primero en conectarse el 0, luego el 1 y asi.

Para corroborar si esta siendo detectado basta poner:

```
jstest /dev/input/js0
```


Apareceran muchos numeros, los cuales estan asignados a cada boton del pad. Para probar si los reconoce solo basta apretarlos y ver si cambian de valor.

**Si me siguieron hasta aca, ya tienen joystick para jugar!! =)**


**3.- Haciendo que el Joystick funcione como Mouse**

Llegamos a la parte final del tuto. Bueno, el proximo necesario para que funque es bajarse el siguiente paquete: **xserver-xorg-input-joystick**

```
sudo apt-get install xserver-xorg-input-joystick
```

Este paquete contiene los modulos necesarios para que el Xorg reconozca los imputs del joystick como si vinieran del mouse.

Una vez instalado, el ultimo paso es modificar el **Xorg.conf**

```
sudo gedit /etc/X11/xorg.conf
```

Al Xorg hay que agregarle estas lineas:

```

Section "InputDevice"
	Identifier "Joystick"
	Driver "joystick"
	Option "Device"   "/dev/input/js0"
EndSection

```

Donde dice "...js0" ustedes deben agregar la posición donde se encuentre el suyo.

Una vez agregadas esas lineas guardamos el Xorg y reiniciamos la PC.

Ya deberian poder usar su Joystick como mouse!!


Espero que lo prueben y les sirva!!

Cualquier duda, consulten!!

[B]Sitios de Consulta!!

[http://bulma.net/body.phtml?nIdNoticia=1268](http://bulma.net/body.phtml?nIdNoticia=1268)
[http://www.linuxquestions.org/questions/linux-hardware-18/adding-usb-joystick-as-2nd-x11-pointer-449434/](http://www.linuxquestions.org/questions/linux-hardware-18/adding-usb-joystick-as-2nd-x11-pointer-449434/)
[http://www.linuxcertif.com/man/4/joystick/50490/](http://www.linuxcertif.com/man/4/joystick/50490/)[/B]

---

