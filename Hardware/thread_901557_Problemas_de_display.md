---
title: "Problemas de display"
date: 2008-08-26
forum: Hardware
---

### Post by Benito Camela on 2008-08-26
Hasta hoy no había instalado Ubuntu. Ya había probado la versión 7 y algo desde el CD sin ningún problema, y me había gustado.
Hace unos días descargué e instalé Ubuntu 8.04, que ya me está dando problemas de video.
Cuando probé la versión 7.xx todo lo relacionado con la salida de video andaba re bien. Pero me extrañé al ver que, cargando Ubuntu 8.04 desde el CD el display era de 640 * 480 píxeles y 60 Hz. Si cambiaba la resolución (Sistema > Preferencias > Resolución de Pantalla) a 1024 * 768, solamente cambiaba el tamaño total de la imagen de la pantalla, pero no el display; éste seguía en 640 * 480. Por ende, la imagen no entraba en la pantalla. Curiosamente podía mover el sector mostrado en la pantalla pocisionando el cursor del mouse en los bordes, como si fuese una cámara. Todavía tengo este problema.

Creo que valdría la pena saber que mi xorg.conf (en el directorio etc/X11) se muestra como si jamás hubiese sido configurado:
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
No tengo la más pálida idea de cómo instalar drivers en Ubuntu o qué tendría que hacer para configurar esto. Me adelanto: **sudo dpkg-reconfigure xserver-xorg** no funciona. Solamente me da una opción sobre algo de video (que por cierto no entiendo) con dos opciones, y ninguna arregla el problema. El resto de lo que me aparece son configuraciones del teclado.

Gracias de antemano.

---

### Post by faktorqm on 2008-08-26
si tenes video nvidia o ati, instala el envy (sistema -> administracion -> gestor de paquetes synaptics). si no, postea a ver que marca tenes y vemos como se hace. cuando terminas, podes apretar ALT + F2 y pegar: 

```
gksudo displayconfig-gtk
```

eso te configura el monitor.

consejo: usa el search (buscar en ingles), este tema se hablo 1509212342356 millones de veces....

---

### Post by Benito Camela on 2008-08-27
Mi placa de video es una S3G UniChrome Pro IGP integrada (chipset: K8M800).

---

### Post by faktorqm on 2008-08-27
ok, ejecuta el comando que te pase antes y deberias tener un driver que se llama "via" que es el que anda con ese modelo (via sigue liberando documentacion asi que si alguien sabe de otro driver mejor que avise) y configura bien las frecuencias del monitor y no deberias tener mayores problemas. (no uses el boton de test por que anda mal). Salu2!

---

### Post by Benito Camela on 2008-08-28
El driver aparecía en S3 > Unichrome, VIA no aporta drivers de video, sino S3Graphics. Y ya 'ta todo listo. Era más fácil de lo que yo creía, juajua.

Thanks!

---

### Post by guillermoezquer on 2008-08-28
hola gente yo tengo un problema similar... eh estado usando ubuntu 7.1 y no tenia problemas con mi salida de video... ahora eh pueso ubuntu 8.04 y la pantalla se ve toda raya lo q hace todo casi ilegible... mi mother es una asus p5vd2-vm con placa de video integrada... desde ya agradesco cualquier tipo de ayuda q me puedan brindar...

---

### Post by faktorqm on 2008-08-29
Ya lo conteste anteayer ese mismo problema en otro thread... lo que no me acuerdo era cual era... lo que tenes que hacer es arrancar e ir apretando CTRL + ALT + + y CTRL + ALT + - para cambiar la resolucion a tiempo real. con mas la subis, con menos la bajas, apreta tantas veces como puedas hasta que se vea algo, no importa si se ve sobredimensionado, importa que se vea, despues si posteas tu marca y modelo de placa de video vemos como hacer para instalar los drivers.

---

### Post by maleixo on 2009-05-10
Hola yo tambien soy nuevo en Ubuntu y estoy usando la última versión 9.04 y estoy presentando este mismo problema con mi tarjeta de video VIA/S3G Unichrome Pro IGP y ya he hecho instalaciones de varios paquetes y tambien he hecho modificaciones al xorg.conf siguiendo indicaciones de otros foros y todavia no he podido arreglar este problema por favor si me pueden ayudar con lo que puedan les agradezco y por favor sean especificos en cada paso ya que no teno mucho tiempo con ubuntu y no conozco todas sus funciones y comandos. Gracias.

---

