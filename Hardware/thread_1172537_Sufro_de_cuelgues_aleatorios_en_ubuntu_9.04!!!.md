---
title: "Sufro de cuelgues aleatorios en ubuntu 9.04!!!"
date: 2009-05-28
forum: Hardware
---

### Post by lukastgo on 2009-05-28
La verdad es q esta nueva distribución se ve buena, pero tengo el problema q mi compu se "CUELGA" "PEGA" "NO RESPONDE", y esto ocurre mínimo una vez al día. Sucede al tener activado o desactivado los efectos, y ocurre de manera aleatoria,es decir puede ocurrir mientras estoy en internet o bien cuando el compu esta prendido pero sin uso. 
La verdad es q este problema me esta empezando a molestar pero no logro encontrar la solución. 

Tengo un Proce Quad Core Intel Core 2 Quad 6600, 2400 MHZ
Tarjeta gráfica  ATI SApphire x1650 PRO 512 Mb
2gb RAM
250 GB DD, de los cuales 30 gb usa ubuntu 9.04
ubuntu 9.04  (ext4) (en ext3 tambien se cuelga)
Win xp SP2 (en la otra partición)

Tengo instalado los controladores por default de la ATI, ya q al instalar los de la pag oficial quedo la cag"··$$ y tuve q reinstalar. (ya llevo 4 reinstalaciones).


En un comienzo pensé que era  el típico problema q traen las tarjetas ATI, en términos de soporte, pero pasado el tiempo ninguna a logrado solucionar mi problema. 

Espero nuevas sugerencias ya q soy un novato aún en temas de ubuntu!

---

### Post by moreback on 2009-05-28
Yo tuve problemas de cuelgues con mi notebook y al final llegué a la conclusión que era algo del procesador. La solución era dejarlo en  un modo de energía que no modificara la frecuencia, por ejemplo en **Performance** que mantiene el procesador a lo máximo de frecuencia que da o también **Conservative**, que varía muy poco la frecuencia. En general Ubuntu me dejaba el notebook en modo **OnDemand**, con lo que la frecuencia se modificaba rápidamente y eso a veces hacía que se colgara. Este problema lo tení incluso con el Windows Vista.

