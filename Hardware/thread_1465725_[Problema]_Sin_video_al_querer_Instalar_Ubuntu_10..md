---
title: "[Problema] Sin video al querer Instalar Ubuntu 10.04"
date: 2010-04-29
forum: Hardware
---

### Post by majatu on 2010-04-29
Buenas gente, antes que nada disculpen el título poco informativo y que postee esto aca, no sabía si ponerlo en problemas de Software o de Hardware.

Acabo de descargar Ubuntu 10.04 64-bits (revise el cd en busca de errores) y prosedí a Instalarlo clean en mi nueva pc.

El problema va apenas doy enter al menu de instalar, comienza a cargar el live-cd y de repente el monitor se queda sin señal de video (aclaro que no es ningún problema de hardware, el monitor es nuevo y ya habia probado el live-cd de Ubuntu 9.10 sin problema alguno, reconoce hasta el driver privativo ATI y me ofrece instalarlo).

¿Alguna idéa de que pueda estar pasando?

Estoy intentando instalar en una PC con un micro AMD Phenom II X4 695, memoria 4gb, aceleradora ATI Radeon HD 5770, y el monitor Samsung SyncMaster P2370MS.

Un Saludo! Y muchas gracias.

**------------ EDIT ------------**
Instalé Ubuntu desde Alternate CD y al querer iniciar el sistema recien instalado me pasó lo mismo, reinicie pero esta vez usando el cable SUB-D (uso cable DVI) y la cosa cambio, ahora anda. Voy a intentar instalando los drivers de la placa y volver a probar con el cable DVI. Si me funciona edito nuevamente.

Saludos!

---

### Post by anarko on 2010-04-30
Creo que una ves instalados los drivers de ati podes decirle al Xorg que mande la imagen por la salida digital. Tenés que hacerlo en el /etc/X11/xorg.conf , si no existe crearlo con las opciones que google te recomiende.

Recomendación : Linux y ati no se amigan todavía, yo me harte de los quilombos y me pase a nVidia.

---

### Post by majatu on 2010-04-30
> **anarko said:**
> Creo que una ves instalados los drivers de ati podes decirle al Xorg que mande la imagen por la salida digital. Tenés que hacerlo en el /etc/X11/xorg.conf , si no existe crearlo con las opciones que google te recomiende.

Recomendación : Linux y ati no se amigan todavía, yo me harte de los quilombos y me pase a nVidia.

Mas o menos va queriendo la cosa, usando ambos puertos dvi de la aceleradora conecte en el mismo monitor tanto un cable dvi como un sub-d (mediante un adaptador de dvi a sub-d), y cambiando entre uno y otro pude hacerlo andar. Lo que pasa que que no quiero hacer que mi pc tenga técnicamente 2 monitores en uno y perder FPS y demás rendimiento.

Recién desconecte el sub-d y arranque solo con dvi conectado y arranco bien, voy a ver que pasa en unas cuantas reiniciadas.

Investigue en inet por configurar el x.org pero no entiendo bien que es lo que debería de agregarle para decir que funcione el puerto dvi por defecto

¿Alguna idea?

De última me pueden decir como hacer para que el sistema bootee en modo texto hasta llegar a la ventana de selecion de usuario?

Un saludo y muchas gracias!

---

### Post by guillermolisi on 2010-04-30
> **majatu said:**
> 
De última me pueden decir como hacer para que el sistema bootee en modo texto hasta llegar a la ventana de selecion de usuario?

Un saludo y muchas gracias!
Esta pregunta va en un [nuevo thread, en Software]("http://ubuntuforums.org/showthread.php?t=1466466"), ya que no es pertinente al tema original.

---

### Post by israeldelahoz on 2010-04-30
tengo el mismo problema no tengo tarjeta de video externa y uso un monitor vga despues de ver la carga de ubuntu un rato,se va la señal del monitor,y oigo el sonido de inicio,cuando inicio desde el live cd,me atemoriza actualizar desde 9.10 por que no c si me pueda pasar lo mismo

---

### Post by guillermolisi on 2010-04-30
> **israeldelahoz said:**
> tengo el mismo problema no tengo tarjeta de video externa y uso un monitor vga despues de ver la carga de ubuntu un rato,se va la señal del monitor,y oigo el sonido de inicio,cuando inicio desde el live cd,me atemoriza actualizar desde 9.10 por que no c si me pueda pasar lo mismo
Y que tarjeta de video usas ?

Lo mejor para contestar esta pregunta es ingresar en una consola/terminal ```
sudo lshw
```y/o```
lspci
``` y copiar y pegar en un nuevo menaje las salidas de uno de los dos. La seccion de ambos que importa es la que se refiere e VGA/Display.

---

### Post by anarko on 2010-04-30
> **majatu said:**
>  Lo que pasa que que no quiero hacer que mi pc tenga técnicamente 2 monitores en uno y perder FPS y demás rendimiento.


