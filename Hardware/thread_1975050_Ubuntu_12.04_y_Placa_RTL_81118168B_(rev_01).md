---
title: "Ubuntu 12.04 y Placa RTL 8111/8168B (rev 01)"
date: 2012-05-06
forum: Hardware
---

### Post by javierlinux1 on 2012-05-06
Buenas noches, tengo la placa de red del asunto, estaba funcionando correctamente con Ubuntu 10.04 y al actualizar a 12.04 dejó de funcionar.
Network Manager dice:"Red cableada el dispositivo no está gestionado" y estuve buscando y vi que a otros les ha pasado lo mismo, pero todavia no aaparece ninguna solución, o las que hay no funcionan.

En alguna parte recomiendan bajar un driver oficial, llegué a el pero es para kernel 2.6.x y 2.4.x y no para el 3 así que no lo usé.

Si alguien me puede dar alguna pista agradecido

Javier

---

### Post by hictio on 2012-05-10
Realmente es rarísimo... Las placas Realtek tradicionalmente funcionarion siempre en Linux sin ningún problema.

---

### Post by javierlinux1 on 2012-05-10
Si, es cierto lo que decís, funcionan siempre, pero en este caso, no s eporqué no lo hace.

Fue automatico, estaba usando 10.04, actualicé, reinicio la máquina y no tenía red.

Tenía un debian en la misma máquina, asique estoy buscando la solucion con eso hasta que pueda volver a usar Ubuntu.

Gracias

---

### Post by guillermolisi on 2012-05-10
Si NM dice que la placa de red no esta gestionada se refiere a que el no la configura. Generalmente esto sucede cuando la interface de red se configura directamente en /etc/network/interfaces.

Fijate si hay algo referido a esa interface ahi. No seria la primera vez que uno se olvida que la configuro "a mano" y espera que el NM lo haga.

---

### Post by javierlinux1 on 2012-05-10
Hola Guille, si es asi como vos decis, está configurada a mano, siempre lo estuvo y siempre funcionó, pero ahora no.

¿que hago? ¿Desinstalo Network Manager? lo tengo pensado, y pondria wicd, pero me parece raro que en todas las demas versiones de ubuntu (esta pc viene desde 7.04) funcionó y ahora lo tenga que cambiar.

Gracias por responder

Javier A. Arfuch

---

### Post by guillermolisi on 2012-05-10
Si vas a una consola, sin abrir sesion grafica, tampoco funciona ?
Que te da "ifconfig -a" ?
Podrias mostrar el archivo de configuracion ?

---

### Post by javierlinux1 on 2012-07-01
Les comento para cerrar el hilo que por otras cuestiones tuve que reinstalar el Sistema y despues de eso, al hacer una instalación nueva, salio andando de entrada, sin tocar nada y manteniendo la configuracion manual del /etc/interfaces.

Gracias a todos los que respondieron y perdon por tardar tanto en volver a responder, pero como se solucionó, me olvidé de venir de nuevo por acá y cerrarlo.

---

