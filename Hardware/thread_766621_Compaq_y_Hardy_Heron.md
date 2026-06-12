---
title: "Compaq y Hardy Heron"
date: 2008-04-25
forum: Hardware
---

### Post by Apipote on 2008-04-25
Hola a todos.

Ruego que si alguien pudo instalar exitosamente hardy en alguna compaq ( yo tengo la f566 ), con wireless funcionando, lo postee por favor.

Gracias.

---

### Post by niko_3100 on 2008-04-25
Yo tengo la v3415la pero que error te tira? Pudiste instalarlo por lo menos pero sin WIFI? o directamente no te levanta el liveCD?

---

### Post by Apipote on 2008-04-25
Lo estoy bajando aún...veremos.

Sin embargo con Gutsy fue de terror...errores por todos lados, con nvidia, acpi, y la maldita broadcom de porquería nunca anduvo con los drivers de ubuntu.

A vos te anda todo bien ahora con Hardy ??

En fin...bad time good face :)
Slds

---

### Post by alejandro.mc on 2008-04-26
Instalé en una F506LA y esta andando todo al pelo. Muy contento por ahora, todo esta muy lindo!

Suerte!

---

### Post by niko_3100 on 2008-04-26
pero lo tenes instalado con wifi?? porque a mi me levanto todo pero no el wifi.

---

### Post by Apipote on 2008-04-26
Ale...
Tenes wifi ???
Y de ser así...como hiciste ???
Que Hardy instalaste 32 o 64 ??
Gracias

---

### Post by lambres on 2008-04-27
Tengo Hardy Heron, y no levanta la placa wifi.
My notebook es Compaq Presario F566LA y mi hardware es:
dario@presario-dario:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

instalé los drivers con ndiswrapper el cual me tira:
dario@presario-dario:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
Que veo que me devuelve alternate driver: ssb cuando debería deciir bcmxx cuando lo habia instalado en 7.10.
Si alguien me puede ayudar se los voy a agradecer.

en las notas de liberación dice lo siguiente:
Route metrics

ifupdown ahora configura el "route metric" por defecto a 100 para interfaces sin opción métrica configurada en /etc/network/interfaces. Estos cambios no suponen ninguna diferencia pra la mayoría de usuarios pero puede afectar a unos cuantos usuarios con requerimientos de red complejos. Si dependes de la anterior métrica de ruta por defecto de 0 (cero) edita /etc/network/interfaces y configura la opción "metric" explícitamente en tu interfaz:

iface eth0 inet static
       address 192.168.0.2
       network 192.168.0.0
       broadcast 192.168.0.255
       netmask 255.255.255.0
       gateway 192.168.0.1
       metric 0


[editar] Network Manager

En Ubuntu 8.04, network-manager sólo gestiona interfaces marcadas para itinerancia. Por lo tanto, todas las interfaces que se gestionaban anteriormente con network-manager serán configuradas en modo itinerante durante la actualización. Técnicamente, esto toma cualquier interfaz usando el método dhcp sin opciones, éstas se marcan automáticamente, y las elimina de /etc/network/interfaces. Si necesitas que tu interfaz sea iniciada por ifupdown cuando se inicie el sistema, necesitas re-habilitarla en /etc/network/interfaces manualmente o deshabilitar la itinerancia en Sistema -> Administración -> Red. 

No se si ayuda en algo

gracias

---

### Post by Apipote on 2008-04-27
Tengo la misma laptot Lambres...
Me quede hasta las 03 am, y no pude hacerla funcionar. Dicen que en algunas broadcom el fcutter funca bien, en mi 4311rev2...no

Lo gracioso es que la placa se ve...solo que no funciona, no aparece en "drivers propietarios".
Algo del blacklist?...seguire experimentando. Creo que existe una solución "sin ndiswrapper".

Voy a probar ahora con las versiones de 64 bits ( me **** no tener flash player...pero bueno )

Nos vemos

---