Las placas de video acelaradoras nuevas son asi estan dividas en 2 una para cada salida, no perdes FPS. Si te fijas en Windows en el administrador de dispositivos vas a ver que tenes 2 veces la placa de video.

---

### Post by leonardomdq on 2010-05-01
Tambien me pasa lo mismo con el video ATI, se queda sin señal el monitor LCD, me pasa a cada rato.

Basta de ATI, mil problemas asi que como dijo anarko me compro la nVidia y termino de una ves por todas (eso espero) :lol:

---

### Post by israeldelahoz on 2010-05-01
> **guillermolisi said:**
> Y que tarjeta de video usas ?

Lo mejor para contestar esta pregunta es ingresar en una consola/terminal ```
sudo lshw
```y/o```
lspci
``` y copiar y pegar en un nuevo menaje las salidas de uno de los dos. La seccion de ambos que importa es la que se refiere e VGA/Display.

-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fea80000-feafffff ioport:dc00(size=8) memory:d0000000-dfffffff(prefetchable)

solo me pasa cuando inicio el live cd de 10.04

---

### Post by israeldelahoz on 2010-05-01
-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fea80000-feafffff ioport:dc00(size=8) memory:d0000000-dfffffff(prefetchable)

---

### Post by guillermolisi on 2010-05-01
> **leonardomdq said:**
> ... me compro la nVidia y termino de una ves por todas (eso espero) :lol:
Por un tiempo, si, pero existiendo Murphy disfruta mientras puedas :)

---

### Post by leonardomdq on 2010-05-01
> **guillermolisi said:**
> Por un tiempo, si, pero existiendo Murphy disfruta mientras puedas :)
Murphy? esta me la perdi, no se de que hablas Willys :P

---

### Post by guillermolisi on 2010-05-01
> **leonardomdq said:**
> Murphy? esta me la perdi, no se de que hablas Willys :P
No me digas que nunca escuchaste hablar de la Leyes de Murphy ? :)

