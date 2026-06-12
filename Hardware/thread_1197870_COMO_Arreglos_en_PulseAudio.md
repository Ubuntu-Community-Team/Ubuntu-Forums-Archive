---
title: "COMO: Arreglos en PulseAudio"
date: 2009-06-26
forum: Hardware
---

### Post by pablo.s on 2009-06-26
[B][SIZE=3]COMO: Arreglos en PulseAudio + Soporte de Ecualizador del Sistema
Autor: [psyke83]("http://ubuntuforums.org/member.php?u=50843")[/SIZE][/B]

[SIZE=3]Introducción[/SIZE]

[COLOR=Red]Nota 1. Usuarios de Jaunty: Si están actualizando desde Hardy o Intrepid, les recomiendo
que sigan la guia para borrar la configuración obsoleta. Si han realizado una instalación
limpia, sigan la guia solamente si experimentan problemas.
Nota 2. Usuarios de Intrepid; debido a un bug en las librerias ALSA, su mixer PCM puede
quedar silenciado o en volumen 0 ocasionalmente. Si no pueden escuchar sonido o escuchan
solo un crujido muy suave, pasen a la Parte C, Paso 3.
Nota 3. Usuarios de OSSv4: PulseAudio no soporta OSSv4, asi que esta guia no les servirá.
Si han elegido instalar OSSv4 y tienen problemas, deben buscar soporte entre los hilos
dedicados al problema. Personalmente no recomiendo a los usuarios instalar OSSv4 debido
a problemas de compatibilidad y soporte.
Nota 4. Usuarios de Kubuntu: No sigan esta guia. PulseAudio no se utiliza en Kubuntu.[/COLOR]

PulseAudio es un servidor de sonido avanzado que ha sido incluido en Ubuntu desde el
lanzamiento de Hardy Heron (8.04). Desafortunadamente, Hardy fué lanzado con una
configuración no muy cuidada de PulseAudio, lo que ha resultado en varios problemas que
los usuarios han tenido, desde cuelgues esporadicos de Firefox hasta tener un mezclado de
sonido completamente descompuesto. En Intrepid debería funcionar por defecto, pero es
bastante posible que su configuración sea igual de descuidada que en Hardy.
Para más información, lea las FAQ abajo.

Siendo Abril de 2009, recomiendo a todos los usuarios interesados en PulseAudio que se
instalen la última versión: Jaunty Jackalope (9.04). Los desarrolladores de Ubuntu han
realizado un trabajo excelente con la integración y configuración de PulseAudio en este
lanzamiento - suficientemente bueno cómo para hacer obsoleta esta guia.

Cuando esté listo para seguir esta guia, esto es lo que necesita saber:
Usuarios de Hardy: Sigan la Parte A + B
Usuarios de Intrepid: Sigan la Parte A + C
Usuarios de Jaunty: Sigan la parte A
Adicionalmente:
    * El Apéndice A brinda consejos generales de solución de problemas. Si usted tiene
    algún problema, debería comenzar por ahi.
    * El Apéndice B brinda información útil  de las caracteristicas más avanzadas y técnicas
    de PulseAudio.
    * El Apéndice C Brnda información sobre cómo configurar correctamente aplicaciones
    específicas que por defecto puede que no funcionen bien con PulseAudio, incluyendo a
    WINE, Skype y todas las aplicaciones que utilizan OSS.
    * El Apéndice D le mostrará cómo habilitar la ecualización de audio para TODAS las
    aplicaciones de su sistema. Esto es especialmente útil para los usuarios de notebooks
    que tienen pobre calidad de audio con los parlantes incorporados. 

**[SIZE=3]FAQ - Preguntas Frecuentes[/SIZE]**
Las consultas más comunes se responden aqui.

