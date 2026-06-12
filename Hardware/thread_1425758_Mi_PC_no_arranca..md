---
title: "Mi PC no arranca."
date: 2010-03-09
forum: Hardware
---

### Post by rubioo on 2010-03-09
Hola les paso a contar el problema que tengo.

Hoy cuando prendo mi compu, luego de que realiza el POST me aparece esto:

> 
Grub Loading
free magic is bronken at 0x41f32b00: 0x10
Aborted. Press any key to exit.

Reboot and select proper boot device
or insert boot media in selected boot device
and press any key
 

Despues de esto, la reinicio y sigue apareciendo lo mismo (la habré reiniciado 20 veces).
También intente bootear con 3 live cds y no arrancaban, ubuntu y opensuse se quedaban 'colgados' y fedora me tiraba un kernel panic (los live cds funcionan ya que hace un par de meses los probé).
Hasta que mágicamente apareció el menú de grub normal y pude entrar a ubuntu.


Cualquier ayuda/sugerencia es bienvenida.

 
Saludos!
PD: tambien

---

### Post by guillermolisi on 2010-03-09
Tiene toda la pinta de ser algun problema de hardware. Me baso en que los CDs Live que probaste tampoco funcionaron, con lo cual descarto que sea el disco rigido y su contenido.

El disco y la lectora que interface usan, IDE ? SATA ? Mixta (uno es SATA y el otro IDE), SCSI ?

Probaste de iniciar la maquina desde un Live pendrive/usb ?

---

### Post by rubioo on 2010-03-10
Perdon por no responder antes, es que recien ahora pude entrar a ubuntu :S

El disco usa SATA y la lectora IDE. Y no pude probar con un pendrive.
Hoy probe con mas live cds y con ninguno arrancaba.
Ademas me aparecia esto (en lugar del mensaje de ayer), aunque a veces me aparece el de ayer y otras este.

> 
Out of range pointer 0x41f71e00
Aborted. Press any key to exit.


---

### Post by guillermolisi on 2010-03-10
Esa unidad optica estara en buenas condiciones operativas o llego la hora del recambio ?
Que pasa si le pones a esa maquina otra unidad temporalmente para hacer pruebas ?

---

