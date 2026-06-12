---
title: "Conexion muy lenta con modem 3G de movistar"
date: 2009-01-01
forum: Hardware
---

### Post by infernus92 on 2009-01-01
hola... hace un rato logre conectar mi modem 3G de movistar desde  mi ubuntu 8.04 con ayuda de una guia que me baje y despues de varios intentos por fin se conecto...
pero la velocidad me marcaba 0.00 Kb/seg :(
lo conecte con gnome ppp como modem serie como me decia la guia
si alguien me puede tirar alguna idea o algo para subir la velocidad por favor... gracias

---

### Post by Hei Ku on 2009-01-27
que guia seguiste?
que modelo de modem es?

es un modem usb? pone el resultado de poner "lsusb" en una terminal.

Con un poco mas de datos, capaz te podamos ayudar. Por lo que entiendo, mas que lenta, la conexion es nula, no?

---

### Post by infernus92 on 2009-01-27
> **Hei Ku said:**
> que guia seguiste?
que modelo de modem es?

es un modem usb? pone el resultado de poner "lsusb" en una terminal.

Con un poco mas de datos, capaz te podamos ayudar. Por lo que entiendo, mas que lenta, la conexion es nula, no?

el modem es un Huawei E226 USB. 

La guia originalmente es para mandriva... pero me sirvio bastante bien... aca te la dejo...


Tarjeta 3G de Movistar.... con Linux más sencillo.
El otro día me entregaron una tarjeta Option PCMCIA Fusion GPRS/UMTS/WIFI, junto con su tarjeta SIM de Movistar y el software de instalación para Windows ¿cómo no?. El caso es acabé preocupado, pensaba que me darían un modem USB de Vodafone, del que encontré esta página con la configuración, que además, tiene bastante información útil sobre los mandatos AT de estos dispositivos, por lo que se la recomiendo a todo el mundo que trastee con estos dispositivos. También estaba preocupado ya mi amigo Sean, el mismo que me proporcionó esta dirección de Internet, tiene una tarejeta Vodafone funcionando y puestos a malas, siempre podría recurrir a su ayuda, pero yo tenía una tarjeta PCMCIA de Movistar, que era distinta a la suya y por lo tanto, me encontraba sólo ante el peligro. 

En teoría, hay versiones de este software "Escritorio Movistar" para otros dispositivos y sistemas operativos, por lo que decidí "preguntar" a Google. Según la página de Movistar, el invento es válido para "Ordenador con sistema operativo Linux, Fedora Core 6 y SUSE 10.1.: 

Podrás conectarte usando como módem gran variedad de terminales 3G y GPRS o con las Tarjetas Internet Móvil Option".. 

Desgraciadamente, yo no soy usuario de ninguna de esas distribuciones, lo mío es Mandriva 2007.

De todos modos, he de decir que cuando accedí a la página de Movistar para descarga del software, lo que hice por curiosidad morbosa, no fui capaz de bajarme nada de ella, no se si por problemas de "accesobilidad" o que está "malita" de estándares, pero como digo fue imposible. 

Como se dice vulgarmente, "me he tenido que buscar la vida por mi cuenta" ya que siempre que seleccionaba un software y pulsaba sobre el enlace, me salía el siguiente mensaje:

Not Found
The requested object does not exist on this server. The link you followed is either outdated, inaccurate, or the server has been instructed not to let you have it. Please inform the site administrator of the referring page.

Ni que decir, que en estas fechas próximas al "día de la marmota", la famosa Phil de la película "Atrapado en el tiempo", me sentía como Bill Murray intentando solucionar mi problema de software para la tarjeta en un bucle sin fin.

Primeramente me puse a la obra sobre Windows XP (para mi descargo he de decir que se trata de un ordenador corporativo con Windows XP de serie, al que he instalado una Mandriva 2007, mi portátil personal como es lógico, no dispone de Windows ni nada que se le parezca, lo siento Bill/Ballmer no me convence el producto, su funcionalidad y mucho menos, el precio). 

Siguiendo las instrucciones al pie de la letra, me doy cuenta de que no se instalan los controladores de la tarjeta adecuadamente, miro en el Administrador de hardware y tras varios intentos, todo con interrogación en amarillo. Después de varios intentos y de haber recurrido a la "lectura del jodido manual", encuentro este texto revelador...

En ocasiones se han detectado problemas en la instalación de los drivers o controladores de la tarjeta PCMCIA de Novatel. Usualmente, estos errores se producen cuando el usuario ya instaló con anterioridad los drivers.

Para desbloquear el proceso de instalación:

1. Accede al registro de Windows ejecutando la aplicación regedit1.
2. Localiza la carpeta HKEY_LOCAL_MACHINE/SOFTWARE/Novatel Wireless.
3. Elimina esta carpeta.

Tras el proceso de desbloqueo, puedes reiniciar la instalación del Escritorio MoviStar de la forma usual.

He de decir, que no hubo solución a pesar de poner en riesgo todo mi sistema por el procedimiento de marras. Luego pensé si el problema está en los controladores, ¿estarán los controladores en el disco?... sí, están pero dentro de un ejecutable único que se descomprime durante la ejecución. Pensé después, la solución puede ser acceder a la página del fabricante Option y descargar de allí los controladores. ¿Cuál no sería mi sorpresa, cuando me encuentro una página en la que hay que introducir el número de serie y el imei de la tarjeta (ambos datos están en el reverso de la tarjeta en números no aptos para mayores de 45 años), pero en la página hay un inquietante texto que dice...

Firmware and Software downloads available through Login are for use with the OPTION GlobeTrotter PC cards only. This Firmware and Software is not intended for customized PC cards obtained through a Network Operator (eg. Vodafone, T-Mobile, Orange ...).

Users of a customized PC card please contact your Network Operator Helpdesk for Support and Upgrade information.

Después de probar, por si las moscas, descubro que mi tarjeta es una de las llamadas "Cusmoized PC card". Pensé, cielos los pobres usuarios de XP no tienen nada que hacer... De nuevo, una búsqueda intensiva en Google y otros buscadores, dieron al traste con mis esperanzas de encontrar unos controladores válidos. Comprobé que había usuarios habían hecho funcionar la tarjeta sin el software "Escritorio Movistar" bajo XP mediante una conexión módem estándar (aquí la primera pista sobre el número de teléfono), pero para ello, los controladores eran fundamentales, es decir, que estaba como antes de empezar. 

Visto lo visto copie la información que aparecía como configuración de ahora inutilizable "Escritorio Movistar" que había instalado en Windows XP, e intenté localizar en dicha configuración una información que aparentemente no aparecía en claro por ninguna parte, el número de teléfono al que había que llamar para conectarse.

Ahora lo que procedía era salir del paso y de las pegas impuestas por el modelo de software propietario y su oscurantismo, para tener conectividad a Internet desde cualquier parte. Desde luego, no me apetecía llamar al Servicio Técnico de Movistar, cuando estaba convencido de que con Linux podría hacerla funcionar en breves instantes... además ¿darían soporte a Linux? ¿me darían la solución realmente?, para pagar una llamada siempre estamos a tiempo ¿no?. Por lo tanto, abrumado por la titánica tarea que se abría ante mis ojos y que solamente era apta para los hackers con más sólidos conocimientos del kernel, me puse a trabajar. 

Lo primero es introducir la tarjeta para ver lo que me dice el sistema, para ello abrí la consola de mensajes con Alt+Ctrl+F12. Los usuarios que no tengan configurado su sistema de este modo tan práctico, pueden usar el socorrido comando tail -f /var/log/messages, como es lógico, lo deben hacer desde una consola como root y después, introducir la tarjeta en su alojamiento... 

Lo que me dijo mi consola F12 fue revelador...

kernel: pccard: CardBus card inserted into slot 0
kernel: PCI: Enabling device 0000:07:00.1 (0000 -> 0002)
kernel: ACPI: PCI Interrupt 0000:07:00.1[B] -> GSI 16 (level, low) -> IRQ 17
kernel: ohci_hcd 0000:07:00.1: OHCI Host Controller
kernel: ohci_hcd 0000:07:00.1: new USB bus registered, assigned bus number 6
kernel: ohci_hcd 0000:07:00.1: irq 17, io mem 0x8c020000
kernel: usb usb6: configuration #1 chosen from 1 choice
kernel: hub 6-0:1.0: USB hub found
kernel: hub 6-0:1.0: 1 port detected
kernel: ohci_hcd 0000:07:00.1: wakeup
kernel: usb 6-1: new full speed USB device using ohci_hcd and address 2
kernel: usb 6-1: configuration #1 chosen from 1 choice
kernel: option 6-1:1.0: Option 3G data card converter detected
kernel: usb 6-1: Option 3G data card converter now attached to ttyUSB0
kernel: option 6-1:1.1: Option 3G data card converter detected
kernel: usb 6-1: Option 3G data card converter now attached to ttyUSB1
kernel: option 6-1:1.2: Option 3G data card converter detected
kernel: usb 6-1: Option 3G data card converter now attached to ttyUSB2

Estaba claro, mi tarjeta se se comportaba como un módem clásico conectado a un puerto serie USB que se abría al conectarla. Probaremos primero con el dispositivo serial ttyUSB0, más que nada, es el primero. Ahora había dos opciones, ir a escribirse los scripts de toda la vida no aptos para no iniciados..., o ser más elegante, probando otros refinamientos para el KDE o Gnome que se encargan de esto. 

Una buena alternativa podría ser Gnome-ppp, que instalé con el ordenador mediante el mandato urpmi gnome-ppp, y y que ejecuté desde una consola como root. ¿Por qué gnome-ppp y no otro?, bueno a pesar de que soy usuario de Mandriva y uso KDE (que me perdone Miguel de Icaza), he de decir que cuando usaba mi moden conceptronics para conectarme a la red de redes, probé con varias opciones y he de decir, que gnome-ppp siempre me funcionó mejor (de eso hace casi 4 años), por lo que ahora no había motivo para no darle otro voto de confianza al programa. 

Ni que decir que urpmi accedió al respositorio de paquetes configurado por omisión, e instaló de forma automática todos os paquetes que se necesitaban para completar las dependencias de este programa de configuración. En este punto sentí vergüenza ajena, por lo "complicado" que estaba resultando el proceso, ya no podía lucirme como hacker... una pena.

Una vez instalado, puse un acceso directo en mi escritorio (con un teléfono rojo como icono en homenaje a (Stanley Kubrick) y comencé a configurar el programa pensando en "volar hacia Moscú". Para ello, hice clic sobre el botón Configuración y seleccioné la pestaña Módem. Hay que señalar, que aunque el programa permite detectar el módem mediante el botón "Detectar", en ocasiones esto no funciona demasiado bien y como yo ya sabía el dispositivo que generaba la tarjeta, simplemente escribí en el apartado Dispositivo lo que ya sabía es decir, /dev/ttyUSB0. 

En el apartado Módem dejaremos "Módem analógico" y en el apartado velocidad, hay que seleccionar la mayor posible, no en vano esto es banda ancha ¿no?. La marcación nos sirve por tonos y el volumen en este caso es irrelevante ya que la tarjeta no tiene altavoz. Los intentos de marcado pueden ser 5 y es conveniente seleccionar la opción "Esperar por tono de marcado".

Ahora hay que indicar el número de teléfono, para lo que fue necesario algo de "ingeniería inversa" y algunas pruebas, por lo que ahorraré el suplicio y prometo que la cadena adecuada es "*99***1#", sin las comillas, es decir; asterisco, 9, 9, asterisco, asterisco, asterisco, 1, almohadilla. 

Una vez que sabemos el número a utilizar, hay que hacer clic sobre el botón "Números de teléfono" e introducirlo en el cuadro de diálogo que aparece. Después de pulsar el botón "Cerrar", hay que hacer clic sobre la pestaña Red para seguir con esta "complicada y ardua configuración", que a todas luces solamente apta para hackers consagrados. 

En esta pestaña, hay que seleccionar la opción IP dinámica y para las DNS, se introducirá en "Nombre de dominio" la cadena "movistar.es", sin las comillas. Después de seleccionar DNS manual, es necesario introducir las direcciones IP de las DNS de Telefónica. 194.179.1.100 como DNS primaria y 194.179.1.101 como secundaria. Finalizado esto, se seguirá la configuración pulsando el ratón sobre la pestaña Opciones.

En esta pestaña hay que seleccionar las opciones siguientes, aunque hay algunas que pueden quedar al criterio del usuario ya que no son críticas:

Mostrar en la barra de tareas, Reconectar automáticamente, Abortar conexión si no hay tono de marcado, Comprobar línea, Comprobar camino por defecto y Enviar respuesta personalizada. La respuesta personalizada es la cadena AT + GCGDCONT=1,"IP","movistar.es", en este caso tal como está escrita, con comas y comillas incluidas. El apartado "Ocupado", lo dejamos con un 0 y acabaremos haciendo clic sobre el botón "Cerrar". En este punto que decir que a través del recuadro respuesta personalizada, se le pueden mandar comandos AT al módem.

En el recuadro principal de la aplicación, hay que usar la cadena "movistar" tanto como nombre de usuario, como contraseña. Se puede seleccionar "Recordar contraseña" (yo como soy hacker ;-), no lo recomiendo) y finalmente, el número de teléfono que debe ser, como ya sabemos, "*99***1#". Si no aparece en ese cuadro, lo podemos volver a escribir, recordando que no hay que usar las comillas.

Hecho esto, ya podemos probar, es la hora de la verdad, para ello, desconecté el cable de red de mi portátil y esperé a que mi Mandriva 2007 me dijera que no hay conexión. Hecho esto, hice clic sobre el botón Conectar de gnome-ppp y esperé... unos segundos, pero nada de nada nada, el caso es que no me funcionó.

Cielos, no puede ser, si soy un hacker reconocido y he llegado a este punto, no me puedo haber equivocado, es imposible. Revisando el log de conexión, que es lo que hae cualquier hacker todas las mañanas antes de desayunar, parecía que el sistema no marcaba el número. Para el que no lo sepa, para ver el log, basta con hacer clic sobre el botón Registro de gnome-ppp, durante el intento de conexión, como se puede ver, es muy complicado. 

Pensando sobre el tema, me vino la iluminación... puede ser el pin de la tarjeta, cielos, la tarjeta tiene pin y no lo estoy metiendo. Como no sabía la forma de desconectarlo por software con las herramientas que tenía en ese momento y estaba ansioso por ver si funcionaba el sistema, decidí meter la tarjeta en mi teléfono móvil y seleccionar en las opciones de seguridad, la desactivación del pin, así a lo bruto, pero altamente efectivo.

Ahora, sí, después de unos instantes de negociar la conexión, apareció el reloj que indica que la conexión está activa y en el monitor de redes de la Barra de Tareas, apareció, durante unos instantes, un mensaje indicando la IP asignada, dicho lo dicho la conexión parecía activa. 

Ahora viene la hora de la verdad, puede que esto solamente sea un espejismo y las cosas no estén funcionando, es necesario cuestionarse todo para estar seguros. Para verificar que funcionaba bien abrí el navegador y tras unos instantes, en mi Firefox apareció la pantalla principal de Google. Es decir, estoy navegando, esa era la prueba del algodón. Después de hacer otras pruebas, comprobé que la velocidad no era demasiado mala, unos 300 Kps y que podía activar la red Tor sin problemas. 

Para acabar la conexión, basta con hacer clic sobre el icono que aparece en la Barra de Tareas y en el cuadro de diálogo siguiente, hacer clic sobre el botón "Desconectar", como se puede ver, una tarea que solamente es apta para personas con sólidos conocimientos de informática aplicada. 

Aquí tenemos los datos del partido, software propietario =0, software libre =10, que gana por goleada, haciendo posible, lo que con el propietario es a todas luces imposible, conectarse a Internet con una tarjeta 3G. 

Que el software propietario es para "tontos" ya lo sabemos, pero cuando dice que no quiere funcionar, no hay forma de lograrlo, como bien hemos podido comprobar en nuestras carnes. Por cierto, cuando pasa esto, te suelen decir en el Servicio Técnico, que si quieres conexión, que reinstales Windows que es lo mejor... cielos que cruz, por enésima vez este año a reinstalar XP. 

Este es un ejemplo claro por el que podemos decir tres cosas:

a) El software libre es más fácil de usar que el propietario, incluso en operaciones de configuración del sistema que son aparentemente complejas, como puede ser la instalación de un módem digital. Es más, en el caso de haber problemas con la instalación, no me obliga como en el caso del propietario, a toquetear el registro. Operación que si no hago bien, me obligará a reinstalar todo y que además, reparte muchas papeletas de perder toda la información almacenada en el ordenador. 

b) El software libre permite hacer cosas que en ocasiones el propietario no permite, con lo que se puede salir de situaciones tan engorrosas como la que acabo de explicar. 

c) Si se proporciona la información que acabo de dar, no es necesario hacer casi nada, solamente instalar gnnome-ppp, configurarlo como he indicado y meter la tarjeta en la ranura PCMCIA, algo en lo que se puede tardar segundos. Simple, rápido y eficaz. Una vez que se tiene la información relevante de configuración, no es necesaria la ingeniería inversa, ni las pruebas de dispositivo. Ya les vale no dar "soporte" para Linux ante semejante "problema" de configuración... eso sí hay que inventar la rueda con un "Escritorio Movistar", con capacidades limitadas bajo Linux y que solamente es utilizable con determinadas distribuciones. Ya podrían entregar el fuente, lo mismo hasta lo mejoramos ;-).


Si me podes tirar alguna idea de que puede ser... a mi se me acabaron... grax

---

### Post by guillermolisi on 2009-01-27
Leiste el tuto publicado en [http://ubuntu-ar.org/node/196](http://ubuntu-ar.org/node/196) ?
Si bien puede que no sea tu caso exacto posiblemente te brinde alguna ayuda lateral, alguna pista.

---