**P: ¿Que es exactamente PulseAudio?**
R: PulseAudio es un servidor de sonido para sistemas POSIX y Win32. Un servidor de sonido
es basicamente un intermediario para sus aplicaciones de sonido. Le permite realizar operaciones
avanzadas en sus datos de sonido mientras pasa entre la aplicación y el hardware. Cosas como
transferir el audio a una máquina diferente, cambiar el formato de la muestra o la cuenta de los
canales y mezclar muchos sonidos a uno solo, son facilmente conseguidas utilizando un servidor de
sonido.
Simplificando: PulseAudio es responsable de la reproducción y el mezclado de audio de su sistema.  
No es un controlador de tarjetas de sonido: de hecho funciona arriba de la Arquitectura Avanzada
de Sonido de Linux (ALSA). Al margen de todos los efectos buenisimos que provee, sirve cómo un
reemplazo para el dispositivo de mezclado virtual de sonido de ALSA (plugin Dmix), permitiendo
así compartir el acceso de la tarjeta de sonido a multiples aplicaciones. 

**P: ¿PulseAudio? Puaj ! No lo quiero en mi sistema.**
R: Bueno, Pulse Audio ya viene instalado y activado en Hardy e Intrepid por defecto; reemplaza al
deamon ESD para los sonidos del sistema y la mayoria de los programas de Ubuntu por defecto ya
lo utilizan (Totem, Rhythmbox y muchas otras aplicaciones a través de GStreamer). Aunque algunas
aplicaciones de alto perfil soportan PulseAudio de forma nativa (VLC y Mplayer), la mayoría todavía
utiliza salida por ALSA o OSS, por lo tanto no tienen soporte nativo de PulseAudio.

**P: Si PulseAudio ya viene instalado ¿para qué preciso esta guia?**
R: Aunque PulseAudio ya viene instalado por defecto desde Hardy, nos quedamos por el camino en
lo que respecta a la parte de configuración. Según Lennart Pöttering, el principal programador del
proyecto: 
"Algunas distribuciones hicieron un trabajo mejor que otras al adoptar PulseAudio. Del lado bueno
mencionaría a Mandriva, Debian y Fedora. Por el otro lado Ubuntu no hizo precisamente un trabajo
brillante. No hicieron la tarea para el hogar. Adoptar PA en una distribución es un pedazo de trabajo,
dado que se comunica con muchas cosas diferentes en muchos lugares diferentes. La integración con
otros sistemas es crucial. La información estaba disponible, en el wiki, las listas de correo  y el canal
de IRC. Pero si te unes y no frecuentas ninguno de ellos, no te enteras de nada. Para mi asombro
cuando Ubuntu adoptó PulseAudio lo lanzaron en una de sus versiones LTS, asi nomás. Me pareció
algo muy valeroso, en contraste que yo trabajo para Red Hat e incluso PulseAudio no era parte de
RHEL en ese entonces. Obtuve una gran cantidad de quejas de usuarios Ubuntu y estoy segurisimo
que la mayoria no las merecia, porque no era mi culpa."

Cuando PulseAudio se está ejecutando, requiere acceso exclusivo a su tarjeta de sonido para funcionar
correctamente porque asume la responsabilidad de mezclar los sonidos de la aplicación en lugar del
dispositivo "dmix" de ALSA. Si usted lanza una aplicación "regular" que no tiene soporte nativo de
PulseAudio, es muy probable que intente abrir el dispositivo "Dmix" y esto le va a quitar a PulseAudio
el control de la tarjeta de sonido. Para el usuario le va a parecer que el mezclado de audio entre las
aplicaciones se ha descompuesto. 
PulseAudio incluye plugins de ALSA (dentro del paquete "libasound2-plugins") cuya función es hacer
que las aplicaciones ALSA reenvien audio al servidor PulseAudio (y de esta forma evitar los problemas
descriptos antes) Desafortunadamente Hardy Heron fué lanzado sin estos plugins habilitados (ni
siquiera instalados) por defecto, lo cual causa muchos, muchos problemas de mezclado de audio a los
usuarios. Para colmo a este problema, la versión de estos plugins ALSA en los repositorios de Hardy no
funcionan correctamente, asi que hace falta instalar versiones actualizadas para que las aplicaciones
ALSA funcionen correctamente con PulseAudio. 

