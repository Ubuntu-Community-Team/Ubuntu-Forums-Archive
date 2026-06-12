---
title: "Activar wifi y web cam en ubuntu 12.04 AIO Exo HR18"
date: 2012-11-20
forum: Hardware
---

### Post by andy_91 on 2012-11-20
Hola, cuanto tiempo no ;) jaja, como andan?, bueno después de mucho tiempo fuera de ubuntu por temas de hardware(estuve usando lenny), decidí aceptar la oferta de telefónica y comprarles un equipo AIO exo HR18, hasta ahora todo el hardware es compatible, pero no logro encender el wifi ni la webcam desde ubuntu.
Para utilizar la webcam en ubuntu debo iniciar desde W7 y activarla con el ControlAP II 1.07 y reiniciar(al apagar el equipo se desactiva), idem wifi, mi duda es como hago para activarlos desde ubuntu.
PD: les dejo un manual que no es de ese equipo, pero es muy parecido en prestaciones(no en modelos/marcas)
[http://www.aminorte.cl/ntbk/wp-content/uploads/2011/09/AIO-1200.pdf](http://www.aminorte.cl/ntbk/wp-content/uploads/2011/09/AIO-1200.pdf)

---

### Post by guillermolisi on 2012-11-23
En una consola/terminal ingresa ```
sudo rfkill list
``` y mostra su salida. En funcion de ella vemos como seguimos.

---

### Post by andy_91 on 2012-11-23
```
andres@andres-AHV:~$ sudo rfkill list
[sudo] password for andres: 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
andres@andres-AHV:~$ sudo rfkill unblock allandres@andres-AHV:~$ sudo rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
andres@andres-AHV:~$ 

```

ahí esta me canse  de hacer sudo rfkill unblock all antes de postear espero encontrar la solución

Pd: te dejo un adicional, por si te sirve:

```
andres@andres-AHV:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operación imposible por estar la radiofrecuencia desactivada

```

---

### Post by biale on 2012-11-23
Bloqueo por hardware. Usualmente existe una tecla que activa el WIFI, pero este no parece ser el caso. El equipo parece depender totalmente de la aplicación "ControlAP II 1.07", ojo si hay que reinstalar W7 o migrar a W8...

Soluciones posibles que se me ocurren:

(1) Hablar con el soporte técnico del producto.
(2) Probar perdido por perdido habilitando el boot desde LAN y rogando que el WIFI también este incluido.
(3) Conseguir un sencillo adaptador USB externo que sea Linux friendly. Hay unos cuantos.

---

### Post by andy_91 on 2012-11-24
> **biale said:**
> Bloqueo por hardware. Usualmente existe una tecla que activa el WIFI, pero este no parece ser el caso. El equipo parece depender totalmente de la aplicación "ControlAP II 1.07", ojo si hay que reinstalar W7 o migrar a W8...

Soluciones posibles que se me ocurren:

(1) Hablar con el soporte técnico del producto.
(2) Probar perdido por perdido habilitando el boot desde LAN y rogando que el WIFI también este incluido.
(3) Conseguir un sencillo adaptador USB externo que sea Linux friendly. Hay unos cuantos.

(1) Te piden Windows
(2) ya intente todo desde la Bios y nada apenas tiene opciones
(3) esos adaptadores para que serian???, no tengo intención de volver a comprar una cámara teniendo una incluida;)

---

### Post by guillermolisi on 2012-11-25
En algunas netbooks Dell se presenta un problema muy parecido. La antena queda fisicamente apagada (hardware block=yes) y tambien se recomienda activarla con Windows y reiniciar, con la antena en ese estado, con Linux.
Tambien hay una solucion que es mucho mas efectiva y que, tal vez, funcione en este caso (siempre que no la hayas probado): Configurar el BIOS con sus valores por defecto.

En las Dell esto vuelve a encender electricamente la antena y queda disponible para otros sistemas operativos.

---

### Post by andy_91 on 2012-11-25
> **guillermolisi said:**
> En algunas netbooks Dell se presenta un problema muy parecido. La antena queda fisicamente apagada (hardware block=yes) y tambien se recomienda activarla con Windows y reiniciar, con la antena en ese estado, con Linux.
Tambien hay una solucion que es mucho mas efectiva y que, tal vez, funcione en este caso (siempre que no la hayas probado): Configurar el BIOS con sus valores por defecto.

En las Dell esto vuelve a encender electricamente la antena y queda disponible para otros sistemas operativos.

no funciona che, que lastima. Seguiré aguantando a W7, muchas gracias de todos modos ;)

---

