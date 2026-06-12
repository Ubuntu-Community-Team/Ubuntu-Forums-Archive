---
title: "Ventilador en Toshiba L305"
date: 2012-08-12
forum: Hardware
---

### Post by aregnando on 2012-08-12
Hola a todos, luego de googlear bastante no pude encontrar respuesta a una pregunta que es: ¿Cómo hago o más bien que archivo tengo que modificar para que el ventilador se encienda a una temperatura diferente de los 80º a los que lo hace ahora? prefiero que funcione todo el tiempo pero que el procesador no llegue a esa temperatura si no más bien que no pase de los 60º, ya modifiqué la frecuencia desde el bios para que no pase de 1 Ghz. y así se mantiene más baja la temp. pero es inevitable que al ver videos esta suba. Como dato mi compu es una Toshiba Satellite L305 en la cual tengo corriendo Ubuntu 12.04. Desde ya muchas gracias.

---

### Post by niko_3100 on 2012-08-13
Hola... reincorporandome a ubuntu hace poquito, era un feliz usuario de windows 7 y hay que admitir que hicieron un excelente trabajo, te puedo decir que eso del fan se deberia controlar por bios. Al menos en mi hp g4 me da la opcion desde la bios de "fan always on", no te aparece??

---

### Post by aregnando on 2012-08-13
Gracias niko_3100, desde el bios ya seleccioné para que la frecuencia del procesador no funcione on demand si no que funciona al mínimo, eso me liberó un poco el tema del recalentamiento que sufría antes, lo que me gustaría es editar el archivo que controla la temperatura a la que enciende el fan para ponerlo que arranque a los 60º en lugar de los 80º ya que muchas veces cuando no la exijo en nada la temperatura no trepa y no tiene sentido que el fan funcione pero no que tenga que llegar a 80º para que encienda.
Igual me voy a fijar en lo que me comentás a ver si veo en el bios alguna opción. Gracias nuevamente.

---

### Post by niko_3100 on 2012-08-13
que procesador tenes? yo tengo un core i3 370m y si bien esta un poquito mas calentito que en windows 7 seran solo 1-2 grados... el que si noto unos 3-5 grados por encima que en windows 7 es mi disco rigido.

Tirame la data de tu procesador cual es.

---

### Post by asterix77 on 2012-08-14
Hace bastante tiempo usé una aplicación en lucid  para eso, pero no recuerdo cual.

Por otra parte no se si te sirva el paquete fancontrol que si no me equivoco, tiene que ir instalado con lm-sensors.

Podrías darle un vistazo

Si recuerdo la aplicación... o la encuentro la posteo.

Saludos

---

### Post by aregnando on 2012-08-14
> **niko_3100 said:**
> que procesador tenes? yo tengo un core i3 370m y si bien esta un poquito mas calentito que en windows 7 seran solo 1-2 grados... el que si noto unos 3-5 grados por encima que en windows 7 es mi disco rigido.

Tirame la data de tu procesador cual es.

Hola niko_3100, mi notebook tiene: : 2x Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
1 Ghz. de Ram e Intel Mobile GM 45 chipset.

---

### Post by aregnando on 2012-08-14
> **asterix77 said:**
> Hace bastante tiempo usé una aplicación en lucid  para eso, pero no recuerdo cual.

Por otra parte no se si te sirva el paquete fancontrol que si no me equivoco, tiene que ir instalado con lm-sensors.

Podrías darle un vistazo

Si recuerdo la aplicación... o la encuentro la posteo.

SaludosHola asterix77 instalé recién fancontrol y ya tenía instalado lm-sensors con lo cual visualizo la temperatura con un applet. No se como se usa fancontrol, ¿hay alguna aplicación desde la cual se pueda controlar las opciones del ventilador? cualquier ayuda será bienvenida. Gracias.

---

### Post by asterix77 on 2012-08-16
En estos momentos estoy en el trabajo y no estoy usando ubuntu, pero quizás esto te pueda ayudar [http://mundobip.com/Control-de-ventiladores-Gu%C3%ADa-de-instalaci%C3%B3n-de-Servidor-con-Linux-Debian-Lenny-al-m%C3%ADnimo-%28Parte-III%3A-Monitorizaci%C3%B3n-de-temperaturas-y-control-de-vetiladores%29_31.htm](http://mundobip.com/Control-de-ventiladores-Gu%C3%ADa-de-instalaci%C3%B3n-de-Servidor-con-Linux-Debian-Lenny-al-m%C3%ADnimo-%28Parte-III%3A-Monitorizaci%C3%B3n-de-temperaturas-y-control-de-vetiladores%29_31.htm)

Por otro lado, ¿has consultado el man del fancontrol?

#man fancontrol

Saludos

---