Al seguir esta guia, su sistema será configurado para utilizar estos plugins ALSA de PulseAudio para
los usuarios de Hardy (y las versiones actualizadas de los paquetes necesarios de mi PPA). Aunque
Intrepid tiene esos plugins instalados y configurados por defecto, seguir esta guia todavia es útilisimo
porque a) usted se asegura de tener una configuración limpia de PulseAudio y b) usted va a obtener
el conocimento del funcionamiento de PulseAudio. 

[B]P: Me alegra saber que este problema está arreglado en Intrepid, pero por qué rayos y centellas no
no arreglaron en Hardy todavía?[/B]
R: La respuesta más simple a esta pregunta es: complejidad. Hardy es un lanzamiento que tiene LTS
(Soporte de Período Extendido) y hay una política muy estricta sobre las actualizaciones. Para arreglar
Hardy, muchos componentes requieren actualizaciones y cambios, que incluyen libflashsupport, ia32-libs,
pulseaudio, libasound2, libasound2-plugins, flashplugin-nonfree, nspluginwrapper...
Hasta el último momento del ciclo de desarrollo de Hardy, los plugins ALSA de PulseAudio no estaban
funcionando correctamente y Flash 9 no funcionaría sin la "maléfica" libreria libflashsupport (digo
maléfica porque causaba cuelgues al azar muy frecuentemente en Firefox), asi que no era posible probar
los cambios necesarios antes del lanzamiento final. Ahora si es posible, pero tomaría un esfuerzo terrible
revisar y aplicar estos cambios.

**P: He seguido tu guia y PulseAudio todavia no funciona!**
Q: Fijese en el Apéndice A y deme la información requerida en tu post.
(Nota: Este post es una traducción. No aplica al 100% del original, pero haremos lo posible por ayudar).
[B]
P: No puedo hacer que Skype/WINE/etc. funcione correctamente con PulseAudio, que puedo hacer ?[/B]
R: Algunas aplicaciones llevan una configuración extra, otras no funcionan con PulseAudio. Fijese en el
Apéndice C para información en aplicaciones especificas. 

**P: Donde puedo encontrar los reportes de bug relacionados con estos problemas?**
R: Si usted cliquea en el número de paso, le llevará al reporte de bug apropiado, si existe.


[SIZE=3]**PARTE A: Instrucciones Comunes (Para Hardy, Intrepid y Jaunty)**[/SIZE]
Todos los usuarios deben seguir los pasos de esta sección para obtener una configuración óptima.

1. Haga backup (y luego borre) los archivos viejos de configuración.

```
$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
```

Nota: No se preocupe si alguno de estos archivos no existen en su sistema.

2. Asegurese que tiene las librerias necesarias de PulseAudio y las utilidades de configuración.

 ```
$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
```

3. Asegurese que la maléfica libreria "libflashsupport" no esté instalada.

```
$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
```

Nota: la libreria "libflashsupport" era (y hasta cierto punto, todavia es) la causa más común de la
inestabilidad de Firefox desde que se lanzó Hardy, porque muchos usuarios habian sido mal
aconsejados al pensar que tenian que instalar esta libreria para estar tranquilos que Flash y PulseAudio
funcionarían correctamente. Si usted ve algún post que recomienda a alguien instalar esta libreria,
por favor respondale con un link a este post, o al reporte de bug. Cuanta más gente sepa de este
problema, mejor. Gracias! 

4. Abra Sistema - Preferencias - Sonido. En la sección de dispositivos, asegurese que todas las opciones
de "Reproducción de sonido" estén en Autodetectar. Ponga el item "Captura de sonido" en ALSA.
Cierre la aplicación cuando termine.
Nota: Elegir PulseAudio para captura de sonido va a causar cuelgues , asi que se le aconseja que elija
el dispositivo "directo" de ALSA.

