---
title: "Error en Ati drivers y X"
date: 2008-08-19
forum: Hardware
---

### Post by Lokkete on 2008-08-19
Buenas, soy algo nuevo en linux pero me las he arreglado bien con todo pero aqui tengo un problema q no encuentro solucion...:S

No puedo lograr que una aplicación la cargue en otro X. cuando cargo el scrip para crear el X y ejecutar el soft en el otro X, el X queda activo pero no carga el programa o juego que ejecute y en la consola me tira este error

(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -1003.

esto me esta pasando hace unas 2 o tres semanas pues antes me funcionaba perfectamente... cambie los driver porque pense q me estaban funcionando mal pues se me quedaba dura la pantalla pero resutaron ser las memorias, entonces quiero poner los driver que puse anteriormente con el evyNG (los cuales eran los que me funcionaban bien) y de ahi en mas me aparece ese error en consola, si quiero ejecutar un juego con el wine en el x donde tengo el gnome-panel los graficos se ponen todos cuadriculados al cargar el juego y al salir de este el gnome-panel en vez de volver a como estaba queda todo cuadriculado, (je tipo grafico de la CZ spectrum...algooooo para el q la conoce), mientras que si cargo un juego en el mismo x con lunchers de linux funciona exelente...

alguna idea? he utilizado todo how to de ati 9600 que he encontrado en internet y fueron muchos incluso drivers para distintas distribuciones en el peor de los casos al no saber que hacer...

alguna idea ayuda que queiran brindar será binevendida...xD

PD:
aqui el scrip que uso para ejecutar un juego
```

#!/bin/bash
#Warcraft III Launcher

X :3 -ac -br +kb -reset &   # Launches a new X session on display 3
cd ~/Juegos/Warcraft\ III/
sleep 2  # Forces the system to have a break for 2 seconds 
DISPLAY=:3 wine w3l.exe -opengl # Launches W3
#X :3 -ac -terminate

```

Ya que esta aprovecho para otra preguntita...

Cuando me funcionaba el tema este de cargar los soft y/o juegos en un 2do X, en el momento que me cambiaba de X con alt+ctro+F"x" los procesos del 2do X quedaban en stand by o sea congelados freezeados como els guste decir, mientras que en el 1er X siempre seguian...

solo 2 problemitas, nada mal para alguien q no sabia nada de linux..xD

les agradeceria cualquier sugerencia

Tengo el ubuntu 8.04

[COLOR="DarkRed"]En sintesis supongo q es drama de drivers o configuracion de estos, he visto muchos con problemas en internet pero no este q describo por aqui...[/COLOR]

---

### Post by MeduZa on 2008-08-21
nadie ? como puede ser posible? Y_Y

yo ni idea que es pero sigo buscando ayuda sobre el tema

---

### Post by Lokkete on 2008-08-21
ayer estube contento 10' cuando vi q salieron la version nueva de los drivers ati, pero solo me duraron 10' hasta q cuando instale y no quiso saber nada
por lo menos me hizo dar cuenta cual de los 4 paquetes de ati es el q no funciona bien....

---

