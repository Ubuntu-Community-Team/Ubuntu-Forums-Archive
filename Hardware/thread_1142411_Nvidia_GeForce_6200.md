---
title: "Nvidia GeForce 6200"
date: 2009-04-29
forum: Hardware
---

### Post by prostata on 2009-04-29
Existen drivers para esta tarjeta gráfica...??? he buscado por internet pero no encuentro, o no se encontrarlos...la Jaunty por defecto me recomienda el 180 y ese es el que he aceptado...¿Es esa la mejor solución para mi gráfica.??

Saludos

---

### Post by guillermolisi on 2009-04-29
> **prostata said:**
> Existen drivers para esta tarjeta gráfica...??? he buscado por internet pero no encuentro, o no se encontrarlos...la Jaunty por defecto me recomienda el 180 y ese es el que he aceptado...¿Es esa la mejor solución para mi gráfica.??

Saludos
Ese driver 180 es la ultima version liberada por nVidia pero no deberias tener impedimentos para usar uno mas viejo (si es que experimentas problemas funcionales con ese driver).

El cuidado que hay que tener es que al hacer el downgrade, suponiendo tengas instalado el 180, es que realmente se desinstale y no quede pegado metiendo ruido con el que quieras instalar. Esto es algo que a varios les ha pasado con versiones anteriores a la 9.04 cuando experimentaban problemas con drivers nVidia nuevitos y necesitaban volver a uno mas viejo.

---

### Post by Otaru on 2009-04-29
No sabia que habia problemas con los drivers de Nvidia GeForce 6200.
Justamente hace poco adquiri una placa de esas y ahora estoy pensando en comprarme algun HDD e instalar el Ubuntu alli mismo, como para ir metiendome en Linux.

**Gracias por la informacion guillermo.**
:)

---

### Post by guillermolisi on 2009-04-29
> **Otaru said:**
> No sabia que habia problemas con los drivers de Nvidia GeForce 6200.
Justamente hace poco adquiri una placa de esas y ahora estoy pensando en comprarme algun HDD e instalar el Ubuntu alli mismo, como para ir metiendome en Linux.

**Gracias por la informacion guillermo.**
:)
En realidad hubo problemas cuando salio 8.10 porque se sucedieron varios cambios funcionales entre el SO, X server, los drivers nVidia y el hardware de la PC. Por ejemplo con placas consideradas legacy de nVidia.

En esa epoca hubieron casos en que se queria remover el driver nuevo, que impedia que el server X se iniciara bien, y volver a uno anterior y quedaba cargado interfiriendo en el funcionamiento (uno pensaba que estaba con el mas viejo, con el cual tenia todo funcionando, y no resultaba asi).

Supongo, porque no he leido aun sobre experiencias actuales similares, que ese problema estaria resuelto en 9.04.

---

### Post by biale on 2009-04-30
Hice un arranque "live" de 9.04 con esa placa, instale el driver 180 desde los repositorios y los efectos de escritorio funcionaron bien. glxgears daba algo así como 1100 fps.  Saludos

---

### Post by Otaru on 2009-05-01
> **guillermolisi said:**
> Supongo, porque no he leido aun sobre experiencias actuales similares, que ese problema estaria resuelto en 9.04.
**Hola:**

Espero que no tenga problemas, ya que vi que existe otra nueva version del Ubuntu, y otra ves me tendria que bajar un CD.

Se actualiza muy rapido, y no se si quedarme con mi Ubuntu 8.04 o con lo nuevo 9.04
**Gracias!** :)

---

### Post by faktorqm on 2009-05-01
> **biale said:**
> Hice un arranque "live" de 9.04 con esa placa, instale el driver 180 desde los repositorios y los efectos de escritorio funcionaron bien. glxgears daba algo así como 1100 fps.  Saludos

ojo que glxgears te manda cada 5 segundos los fps.... salu2!

---

### Post by guillermolisi on 2009-05-01
> **Otaru said:**
> **Hola:**

Espero que no tenga problemas, ya que vi que existe otra nueva version del Ubuntu, y otra ves me tendria que bajar un CD.

Se actualiza muy rapido, y no se si quedarme con mi Ubuntu 8.04 o con lo nuevo 9.04
**Gracias!** :)
Y ... depende de cada caso, no hay ninguna receta salvo la regla de oro que dice "Si funciona bien, no lo toques".

Que se lance una nueva version cada seis meses no significa necesariamente que se tenga que hacer el upgrade.

Por ejemplo, en las maquinas que uso Ubuntu (laburo y casa) aun estoy con la 8.04 solamente porque las versiones LTS me parecen apropiadas para laburar y no estar actualizando paquetes todos los dias y lidiar con bugs pendientes de resolucion hasta que llegue el arreglo.

Tambien creo que depende si usas desktop o notebook. Para las ultimas mi recomendacion es 8.10 o superior. Muchisimo mejor que la 8.04 para ese tipo de maquinas desde el punto de vista de la experiencia del usuario.

---

### Post by Otaru on 2009-05-04
[B]Hola:
Gracias por tu comentario.[/B]

> **guillermolisi said:**
> Y ... depende de cada caso, no hay ninguna receta salvo la regla de oro que dice "Si funciona bien, no lo toques".
Si eso es verdad.
Estube mucho tiempo son pasar a Win XP con SP3.
Un dia formatee y alli si instale completo.

> **guillermolisi said:**
> Que se lance una nueva version cada seis meses no significa necesariamente que se tenga que hacer el upgrade.
Tambien creo que depende si usas desktop o notebook.
Crei que cada 6 meses tendria que formatear y bajarme la version nueva :-? por eso mi pregunta.

Uso PC (si pc = desktop)

[B]Gracias por el comentario.
Dudas aclaradas.[/B]
:P

---

### Post by hictio on 2009-05-04
> **guillermolisi said:**
> Y ... depende de cada caso, no hay ninguna receta salvo la regla de oro que dice "Si funciona bien, no lo toques".

Que se lance una nueva version cada seis meses no significa necesariamente que se tenga que hacer el upgrade.

Por ejemplo, en las maquinas que uso Ubuntu (laburo y casa) aun estoy con la 8.04 solamente porque las versiones LTS me parecen apropiadas para laburar y no estar actualizando paquetes todos los dias y lidiar con bugs pendientes de resolucion hasta que llegue el arreglo.

Tambien creo que depende si usas desktop o notebook. Para las ultimas mi recomendacion es 8.10 o superior. Muchisimo mejor que la 8.04 para ese tipo de maquinas desde el punto de vista de la experiencia del usuario.

Yo estoy de acuerdo con eso pero para servidores en producción.

Para laptops, o computadoras hogareñas, no me molesta probar "lo nuevo", fundamentalmente por la propia experiencia de hacerlo.
En mi laptop con Hardy había varias cosas que no funcionaban correctamente (el WiFi, los puertos USB después de hibernar/ suspender la máquina); con Intrepid se arregló todo; y con Jaunty todo sigue funcionando Ok, y además es más rápida la respuesta general.

No me parece gran cosa tener que instalar desde cero (y restablecer backups, etc.) si con eso gano un mejor sistema.

---

