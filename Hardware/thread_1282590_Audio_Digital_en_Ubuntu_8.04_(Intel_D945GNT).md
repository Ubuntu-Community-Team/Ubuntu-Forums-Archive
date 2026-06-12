---
title: "Audio Digital en Ubuntu 8.04 (Intel D945GNT)"
date: 2009-10-04
forum: Hardware
---

### Post by LeandroS on 2009-10-04
Buenas tardes.
Soy un nuevo usuario de Ubuntu, y lo instale, ya que me aburri de windows y sus problemas.
Pero al terminar de instalarlo tengo el siguiente problema.
No puedo hacer andar la salida spdif de mi placa de sonido onboard
Yo tengo un amplificador yamaha con entrada digital, y lo hago andar a traves de eso para sacar dolby digital 5.1.
La placa de sonido onboard es una Intel Azalia Audio Device o la 9223.
Tienen idea como hacerlo funcionar, toque de todo y lolo pude hacer funcionar los 3 parlantes, pero no el subwoofer.
Muchas gracias.

---

### Post by mende1 on 2009-10-04
Instala todas las actualizaciones. Si sigue igual, puedes buscar los controladores para Linux por Internet. Si sigue igual, yo empezaría a pensar que PulseAudio no se lleva muy bien con tu tarjeta de sonido.

Saludos

---

### Post by mende1 on 2009-10-04
O prueba a instalar la versión 9.04 de Ubuntu, a ver si sigue igual.

Saludos

---

### Post by pablo.s on 2009-10-04
Ejecuta en una terminal
el comando

```
alsamixer
```

y fijate si los canales tienen
el volumen alto o se encuentran
silenciados.

---

### Post by LeandroS on 2009-10-06
Gracias a todos por las respuestas.
Finalmente, pude hacer funcionar el audio, el unico problema que tengo es:
Como dije antes, y disculpen que repita los datos, pero para explicarlo mejor, tengo un mobo Intel D945GNT, que viene un una placa de sonido onboard IDT 9220,9223, a la cual, a traves de la salida SPDIF (optico), lo envio a un amplificador yamaha, y a su vez a un 5.1.  El unico problema que resta ahora, es hacer funcionar el subwoofer (por las dudas tengo instalado un XP en otro disco, lo puse, lo levante y el audio funciona perfecto, subwoofer incluido)ya que no emite ningun sonido.  Instale todos los paquetes de alsa, y estuve viendo la configuración de /etc/modprobe.d/alsa.base.conf, pero la verdad es que no tengo idea bien como configurarlo.
En el mixer que viene con ubuntu, tengo activado la opcion IEC958, que si la desactivo, no obtengo nigun sonido.
No se si necesitan que corra algo y les envie la salida.
Muy atentos y muchas gracias.

---

### Post by mama21mama on 2009-10-07
probaste el [nuevo alsa]("http://mamalibre.eshost.com.ar/?q=content/solucionado-alsamixer-con-problemas-en-la-captura#comment-351")?

yo tuve un problema de sonido, seguro or un update matador de esos que saca Ubuntu, y con el nuevo alsa se soluciono.

---

### Post by guillermolisi on 2009-10-07
> **mama21mama said:**
> probaste el [nuevo alsa]("http://mamalibre.eshost.com.ar/?q=content/solucionado-alsamixer-con-problemas-en-la-captura#comment-351")?

yo tuve un problema de sonido, **seguro or un update matador de esos que saca Ubuntu**, y con el nuevo alsa se soluciono.
Por favor, evitar comentarios de esta clase, como el destacado en negrita, si no hay y/o no se aportan elementos para fundamentarlos en forma contundente.

Luego, los paquetes de Alsa, para el caso, que se incluyen en actualizaciones los provee el proyecto Alsa, no Ubuntu y siempre (aunque muchos no lo tengan incorporado) es recomendable leer los changelogs, readme & release notes de las nuevas versiones antes de actualizar.

---

### Post by mama21mama on 2009-10-07
me gustan los comentarios de esta clase.
que problemas tenes con mi comentarios, dije algo fuera del coc o algo que personalmente no te gusto?

digo que el problema es update en mi caso...por que no actualice alsa en un update y me vinieron bug, si no preguntale a juan-arg en el irc que tambien le paso. y algunos sabemos que los updates de ubuntu algunas cosas se mejoran o al contrario.

me paso con karmic alpha que un update me arruino el so.

---

### Post by mama21mama on 2009-10-07
guillermolisi por favor si borras un comentario, aclara a las demás personas, eso es ser comunidad.

---

### Post by guillermolisi on 2009-10-07
> **mama21mama said:**
> guillermolisi por favor si borras un comentario, aclara a las demás personas, eso es ser comunidad.
Este tipo de mensajes deben ir por via privada por que son Off Topic para la tematica del thread al igual que el anterior. No estan borrados, estan moderados, no aprobados y tenes la explicacion en tu perfil, cosa que no mencionas en tu reclamo.

---

### Post by faktorqm on 2009-10-08
Mira esto, si necesitas traduccion avisa [http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut) salu2!

---

