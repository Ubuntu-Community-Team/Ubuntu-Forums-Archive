---
title: "Portatil HP G50-103NR (Problemas con la Wifi y LAN)"
date: 2008-11-28
forum: Hardware
---

### Post by Xavierss on 2008-11-28
Buenas amigos, Descargue ilusionado la distribucion de Ubuntu Ultimate Edition 2.0 con el animo de probar un nuevo SO y con tantas cosas buenas que se oye de linux siempre dan ganas de probarlo, nunca lo habia hecho hasta ayer tengo windows vista ultimate instalado y me decidi por instalar el ubuntu tambien, lo probe y todo bien esta muy bueno el SO la interfaz grafica con compiz es demasiado el unico de detalle es que no me reconoce la wireless ni el lan de mi laptop y se te baja como el animo que estes probando un SO tan bueno como Linux y tu primera impresion sea problemas con la wifi, problemas con la lan... no puedo conectarme a internet es frustante me canse de buscar en internet y encontre como 12736187468 casos como el mio pero con distintas portatiles... Lo poco que pude usar el ubuntu me encanto pero me frusto lo del internet si alguien tiene una solucion automatizada para este problema de drivers o no se como se llamara en linux por favor se lo agradeceria mucho... En windows simplemente se va a la pagina directa del fabricante se descarga el driver mas actualizado y se instala y listo pero en ubuntu al paracer es una odisea hacer algo asi...

Saludos espero sus respuestas y gracias por su atencion

La portatil en la cual instale ubuntu es una HP G50-103NR

---

### Post by Hei Ku on 2008-11-28
Primera respuesta. Andá a la pagina del fabricante y pedí el driver de linux.
(Todos sabemos que no te van a dar ni la hora, pero es la manera de hacerles notar su falla)

Segunda respuesta. Abri una terminal y pone estos dos comando y postea el resultado.
```

lspci
lsusb

```

Necesitamos saber qué tenés antes de poder ayudarte. Y no, el modelo de notebook no ayuda porque la misma notebook puede tener distintos modelos de placas de red.

---

### Post by faktorqm on 2008-11-28
Hola y bienvenido al foro.

Que no exista un proceso automatizado para la instalacion de los drivers es culpa de las empresas que fabrican los dispositivos que no hacen drivers para linux. De las empresas que si lo hacen, hay dos tipos, las que liberan el driver y las que no. Las que no liberan el driver, poseen un proceso automatizado de instalacion y listo. Las que liberan el driver, en el 99% de los casos ¡no necesitas tocar nada!

Otra cosa: la version de ubuntu que nombras no es oficial. Las versiones no oficiales de ubuntu no son ni se consideran _seguras_. Te recomendaria que te bajes un ubuntu original y reinstales.

Bueno, necesitamos para poder ayudarte algunos datos mas sobre tu notebook, ya que con el modelo no alcanza, por que en la página de hp son tan vivos que te ponen "Wireless LAN 802.11 b/g WLAN" y "Integrated 10/100 Ethernet LAN", no son tiernos? :lolflag:
funte: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01607697&lc=en&dlc=en&cc=us&product=3818753&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01607697&lc=en&dlc=en&cc=us&product=3818753&lang=en)

Anda a aplicaciones -> accesorios -> terminal y a aplicaciones -> accesorios -> editor de textos. En la terminal escribi "lspci" (sin comillas) y apreta enter. te va a tirar un listado de cosas, lo copias y lo pegas en el editor de textos. Luego volves y escribis "ifconfig" (sin comillas) y haces lo mismo. Luego guardas y pegas ese texto aca en el foro asi lo vemos y te decimos que driver va.
Esos comandos, el primero te lista todos los dispositivos pci que tenes en tu compu, y el segundo te muestra las configuraciones de la placa de red (en realidad este ultimo no sirve de nada, ya que no tenes ninguna de las dos redes pero quiero saber si al menos "ve" algo).

Salu2!!! :popcorn:

---

### Post by Xavierss on 2008-11-28
Buenas gracias por recibirme en el foro, la verdad es que no esperaba una respuesta tan rapida y con tantas ganas de ayudar sinceramente muchas gracias... Estas cosas motivan, me dieron esperanzas donde ya no habia..

Bueno primero que todo lo que me pidieron la informacion del lspci en el terminal

LSPCI

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03) 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Podemos ver las ultimas dos lecturas que ahi estan los niños, por los menos los ve

Ahora la info del ifconfig

IFCONFIG

eth0      Link encap:Ethernet  direcciónHW 00:1f:16:4e:4f:43   
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1 
          RX packets:0 errors:0 dropped:3591805675 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          colisiones:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupción:220 Dirección base: 0x6000  
 