### Post by lambres on 2008-04-27
Bueno, al fin lo logré, seguí este tuto y funcionó.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Es causado por un bug en como carga el modulo.

gracias igual y espero que les sirva.

---

### Post by Apipote on 2008-04-27
Bueno...no hay caso. 
La broadcom 4311 rev 2 de mi f566 sigue peleada con los drivers nativos de Ubuntu Hardy. 
Fcutter, no funciona para nada.
Hasta la próxima versión...
Gracias.

---

### Post by niko_3100 on 2008-04-28
Pero lambres solo hiciste eso? lo que dice de la ultima parte del hardy y ndiswrapper?? y te funco? espero que me ande hoy cuando llego a mi casa lo pruebo, es una pena tener una notebook router wifi ubuntu 8.04 pero no tener la placa bien instalada.

---

### Post by lambres on 2008-04-28
> **niko_3100 said:**
> Pero lambres solo hiciste eso? lo que dice de la ultima parte del hardy y ndiswrapper?? y te funco? espero que me ande hoy cuando llego a mi casa lo pruebo, es una pena tener una notebook router wifi ubuntu 8.04 pero no tener la placa bien instalada.

si, tenes que hacer lo que dice del bug de hurdy, con eso funciono en mi presario f566la.
Contame como te fue.

lambres

---

### Post by clodo on 2008-04-28
Como va, proba ejecutar esto en este orden:

sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

---

### Post by niko_3100 on 2008-04-29
Si con eso me levanto joya, pero cuando tiraba sudo rmmod b43 o b44 o b43legacy me decia que no existia el modulo en /proc/modules... no le di bola y segui siguiendo el tuto y me levanto la placa wifi pero como dice ahi cada ves que reinicio tengo que hacer los comandos de nuevo. Como haria para que me lo levanto en el arranque? un script con sos 3 comandos y lo meto en init.d??

---

### Post by Mister X on 2008-04-29
> **niko_3100 said:**
> Si con eso me levanto joya, pero cuando tiraba sudo rmmod b43 o b44 o b43legacy me decia que no existia el modulo en /proc/modules... no le di bola y segui siguiendo el tuto y me levanto la placa wifi pero como dice ahi cada ves que reinicio tengo que hacer los comandos de nuevo. Como haria para que me lo levanto en el arranque? un script con sos 3 comandos y lo meto en init.d??

tenes que agregar los modulos que no queres cargar al inicio en /etc/modprobe.d/blacklist

y agregar los modulos que si queres cargar al inicio en /etc/modules

---

### Post by niko_3100 on 2008-04-29
Mira aca te dejo mi blacklist

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

aca agregaria ssb??





Y ACA MI /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp


ahi agregaria ndiswrapper?? Que pocos modulos que carga...

---

### Post by Apipote on 2008-04-29
Bueno, a quienes no nos gusta ndiswrapper con drivers de windows:

He leído en [www.kernel.org](www.kernel.org) , la próx versión 2.6.25 soporta la broadcom 4311 rev 2. O sea la que tienen algunas Compaq.
Esperemos a "Intrepid" a ver que pasa, porque salvo esta maldita placa, Hardy me levanta todo sin problemas. 

Al margen...me parece que en esta máquina de 64 bits, Hardy 64 bits anda mejor.

Slds

---

### Post by niko_3100 on 2008-04-29
Bueno yo ya pude solucionar lo del wifi, pero a alguno le reconoce los comandos para variar el brillo? Es decir FN +F7 y Fn + F8 ?? A mi no

---

### Post by lambres on 2008-04-29
> **niko_3100 said:**
> Bueno yo ya pude solucionar lo del wifi, pero a alguno le reconoce los comandos para variar el brillo? Es decir FN +F7 y Fn + F8 ?? A mi no

A mi me funcionan las teclas del brillo.
Igualmente configuré el teclado como latino americano y en el tipo de teclado le puse compaq notebook o al go por el estilo, pero funcionaba sin problemas.

Saludos

Lambres

---

