---
title: "Regnum ONline con placa intel 965 onboard"
date: 2008-03-25
forum: Hardware
---

### Post by Etrigan on 2008-03-25
Alguien consiguio hacer andar el Regnum online con el chip Intel 965?? 
Dell vostro 1400

hace rato que vengo probando y no pasa nada. 
Tambien el problema que tengo es que para que arraquen los efectos visuales tube que quitar mi laca de la blacklist de compiz, pero a la hora de reproducir un DVD, tengo que desactivar los efectos visuales porque no me muestra nada de nada! 

tampoco pude hacer andar la webcam ni el microfono fontal, segui cuanto instructivo encontre, pero nada...

---

### Post by sajnox on 2008-03-25
Para ver un DVD con compiz activado, por lo menos con vlc tenes que setear lo siguiente:

Opciones\Preferencias\Modulos de Salida\Salida de Video X11

Para ver esto tenes que tener el checkbox de opciones avanzadas activado

Espero que te sirva.

---

### Post by leo_rockway on 2008-03-26
Por el problema del Regnum OnLine: ellos no tienen soporte oficial para Linux, pero en su foro siempre encontrás a alguien que te da una mano (no es raro que los developers anden dando vueltas para ver en que poder mejorar el cliente).

---

### Post by MaReaDo^ on 2008-03-27
que placa de sonido tenes? porque hay mucha gente que con placas intel hda tienen dramas con el microfono, es mas, yo tuve y tengo una intel hda
por eso pregunto
el tema de la webcam no estoy seguro como ayudarte
el regnum lo probaste con la ultima version de wine qu salio hace 2 dias?
y contanos si las otras ayudas que te pusieron te sirvieron

---

### Post by User21 on 2008-03-27
Se que puede que no venga al caso, pero el cliente Linux de Regnum funciona **perfecto**, en mi Nvidia MX4000 de 64MB. Creería que bastase con tener aceleración gráfica en tu tarjeta, ya que cuenta con un MODO SEGURO DE VIDEO, el cual probé, pero no aseguro nada. Lo hice funcionar con las instrucciones que vi [**aquí**]("http://www.ubuntugames.org/regnum"). 
En un principio el Regnum demora en descargar la data (yo bajaba los datos del programa a 100 kb/s promedio), pero una vez bajado cierto trecho, el juego corre de lujo y sigue descargando data en "2do plano" :D 
De todas formas, en mi caso, no uso compiz. 

No, **no juego Regnum**. Solo quería probar que tal andaba la versión Linux.

---

### Post by InsektO on 2008-03-27
> **MaReaDo^ said:**
> que placa de sonido tenes? porque hay mucha gente que con placas intel hda tienen dramas con el microfono, es mas, yo tuve y tengo una intel hda
por eso pregunto
el tema de la webcam no estoy seguro como ayudarte
el regnum lo probaste con la ultima version de wine qu salio hace 2 dias?
y contanos si las otras ayudas que te pusieron te sirvieron

No hace falta probarlo con Wine porque el RO tiene un cliente nativo para Linux (que anda mucho mejor que el de Win, y fue en un principio lo que me motivó a pasarme a Ubuntu :o).

Como ya dijeron, el foro de soporte técnico de Linux, si bien no es "oficial", tiene usuarios muy predispuestos a ayudar con cualquier tipo de inconveniente que surja. Si andan por allá me van a ver bastante...

Saludos!

---

### Post by MaReaDo^ on 2008-03-27
ah, no sabia eso del juego

---

### Post by jpmorelli on 2008-03-27
Se que no viene al caso ( version 2 ), pero ya que estamos alguno que abra otro thread y muestre un par de screens que me gustaría verlo.
Ya que estamos aprovecho para sentir de nuevo mi alegría al saber que mi juego preferido NWN ( Neverwinter nigtmares ) tiene cliente nativo para linux y me funciona perfectoooo.
Gracias y perdón por la molestia.

---

### Post by User21 on 2008-03-27
Aca te dejo un unico screen que hice, porque estaba re a full webeando. xD
Ademas, soy nivel 1 y doy vergüenza de siquiera mostrarme sin armadura!

---

### Post by leo_rockway on 2008-03-27
Acá hay otro screenshot.

EDIT: vale aclarar que Regnum Online es freeware, (es decir, gratis, no libre).

---

### Post by jpmorelli on 2008-03-27
Geniales !!! Gratis ??? eso si que no lo sabía !!! Ya me pongo a mirar que onda, solo para satisfacción propia :) no me quiero enganchar...
En cualquier momento abro un thread con imágenes de NWN :guitar:

Ya que estamos y para ayudar con el verdadero post, yo tengo la misma placa Intel D965, pero le puse una PCIe Nvidia 7300GS ( si, ya se que la GT le pasa el trapo, pero no dió para más ), pero según tengo entendido para las Intel hay que cargar alguno de estos paquetes:

915resolution
xserver-xorg-video-i810
xserver-xorg-video-intel 

Suerte !

---

### Post by leo_rockway on 2008-03-27
> **jmorelli said:**
> Geniales !!! Gratis ???

Dije "pero no libre!" (este post fue esponsoreado por la free software foundation, muchas gracias por su atencion)

---

### Post by Etrigan on 2008-05-13
Buena gente, reinstale mi vostro 1400 (con el intel 965) . ubuntu 8.04. 
Compiz ya funciona correctamente , (no hace falta quitar la placa de la blacklist - salvo el efecto agua, pero bueno..), la web cam anda joya! lo unico que no pude hacer funcionar es el microfono, lei bastante y lo unico que encontre factible es actualizr el bios, pero aun no se bien como. 

El Regnum ONline no funciona, solo probe la version para linux. 
me dice que debo instalar los Direct x jejejejej ... no creo que eso sea factible!

---

### Post by fencer on 2008-09-28
la solucion es instalar el driconf desde el gestor synapticc, activan la compresión de texturas S3TC, desde la segunda pestaña..

---