5. Abra la aplicación de Control de Volumen de PulseAudio ("pavucontrol" o puede lanzar Aplicaciones -
Sonido y Video - Control de Volumen). En la sección Dispositivos de Salida verá una lista de los dispositivos
de reproducción disponibles en su sistema. Haga click derecho en la entrada que usted desea que sea el
dispositivo por defecto y habilite la casilla "Por defecto". También dirijase a Dispositivos de Entrada, haga
click derecho en el dispositivo que usted quiere que sea su entrada (microfono) y asegurese que la casilla
"Por defecto" esté habilitada. Cierre la aplicación cuando termine.
Nota: Si le aparece el error "Fallo de conexión: Conexión rechazada", lance manualmente PulseAudio
antes de abrir la aplicación de Control de Volumen. 

```
$ pulseaudio & pavucontrol
```

6. Continue con la PARTE B si está ejecutando Hardy o la PARTE C si está ejecutando Intrepid.
Si está ejecutando Jaunty, ya terminó. Salga de la sesión y vuelva para que se activen los cambios.

**[SIZE=3]PARTE B: Hardy Heron (8.04)[/SIZE]**

Aviso Importante: Mi PPA contiene los paquetes necesarios traidos desde Intrepid para: 
PulseAudio, ALSA, Flash 10 y nspluginwrapper. Si usted actualiza a una distribución nueva o
Hardy recibe actualizaciones oficiales para cualquiera de estos paquetes, no va a tener ningún
problema.

0. Para usuarios de 64 bits solamente: Instalen "getlibs" y algunas librerias de 32 bits extra que
son requeridas por Flash 10 y Skype para funcionar apropiadamente:

```
$ wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb && sudo dpkg -i getlibs-all.deb && rm getlibs-all.deb
$ sudo getlibs -p libnss3-1d libnspr4-0d libcurl3 libasound2-plugins
```


1. Edite su archivo /etc/apt/source.list

```
$ gksudo gedit /etc/apt/sources.list
```

Si no las tiene, añada las lineas siguientes al final del archivo y guarde:

```
# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
deb-src http://ppa.launchpad.net/psyke83/ubuntu hardy main
```

2. Añada la clave pública de mi PPA, actualice los repositorios y actualice paquetes:

```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16AE4E77 && sudo apt-get update && sudo apt-get dist-upgrade
```

3. Habilite los plugins de ALSA para PulseAudio:

```
$ asoundconf set-pulseaudio
```

Nota: Por favor espere hasta que haya actualizado los paquetes del paso previo antes de ejecutar
este comando. Mis paquetes tienen un parche para "asoundconf" para asegurarse que habilita a los
plugins de PulseAudio correctamente.

4. Salga de la sesión y vuelva para que los cambios se activen.

**[SIZE=3]PARTE C: Intrepid Ibex (8.10)[/SIZE]**
Siga los pasos que se describen en esta sección solo si está ejecutando Intrepid.
Aviso Importante: Actualmente no hay paquetes actualizados para Intrepid en mi PPA (con la
excepción de un paquete de nspluginwrapper actualizado para usuarios de i386). He decidido
mantener este paso en la guia en caso que actualice algún paquete importante que no llegue a
estar en los repositorios oficiales. Nunca actualizaré ningún paquete "riesgoso" (digamos alguno
que no haya sido testeado exhaustivamente), solo actualizaciones  que sean suficientemente
estables. 

1. Edite su archivo /etc/apt/source.list

```
$ gksudo gedit /etc/apt/sources.list
```

Si no las tiene, añada las lineas siguientes al final del archivo y guarde:

```
# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu intrepid main
deb-src http://ppa.launchpad.net/psyke83/ubuntu intrepid main
```

2. Añada la clave pública de mi PPA, actualice los repositorios y actualice paquetes:

```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16AE4E77 && sudo apt-get update && sudo apt-get dist-upgrade
```

3. Asegurese que el mezclador PCM de su tarjeta de sonido no esté silenciado o puesto
al 0% de volumen (lo que parece ser un bug en Intrepid)

```
$ alsamixer -Dhw
```

Nota: Cuando los plugins ALSA de PulseAudio están activos, usted debe especificar adrede su 
dispositivo de audio en alsamixer (marcado en azul aqui arriba), de otra forma abrirá el mezclador
de PulseAudio.

4. Salga de la sesión y vuelva para que los cambios se activen.


