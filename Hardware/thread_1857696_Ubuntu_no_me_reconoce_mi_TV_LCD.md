---
title: "Ubuntu no me reconoce mi TV LCD"
date: 2011-10-10
forum: Hardware
---

### Post by drazhe on 2011-10-10
Hola comunidad! tengo un inconveniente técnico, el otro día quice conectar mi notebook a un TV LCD de 42" para ver una película, conecto todo correctamente, inicio todo como corresponde, en la TV LCD se ve la carga del sistema y el logo de Ubuntu cuando carga, pero a la hora de mostrarme el escritorio, se queda congelado todo negro y no se puede ver nada... 

ya probé con detectar los monitores desde el **nvidia X server setting** y desde las **preferencias de monitores** y nada... 

alguna sugerencia? se que se puede hacer esto porque ya lo hice con un ubuntu 9.04 y no tuve problemas, pero con la ultima versión de Natty Narwhal, no puedo ver nada desde el 2do monitor...

---

### Post by papibe on 2011-10-10
¿Qué conexión estás usando? ¿HDMI? ¿DVI? ¿VGA?
¿Estás seguro que el driver de NVidia está en uso? si no, puedes publicar tu /etc/X11/xorg.conf?

Saludos.

---

### Post by Sonicrulz12 on 2011-10-10
oo tambien antes de que te conectes ya tener la computadora prendida y luego ya escoge el monitor

---

### Post by Sonicrulz12 on 2011-10-10
si te ayudo?

---

### Post by guillermolisi on 2011-10-10
Como esta configurado el dual head monitor para la placa de video ?

Si esta como continuacion de un mismo y unico escritorio vas a tener problemas con la resolucion.

Tenes que configurarlo para que te muestre el mismo escritorio en los dos monitores, modificando la resolucion del que posee la maquina al adaptarse a la del TV.

Si no resulta, proba desconectando logicamente el monitor de la PC dejando solamente activa la salida a la TV.

Tambien es importante poder responder a la pregunta de Papibe.

---

### Post by Sonicrulz12 on 2011-10-10
perdon esque mi espanol no es el mejor

---

### Post by drazhe on 2011-10-14
conseguí que mi **nvidia x server setting** reconociera el 2do monitor (osea la TV LCD) haciendo lo que me dijeron... el tema es que no encuentro la combinación de teclas que lo activa... no es que sea idiota, pero es un PC de escritorio y no tiene la tecla FN como las portátiles... alguna idea? tampoco encuentro el detalle en el apartado SISTEMA>PREFERENCIAS>COMBINACIÓN DE TECLAS

---

### Post by papibe on 2011-10-14
Nunca he escuchado ni leído que eso funcione en un desktop con Ubuntu (combinación teclas para cambiar monitor). Que yo sepa, cuando conectas un monitor, tienes que configurarlo con el 'Nvidia X Server Settings'.

Ahora, si vas a tener la TV conectada siempre, puedes grabar (o salvar) los settings permanentemente. Para esto ejecuta:
```
$ gksudo nvidia-settings
```
Eso llama el 'Nvidia X..' como super usuario. Configura tus monitores de modo que queden como te guste. Luego del lado izquierdo seleccionas 'X Server Display Configuration', y del lado derecho 'Save to X Configuration File'. La próxima vez que inicies to máquina va a reconocer los 2 monitores.

Ojo que si vas a conectar la TV de vez en cuando, lo anterior no es recomendable.

¿Te ayuda o te sirve esto?
Saludos.

---

### Post by drazhe on 2011-10-14
> **papibe said:**
> Nunca he escuchado ni leído que eso funcione en un desktop con Ubuntu

de poder se puede, en Window$ no tengo drama, pero con Ubuntu no consigo hacerlo funcionar... el **nvidia X server setting** me reconoce los 2 monitores, pero no se como pasar la imagen al 2do.. en un portátil por lo general es la tecla FN+4 o FN+f4, pero el teclado de mi desktop no tiene la tecla FN, y en combinaciones de teclas no encuentro la orden referente a dicha acción para especificar una combinación de teclas propia...

---

### Post by papibe on 2011-10-14
¿Has conseguido alguna imagen en la TV?

Prueba esto: Abre 'Nvidia X..', selecciona 'X Server Display Configuration', del lado derecho selecciona el recuadro que identifica a tu TV (va a quedar con un marco rojo). Presiona más abajo el botón 'Configure', selecciona Twin View o Twin View (Clone).

¿Estamos más cerca?
Saludos.

---

### Post by drazhe on 2011-10-15
> **papibe said:**
> ¿Has conseguido alguna imagen en la TV?

Prueba esto: Abre 'Nvidia X..', selecciona 'X Server Display Configuration', del lado derecho selecciona el recuadro que identifica a tu TV (va a quedar con un marco rojo). Presiona más abajo el botón 'Configure', selecciona Twin View o Twin View (Clone).

¿Estamos más cerca?
Saludos.

y por ahora si, no va a quedar otra que usarlo así.... gracias de cualquier manera!

---

