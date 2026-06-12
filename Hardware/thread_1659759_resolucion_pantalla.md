---
title: "resolucion pantalla"
date: 2011-01-04
forum: Hardware
---

### Post by fguerraty on 2011-01-04
hola, recientemente adquiri un lanix Neuron PX, venia con un ubuntu bastante antiguo si mal no recuerdo era 6. algo (no muy seguro) y como me gusto bastante la rapidez d el plataforma decidi seguir con linux, lo unico que no me convencia era la resolucion de pantalla, de muy mala calidad (digo del S.O.), pues bien, instale el 10.10 esperando que la nueva version fuera mas amigable a la vista (y que para mi es super necesario, ya que hago muchas traducciones de textos en el laptop y las letras son muy difusas) pero, sigue lo mismo, he intentado cambiar el tipo de letra, negrita, mejor definida, pero nada, la calidad es tan mala que al cabo de un rato mis ojos se sienten realmente cansados, lo raro es que la calidad de videos y fotos es muy buena, nada que decir, es solo lo relacionado con el S.O. como open office, barra de tareas iconos de escritorio etc. ah ! y lo otro es que las paginas web se muestran demasiado grandes ya sea mozilla o google chrome, una suerte de revisar la web en un celular por así decir, tengo que mover las barras arriba abajo izquierda y derecha para ver el contenido completo, y si le hago y zoom out (al 75% mas menos para que la pagina se vea completa) no se distinguen las letras si no una sola mancha negra por lo cual debo hacer un zoom al 100% nuevamente para ver que dice...
ahora, la pregunta es Ubuntu es asi en su calidad grafica o algo anda mal con mi laptop? se que hay un sacrificio de algo en pro a la rapidez, pero, me parece extremadamente alto.... 

agradeceria sus comentarios, y ayuda.

---

### Post by RafaelG on 2011-01-04
Fguerraty,

He ubicado el Post en el Sub Foro adecuado. Por favor, la próxima vez que desees publicar una duda en el foro revisa el siguiente link donde explica la division que utilizamos:
[COLOR=Blue][http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)[/COLOR]

También te pido que leas las normas que intentamos aplicar en el foro para que tu experiencia en el mismo sea más efectiva:
[COLOR=Blue][http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)[/COLOR]

[SIZE=2]En referencia a tu inconveniente, podrias indicar la resolucion de tu pantalla actualmente en el OS, para eso puede ir a **sistema/preferencias/monitor.**

Favor podrias postear tu[/SIZE] [FONT=monospace][SIZE=2]:
[/SIZE][/FONT][SIZE=2]> lspciSaludos,[/SIZE]

---

### Post by fguerraty on 2011-01-04
RafaelG, primero que nada muchas gracias por ubicar el thread en el lugar correcto y por la bienvenida. revise lo que tu me dices, y lo que se lee es lo siguinte, en el monitor me dice: unknown, en resolution: 800X600 (4:3), con opcion de cambiar a 600X400(4:3), con el antiguo OS me daba la opcion de 1260X960 ahora solo esto. en el refresh rate 61hz, el boton de detect monitors no parece tener efecto alguno al presionarlo... 
oh y la otra duda que tengo es lo que me pides postear... no entendi lo del quote: lspci.... sorry soy demasiado newbie para esto creo...

---

### Post by bichopro on 2011-01-04
Me huele a que tu tarjeta es nvidia o ati por lo que necesitas instalar drivers propietarios. Es sumamente facil hacerlo. Ve a sistema y busca "controladores adicionales" y luego instala el que te diga recomendado, con eso deberia bastar

---

### Post by Maciett on 2011-01-05
fguuerraty lspci es un comando que se escribe en la consola, encuentra la consola en Aplicaciones-->Accesorios-->Terminal y tipea el comando lspci, luego presionas enter y copias acá lo que diga a continuación.

Saludos

---

### Post by asterix77 on 2011-01-05
Al ejecutar el comando lspci por consola, te va a aparecer un listado largo con las características de tu pc. Ahora si quieres depurar la salida, y ver en forma especifica la información relacionada al modelo de tu tarjeta gráfica, debes escribir en la terminal


$lspci | grep VGA


Saludos

---

### Post by RafaelG on 2011-01-05
Fguerraty;

Para que tengas una idea, necesitamos saber cual es tu tarjeta de video y con el codigo antes mencionado aparece la informacion. Determinando cual es tu tarjeta podremos orienta la ayuda para identificar si el problema esta relacionado con la tarjeta de video y si posiblemente no tienes instalados los controladores (Drivers) necesarios para que trabaje tu tarjeta de video correctamente en Ubuntu y en definitiva solucionar el inconveniente con la resolucion de tu pantalla.

Saludos,

---

### Post by fguerraty on 2011-01-06
aha! ya entendi, aqui dejo lo que me aparece, intentare hacer lo que me dice  Rafael... aqui va:

felipe@fakinlaptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
felipe@fakinlaptop:~$ 

gracias nuevamente

---

### Post by asterix77 on 2011-01-07
En el siguiente link, hay un usuario que al parecer tiene el mismo problema, con la misma tarjeta. Claro que su distro es karmic pero te puede funcionar.
 
[http://ubuntuforums.org/showthread.php?t=1364097](http://ubuntuforums.org/showthread.php?t=1364097)
 
 
Saludos y espero que te sirva

---

