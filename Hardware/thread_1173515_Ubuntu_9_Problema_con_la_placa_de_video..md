---
title: "Ubuntu 9: Problema con la placa de video."
date: 2009-05-29
forum: Hardware
---

### Post by Hadso on 2009-05-29
Hola gente, una vez mas recurro a su amable ayuda. 
Acabo de instalar Ubuntu 9 en una PC AMD Athlon 64, placa onboard Asus, RAM 1.2.
En fin, Windows anda muy bien y todo eso. Pero Ubuntu, si bien ando bien, noto a lo gráficos un poco lentos. Los slides y efectos también. 
Creo que el tema es la configuración de la placa de video. 
Busqué como saber cuál es la placa que tengo y me aparece lo siguiente: 

01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

Despues, traté de configurarla con:

sudo envyng -g

Pero el programa no me dice exactamente que placa tengo y no me atrevo a andar adivinando, 

Por lo tanto:
1) Me gustaría saber si el problema es la placa de video. Los gráficos se ven lentos, los efectos, los videos en fullscreen, etc. 

2) De ser ese el problema, como puedo resolverlo?

3) Si el problema no es la placa de video, cuál es?

Muchas gracias a todos!

---

### Post by pablo.s on 2009-05-29
Consejo rápido: comprá una 
p&#314;aca de video. Lo que tenés
apenas califica, por lo menos
en GNU/Linux.
Hay otros posts con el mismo
problema: 


