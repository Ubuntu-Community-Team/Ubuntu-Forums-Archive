---
title: "Probelma con los gráficos."
date: 2010-11-20
forum: Hardware
---

### Post by daggaz on 2010-11-20
Bueno, resulta que me hice de una bonita Netbook Asus Seashell Series  a pesar de lo mucho que me quejaba de las mini computadotas, y estoy  feliz con ella.
Probé el Ubuntu Netbook remix en versiones anteriores con buenos  resultados, pero en esta versión donde nos meten el Mutter no estoy tan  contento, por lo que cambié a la desktop edition y me siento mucho más  libre y cómodo (como Ubuntu debe ser).
El problema viene cuando quería darle un poco de vida al escritorio con  Compiz... Pues imposible hacer que funcione hasta el momento. Intenté  con el Fusion-Icon pero me da el siguiente error en terminal:
 ```
$ fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
Backend     : ini
Integration : true
Profile     : default
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in 
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.6/dist-packages/FusionIcon/interface.py", line 21, in 
    from util import env
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 419, in 
    decorators = CompizDecorators(_installed)
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 226, in __init__
    self.command = context.Plugins['decoration'].Display['command']
KeyError: 'decoration'
``` Desde la configuración de «Apariencia» no me resulta y tampoco desde la configuración de Compiz.
Decidí activar el Composite de Metacity para que al menos mi dock se  viera lindo, pero extraño algunas cosas como la posibilidad de la  continuidad de los escritorios, el expose y el app shiffer  y podasi  como arrastrar ventanas de un escritorio a otro, entre otras cosas.
 Mi *lspci* tira:
 ```
$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
``` y el *compiz-check*:
 ```
$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation N10 Family Integrated Graphics Controller
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Another compositing manager in use. 

Would you like to know more? (Y/n) y

 The default window manager of GNOME has its own compositing manager to
 provide basic desktop effects.
 If this one is in use, Compiz will not be able to run. 

Do you want to disable GNOME's compositing manager? (Y/n) n
``` Si desactivo la compositing de Meacity todo parece estar bien, pero no cambian las cosas...
 Y por último *glxinfo | grep direct* dice:
 ```
direct rendering: Yes
``` Imagino que hay algún problema con el controlador de Intel ¿hay algo que  pueda hacer al respecto? ¿esperar? ¿o simplemente admitir que no da  para tanto?
 Muchas gracias...

---

### Post by CesarOscar on 2011-01-02
Yo tengo un problema similar, instale UNE (Ubuntu Netbook Edition), me gusto la interfaz pero prefiero UDE por compiz-fusion. Me paso lo mismo en que ni metacity ni compiz me funcionan por default al iniciar sesion, inicia con mutter como window manager que impide los efectos de metacity, compiz, emerald, etc.

La solucion (temporal espero) la encontre en compiz-fusion icon, que me permite cambiar facilmente el window manager, especialmente porque compiz --replace me resulta en error. Tengo que hacerlo dos veces antes de que funcione. 

Espero que te sirva de algo

PD: que bueno es ver a un hispano parlante por aqui :)

---

### Post by marcelo_bur on 2011-01-03
Hola Cesar Oscar. Yo en verdad no puedo ayudarlos mucho en este tema, soy bastante nuevo en Ubuntu y nunca me preocupó la apariencia, solo me interesa que funcionen bien las aplicaciones.
En fin, el comentario que quiero hacerte es que no es extraño que encuentres hispano parlantes por aqui, este es el foro de Argentina.
Saludos.

---

### Post by daggaz on 2011-01-03
Hola Cesar 
Puedes cambiar el gestor de ventanas y el decorador desde el «gestor de aplicaciones al inicio» si no mal recuerdo (está en el menú de Sistema/Preferencias)... Desactiva Mutter y activa Metacity o Compiz.
El problema para mí, más bien es que no puedo iniciar ni Compiz ni los efectos de Metacity por que mi tarjeta de gráficos no está siendo reconocida por Ubuntu, muy posiblemente a causa de que no existe un controlador específico para dicha tarjeta, o al menos eso es lo que yo he entendido.
Lo que pudo hacer hasta el momento fue dejar a Metacity como mi gestor y activar el Composite, que al menos hace que existan sombras y transparencias.

En cuanto a lo de habla hispana, hay muchísimos foros en internet de hispanohablantes usuarios de Linux, cada país hispanohablante tiene al menos una comunidad virtual por cada distribución. Aunque hay algunos foros mucho más poblados de respuestas que otros... Pero bueno, esos son otros temas para otros foros.

...Estoy de acuerdo con marcelo_bur, lo importante es que las cosas funcionen bien antes que se vean muy bien... Pero bueno, soy un amante de lo que se ve bien, así que si existe la posibilidad ¿por qué no intentarlo? al fin de cuentas, es una de las mayores críticas al software libre, el hecho de que no se de le tanta importancia a la estética y facilidad de uso para el usuario lego... 
Y bueno, hay ejemplos de sobra de un mal diseño y ejemplos de sobra de buenos, y a mi, el escritorio Gnome con una buena combinación de Compiz me resultan muy agradables, y no solo por lo bonito, si no por que te puede hacer la vida más fácil. Por ejemplo, el monitor de mi netbook es diminuto y hay ventanas que se salen del escritorio y los botones de «OK» ya no están... Si tuviera Compiz, sería cosa de ir al escritorio de abajo y pulsar el botón, pues los escritorios se continúan en los bordes con los otros, cosa que no pasa ahora :/
Por poner un ejemplo más y para despedirme por ahora, soy una persona que maneja varias aplicaciones al mismo tiempo, y alguna funciones de selección de ventanas y escritorios con atajos en el teclado de Compiz son incluso mejores que las incluidas en el OSX, cosa que me facilita mucho el trabajo y me ahorro muchos clicks o tabs...

En fin, seguiré esperando, quizás en alguna de estas actualizaciones aparezca un controlador para mi tarjeta, pues parece no haber otra respuesta.

Gracias.

---

