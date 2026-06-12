---
title: "Touchpad HP DV6-3132TX"
date: 2011-06-02
forum: Hardware
---

### Post by Tosh78 on 2011-06-02
Hola a todos.
Antes que nada perdon por postear pero sinceramente no la tengo clara con el hardware y no soy un usuario avanzado en linux. 
Les cuento que instale Ubuntu 11.04 en mi HP DV6 pero para sorpresa mia, el touchpad funciona medio raro. O sea, el puntero funciona, pero el boton derecho no funciona a no ser que use 2 dedos, el boton izquierdo hace algunas cosas pero no todas (no puedo, por ejemplo, agarrar una ventana y moverla) y cada tanto salta el puntero cuando estoy tocando los botones.

Probe con Chakra, la ultima version, que tiene el kernel 2.6.38.4 y me funciona a la perfeccion. Alguien puede darme una mano? Lo agradeceria muchisimo.

Saludos!

---

### Post by asterix77 on 2011-06-03
Haz intentado cambiar la configuración desde Sistema ----->Preferencias ---->Ratón


Aquí puedes configurar tanto un mouse como un touchpad, y puedes probar los cambios.


Saludos

---

### Post by guillermolisi on 2011-06-04
> **Tosh78 said:**
> Hola a todos.
Antes que nada perdon por postear pero sinceramente no la tengo clara con el hardware y no soy un usuario avanzado en linux. 
Les cuento que instale Ubuntu 11.04 en mi HP DV6 pero para sorpresa mia, el touchpad funciona medio raro. O sea, el puntero funciona, pero el boton derecho no funciona a no ser que use 2 dedos, el boton izquierdo hace algunas cosas pero no todas (no puedo, por ejemplo, agarrar una ventana y moverla) y cada tanto salta el puntero cuando estoy tocando los botones.

Probe con Chakra, la ultima version, que tiene el kernel 2.6.38.4 y me funciona a la perfeccion. Alguien puede darme una mano? Lo agradeceria muchisimo.

Saludos!
Chakra viene con KDE y este posee una utilidad grafica para configurar el touchpad (en System Settings - Input Devices).

---

### Post by Tosh78 on 2011-06-07
> **asterix77 said:**
> Haz intentado cambiar la configuración desde Sistema ----->Preferencias ---->Ratón


Aquí puedes configurar tanto un mouse como un touchpad, y puedes probar los cambios.


Saludos

Si, probe con eso, pero no pude hacerlo andar. Sigue igual.

---

### Post by Tosh78 on 2011-06-07
> **guillermolisi said:**
> Chakra viene con KDE y este posee una utilidad grafica para configurar el touchpad (en System Settings - Input Devices).

Ah! No sabia eso. Voy a ver que encuentro. De todas formas, me interesa mas hacerlo andar en Ubuntu, si es posible.

---

### Post by Tosh78 on 2011-06-20
Bueno, al final pude encontrar la solucion a este problema. La posteo por si a alguien le sirve.

Lo que hice fue ejecutar lo siguiente en una consola:
sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
reboot

Y a partir de ahi, el touchpad empezo a funcionar bien.

Yo la verdad que no tengo mucha idea de que fue lo que eso hizo, pero funciono. Si alguno se copa y explica que es lo que eso hace, mejor, asi entiendo de donde viene el problema.

---

### Post by granjero on 2011-06-20
lo que hiciste allí fue loguearte como super usuario.
luego creaste un archivo "psmouse.modprobe" que tiene como contenido "options psmouse proto=exps" en el directorio /etc/modprobe.d/
y después reiniciaste.

salud!

---

### Post by alehop on 2011-12-06
Tengo el mismo problema, pero he intentado hacer lo de la terminal, el problema es que me dice que tengo permiso denegado al escribir todo el codigo... ayudaaa!

---

### Post by guillermolisi on 2011-12-06
> **alehop said:**
> Tengo el mismo problema, pero he intentado hacer lo de la terminal, el problema es que me dice que tengo permiso denegado al escribir todo el codigo... ayudaaa!

Te pide que ingreses una clave, por el sudo, y esa clave tiene que ser la misma que posee la cuenta de usuario que estas utilizando.

---

