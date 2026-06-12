---
title: "Colgada rara"
date: 2008-03-21
forum: Hardware
---

### Post by euzkoarima on 2008-03-21
Hola gente, estoy teniendo dos o tres veces por día una colgada bastante rara (y molesta), estoy trabajando lo mas bien y de repente se pone una pantalla de solo texto (tipo como si hubiese hecho <ctrl><alt>F2) durante menos de un segundo (o sea, no llego a ver que dice) y se reinicia el systema, más bien, es como si hubiese forzado un cerrar sesión. Es decir, no reinicia todo, me vuelve a pedir login.

Lo único en común hasta ahora es el firefox abierto, pero no le hecho la culpa, a veces estaba en background.
La pregunta: que archivos de log tendría que mirar como para comenzar a descubrir que pasa y ver si puedo solucionarlo??
Cualquier otra idea es bienvenida.

Saludos.

---

### Post by newtonfn on 2008-03-21
No estoy seguro, pero yo comenzaría mirando /var/log/Xorg.0.log
Tambien messages, que aunque no creo tenga nada que ver nunca está de mas mirarlo tampoco.

Tampoco estoy seguro, pero a veces algunas aplicaciones dejan un log de algunos errores en el home del usuario.. si hay algun archivo ahi'tambien deberías revisarlo. (Se que el nautilus a veces me dejaba cosas ahí.. .que otra aplicacion, o el motivo, que lo haga, desconozco)

---

### Post by euzkoarima on 2008-03-22
Gracias, no econtré nada aún. Aviso si encuentro algo.

Saludos

---

### Post by euzkoarima on 2008-03-22
Bien, acaba de colgarse, paso lo que "creo" da algo de información. De los logs saco esto

En auth.log
> Mar 22 18:19:28 PC-Wado gdm[14533]: pam_unix(gdm:session): session closed for user wado
Mar 22 18:19:45 PC-Wado gdm[16873]: pam_unix(gdm:session): session opened for user wado by (uid=0)
Mar 22 18:19:45 PC-Wado gdm[16873]: gkr-pam: unlocked 'login' keyring

de daemon.log
> Mar 22 18:19:28 PC-Wado gdm[14533]: WARNING: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0 

de syslog
> Mar 22 18:17:01 PC-Wado /USR/SBIN/CRON[16837]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 22 18:19:28 PC-Wado gdm[14533]: WARNING: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0 
Mar 22 18:19:48 PC-Wado hcid[5360]: Default passkey agent (:1.136, /org/bluez/passkey) registered
Mar 22 18:19:48 PC-Wado hcid[5360]: Default authorization agent (:1.136, /org/bluez/auth) registered
Mar 22 18:19:50 PC-Wado NetworkManager: <info>  Updating allowed wireless network lists. 
Mar 22 18:19:50 PC-Wado NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

y de Xorg.0.log
> AUDIT: Sat Mar 22 18:19:32 2008: 16876 X: client 2 rejected from local host (uid 1000)
AUDIT: Sat Mar 22 18:19:32 2008: 16876 X: client 3 rejected from local host (uid 1000)

Alguna idea??

---

### Post by Hei Ku on 2008-03-22
busca en el messages.log si ves algo a las 18:19:28

El error clave parece ser 

Mar 22 18:19:28 PC-Wado gdm[14533]: WARNING: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0

---

### Post by euzkoarima on 2008-03-22
justo a esa hora nada, pero alrededor de esa hora dice

> Mar 22 18:05:34 PC-Wado kernel: [159709.236000] atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
Mar 22 18:05:34 PC-Wado kernel: [159709.236000] atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.
Mar 22 18:24:05 PC-Wado -- MARK --
Mar 22 18:34:27 PC-Wado exiting on signal 15

dicho sea de paso, volvio a colgarse, los mensajes en los logs son casi los mismos salvo por la hora. Patrón hay, pero que es, ni idea.

---

### Post by newtonfn on 2008-03-22
Puedo estar equivocandome feo, en mi pequeña experiencia, y por lo que vi al revisar un poco en internet la madre de todos los problemas es el video.

Si los efectos de escritorio estan activados, desactivalos.
Si estas usando drivers propietarios, desinstalalos y volvé a los free.

Y ya que estamos, comentanos que equipo tienes. Y algo que no me quedó claro, si esto sucede desde siempre o antes andaba bien y de la nada comenzó a pasar.

Finalmente, aunque parezca una tontería, en estos foros (pero en ingles) varias personas se quejaron de un error similar, e incluso todos dicen tener el Firefox abierto.. tal vez sea innecesario, pero no vendría mal intentar no usarlo. Podrías instalar en su lugar Opera u algun otro explorador como Epiphany

Espero tengas suerte con tu problema.
Saludos

---

### Post by newtonfn on 2008-03-22
Otro detalle.. aparentemente hay otro log de error que podría ser interesante ver.
Fijate en /var/log/gdm/:0.log para ver si hay algo que pueda arrojar un poco de luz al problema.

---

