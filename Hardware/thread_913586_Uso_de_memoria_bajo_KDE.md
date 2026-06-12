---
title: "Uso de memoria bajo KDE"
date: 2008-09-07
forum: Hardware
---

### Post by fgl82 on 2008-09-07
Bueno, luego de lograr que todo quede como yo quería (ver thread "Argumentos a Favor de KDE), noté una diferencia importante entre KDE y Gnome. Por lo menos en mi sistema. 

Cuando usaba gnome, mi memoria utilizada no pasaba de 300 MB, o quizá un poco más.

Bajo KDE, la misma se dispara rápidamente durante mis sesiones hasta casi 1 GB.

Esto no me preocupa especialmente, tengo 2GB, pero mi duda es si esto es normal o algo raro anda pasando con mi sistema.

Noto, eso sí, que las aplicaciones se inician mucho más rápido que en Gnome y todo el sistema en general se siente más ligero. Ah, y tengo instalado preload (aunque bajo Gnome también lo tenía).

Ahora las dudas puntuales serían:

1) ¿Es normal que la memoria utilizada se me vaya a casi 1 GB y no vuelva a bajar de ahí aunque cierre aplicaciones?
2) ¿Esto tiene que ver con KDE? Digo, la administración de memoria es algo propio del SO, y estoy usando ubuntu, como antes, ni siquiera cambié a Kubuntu, pero ¿puede tener KDE algo que ver en esto?
3) ¿Es posible que la memoria extra que noto usada sea utilizada como una especie de cache y por eso las aplicaciones lanzan más rápido?

Gracias a los que respondan :D

¡Saludos!

---

### Post by Hei Ku on 2008-09-07
Es un cache. KDE hace un prefetch para ser mas rapido. Te va a utilizar todo lo que pueda y necesite, mientras no lo necesiten otras aplicaciones.
En mi maquina casi siempre tengo toda la RAM, 1GB, ocupado, aunque tenga pocas aplicaciones andando, pero si abro mas lo libera y no se siente.
En resumen, se adapta a tu sistema, y anda mas rapido si puede.

---

### Post by WanderingKnight on 2008-09-07
En realidad Linux hace un prefetch por si solo. No es cosa ni de GNOME ni de KDE. KSysGuard simplemente te lo muestra y el System Monitor de GNOME no.

Prueben abrir una sesion de TTY sin ambiente gráfico, tiren un top y vean como crece la memoria ocupada.

---

### Post by fgl82 on 2008-09-08
> **Hei Ku said:**
> Es un cache. KDE hace un prefetch para ser mas rapido. Te va a utilizar todo lo que pueda y necesite, mientras no lo necesiten otras aplicaciones.
En mi maquina casi siempre tengo toda la RAM, 1GB, ocupado, aunque tenga pocas aplicaciones andando, pero si abro mas lo libera y no se siente.
En resumen, se adapta a tu sistema, y anda mas rapido si puede.

Gracias por la info, era lo que pensaba.

Con respecto a lo que dice el último comment, ¡mirá vos! O sea que Gnome me miente, jajaja, malo, malo Gnome :P

Igual no sé si Gnome aprovechará igual los recursos, porque, como digo, sentía el sistema más lento bajo Gnome.

---

### Post by niko_3100 on 2008-09-08
A mi gnome me anda de pelos, es mas cuando probe kde lo vi mucho mas lento el sistema y encima vi qu consumia mucha memoria, no me gusto jeje!! pero si queres algo que no consuma nada de nada instalate el xubuntu o fluxbuntu o algo asi. Igual si tenes la memoria para algo que se la banque, para que la pagaste sino jeje!!

---

### Post by fgl82 on 2008-09-08
> **niko_3100 said:**
> A mi gnome me anda de pelos, es mas cuando probe kde lo vi mucho mas lento el sistema y encima vi qu consumia mucha memoria, no me gusto jeje!! pero si queres algo que no consuma nada de nada instalate el xubuntu o fluxbuntu o algo asi. Igual si tenes la memoria para algo que se la banque, para que la pagaste sino jeje!!

No, obvio, si tuviera menos memoria pondría esos que me decís vos.

Pero con 2GB, prefiero usarla, je y, como te digo, me anda todo mejor con KDE, o eso me parece al menos... quizá tenga que ver tb la ausencia de compiz, ni idea

---

### Post by niko_3100 on 2008-09-09
aaaahhhhh hubieras empezado por ahi, obvio compiz alenta todas las ventanas, obvio que no mucho (casi nada) pero cuando comparas te das cuenta que algo alenta.

---

