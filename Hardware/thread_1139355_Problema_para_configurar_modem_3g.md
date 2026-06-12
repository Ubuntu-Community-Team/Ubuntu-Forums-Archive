---
title: "Problema para configurar modem 3g"
date: 2009-04-27
forum: Hardware
---

### Post by LuisTuc on 2009-04-27
Buenas! les comento mi problema: en la pasada FLISoL 2009 consegui q me instalen Ubuntu (la version 8.04) q era lo q tanto intente hace mucho tiempo, no podia hacerlo por un problema con mi Bios, el APIC, la placa d Video VIA, y tantas otras cosas.
esa misma noche en la Realse Party d Ubuntu 9.04 Jaunty, comentandolo con las persona alli presentes me dicen q no fue lo mas acertado instalarme esa version ya q tiene problemas con las Placas Wi-Fi (*mas con la mia una Realtek rlt8187b*) y con los modems 3g, intentamos incansablemnte instalarme la version 8.10 pero ni siquiera con todas la grandes mentes q c encontraban en la fiesta (y hablo d "[COLOR=DarkOrange]**Ubuntu Gurues**[/COLOR]" jejej!) pudimos instarlo... [SIZE=2][COLOR=Red]_**(nota: nunca c compren una Commodore KE8390MB)**_[/COLOR][/SIZE] asi q bue... me kedo con mi ubuntu 8.04... mi duda es la siguiente:


_ALGUIEN SABE COMO CONFIGURAR UN MODEM 3G HUAWEI E160 PARA PERSONAL??_


desde ya tengan en cuenta q soyyy muyy Novatoide... :P agradecere cualquier ayuda! gracias!




P.D.: La pase muy bien esa noche... la verdad la gente de Ubuntu le pone mucha onda loko!

---

### Post by Ptero-4 on 2009-04-27
Puedes quiza tratar con el recien salido 9.04. Yo también tengo una rtl8187b y desde intrepid esta funciona nativamente (tienes que meter una configuración manual en el /etc/rc.local para que no casque cada dos por tres), y el jaunty funciona incluso mejor (ya no casca, ni necesita esa configuración en el /etc/rc.local).

---

### Post by LuisTuc on 2009-04-27
> **Ptero-4 said:**
> Puedes quiza tratar con el recien salido 9.04. Yo también tengo una rtl8187b y desde intrepid esta funciona nativamente (tienes que meter una configuración manual en el /etc/rc.local para que no casque cada dos por tres), y el jaunty funciona incluso mejor (ya no casca, ni necesita esa configuración en el /etc/rc.local).

Gracias... ya me habian tirado esa solucion, pero esa misma noche tambien intentamos instalarle la 9.04 (estubimos como 1h:30m bajandola) y no pudimos... lo ideal seria intentar hacerlo andar desde la 8.04.


Igualmente muchas gracias!

---

### Post by staar on 2009-04-27
hay un tuto en ubuntu-ar para tu caso: [http://ubuntu-ar.org/node/196]("http://ubuntu-ar.org/node/196"), aunque puede que te parezca medio complicado, mucha consola para alguien nuevo :-P, yo también tengo un modem de estos, y recuerdo que lo que hice en hardy para hacerlo anda fue: ir a Conexiones de Red (así se llama ahora, en hardy creo que era Red, a secas) y crear una nueva conexión ppp (por modem, a mi me figuraba abajo de la cableada), tipo gprs, con los datos que te paso al final, pero recuerdo que tenía el problema de que conectaba pero no podía navegar, por los DNS, que tenían que ser estáticos, algo que sinceramente no recuerdo como resolví, pero primero empezemos por crear la conexión...

los datos que necesita eran, según me acuerdo (o no :-P)...

-Número de telefono: *eldepersonal* (no lo sé)
-Usuario (es igual para todos los clientes): *eldepersonal*
-Contraseña (también): *eldepersonal*
-APN: *eldepersonal*
-DNS 1 (se setean en otra pestaña, ahi mismo en Red): *eldepersonal*
-DNS 2: *eldepersonal*

y creo que nada más, ah, por las dudas, el modem está en /dev/ttyUSB0, NO en /dev/modem (como viene por defecto) ;-)

fijate si con eso te conecta, después vemos lo de los DNS...

ah, para conectarte y desconectarte, tenés que hacerle click al iconito del modem, ahi en Red...