### Post by euzkoarima on 2008-03-22
Varias cosas, primero me pasa desde hace unos dias solamente. Además tambien pasa sin firefox abierto. Quizas estoy paranoico, pero me parece que el mouse tiene que ver, por las dudas acabo de sacar el que tenia (PS2) y puse uno usb.
Con respecto al log del gdm dice

> X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux PC-Wado 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 22 19:30:28 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
SetClientVersion: 0 9

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c95d1]
1: [0xffffe420]
2: /usr/bin/X [0x817e389]
3: /usr/bin/X [0x817ad15]
4: /usr/bin/X(CompositePicture+0x153) [0x8161223]
5: /usr/bin/X [0x81674ff]
6: /usr/bin/X [0x8164425]
7: /usr/bin/X [0x815765e]
8: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
9: /usr/bin/X(main+0x495) [0x8076f05]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d5f050]
11: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting

Estuve buscando en internet y vi que es un bug levantado en launchpad, y que en debian y suse tambien pasa.
Nadie parece tener claro que pasa pero apuntan a lo mismo que comentas, efectos graficos, placas de video, etc.

Mi plan: primero ver que pasa con el mouse usb, despues reconfiguar xorg como sugieren algunos, y despues sacar compiz.

Bueno por un par de dias no voy a estar, pero le martes vuelvo a la carga con esto.

Gracias.

---

### Post by Hei Ku on 2008-03-23
Ahora que decis, a mi me pasaba algo similar cuando usaba Compiz. Era muy extraño, pero pasaba si iniciaba KDevelop y cambiaba de escritorio antes que terminara de cargar. O sea, si no me quedaba viendo como cargaba, me reiniciaba el X.
Despues de actualizar a Gutsy el Compiz en KDE me anduvo para atras, asi que deje usarlo y me olvide, pero es muy similar a tu experiencia.

---

### Post by newtonfn on 2008-03-23
Bueno, lo positivo es que hay un backtrace que dice que un error se produjo, lo negativo es que no dice mucho. Pero se puede pensar que el problema está en una función llamada FontFileCompleteXLFD u otra llamada CompositePicture, u otras que desconocemos el nombre, o un error en cualquier otro lugar que no esta en el backtrace pero se manifiesta recien en esta instancia (o sea en cualquier lado)

Como dices que antes andaba y despues dejo de andar bien, seria bueno que deshagas cualquier cambi oque hiciste en ese tiempo, tal vez algun programa, alguna configuración o algo fue el causante del problema.

