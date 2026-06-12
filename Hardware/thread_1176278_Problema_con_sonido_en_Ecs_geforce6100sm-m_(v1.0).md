---
title: "Problema con sonido en Ecs geforce6100sm-m (v1.0)"
date: 2009-06-02
forum: Hardware
---

### Post by benzema on 2009-06-02
Bueno paso a comentarles, instale la ultima version de ubuntu en su version para 32 bits, me reconoce todo, pero cuando quiero usar el Ts (Team Speak, programa para charlas online) tengo que gritar para que se escuche algo, intente subirlo por el icono de sonido que esta en el escritorio pero no solo que igualmente no puedo hablar si no que tambien ahora se escucha un sonido de lluvia todo el rato cuando tengo puestos los auriculares, a tampoco me anda el sonido de los videos de youtube, pero puedo escuchar musica normalmente. ¿alguien tiene este mismo mother?

Gracias, y saludos a la comunidad.

---

### Post by guillermolisi on 2009-06-02
> **benzema said:**
> Bueno paso a comentarles, instale la ultima version de ubuntu en su version para 32 bits, me reconoce todo, pero cuando quiero usar el Ts (Team Speak, programa para charlas online) tengo que gritar para que se escuche algo, intente subirlo por el icono de sonido que esta en el escritorio pero no solo que igualmente no puedo hablar si no que tambien ahora se escucha un sonido de lluvia todo el rato cuando tengo puestos los auriculares, a tampoco me anda el sonido de los videos de youtube, pero puedo escuchar musica normalmente. ¿alguien tiene este mismo mother?

Gracias, y saludos a la comunidad.
Fijate si tenes a la vista todos los controles de audio, particularmente los de entrada de audio/microfono.

A veces el master control no es el que uno cree sino otro (PCM, por ejemplo) y hay controles de ganancia de microfono que podrian disminuir ese ruido blanco que escuchas como lluvia cuando abris el canal.

---

### Post by benzema on 2009-06-02
Tengo todo en alto pero no hay caso, voy a ver si alguien tiene este mother y usa microfono para ver como lo tiene configurado .. Gracias por el aporte igualmente.

---

### Post by Hei Ku on 2009-06-02
Probaste con alsamixer? Suele ser mas completo que lo que ves desde la pantalla de gnome.

Pone alsamixer en una terminal.

---

### Post by benzema on 2009-06-02
> **Hei Ku said:**
> Probaste con alsamixer? Suele ser mas completo que lo que ves desde la pantalla de gnome.

Pone alsamixer en una terminal.


Esaa con alsamixer ahi lo pude poner y aunquesea se me escucha en el team speak, bastante lluvioso pero me escuchan demasiado te debo una master. :p

---

### Post by dirty fingers on 2009-06-03
no tenes en la parte de conmutadores la opción "mic boost 20dB ?

---

### Post by tanoleo on 2009-09-02
Yo tengo otro problema, no tengo audio!!!!!!!!!, en ningun lado, tengo todos los sonidos altos, pero no escucho ni el inicio de la secion en ubuntu, la ultima version.-

---

### Post by guillermolisi on 2009-09-02
> **tanoleo said:**
> Yo tengo otro problema, no tengo audio!!!!!!!!!, en ningun lado, tengo todos los sonidos altos, pero no escucho ni el inicio de la secion en ubuntu, la ultima version.-
Tal como aconsejo Hei Ku, probaste ver los controles con Alsamixer en una terminal/consola ?

---

### Post by josecuervo86 on 2009-09-02
Por ahi tambien es recomendable que corras:

```
gstreamer-properties
```

porque capaz que es un problema de configuración de las salidas

---

