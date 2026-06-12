---
title: "LCD LG se pone en estado de ahorro de energia"
date: 2009-12-19
forum: Hardware
---

### Post by leonardomdq on 2009-12-19
Hola Comunidad, hace un par de dias instale compiz-fusion y nose si tendra algo que ver pero el monitor LCD LG W2043S se pone en modo ahorro de energia  :confused: despues de unos minutos, lo extraño es que en **Sistema -> Preferencias -> Gestor de energia** tengo asi la configuracion:

```

Acciones
- Poner el equipo en reposo si el equipo esta inactivo durante: **Nunca**

Pantalla:
-Poner la pantalla en reposo si esta inactivo durante: **Nunca**

```Y en **Preferencias de Salvapantallas **todo destildado porque no uso.

Nose que puede ser...espero que alguno pueda ayudarme.

---

### Post by guillermolisi on 2009-12-19
Pasa a modo de ahorro de energia o se desconecta para proteger el monitor porque la señal de video intenta trabajar con frecuencias de barrido fuera de rango para ese monitor ?

---

### Post by leonardomdq on 2009-12-19
Gracias por contestar
Nunca me hizo eso, Guillermo hay alguna manera de corregirlo?

---

### Post by leonardomdq on 2009-12-20
alguna idea?

---

### Post by guillermolisi on 2009-12-21
> **leonardomdq said:**
> alguna idea?
A mi se me hace dificil opinar sin saber si el monitor se desconecta, por lo que mencione sobre las frecuencias de barrido, o pasa a ahorro de energia (es decir, es una pregunta que quedo pendiente).

Cuando el monitor se deconecta de la señal de video suele aparecer un cartelito dando aviso de tal situacion (y el led de encendido suele no tener el mismo color o frecuencia de parpadeo que cuando esta en ahorro de energia).

---

### Post by leonardomdq on 2009-12-21
Hace un rato logre saber cual era el conflicto, justo entre a avisar y me encontre con tu respuesta.
Por lo visto el conflicto lo producia algun efecto de compiz-fusion, porque habia instalado el paquete compiz-fusion-plugins-unsupported, configure todo con los efectos que queria y de ahi en mas vino el problema.
Lo que hice fue dejar todas las opciones de compiz-fusion que venian por default y configure algunos efectos, reinicie y no se puso mas en modo ahorro de energia. 

Muchas gracias Guillermo.

SOLVED

---