### Post by rubioo on 2010-03-10
Espero que este en buenas condiciones. En estos dias estuve grabando cds y dvds, parecia estar bien.
Y no tengo otra para probar :(

---

### Post by anarko on 2010-03-11
Pone el live CD de ubuntu y hace el mem test y dejalo toda la noche. 
Te sacas la duda de si tenes la memo pinchada, puede ser tambien un recaletamiento de algun componente.

---

### Post by rubioo on 2010-03-11
Bueno, esta noche la dejo haciendo el test.
Y tambien la podria limpiar por dentro, no?

---

### Post by rubioo on 2010-03-12
Termino el test y no encontro ningun error.
Tambien encontre esto:
[http://www.ubuntu-es.org/?q=node/125439]("http://www.ubuntu-es.org/?q=node/125439")

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/498882]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/498882")

---

### Post by guillermolisi on 2010-03-12
> **rubioo said:**
> Termino el test y no encontro ningun error.
Tambien encontre esto:
[http://www.ubuntu-es.org/?q=node/125439](http://www.ubuntu-es.org/?q=node/125439)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/498882](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/498882)
Estas evaluando la alternativa de pasarte a Grub 1 ? Podria ser una solucion contundente para tu caso hasta que se aclare y resuelva cual es el problema con Grub2 ?

Un solo caso denunciado como bug hasta la fecha, asi que se me ocurre que es bastante particular. Mientras se mantenga con baja cantidad de informes, no creo que le den una prioridad "interesante" para resolverlo, es mas, a esta altura es posible que lo programen para el nuevo release de Ubuntu dada su proximidad (lo cual seria bastante bueno).

---

### Post by rubioo on 2010-03-12
Desde que hice el test y hasta ahora, las 3 o 4 veces que la reinicie arranco bien.
Asi que vamos a ver como sigue la mano, si empieza a hacer lo mismo que antes instalo grub1.

Porque otra 'solucion' parece no haber todavia.

---

### Post by naldocz on 2010-03-12
**problemas con arranque de ubuntu 9.10** 			 			 			 		   		 		 		Hola chicos..
ando con algun problemita que no se como solucionarlo y espero la gran  ayuda de ustedes.
les cuento que hace unas semanas installe en mi pc sin particion de  disco, la version 9.10 de ubuntu y que hasta el momento funcionaba de  maravilla, si pero de repente no comenzo a iniciarse directamente en  ubuntu sino que me da para la eleccion de inicializar desde ubuntu,  linux 2.6.31-20-generic y versiones anteriores con sus respectivos  recovery mode y luego el memory test.
cuando doy para que inicie en la primera opcion ubuntu linux 2.6.32-20  generic, me lleva a la siguiente: 

Filesystem check failed
a maintenance shell will now be started
CONTROL-D will terminate this shell and re-try
root@users- desktop:

y ya no va adelante.
con la desesperacion e intentado con el cd del supergrub y con el livecd  de ubuntu 9.10 para re instalarlo pero sin ningun resultado... es como  si no los leyera..
entonces les pido una gran ayuda para salir de esta que no entiendo por  que de repente paso esto.
gracias y a la espera..

---

### Post by guillermolisi on 2010-03-12
> **naldocz said:**
> **problemas con arranque de ubuntu 9.10**                                                                             Hola chicos..
ando con algun problemita que no se como solucionarlo y espero la gran  ayuda de ustedes.
les cuento que hace unas semanas installe en mi pc sin particion de  disco, la version 9.10 de ubuntu y que hasta el momento funcionaba de  maravilla, si pero de repente no comenzo a iniciarse directamente en  ubuntu sino que me da para la eleccion de inicializar desde ubuntu,  linux 2.6.31-20-generic y versiones anteriores con sus respectivos  recovery mode y luego el memory test.
cuando doy para que inicie en la primera opcion ubuntu linux 2.6.32-20  generic, me lleva a la siguiente: 

Filesystem check failed
a maintenance shell will now be started
CONTROL-D will terminate this shell and re-try
root@users- desktop:

y ya no va adelante.
con la desesperacion e intentado con el cd del supergrub y con el livecd  de ubuntu 9.10 para re instalarlo pero sin ningun resultado... es como  si no los leyera..
entonces les pido una gran ayuda para salir de esta que no entiendo por  que de repente paso esto.
gracias y a la espera..
Si abris un nuevo hilo por este tema no pongas el mismo mensaje en otro que, si bien tambien esta referido al arranque del sistema, posiblemente tenga otra solucion distinta al tuyo porque podrian ser causas diferentes las que provocan el problema.

El hilo sobre tu consulta esta [aqui]("http://ubuntuforums.org/showthread.php?t=1428294").

---

### Post by rubioo on 2010-03-13
Bueno, desde ayer a la tarde que no puedo entrar a ubuntu ni a windows.
Sigue apareciendo lo mismo, e hice otra vez el memtest desde el live cd y ahora me dice que hay muchos errores (demasiados). :S

No se que hacer.

---

### Post by guillermolisi on 2010-03-13
> **rubioo said:**
> Bueno, desde ayer a la tarde que no puedo entrar a ubuntu ni a windows.
Sigue apareciendo lo mismo, e hice otra vez el memtest desde el live cd y ahora me dice que hay muchos errores (demasiados). :S

No se que hacer.
O hay una placa de memoria que no esta haciendo buen contacto con el peine del slot o esta falluta y a veces funciona bien y otras no (puede ser temperatura en las placas de memoria que hace que funcione mal y si funciona mal levanta mas temperatura).

El memtest tiene pruebas cortas y otras muy extensas y detalladas. Creo que para este caso amerita una prueba bien a fondo.

No vendria mal revisar fisicamente las placas de memoria y su insercion en cada slot como tampoco cambiar su orden, si son mas de una, asi podria determinarse cual de las dos anda mal (o tres o cuatro) con pruebas sucesivas.

Lo mas importante del caso es que si las memorias estuvieran en condiciones confiables nunca, durante ninguna sesion de pruebas, deberian dar errores. Si en uno dan errores, ya da para pensar en su reemplazo.

---

### Post by rubioo on 2010-03-13
Antes que nada, te queria agredecer por ayudarme :)
Ahora pude entrar a ubuntu. La prendi y arranco como si nada :S
Asi que, voy a aprovechar para hacer backups (por las dudas) y mas tarde o mañana a primera hora, la desarmo y me fijo que este todo bien.

---

### Post by rubioo on 2010-03-14
Hoy limpie toda mi compu. Y hasta ahora va bien. Espero que continue asi :)

---

