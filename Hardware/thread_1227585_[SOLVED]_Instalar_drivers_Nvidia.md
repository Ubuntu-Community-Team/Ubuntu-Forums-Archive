---
title: "[SOLVED] Instalar drivers Nvidia"
date: 2009-07-30
forum: Hardware
---

### Post by demian86 on 2009-07-30
[COLOR=Purple][B]Ante todo me presento. Demian86     xD

Recien hoy me instale Ubuntu 8.04..1 y lo eh actualizado hasta el tope.

El problema lo tengo al instalar el controlador de la Asus V9520 Video Suite que lleva un nucleo NV34B, osea una FX5200 con unos retoquesitos de fabrica.

Termino de instalar el controlador sin nigun problema (luego de luchar 1 hora con los comandos).
cuando vuelvo al escritorio engo problemas con la resolucion, y como puedo lo corrigo, ya que se me va automaticamente a 1024 x 768. cuestion que el monitor no lo soporta.

Cuando reinicio la pc directamente me salta error de X Server, algo asi. ustedes saben, recien comienso.

Entonces dispongo a recuperar el sistema, lo hago tranquilamente, pero cuando cuando quiero entrar a las configuraciones de la placa me marca como que no estuviesen instalados los controladores   U.U.

Alguna sugerencia.

Desde ya gracias por leerlo.
[/B][/COLOR]

---

### Post by Fak89 on 2009-07-30
Hola Demian, bienvenido!

El tema de los drivers es un problema para nosotros los nuevos, pero aca te paso un instalador, "Envy" es para instalar drivers de nVidia y ATI, y es realmente facil de usar.. i
Para instalar Envy pone en la terminal:

```
$ sudo apt-get update
$ sudo apt-get install envyng-core envyng-gtk
```Despues, cuando termine de instalar, ahi mismo en la terminal pone:

```
envyng -t
```Te va a dar a elegir algunas opciones, vas a la que necesites y te van a aparecer unos 4 paquetes mas o menos para diferentes versiones de la placa, tambien te dice cuales te funcionan y cual te recomienda, pone el numero del recomendado y este te va a descargar e instalar el paquete solo desde la terminal.

Despues de eso ya tenes los drivers mucho mas facil.
Espero que te resuelva el problema, un saludo.

---

### Post by demian86 on 2009-07-30
> **Fak89 said:**
> Hola Demian, bienvenido!

El tema de los drivers es un problema para nosotros los nuevos, pero aca te paso un instalador, "Envy" es para instalar drivers de nVidia y ATI, y es realmente facil de usar.. i
Para instalar Envy pone en la terminal:

```
$ sudo apt-get update
$ sudo apt-get install envyng-core envyng-gtk
```Despues, cuando termine de instalar, ahi mismo en la terminal pone:

```
envyng -t
```Te va a dar a elegir algunas opciones, vas a la que necesites y te van a aparecer unos 4 paquetes mas o menos para diferentes versiones de la placa, tambien te dice cuales te funcionan y cual te recomienda, pone el numero del recomendado y este te va a descargar e instalar el paquete solo desde la terminal.

Despues de eso ya tenes los drivers mucho mas facil.
Espero que te resuelva el problema, un saludo.
[COLOR=Purple][B]
Gracias.

Ahora pude instalarlos;

El problema ahora lo tengo con la resolucion. Lo maximo que me permite es 640x480 a 60 Hz.

Hay alguna manera de solucionar esto ?

Gracias[/B][/COLOR]

---

### Post by Fak89 on 2009-07-30
Nunca me paso, pero supongo que se puede arreglar en Sistema > Preferencias > Pantalla. Si te aparece un cartel que dice "Parece que sus controladores gráficos no permiten las extensiones necesarias...", pone en Si y en el panel podes configurar la resolución en la parte de "X Server Display Configuration".

Reinicia y a ver que pasa :)

---

### Post by demian86 on 2009-07-30
> **Fak89 said:**
> Nunca me paso, pero supongo que se puede arreglar en Sistema > Preferencias > Pantalla. Si te aparece un cartel que dice "Parece que sus controladores gráficos no permiten las extensiones necesarias...", pone en Si y en el panel podes configurar la resolución en la parte de "X Server Display Configuration".

Reinicia y a ver que pasa :)


[COLOR=Purple][B]Lamentablemente no me deja; como te comente, lo maximo es de 640 x 480

Ya revise en Nvidia X Server Settings y en Opciones de resolucion de panttla y no me deja.

Tambien verifique que no puedo habilitar los efectos visuales, asi que supongo que no tengo habilitada la aceleracion 3D

Ideas (?)
[/B][/COLOR]

---