### Post by niko_3100 on 2008-04-30
No, yo no puedo regular el brillo SALLLVOOO!!!! que lo configure en el grub ahi si me deja despues cuando inicia ubuntu ya no me deja, probe hasta con el plugin de compiz para regular el brillo y tampoco... No se que onda.

---

### Post by alejandro.mc on 2008-04-30
Mira yo te cuento. Apenas instale el Hardy me prompteo para instalar los drivers de Nvidia (si no te mensajea para que lo instales vas a Preferencias > Hardware Drivers y le das tilde para que lo instale), los instale, reinicie y despues me tei ahi en Hardware Drivers otra vez y estaba para tildar la placa wifi Broadcom B43 wireless driver, lo tilde instaló y reinicie.

Con eso ya tenia todo al dia. Una Compaq F506LA! No se si te sirve lo que digo pero bueno mucho mas no puedo aportar, solo digo que lo de el ndiswrapper lo habia probado varias veces antes de Hardy y nunca funcionaba.

Saludos y Suerte!

---

### Post by Apipote on 2008-04-30
Si, es obvio que depende de la broadcom que tengas.
Con la 4311 nada...algunas otras como la tuya, parece que funcan.
Seguiré con mi xp sp3, hasta octubre...:(

---

### Post by niko_3100 on 2008-04-30
Pero apipote dejate de jo... te vas a bancar xp por no meter unos driver de... xp, pasate a hardy, total el driver es en realidad secuencias de 1 y 0 en cualquier SO no le va a hacer mal. Ahora... lo que te va a hacer mal a vos va a ser el xp si lo vas a usar jaja!!

---

### Post by Flechagorda on 2008-04-30
El lunes me entregaron una Compaq F756...

Ni llego a prender el Vista, ya de entrada, CD de Ubuntu 8.04...

RECONOCIO DE ENTRADA:

Touchpad con los scroll...
Todas las teclas FN, volumen, brillo, etc etc
Sonido
Placa NVIDIA, solo instale Compiz manager y listo...
Placa de Red y Modem ni hablar....
La webcam que trae integrada...la probe con cheese y anda joya, me queda probarla con Pidgin, porque emesene no tiene video todavia...

O sea, levanto casi todo sin problemas y sin configurar nada.

Lo unico, fui WIFI...

Viene con este modelo:

Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter

Para empezar, el interruptor que viene en la parte delantera de la laptop, no cambia de color, queda siempre amarillo. Pero su funcion (habilitar o deshabilitar) la cumple a la perfeccion..

Los Controladores Restringidos la reconocen e instalan unos drivers...Deshabilite el "Atheros Hardware Access Layer (HAL)", e instale los drivers de MADWIFI. Y listoooooo

Si los puedo ayudar con cualquier pregunta en particular sobre este modelo...

Abrazo para todos...

---

### Post by niko_3100 on 2008-04-30
Como es eso de madwifi?? que es jeje!!

---

### Post by Flechagorda on 2008-04-30
MADWIFI es un grupo de voluntarios que desarrolla drivers para wifi en linux (sacado de la pagina oficial)

Mira un poco por aca, porque soy medio novatoide y no se bien como explicarte...

[http://www.ubuntu-es.org/index.php?q=node/83054](http://www.ubuntu-es.org/index.php?q=node/83054)

[http://www.linlap.com/wiki/Configuring+the+madwifi+driver+for+Atheros+based+wireless+controllers+in+Ubuntu+7.10](http://www.linlap.com/wiki/Configuring+the+madwifi+driver+for+Atheros+based+wireless+controllers+in+Ubuntu+7.10)

En el link de Ubuntu-ES esta clarisimo como hacer, yo segui esos pasos y fue de primera....

---

### Post by Apipote on 2008-05-01
Niko entendé a un obse...:)

Flecha, te envidio sanamente, yo padezco desde que compré esta f566 con linux.

Abrazo

---

### Post by faktorqm on 2008-05-01
Apipote: viste esto? (OJO, es para 4312 rev 02)

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Otro tip: si le pasas al kernel en el grub el noapic, no te anda. 

Otro post importante que resolvio el problema, y luego no le andaba la red cableada (cuac!!)

[http://ubuntuforums.org/showthread.php?t=773774](http://ubuntuforums.org/showthread.php?t=773774)

y esto lo viste tambien?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

pero es artheros tu placa o es bradcom? no entiendo....
apipote: podrias postear vos por favor las especificaciones de tu compu, adjuntando un lspci y un lsusb? gracias, te vamos a ayudar mejor asi. Salu2!

---

### Post by niko_3100 on 2008-05-01
Si apipote te re entiendo a mi tambien me ****, pero tene en cuenta que no es la culpa ni de ubuntu ni de windows sino de broadcom que no tiene un driver como la gente para linux OJO como placa wifi me anda de 10 y tiene muuucho alcanza mas que las intel pero eso es lo peor los drivers para ubuntu pero para mi es mucho peor tener que bancarme windows por un Topu wifi.

---

### Post by Apipote on 2008-05-02
Facto
Te cuento es una broadcom 4311 rev 2. La más dificil de todas. No hay forma de alguno de los Ubuntu que vengo probando desde hace 7 meses me la levante. No me va el ndiswrapper, y debo reconocer que con xp sp3 vuela. Estudio tus links y te cuento.
Ya sé que con intrepid andará
Abrazo

---

### Post by niko_3100 on 2008-05-11
Gente se me cuelga hardy.... estoy lo mas bien con mi hardy haiendo cosas, escuchadno musica lo que sea y derepente se congela la pantalla y muere, no mueve el mouse, no puedo resetear las x, no pued abrir una consola en modo texto, no me puedo conectar por ssh... Se friza la compaq y tengo que apagar y volver a prender... que sera? alguno tiene idea? Hice un memtest a full lo deje toda la noche y no me tiro ningun error de memoria tampoco, que sera? los drivers nvidia?

---

### Post by euzkoarima on 2008-05-12
La verdad ni idea, pero supongo que para tratar de develar el misterio tendrías que fijarte en los logs del sistema, a ver si alguno da una pista. Fijate y postealos.

Suerte

---

### Post by niko_3100 on 2008-05-12
los logs del sistema en donde esta? /var/logs pero cual es de todos?

---

### Post by faktorqm on 2008-05-12
Y pone estos asi nos divertimos un rato :KS

```
cat /var/log/daemon.log
```

```
cat /var/log/debug
```

```
cat /var/log/kern.log
```

```
cat /var/log/syslog
```

```
cat /var/log/Xorg.0.log
```

Salu2!

---

### Post by lega on 2008-05-19
Me compré la Compaq F755, en realidad se la compró mi esposa, a la 1/2 hora de probar Vista, mi señora me dijo, bueno hacé los discos de recuperación e instalá Ubuntu :) dejamos Vista en una partición por las dudas, al iniciar el Live cd ya me puso el cartel que unos drivers restictivos ya estaban en uso, creo que eran los de wifi decía Atheros nosequemás(mañana pongo caps ahora no estoy en casa) al terminar la instalación me ofreció instalar los drivers de nvidia y anduvo todo bien, no tengo manera de probar la placa wireles, porque en casa todavía no tengo, la luz esta siempre en rojo, en cambio en Vista ni bien inicia se pone en azul

La única forma de saber si reconoció el wireless es que ir a un lugar con wifi? la webcam tampoco la probé.
Saludos

---

### Post by niko_3100 on 2008-05-19
si o pone ifconfig y fijate si tenes algo como wlan0 o algo asi o sino anda a un bar con wifi y probala, pero creo que tendira uqe tener la lucesita en color celeste, yo por lo menos en mi compaq v3415 la tengo asi pero mi placa wifi es broadcom no atheros.

---

### Post by lega on 2008-05-21
Actualizo información sobre la placa wireless en la Compaq F755 el ifconfig no listaba la placa, asi que seguí las instrucciones que figuran en [este thread de Ubuntu-es]("http://www.ubuntu-es.org/index.php?q=node/83054") que puso Flechagorda acá mismo y aparentemente anda...digo aparentemente porque no he tenido oportunidad de probarla, pero el ifconfig ahora si sale wlan0, la luz siempre esta roja, sin embargo ahora el icono de redes en la barra de notificación tengo la opción de crear ua coneccion inalambrica cosa que antes no aparecía.
Todo lo demás no tuve problemas, placa de video ok, sonido tambien, modem,webcam, auriculares (leí que los altavoces no se apagaban al enchufar los auriculares en gutsy)
La verdadera prueba será cuando compre el router wifi el mes que viene, pero le tengo fe :)
Saludos

---

### Post by vk-cdg on 2008-08-11
> **Flechagorda said:**
> MADWIFI es un grupo de voluntarios que desarrolla drivers para wifi en linux (sacado de la pagina oficial)

Mira un poco por aca, porque soy medio novatoide y no se bien como explicarte...

[http://www.ubuntu-es.org/index.php?q=node/83054](http://www.ubuntu-es.org/index.php?q=node/83054)

[http://www.linlap.com/wiki/Configuring+the+madwifi+driver+for+Atheros+based+wireless+controllers+in+Ubuntu+7.10](http://www.linlap.com/wiki/Configuring+the+madwifi+driver+for+Atheros+based+wireless+controllers+in+Ubuntu+7.10)

En el link de Ubuntu-ES esta clarisimo como hacer, yo segui esos pasos y fue de primera....

Bajé el driver como dice el tuto y me encuentro que el archivo tiene adentro solo un readme con esta leyenda.

```
You most likely downloaded this tarball since you are looking for a version of MadWifi which supports the AR5007 chipset family, which is for example used in the EeePC.

However, since you've downloaded this tarball, you've followed outdated instructions. The code that this tarball once contained is now obsolete.
Please follow these instructions to enable your AR5007-based WLAN device:
http://madwifi.org/ticket/1192

If you have any questions about it, please contact our regular support
channels: http://madwifi.org/wiki/Support

Thanks.
```

Aparentemente hay un nuevo driver o una nueva forma de instalarlo. Anoche era demasiado tarde (2:30 AM) y me tenía que ir a dormir así que veré si hoy puede hacerla andar con este tuto. Mi inglés no es tan bueno.

---

### Post by vk-cdg on 2008-08-25
> **Flechagorda said:**
> El lunes me entregaron una Compaq F756...

Ni llego a prender el Vista, ya de entrada, CD de Ubuntu 8.04...

RECONOCIO DE ENTRADA:

La webcam que trae integrada...la probe con cheese y anda joya, me queda probarla con Pidgin, porque emesene no tiene video todavia...


Revivo este post porque ayer justamente se me ocurrió probar la webcam. Tengo instalado el "Camorama" y cuando lo abro me dice que no encuentra el dispositivo en /dev/Video0.

Me surgen 2 preguntas (una mas idiota que otra)

1) Como hago para ver que dispositivo está usando (video0, video1, etc)
2) Como hago para reconfigurar el soft?

Gracias!

---

### Post by lega on 2008-08-25
sugerencia, tambien idiota, probaste con cheeze?

---

### Post by vk-cdg on 2008-08-25
Mmmmm.... nop, no lo tenía al prog. ese. Llego a casa y pruebo.

---

### Post by luks911 on 2008-08-25
Yo tengo una Compaq F754, con camorama no funciona, con cheese anda pero es un poco lento y graba mal, con el que anduvo del todo bien es con wxcam ([http://wxcam.sourceforge.net/index.php](http://wxcam.sourceforge.net/index.php)).

---

### Post by niko_3100 on 2008-08-28
Muchachos a ver si me peuden ayudar. Tengo instalado hardy 8.04 en mi nueva compaq v3614 y cada ves que la prendo vuelve el brillo al estado inicial, es decir super brilloso, cuando en realidad tendria que dejarme los valores que yo le deje configurado, a alguno mas le pasa? y tampoco me toma que le deshabilite el touchpad

---

### Post by sergiom99 on 2008-08-28
el tema del brillo yo lo configuré desde los seteos de energía, para que cuando estoy a batería tenga un intensidad y cuando estoy con AC otra.
(en Kubuntu) si le das doble clic al ícono de batería, entrás a esta configuración.

El touchpad no me lo guarda como desactivado, sino que cuando voy a poner la contraseña en el login lo desactivo porque uso un mouse USB.
salu2.-

---

### Post by vk-cdg on 2008-08-28
Respecto del brillo, me pasa lo mismo, pero en realidad no le di demasiada bola. 

En cuanto al touchpad, no entendí bien que es lo que te pasa. A mi me lo habilita y deshabilita al tocar el botón correspondiente, pero no probé (porque por el momento no tengo mouse para la note) si me deja recordado el último estado. 
Lo que si me pasa, es que cuando lo habilito (luego de haberlo deshabilitado) me abre la pantalla de ayuda (como si hubiera apretado F1). No me calenté demasiado porque no suelo deshabilitar el touch.

---

### Post by niko_3100 on 2008-08-28
A mi tambien me pasa lo de la pantalla de ayuda igual igual. Lo que yo digo es: como yo uso un mouse por usb tengo todo el tiempo deshabilitado el touchpad y brillo con poca intensidad, ahora bien cuando la desconecto de la corriente y la vuelvo a conectar y prender, me vuelve el brillo al maximo y el touchpad habilitado, es decir no guardo o no "recuerda" como configure el brillo a mi gusto si la apago.

---

### Post by luks911 on 2008-08-28
> **vk-cdg said:**
> Respecto del brillo, me pasa lo mismo, pero en realidad no le di demasiada bola. 

En cuanto al touchpad, no entendí bien que es lo que te pasa. A mi me lo habilita y deshabilita al tocar el botón correspondiente, pero no probé (porque por el momento no tengo mouse para la note) si me deja recordado el último estado. 
Lo que si me pasa, es que cuando lo habilito (luego de haberlo deshabilitado) me abre la pantalla de ayuda (como si hubiera apretado F1). No me calenté demasiado porque no suelo deshabilitar el touch.

Lo del brillo también me pasa con la F754, pero desde que la estoy usando sin la batería. Antes, aunque estuviese enchufada pero con la batería, no pasaba. En fin.

Y también pasé por lo del touchpad y la ayuda. Eso sí lo arreglé. Hay que ir a Combinación de Teclas (en preferencias o administración, no recuerdo) y buscar cuál es la combinación que dispara la ayuda, y borrar esa configuración o, si quieren,  cambiarla. Ah, antes, con Gutsy, en vez de la ayuda se abría el Rythmbox. Me molestaba bastante.

Saludos

---

### Post by lega on 2008-08-28
ah..lo de el touchpad también me pasa en la Compaq F755, mi esposa me tiene podrido con que cada vez que lo habilita se le dispara la ayuda, voy a buscar la combinación.
Gracias.

---

### Post by sergiom99 on 2008-08-28
lo de la ayuda a mi me pasaba en Kubuntu 7.10 y nunca pude encontrarle la vuelta. Desde que puse Hardy "se arreglo solo".

si seteas que nivel de brillo queres para cada modo de energia no te lo guarda cuando pasas a ese modo?

---

### Post by luks911 on 2008-08-28
> **sergiom99 said:**
> 
si seteas que nivel de brillo queres para cada modo de energia no te lo guarda cuando pasas a ese modo?

Es que usando gnome no aparece esa opción en gestión de energía, si no recuerdo mal, je.

---

### Post by sergiom99 on 2008-08-28
> Es que usando gnome no aparece esa opción en gestión de energía, si no recuerdo mal, je.
*[parodia de flame] ja, pongan eyecandy nomas... que despues no pueden configurar nada... [/parodia de flame]*

en algun lugar debe estar guardado entonces. se que hay comandos para setear el brillo, que obviamente no los conozco, pero se podria hacer scripts para que los corra al arrancar. es un ugly-fix, pero es lo unico q se me ocurre ahora.

---

### Post by luks911 on 2008-08-28
> **sergiom99 said:**
> *[parodia de flame] ja, pongan eyecandy nomas... que despues no pueden configurar nada... [/parodia de flame]*

en algun lugar debe estar guardado entonces. se que hay comandos para setear el brillo, que obviamente no los conozco, pero se podria hacer scripts para que los corra al arrancar. es un ugly-fix, pero es lo unico q se me ocurre ahora.

Sí, esa debería ser la solución con qué comando se cambia el brillo. Porque us(amos)o el applet de gnome.

---

### Post by sergiom99 on 2008-08-28
buscando en los foros, aparece esto:
[http://ubuntuforums.org/showthread.php?t=881241&highlight=change+screen+brightness](http://ubuntuforums.org/showthread.php?t=881241&highlight=change+screen+brightness)
[http://ubuntuforums.org/showthread.php?t=767374&highlight=change+screen+brightness](http://ubuntuforums.org/showthread.php?t=767374&highlight=change+screen+brightness)
[http://ubuntuforums.org/showthread.php?p=4178093#post4178093](http://ubuntuforums.org/showthread.php?p=4178093#post4178093)
(a ver si aplica a lo tuyo)

y el comando es:
[QUOTE=vor]If you can't find any gui applications to do it, you could try xbacklight.  For example, to set it to 50% brightness, try:

```

xbacklight -set 50

```[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=838741&highlight=change+screen+brightness](http://ubuntuforums.org/showthread.php?t=838741&highlight=change+screen+brightness)

---

### Post by luks911 on 2008-08-28
Groso, gracias. En casa con la notebook pruebo lo del xbacklight, porque las Fn funcionan. Si va, lo pongo al inicio y chau.
:lolflag:

---

### Post by niko_3100 on 2008-08-28
ah mira vos, llego a casa y lo prueb y lo del touchpad no pense que era tan facil como eso, que navoleti... a todos les anda el wifi? mi wifi broadcom es re potente, esta muy bueno.

---

### Post by luks911 on 2008-08-28
Che, no, el xbacklight no anda. Bah, no debe ser compatible con mi pantalla/driver de video. Porque me dice que 
"No outputs have backlight property"

Parece que sigo con las Fn, que no es poco.

---

### Post by niko_3100 on 2008-08-28
Se a mi tampoco me funciono lo del xbacklight

---

### Post by sergiom99 on 2008-08-28
uuuh! sera algo de KDE entonces?
```
sudo apt-get install xbacklight
```
```
xbacklight [-help]  [-display display] [-get] [-set percent] [- inc percent] [-dec percent]
```

creo que hay uno para nvidia que se llama nvclock.

---

### Post by niko_3100 on 2008-08-29
nono, no creo que sea solo para kde, debe ser para algunas placas No nvidia, no es tan grave el problema pero cada ves que la prendes molesta un poco, por suerte cuando subis o bajas el brillo te aparece un iconito que te dice en que nivel estas, cosa que win no y tampoco con el volumen... grande gnome!! y ubuntu!!

---

### Post by sergiom99 on 2008-08-29
ok, entonces como tarea para el hogar les queda investigar por el lado de nvidia. tal vez con el comando nvclock que te mencione.
cuando llegue a casa pruebo en la mia, pero nunca me hizo falta porque lo tengo configurado desde los power-settings. o sino lo hago con las FnKeys.
Agradezcan que se las reconoce que hay mucho con Vaios que put3an por eso.

---

### Post by niko_3100 on 2008-09-01
No, el nvclock no es, como es el programa de gestion de energia en KDE? por ahi lo bajo y lo pruebo aunque... me tengo que bajar todas las librerias propias de kde pero bueno.

---

