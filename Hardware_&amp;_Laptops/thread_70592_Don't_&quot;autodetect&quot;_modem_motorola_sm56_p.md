---
title: "Don't &quot;autodetect&quot; modem motorola sm56 pci speakerphone modem"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by efpc2003 on 2005-09-30
HOW TO....?
I don't speak english...I hope you understandme.
Ubuntu 5.04 don't autodetect modem motorola [COLOR="DarkRed"]sm56 pci speakerphone[/COLOR]....but....list it into "device manager", I can see the modem in/at "device manager". When I run the hardware test.....freeze/crash when network test comes. I was try to select the port but ubuntu can't find the modem at none port.
I need connect to internet but I don't know how and what to do.
HELPME PLEASE!!!!
Esteban (from Montevideo-Uruguay)

---

### Post by jasmuz on 2005-10-03
Saludos.

El hecho de que tu Modem se encuentre en el Device Manager no significa que esté operacional.

Abre una terminal y teclea lspci

Si te sale información sobre el modem entonces ha sido reconocido, despues harás un sudo pppconfig para crear tu cuenta de internet y debes escoger el puerto que está usando el modem.

Cualquier cosa, dejame saber.

---

### Post by az on 2005-10-03
[QUOTE=efpc2003]HOW TO....?
I don't speak english...I hope you understandme.
Ubuntu 5.04 don't autodetect modem motorola [COLOR="DarkRed"]sm56 pci speakerphone[/COLOR]....but....list it into "device manager", I can see the modem in/at "device manager". When I run the hardware test.....freeze/crash when network test comes. I was try to select the port but ubuntu can't find the modem at none port.
I need connect to internet but I don't know how and what to do.
HELPME PLEASE!!!!
Esteban (from Montevideo-Uruguay)[/QUOTE]

Motorola does not support linux.  You can send them an email asking them to release the specs or a driver for the modem.  They had released a driver a long time ago for older linux kernels but they have since gotten out of the modem business.  You are screwed.

---

### Post by efpc2003 on 2005-10-04
[QUOTE=jasmuz]Saludos.
El hecho de que tu Modem se encuentre en el Device Manager no significa que esté operacional.
Abre una terminal y teclea lspci
Si te sale información sobre el modem entonces ha sido reconocido, despues harás un sudo pppconfig para crear tu cuenta de internet y debes escoger el puerto que está usando el modem.
Cualquier cosa, dejame saber.[/QUOTE]
NO FUNCIONÓ.
En el panel superior de gnome tengo el icono del modem, le doy activar, me pregunta ¿conectar? le digo SI  y abre el diálogo “conectando con el proveedor de internet” y a los 2 o 3 segundos desaparece y no hace más nada.
HICE LO SIGUIENTE:
root@ubuntu:~# lspci
0000:00:00.0 Host bridge: Intel Corp. 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corp. 82810 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97 Audio (rev 02)
0000:01:05.0 Communication controller: Motorola SM56 PCI Modem
Number    9000071          Número de teléfono                      &#9474;
&#9474;       ISPLogin  ogin:miusuario          Texto de petición de acceso          
&#9474;       User      miusuario               Nombre de usuario del ISP        
&#9474;       ISPPrompt ssword:micontraseña   Texto de petición de contraseña          
&#9474;       Password  micontraseña        Contraseña del ISP                        &#9474;
&#9474;       Speed     115200               Velocidad del puerto                    &#9474;
&#9474;       Com       /dev/ttyS2           Puerto de comunicaciones del módem      &#9474;
&#9474;       Method    chat                 Método de autenticación
Preferencias avanzadas para netgate» &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
Este menú le permite cambiar algunas de las preferencias más ocultas.
Seleccione la preferencia que quiera cambiar y seleccione «Previous»
cuando esté satisfecho. Use las teclas de flecha para moverse por la lista.
Modeminit    ATZ                  Cadena de inicialización del módem
ISPConnect   ''                   Respuesta de conexión
Pre-Login                         Órdenes previas a la conexión
Defaultroute defaultroute         Estado de la ruta predeterminada
Ipdefault    noipdefault          Establece la dirección IP
Debug        enabled              Activar o desactivar la depuracion
Demand       disabled             Activar o desactivar la marcación bajo demanda 
Persist      disabled             Activar o desactivar el modo persistente
Nameservers  dynamic              Cambiar el DNS
Add-User                          Añadir un usuario PPP
Post-Login   '' \d\c              Órdenes post-conexión
Idle-timeout none                 Tiempo de espera por inactividad
TUVE QUE SELECCIONAR EL PUERTO MANUALMENTE YA QUE EL SISTEMA NO LO ENCONTRÓ. UTILICÉ EL PUERTO /dev/ttyS2 PORQUE EN WINDOWS ESTÁ FUNCIONANDO CON “com3”, y /dev/ttyS1 que es el que el sistema recomienda no funciona. Usé “CHAT” porque mi ISP me solicita usuario y contraseña.
POR SI SIRVE DE ALGO TE CUENTO QUE EN LA CONFIGURACIÓN DE WINDOWS EN LAS PROPIEDADES DE LA CONEXIÓN ESTA MARCADO LO SIGUIENTE:
Tipo de servidor: ”PPP:Internet, Windows 2000/NT Server, Windows ME”
En “Opciones avanzadas” está marcado: “Habilitar la compresión por software”
En “Protocolos de red admitidos” está marcado: “TCP/IP”
Y en la configuración TCP/IP está marcado:
“Dirección IP asignada por el servidor”,
“Direcciones DNS asignadas por el servidor”,
“Utilizar compresión en encabezado IP” y
“Utilizar puerta de enlace predeterminada en red remota”.
Espero que estos datos que te proporciono ayuden para que me digas qué es lo que estoy haciendo mal. Como puedes ver soy nuevo en esto y el objetivo es deslindarme de microsoft.

---

### Post by jasmuz on 2005-10-04
Estimado Amigo:

No me habia percatado que era un PCI Modem de Motorola, puedes consultar [www.linmodems.org](www.linmodems.org) para informaci&#243;n, pero para ser sincero, estos modems son un dolor de cabeza para linux ya que no cumplen con espeficicaciones de modems reales.

---

