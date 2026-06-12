---
title: "Ubuntu 10.4 no se conecta a internet cableada"
date: 2010-05-04
forum: Hardware
---

### Post by diegoese on 2010-05-04
Gente,

Este es mi primer post en este foro así que cualquier error o dato que falte me avisan y lo corrijo.
Como dice el título mi Ubuntu 10.4 no se conecta a internet a través del cable aunque la cuestión es un poco más compleja. Paso a detallar.
Ayer a la mañana instalé de cero un Ubuntu 10.4 en mi PC, una Celeron D de 3.20 GHZ y 320 GB de HD. Hace varios años que uso Ubuntu así que no tuve mayores problemas con la instalación ni con el arranque: Ubuntu booteo perfecto, me reconoció la red enseguida -ninguna otra versión había tenido problemas para conectarse a internet ni siquiera mediante wi-fi- y hasta me reconoció inmediatamente mi HP Laserjet P1505 y la instaló en consecuencia. El problema vino más tarde: cuando particioné el disco desde el LiveCD procuré dejar 100 GB libres para instalar ahí un XP y tener arranque dual. A la noche, me siento a instalar -tal vez acá esté parte del problema- un Windows XP desatendido, más precisamente [este]("http://biodigitzman.blogspot.com/2007/08/biovistamax-77-sp4-series-final-xp.html"). Luego de dos intentos de instalación fallidos, abandoné el XP y por supuesto el MBR me había comido el GRUB. Intenté recuperarlo con el Super Grub Disk pero también me tiró error así que entre al Ubuntu mediante la opción "Arrancar directamente" para ver si podía, desde ahí, recuperar el GRUB.
Acá empezaron los problemas.
Ni bien entro a Ubuntu en modo fallos a través del SGD veo que no tengo internet: las herramientas de red me reconocen la red automática eth0 pero no se logra conectar, amén de que el led correspondiente a PC Activity en mi modem Motorola no se enciende. Finalmente arreglé el GRUB -saqué los datos de internet, conectándome en otra máquina- y reinicié: todo seguía igual. Después de probar varias veces, se me ocurrió reinstalar Ubuntu, formateando todo el disco pero nada cambió. 
Básicamente, Ubuntu me reconoce la red cableada -el cable anda, ya que lo conecté a mi notebook e inmediatamente la luz de PC Activity del Modem se enciende- pero no se conecta ni parece enviarle ningun dato al Modem. 
¿Alguien sabe qué puede ser?
Cualquier dato que necesiten me lo piden
Gracias

---

### Post by totolinux on 2010-05-04
Hola. Intentaste conectarte con algún livecd de la 10.04 o anterior?, digo para descartar problemas de hardware..

---

### Post by diegoese on 2010-05-04
Muchachxs, doy por resuelto el problema... sin conocer exactamente cómo. En relación a la siguiente pregunta:

> **totolinux said:**
> Hola. Intentaste conectarte con algún livecd de la 10.04 o anterior?, digo para descartar problemas de hardware..

Sí, intenté conectarme con el Live del 10.4, el del 9.04 e inclusive con un Kubuntu 9.04 y todo seguia igual.

Sin embargo, hoy, después de postear mi problema en el foro, se me dio por instalar una versión de XP Profesional SP3 en la partición sin asignar que había dejado al instalar el 10.4. Ya sobre el final de la instalación del XP veo que la luz de PC Activity vuelve a prenderse, cuando entro a XP tenía internet. Así que probé, luego de una pasada por el SGD, probar la red en Ubuntu y, milagrosamente, había vuelto. Todavía no entiendo bien qué pasó y no sé cómo se solucionó. Pero acá estoy, con internet otra vez. Supongo que algo habré hecho en el HD cuando instalé fallidamente el BioVista porque fue ahí, una vez que arranqué el 10.04 mediante SGD, que perdí la señal. Pero son todas conjeturas.
Si a alguien le interesa tirar posibilidades, sigo acá, porque la verdad me quedé con ganas de saber qué pasó aunque, por ahora, no quiera volver a formatear ninguna partición, al menos, hasta octubre.

Saludos

---

### Post by alfplayer on 2010-05-04
Si es el modem negro vertical de Fibertel, el origen del problema puede ser el mismo que tuve que es dificultad para reconectarse con otra computadora si antes no se lo apaga.

Para intentar descartar a windows del problema podés probar, después de apagar la computadora, sin cambiar el orden:

[LIST]
[*]desconectar el cable de energía del modem
[*]esperar unos segundos o minutos
[*]reconectarlo
[*]esperar que se inicie el modem
[*]iniciar ubuntu
[/LIST]

---

