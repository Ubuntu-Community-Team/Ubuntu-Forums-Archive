---
title: "Como desactivar la tarjeta de audio interna?"
date: 2010-07-12
forum: Hardware
---

### Post by efis22 on 2010-07-12
Estimados;
Tengo desabilitada la tarjeta de audio desde la BIOS, pero aún así  Ubuntu me la toma, el problema es que tengo mi Tarjeta Externa, y cuando  la enciendo, se desconfigura el audio y es molesto volver hacer toda la  configuración de nuevo, cada vez que prendo el PC.


 Hay alguna forma de Desactivar la tarjeta interna desde Ubuntu?.


 Quedo a la espera de sus respuestas, de antemano muchas gracias.

---

### Post by RafaelG on 2010-07-13
> **efis22 said:**
> Estimados;Hay alguna forma de Desactivar la tarjeta interna desde Ubuntu?.
[SIZE=2]
Estimado, 

Configuraste el **PulseAudio**? si no entonces te recomiendo configures el **Pulseaudio** ya que podras configurar la tarjeta de Audio ya sea interna o externa que sera la default y las secundarias asi como tambien los diferentes niveles de input y output de cada tarjeta y por ultimo los niveles de input y output de cada aplicacion de sonido en tu OS.[/SIZE]

---

### Post by efis22 on 2010-07-13
Gracias Rafael;
La solució fue mas facil de lo que creia, me meti en Pulseaudio, ahí en Hardware, y donde estaba la tarjeta interna de audio, simplemente le puse la opción de "Apagado" y ahora no interfiere más.

Gracias por la ayuda, espero que le sirva a otro usuario que tenga problemas con tarjetas externas.

Saludos.

---