Para controlar la frecuencia puse en el panel el applet de **Monitor de frecuencia de la CPU**. y con eso lo fijo a Performance. También habilité el **Laptop-Mode** (/etc/laptop-mode/laptop-mode.conf) y lo configuré pare que me dejara siempre en **Performance**. El **gnome-power-manager** también lo puedes configurar usando el **Editor de configuración** y metiéndote en la clave **/apps/gnome-power-manager/cpufreq/**.

Ojalá te sirva esta información.

Saludos.

---

### Post by lukastgo on 2009-05-29
UFFF soy bastante novato en esto de ubuntu, pero lo que hice fue ir al panel superior, apretar el bot derecho y añadí  el monitor de frecuencia de la CPU, pero no logre llegar a las opciones que tu me dices. Esto no se si es porque mi proce es de 4 nucleos o bien los pasos anteriormente nombrados estan mal.

Al colocarme sobre el icono del panel me dice q "CPU0 Sin soporte para escalado de frecuencia   2,40 GHz (100%)" 

esto es como la modificación de overclock q se hace en win o nada q ver?

---

### Post by moreback on 2009-05-30
Lo que dice es que no tiene soporte para cambiarte la frecuencia en tus procesadores y que están al 100%.

U sea que ese nu es el problemuuuuu. AHora me inclino por tu tarjeta de video.

---

### Post by lukastgo on 2009-05-30
Si es la tarjeta de video uffff no se que hacer, ya que antes traté de instalar los drivers de la pag oficial de ATI pero al reiniciar y luego del logo de ubuntu y antes de llegar al escritorio (o tal vez estando en el) la pantalla se transforma en miles de colores, sin lograr distinguir nada. Traté de entrar desde el livcd pero no logré modificar y quitar el drivers de ATI, por lo q no me quedo más que reinstalar! (ya llevo 4)

En el buscardor de synaptic coloco ATI, para así saber q es lo q tengo instalado y aparecen:
 -xserver-org-video-ati
-xserver-xorg-video-radeon
-redeontool
-xserver-xorg-video-mach64
-xserver-xorg-video-r128
-fglrx-modaliases
-jockey-gtk
-jockey-common


Te agradezco las sugerencias q me estas dando, y si necesitas algún dato adicional para así solucionar mi problema te lo entrego con gusto.

---

### Post by Carlos C on 2009-05-30
que te muestra si escribes en el terminal "lspci"? Tengo curiosidad por saber si algo puede resultar conflictivo a demás de la tarjeta de video. ¿Usas compiz?

Yo también tengo una ATI (claro que no la misma, lo que es importante) y uso los drivers que vienen por defecto en jaunty. Por primera vez no tengo que instalar los privativos y la verdad es que funciona bastante bien.
Saludos.

---

### Post by lukastgo on 2009-05-30
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Radeon X1650 Pro (Secondary) (rev 9e)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

 y tengo los efectos en extra!, saludos y espero me puedas ayudar
pd: con efectos nulo, normal o extras igual se pega

---

### Post by Carlos C on 2009-05-30
Bueno, descarta cosas, lamentablemente es difícil saber que puede ser con los pocos datos que tienes. En tu caso haría un test de la memoria ram, porque si la memoria ram está defectuosa es normal que estas cosas pasen. En el menú de inicio del LiveCD, según recuerdo, hay una opción para verificar tu memoria ram.

---

### Post by AlvaroV on 2009-05-31
Es interesante este tema porque yo tambien instale la 9.04 y comence a tener cuelgues, que antes no me ocurrrían con otras versiones. Y fue tan así que decidi volver a la 8.04 que no tiene esos problemas. Sería bueno tratar de saber que ocurre ya que como he leído en Internet el tema de los cuelgues de la 9.04 es recurrente.

---

### Post by mcisternas on 2009-05-31
> **AlvaroV said:**
> Es interesante este tema porque yo tambien instale la 9.04 y comence a tener cuelgues, que antes no me ocurrrían con otras versiones. Y fue tan así que decidi volver a la 8.04 que no tiene esos problemas. Sería bueno tratar de saber que ocurre ya que como he leído en Internet el tema de los cuelgues de la 9.04 es recurrente.

Yo empecé a sufrir esos cuelgues extraños en Intrepid Ibex 8.10. Tal versión duró como dos semanas en mi laptop porque ya no me dejaba trabajar con la estabilidad que me daba Hardy Heron. 

Por tal problema, tuve que volver a Hardy hace ya unos seis meses mas o menos pues en esa versión no hay dramas.

---

### Post by lukastgo on 2009-05-31
realice el Memtest 86+ que viene como una opción de inicio y no encontró ningún problema en las memorias. Este mismo test lo realice desde el livcd y tampoco encontro nada.

No se si esto bastara para desestimar que sean las memorias el problema. Espero más sugerencias!

---

### Post by guillermolisi on 2009-06-02
Usaste esa misma maquina con otros sistemas operativos sin problemas, sin cuelgues ?
Si fue asi, cuanto hace de ello ?

---

### Post by lukastgo on 2009-06-02
El disco duro de 250 Gb lo tengo paricionado en:
220 Gb para windows XP SP2 (hoy lo uso sin problemas)
30 GB para ubuntu 9.04 (con el respectivo problema de los cuelgues)

En Ubuntu 9.04 sufro cuelgues aleatorios desde la primera instalación (ya llevo 4) y todas han sido instalaciones limpias (formateando todas las particiones en los 30 GB que dejo pa linux).

pd: Comencé instalando Debian pero lo desinstale debido a que no me reconocía de manera automática la wifi, cosa que si hacia ubuntu 9.04

---

### Post by guillermolisi on 2009-06-02
> **lukastgo said:**
> El disco duro de 250 Gb lo tengo paricionado en:
220 Gb para windows XP SP2 (hoy lo uso sin problemas)
30 GB para ubuntu 9.04 (con el respectivo problema de los cuelgues)

En Ubuntu 9.04 sufro cuelgues aleatorios desde la primera instalación (ya llevo 4) y todas han sido instalaciones limpias (formateando todas las particiones en los 30 GB que dejo pa linux).

pd: Comencé instalando Debian pero lo desinstale debido a que no me reconocía de manera automática la wifi, cosa que si hacia ubuntu 9.04
Ok. Entonces, si con WinXP la maquina se comporta adecuadamente, el problema no pasa por el hardware sino por algun driver (y ahi la cosa se pone mas dificil de determinar).

Es una desktop o una notebook ?
Si es el primer caso, que motherboard es ?
Que chipset trae ?

No vendra la cosa por el lado del driver para ACPI ?

---

### Post by lukastgo on 2009-06-02
-desktop
-placa madre [MSI p35 neo]("http://latam.msi.com/spanish/products/detail_spec/P35_Neo_spa.htm")

eso del ACPI no entendí como verlo.

Vale por la ayuda y sigo pendiente con las recomendaciones

---

### Post by guillermolisi on 2009-06-02
> **lukastgo said:**
> -desktop
-placa madre [MSI p35 neo]("http://latam.msi.com/spanish/products/detail_spec/P35_Neo_spa.htm")

eso del ACPI no entendí como verlo.

Vale por la ayuda y sigo pendiente con las recomendaciones
Te paso lo primero que salio cuando puse ACPI en Google, [un articulo de Wikipedia.]("http://es.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface")

Como dice en la nota, algunos sistemas operativos usan esta facilidad para "saber" que tipo de hardware posee la maquina y a veces funciona bien y otras no, dependiendo de como esta implementada en el chipset (fijate que hay una referencia a una nota donde alguien habla sobre Foxconn y su BIOS respecto de este tema del ACPI).

Si el SO no puede leer adecuadamente la informacion que necesita para conocer que componentes posee la maquina, pueden surgir problemas desde la imposibilidad de iniciar (booting) hasta el mal o ningun reconocimiento de un dispositivo.

---

### Post by lukastgo on 2009-06-02
mmmmmmmmmmm como sale en wiki este es un problema q no se puede asegurar con certeza,a sí q mejor dejemoslo como ultima ultima y utlima opción jejejej. 
Pero como se si tengo instalado los drivers impresindibles para que el SO funcione bien?.

dale q sigo atento..

---

### Post by guillermolisi on 2009-06-02
> **lukastgo said:**
> mmmmmmmmmmm como sale en wiki este es un problema q no se puede asegurar con certeza,a sí q mejor dejemoslo como ultima ultima y utlima opción jejejej. 
Pero como se si tengo instalado los drivers impresindibles para que el SO funcione bien?.

dale q sigo atento..
Te vas a dar cuenta que te falta algun driver cuando un dispositivo no funcione en absoluto.
Te vas a dar cuenta que un driver no es el apropiado para un dispositivo cuando este funcione defectuosamente.

Normalmente la distribucion contempla una amplia gama de drivers, necesarios y suficientes como para asegurar funcionamiento operativo en muchas plataformas de hardware siempre que sus fabricantes faciliten informacion sobre sus dispositivos.

Aquellos componentes cuyos fabricantes no facilitan informacion para que se desarrollen driver abiertos, caso nVidia por ejemplo, requeriran que los drivers los provea quien fabrica el hardware.

Los drivers abiertos se incluyen, normalmente, en el kernel.
Los propietarios/cerrados van como modulos, al igual que algun driver abierto no incluido en el kernel.

---

### Post by lukastgo on 2009-06-03
Pero como te comente sufro de cuelgues aleatorios, por lo q no he logrado determinar q es lo q falla.
-Estando o no conectado a la wifi falla.
-Si el compu esta prndido pero sin uso también falla.


MMMMMM pero una situación en la cual ** "siempre pero siempre falla"** es cuando realizo auditorías wireless,es decir utilizando el aircrak. 
O bien se cae cuando inyecto trafico con el aireplay. 

Esto no demanda gran trabajo del procesador, pero no pasan ni 5 minutos y se cae SIEMPRE (o mejor dicho el compu se pega o cuelga completamente) debiendo reiniciar a la mala, es decir apretando el reset.

Ahí si q te pille con saber cual es el problema. Ya que ni idea q recursos son los q utiliza el aircrack.

---

### Post by guillermolisi on 2009-06-03
> **lukastgo said:**
> Pero como te comente sufro de cuelgues aleatorios, por lo q no he logrado determinar q es lo q falla.
-Estando o no conectado a la wifi falla.
-Si el compu esta prndido pero sin uso también falla.


MMMMMM pero una situación en la cual ** "siempre pero siempre falla"** es cuando realizo auditorías wireless,es decir utilizando el aircrak. 
O bien se cae cuando inyecto trafico con el aireplay. 

Esto no demanda gran trabajo del procesador, pero no pasan ni 5 minutos y se cae SIEMPRE (o mejor dicho el compu se pega o cuelga completamente) debiendo reiniciar a la mala, es decir apretando el reset.

Ahí si q te pille con saber cual es el problema. Ya que ni idea q recursos son los q utiliza el aircrack.
Aircrack utiliza el driver de la placa WiFi, paquetes TCP/IP, y alguna que otra cosa que se me esta pasando por alto.

Podes probar de dejar la PC funcionando con la placa WiFi deshabilitada/apagada ?

Me parece que un procedimiento de descarte seria lo mas apropiado para este caso.

---

### Post by lukastgo on 2009-06-03
MMMM puede ser ya que a veces cuando prendo el compu y luego de pedirme la clave de autenticación para entrara a la wifi también se cuelga. Bueno seguiré tu consejo hoy y te cuento q es lo q pasa. 

Te cuento q mi tarjeta PCI wireless es una [TP-Link (TL-WN651G) ]("http://www.tp-link.com/products/product_des.asp?id=17")

---

### Post by moreback on 2009-06-04
No sé si será el mismo problema pero no pierdes mucho probando la solución que dan acá [http://foros.ubuntu-cl.org/viewtopic.php?t=5869](http://foros.ubuntu-cl.org/viewtopic.php?t=5869) (pagondel)

---

### Post by lukastgo on 2009-06-05
moreback gracias por responder! mmmmm si revise ese foro, pero el problema q como soy bastante novato en ubuntu no quise aplicar esos comandos por miedo de mandarme alguna cag,,,,.

Sobre el tema de q el kernel ahorraba trabajo de la CPU, y este se activa mediante la demanda, me parece q        guillermolisi me dijo q mi porcesador esta siempre trabajando al 100%. Esto debido a que no podía variar la frecuencia de trabajo.


      guillermolisi q opinas sobre la solución presente en el foro que moreback gentilmente me invita a revisar?

Saludos y sigo atento al foro


pd: no aplico "aún" esta solución pq era para problemas en versiones anteriores, y como me inicie con 9.04  no se si hubiese tenido el mismo problema q sufro ahora.

MMMMM y si bajo la versión de 8.04 (32bit) y la pruebo con el aircrack? (ya q los cuelges con este programa son seguros). Tal vez podría saber si el problema ya estaba presente en versiones anteriores o es algo de la 9.04.    (todo esto desde el livcd!! eso si)

q opinan?

---

### Post by guillermolisi on 2009-06-06
> **lukastgo said:**
> moreback gracias por responder! mmmmm si revise ese foro, pero el problema q como soy bastante novato en ubuntu no quise aplicar esos comandos por miedo de mandarme alguna cag,,,,.

Sobre el tema de q el kernel ahorraba trabajo de la CPU, y este se activa mediante la demanda, me parece q        guillermolisi me dijo q mi porcesador esta siempre trabajando al 100%. Esto debido a que no podía variar la frecuencia de trabajo.


      guillermolisi q opinas sobre la solución presente en el foro que moreback gentilmente me invita a revisar?

Saludos y sigo atento al foro


pd: no aplico "aún" esta solución pq era para problemas en versiones anteriores, y como me inicie con 9.04  no se si hubiese tenido el mismo problema q sufro ahora.

MMMMM y si bajo la versión de 8.04 (32bit) y la pruebo con el aircrack? (ya q los cuelges con este programa son seguros). Tal vez podría saber si el problema ya estaba presente en versiones anteriores o es algo de la 9.04.    (todo esto desde el livcd!! eso si)

q opinan?
No recuerdo haber mencionado algo sobre la CPU de tu maquina, pero de todas formas me parece que con probar esa solucion aconsejada, que figura en el foro anterior, no perdes nada. Para probar usaria la modificacion mas volatil, la que se expone al principio y que se pierde al cambiar el kernel.

Si funciona todo bien, entonces implementaria la solucion que se aconseja despues, asi te olvidas de las actualizaciones del kernel.

Todo esto seria valido mientras este comportamiento con la funcion tickless exista. Luego, resuelto el tema definitvamente en el kernel o en el hardware, no haria mas falta.

Otra prueba que podes hacer (que me parece prioritaria respecto de la solucion en el Grub, y que ya mencione), para descartar si es o no algo relacionado con la interface de red WiFi, es deshabilitarla (electricamente hablando - si fuera necesario retirarla de la PC) y trabajar via red cableada, observar que pasa y sacar conclusiones despues.

---

### Post by lukastgo on 2009-06-06
mmmmmmm el tema de sacar la tarjeta sería un poco más complicada ya q le señal me llega por wifi. Solución para aquello seria hacer un "puente" entre:
un Pc viejo q tengo =>un Acces point (para tomar la wifi)=> y luego pasar al compu q me da problema mediante cable. 

Bueno aplicare la la sugerencia de moreback y vere q pasa al usar el aircrak (problema de cuelgue al 100%)

[SIZE=5]vale nuevamente por todas las sugerencias![/SIZE]

---

### Post by Patriciologico on 2009-06-07
Lo que guillermolisi recomienda al retirar la tarjeta, es algo transitorio, para poder enfocar mejor el problema.

---

### Post by Carlos C on 2009-06-07
> **Patriciologico said:**
> Lo que guillermolisi recomienda al retirar la tarjeta, es algo transitorio, para poder enfocar mejor el problema.
Así es, también estoy de acuerdo con que debe probar lo que se le sugiere. La idea es que se pruebe el equipo sin tener conexión wifi trabajando. Si no ocurre un cuelgue del sistema entonces el problema claramente va por ese lado.

En mi caso también tuve ese problema en Hardy y efectivamente era un problema de mi conexión wifi, de hecho lo comenté en el foro anterior en ese mismo hilo.

---

### Post by lukastgo on 2009-06-09
realice el cambio de nohz=off y los cuelgues continuan. Tanto al usar Aircrack como al realizar descargas, probaré la segunda opción (retirar la tarjeta wifi) y ver como funciona el compu.


pd: PFFFFFFFFF la wifi la recibiré desde el AP y este la llevará al compu mediante el cable de red, para ver como funciona la wifi. 
El problema es q no podre utilizar el aircrack (el cual me daba el 100 % de cuelgues).

---

### Post by lukastgo on 2009-06-09
> **Carlos C said:**
> Así es, también estoy de acuerdo con que debe probar lo que se le sugiere. La idea es que se pruebe el equipo sin tener conexión wifi trabajando. Si no ocurre un cuelgue del sistema entonces el problema claramente va por ese lado.

En mi caso también tuve ese problema en Hardy y efectivamente era un problema de mi conexión wifi, de hecho lo comenté en el foro anterior en ese mismo hilo.


busque tu tema pero lo lo encontré, me tirarías el link?

---

### Post by Carlos C on 2009-06-09
Me refería al enlace que dio moreback y donde yo había dado la solución que a mí me resultó:
> **moreback said:**
> No sé si será el mismo problema pero no pierdes mucho probando la solución que dan acá [http://foros.ubuntu-cl.org/viewtopic.php?t=5869](http://foros.ubuntu-cl.org/viewtopic.php?t=5869) (pagondel)

Simplemente instalé Wicd. Lo encuentras en los repositorios.
Saludos.

---

### Post by lukastgo on 2009-06-09
instale el wicd, haré algunas pruebas y veré q pasa con los cuelgues.

---

### Post by lukastgo on 2009-06-10
> **lukastgo said:**
> instale el wicd, haré algunas pruebas y veré q pasa con los cuelgues.



edito: Continúan los cuelgues, aun cuando tengo instalado ahora el wicd (en reemplazo del network-manager). Un tema que me dejo intrigado es q en un momento tuve el compu sin ninguno de los 2 programas, anteriormente nombrados, y probe usar el aircrack obteniendo como resultado nuevamente cuelgues. Por lo que no sería un problema de programas de red, sino más bien uno referente a mi tarjeta wifi TP-LINK WN651G (con chipset Atheros).


Buscando en el gestor de paquetes Synaptic algo referente al chipset encontré esto, pero estan "DESmarcados" 
- atl2-source /Controlador base Linux para el adaptador Atheros(R) L2 Fast Ethernet
-madwifi-tools /tools for the Multiband Atheros Driver for WiFi
-hostapd /user space IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator

Como puedo saber si tengo los controladores q la tarjeta atheros necesita?

Saludos!


pd: volví a instalar el Network-manager ya q el wicd es demasiado lento en conectar (y a veces sin buenos resultados)

---

### Post by Carlos C on 2009-06-11
Las tarjetas Atheros AR5001X se detectan automáticamente, por lo que no debieras tener problemas con eso. Si vas a Sistema-->Controlador de hardware ¿dice que está habilitada?

---

### Post by lukastgo on 2009-06-11
pffff no pude subir la imagen pero aca __esta la respuesta a lo que preguntas



pd: jejej ahora sí esta la imagen!   (mmm q pasa si los activo?)

---

### Post by Carlos C on 2009-06-12
mmm no se ve nada. Por favor adjunta un enlace a algún sitio donde subas la imagen, como imageshack.

---

### Post by lukastgo on 2009-06-12
[[IMG]http://s3.subirimagenes.com:81/imagen/previo/thump_2713873pantallazo1.png[/IMG]]("http://www.subirimagenes.com/imagen-pantallazo1-2713873.html")

waaaaaaaaaa hace 1 día atrás estaba la imagen  :( , bueno acá esta de nuevo

---

### Post by Carlos C on 2009-06-13
Bueno, en vista de que tienes problemas podrías probar activando el driver privativo y ver si con eso cesan los cuelgues. En caso de que no sea así te sugiero regresar al driver libre.

---

### Post by lukastgo on 2009-06-17
con los drivers de madwifi se mantienen los cuelgues, volvi a los libres pero se producen cuelgues al inicio (luego de q se carga el escritorio), no he podido hacer un update pq no logro conectar a wifi de manera constante (y solo he estado usando win en estos momentos). Estoy esperando realizar lo anterior y ver si los cuelgues disminuyen en algo. MMMMMm raro :(
 
 
 
pd: un hecho q me intrigo es la imposibilidad q tuve de colocar mi tarjeta en modo monitor (en un comienzo), pero ahora volvio a la normalidad. Y no hice nada extraño.
 
"sudo airmon-ng start wlan0"

---

### Post by lukastgo on 2009-06-18
> **lukastgo said:**
> con los drivers de madwifi se mantienen los cuelgues, volvi a los libres pero se producen cuelgues al inicio (luego de q se carga el escritorio), no he podido hacer un update pq no logro conectar a wifi de manera constante (y solo he estado usando win en estos momentos). Estoy esperando realizar lo anterior y ver si los cuelgues disminuyen en algo. MMMMMm raro :(
 
 
 
pd: un hecho q me intrigo es la imposibilidad q tuve de colocar mi tarjeta en modo monitor (en un comienzo), pero ahora volvio a la normalidad. Y no hice nada extraño.
 
"sudo airmon-ng start wlan0" (comando q antes no funcionaba)

---

### Post by xangelux on 2009-06-21
Pues miren, los cuelgues empezaron, como alguien mensionó por ahí, en el 8.10 y continuaron desde entonces, esto es debido al soporte de los drivers Madwifi. Cuando a mi me presentó este problema, usé el conky para que me mostrara los procesos que mas tomaban de mi procesador en todo momento, lo que descubrí es que al momento del cuelgue madwifi subia a un 80%-90% del uso del procesador dejando al sistema paralizado, esperando lo suficiente, esto volvía a bajar y continuaba mi trabajo. Esto pasaba frecuentemente por lo que mi conclusion es que madwifi tiene por ahí un procesillo oculto para monitorear algo, ya sea señales o algún proceso o variable. No soy tan experto como para poder escudriñar todo esto, así que tomé la decisión de compilar mi propio madwifi. De este sitio [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) entren a la carpeta del madwifi-hal mas reciente en el momento (ATENCION: no es madwifi si no madwifi-hal), descarguen el tar.gz más nuevo (el de la fecha más reciente) guardenlo en donde no lo vayan a mover (Se necesitará cada vez que actualizen su kernel, yo hice una carpeta especial para los paquetes que compilo) una vez ahí hagan 

$ tar -zxvvf madwifi-halxxxxxxx.tar.gz  #(Donde xxxxxx es la versión)
$ cd madwifi-halxxxxxxx
$ make
$ make install
$ sudo modprobe ath_pci
$ sudo gedit /etc/modules 

Este último comando abrirá el archivo de modulos que se cargan al iniciar el sistema por lo que añadimos el que acabamos de compilar al final del archivo poniendo

# Modulo o driver madwifi
ath_pci

Listo, ya tenemos funcionando madwifi sin cuelgues. Ahora, cada vez que actualicen su kernel antes de reiniciar despues de actualizar su kernel, dirijanse mediante consola a su directorio donde guardaron los archivos de madwifi y tecleen:

$ cd madwifi-halxxxxxxx
$ sudo make uninstall
$ sudo make clean

Reinician su computadora, van a consola de nuevo al mismo lugar y repiten

$ cd madwifi-halxxxxxxxx
$ make
$ sudo make install

Y es todo, si a alguien le interesa pueden mantenerse monitoreando el sitio que puse arriba para actualizar su descarga del modulo y mantenerse al día, el proceso es el mismo.

Espero que les haya servido, Saludos.

---

### Post by AlvaroV on 2009-06-21
Yo también en su momento huí de la 9.04 por los cuelgues, sin embargo ahora regrese, eso sí hice algo distinto y los cuelgues por el momento no han vuelto. Instale desde cero y aumente la partición swap de 1700 +/- que es lo que da Ubuntu por defecto a casi 4 megas. Quizás podría tener que ver.

---

### Post by lukastgo on 2009-06-22
> **xangelux said:**
> Pues miren, los cuelgues empezaron, como alguien mensionó por ahí, en el 8.10 y continuaron desde entonces, esto es debido al soporte de los drivers Madwifi. Cuando a mi me presentó este problema, usé el conky para que me mostrara los procesos que mas tomaban de mi procesador en todo momento, lo que descubrí es que al momento del cuelgue madwifi subia a un 80%-90% del uso del procesador dejando al sistema paralizado, esperando lo suficiente, esto volvía a bajar y continuaba mi trabajo. Esto pasaba frecuentemente por lo que mi conclusion es que madwifi tiene por ahí un procesillo oculto para monitorear algo, ya sea señales o algún proceso o variable. No soy tan experto como para poder escudriñar todo esto, así que tomé la decisión de compilar mi propio madwifi. De este sitio [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) entren a la carpeta del madwifi-hal mas reciente en el momento (ATENCION: no es madwifi si no madwifi-hal), descarguen el tar.gz más nuevo (el de la fecha más reciente) guardenlo en donde no lo vayan a mover (Se necesitará cada vez que actualizen su kernel, yo hice una carpeta especial para los paquetes que compilo) una vez ahí hagan 

$ tar -zxvvf madwifi-halxxxxxxx.tar.gz  #(Donde xxxxxx es la versión)
$ cd madwifi-halxxxxxxx
$ make
$ make install
$ sudo modprobe ath_pci
$ sudo gedit /etc/modules 

Este último comando abrirá el archivo de modulos que se cargan al iniciar el sistema por lo que añadimos el que acabamos de compilar al final del archivo poniendo

# Modulo o driver madwifi
ath_pci

Listo, ya tenemos funcionando madwifi sin cuelgues. Ahora, cada vez que actualicen su kernel antes de reiniciar despues de actualizar su kernel, dirijanse mediante consola a su directorio donde guardaron los archivos de madwifi y tecleen:

$ cd madwifi-halxxxxxxx
$ sudo make uninstall
$ sudo make clean

Reinician su computadora, van a consola de nuevo al mismo lugar y repiten

$ cd madwifi-halxxxxxxxx
$ make
$ sudo make install

Y es todo, si a alguien le interesa pueden mantenerse monitoreando el sitio que puse arriba para actualizar su descarga del modulo y mantenerse al día, el proceso es el mismo.

Espero que les haya servido, Saludos.




MUCHAs gracias por responder a mi problema, ahora intentaré tu solución a ver q pasa.

---

### Post by lukastgo on 2009-06-22
> **AlvaroV said:**
> Yo también en su momento huí de la 9.04 por los cuelgues, sin embargo ahora regrese, eso sí hice algo distinto y los cuelgues por el momento no han vuelto. Instale desde cero y aumente la partición swap de 1700 +/- que es lo que da Ubuntu por defecto a casi 4 megas. Quizás podría tener que ver.



mira así disttribuí mis 30 Gb para ubuntu 9.04:

-boot ext4 200 Mb
-/ ext4 15 Gb
-/home ext4 12 Gb
-swap 2 Gb    ===> sobre este punto aún lo consideras insuficiente, si es así le aumento lo q estimes conveniente para hacer las pruebas.



Y nuevamente gracias por responder!!!



edito 2 minutos después: luego de los cambios de drivers privativos a no privativos (no se si por esa causa), el periódo de cuelgues va en aumento, ya que ahora casi no alcanzo a conectar a una red cuando ya sufro de cuelgues. Otro punto q me tiene complicado es q me dejo de funcionar el synaptic ya q me marca un error (q en estos momentos no me acuerdo) y solo logro actualizar mediante sudo apt-get update  ==>donde también me marca un error (con un repositorio me parece, pero luego les confirmaré aquella duda).

---

### Post by lukastgo on 2009-06-22
[SIZE=5]**[B]xangelux**[/B][/SIZE]===> ya hice tu recomendación sin problema, ahora haré algunas pruebas a ver q pasa con los cuelgues. 


perdón por re postear pero este es el problema q me da_[COLOR=SeaGreen]** synaptic**[/COLOR]_


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/cl.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.
E: _cache->open() failed, please report.



Con el _[COLOR=SeaGreen]**gestor de actualizaciones **[/COLOR]_me tira este error en pantalla:


No se ha podido inicializar la información de los paquetes

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/cl.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'


con el comando [COLOR=Green]_**sudo apt-get update**_[/COLOR] me da este error:

Leyendo lista de paquetes... ¡Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/cl.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado

y no cacho mucho de q se tratan todos estos problema.

---

### Post by Carlos C on 2009-06-22
Creo que estamos frente a otro problema. Compilando madwifi, ¿conseguiste solucionar lo de los cuelgues? Si es así por favor abre otro hilo para tratar este problema nuevo.
Saludos.

---

### Post by lukastgo on 2009-06-26
mmm sufrí un cuelgue pero me parece q en este punto hice mal el proceso ya q copie textual esta instrucción 


**# Modulo o driver madwifi   ===>**copio esto así o debo colocar el q yo baje ?
** ath_pci**




mmmm quede con la duda:confused:



edito: así lo deje 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
# Modulo o driver madwifi
ath_pci



siendo las dos ultimas lineas las q agregue, pero ese "o" es el q me provoco la duda.

---

### Post by lukastgo on 2009-06-26
> **lukastgo said:**
> [SIZE=5]**[B]xangelux**[/B][/SIZE]===> ya hice tu recomendación sin problema, ahora haré algunas pruebas a ver q pasa con los cuelgues. 


perdón por re postear pero este es el problema q me da_[COLOR=SeaGreen]** synaptic**[/COLOR]_


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/cl.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.
E: _cache->open() failed, please report.



Con el _[COLOR=SeaGreen]**gestor de actualizaciones **[/COLOR]_me tira este error en pantalla:


No se ha podido inicializar la información de los paquetes

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/cl.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'


con el comando [COLOR=Green]_**sudo apt-get update**_[/COLOR] me da este error:

Leyendo lista de paquetes... ¡Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/cl.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado

y no cacho mucho de q se tratan todos estos problema.



**[SIZE=6]edito 26/06/09: [/SIZE]**solucione este problema de synaptic mediante este comando en consola:

**sudo rm /var/lib/apt/lists/* -vf**
 **sudo apt-get update**




[B]Y comenzó de una la actualización, sobre los cuelgues estoy en periodo de pruebas (pero con la duda q les plantee en el post # 46)
[/B]

---

