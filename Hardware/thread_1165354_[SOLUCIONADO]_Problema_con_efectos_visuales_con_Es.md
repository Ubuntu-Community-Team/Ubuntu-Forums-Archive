---
title: "[SOLUCIONADO] Problema con efectos visuales con Escritorio"
date: 2009-05-20
forum: Hardware
---

### Post by RafaelG on 2009-05-20
Hola, tengo problema para activar los efectos especiales en mi escritorio ya que cuando procedo a activarlo no deja. en este momento utilizo ubuntu 9.04, en la version anterior 8.10 no presnetaba problema al activar efectos Nomal.  no se si mi tarjeta tiene capacidad para activar los efectos especiales del escritorio. dejo informacion necesaria:

eligonzalez@ubuntu:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
eligonzalez@ubuntu:~$ lsmod |grep drm
drm                   123232  3 i915
eligonzalez@ubuntu:~$ lsmod |grep agp
intel_agp              39408  1 
eligonzalez@ubuntu:~$

---

### Post by RafaelG on 2009-05-20
:)Hola, estuve Googliando y consegui  como resolver mi problema. Fue super sencillo. aca les dejo como lo hice para aquellas personas que puedan tener el mismo problema.

A diferencia de Ubuntu 8.10, en que la tarjeta gráfica Intel GM965/GL960 permitía ya tras la instalación poder activar los efectos visuales &#8220;Normal&#8221; y &#8220;Extra&#8221;, con Ubuntu 9.04 no es posible tras solamente la instalación.
 

Para poder activar entonces los efectos en Jaunty Jackalope haremos lo siguiente:
  Editamos el archivo /usr/bin/compiz como usuario con privilegios de root

**sudo gedit /usr/bin/compiz**
 

y buscamos la línea
 
**T = &#8220;$ T 8086:2 a02&#8243; # Intel GM965**
 

para que quede así
 
**# T = &#8220;$ T 8086:2 a02&#8243; # Intel GM965**
 

Luego de haber guardado los cambios en el archivo, reiniciamos las X o cerramos nuestra sesión y ya podrás activar los efectos visuales sin dificultad.