### Post by Hei Ku on 2009-05-10
Postea el resultado de correr lspci en la terminal y el contenido de tu archivo /etc/X11/xorg.conf, a ver si podemos hacer algo. Personalmente, pienso que las placas VIA son un infierno para configurar, y una vez configuradas bien, su performance es de todas maneras pobrisima, pero vamos a hacer lo que se pueda.

---

### Post by guillermolisi on 2009-05-10
> **Benito Camela said:**
> El driver aparecía en S3 > Unichrome, VIA no aporta drivers de video, sino S3Graphics. Y ya 'ta todo listo. Era más fácil de lo que yo creía, juajua.

Thanks!
Esa placa de video, como casi todas (por ser generoso) con chipset VIA y que serian elegibles de driver OpenChrome o UniChrome, no funcionan y, en el mejor de los casos, podrias lograr aceleracion 2D cuando no una merma importante en el desempeño de la maquina.

Lamento tener que decir esto siendo usuario de dos maquinas con el mismo problema (totalmente asumido luego de quemar y quemar alternativas ademas de mis ojos leyendo toda experiencia relacionada con este tema - vas a encontrar que algunos dicen que les funciona, pero son los pocos privilegiados que confirman la regla).

El sitio OpenArena, donde se publican los drivers para VIA, apesta porque lo han hecho de compromiso, solo para cumplir.

Si queres preservar tu salud mental y disfrutar de aceleracion 3D verdadera, gastate unos mangos en una placa nVidia (no te digo ATI porque parece que aun estan algo verdes algunos de sus drivers, sino tambien podria ser una muy buena opcion).

---

### Post by maleixo on 2009-05-10
> **Hei Ku said:**
> Postea el resultado de correr lspci en la terminal y el contenido de tu archivo /etc/X11/xorg.conf, a ver si podemos hacer algo. Personalmente, pienso que las placas VIA son un infierno para configurar, y una vez configuradas bien, su performance es de todas maneras pobrisima, pero vamos a hacer lo que se pueda.

Gracias compa aqui estan los datos de lspci:

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

y aunque ya he hecho muchas modificaciones al archivo xorg.conf aqui te pongo una copia de como lo tengo actualmente:

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "openchrome"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

La verdad es que nunca habia tenido la necesidad de instalar otra tarjeta de video porque esta trabaja perfectamente en windows pero en Ubuntu si que es un problema y quisiera no tener que instalar otra porque actualmente no necesito una tarjeta de video de muchas prestaciones pero tampoco me sirve asi como está porque con solo decirte que tarda hasta 10 segundos en cargar una diapositiva con animaciones de una presentación ya te puedes dar una idea y eso desespera a cualquiera. Gracias por la ayuda.

---

### Post by guillermolisi on 2009-05-10
> **maleixo said:**
> Gracias compa aqui estan los datos de lspci:

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

y aunque ya he hecho muchas modificaciones al archivo xorg.conf aqui te pongo una copia de como lo tengo actualmente:

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "openchrome"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

La verdad es que nunca habia tenido la necesidad de instalar otra tarjeta de video porque esta trabaja perfectamente en windows pero en Ubuntu si que es un problema y quisiera no tener que instalar otra porque actualmente no necesito una tarjeta de video de muchas prestaciones pero tampoco me sirve asi como está porque con solo decirte que tarda hasta 10 segundos en cargar una diapositiva con animaciones de una presentación ya te puedes dar una idea y eso desespera a cualquiera. Gracias por la ayuda.
Ok. Si no tenes necesidad de aceleracion 3D entonces cambiale el driver por el VESA (que es el mas generico de todos) en lugar del openchrome.

Luego y siempre que tengas alguna cuestion con la resolucion de la pantalla, trabajando con el /etc/X11/xorg.conf podes lograr algo mas que decente y practico.

Llegue a tener resolucion de 1024x768 con VIA y driver VESA, KDE3.5.10, y monitor Samsung de 17" 794v o similar, que me permitio trabajar por mucho tiempo.

---

### Post by maleixo on 2009-05-11
Cuando dije que no necesito una tarjeta de muchas prestaciones me refería mas que todo a que yo no uso programas que exigen muchos graficos como los juegos de video actuales pero claro que necesito aceleración 3D porque ni con el openchrome ni con el vesa puedo ni siquiera activar los efectos de escritorio, que por cierto el vesa funciona peor que el openchrome, y yo necesito usar programas como el compiz y virtualbox además que también quiero realizar algunas modificaciones de apariencia. Sera que me puedes ayudar??

---

### Post by Hei Ku on 2009-05-11
Con el driver de openchrome, una vez que ingresaste, pone esto en la terminal:

glxinfo | grep rendering

glxingo | grep vendor

Postea los dos resultados, a ver qué te tira, y de ahí seguimos.