### Post by Fak89 on 2009-07-30
Me mataste, igualmente encontre unos posts relacionados.
Te dejo los links por las dudas
[http://ubuntuforums.org/showthread.php?t=856803](http://ubuntuforums.org/showthread.php?t=856803) 
[http://ubuntuforums.org/showthread.php?t=1220598](http://ubuntuforums.org/showthread.php?t=1220598)
[http://ubuntuforums.org/showthread.php?t=1221119](http://ubuntuforums.org/showthread.php?t=1221119)
[http://ubuntuforums.org/showthread.php?t=1209929](http://ubuntuforums.org/showthread.php?t=1209929)
[http://ubuntuforums.org/showthread.php?t=1215309](http://ubuntuforums.org/showthread.php?t=1215309)

Para la aceleracion 3D, fijate si te sirve esto:
[http://www.softwarelibre.org/content/ubuntu_904_jaunty_jackalope_64_bits_habilitar_aceleraci%C3%B3n_nvidia_3d_y_activar_efectos_de_esc]("http://www.softwarelibre.org/content/ubuntu_904_jaunty_jackalope_64_bits_habilitar_aceleraci%C3%B3n_nvidia_3d_y_activar_efectos_de_esc")

y si no sirve nada de esto, creo que tendras que esperar a que responda alguien con mas conocimientos :(

---

### Post by staar on 2009-07-30
ese problema es bastante común, pasate por acá [http://ubuntuforums.org/showthread.php?t=1183319]("http://ubuntuforums.org/showthread.php?t=1183319")

saludos

---

### Post by demian86 on 2009-07-31
Ante todo, como en la **version 8.04.3 LTS** [**Hardy Heron**] no tuve forma de instalar los controladores, ya que me daba demasiados errores, decidi; y formatie.

Ahora estoy con ** 9.04** [**Juanty Jackalope**].
**[SIZE=3][B]staar**[/SIZE] gracias !!!!
[/B]

Me sirvio bastante, mas que todo para cambiarle la resolucion.

Hasta aca todo bien.

No se, pero cuando intento instalar la **version 173** del controlador de **Nvidia** empienzan los problemas, ni editando el **xorg.conf** se salva, asi que instale la **version 96** y edite el **xorg.conf** para las resoluciones.

Aca les dejo el **xorg.conf**

```

Section "Monitor"
    Identifier    "Configured Monitor"
        HorizSync       31.5 - 48.0
        VertRefresh     50.0 - 87.0
        Option          "DPMS"       
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals" "True"
    Option  "UseEdid" "False"
    Option  "MetaModes" "800x600 +0+0"
    SubSection "Display"
    Depth           24
    Modes   "800x600" "640x480"
EndSubSection 
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

Aviso que estoy utilizando un monitor** Samsung SyncMaster 3Ne** de **14"**

El unico problema que tengo ahora es que no puedo activar los efectos del escritorio.

Alguna sugerencia.

---

### Post by staar on 2009-07-31
porqué no podés instalar los drivers? que error te tira? tengo casi la misma placa y no tuve dramas para instalarlos (más allá de que la barra de progreso del 'Controladores de hardware' no anda, pero los drivers se instalan lo mismo, solo hay que esperar), y la versión 173.xx es la recomendada para la serie FX5, la 96 es para placas más viejas...

saludos

---

### Post by demian86 on 2009-07-31
> **staar said:**
> porqué no podés instalar los drivers? que error te tira? tengo casi la misma placa y no tuve dramas para instalarlos (más allá de que la barra de progreso del 'Controladores de hardware' no anda, pero los drivers se instalan lo mismo, solo hay que esperar), y la versión 173.xx es la recomendada para la serie FX5, la 96 es para placas más viejas...

saludos

Cuando instalo el 173, luego de reiniciar me salta error X server con el entorno grafico,  me dice que el kernel de los controladores no inicia, u algo asi.
Aunque entre por la consola y edite** xorg.conf** me da el mismo fallo siempre.

Recien termine de actualizar, voy a probar en instalarlo nuevamente el 173. haber si anda esta vez.

Edito:

Luego de actualizar eh podido instalar l 173 sin ningun problema.

Ahora tengo habilitado la aceleracion 3D y puedo activar los efectos graficos sin nigun problema.

Asi que ya esta solucionado.

Que algun Mod o S.Mod edite el titulo y le ponga solucionado.

Ante todo muchas gracias a **[staar]("http://ubuntuforums.org/member.php?u=695981")** y a** [Fak89]("http://ubuntuforums.org/member.php?u=876795")**

Por haberme ayudado

Saludos

---

### Post by Barasuishou on 2009-08-03
hola, yo tengo un problema al instalar los drivers de la placa de vid, también nvidia, hace un tiempo intenté 2 veces instalarlos sin exito, así que siempre dejé los que venían con ubuntu, pero hace rato los tengo y los quize actualizar(además por lo que entendí andan mejor y una vez instalados bien ya es más fácil actualizar), lo que hize fué esto

sudo /etc/init.d/gdm stop
y
sudo sh ./(mi driver que baje)

como no encontró versión para mi kernel(por lo que entiendo) compiló una, todo bien hasta ahí, después reinicié y tira error y me manda opciones si quiero en low res o consola, y un par más

como lo puedo arreglar o que me falta hacer para completar la instalación????

---

### Post by staar on 2009-08-03
es más fácil (en varios sentidos) instalar los drivers de los repositorios, que los bajados desde la página de nvidia...

simplemente ```
sudo aptitude install nvidia-glx-xx
``` substituyendo las xx por la serie del driver que corresponda a la placa (96, 173 o 185)

saludos

---

