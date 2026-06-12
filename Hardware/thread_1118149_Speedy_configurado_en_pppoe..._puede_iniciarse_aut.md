---
title: "Speedy configurado en pppoe... puede iniciarse automaticamente?"
date: 2009-04-06
forum: Hardware
---

### Post by jochy2525 on 2009-04-06
Speedy configurado en pppoe... puede iniciarse automaticamente?

...

finalmente he logrado que el ******* Speedy funcione en ubuntu.. sin embargo al hacer una prueba de conectividad con dslreports me dice que tengo que modificar el RWIN .. no tengo idea como hacerlo! se puede mejorar la conexion a traves de algun codigo???

tambien me interesaria que me respondan una duda de tipo existencial:

realmente hay que poner cada vez q predo la PC , pon dsl-provider ... rompe mucho las */*/* .. la verdad q no entiendo ! xq cuando pongo pppoeconf me dice que si quiero q se inicie solo .. sin embargo, de automatico no tiene nada.

bueno gente .. siendo este mi primer post en el foro , les deseo muy buen dia para todos

---

### Post by andy_91 on 2009-04-06
buen dato yo ponia siempre sudo pppoeconf cada vez que prendia el pc ahora voy a probar con pon dsl-provider (es menos molesto que hacer todo el proseso siempre)

gracias no conocia ese comando ;)

---

### Post by josecuervo86 on 2009-04-06
Mira, yo hasta hace... a ver.... 24 horas cada vez que entraba tenia que ir a **red** y marcar las casillas de "Conexión cableada" y "Conexion punto a punto" para que se conectara a internet por speedy con un modem huawei mt880. Ayer a la noche puse **pppoeconf**, segui los pasos y puse que se iniciara automaticamente (ya estaba medio cansado de tener que hacer toda una perorata hasta poder conectarme) y salio andando solito. Ahora cada vez que prendo la PC arranca internet solo. Lo mas raro es que en **conexiones de red** no me reconoce la conexion, pero antes tampoco lo hacia.

---

### Post by jochy2525 on 2009-04-06
lo mas raro que ahora.. se conecta solo! no pongo ningun comando.. ya no entendio mas nada!

ahora bien... porque no la detecta como otro tipo de conexion? no tendria que aparecer la IP ??

tambien otra solucion posible es routear el modem, aca les dejo mi tutorial que esta en mi foro.. la solucion definitiva: [http://foro.comunidadcualquiera.com.ar/software-y-hardware-f5/routea-tu-modem-de-telefonica-y-evita-el-marcador-de-speedy-t421.htm](http://foro.comunidadcualquiera.com.ar/software-y-hardware-f5/routea-tu-modem-de-telefonica-y-evita-el-marcador-de-speedy-t421.htm)

la verdad es muy buena opcion, pero yo empece a tener mas problemas de velocidad de los que tengo... resulta queda como sin respuesta el modem, eso es xq se agotan las tablas NAT del modem... huawei smartax mt880= porqueria

---

### Post by josecuervo86 on 2009-04-06
> **jochy2525 said:**
>  huawei smartax mt880= porqueria

Que no te quede ninguna duda!! No veo la hora de jubilarlo :P

---

### Post by faktorqm on 2009-04-07
> **jochy2525 said:**
> tambien otra solucion posible es routear el modem, aca les dejo mi tutorial que esta en mi foro.. la solucion definitiva: [http://foro.comunidadcualquiera.com.ar/software-y-hardware-f5/routea-tu-modem-de-telefonica-y-evita-el-marcador-de-speedy-t421.htm](http://foro.comunidadcualquiera.com.ar/software-y-hardware-f5/routea-tu-modem-de-telefonica-y-evita-el-marcador-de-speedy-t421.htm)

LA solucion es routear, si todos los que postearon aca diciendo que tienen que escribir no se que en lugar de rutear del modem... bue. Pongan el modem en modo router, salvo que no se pueda. Si no saben como agregar al inicio del sistema algo para que corra un script, abran otro thread para no ensuciar este y les explico como se hace.

> **jochy2525 said:**
> la verdad es muy buena opcion, pero yo empece a tener mas problemas de velocidad de los que tengo... resulta queda como sin respuesta el modem, eso es xq se agotan las tablas NAT del modem... huawei smartax mt880= porqueria

que esperas amigo? comprate un cisco 1700! no vas a tener ninguno de todos los problemas que mencionas aca :lolflag:

hablando en serio: no creo que sea problema del modem en si sino de la calidad de tu linea. Lamentablemente esto puede ser una loteria y dependiendo donde vivas podes llegar a tener mas o menos velocidad que otro. No me acuerdo de memoria el modem ese a pesar que lo configure 150000 veces pero debe traer algo parecido a test de linea, o algo asi, para que te diga el ruido y todas esas cosas. Fijate y postea a ver que dice eso. 

ahh y no usen mas pppoeconf a menos que sea asquerosamente necesario :lolflag:

---

