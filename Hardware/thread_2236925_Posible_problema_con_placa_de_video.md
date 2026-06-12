---
title: "Posible problema con placa de video"
date: 2014-07-29
forum: Hardware
---

### Post by nikoaton on 2014-07-29
Personas!. El problema es el siguiente: Mi pc es  una laptop lenovo Y560D y tiene una ati mobility radeon 5730 integrada y  hace poco enchufe un mouse "gamer" y me tiro pantallazo azul, reinicie y después de logo de windows quedo en pantalla negra, hice las mil y una, se podrán imaginar. Entonces decidí formatear la pc todo desde cero e  instalar los drivers todo de nuevo, el problema seguía. entonces decidí  instalar Ubuntu (versión 14.04, la ultima) y resulta que en la parte de controladores veo que si se esta usando la laca de vídeo (dice: "usando  pservidor X de X.org - envoltura de los controladores gráficos de  amd/ati desde xserver-xorg-video-ati (código abierto, probado)" como soy  nuevo en esto, la verdad no se si esta usando la VGA o la ATI. quisiera  saber si pueden ayudarme con esto y sino no hay problemas.
Mas que nada quiero saber porque no puedo iniciar windows en modo normal con la placa de video habilitada ya que veo si funciona con Ubuntu Abrazo a todos. 
Soy nuevo en Linux :D

---

### Post by dave131 on 2014-07-29
? "I suggest you visit the Spanish forums at [this address]("http://www.ubuntu-es.org/?q=forum"). / Te recomiendo que visites los foros en español que podrás encontrar en [esta dirección]("http://www.ubuntu-es.org/?q=forum")."

---

### Post by arieleoar on 2014-07-29
Hola, si la esta usando, sino te saldria una notificacion pidiendo que elijas un controlador privativo para tu tarjeta de video, igual revisa entre los controladores privativos y elige el recomendado, muchas personas tienen problemas con el controlador "x.org-xserver". En mi caso que tengo una nvidia (y en las nvidia en general) no se recomienda usar el controlador Xorg (en experiencia propia las ventanas se comportaban de forma extraña).
Te recomiendo tambien que vayas a la consola y ejecutes antes que nada:
```
sudo apt-get update
```
de ahi te notificara automaticamente si tienes que actualizar algo del sistema y te sumara opciones a la lista de controladores.
Espero que te sirva amigo.

---

### Post by nikoaton on 2014-07-31
Bueno hice todo lo que me dijiste y resulta que me figura "recomendado" el controlador que mencione anteriormente. Probe los otros pero no inicia el sistema operativo, se queda en pantalla negra., probe las 2 opciones que aparecen como "privativos", asi que me quedo con el tengo (x.org-xserver). Muchas gracias por contestar. Abrazo grande!

---

