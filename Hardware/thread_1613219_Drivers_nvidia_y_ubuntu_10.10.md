---
title: "Drivers nvidia y ubuntu 10.10"
date: 2010-11-04
forum: Hardware
---

### Post by sitodonosti on 2010-11-04
Hola, 

soy usuario de ubuntu desde hace 4 años y nunca me había pasado esto. Os comento, tengo un portatil ahtec con una tarjeta grafica nvidia 8600 GT, y cuando le doy a probar ubuntu sin instalar me sale una resolucion baja, muy baja, pensé que instalando los drivers de la tarjeta grafica valdría pero al instalalos y reiniciar el ordenador queda la pantalla de login pero en forma de terminal. si entro a través de terminal con mi usuario y password y pongo startX no me deja.

He visto que a gente tambien le ha fallado esto pero que han cambiado de driver privativo de las dos opciones que te da ubuntu(probado y no funciona).

No se qué mas hacer...
Alguna ayudita please??
gracias y un saludo!

---

### Post by atari130xe on 2010-11-04
> **sitodonosti said:**
> Hola, 

soy usuario de ubuntu desde hace 4 años y nunca me había pasado esto. Os comento, tengo un portatil ahtec con una tarjeta grafica nvidia 8600 GT, y cuando le doy a probar ubuntu sin instalar me sale una resolucion baja, muy baja, pensé que instalando los drivers de la tarjeta grafica valdría pero al instalalos y reiniciar el ordenador queda la pantalla de login pero en forma de terminal. si entro a través de terminal con mi usuario y password y pongo startX no me deja.

He visto que a gente tambien le ha fallado esto pero que han cambiado de driver privativo de las dos opciones que te da ubuntu(probado y no funciona).

No se qué mas hacer...
Alguna ayudita please??
gracias y un saludo!

Los drivers Nvidia al menos los 260.19.06 y los 260.19.12 no funcionan correctamente en Ubuntu Maverick 10.10, yo tengo una Gráfica Geforce 8400GS de 256MB PCIe y no hay caso tuve que volver a Ubuntu 10.04.1 porque no quería quedarme sin aceleración Gráfica, pasate por el bug que abrí en Launchpad que es el siguiente:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596)

Si nó estás registrado en Launchpad hacélo (hazlo me parece que sos de españa jejeje) asi te sumás como afectado por ese problema. "arriba a la izquierda de la pantalla en el bug hay una opción que dice: 

[COLOR="Red"]This bug affects you and 21 other people[/COLOR]

No sé que van a hacer pero sé que no es un problema únicamente mío y es una pena que lo que funcionaba perfecto hasta la versión 10.04.1 no funcione en Maverick.

Mientras tanto podés instalarle la versión sugerida (no recomendada) 173. que aparece  para instalar en el mismo menú de los controladores de hardware en Maverick) para tener aceleración 3D pero el rendimiento es horrible y bueno... a esperar se ha dicho :)

---

### Post by sitodonosti on 2010-11-04
> **atari130xe said:**
> Los drivers Nvidia al menos los 260.19.06 y los 260.19.12 no funcionan correctamente en Ubuntu Maverick 10.10, yo tengo una Gráfica Geforce 8400GS de 256MB PCIe y no hay caso tuve que volver a Ubuntu 10.04.1 porque no quería quedarme sin aceleración Gráfica, pasate por el bug que abrí en Launchpad que es el siguiente:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596)

Si nó estás registrado en Launchpad hacélo (hazlo me parece que sos de españa jejeje) asi te sumás como afectado por ese problema. "arriba a la izquierda de la pantalla en el bug hay una opción que dice: 

[COLOR="Red"]This bug affects you and 21 other people[/COLOR]

No sé que van a hacer pero sé que no es un problema únicamente mío y es una pena que lo que funcionaba perfecto hasta la versión 10.04.1 no funcione en Maverick.

Mientras tanto podés instalarle la versión sugerida (no recomendada) 173. que aparece  para instalar en el mismo menú de los controladores de hardware en Maverick) para tener aceleración 3D pero el rendimiento es horrible y bueno... a esperar se ha dicho :)
ok gracias, si soy de españa ejej pero te entiendo perfectamente mi entrenador de baloncesto es aregentino estoy acostumbrado jajajja
ya me pase por tu hilo y he visto que no hay solución haré lo que me dices y que lo sepan, mientras me volveré a la anterior porque la 173 me pone un resolución mala...

---

### Post by atari130xe on 2010-11-04
> **sitodonosti said:**
> ok gracias, si soy de españa ejej pero te entiendo perfectamente mi entrenador de baloncesto es aregentino estoy acostumbrado jajajja
ya me pase por tu hilo y he visto que no hay solución haré lo que me dices y que lo sepan, mientras me volveré a la anterior porque la 173 me pone un resolución mala...

Aparentemente desde la incorporación del driver Nouveau para reemplazar al propietario de Nvidia se originan estos conflictos, leyengo en varios foros encontré que hay gente con este mismo problema o similar ya desde la versión 10.04 de Ubuntu, Fedora y otras distros que aplican el driver. El tema supongo pasa porque al instalar el driver propietario entra en conflicto con el driver Nouveau que ya viene "empotrado" en el mismo Kernel (corazón del sistema operativo) entonces no hay manera "fácil y práctica" de que no se cargue al inicio, por eso en muchos casos (el mío sin dudas) por más "blacklist nouveau" que le agregue, etc. sigue cargándose. En fín paciencia :)

Saludos desde Argentina y cualquier cosa estamos en el foro para ayudar en lo que sea posible, la gente de Ubuntu Argentina es de una calidad increíble.

---