saludos

EDIT: la verdad que sería un golazo hacer andar una versión más nueva en tu máquina, ahora para configurar estas conexiones, hay un asistente, que aparece automáticamente al conectar el modem, con el que tardás menos de diez o cinco segundos (posta, son DOS pasos) en tener andando la conexión...

EDIT2: había puesto todos los datos para claro, y ahora veo que tenés personal :-P , bueno, no importa, conseguite esos datos para tu proveedor, si llamás al servicio técnico te los tienen que dar, sino googlealos ;-) ....

---

### Post by LuisTuc on 2009-04-27
Gracias Staar, la verdad si me dio un poko d miedo al principo.. jeje.. peo bue... intentando la hice andar.... pero me duro poco la alegria ya q... buskando como hacer andar el modem, encontre q la version 8.04 tiene muchos problemas con mi notebook... asi q me decidi a instalarle como sea la version 8.10! y lo logreee! la verdad estoy muyc ontento ahora... apnas lo conecte almoedem comenzo a andar... Un Flashh...

lo mismo muchas gracias.... por la rapidez y por las ganas d ayudar...!!

Ubuntu Rocks! :guitar:

---

### Post by sp33d3rs on 2009-04-27
> **LuisTuc said:**
> Gracias Staar, la verdad si me dio un poko d miedo al principo.. jeje.. peo bue... intentando la hice andar.... pero me duro poco la alegria ya q... buskando como hacer andar el modem, encontre q la version 8.04 tiene muchos problemas con mi notebook... asi q me decidi a instalarle como sea la version 8.10! y lo logreee! la verdad estoy muyc ontento ahora... apnas lo conecte almoedem comenzo a andar... Un Flashh...

lo mismo muchas gracias.... por la rapidez y por las ganas d ayudar...!!

Ubuntu Rocks! :guitar:

Seee, me acuerdo, y concuerdo totalmente con vos, las commodore, tanto pc como notebook siempre traen dolores de cabeza... lo que si, ojo, con windows tampoco me gusta ese modelo de notebook. jajaja

---

### Post by Shilua on 2009-04-27
perdon por el post pero soy nuevo yo tengo en mi pc el ubuntu 8.04 pero por lo que lei en este post solo con instalar el 8.10 y conectar el modem funciona?? o tengo que seguir los pasos que dejo staar

---

### Post by zeroadrenaline on 2009-04-27
UUUUUUUUUUUHHHHHHHHHH Luis, como luchamos con tu commodore.
Bueno, ya que pudiste solucionar, y mejor aun que lo hayas documentado en el foro, mis felicitaciones.

---

### Post by staar on 2009-04-27
> **LuisTuc said:**
> Gracias Staar, la verdad si me dio un poko d miedo al principo.. jeje.. peo bue... intentando la hice andar.... pero me duro poco la alegria ya q... buskando como hacer andar el modem, encontre q la version 8.04 tiene muchos problemas con mi notebook... asi q me decidi a instalarle como sea la version 8.10! y lo logreee! la verdad estoy muyc ontento ahora... apnas lo conecte almoedem comenzo a andar... Un Flashh...

lo mismo muchas gracias.... por la rapidez y por las ganas d ayudar...!!

Ubuntu Rocks! :guitar:

de nada ;-) , me alegro que hayas podido con intrepid...

> **Shilua said:**
> perdon por el post pero soy nuevo yo tengo en mi pc el ubuntu 8.04 pero por lo que lei en este post solo con instalar el 8.10 y conectar el modem funciona?? o tengo que seguir los pasos que dejo staar

a partir de la versión 8.10, ubuntu viene con el network manager 0.7, con esta versión viene ese asistente que nombre, es muy fácil, solo conectar el modem, elegir el proveedor (trae predefinidos un montón, incluyendo los tres de argentina), ponerle nombre a la conexión, y listo, ya esta funcionando...

saludos

---

### Post by faktorqm on 2009-04-28
Luis, como andas? Al igual que como te dije en la release party, lo mejor que podes hacer es, o instalarte 9.04 desde el cd alternate (por que recuerdo que con el live cd tenias problemas, al menos de 8.10) y a partir de ahi te podes leer algo como esto [http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630) que te dice todo. Si no sabes inglés avisame y lo traducimos, total queda para los tutoriales de ubuntu-ar.org :P

Salu2!

---