---

### Post by guillermolisi on 2009-05-11
> **maleixo said:**
> Cuando dije que no necesito una tarjeta de muchas prestaciones me refería mas que todo a que yo no uso programas que exigen muchos graficos como los juegos de video actuales pero claro que necesito aceleración 3D porque ni con el openchrome ni con el vesa puedo ni siquiera activar los efectos de escritorio, que por cierto el vesa funciona peor que el openchrome, y yo necesito usar programas como el compiz y virtualbox además que también quiero realizar algunas modificaciones de apariencia. Sera que me puedes ayudar??
Siendo asi, entonces volvemos al principio cuando recomende agregar una placa con buen soporte desde Ubuntu (nVidia) aunque sus drivers sean propietarios, y dejar de usar la VIA integrada.

---

### Post by maleixo on 2009-05-12
> **Hei Ku said:**
> Con el driver de openchrome, una vez que ingresaste, pone esto en la terminal:

glxinfo | grep rendering

glxingo | grep vendor

Postea los dos resultados, a ver qué te tira, y de ahí seguimos.

ok los resultados de "glxinfo | grep rendering" son:

direct rendering: Yes

y de "glxinfo | grep vendor" ya que "glxingo | grep vendor" no lo reconoce como comando valido y me imagino que fue un error de tipeo, los resultados son:

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: VIA Technology

espero que esto te de una idea de como resolver, Gracias.

---

### Post by Hei Ku on 2009-05-12
> **maleixo said:**
> ok los resultados de "glxinfo | grep rendering" son:

direct rendering: Yes

y de "glxinfo | grep vendor" ya que "glxingo | grep vendor" no lo reconoce como comando valido y me imagino que fue un error de tipeo, los resultados son:

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: VIA Technology

espero que esto te de una idea de como resolver, Gracias.

Abrite una terminal, y pone: glxgears

Espera un rato y deberia empezar a imprimir un conteo de FPS. Dejalo 2 minutos y despues cerralo y postealo aca.

Me parece que esta todo instalado ok y te anda todo lo rapido que te puede andar.

---

### Post by maleixo on 2009-05-13
> **Hei Ku said:**
> Abrite una terminal, y pone: glxgears

Espera un rato y deberia empezar a imprimir un conteo de FPS. Dejalo 2 minutos y despues cerralo y postealo aca.

Me parece que esta todo instalado ok y te anda todo lo rapido que te puede andar.

OK aqui estan los resultados:

3350 frames in 5.0 seconds = 669.854 FPS
3387 frames in 5.0 seconds = 677.380 FPS
3010 frames in 5.0 seconds = 601.856 FPS
3353 frames in 5.0 seconds = 670.567 FPS
3382 frames in 5.0 seconds = 676.384 FPS
3380 frames in 5.0 seconds = 675.995 FPS
3386 frames in 5.0 seconds = 677.026 FPS
3386 frames in 5.0 seconds = 677.026 FPS
3386 frames in 5.0 seconds = 677.089 FPS
3386 frames in 5.0 seconds = 677.113 FPS
3386 frames in 5.0 seconds = 677.081 FPS
3372 frames in 5.0 seconds = 674.309 FPS
3254 frames in 5.0 seconds = 650.671 FPS
3381 frames in 5.0 seconds = 676.167 FPS
3385 frames in 5.0 seconds = 676.865 FPS
3380 frames in 5.0 seconds = 675.826 FPS
3386 frames in 5.0 seconds = 677.012 FPS
3385 frames in 5.0 seconds = 676.961 FPS
3386 frames in 5.0 seconds = 677.024 FPS
3386 frames in 5.0 seconds = 677.072 FPS
3385 frames in 5.0 seconds = 676.994 FPS
3386 frames in 5.0 seconds = 677.056 FPS
3386 frames in 5.0 seconds = 677.107 FPS
3355 frames in 5.0 seconds = 670.900 FPS
3354 frames in 5.0 seconds = 670.799 FPS

la verdad no creo que eso sea lo mas rapido o acaso esta tarjeta de video no puede soportar ni siquiera los efectos de escritorios?? o correr una presentación de diapositivas sin pararse?? es más incluso cuando agarro la barra de desplazamiento con el mouse y empiezo a bajar la pagina web no puede bajar la pagina a la velocidad con que bajo la barra de desplazamiento (y no lo hago de golpe). Asi que por favor intentemos hacer algo para solucionarlo. Gracias

---

### Post by Hei Ku on 2009-05-13
Es todo lo rapido que va a andar. Desde un principio fuimos claros sobre cómo son las cosas con las placas VIA.

---