Yo sigo poniendole mis fichas a Compiz y/o los drivers que estan trayendo problemas, pero tambien podés probar quitando las fuentes del sistema, despues de todo el backtrace habla de un problema con un archivo de fuentes. (en este r[eporte de error de launchpad]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/71913") un usuario dice haber solucionado el problema eliminando el directorio /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType)

En este mismo lugar alguien reportó haberlo solucionado desactivando glx. Con lo cual se va toda mejora grafica que quieras, e impide el funcionamiento de compiz, asi que esto sería bueno hacerlo si desactivar compiz no logra solucionar el problema.

En todo caso mi consejo es que lo primero a intentar, luego de cambiar el mouse que no es gran lio, sea desactivar compiz. Y esto te aconsejo hacerlo aún antes de reconfigurar xorg. (mi temor es que al reconfigurar xorg se reconfigure pero compiz no ande... nunca lo hice asi que no se.. pero es probable)

En fin, espero que cuando regreses tengas suerte en este asunto. Es bastante desagradable que se cierre la interfaz grafica si previo aviso.

---

### Post by euzkoarima on 2008-03-25
Bueno, les cuento como va la cosa. Primero como estaba convencido que el mouse tenia algo que ver puse uno usb y nada, se cuelga igual. Después me acordé que si bien no había instalado nigún soft nuevo (solo había aceptado los updates de los repositorios) lo que si había hecho, más o menos coincidente con el inicio de las colgadas fue cambiar el tema que uso en emerald.
Así que volví al viejo tema (con el que se supone que las cosas funcionaban), pero no, se cuelga, eso sí, mucho más espaciado (1 vez cada 3 horas en vez de cada 40 minutos, mas o menos).

Otra cosa: siempre que se cuelga (al menos los úttimos dias) es después de un click del mouse, típiciamente en los botones para minimizar o cerrar ventanas. Decidí que voy a probar por un rato de usar <alt>F9 y <ctrl>w a ver si con eso no se cuelga (no más de curiosidad, porque tampoco seria *LA* solución, pero ya que estamos).

Contesto a quien pregunto que equipo tengo
gabinete vitusuba 8030
micro amd athlon X2 5200+
mother Gigabyte GA-M57SLI-S4
Placa de video GeForce 7300 LE (marca sentey)
2G de ram

Otra, en una colgada de hoy me dio los siguentes logs, lo raro es que no se de que wireless me habla, se supone que no tengo nada de eso

auth.log
> Mar 25 17:24:24 PC-Wado gdm[5390]: pam_unix(gdm:session): session closed for user wado
Mar 25 17:24:36 PC-Wado gdm[6839]: pam_unix(gdm:session): session opened for user wado by (uid=0)
Mar 25 17:24:36 PC-Wado gdm[6839]: gkr-pam: unlocked 'login' keyring

daemon.log
> Mar 25 17:24:24 PC-Wado gdm[5390]: WARNING: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0 
Mar 25 17:24:39 PC-Wado NetworkManager: <info>  Updating allowed wireless network lists. 
Mar 25 17:24:39 PC-Wado NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

syslog
> Mar 25 17:24:24 PC-Wado gdm[5390]: WARNING: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0 
Mar 25 17:24:39 PC-Wado NetworkManager: <info>  Updating allowed wireless network lists. 
Mar 25 17:24:39 PC-Wado NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

Por útlimo se me ocurre el siguiente orden de pruebas para normalizar la cosa y si es posible quisiera opiniones/sugerencias al respecto

1. reconfigurar el xserver
2. eliminar emerald
2 eliminar compiz.

Gracias y saludos

---

### Post by euzkoarima on 2008-03-28
Bueno, finalmente seguí los consejos de newtonfn y en vez de reconfigurar el xserver desactive compiz (y obviamente emerald). Ahora estoy en gnome "normal" sin ningún efecto gráfico y .... SOLUCIONADO.

No se colgó más desde que desactivé hace 2 días.

Saludos y gracias a todos.

---

### Post by alejandro.mc on 2008-03-31
Tengo el mismo problema que vos. Esa misma tildada, igual que como la describis. Obviamente tambien estoy usando COmpizDusion a full, todos los efectos, sin placa de video dedicada. Por ende se entiende, pero no me pasa muy seguido de hecho me paso solo 4 veces. 

Si te pasa mas seguido por ahi podrias probar desactivar algunas cosas de CompizFusion, no todo.

Saludos.

---

### Post by euzkoarima on 2008-04-01
Si, te cuento que antes de desativar todo puse en apariencia->efectos visuales "normal", que te desactiva unos cuantos (el cubo por ejemplo) pero no todos.

La verdad es que como es "mi puesto de trabajo" tampoco puedo andar haciendo muchas piruetas, me apretaba el tiempo y tenia que hacerla estable si o si. Pero cuando tenga tiempo la que creo que vale la pena probar es dejar compiz activo, pero sin el emerald, creo que puede andar. Prometo que el día que haga la prueba posteo que pasó.

Saludos

---

### Post by alejandro.mc on 2008-04-01
Dale gracias! Suerte!

---

### Post by PatoDB on 2008-04-01
> **alejandro.mc said:**
> Tengo el mismo problema que vos. Esa misma tildada, igual que como la describis. Obviamente tambien estoy usando COmpizDusion a full, todos los efectos, sin placa de video dedicada. Por ende se entiende, pero no me pasa muy seguido de hecho me paso solo 4 veces. 

Si te pasa mas seguido por ahi podrias probar desactivar algunas cosas de CompizFusion, no todo.

Saludos.

Te comento que a mi me paso lo mismo!!

Tambien me tiraba el mismo error... lo hizo 3 o 4 veces, y de repente dejo de hacerlo... 0.0

Pero recuerdo que cuando me tiraba el error ese, tenia ciertos problemas con el Compiz, ya que no podia poner la opcion "Personalizado" en Efectos Visuales. Luego reinstale algunos paquetes que me faltaban del Compiz... Y volvio a la normalidad.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

[COLOR="Red"]EDIT:[/COLOR]

Bastaba que dijera que se habia solucionado, para que me salte el error de nuevo... :P

Busque en el **syslog** y aparecio esto:

> Apr  2 18:20:32 Death gdm[5130]: WARNING: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0 
Apr  2 18:20:34 Death kernel: [13519.152021] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Apr  2 18:20:34 Death kernel: [13519.152052] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Apr  2 18:20:34 Death kernel: [13519.152144] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

Y en **daemon.log** aparecio:

> Apr  2 18:20:32 Death gdm[5130]: WARNING: gdm_slave_xioerror_handler: ha ocurrido un error fatal de X - Reiniciando :0 


Alguna Idea?

---

### Post by Breathe on 2008-06-13
Me ha pasado exactamente lo mismo y lo solucione rapidamente recompilando el driver de nvidia... no hace falta que desinstales todo.
Prueba con el script de la pagina web de nvidia a hacer lo siguiente:

sudo sh NVIDIAxxxxxx.run -K

Con esto solo estaras recompilando el driver... no reinstalando todo... prueba y si no funciona

sudo sh NVIDIAxxxxxx.run --uninstall
sudo sh NVIDIAxxxxxx.run

Recuerda que para poder llevar a cabo esto, antes has debido:

1. Desinstalar todo lo que tenga que ver con nvidia en synaptic (si... todo... algooooo)
2. Desinstalar linux-restricted-modules-xxxxxx
3. Para salir del entorno grafico a modo texto ctrl+alt+f1
4. Parar el servicio de gdm. sudo /etc/init.d/gdm stop
5. Luego haces los pasos arriba indicados... y cuando hayas acabado... reactivas gdm: sudo /etc/init.d/gdm start

Y listo... lo siento por no dar un seguimiento para las ati... pero no
exactamente como se instala... y prefiero no decir tonterias


Microsoft nos da Windows, mientras que Linux nos da TODA LA CASA... XD

---

