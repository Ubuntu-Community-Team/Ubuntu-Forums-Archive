---
title: "Problemas driver para Realtek 8187L"
date: 2009-12-26
forum: Hardware
---

### Post by madbyte on 2009-12-26
Buenas,

Tengo un molesto problema con mi conexion WiFi, ya que no puedo tener una navegación fluida en internet, se me corta y tengo que estar reconectando constantemente, a veces no puedo ni terminar de cargar una pagina completa. No es problema de intensidad de señal ya que el indicador me muestra un 3/4 de nivel. Mi una placa es una WiFi USB con chipset 8187L de Realtek que viene con las Asus P5W DH. Me baje el driver desde el sitio oficial, el rtl8187L_linux_26.1038.0626.2009, pero cuando intento compilar me da errores y no se como seguir adelante:

[I]make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/ramiro/Escritorio/rtl8187L/ieee80211/ieee80211_module.o
/home/ramiro/Escritorio/rtl8187L/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/ramiro/Escritorio/rtl8187L/ieee80211/ieee80211_module.c:123: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/ramiro/Escritorio/rtl8187L/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/ramiro/Escritorio/rtl8187L/ieee80211] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2
ramiro@ramiro-desktop:~/Escritorio/rtl8187L$ 
[/I]
Alguna ayuda para un alma en pena??

---

### Post by guillermolisi on 2009-12-26
Ya leiste [este thread]("http://ubuntuforums.org/showthread.php?t=1065698") ?

---

### Post by madbyte on 2009-12-27
Si lo habia leido, pero como no puedo compilar el driver no puedo hacer mucho. Envié un mail al soporte de Realtek a ver que me dicen. No quiero andar tocando mucho primero voy a intentar a ver si puedo compilar sin errores y si no bue... tendre que meter mano...

---

### Post by guillermolisi on 2009-12-28
Aun te queda la alternativa de usar ndiswrapper con los drivers para Win.

---

### Post by luks911 on 2009-12-28
> **madbyte said:**
> Buenas,

Tengo un molesto problema con mi conexion WiFi, ya que no puedo tener una navegación fluida en internet, se me corta y tengo que estar reconectando constantemente, a veces no puedo ni terminar de cargar una pagina completa. No es problema de intensidad de señal ya que el indicador me muestra un 3/4 de nivel. Mi una placa es una WiFi USB con chipset 8187L de Realtek que viene con las Asus P5W DH. Me baje el driver desde el sitio oficial, el rtl8187L_linux_26.1038.0626.2009, pero cuando intento compilar me da errores y no se como seguir adelante:

[I]make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/ramiro/Escritorio/rtl8187L/ieee80211/ieee80211_module.o
/home/ramiro/Escritorio/rtl8187L/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/ramiro/Escritorio/rtl8187L/ieee80211/ieee80211_module.c:123: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/ramiro/Escritorio/rtl8187L/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/ramiro/Escritorio/rtl8187L/ieee80211] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2
ramiro@ramiro-desktop:~/Escritorio/rtl8187L$ 
[/I]
Alguna ayuda para un alma en pena??

Es un problema ente el kernel 2.6.31 y el driver. No vas a poder compilarlo hasta que alguien que sepa lo arregle. Mientras tanto, te queda ndiswrapper.

---

### Post by madbyte on 2009-12-29
> **luks911 said:**
> Es un problema ente el kernel 2.6.31 y el driver. No vas a poder compilarlo hasta que alguien que sepa lo arregle. Mientras tanto, te queda ndiswrapper.

Hola, gracias por responder, me podrias aclarar que quieres decir con *'hasta que alguien que sepa lo arregle'* ¿Es un problema dificil de resolver, sin embargo no imposible, pero que escapa a mis escasos/nulos conocimientos en linux? O ¿Es un problema del driver de Realtek, o un bug, que por el momento no tiene solución? 

Si, despues de andar leyendo varios posts, y sumando las sugerencias tuya y de guillermolisi, gano el ndiswrapper como la mejor solucion alternativa. 

Dentro de unos dias posteo comentando los resultados.

Saludos

---

### Post by luks911 on 2009-12-29
Quiero decir que yo tampoco tengo idea de cómo arreglarlo. Habría que modificar el driver o el kernel. Vi por ahí un parche para el driver pero 1) no sé aplicarlo y 2) también leí que no funcionaba.
Espero que con ndiswrapper vaya bien y cualquier cosa avisá.