**[SIZE=3]Apéndice A - Solución de Problemas Generales.[/SIZE]**
En esta sección se perfilarán algunos pasos generales en la solución de problemas que usted
puede hacer para ayudar en la identificación de problemas, y la información necesaria para
ayudar con sus problemas:

1. Cierre todas las aplicaciones que puedan estar utilizando la tarjeta de sonido.
2. Abra el "Selector de Dispositivos PulseAudio" de Aplicaciones - Sonido y Video, Haga click
en el icono applet, click en "Control de Volumen", click en "Reproducción".
3. Lance la aplicación que quiere probar y permitale reproducir sonido.
4. Compruebe la pestaña de Reproducción y vea si la aplicación muestra una entrada mientras
reproduce (o debería reproducir) audio. 

Posibles resultados dentro de la pestaña de Reproducción:
1. La aplicación reproduce audio y tiene una entrada en la pestaña de Reproducción;
 - La aplicación está utilizando PulseAudio correctamente.
2. La aplicación reproduce audio y no tiene una entrada en la pestaña de Reproducción;
 - La aplicación está o accediendo directamente a la tarjeta de sonido o reproduciendo
sonido mediante el dispositivo dmix de ALSA. Esto hace que PulseAudio no trabaje bien
y causa errores de mezclado de audio.
3. La aplicación no reproduce audio y no tiene una entrada en la pestaña de Reproducción;
- La aplicación está utilizando PulseAudio pero hay un problema, como: un bug en PulseAudio,
un problema con su módulo ALSA del núcleo o las librerias, o bien el mezclador PCM/Master
está silenciado. 
4. La aplicación no reproduce audio y no tiene una entrada en la pestaña de Reproducción;
- La aplicación está tratando de acceder directamente a la tarjeta de sonido o reproducir
sonido mediante el dispositivo dmix de ALSA, pero la tarjeta ya está siendo usada. Es lo
opuesto al caso B, lo cual también causa errores de mezclado.
5.  El Control de Volumen de PulseAudio muestra el error "Fallo de Conexión: Conexión rechazada";
- El daemon de PulseAudio no se está ejecutando.
6. Otra (especifique)  

Nota: A menos que la aplicación que está probando sea incompatible con PulseAudio, usted
siempre debe esperar obtener el resultado "1" en un sistema configurado correctamente.
Si precisa de asistencia con una aplicación en particular (o no puede hacer funcionar de ninguna
manera PulseAudio), denos la siguiente información:

1. Su distribución y arquitectura.
2. Un listado de sus dispositivos de audio:
```
$ aplay -l
```
3. La salida de pulseaudio en su sistema:
```
$ pkill pulseaudio; sleep 2; pulseaudio -vv
```
4. Si está teniendo un problema con solo una aplicación, especifique el nombre y los resultados
que obtuvo de las instrucciones anteriores 


**[SIZE=3]Apéndice B: Configuración Avanzada de PulseAudio[/SIZE]**
Este apéndice explica algunas tecnicas avanzadas de las caracteristicas de PulseAudio.

**P: Donde están las utilidades de configuración de PulseAudio?**
R: Si ha seguido al dedillo esta guia, puede tener acceso a todas las utilidades con lanzar
Aplicaciones - Sonido y Video - Selector de Dsipositivos PulseAudio. El icono aparecerá en
su panel. Click derecho para ver las opciones.
Las aplicaciones principales que usted quiere revisar son el Gestor (para ver el estado actual
del servidor) y el Control de Volumen (para manipular el volumen)
Nota: No juegue con ninguna de las opciones hasta que obtenga una configuración que funcione.
De otra manera será una pesadilla el aislar su problema. 

**P: Cómo puedo saber si la aplicación está utilizando PulseAudio correctamente?**
R: La aplicación le dará un resultado "1" de la guia de solución de problemas en el Apéndice A.

**P: Cómo puedo cambiar el dispositivo de reproducción y grabación por defecto de mi sistema?**
R: Fijese en la Parte A, paso 5.