[http://ubuntuforums.org/showthread.php?t=1154393](http://ubuntuforums.org/showthread.php?t=1154393)
[http://ubuntuforums.org/showthread.php?t=1163603](http://ubuntuforums.org/showthread.php?t=1163603)

---

### Post by Hadso on 2009-05-29
> **pablo.s said:**
> Consejo rápido: comprá una 
p&#314;aca de video. Lo que tenés
apenas califica, por lo menos
en GNU/Linux.
Hay otros posts con el mismo
problema: 


[http://ubuntuforums.org/showthread.php?t=1154393](http://ubuntuforums.org/showthread.php?t=1154393)
[http://ubuntuforums.org/showthread.php?t=1163603](http://ubuntuforums.org/showthread.php?t=1163603)

Hay alguna solución que no implique cambiar la placa de video?

Gracias!

---

### Post by pablo.s on 2009-05-29
> **Hadso said:**
> Hay alguna solución que no implique cambiar la placa de video?

Es el paso más barato, creeme.

---

### Post by Hei Ku on 2009-05-29
Busca en los varios threads que existen sobre este tema.

Con suerte, vas a tener mala performance incluso si logras instalar los drivers.

---

### Post by Hadso on 2009-05-29
> **pablo.s said:**
> Es el paso más barato, creeme.

Entiendo, he visto que hay muchos problemas. 
Pero me gustaría intentarlo... donde puedo encontrar información? 
O tengo que empezar por buscar a lo loco por internet?

Gracias!

---

### Post by josecuervo86 on 2009-05-29
Las placas VIA andan pesimamente en GNU/linux, si no me crees preguntale a Guillermolisi :P

---

### Post by pablo.s on 2009-05-29
Hay muchos posts en este
foro sobre ese tipo de placas.
Te recomiendo que los
leas y veas las diferentes
experiencias de cada uno
de los que intentaron
hacer funcionar el 3D de las
placas UniChrome.

---

### Post by Hei Ku on 2009-05-29
En este mismo foro hay muchos threads con info sobre el tema.
Con poner VIA en el campo de Search, te van a aparecer un monton de lugares para buscar.

---

### Post by Hadso on 2009-05-29
> **pablo.s said:**
> Hay muchos posts en este
foro sobre ese tipo de placas.
Te recomiendo que los
leas y veas las diferentes
experiencias de cada uno
de los que intentaron
hacer funcionar el 3D de las
placas UniChrome.

El tema es que no me interesa lograr los efectos, correr compiz y todo eso. 
Simplemente quiero que los gráficos se vean de manera aceptable. 
Ya de por sí me está costando encontrar los drivers, pero instalarlos, leí por ahí, no es díficil. O sí?

---

### Post by pablo.s on 2009-05-29
El problema principal
es que utiliza el modo VESA,
que no sirve para ver videos
ni nada con movimiento.
Ni siquiera Flash, es muy
viejo, por decirlo asi.
Por eso te recomendamos
comprar cualquier otra
placa que funcione, supongamos
una ATI o Nvidia baratas.

---

### Post by Hadso on 2009-05-29
> **pablo.s said:**
> El problema principal
es que utiliza el modo VESA,
que no sirve para ver videos
ni nada con movimiento.
Ni siquiera Flash, es muy
viejo, por decirlo asi.
Por eso te recomendamos
comprar cualquier otra
placa que funcione, supongamos
una ATI o Nvidia baratas.

Seguiré buscando data. Por lo menos hasta que tenga los 50 U$S para la placa. 
Gracias.

---

### Post by Hei Ku on 2009-05-29
La wiki de ubuntu tiene un tutorial para estas placas. [https://wiki.ubuntu.com](https://wiki.ubuntu.com)

---

### Post by guillermolisi on 2009-05-29
Las placas de video VIA usan el driver Vesa porque los drivers que desarrollaron para Linux, disponibles en [Via Arena]("http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220"), apestan.

Podes probar con los de ellos, con los libres, con Openchrome, con Unichrome, si funciona con resolucion (>1024x768 ) y velocidad adecuadas, por lo menos con aceleracion 2D, me comprometo a pagar la proxima Release Party en un hotel cinco estrellas de cadena internacional ;)

---

### Post by sajnox on 2009-05-30
Esta (0) maquina usa Linux y una placa de red Via Chrome y he visto la maquina andando decentemente, no creo que haya tenido aceleracion 3d, pero andaba....tambien recuerdo que cuando lo busque habia un flaco que mezclando los xorg.conf de ambos SO (ubuntu y zonbu) habia logrado hacerla andar decentemente, sera cuestion de buscar un poco por ese lado

(0) [http://www.zonbu.com/shop/product.php?productid=30&cat=2&page=1](http://www.zonbu.com/shop/product.php?productid=30&cat=2&page=1)

PS: Tengo ganas de que la placa ande para ver las excusas que pone Guille para no pagar la release party en las condiciones que dice qeu lo haria

---

### Post by guillermolisi on 2009-05-30
> **sajnox said:**
> Esta (0) maquina usa Linux y una placa de red Via Chrome y he visto la maquina andando decentemente, no creo que haya tenido aceleracion 3d, pero andaba....tambien recuerdo que cuando lo busque habia un flaco que mezclando los xorg.conf de ambos SO (ubuntu y zonbu) habia logrado hacerla andar decentemente, sera cuestion de buscar un poco por ese lado

(0) [http://www.zonbu.com/shop/product.php?productid=30&cat=2&page=1](http://www.zonbu.com/shop/product.php?productid=30&cat=2&page=1)

PS: Tengo ganas de que la placa ande para ver las excusas que pone Guille para no pagar la release party en las condiciones que dice qeu lo haria
Pasaron mas de dos años hasta que me decidi poner una placa nVidia a una de las maqunas con video VIA. Mientras la usaba con driver Vesa y a 1024x768, sin aceleracion de ninguna clase, con KDE 3.5. La maquina tiene 2Gb RAM asi que por lo menos a 128 para video llego y aun asi, probando los drivers disponibles, leyendo casos exitosos (uno solo pero que nadie pudo confirmar porque no se repitio) y varias "recetas" .. nada.

Varios pudieron lograr cierta aceleracion 2D que se arrastraba y decidieron volver a Vesa.

PS: Antes de poner mi compromiso lo pense 3 veces y conte hasta diez ... y si funciona comprobadamente sere un beneficiado aunque tenga que honrar mi palabra (y me gaste varios morlacos que tambien voy a disfrutar). ;)

---

### Post by pablo.s on 2009-05-30
Guille, te costaba menos 
pagarle una placa de 200
pesos al amigo... Ahora
se complicó la cosa.

---

### Post by Hei Ku on 2009-05-30
Podemos empezar por aca:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Guille, mira que de dificiles que somos capaz que la sacamos andando. :lolflag:

---

### Post by guillermolisi on 2009-05-30
> **Hei Ku said:**
> Podemos empezar por aca:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Guille, mira que de dificiles que somos capaz que la sacamos andando. :lolflag:
Ya voy haciendo la prevision de fondos, por las dudas ... si no tengo que pagar el compromiso le dare otro destino :D

El asunto, como para que no queden dudas, es que tenga por lo menos aceleracion 2D que permita una operabilidad razonable del escritorio grafico. Si la misma maquina con drivers Vesa iguala o supera resolucion, aceleracion y operacion, queda descartada la prueba.

---

### Post by sajnox on 2009-05-30
> **guillermolisi said:**
> El asunto, como para que no queden dudas, es que tenga por lo menos aceleracion 2D que permita una operabilidad razonable del escritorio grafico. Si la misma maquina con drivers Vesa iguala o supera resolucion, aceleracion y operacion, queda descartada la prueba.

Ya estas arrugando.....el tema es que hagamos (aramos dijo el mosquito) andar la placa en forma decente, no me importa con que drivers

Hei Ku que preferis - El Hilton o el Four Seasons?, es mas si lo paga Guille yo le pago el pasaje Marianom para que se venga

---

### Post by pablo.s on 2009-05-30
Después dicen que el
Software Libre carece
de motivación...

---

### Post by Hei Ku on 2009-05-30
Hadso, podes postear tu xorg.conf?

Y tambien el resultado de ejecutar glxinfo en una terminal.

---

### Post by guillermolisi on 2009-05-30
> **sajnox said:**
> Ya estas arrugando.....el tema es que hagamos (aramos dijo el mosquito) andar la placa en forma decente, no me importa con que drivers

Hei Ku que preferis - El Hilton o el Four Seasons?, es mas si lo paga Guille yo le pago el pasaje Marianom para que se venga
No es arrugue, es especificacion para que cualquiera sepa si se cumplio el objetivo o no (ya sea el de hacer funcionar la placa o de que cumpla mi compromiso) ;)

Decente es un termino demasiado abarcativo. Cualquier driver va bien mientras alcance o supere las especificaciones, porque ya hay uno que la hace funcionar que es Vesa pero no cuenta para el caso (no como vidrio, por ahora). Por eso hable de Unichrome y OpenChrome.

Sin especificaciones queda el tema a juicio altamente subjetivo.

---

