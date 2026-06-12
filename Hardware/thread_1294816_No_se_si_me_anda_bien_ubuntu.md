---
title: "No se si me anda bien ubuntu"
date: 2009-10-18
forum: Hardware
---

### Post by alxgom on 2009-10-18
la cosa es asi, cuando pongo la opcion para probar ubuntu sin instalar, despues de que carga la barra dejo de ver la pantalla. Si prendo y apago el monitor puedo verla por 1 seg.
Probe con el modo de prueba grafico seguro(o algo asi) y me cargo todo, pero corre muy lento y se traba.

como puedo hacer para saber si es un problema de herdware o otra cosa?, como lo soluciono?.
si lo instalo voy a seguir con ese problema?

gracias

---

### Post by Applelnx on 2009-10-18
No se muy bien que puede pasar, pero te aconsejo que pongas el modelo de computadora que estas usando asi alguien te puede llegar a ayudar. Saludos

---

### Post by alxgom on 2009-10-18
el monitor es un Samsung syncmaster 550v

la maquina tiene  intel celeron 2.13ghz con 192 ram

la placa de video es integrada

---

### Post by oktubrer on 2009-10-18
Por lo que decis de prender y apagar el monitor puede ser un problema de la tasa de refresco.  Podrías probar iniciarlo en una resolución menor a ver que pasa, fijate que en el primer menú cuando bootea el CD una de las teclas de función que aparece abajo es para la resolución de pantalla.

---

### Post by alxgom on 2009-10-18
aca?
[http://a.imagehost.org/0761/02_8.png](http://a.imagehost.org/0761/02_8.png)

---

### Post by alxgom on 2009-10-18
_no lo encuentro_[]("http://a.imagehost.org/0761/02_8.png")

---

### Post by oktubrer on 2009-10-18
> **alxgom said:**
> aca?
[http://a.imagehost.org/0761/02_8.png](http://a.imagehost.org/0761/02_8.png)

Si, F4, "Modos"
¿Que opciones aparecen?

---

### Post by alxgom on 2009-10-18
aparece:-Normal
              -grafico seguro
              -usar disco de actualizacion de contrloadores
              - instalacion OEM


hace un rato probe en grafico seguro y llego a ver todo, pero tarda 20 min en cargar y anda lentisimo.
tamb. aparecion un cartel : "el panel ha encontrado un problema mientras cargaba                  -- OAFIID:Gnome_Panel_TrashApplet--

y me pregunta si deseo borrarla

---

### Post by guisheca on 2009-10-18
Con esa ram no te da para arrancar el live-cd de ubuntu, no me acuerdo ahora mismo cuanto era que se necesitaba mínimo para arrancarlo, pero si no te falta por ahí nomas anda. Aparte de que no te debe reconocer bien la placa de video por eso en modo normal no se ve bien, y en modo gráfico seguro se ve lento, por falta de ram.

Fijate, descargate el xubuntu o mejor todavía el lubuntu (que está en beta, pero en pocos días ya sale el definitivo).

Yo creo que ese es el problema.

---

### Post by guillermolisi on 2009-10-19
> **guisheca said:**
> Con esa ram no te da para arrancar el live-cd de ubuntu, no me acuerdo ahora mismo cuanto era que se necesitaba mínimo para arrancarlo, pero si no te falta por ahí nomas anda. Aparte de que no te debe reconocer bien la placa de video por eso en modo normal no se ve bien, y en modo gráfico seguro se ve lento, por falta de ram.

Fijate, descargate el xubuntu o mejor todavía el lubuntu (que está en beta, pero en pocos días ya sale el definitivo).

Yo creo que ese es el problema.
Para instalar desde un LiveCD el minimo de RAM necesario es de 384Mb.

Con valores por debajo de esa cantidad de memoria lo recomendable es usar una version Alternate para instalar.

Hubo casos con 192 y 256 Mb RAM que han instalado pero el proceso duro practicamente una noche y, segun comentarios, parecia que la maquina se habia colgado. Estos casos que recuerdo son de la epoca de las versiones 7.xx

---

### Post by Tosh78 on 2009-10-19
Si, es verdad lo que dice Guillermo. Con esa ram Ubuntu no te va a funcionar. Podes probar con Xubuntu, que si no mal recuerdo necesita 192 mb de ram. Otra opcion es Lubuntu.

---

### Post by guidito73 on 2009-10-20
Podés instalar con 256 de RAM (O un poco menos, como vos) siempre y cuando tengas una Swap hecha. Podés hacerlo con GParted y te lo toma solo el proceso de instalación.

Igual, te conviene cortar por lo sano y mandarte con Xubuntu o Lubuntu. Consejo de chatarrero.

---