lo        Link encap:Bucle local   
          inet dirección:127.0.0.1  Máscara:255.0.0.0 
          dirección inet6: ::1/128 Alcance:Anfitrión 
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1 
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0 
          colisiones:0 txqueuelen:0  
          RX bytes:4440 (4.4 KB)  TX bytes:4440 (4.4 KB)

Nota: si aparece algo es porque estuve intentanto por todos lados configurar la red pero todos los intentos terminaron en fracaso, disculpen es mi primera vez en ubuntu y trato de hacer lo mejor que puedo

Alguien pidio la info del lsusb y bueno tambien la saque para postearla

LSUSB

Bus 005 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Y bueno vuelvo a decirle gracias de nuevo de veras ya me habia desilucionado de la idea de usar el ubuntu que lo poco que he visto me ha encanto y me devolvieron la esperanza...

Saludos :wink:

---

### Post by faktorqm on 2008-11-28
Bueno perfecto, con lo de la placa WI-FI el tutorial que tenes que seguir es este: [http://ubuntuforums.org/showthread.php?t=887531](http://ubuntuforums.org/showthread.php?t=887531) y lo hice yo, asi que quedate tranquilo que si no te anda algo pregunta y lo vemos, pero a muchos usuarios les anduvo. (lee el thread completo)

Con lo de la placa de red cableada, el ifconfig te la esta viendo, lo que no signifique que ande, pero lo que te esta diciendo ahi es que no esta configurada. Los pasos a seguir son:

Primero que nada fijate como la tenes configurada en el windows. (muy probablemente la tengas en dhcp, sino anota todos los datos). Despues enchufa el cable de red xD. Luego hace un solo click en el icono (normalmente arriba a la derecha al lado del reloj) con dos computadoras y te va a aparecer un boton que dice configuracion manual... le das click otra vez y ahi te abre un a ventana nueva. Apretas desbloquear, pones la misma contraseña que usaste para entrar al sistema y luego seleccionas red cableada y apretas propiedades. Ahi en configuracion elegis, si tenes dhcp, pone dhcp, y si tenias mas datos de ip, mascara gateway, dns y etcetc elegis ip estatica e ingresas todo.

Espero que te haya servido, y contanos como te fue. Salu2!!!!

---

### Post by Xavierss on 2008-11-30
Amigo faktorqm te cuento que intentando resolver el problema de la wireless con el tuto que me pasaste de repente me comenzo a funcionar el LAN pero con el wireless no tuve exito, segui los pasos que indicas en el tutorial y no funciono lo repeti varias veces descartando que hubiera hecho algo mal y no lo logre... despues no pude contenerme probando ubuntu navegando y todo bien pero luego me aparecio que tenia que actualizar mi sistema que habian varias actualizaciones y no lo pense dos veces y actualice todo deje eso descargando y me fui... cuando volvi estaba todo toltamente actualizado pero el LAN ya no funcionaba de nuevo y ahora estoy sin Wireless ni LAN :(  y otra cosa rara que tengo es que cuando se activa el protector de pantalla por mucho tiempo que muevo el mouse no me vuelve al escritorio se quita el salvapantalla pero no vuelvo a poder entrar al sistema tengo que reiniciar pero eso es lo de menos solo quisiera poder navegar con ubuntu :( :(... Gracias por toda la ayuda que me has brindado faktorqm en serio gracias

---

### Post by luks911 on 2008-11-30
Xavierss,

El tuto para el wifi que tenés que seguir es [este]("http://ubuntuforums.org/showpost.php?p=5577447&postcount=13")[0], es el post 13 del hilo que te pasó Faktor. Porque aparece uno al principio del hilo pero ya no sirve.
En cuanto a la LAN, se me ocurre que es cuestión de que la configures como dijo, otra vez, Faktor.

Saludos

[0] [http://ubuntuforums.org/showpost.php?p=5577447&postcount=13](http://ubuntuforums.org/showpost.php?p=5577447&postcount=13)

---

### Post by Xavierss on 2008-11-30
Listo lo logre gracias a ustedes de veras muy agradecido ahorita estoy conectado via wifi lo unico que lo logre fue instalar el wicd pero todo esta funcionando perfectamente... muchisimas gracias de veras, el lan me sigue sin funcionar pero bueno normalmente siempre me conecto por wifi

Mis agradecimientos a:

faktorqm (por la ayuda que me presto desde un principio y al increible tutorial)

luks911 (por enviarme a la parte del tutorial que no lei y las ganas de ayudar)

de veras muy agradecido...

Si pudieran ayudarme con lo del LAN seria genial asi tendria mi ubuntu configurado completamente... Les comento que la primera vez solo conecte el cable de red y ubuntu automaticamente detecto la conexion del cable y a los segundos ya estaba conectado pero ahora conecto el cable y ni siquiera lo detecta es como si no fuera conectado nada.. revise las opciones y esta activada lo de las redes pero no hace nada... 

Saludos y muchisimas gracias por su ayuda... agradecido de veras :KS

---