**P: Es posible cambiar a un dispositivo de reproducción y/o grabación para una aplicación sola?**
R: Si. Lance la aplicación deseada y reproduzca algún sonido (o grabe) y luego abra el Control
de Volumen de PulseAudio. Haga click en la solapa de Reproducción o Grabación y haga click
en la entrada de la aplicación que desea. Elija la opción "Mover flujo" y seleccione el dispositivo
de salida.
Nota: El nivel de volumen, preferencias de flujo (reproducción) y fuente (grabación) serán 
salvados automaticamente para cada aplicación que ejecute, asi PulseAudio puede recordar
sus preferencias. Si desea ver o borrar las preferencias, estas se guardan en el archivo
"~/.pulse/volume-restore.table".

**P: Si enchufo mis auriculares USB/Bluetooth, mis parlantes dejan de funcionar!**
R: Esto es normal, dado que PulseAudio soporta "enchufado en caliente" de dispositivos de
audio. Si enchufa un nuevo dispositivo, PulseAudio puede elegirlo como flujo por defecto.
Fijese en la Parte A, Paso 5.

**P: PulseAudio funciona correctamente, pero hay un cierto tartamudeo en mi sistema.**
    Hay algo que pueda hacer para arreglarlo?
R: Edite el archivo /etc/pulse/daemon.conf:
```
$ gksudo gedit /etc/pulse/daemon.conf
```

Encuentre las siguientes lineas (por lo general abajo)

```
default-fragments = 8
default-fragment-size-msec = 10
```

Experimente con valores diferentes para ambas entradas. No le puedo decir cuales valores
son óptimos para sus sistema, porque cada tarjeta de sonido tiene diferentes tamaños de buffer
y caracteristicas, por lo tanto haga prueba y error.
Nota 1: Debe reiniciar PulseAudio para que los cambios tengan efecto.
Nota 2: Si su sistema estaba tartamudeando in versiones anteriores a Hardy, entonces es probable
que esté sufriendo de un problema del núcleo ALSA. Esto no le va a servir. 

**P: No estoy satisfecho con la calidad de audio/ Uso del CPU de PulseAudio. Cómo cambio esto?**
R: Oficialmente, PulseAudio da una calidad de reproducción de sonido superior a ALSA por defecto,
dado que tiene un resampleador de mejor calidad. Significa también que utiliza más CPU en
comparación a ALSA, por desgracia. Si usted quiere cambiar el resampleador:
Edite /etc/pulse/daemon.conf:

```
$ gksudo gedit /etc/pulse/daemon.conf
```

Encuentre la siguiente linea:

```
resample-method = speex-float-1
```

Puede cambiar el resampleador a cualquiera de los siguientes, listados en orden descendiente, desde
la más alta calidad a la más baja calidad (por lo tanto, menor uso de CPU)

> src-sinc-best-quality, src-sinc-medium-quality, src-sinc-fastest, speex-float-{10-0}, speex-fixed-{10-0}, 
ffmpeg, src-zero-order-hold, src-linear, trivial


**[SIZE=3]Apéndice C: Guia de Compatibilidad de Aplicaciones[/SIZE]**
Este apéndice explica cómo configurar aplicaciones específicas que pueden requerir una
configuración manual para trabajar con PulseAudio.

**Aplicaciones OSS**: Necesitará lanzar la aplicación usando el envoltorio "padsp".
Para más información vea "man padsp"
**Skype:** Abra las opciones de Skype, luego vaya a Dispositivos de Audio. Necesita
colocar "Salida de Sonido" y "Timbre" en el dispositivo "pulse" y colocar "Entrada
de Sonido" a la definición de su microfono. Por ejemplo, mi propio microfono está
definido como "plughw:I82801DBICH4,0".
**WINE:** Abra la aplicación de configuración de WINE ("winecfg"). En la pestaña de
Audio, elija el controlador de ALSA y deje todo lo demás por defecto. Si el sonido
tartamudea, elija el controlador OSS, y use el envoltorio "padsp" para lanzar el
ejecutable de WINE (mediante la terminal, o edite los atajos) 