---

### Post by madbyte on 2010-01-06
Bien, vuelvo a actualizar el post. 
Instale el ndiswrapper, instale el driver segui unos pasos, reinicie y no tenia conexion inhalambrica, vuelvo a reiniciar, y se me cuelga en la pantalla de ingreso de la contraseña, vuelvo a reiniciar, pantalla negra, vuelta de nuevo a reiniciar entra pero no se terminan de cargar todos los iconos, faltaban algunos del escritorio y de la barra de tareas, intento remover el driver con sudo pero es como que se cuelga y no me deja ingresar la contraseña del comando y cuando reinicio me dice que no responde el File Manager... :(

Estos son los pasos que segui:

   [FONT=Arial][I][SIZE=2]ramiro@ramiro-desktop:~$ ndiswrapper -l
ramiro@ramiro-desktop:~$ 
ramiro@ramiro-desktop:~$ cd Escritorio
ramiro@ramiro-desktop:~/Escritorio$ cd WinX64
ramiro@ramiro-desktop:~/Escritorio/WinX64$ sudo ndiswrapper -i Netrtuw_x64.inf
installing netrtuw_x64 ...
ramiro@ramiro-desktop:~/Escritorio/WinX64$ ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

ramiro@ramiro-desktop:~/Escritorio/WinX64$ sudo ndiswrapper -mi
module configuration information is stored in /etc/modprobe.d/ndiswrapper
ramiro@ramiro-desktop:~/Escritorio/WinX64$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper
ramiro@ramiro-desktop:~/Escritorio/WinX64$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
ramiro@ramiro-desktop:~/Escritorio/WinX64$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netrtuw_x64 : driver installed
      device (0BDA:8187) present (alternate driver: rtl8187)
ramiro@ramiro-desktop:~/Escritorio/WinX64$[/SIZE][SIZE=2]
[/SIZE][/I][/FONT] [FONT=&quot]
[/FONT]

---

### Post by guillermolisi on 2010-01-06
MadByte, estas corriendo Ubuntu 64 bits ? 

Me da la impresion que el driver para Win de la placa que estas usando es para 64 bits, por lo menos eso pareceria indicar el nombre del archivo [FONT=Arial][I][SIZE=2]Netrtuw_x64.inf

[/SIZE][/I][SIZE=2]Habria que confirmar si es un driver para 64 bits o no.[/SIZE][I][SIZE=2]
[/SIZE][/I][/FONT]

---

### Post by madbyte on 2010-01-06
asi es tengo Ubuntu 9.10 64 Bits

---

### Post by luks911 on 2010-01-07
Por un lado, miraría los logs a ver a si aparece el motivo del cuelgue. Y por otro, probaría poniendo en blacklist el driver nativo que no vas a usar: rtl8187. Para eso:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

y al final del archivo agregás

```
blacklist rtl8187
```

No estoy seguro pero puede haber un conflicto entre ambos drivers.

---

### Post by madbyte on 2010-01-07
Cada vez que desde la terminal le doy enter a un comando con sudo no hace nada se queda colgada y no me aparece la opcion de entrar la contraseña.

---

### Post by luks911 on 2010-01-07
Ya dudo de que tenga que ver con los drivers :-P pero hacé una cosa. entra en modo recovery apra poder hacer esos cambios. Cuando se incia la máquina mantené apretada la tecla Shift, eso va hacer que entres al menú del Grub, donde podés elegir el Recovery Mode. Luego, optás por que te lleve a una terminal como root (no recuerdo como la llama en inglés a la opción) y los cambios en lugar de con gedit los hacés con nano. O sea

```
nano /etc/modprobe.d/blacklist.conf
```

---

### Post by madbyte on 2010-01-07
luks911, hice lo que me sugeriste, entre en la opcion *root   drop to root shell* *promp*t, y cuando ejecuto el gedit me sale:

*(gedit:1279): Gtk-WARNING **: cannot open display*

---

### Post by luks911 on 2010-01-07
> **madbyte said:**
> luks911, hice lo que me sugeriste, entre en la opcion *root   drop to root shell* *promp*t, y cuando ejecuto el gedit me sale:

*(gedit:1279): Gtk-WARNING **: cannot open display*

Sí, claro. Por eso te decía más arriba, je, que vas a tener que usar nano (otro editor de texto) porque gedit necesita tener gnome funcionando.

---

### Post by madbyte on 2010-01-07
uupppsss q bolu... bue asi se aprende... jeje ok ya intento d nuevo

---

### Post by madbyte on 2010-01-07
Bien, agregue el driver, reinicie y me aparecieron los iconos que me faltaban en la barra de tareas, siguen sin aparecer los del escritorio y sigo sin poder ingresar la contraseña a sudo desde la terminal. Al reiniciar me salio de nuevo que no responde el File Manager.
Podria poner en blacklist al ndiswrapper??

---

### Post by luks911 on 2010-01-07
Podés probar, pero para mí está pasando otra cosa. Si hay conflicto entre los drivers puede que no inicie o que no funcione el wifi, pero no creo que tengas los problemas que estás teniendo. Claro que me puedo equivocar.
¿Cuál es el error específico que devuelve sobre el file manager?

---

### Post by madbyte on 2010-01-08
Agregue al blacklist el ndiswrapper y sigue todo igual.

No me tira un error, cuando intento reiniciar se me abre una ventana indicando 'File Manager' abajo 'no responde' mas abajo 'Esperando a que finalice el programa...' y tres opciones: 'Bloquear Pantalla', 'Cancelar' o 'Reiniciar de todas formas'. Intente hacer una captura de la pantalla pero no pude guardarla. 

Antes de instalar el ndiswrapper hice una actualizacion con el Gestor, hacia mucho que no actualizaba y me salio una larga lista, eso incluyo tambien un nuevo driver para la placa de video puede ser que sea eso??? Tengo una nVidia 250 GTS. Cuando termino la actualizacion me pidio reiniciar, y quedo todo ok, y de ahi arranque con lo del ndiswrapper.

---

### Post by luks911 on 2010-01-08
Cosas que se me ocurren:
1) ¿El mensaje de que el file manager no responde apareece al iniciar? Cuando aparezca probá de ir a una terminal y ejecutar ```
killall nautilus
``` copia acá si aparece algún mensaje. Eso debería matar al nautilus y, en condiciones normales, trataría de iniciarse de nuevo.
2) Mové la configuración de nautilus con
```
mv .nautilus .nautilus_backup
``` y reinicia.
Así podés probar si hay algo en la configuración provocando eso. Si no es eso, hacés el camino inverso 
```
mv .nautilus_backup .nautilus
``` y le decís que reemplace los archivos. Si no te deja llegar a una teminal también lo podés hacer desde el recovery mode, pero teniendo en cuenta que la ruta es 
/home/tu_usuario/.nautilus
3) ¿Cuál es la salida del comando```
df -h
```? Eso muestra el espacio libre en disco.

