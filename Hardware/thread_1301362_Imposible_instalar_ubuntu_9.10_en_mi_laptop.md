---
title: "Imposible instalar ubuntu 9.10 en mi laptop"
date: 2009-10-26
forum: Hardware
---

### Post by obedlink on 2009-10-26
weno

quiero decirles que no podre disfrutar de ubuntu 9.10 en mi Dell Studio 1535 con graficos Intel GM965 y chipset 965 express

la razon: aparentemente el servidor graficos no arranca, y ni en modo "grafico seguro", inmediamente al seleccionar "instalar ubuntu" o "probar ubuntu sin alterar el equipo" la pantalla de pone en blanco y empiezan a aparecer lineas verticales de colores, el teclado se bloque, porlo que no puedo entrar en consola, la unica solución es reiniciar en seco.

que he hecho para tratar de solucionar el problema
1.- instalar ubuntu 9.10 con el alternate CD
2.- Entrar con el live CD de ubuntu 9.04 y añadir en el xorg.conf, driver "intel" y driver "VESA" y sin ningun resultado

esto esto es lo mas que se me ocurrio hacer, intente entrar en el modo recuperacion, pero ni bien aparece el menu del modo recuperacion, la pantalla se pone blanca y aparece los colores, porlo que llego a un conclusion, de haber una solución debe de ser de forma externa :(

NOTA: este problema viene desde la alpha 2

---

### Post by guillermolisi on 2009-10-26
Fijate si [la solucion que parece haber funcionado en este caso]("http://ubuntuforums.org/showthread.php?t=1130135&highlight=intel+965") tambien resuelve el tuyo.

---

### Post by obedlink on 2009-10-26
nada de eso creo que funciona, las soluciones que utilizen consola estan descartadas, porque el sistema simplemente no arranca, reconfigurar las X tampoco, y añadirle opciones al xorg.conf menos, si poniendo que use los driver VESA que son los mas arcaicos no funcio, no creo que habilitanto DRI, EXA o UXA sirvan.

ahora que me acuerdo, cuando entre con el Live CD de 9.10 el la carpeta /etc/X11/ no aparecia el xorg.cong :S. yo le puese el xorg.conf de la instalacion del ubuntu 9.04

---

### Post by pablo.s on 2009-10-26
Te propongo ir paso a paso
para ver cual puede ser la 
causa del problema.

Pregunta: ¿Cuando instalás
desde la versión Alternate,
digamos la Beta, te sigue
haciendo ese problema?

¿Desde el LiveCD no te deja
hacer la instalación?

¿Cuál versión tenías antes
que SI te funcionaban los
drivers de Intel?

---

### Post by guillermolisi on 2009-10-26
Seria muy interesante iniciar la maquina con 9.04 y en una consola/terminal lograr la salida de "lspci" y "sudo lshw" asi tenemos el panorama completo de los componentes de hardware mas importantes al momento.

Particularmente me llama mucho la atencion que Ubuntu no funcione en una Dell.

---

### Post by obedlink on 2009-10-26
> **pablo.s said:**
> Te propongo ir paso a paso
para ver cual puede ser la 
causa del problema.

Pregunta: ¿Cuando instalás
desde la versión Alternate,
digamos la Beta, te sigue
haciendo ese problema?

¿Desde el LiveCD no te deja
hacer la instalación?

¿Cuál versión tenías antes
que SI te funcionaban los
drivers de Intel?

Respuestas
1.- el problema me lo da desde la alpha 2 hasta la RC, y probablemente se mantenga en la final.

2.-el live CD de karmic tampoco arranca, aparace ya la mensionada pantalla blanca con colores verticales.

3.- con (K)Ubuntu 9.04 ningun problema

Aclaraciones: es estraño pero la unica distro que me funciona es la ubuntu 9.04, he probado mandriva 2009, fedora 11, opensuse 11.1 y todas esas tienen el mismo problema la dichosa pantalla blanca.

---

### Post by obedlink on 2009-10-31
weno acabo de instalar ubuntu 9.10 final con el alternate CD y como siempre no arranca los graficos despues de instalar.

usando el liveCD de 9.04 entre la particion del 9.10 y en /etc/X11 no aparece ningun xorg.conf.

sabiendo que tengo una grafica Intel GM965: empiezen a pasarme xorg.conf para provar.

---

### Post by moreback on 2009-11-01
Interesante sería que pasaras el **/var/log/Xorg.0.log**, ese archivo tiene los logs del servidor gráfico donde debieran aparecer los errores que te da al partir.

El mío en Jaunty era básicamente este

```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"        "EXA"
    Option        "MigrationHeuristic"    "greedy"
    Option        "EXAOptimizeMigration"    "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Lo había modificado para usar EXA, pero no sé si eso funcionará ahora en Karmic.

Mi tarjeta:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    Subsystem: Dell Device **0228**
```

---

### Post by obedlink on 2009-11-01
lo probare luego, en este momento estoy instalando jaunty para luego hacer una actulización via "gestor de actualizaciones"

si de nuevo surge el problema lo probare.

---

### Post by obedlink on 2009-11-01
bueno, he hecho esto

1- instale jaunty desde cero
2.-inmediatamente despues de instalar actualize a karmic via "gestor de actualizaciones"
3- al reinicial veo que dejo el viejo GRUB 1, pero aparecen las entradas para el kernel 2.26.31-14 y el kernel 2.26.28-11 cada uno con su respectivo "recovery mode", ¿cual es la sorpresa?, entrando con el kernel 2.26.31-14 seguimos con el problema de la pantalla blaca, pero con el kernel 2.26.28-11 todo nomal por fin karmic sin ningun problema!!! pero lastimozamente no hay aceleracion 3D, no compiz :(

conclusión: algo está pasando con el kernel 2.26.31-14.

---

### Post by david.ducos on 2009-11-19
Yo tengo el mismo problema. Con el kernel 2.6.28-14 anda pero con el 2.6.31-14 NO!
Misma placa de video, es una Dell 1525.
En mi caso, estoy intentando instalar Kubuntu.
No llega a la parte donde me tendria que logear, se queda la pantalla negra con un aparente cursor. Lo extraño es que la pantalla no es como cuando oprimo alt+ctrl+F1 sino que queda una pantalla como de mayor resolucion, algo parecido a un driver vesa.
Pero por mas que en el xorg le diga que utilice el driver vesa, no funciona. Ni intel ni vesa, nada.
Alguien encontro alguna solucion?

---

