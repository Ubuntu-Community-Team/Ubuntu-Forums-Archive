---
title: "Problema conección pppoe con network manager"
date: 2009-11-29
forum: Hardware
---

### Post by srsgraf on 2009-11-29
Que tal amigos. primero que nada me llamo sebastián y soy de chile.
el motivo es que me he instalado el karmic koala y esta buenísimo pero no puedo hacer o mejor dicho lograr conectarme al modem (telefónica)por medio de pppoe (no tengo router inalambrico). en el network manager configuro la conección con el nombre de usuario y la clave, y al tratar de conectarme no lo hace y vuelve a decirme que esta conectado a eth0 pero no a telefónica.
fuí a un lugar público en donde hay internet wifi y tampoco logró conectarse.
traté de hacer la conección pppoe por medio de la consola, pero no está instalada esa opción.

¿como logro conectarme por medio de cable (pppoe)?
¿que solución me pueden dar si no tengo como conectarme a internet?
¿que alternativa existe a network manager y como instalarlo?

ayuda please!!!

pd: el modem es zte.
gracias

---

### Post by CdK1 on 2009-12-01
Podrías especificar el modelo del modem...

---

### Post by moreback on 2009-12-02
Tienes que borrar la conexión "Auto eth0" que sale en la pestaña "Cableada" de las conexiones de red del Network-Manager. Ésta se está conectando primero y no te deja conectar con la conexión DSL que creaste.

Saludos.

---

### Post by prod_chileno on 2009-12-02
soy nuevo en esto y creo que este para mi ya es el ultimo medio antes de arrepentirme de haber migrado a linux... tengo el mismo problema que tu, pero la diferencia que yo si me pueod conectar a travez de una banda ancha movil, inalambrica, pero a la hora de conectarme a travez de lan con el modem de terra... nada funca, intento el pppoeconf en la consola y solo me reconoce 2 dispositivos ethernet: vboxnet0 y wlan0 cosa a la cual ninguno de elolos conecta, el dispositivo primero que nombre antes no aparecia nose de donde aparecio... heeeeeeeeeeeeelllllllllllp
 
muchas gracias

---

### Post by moreback on 2009-12-02
> **moreback said:**
> _Tienes que borrar_ la conexión "Auto eth0" que sale en la pestaña "Cableada" de las conexiones de red del Network-Manager. Ésta se está conectando primero y no te deja conectar con la conexión DSL que creaste.

Saludos.

No es tan necesario borrar la conexión **Auto eth0**, basta con editarla y quitarle el tic a la opción **Conectar automáticamente**.

Saludos.

---

### Post by themasterdark on 2009-12-05
Justo me encontraba con el problema del pppoe por red cableada.... y bueno les cuento como lo solucione hace como 3 hrs. atras jaja xD

bueno no ahi nada que hacerle a eth0 por si acaso, dejenlo así tal cual.

bueno les cuento... 

primero que nada deben agregar un repositorio (por lo que deberán estar conectados a internet de alguna forma alternativa, una red de algún local, universidad, o etc...) 

bueno al grano.

el repositorio que deben agregar es:

deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main

El cual no es nada mas, que una versión posterior de NetworkManager a la que trae karmic.

bueno no comentare como agregarlo, poke ya ahi mucha informacion en la red.

luego de eso simplemente hacen un:

sudo aptitude update

sudo aptitude full-upgrade

con ello... reinicien su pc o notebook.

abran una terminal y para asegurarnos que funcione borraremos las conecciones que existan.

en un terminal:

sudo gedit /etc/network/interfaces

y borren todo, que no ahi problema ya que toma automatico las cableadas autoconfiguradas.

bueno luego de eso, hacemos click derecho en el icono de red del NetworkManager que aparece en la barra de tareas, y creamos una nueva conecciones dsl, allí, agregamos todos los datos y le dejamos sin el click de conectar automaticamente, asi se aseguran de que estan conectados a esa red.

Listo...
boton izquierdo en el mismo icono de NetworkManager y conectar a la red que uds. Hicieron (el nombre que le pusieron cosa de uds.)

Saludos.!!

---