---

### Post by guillermolisi on 2010-01-08
> **madbyte said:**
> Agregue al blacklist el ndiswrapper y sigue todo igual.

Lo que hay que agregar a la blacklist no es ndiswrapper sino el driver nativo para la placa en cuestion.

---

### Post by luks911 on 2010-01-08
> **guillermolisi said:**
> Lo que hay que agregar a la blacklist no es ndiswrapper sino el driver nativo para la placa en cuestion.

Sí, primero agregó el driver nativo y tuvo el mismo resultado. ¿Alguna idea? Porque me cuesta encontrar la relación entre lo que pasa y el wifi.

---

### Post by guillermolisi on 2010-01-08
> **luks911 said:**
> Sí, primero agregó el driver nativo y tuvo el mismo resultado. ¿Alguna idea? Porque me cuesta encontrar la relación entre lo que pasa y el wifi.
He leido threads de la seccion general del foro (en Ingles) para esta placa y hay gente que logro hacerla funcionar con drivers nativos pero con resultados no muy satisfactorios, particularmente porque se quejan del pobre rendimiento/alcance de la antena. Otros aplicaron la solucion de ndiswrapper y funciono perfecto, pero si no recuerdo mal, en general son casos en que usaban 32 bits, por lo menos para los drivers.

---

### Post by madbyte on 2010-01-08
> **luks911 said:**
> Cosas que se me ocurren:
1) ¿El mensaje de que el file manager no responde apareece al iniciar? Cuando aparezca probá de ir a una terminal y ejecutar ```
killall nautilus
``` copia acá si aparece algún mensaje. Eso debería matar al nautilus y, en condiciones normales, trataría de iniciarse de nuevo. 

