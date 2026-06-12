---
title: "Acer Aspire One - WIFI no funciona"
date: 2009-05-15
forum: Hardware
---

### Post by jclevien on 2009-05-15
Hola que tal,

Les cuento que adquirí una notebook Acer Aspire One "mejorada" (1.5 GB RAM, disco de 320 GB y batería de 9 horas), venía con Windows XP Home y decidí cambiarlo por Ubuntu 9.04 Jackalope debido a que el mismo posee el Rosegarden y otras cosas de importancia para mi (más que nada la red neuronal ffnet para Python).

Bien, para mi asombro funciona todo perfecto... menos la placa wifi integrada. No encuentro la manera de hacerla funcionar, he probado de instalar ndiswrapper, el driver ath5k y ath9k, el madwifi alternativo... no hay caso, o sea, detecta que hay una placa wlan0 pero no puede ver redes disponibles (y se que las hay porque lo probe en un lugar con soporte Wifi).

La versión que estoy usando de Ubuntu es la 9.04 Jaunty Jackalope Desktop con GNOME.

La pregunta natural es: ¿conocen algún tutorial que pueda resolver este problema que no sea como los que mencioné? (y que funcione claro) :)

¡Por supuesto que les agradezco su ayuda desde ahora!

Juan

---

### Post by jpmorelli on 2009-05-15
Yo tengo una Acer Aspire One con Ubuntu 9.04 instalado y funciona perfecto ! Tal vez porque hice un upgrade desde la 8.10 para la cual si tuve que seguir un tutorial para hacerla funcionar...pero la verdad que yo compile el driver para esa versión cuando había salido y ahora el nuevo kernel de jaunty me la tomo automaticamente.

Te paso el link del tutorial super bien explicado para que te fijes cualquier cosa, acordate que está hecho para Ubuntu 8.10 !

Saludos y cualquier cosa chiflá !

[http://www.emezeta.com/articulos/ubuntu-8-10-en-acer-aspire-one]("http://www.emezeta.com/articulos/ubuntu-8-10-en-acer-aspire-one")

---

### Post by jclevien on 2009-05-15
Hola jmorelli,

La verdad que tuviste suerte, porque yo instalé el Jaunty de cero y nada.
El truco de compilar el madwifi lo hice también, y no funcionó.

Otra cosa: ¡el GNOME es un desastre! La pantalla tiembla cada 5 minutos, y luego de unos 8 se pone totalmente blanca, obviamente virus no será, ya tuve varios problemas con GNOME y el vino, en versión Hardy.

Voy a optar por XFCE, me parece el entorno más sólido y liviano, tengo una máquina que le instalé un Mint XFCE Elyssa y anda muy bien sin colgarse.

Volviendo al tema wifi, estoy un poco triste, porque la verdad me sorprendió la excelente velocidad (si! puedo instalar el Ubuntu en XFS y el GRUB lo aguanta bien!), solo es este "detalle" del wifi... ¿alguna otra alternativa se te ocurre?

Desde ya mil gracias por la ayuda.


Juan

---

### Post by Hei Ku on 2009-05-15
Primero que nada, podrias postear el resultado de correr lspci en una terminal, para saber bien qué placa wifi tenes.

---

### Post by pablo.s on 2009-05-15
Si no me equivoco, ese es un modelo
de netbook. Hubieras tenido mas éxito
si hubieras instalado un sistema más
acorde a la maquina como por ejemplo
Ubuntu Netbook Remix o Crunchbang
Linux para netbooks, que ya vienen con
lo necesario para el WiFi de gran cantidad
de netbooks y un kernel compilado para
los procesadores Atom, habilitando el bajo
consumo de energia y la resolución de
pantalla.

---

### Post by Hei Ku on 2009-05-15
Te fijaste en esta pagina las recomendaciones y guias que da?

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by jclevien on 2009-05-15
Gracias por sus respuestas.

Voy a probar la versión Remix que menciona pablo.s, instalé el Xubuntu y va OK, pero lamentablemente luego de cierto tiempo la pantalla también se pone blanca misteriosamente al igual que con GNOME y estoy obligado a apagar la máquina.

Estoy sospechando que la opción de pablo.s es la más viable, ya que esa versión debe incluir drivers y demás yerbas específicos para esta netbook.

Nuevamente, gracias, les cuento como me fue con las pruebas usando Remix.


Juan

---

### Post by jclevien on 2009-05-16
Bueno, finalmente pude bajar el archivo img del Netbook remix, perdí una primera descarga por corte de luz cuando iba al 50% y luego lo pude bajar en 4 horas...

Bien, ya lo tengo andando al Remix en mi laptop, el único inconveniente que tengo es el temblequeo de mi pantalla (aclaro que poseo un monitor externo de 17" que uso cuando estoy en casa junto a la laptop).

Digamos que no es algo con lo que no pueda vivir, pero da la sensación de que la máquina se va a colgar en cualquier momento........ :(

¿Por casualidad les ha pasado algo similar?

Gracias.


Juan

---

### Post by pablo.s on 2009-05-16
¿Temblequeo?
Fijate a que tasa de refresco está
configurado el monitor externo y
de ser posible, probá aumentarla.

System - Preferences - Display

---

### Post by jclevien on 2009-05-16
Listo pablo.s, lo que hice fue esto:

1. Actualicé los drivers Intel de la placa a la última version. Paso la URL por si alguien necesita resolver este problema: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/")

2. Además hay que activar una opción del xorg.conf, que está aquí: [http://kb.huptas.net/2008/02/21/ubuntu-804-hardy-heron-issues-w-external-screen-and-intel-gma950-dell-latitude-d620/]("http://kb.huptas.net/2008/02/21/ubuntu-804-hardy-heron-issues-w-external-screen-and-intel-gma950-dell-latitude-d620/")

El ítem 1 me resolvió la pantalla negra/blanca repentina, el ítem 2 el temblequeo.

Gracias a todos por sus respuestas.


Juan

---