Link relacionado: [http://ubuntusur.org/?p=512&cpage=1#comment-31923](http://ubuntusur.org/?p=512&cpage=1#comment-31923)

---

### Post by Patriciologico on 2009-05-20
Solo aclarar, que ciertas Intel, vienen en lista negra de Compiz, en 9.04, por haber presentado problemas de driver, he leído al menos cuatro soluciones, que van desde volver al driver 8.10, actualizar a drivers de mejora constante (no los del repositorio oficial) editando Xorg y activando UXA, sacar la intel de la lista negra o evitar que Compiz chequee el blacklist para mas información [Acá]("http://www.google.cl/search?hl=es&q=problema%2Bintel%2Bubuntu%2B9.04&btnG=Buscar&meta=&aq=f&oq=")

---

### Post by Carlos C on 2009-05-20
Justo el otro día debí hacer eso con este modelo de tarjeta, sacarlo de la lista negra y luego activar UXA porque compiz corría muy lento. Así que RafaelG ojo con eso, que una cosa es que te permita habilitar los efecto y otra que corran bien. Si el cubo gira pesadisimo es porque necesitas habilitar UXA.

---

### Post by robertor on 2009-05-20
No sé si será la tónica, pero yo a veces he tenido problemas activando y desactivando los efectos visuales: mi problema era activandolos desde la interfaz gráfica. La forma que encontré para activarlos, era cambiando el gestor de ventanas, de la siguiente forma:
```

compiz --replace

```
Ese comando, ejecutado desde una consola (por ejemplo gnome-terminal), debiera reemplazar el actual gestor de ventanas (en ubuntu, por defecto es metacity).
Si por alguna razón, este no logra levantarse, metacity se debiera restaurar. En caso de que no, te quedarás sin gestor de ventanas, debiendo ejecutar metacity nuevamente.
Ojala eso te permita descartar el driver de video.
Saludos!
Roberto

---

### Post by RafaelG on 2009-05-21
Hola Bueno he leido y si con UXA trabajaria mucho mejor mi tarjeta, solo que no se como se Habilita.

---

### Post by Patriciologico on 2009-05-21
> **RafaelG said:**
> Hola Bueno he leido y si con UXA trabajaria mucho mejor mi tarjeta, solo que no se como se Habilita.

[Aqui la respuesta]("http://foros.ubuntu-cl.org/viewtopic.php?t=8198") 

Saludos!

---

### Post by RafaelG on 2009-05-21
Gracias Patricio, si habia leido esa pagina pero no logro saber como se abre Xorg.conf, lo he escribido en el terminal pero no aparece nada y bueno disculpa mi ignorancia pero no logro entender como se habilita UXA

---

### Post by Patriciologico on 2009-05-21
> **RafaelG said:**
> Gracias Patricio, si habia leido esa pagina pero no logro saber como se abre Xorg.conf, lo he escribido en el terminal pero no aparece nada y bueno disculpa mi ignorancia pero no logro entender como se habilita UXA
nada que disculpar, andaba yo muy apurado. Xorg.conf, es un archivo de texto que guarda la configuracion del servidor grafico, por lo tanto no es ejecutable desde consola, mas bien es editable con un editor como gedit.

Para ver el archivo abre nautilus(es el navegador de archivos) y ve a lSistema de archivos /etc/X11/ en ese directorio se encuentra el archivo xorg.conf, podras abrirlo y verlo, pero no editarlo pues en esa carpeta no tienes permisos necesarios.

Para editarlo (ahora si en un terminal) ingresa el siguiente código

```
sudo gedit /etc/X11/xorg.conf
```

Eso hace que abras el archivo con gedit (editor de textos) con poderes de superusuario.

Recuerda que un mal manejo del archivo xorg.conf, te puede dejar sin entorno grafico, por lo tanto guarda una copia de respaldo antes de editarlo.

Saludos!

---

### Post by RafaelG on 2009-05-21
Hola Bueno me fue Peor... hice lo siguiente:
 
To enable it, put this in your xorg.conf: 
 
 
Section "Device"
Identifier "Configured Video Device"
# ...
Option "AccelMethod" "uxa"
EndSection
 
reinicie y no me corre el SO, se queda en pantalla negra donde antes aparecia para introducir el usuario y la contrasena.

---

### Post by Patriciologico on 2009-05-21
No no no, lo que dice es que agregues la linea

```
Option "AccelMethod" "uxa"
```

Entre

Section "Device"

y 

EndSection

Generalmente los agregados van justo en la linea antes de EndSection.

¿Guardaste un respaldo de tu xorg.conf como te dije?

---

### Post by RafaelG on 2009-05-21
No.

---

### Post by Patriciologico on 2009-05-21
> **RafaelG said:**
> No.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

```

Ese es el xorg.conf, que trae por defecto jaunty, ingresa desde un livecd, monta el disco y reemplazas el xorg.conf por otro con este texto dentro.

Tambien puedes entrar en modo recovery y hacerlo por consola, pero creo te complicara mas.

Saludos!

---

### Post by RafaelG on 2009-05-21
Como consigo el Xorg.conf en el Livecd, como lo sustituyo por el correcto?

---

### Post by moreback on 2009-05-21
Para que Compiz no tome en cuenta la lista negra, hay que agregar la línea

```
SKIP_CHECKS=yes
```

dentro del archivo **/etc/xdg/compiz/compiz-manager**.

---

### Post by Carlos C on 2009-05-21
> **RafaelG said:**
> Como consigo el Xorg.conf en el Livecd, como lo sustituyo por el correcto?
No es necesario sustituirlo. Basta con que borres o comentes la linea que agregaste. Para eso puedes iniciar una sesión con el LiveCD. Luego debes montar tu partición. Anoté como hacerlo acá:

[http://ubuntuforums.org/showpost.php?p=7321465&postcount=19](http://ubuntuforums.org/showpost.php?p=7321465&postcount=19)

Después de que hayas montado la partición podrás ingresar a ella entrando a la carpeta en donde la montaste. Podrás hacer las modificaciones necesarias. En este caso tienes que comentar las líneas agregadas (añades el símbolo # al inicio de la linea) o las borras o reemplazas el archivo /etc/X11/xorg.conf por el que viene en el LiveCD.

Para habilitar la aceleración UXA lo mejor es que veas el hilo que creó moreback:

[http://ubuntuforums.org/showthread.php?t=1166388](http://ubuntuforums.org/showthread.php?t=1166388)

---

### Post by RafaelG on 2009-05-21
Hola Carlos bueno ya despues de haber editado el Xorg.conf sin preguntar bien como hacerlo ahora prefiero preguntar bien como solucionar el problema, disculpa mi falta de conocimiento estuve leyendo los Link que postiaste, primero que todo para tener claro cuando se refieren al Livecd se refieren al cd que grabo al momento de la instalacion, si es asi cuando lo introdusco en la unidad de cd-dvd no correo solo y al momento de abrirlo aparecen varias carpetas y documentos y el Setup de instalacion de Ubuntu 8.10 el cual solo da opcion de desinstalar Ubuntu,no se muy bien como entrar con el Livecd y hacer la respectiva particion y bueno todo lo demas. agradeciendo ante mano toda la ayuda me despido esperando una pronta respuesta.

---

### Post by Carlos C on 2009-05-21
En el fondo debes iniciar el computador con el cd en el lector. En el BIOS de tu computador debe estar habilitada la opción de que inicie desde el lector de cd. De esa manera al prender el computador este leerá el cd y te mostrará un menú. La primera opción del menú te permite probar Ubuntu sin modificar el sistema. De esa manera cargará una versión de Ubuntu que será leida desde el cd, no tu disco duro. Esa es la opción que quieres. Una vez que hayas entrado al escritorio sigues con las indicaciones que te comenté antes.
Saludos.

---

### Post by Patriciologico on 2009-05-22
Una duda, recuerdo cuando tenia problemas con Xorg entraba en modo recovery y corria 
en modo root (ya que en recovery se activa root y no se usa sudo)

```
dpkg-reconfigure xserver-xorg
```

¿Esa opción aun es valida?

---

### Post by RafaelG on 2009-05-22
Hola Carlos como se habilita la opcion de que incie el Livecd desde el lector de Cd ya que cuando lo hago no aparece ningun menu de opciones y se queda en pantalla negra al momento del Longin y con el Bio aparece las siguientes opciones:

Ubuntu 9.04
Ubuntu 9.04 (Recovery Mode)
Ubuntu 9.04
Ubuntu 9.04 (Recovery Mode)
Ubuntu 9.04 Mentes86+
Windows vista Longload

---

### Post by Patriciologico on 2009-05-22
se habilita en el menu de la bios, no desde el grub.

[Guia Ubuntu]("http://www.guia-ubuntu.org/index.php?title=Arrancar_desde_el_CD")

Saludos!

---

### Post by Carlos C on 2009-05-22
> **RafaelG said:**
> Hola Carlos como se habilita la opcion de que incie el Livecd desde el lector de Cd ya que cuando lo hago no aparece ningun menu de opciones y se queda en pantalla negra al momento del Longin y con el Bio aparece las siguientes opciones:

Ubuntu 9.04
Ubuntu 9.04 (Recovery Mode)
Ubuntu 9.04
Ubuntu 9.04 (Recovery Mode)
Ubuntu 9.04 Mentes86+
Windows vista Longload
Ese es el menú del grub. El BIOS se lee antes del grub. En él se indica, entre otras cosas, el orden en el que el equipo busca un medio para bootear. En general se entra al BIOS apretando la letra suprimir o F2, pero depende de tu computador y es algo que se indica en cuanto prendes el computador. Tienes cerca de un segundo para leer el mensaje que te indica como entrar al bios. Una vez que se carga el grub es porque pasó el momento de entrar al bios y debes itentarlo de nuevo.
Saludos.

---

### Post by RafaelG on 2009-05-22
Hola, bueno aprete F2 y efectivamente entre al BIO con el Cd en la unidad lectora pero el Cd no corrio. hay varias Opciones y pestanas en el BIO que no se como poder hacer correr el Cd, por otro lado hay alguna manera mas facil como por ejemplo entrando al Recovery mode en  Root para poder editar el xorg.conf?

---

### Post by moreback on 2009-05-22
Intenta con F12 para un menú de booteo inicial, si no te funciona no queda otra que te leas el manual de usuario que viene con tu notebook o estés atento a los mensajes que aparecen al iniciarse tu notebook.

---

### Post by RafaelG on 2009-05-22
> **moreback said:**
> Intenta con F12 para un menú de booteo inicial, si no te funciona no queda otra que te leas el manual de usuario que viene con tu notebook o estés atento a los mensajes que aparecen al iniciarse tu notebook.

Hola Si F12 Funciono y pude entrar al Cd, cuando seleciono la primera opcion del Menu que permite probar ubuntu sin modificar el sistema y seguidamente aparece una pequena Ventana que dice: 

Error al leer el Cd
    Reiniciar

cuando hago click en reiniciar vuelvo de nuevo al bio y asi a repetir de nuevo lo mismo, que puedo hacer ahora ya que no puedo ingresar en el modo de probar ubuntu si modificar el sistema desde el Liveccd.

---

### Post by Carlos C on 2009-05-22
¿Estás seguro que el cd está bueno? En el mismo menú en donde tienes la opción de probar Ubuntu sin modificar el sistema puedes escoger la opción de hacer un test al cd. Te sugiero que lo hagas para descartar esa posibilidad.

---

### Post by RafaelG on 2009-05-23
> **Carlos C said:**
> ¿Estás seguro que el cd está bueno? En el mismo menú en donde tienes la opción de probar Ubuntu sin modificar el sistema puedes escoger la opción de hacer un test al cd. Te sugiero que lo hagas para descartar esa posibilidad.


Hola... bueno el CD estaba malo asi que descargue uno nuevo y bueno hice lo que me habias mencionado para solucionar el problema y todo bien, estoy escribiendo desde Ubuntu sin problema, muchas gracias a todos los que me ayudaron  resolver el problema.

Nos vemos hasta la proxima !!

---

### Post by Patriciologico on 2009-05-23
RafaelG no sabes cuanto me alegro, justo anoche conversabamos por IRC con Carlos_C, si acaso te habiamos perjudicado en vez de ayudarte con nuestras respuestas. Y habiamos decidido que redactara un manual paso a paso para reparacion en modo recovery. Lo bueno es que ya se arreglo.

Saludos!

---

### Post by Carlos C on 2009-05-24
Uff menos mal :D

---

### Post by RafaelG on 2009-05-24
Si yo creo que seria muy bueno que preparen un Manual de HowTo Repacion en Modo Recovery  ya que puede que una persona no tenga el Livecd por X motivo. Pero tenga la oportunidad de Reparar el Sistema desde Recovery.

      bueno Muchachos muchas gracias por sus ayuda y nos vemos hasta la proxima saludoss!!!

---

### Post by Elkan76 on 2009-05-24
Respuesta atrasada

---

### Post by moreback on 2009-05-24
> **Elkan76 said:**
> Respuesta atrasada
jajaja bienvenido otra vez!):P

---

