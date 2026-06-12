---
title: "Nuevo en ubuntu y queriando poder usar todos los botones de mi mouse Logitech MX Rev"
date: 2009-05-21
forum: Hardware
---

### Post by mar_celo on 2009-05-21
Hola a todos

Recien vengo de instalar el ubuntu 9.04 y veo que mi mouse logitech mx no tiene drivers y por lo tanto solo funciona como un mouse normal.  Realmente me gustaria poder programra los botones de costado como lo tenia en windows.  Alguno podria ayudarme tienendo en cuanta que esto de usar la linea de comandos no es muy sencillo para mi.

Muchas gracias!!!

---

### Post by luks911 on 2009-05-21
Fijate si sirve esto[0].

[0] [http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/howto_logitech_mx_revolution_on_ubuntu](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/howto_logitech_mx_revolution_on_ubuntu)

---

### Post by mar_celo on 2009-05-21
Lei un poco de lo que me mandaste y no se si es lo mismo que yo uso, yo instale el ubuntu 9.04 y hay hablan de otro ubuntu.  Ademas cuando yo miro mi [I]/etc/X11/xorg.conf yo no tengo nada de esto, ni existe la seccion

[/I]Section "ServerLayout"
	Identifier      "Default Layout"
	Screen		"Default Screen" 0 0
	Inputdevice     "Generic Keyboard"
	Inputdevice     "Configured Mouse"
	...
	Inputdevice     "My Mx Rev" "SendCoreEvents"
EndSection

---

### Post by staar on 2009-05-21
según el enlace que posteó luks, a partir de intrepid (la versión de ubuntu anterior a la actual) el sistema tiene que reconocer automáticamente al mouse con solo conectar el bluetooth usb antes de que carge el servidor gráfico, preferentemente al iniciar la pc...

estás seguro de que los botones no son detectados?, o es solo que no están configurados con ninguna acción? para estar seguros anda a Combinaciones de teclas y probá asignándole alguna acción a los botones...

sino, tenés que seguir el tuto que te pasó luks, pero salteándote la primera parte, la del xorg.conf, yendo directamente a la configuración de las hotkeys, que necesitan de la instalación de un par de programas, tenés que compilar otro para poder cambiar el tema de la rueda, etc...

sin entendés algo, no dudes en chiflar que lo vemos...

saludos

---

### Post by mar_celo on 2009-05-22
Realmente no entiendo mucho todo lo que dice que hay que hacer.  Yo te cuento que luego que instale el ubuntu y encendi la maquina por primera vez, el mouse funcionaba como un mouse normal, dos botones, pero no vi en ningun lado que haya reconocido que es un logitech mx, ademas los botones de costado no hacen nada.
Vos me decis que deberia empezar por confiugar las Xbindkeys??, lo unico como dije no entiendo realmente mucho que es lo que hay que hacer, esto de que todo lo tenga que hacer por linea de codigo no es algo que estoy habituado 
[B]
[/B]

---

### Post by luks911 on 2009-05-22
Se me ocurren dos cosas que podés más sencillas que lo del howto:

1) lo que dice staar de ir a Sistema > Preferencias > Combinaciones de teclas y ver si ahí te detcta las teclas y les podés asignar acciones.

2) probar btnx un programa con un frontend para configurar mouse como el tuyo. A partir de Jaunty está en los repositorios, así que lo instalás con un 

```
sudo aptitude install btnx 
```

O bien buscando el paquete btnx en Synaptic, tiene algunas dependencias así que no te asustes si te pide instalar otras cosas. Acá[0] está el manual del programa. 
No lo sugerí antes porque no lo sabía, ahora buscando un poco lo encontré. Cualquier cosa volvé a chiflar. Y no le temas a la linea de comandos :-P

[0] [http://www.ollisalonen.com/btnx/man/](http://www.ollisalonen.com/btnx/man/)

---

### Post by mar_celo on 2009-05-22
Mira instale lo que me dijiste y sale lo siguiente cuando termino la instalacion

Procesando disparadores para menu ...
Configurando btnx-config (0.4.9-1) ...
Configurando btnx (0.4.11-1ubuntu1) ...
Starting btnx : Button Extension - mouse button rerouter daemon
 btnx: uinput modprobed successfully.
 btnx: Could not read the config manager file: No such file or directory
Segmentation fault
btnx failed to start (error code 139) - try btnx-config

Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho

Por lo que veo hay un error, pero ni idea que hacer, intento leer lo que mandaste y realmente no esta escrito para alguien que es el 3 dia que usa linux, es como leer en chino, no intiendo un pomo que es lo que hay que hacer, ademas vi que la ultima actualisacion del manual ese fue en el 2008 y el ubunto 9.4, salio solo haces unas semanas o sea no se cuando es lo mismo o hay cambios

---

### Post by luks911 on 2009-05-22
Ok, no importa el mensaje de error. Una vez instalado, andá a Aplicaciones > Herramientas del Sistema > btnx
Con eso comenzás la configuración del programa para tu mouse. Te va a pedir tu contraseña.
Para empezar, vas  a ver la derecha un botón para detectar mouse y botones. Después sigue la etapa de configuración. Para la detección y configuración mirate los puntos 5, 6, 8 y 9 del manual[0] (no es tanto como parece).
Tené en cuenta que el programa en sí que se va a encargar de "interpretar" al mouse recién va a comenzar a funcionar tras el próximo reinicio. Aunque supongo que tras la configuración podés probarlo ejecutándolo desde terminal con ```
btnx
```

[0] [http://www.ollisalonen.com/btnx/man/](http://www.ollisalonen.com/btnx/man/)

---

### Post by mar_celo on 2009-05-23
Genial funciono, me llevo un monton de tiempo encontrarle la vuelta pero ya funcionan lso otros botonoes

Muchas gracias!!!

---

### Post by luks911 on 2009-05-23
Buenísimo, me alegro de que haya servido.

Saludos

---

