---
title: "Batería de laptop y entorno de escritorio"
date: 2009-06-18
forum: Hardware
---

### Post by sartrejp on 2009-06-18
Escuché por ahí que un SO (Ubuntu) con un entorno de escritorio como Gnome consume más batería que si tiene, por ejemplo, LXDE.
¿Saben si es cierto y si es mucha la diferencia? Lo que decían era que duraba casi el doble, alguien sabe o ha hecho una prueba o comparación al respecto?



P.S.: Dado el tema, batería, duración, entorno elegido, no sabía si ponerlo en hardware, software o comunidad, si creen que debe moverse, lo entiendo.

---

### Post by pablo.s on 2009-06-18
No me parece...
Que pruebas hay?

---

### Post by guillermolisi on 2009-06-18
Si es cierto que un escritorio grafico con colores claros consume mas energia que uno oscuro, independientemente de si es Gnome, KDE o LXDE, con lo cual la autonomia de la bateria cambia.

---

### Post by sdennie on 2009-06-19
Lo que pasa es que tu maquina esta usando casi 0% del micro la gran majoria del tiempo asi que en realidad, no hay ningun diferencia entre Gnome y LXDE por que 0% es 0%.  Soy [fanatico de "power savings"]("http://ubuntuforums.org/showthread.php?t=847773") y antes use Ubuntu con gnome y ahora uso sBOS con LXDE y no hay ningun diferencia.

---

### Post by Mister X on 2009-06-19
Yo he experimentado algo con ese tema y tengo una espina clavada que no me puedo sacar, jaja...
Tengo una laptop Dell Vostro con Centrino Duo (todo intel), y el tema es que bajo las mismas condiciones (brillo del lcd bajo, sin usar el dvd, etc etc) en windows la bateria llega a las 6 hs y en Ubuntu 3,5 hs.
Y te aclaro que en Ubuntu he llegado a matar todos servicios que tengo inclusive quedarme sin el servidor X y trabajando en consola y la situacion es la misma...
Hay un programa que se llama powertop y sirve para medir el consumo y optimizarlo pero no hago gran diferencia, ni hablar de llegar al nivel de consumo de win... igual ya no uso windows asi que me quedo con las 3,5 hs de autonomia:p

---

### Post by guillermolisi on 2009-06-20
> **Mister X said:**
> Yo he experimentado algo con ese tema y tengo una espina clavada que no me puedo sacar, jaja...
Tengo una laptop Dell Vostro con Centrino Duo (todo intel), y el tema es que bajo las mismas condiciones (brillo del lcd bajo, sin usar el dvd, etc etc) en windows la bateria llega a las 6 hs y en Ubuntu 3,5 hs.
Y te aclaro que en Ubuntu he llegado a matar todos servicios que tengo inclusive quedarme sin el servidor X y trabajando en consola y la situacion es la misma...
Hay un programa que se llama powertop y sirve para medir el consumo y optimizarlo pero no hago gran diferencia, ni hablar de llegar al nivel de consumo de win... igual ya no uso windows asi que me quedo con las 3,5 hs de autonomia:p
Que version de Ubuntu usas en esa Dell ?

---

### Post by Mister X on 2009-06-20
todavia estoy con la 8.10

---

### Post by guillermolisi on 2009-06-20
> **Mister X said:**
> todavia estoy con la 8.10
Raro lo que mencionas ya que con Ubuntu 8.10 los comentarios de quienes lo han instalado en notebooks fueron diametralmente opuestos. Mejoraron notoriamente la autonomia de sus maquinas.

No le estara faltando activar algo que tenga que ver con el ahorro de energia, en lugar de sobrarle algun proceso/demonio ?

Las funciones ACPI fueron reconocidas bien o alguna fallo ? (esto lo deberias poder ver en los logs)

---

### Post by Mister X on 2009-06-20
Nunca encontre nada raro con el ACPI, lo que si es claro que el consumo extra de bateria no es por uso de CPU...

Cuando tenga unos dias con tiempo libre voy a actualizar a 9.04 y voy a seguir investigando.

---