[http://www.murphys-laws.com/](http://www.murphys-laws.com/)

[http://es.wikipedia.org/wiki/Ley_de_Murphy](http://es.wikipedia.org/wiki/Ley_de_Murphy)

---

### Post by leonardomdq on 2010-05-01
> **guillermolisi said:**
> No me digas que nunca escuchaste hablar de la Leyes de Murphy ? :)

[http://www.murphys-laws.com/](http://www.murphys-laws.com/)

[http://es.wikipedia.org/wiki/Ley_de_Murphy](http://es.wikipedia.org/wiki/Ley_de_Murphy)
Si claro que la conocia, no habia agarrado que era por la ley de murphy.
Si va a andar bien con nVidia, apuesto todas las fichas,la tenia que haber comprado de entrada la placa pero no pude.
Sabes que con el video onboard que tengo mucho no puedo hacer (ATI 2100)

Saludos :D

---

### Post by Fistandantilus on 2010-05-04
> **leonardomdq said:**
> Tambien me pasa lo mismo con el video ATI, se queda sin señal el monitor LCD, me pasa a cada rato.

Basta de ATI, mil problemas asi que como dijo anarko me compro la nVidia y termino de una ves por todas (eso espero) :lol:

No entiendo por que hablan tan mal de ATI. Hasta el momento tuve 2 maquinas AMD+ATI y ninguna de las 2 me dieron problemas....

[Máquina Viejarda]
Micro: AMD Athlon 64 3200+
Mother: Asus A8V-MX
RAM: 2Gb DDR Génerica
Video: ATI Radeon 9600Pro (Driver Open Source, Accel x Hardware)
HDD: Maxtor 120Gb 7200RPM IDE
Monitor: AOC 19" CRT

[Máquina Actual]
Micro: AMD Phenom II 965 BE
Mother: Asus Crosshair III Formula
RAM: 8Gb DD3 1333Mhz Kingston Hyper-X
Video: ATI HD 5870 (fglrx 10.4, el oficial, no el de los repos)
HDD: WD Caviar Black 32Mb Cache, 7200RPM SATA
Monitor: Samsung P2370 23", lo tengo conectado con el cable DVI sin problemas...

Saludos!.

---

### Post by guillermolisi on 2010-05-05
Señores, por favor no salirse del tema del thread. Para opiniones esta la seccion Comunidad y/o la via personal, siempre dentro de las pautas del Codigo de Conducta.

Gracias.

---

### Post by Fistandantilus on 2010-05-08
> **guillermolisi said:**
> Señores, por favor no salirse del tema del thread. Para opiniones esta la seccion Comunidad y/o la via personal, siempre dentro de las pautas del Codigo de Conducta.

Gracias.

Eso es[COLOR=Black] guillermolisi tenes razón, por favor no posteen opiniones:

> **guillermolisi said:**
> Por un tiempo, si, pero existiendo Murphy disfruta mientras puedas 

> **leonardomdq said:**
> Murphy? esta me la perdi, no se de que hablas Willys 

> **guillermolisi said:**
> No me digas que nunca escuchaste hablar de la Leyes de Murphy ?

[http://www.murphys-laws.com/](http://www.murphys-laws.com/)

[http://es.wikipedia.org/wiki/Ley_de_Murphy](http://es.wikipedia.org/wiki/Ley_de_Murphy)

> **leonardomdq said:**
> Si claro que la conocia, no habia agarrado que era por la ley de murphy.
Si va a andar bien con nVidia, apuesto todas las fichas,la tenia que haber comprado de entrada la placa pero no pude.
Sabes que con el video onboard que tengo mucho no puedo hacer (ATI 2100)

Saludos 

La verdad es que sos hipócrita.

[/COLOR]

---

### Post by guillermolisi on 2010-05-08
> **Fistandantilus said:**
> Eso es[COLOR=Black] guillermolisi tenes razón, por favor no posteen opiniones:

La verdad es que sos hipócrita.

[/COLOR]
Lamento que interpretes mi comentarios como hipocresias, pero solo me referia a que para ningun caso existe una solucion definitiva y perdurable simplemente porque las cosas (como la vida) estan en continuo cambio y lo que hoy parece una "maravilla curativa que salva a la humanidad" mañana es la septima plaga. Se entiende mejor ahora ?

Fue un comentario general y no emiti opinion ni en favor ni en contra de tal o cual fabricante, marca o tecnologia. Lo que es mejor para algunos no necesariamente debe serlo para otros.

Futuros comentarios al respecto por favor via PM. Gracias.

---

### Post by guillermolisi on 2010-05-08
Acabo de ver que con este tema, en el foro general de Instalacion y Actualizacion (en Ingles) que hay mucha gente con problemas similares, tanto con ATI como con Intel, y que algunas soluciones a unos les funciona y a otros no.

Noten que en varios casos la cosa pasa por el Grub 2 ya que (a mi entender) pareceria ser una forma de saltar un bug de esta clase (forzando una configuracion de video en particular a ese nivel)

Mas info [aqui]("http://ubuntuforums.org/showthread.php?t=1463294").

---

### Post by blackz2 on 2010-05-22
hola bueno, he usado ubunto desde versiones pasadas y nunca habia tenido este problema, la cosa es que me descargue la imagen y todo bien, aparece el menu morado, pero al darle clic a live cd, o a instalar Ubuntu, mi monitor queda negro, y no da mas video, lo extraño es que solo pasa con esta version de Ubuntu la 10.04, tengo instalada la 9.10 y va sin problemas, pero quiero probar este nuevo sistema. 

puse el comando para ver mi tarjeta de video y salio esto
-display
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:16 memory:fc000000-fcffffff memory:e0000000-efffffff(prefetchable) memory:fb000000-fbffffff memory:50000000-5001ffff(prefetchable)

es un poco extraño pq dicen que no tiene que ver problemas con las tarjetas Nvidia, espero se encuentre una solucion pronto, gracias.

---

### Post by atapiac on 2010-06-27
Me paso lo mismo que a blackz2, con la versión 9.10 funciono a la perfeccion, pero al tratar de instalar la version 10.04 me ocurre tal cual explica blackz2, si se encuentra alguna solución favor avisar.

Tengo una placa madre Intel D945GCNL.

---

### Post by jlnvillegas on 2011-11-06
queridos amigos:
quiero que mi portátil (lapton) Asus V6J con sistema operativo Ubuntu 11.04 envié una señal de vídeo VGA para un monitor externo  tengo una tarjeta de vídeo nvidia geforce go 7400

 description: VGA compatible controller
                product: G72M [GeForce Go 7400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_li

espero que esta información sea completa par que una buena persona que conozca del tema me pueda colaborar pues la verdad soy muy nuevo en el tema. de antemano agradezco su amable colaboración

---

### Post by guillermolisi on 2011-11-06
El post sobre double head video con Asus esta en [thread nuevo]("http://ubuntuforums.org/showthread.php?t=1876696")

---

### Post by guillermolisi on 2011-11-06
> **jlnvillegas said:**
> queridos amigos:
quiero que mi portátil (lapton) Asus V6J con sistema operativo Ubuntu 11.04 envié una señal de vídeo VGA para un monitor externo  tengo una tarjeta de vídeo nvidia geforce go 7400

 description: VGA compatible controller
                product: G72M [GeForce Go 7400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_li

espero que esta información sea completa par que una buena persona que conozca del tema me pueda colaborar pues la verdad soy muy nuevo en el tema. de antemano agradezco su amable colaboración
Este post esta en [thread nuevo]("http://ubuntuforums.org/showthread.php?t=1876696")

---

