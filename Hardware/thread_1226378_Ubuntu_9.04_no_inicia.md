---
title: "Ubuntu 9.04 no inicia"
date: 2009-07-29
forum: Hardware
---

### Post by ketzelleshelle on 2009-07-29
Cuando enciendo la laptop, aparece el grub, elijo Ubuntu, aparece el logo, la barra de carga, carga sin problemas y al momento de iniciar se queda todo negro... 

Cuál podría ser el problema o alguna pista de por donde comenzar?

Muchas Gracias!

Ketzel

---

### Post by Mauro22 on 2009-07-29
Cuando llegas a la parte de la pantalla negra hace:

Control + Alt + F1

te lleva a la consola, logueate con tu user & pass

hace:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
```

Por si las moscas ;) igual no anda...

y ahora:

```
sudo dpkg-reconfigure xserver-xorg
```


Segui el asistente y cuando volves a la consola hace:

```
sudo /etc/init.d/gdm restart
```


Porque se puse negra? alguna actualizacion??

---

### Post by ketzelleshelle on 2009-07-29
Gracias por responder.
Arrancamos mal...cuando se pone la pantalla negra, Control+Alt+F1 no hace nada...

No se porqué se puso negra, hacía como diez días q no usaba Ubuntu en esta máquina ya que estaba de viaje, y hoy cuando la encendí pasó eso...

No se porqué se me hace que tenga que ver tal vez con algo de la placa de video...?

Gracias.

---

### Post by guillermolisi on 2009-07-29
Danos detalles de la placa de video, marca, modelo, y del monitor.

---

### Post by ketzelleshelle on 2009-07-29
Muchachos me dan una mano? No pude solucionarlo y no encuentro por ningún lado... Me aconsejan reinstalar?

> **guillermolisi said:**
> Danos detalles de la placa de video, marca, modelo, y del monitor.

Dell Inspiron 1525
Procesador: Intel Core 2 Duo T5500
Adaptador Gráfico: Intel Graphics Media Accelerator (GMA) X3100
Pantalla: 15.4 pulgadas, 16:10, 1280x800 pixeles

Y puedo dar un dato más aunque no sé si será útil: luego de hacer la carga de Ubuntu con el logo, suceden una serie de pantallazos entre grises y negros.

---

### Post by ketzelleshelle on 2009-08-04
> **Mauro22 said:**
> Cuando llegas a la parte de la pantalla negra hace:

Control + Alt + F1

te lleva a la consola, logueate con tu user & pass

hace:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
```

Por si las moscas ;) igual no anda...

y ahora:

```
sudo dpkg-reconfigure xserver-xorg
```


Segui el asistente y cuando volves a la consola hace:

```
sudo /etc/init.d/gdm restart
```


Porque se puse negra? alguna actualizacion??

Finalmente logré terminar lo que me propusiste:

En primer lugar te cuento que el comando es gmd y no gdm, estuve horas hasta q me avive.

Y en segundo lugar...lamento decir que todo sigue igual.

Alguna otra sugerencia?

Gracias!

---

### Post by Mauro22 on 2009-08-04
El comando es gdm  viene de Gnome Display Manager... gmd es otra cosa.. Yo te dije gdm porque dijiste que tenes Ubuntu, si tenes kde tenes que poner kdm

gdm es para Gnome
kdm es para KDE  Kde Display Manger


Escuchas el ruido del login, a pesar de no ver nada??

Por ahi esta fuera de frecuencia, podes probar:

a) poner tu usuario y contraseña a ver si inicia igual.

b) Apretar control + alt + +  (control alt mas)  -o-    control + alt + - (control alt menos) para ir cambiando las resoluciones del gdm...

---

### Post by ketzelleshelle on 2009-08-04
Evidentemente lo editaste porque el día que me lo pasaste lo imprimí y dice gmd. Gracias.

No hace el ruido del inicio, no puedo poner user ni pass y ninguno de los dos (ctrl + + ctrl + -) funciona...

Esto está difícil...

---

### Post by Mauro22 on 2009-08-04
La verdad que si... pero todo tiene solucion, no? esa es la definicion de problema


A ver... en el GRUB tenes varios Kernels para elegir?

Si hay, probaste con esos? Son todos los que no dicen ni recovery ni nada mas, solo el numero de kernel y -generic


Tambien podes irte a la consola, loguearte y hacer un:

sudo apt-get upgrade 

Para ver si hay una actualizacion "critica" que te impide levantar video.

---

### Post by ketzelleshelle on 2009-08-04
Probé con todos los kernel, probé con el menú recovery y nada.

El upgrade tampoco actualiza más que el brasero...

Un dato más: creo recordar (o sea es posible) que el problema comenzó luego de hacer un TV Out...

---

### Post by pablocp_16 on 2009-09-14
hola. a mi me pasa lo mismo que a ti por favor me gustaria que me dijeras si has encontrado alguna solucion de como hacerlo ya que estoy desesperado y no puedo acceder a ubuntu yo utilizo 9.04

---

### Post by gmunioz on 2009-09-14
Hola...:

Si Ubuntu no inicia en modo gráfico, prueban:

Pulsar escape cuando inicia el ordenador.

En el menu del Grub elegir recovery mode
(es la segunda opción)

En el submenu emergente, elegir netroot

Si inicia, inicia en consola, como administrador

y significa que hay un fallo en las gráficas.

Entonces se puede intentar cambiar el driver a vesa

cuyo aspecto no es muy lindo pero permite iniciar

en modo gráfico para intentar solucionar desde allì.

Ejecutar 

nano /etc/X11/xorg.conf  

Buscar la sección Device y dejarla asi

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver          "vesa"
EndSection
```

Guardar el archivo

Cerrar nano

ejecutar

startx

Y leer los mensajes si hay errores, para

postearlos.

---

### Post by walterpy on 2009-09-24
yo tambien tuve ese problema hace 2 dias...y lo solucione con esto

```
sudo apt-get remove --purge xorg-driver-fglrx
```

espero que se solucione tu problema..a mi me paso eso cuando instale el compiz

---

### Post by Hei Ku on 2009-09-24
> **walterpy said:**
> yo tambien tuve ese problema hace 2 dias...y lo solucione con esto

```
sudo apt-get remove --purge xorg-driver-fglrx
```

espero que se solucione tu problema..a mi me paso eso cuando instale el compiz

Esto lo que hace es desinstalar el driver fglrx, el driver privativo de ATI. Dependiendo del modelo de placa, no vas a tener aceleracion 3d si lo desinstalas.

Por favor, cuando den un comando expliquen que es lo que estan haciendo. O digan que no saben.

---

### Post by ketzelleshelle on 2009-09-25
Lamentablemente no me quedó más remedio que reinstalar.
Probé todo lo que me dijeron, busqué info por todos lados y no pude solucionarlo...
Gracias de todos modos por la ayuda.

---