### Post by Shilua on 2009-04-30
> **staar said:**
> 


a partir de la versión 8.10, ubuntu viene con el network manager 0.7, con esta versión viene ese asistente que nombre, es muy fácil, solo conectar el modem, elegir el proveedor (trae predefinidos un montón, incluyendo los tres de argentina), ponerle nombre a la conexión, y listo, ya esta funcionando...

saludos

muchas gracias ahora solo a instalar el 9.04 que anoche lo deje descargando en el ciber ^^

---

### Post by gually on 2009-07-07
Hola a todos... ):P

Soy muyy nuevo en todo el mundo de linux... 

Primero probe un distro que era el musix pero no le entendia nada no podia configurar mi vga ni mi audio ni el 3g, que es un huawei e160 de claro.... 

Ahora con el ubuntu estudio 9.04 instale todo y segui los pasos que encontre para un modem 3g de la marca ZTE Mf626 que anda rondando por todas partes.... 

Mi gran problema es que hago todas las adaptaciones para el huawei, y al buscar  Sistema -> Preferencias -> Conexiones de Red no encuentro lo que seria Conexiones de red... 

El tuto es para Ubuntu y no se si cambian algunas cosas con el Ubuntu estudio!!! 

Desde ya gracias!!!):P

---

### Post by staar on 2009-07-07
no es necesario que hagas los toqueteos que necesitan los ZTE, en teoría, los huawei andan con solo conectarlos...

creo que en jaunty cambió la traducción para lo que antes era Conexiones de Red, la forma más fácil de acceder a él es haciendo clic derecho en el applet de network-manager del panel (el ícono de las dos pcs) y eligiendo Editar conexiones, en la solapa Banda ancha móvil...

igual, en teoría, al conectar el modem por primera vez te tendría que haber aparecido un asistente para configurar la nueva conexión, permitiendo elegir el proveedor y el nombre de la conexión (no necesita nada más, los datos los tiene, al menos de los 3 proveedores de argentina), con solo seguirlo tendrías que tener la conexión andando...

saludos

---

### Post by gually on 2009-07-09
hola... ya probe de todoooooo.... y en mi practica el modem no me reconoce de una... ni de dos ni nada... pero en el virndows si anda de maravillas, ironico no... y bueno si alguien me puede ayudar para instalar de cero... plissssssssss porque probe incluso con los archivos .deb y cada vez que le daba docle clik a un archivo me pedia que necesitaba otro y tenia que reiniciar para bajar con el xp y asta ahora no me anda nada!!! :confused::confused::confused:

---

### Post by staar on 2009-07-09
con el modem conectado, abrí una Terminal (en Aplicaciones > Accesorios) y corré ```
lsusb
``` pegá la salida acá...

después corré ```
ls /dev/ttyUSB*
``` y también mostranos lo que sale...

saludos

---

### Post by gually on 2009-07-24
buen esto es lo que me muestra


> **staar said:**
> con el modem conectado, abrí una Terminal (en Aplicaciones > Accesorios) y corré ```
lsusb
``` pegá la salida acá...

fwagner@gually:~$ lsusb
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
fwagner@gually:~$ 

después corré ```
ls /dev/ttyUSB*
``` y también mostranos lo que sale...

saludos

fwagner@gually:~$ ls /dev/ttyUSB*
/dev/ttyUSB0  /dev/ttyUSB1
fwagner@gually:~$

---

### Post by staar on 2009-07-24
el modem está reconocido perfectamente, hacé clic derecho en el applet de network-manager del panel (el ícono de las dos pcs, arriba, al lado del reloj) y elegí Editar conexiones, en la solapa Banda ancha móvil creá una nueva conexión y ponele los datos de tu proveedor, una vez que lo hiciste con click normal en el mismo applet elegís la conexión y se conecta, listo...

saludos

---

### Post by gually on 2009-07-27
gracias voy a probar esta noche en casa... :D:D:D

---

### Post by Snyflex on 2009-11-05
Hola!!

Resulta que instale Ubuntu 9.10 Karmic, pero cuando conecto mi Modem Alcatel One Touch xO3O a la pc, lo que hace es que me lo reconoce como si fuera un dispositivo USB.

Ok, hago los Ajustes en el NW, pero no se me conecta ni nada.
Soy nuevo en esto de Ubuntu e Linux, no se nada.
Ayuda porfavor.:p

---