**[SIZE=3]Apéndice D: Ecualizador Amplio del Sistema[/SIZE]**
En esta sección, configuraremos PulseAudio para usar la salida ecualizada, la que es
especialmente útil para los parlantes de notebooks que tienen una respuesta de
frecuencia muy pobre. Si su sonido es "latita" o se distorsiona en rangos altos, esto
hará una mejora de la calidad de su audio.

Advertencia 1: No intente configurar la ecualización hasta que haya seguido las otras partes de
la guia y verifique que PulseAudio funciona correctamente.
Advertencia 2: La ecualización puede no funcionar en sistemas de 64 bits, dado que se precisan
librerias de 32 bits. Si no le funciona, revierta los cambios que haya realizado.
Advertencia 3: La ecualización no funciona todavia para usuarios de Jaunty, porque parece que
hay ciertos plugins LADSPA en el paquete libasound2-plugins. Ahora estoy investigando esto.

1. Instale los plugins y herramientas LADSPA:

```
$ sudo apt-get install swh-plugins ladspa-sdk
```

2. Edite ~/.asoundrc:

```
$ gedit ~/.asoundrc
```

Añada el siguiente texto al final del archivo y guarde:

```
pcm.equalized {
  type plug
  slave.pcm "equalizer";
}

pcm.equalizer {
  type ladspa

  # The output from the EQ can either go direct to a hardware device
  # (if you have a hardware mixer, e.g. SBLive/Audigy) or it can go
  # to the software mixer shown here.
  slave.pcm "plughw"
  #slave.pcm "plug:dmix"

  # Sometimes you may need to specify the path to the plugins,
  # especially if you've just installed them.  Once you've logged
  # out/restarted this shouldn't be necessary, but if you get errors
  # about being unable to find plugins, try uncommenting this.
  path "/usr/lib/ladspa"

  plugins [
    {
      label mbeq
      id 1197
      input {
       #this setting is here by example, edit to your own taste
       #bands: 50hz, 100hz, 156hz, 220hz, 311hz, 440hz, 622hz, 880hz, 
       #       1250hz, 1750hz, 2500hz, 5000hz, 10000hz, 20000hz
       #range: -70 to 30
        controls [ -1 -1 -1 -1 -5 -10 -20 -17 -12 -7 -6 -5 -5 0 0 ]
      }
    }
  ]
}

```
Nota 1: Si está utilizando Intrepid o jaunty, este archivo no existe- está bien.
Simplemente pegue en un archivo nuevo y guarde normalmente.
Nota 2: Si tiene multiples tarjetas de sonido, la sección de este texto en azul
debe ser modificada ligeramente.

3. Edite /etc/pulse/default.pa:

```
$ gksudo gedit /etc/pulse/default.pa
```

Encuentre la siguiente linea marcada en azul:

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
[COLOR=Blue]#load-module module-alsa-sink[/COLOR]
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
```

Cambie la linea en azul por la siguiente y guarde:

```
load-module module-alsa-sink device=equalized
```

Nota: Asegurese descomentar (#) al comienzo de la linea

4. Salga de la sesión y vuelva para que se efectuen los cambios.

Listo!

---

### Post by pablo.s on 2009-07-03
[COLOR=White].[/COLOR]

---

### Post by Hei Ku on 2009-07-04
Esto debería ir como tuto a la pagina. 

Guille, te copas y lo subis?

No da hacer un sticky porque es un tema especifico.
Y los mensajes vacíos, desde mi punto de vista, son spam. ;)

---

### Post by guillermolisi on 2009-07-04
Hoy lo subo en Tutoriales y mando avisos al Foro y a la Lista.

---

### Post by guillermolisi on 2009-07-06
En el siguiente link encontraran la publicacion del tutorial que dio inicio a este thread, gracias a la gentileza de su autor y al trabajo realizado por Pablo.S.

[http://ubuntu-ar.org/node/243](http://ubuntu-ar.org/node/243)

Nota: Aun falta actualizar el indice de tutoriales ... asi que no lo busquen ahi, por ahora ...

---