El mensaje me aparece cuando reinicio. Mate el proceso pero no cambio en nada.

> **luks911 said:**
> 
2) Mové la configuración de nautilus con
```
mv .nautilus .nautilus_backup
``` y reinicia.
Así podés probar si hay algo en la configuración provocando eso. Si no es eso, hacés el camino inverso 
```
mv .nautilus_backup .nautilus
``` y le decís que reemplace los archivos. Si no te deja llegar a una teminal también lo podés hacer desde el recovery mode, pero teniendo en cuenta que la ruta es 
/home/tu_usuario/.nautilus

Al reinciar me aparecieron en el escritorio los iconos de carpetas, y de unos rar, pero me faltan iconos de unos pdf 

> **luks911 said:**
> 
3) ¿Cuál es la salida del comando```
df -h
```? Eso muestra el espacio libre en disco.

Pude guardar un screenshot:

[[IMG]http://img690.imageshack.us/img690/6663/pantallazo1ko.th.jpg[/IMG]]("http://img690.imageshack.us/i/pantallazo1ko.jpg/")

Una pregunta... ¿¿¿¿Que son esos 3 Gigas????

Marque con un recuadro rojo donde deberia aparecer un applet que en unas ventanitas me indican actividad de la red, uso del disco y si mal no recuerdo la otra era uso del procesador.

Una cosa que me pasa a veces:
Cuando reinicia me aparece la primera pantalla con el logo de ubuntu en blanco en el  centro y despues me sale al TTY1 y se queda ahi con unos mensajes como:

[XX.XXXXX] evbug.c: Event. Dev: input3; Type: 4, Code:4 Value: 458792

---

### Post by luks911 on 2010-01-08
Lo que hace que veas íconos/archivos en tu escritorio es nautilus. Si lo matás, desaparecen. O sea, están en la carpeta Escritorio, pero dejás de verlos.

Cuando moviste la configuración y reiniciaste, más allá de los cambios que notaste, ¿seguías teniendo el error al inicio de que no responde? Si es así, probá de ejecutarlo en una terminal a ver si devuelve algún error.

Con respecto al espacio, podría haber más libre en / pero no parece ser ese el problema. Podés liberar un poco con 
```
sudo apt-get clean
```
para borrar paquetes descargados y ya instalados. 
No sé qué son los 3GB, pero debe ser normal. Yo tengo 1,5 y con los mismos porcentajes de uso en esos ítems.

Sobre esto
> [XX.XXXXX] evbug.c: Event. Dev: input3; Type: 4, Code:4 Value: 458792encontré este[0] link y este[1] otro link, en definitiva sugieren lo mismo: poner en blacklist el módulo evbug. Tampoco creo que sea culpable de lo que pasa con nautilus.

Finalmente, para despejar dudas sobre lo que planteaba Guillermo más arriba y si no lo hiciste, ¿si ponés en blacklist tanto el driver nativo de wifi como ndiswrapper continúa el problema con nautilus? Si sigue, lo que haría, falto de ideas, es probar reinstalar nautilus. 

Ah, otra pregunta: instalas 9.10 de cero o actualizaste desde una versión anterior. Pregunto porque actualizando de 8.04 a 8.10 tuve unos líos en los que algunos applets dejaron de andar y se me fue todo tan al diablo que reinstalé.

[0] [http://ubuntuforums.org/showthread.php?t=1162100](http://ubuntuforums.org/showthread.php?t=1162100)
[1] [http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=3168&start=0&postdays=0&postorder=asc&highlight=](http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=3168&start=0&postdays=0&postorder=asc&highlight=)

---

### Post by madbyte on 2010-01-12
hola, si tengo el rtl8187 en el blacklist, agregue el evbug y todo lo que probe no sirvio de nada y sigue igual y.... me canse... asi que creo que va cepillada, lamento perder algunas cosas que ya tenia pero no le veo otra salida, ya que por un lado soy nuevo en esto y por el otro no puedo hacer nada ya que lo basico no anda, no puedo ingresar comandos con sudo, estoy sin internet y no puedo ni siquiera abrir carpetas que se bloquea.

Me inicie en Ubuntu con la version 9.10, asi que la instalacion fue desde cero. 

Ubuntu...  vuelta a fojas cero...  ](*,)

Te agradezco mucho por la ayuda. :D

Saludos

---

### Post by luks911 on 2010-01-12
Reinstalando también se aprende. Dale para adelante. En tu lugar, antes de instalar cualquier cosa luego de instalar, pruebo el wifi con ndiswrapper hasta que funcione, para estar seguro de que eso no sea el causante del problema, cosa que duda.
No dudes en volver a consultar.
Saludos

---

### Post by madbyte on 2010-01-12
Seeee, leccion aprendida, :-({|= hasta que no quede andando todo pichi no le instalo nada...  

Saludos

---

### Post by interaudi on 2010-02-18
Hola, exploren estas dos posibilidades. 1. Karmic no deja compilar drivers (Error2, no deja compilar, error de kernel 31), instale Linux Backports, y la navegacion es excelente. 2. Han ensayado el ultimo driver 2010 de Realtek? (Hablo en versiones no Karmic), si pueden compilarlo , ensayenlo, por comentarios he oido que da una navegacion estable, no lo he podido hacer por problemas (sin navegacion), y me cuentan su experiencia. 3. Ultima opcion: Compat wireless. Ya la probe, es buena, algo inestable la navegacion (escoger drivers mac para navegacion, drivers ieee para inyeccion, no usar juntos: kermel panic). Siempre uso WICD, con iwconfig wlan0 rate 5.5M fixed, espero sus opiniones. Gracias

---

### Post by guillermolisi on 2010-04-29
Acabo de verificar que en una notebook cuyo WiFi es un USB Realtek 8187L usando la 10.04 RC actualizada al dia comenzo a funcionar. Hasta anteayer no logre nunca que se encendiera y conectara y los drivers disponibles de Realtek no compilan en esa version de Ubuntu.

El driver en uso es el rtl8187.

---

### Post by alfplayer on 2010-04-29
> **guillermolisi said:**
> Acabo de verificar que en una notebook cuyo WiFi es un USB Realtek 8187L usando la 10.04 RC actualizada al dia comenzo a funcionar. Hasta anteayer no logre nunca que se encendiera y conectara y los drivers disponibles de Realtek no compilan en esa version de Ubuntu.

El driver en uso es el rtl8187.

Yo tengo unos adaptadores USB que usan ese integrado. Probé uno con Lucid y funcionó sin ningún problema de configuración para navegar. Como no pude probarlos por tiempo extendido no puedo decir que es estable.

---

### Post by madbyte on 2010-08-27
Cuento el final de esta historia. 

Después de meses usando y probando Ubuntu pude comprobar que el enlace se vuelve inestable e intermitente cuando la intensidad de la señal cae por debajo del 70% y se corta definitivamente por debajo del 65%. A veces tenía que hacer malabares orientando la antena para obtener más del 70% de señal. 

Luego de poner en blacklist al rtl8187:

El driver que se ofrece en el sitio de Realtek tampoco me sirvió. Luego de compilarlo e instalarlo, en el momento en que se establecía la conexión la pc se colgaba. 

El ndiswrapper con el driver para 64 bits tampoco funciona (tenía la 10.04 64 bits)

No quería abandonar Ubuntu así que probé con la ultima opción que me quedaba: Ubuntu 32 bits con ndiswrapper. Esa fue la única combinación que logro hacer funcionar el rtl8187 con cualquier intensidad de señal sin problemas. Me quedé sin 64 bits y sin poder sacar provecho a los 6 Gigas de RAM aunque por ahí lei que con un kernel PAE se logra, pero eso ya es para otro tema. 

Saludos

---

### Post by guillermolisi on 2010-08-27
Como estoy experimentando algunos modelos nuevos de dongles WiFi USB que vienen con chips recientes, casos de Linksys y Encore clase N y chips Ralink, estuve leyendo que aparentemente (aun no hice la comprobacion) estos funcionarian con el ultimo kernel (el que esta actualmente en uso con MM) 2.6.35.

Este chip del caso tambien es uno de los modelos recientes de Realtek asi que una pruebita mas, usando el kernel mencionado, creo que valdria la pena.

Y si, con el kernel PAE accedes a toda la memoria instalada con un costo imperceptible.

---

### Post by madbyte on 2010-08-27
Calculo que debe ser para el nuevo chip 8187SE pero vale la pena probar, cuando pueda me instalo la MM y les cuento como me fue.

Saludos

---