### Post by luisrrg on 2010-11-17
Yo tuve el mismo problema con una 8400GS, finalmente instale el driver NVIDIA-Linux-x86_64-173.14.28-pkg2.run y ya todo esta como antes en 10.04: 1280X1024 24bits.

---

### Post by sitodonosti on 2010-11-19
> **luisrrg said:**
> Yo tuve el mismo problema con una 8400GS, finalmente instale el driver NVIDIA-Linux-x86_64-173.14.28-pkg2.run y ya todo esta como antes en 10.04: 1280X1024 24bits.

osea con ubuntu 10.10 y esos drivers?
de donde te los bajaste?
El otro día estuve instalando ubuntu 10.04 y la resolución me falla la verda....

---

### Post by luisrrg on 2010-11-19
el driver 173 lo baje de

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

[http://www.nvidia.com/object/linux-display-amd64-173.14.28-driver.html](http://www.nvidia.com/object/linux-display-amd64-173.14.28-driver.html)

ya tengo aceleración 3D, pero tengo problemas con el pugin flash privativo, las paginas en firefox se atascan.

---

### Post by atari130xe on 2010-11-20
El último driver que funcionó en mi pc es el 195.36.31 (con el cuál funciona la aceleracíon 3D perfectamente y no se "cuelga") antes que instalar el 173.xx que ralentiza mucho la pc.

[http://www.nvidia.com/object/linux-display-ia32-195.36.31-driver.html]("http://www.nvidia.com/object/linux-display-ia32-195.36.31-driver.html")

---

### Post by lorenxz on 2010-11-23
[QUOTE=sitodonosti;10070419]Hola, 

He visto que a gente tambien le ha fallado esto pero que han cambiado de driver privativo de las dos opciones que te da ubuntu(probado y no funciona).

Eso puede ocurrir porque la resolución y/o la frecuencia de renovación (Hz) predeterminada con que inicia el nuevo driver es muy alta para lo que es capaz de desplegar un monitor CRT (85Hz max) o un laptop antiguo. 
Entonces Ubuntu no inicia en modo gráfico sino solo en el terminal.
A mi me ha pasado eso dos veces, ya que solo tengo dos monitores analógicos uno de los cuales tolera máximo 80Hz y debe usar 70Hz derenovación vertical. Me imagino que si la renovación predeterminada al iiciar es de 100Hz se va a error y ocurre eso. 

Hay varios parámetros predeterminados erroneos en esto de los drivers privativos de Nvidia, entre ellos algo relacionado con el modo Panoramix usado en la pantalla continua para dos monitores. Vi un posteo al respecto en oro foro acerca de cómo reparar esos parámetros editando un archivo desde el terminal, pero está en ingles y es medio complicado. 

Cuando tenga tiempo lo voy a intentar hacer y les cuento acá como me fue.

Lorenzo

---

### Post by kabeza on 2010-11-26
Gracias a Dios encontre este hilo hoy
Hace "meses" que vengo sufriendo con 10.10 y mi GForce 8400GS

He probado todo. 173, 195, 260, casi todos los drivers. Ahora que han nombrado un par, los bajare y probare, y ademas ya hay una nueva version del 260 (19.21) que voy a ponerme a probar para ver si puedo solucionar este problema de la resolucion y del "compiz en camara lenta"

Cualquier cosa les aviso ;)

---

### Post by Ganton on 2010-12-01
Para quien le pueda interesar:

A mí me fue de gran ayuda lo que dijeron en 
[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

---

### Post by gaizka87 on 2011-01-17
Hola,

Utilizo Ubuntu desde hace tiempo y al principio tenia problemas con los drivers de la tarjeta de sonido (que con las actualizaciones de distribucion se solucionaron) y tambien con los de la tarjeta de video, que son con los que actualmente tengo una lucha a brazo partido.

El caso es que con la instalacion de Ubuntu 10.04 LTS 32-bit conseguí instalar el driver privativo de Nvidia desde Administracion->Configuracion de hardware. Todo funcionaba a la perfeccion, resolucion, aceleracion gráfica, Nvidia server. A la vista de los buenos resultados obtenidos me decidí a cambiar la distribución a una más reciente, Maverick Meercat pero esta vez de 64-bit.

La historia con esta distribucion es la siguiente: al principio no se veia nada, una pantalla de colores raros. Leyendo en foros descubrí que había una especie de conflicto entre el driver nouveau y el nv, lo solucioné quitando el nouveau y marcando el nv desde synaptic. Ahora al intentar instalarlo desde Administracion->Configuracion de hardware tengo el error de que se me apaga la pantalla a la hora de iniciar el ordenador (creo que es algo de la frecuencia de refresco de la pantalla, un fallo a la hora de crear el archivo /etc/X11/xorg.conf), tras lo cual he utilizado la configuracion de respaldo. También he intentado instalar desde la consola el ultimo driver disponible nvidia-current (creo que es la 265) sin exito.

Alguien tiene alguna experiencia similar? mi tarjeta es la NVIDIA 8600 GT

Mi siguiente paso es probar a instalar los driver bajados de la web de Nvidia

---

### Post by mama21mama on 2011-01-17
yo ando en lubuntu 10.10 de una instalacion limpia via micro-sd con version alternate u mi nvidia GeForce 7050 / nForce 610i anda muy bien con los privativos. uso la v 260.19.06 del driver que lo instale desde el menu del ubuntu el recomendado.

---

### Post by vhs95 on 2011-02-03
Bien importante que verifiques tu fuente de poder...

yo useaba una de 600w y en ubuntu no funciono nunca mis 2 SLI, hasta que empece a desconectar componentes de la corriente electrica y entonces ya me funcionó correctamente, por lo tanto, necesite comprar una fuente mas grande

saludos

---

