---
title: "Dudas genéricas de instalación de drivers y software [primer contacto]"
date: 2009-07-15
forum: Instalación y Actualización
---

### Post by jukitx on 2009-07-15
Hola,
   
  Bueno, antes de nada aprovecho mi primer post para saludar a todo el mundo :)
   
  Antes de nada comentar que solo he trabajado con Windows con lo cual en el tema Linux estoy muy muy verde. A pesar de eso, en el pasado, ya hice algún intento con Linux (suse, redhat y otros) y al final acabé volviendo siempre a Windows porque nunca me acababa de aclarar con la instalación del hardware y el software que usaba habitualmente. El post será un poco largo porque quisiera ver si es posible aclararlo todo de una vez. Si no es posible repartiré las dudas en varios post y lo pondré en el sitio correspondiente sin problema. Sin embargo, creo que si me podéis aclarar todas las dudas que hay en este post puede ser útil a mucha gente que se encuentra en mi misma situación porque, a mi juicio, son las dudas que debe tener la mayoría de gente cuando se cambia de Windows a Linux.
   
  Bien, antes de nada quería comentar lo siguiente. Tengo una ISO creada de Windows Vista x64 y mi idea era la de instalar Ubuntu bien y luego crear una ISO para irlo usando eventualmente hasta que me acostumbre. De esta forma, cuando quiera cambiar de sistema operativo solo tengo que regenerar mi disco duro usando norton ghost. De momento prefiero no instalar los dos sistemas operativos de forma simultánea ya que tendría que hacer particiones.
   
  Actualmente ésta es la configuración del hardware de mi equipo:
   
  - Disco duro 500GB SATA con una sola partición primaria de todo el espacio para usar con el sistema operativo.
  - Disco duro de 1500GB SATA con una sola partición primaria para guardar datos y en formato NTFS. No deseo cambiar el sistema de ficheros de ésta partición por el momento.
  - Tarjeta grafica Asus Nvidia Geforce 9800GTX+ 
  - Tarjeta wifi USB con chipset realtek RTL8187L
  - Impresora multifunción con scanner Epson Stylus DX4850
  - Tarjeta de sonido Realtek integrada en placa base.
  - Tarjeta Ethernet Realtek integrada en placa base.
  - Placa Base Asus M3A78-EM. Dispone de VGA integrada pero no la uso ya que tengo una externa mejor.
  - Memoria 4GB DDR3-800MHz
  - Procesador AMD Phenom X4 9950 a 2.6GHz
  - Chipsets de placa base AMD 780G/SB700
  - Ubuntu 9.04 x64
   
  Bien antes nada, comentar que ya he instalado el Ubuntu pero al encontrarme con varios problemas de instalación de hardware he regenerado el Windows otra vez de modo que tendré que volver a instalar Ubuntu.
   
  A continuación planteo una duda de instalación de Ubuntu:
   
  1- Creo que hay que hacer como mínimo 2 particiones. Una para el SO y otra para el archivo de paginación para la memoria RAM. Así pues usaré el disco duro de 500GB para tal fin. Veo que hay varios sistemas de ficheros para formatear la partición del SO. Cuál es el mejor sistema de ficheros para Ubuntu? por qué es mejor? En la partición para la memoria RAM no me sale ningún sistema de ficheros, así que entiendo que solo hay uno. De qué tamaño tiene que ser la partición para RAM? El doble que el tamaño de mi RAM? o sea, 8GB? si pongo más es mejor? si pongo menos es peor? por qué?
   
  Una vez instalado el SO tengo que instalar los drivers. Comentar que vi que muchos drivers ya están pre-instalados sin embargo, tenía problemas con la tarjeta wifi y la tarjeta gráfica. De todas maneras lo que quería saber es como se instalan los drivers de forma general para saberlo para siempre y cada vez que me cambie el hardware no tenga problema. Además así podré poner drivers optimizados para cada cosa.
   
  Varias dudas acerca de los drivers en Linux:
   
  2- Puedo usar drivers de Windows vista x64 en Linux? De Windows vista x86 o Windows xp x86 en Linux? Tienen el mismo rendimiento que los de Linux x64 o x86 respectivamente? Si es posible hacerlo es algo muy complejo de hacer? 
   
  3- Si dispongo de drivers optimizados para Linux  pero no me especifica si son x64 o x86 puedo instalarlos indistintamente en Ubuntu x64? No es obligatorio que sean x64? Como puedo saber si un driver está optimizado para x64 o x86 en Linux? Obviamente supongo que lo ideal es que sean para Linux x64 para que sea lo más optimizado posible.
   
  4- A la hora de descargar drivers en la web del fabricante debo mirar para qué distribución de Linux son? Es decir, si pone Linux me vale tanto para Ubuntu, redhat, suse, etc.? Es que normalmente pone solo Linux y no menciona la distribución. Están igualmente optimizados?
   
  Algunas aclaraciones sobre los drivers que me he descargado:
   
  -  Dispongo de la última versión de drivers para la tarjeta grafica Nvidia optimizado para Linux x64
  - Dispongo de drivers para Linux pero no sé si son x64 o x86 de la web de Asus para los siguientes componentes: tarjeta de sonido integrada, tarjeta  Ethernet integrada y chipset de la placa base.
  - Dispongo de drivers para Linux pero no sé si son x64 o x86 de la web de realtek para la tarjeta wifi USB.
   
  5- Si no voy a usar la tarjeta grafica integrada, es necesario instalar los drivers para el chipset de la placa base? Ya sé que no es obligatorio, pero lo digo en el sentido de que el sistema tenga un mejor rendimiento. Comentar que en la web de AMD no he encontrado drivers para Linux específicamente para el chipset aunque sí para la tarjeta grafica integrada. Comentar que la grafica integrada esta dentro del mismo chipset para mi placa base, entonces de ahí la duda. En la web de Asus me salen drivers separados para Linux para la tarjeta grafica y para el chipset, por tanto debería instalar al menos el chipset no?
   
   
  Bueno, ahora voy al grano. 
   
  Dudas concretas para instalar la tarjeta grafica:
   
  Según la web de Nvidia me dice que para instalar el drivers tengo que seguir estos 3 pasos:
   
  ==================================================================
  Para descargar e instalar los controladores, siga estos pasos:
   
  PASO 1: Lea detenidamente la Licencia de software de NVIDIA.
   
  Es necesario aceptar esta licencia antes de descargar cualquier archivo.
   
  PASO 2: Descargue el archivo del controlador
  Descargue  - NVIDIA-Linux-x86_64-185.18.14-pkg2.run
   
  Usuarios de SuSE: leer las instrucciones de SuSE NVIDIA Installer HOWTO antes de descargar el controlador.
   
  PASO 3: Instale el controlador
  Escriba "sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run" para instalar el controlador y modifique el archivo archivo de configuración de X server * según corresponda. Consulte el archivo README si necesita instrucciones más detalladas. 
  ====================================================================
   
  * X server que es esto??? 
   
  Bien, de entrada intento hacer doble clic encima del archivo "NVIDIA-Linux-x86_64-185.18.14-pkg2.run" para ver si es “auto-instalable”. Me sale error y me dice que tengo que iniciar sesión como Root. Luego intento hacer lo que dice en el paso 3, o sea, abro una consola y escribo el comando:
   
  "sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run"
   
  Me sale error también, creo que es porque antes tengo que situarme previamente en el directorio donde está el archivo a ejecutar. Entonces, como se hace eso? Aunque preferiría saber cómo se instala esto sin tener que usar comandos. 
   
  6- Para instalar drivers o programas, debo crear una cuenta Root? Si lo hago sin crear una cuenta Root voy a tener problemas de éste tipo?
   
  7- Como se crea un cuenta Root de una forma rápida?
   
  Luego, para instalar la resta de componentes de hardware no veo ningún archivo que pueda ejecutar de modo que sea “auto-instalable”.
   
  8- Existe algún administrador de dispositivos para Linux? Es decir, yo selecciono la carpeta donde están los drivers y que estos se instalen solos sin que tenga que ponerme a teclear comandos.
   
  9- Si no hay administrador de dispositivos para Linux, que procedimiento GENERAL puedo usar para instalar cualquier componente de hardware sea cual sea. Es decir, lo que quiero es saber alguna forma de instalar hardware haciéndolo siempre igual y que no tenga que aprender un método especifico para cada dispositivo.
   
  10- Una vez tenga instalado todo el hardware, deberé configurar los programas que van a usar ese hardware o puedo usarlos directamente? Es decir, por ejemplo, el navegador firefox, el reproductor de música, etc.
   
  Bien, ahora algunas dudas sobre el sistema Ubuntu:
   
  11- existe algún aplicativo tipo “Windows update” que yo lo ejecute y pueda descargar actualizaciones criticas para la estabilidad del sistema? Me podéis dar la ruta de ese aplicativo para que lo ejecute de vez en cuando? Debo iniciar sesión como Root para hacerlo?
   
  12- me saldrán solo componentes del sistema operativo en el “Ubuntu update”? O también me saldrán programas generales? Por ejemplo, un reproductor de música, un visualizador de fotos, etc. Es fácil distinguirlo de la resta de componentes del sistema operativo? Es que me gustaría usar este aplicativo solo para actualizar el SO, luego, los programas que yo vaya a usar ya me los descargaré yo por mi cuenta. Pregunto esto porque me da miedo encontrarme con componentes que desconozco y que sean programas que no voy a usar y lo descargue e instale todo sin darme cuenta.
   
  12- qué es eso de compilar el núcleo del sistema? El kernel? Se hace con el “Ubuntu update”? o tengo que descargarlo de forma independiente? Hace falta instalarlo como Root? Sería el equivalente al service pack del Windows? Es mejor compilar el núcleo o reinstalar el sistema operativo completo con la última versión del kernel?
   
  13- en el tema del hardware el “Ubuntu update” detecta nuevos drivers? Es seguro que si yo tengo un hardware instalado descargado de la web del fabricante es aconsejable que me descargue el que me salga en el Ubuntu update? 
   
  14- Para instalar software general, los programas son  auto-instalables? O sea, es suficiente hacer doble clic encima del archivo descargado para instalarlo directamente y seguir los pasos? O depende del tipo de programa? 
   
  15- Cuando vaya a instalar un programa como elijo en qué ubicación del disco duro se va a instalar? O sea, en qué carpeta.
   
  16- Una vez instalado el SO en la barra de direcciones me salen cosas como /DEV y pero no me salen la dirección de las carpetas. Pero luego veo que si vas “medios de almacenamiento” (o algo así) entonces ya puedes ver el contenido del disco duro “normal”. Tenéis algún tipo de guía para que entienda un poco que son esas “direcciones”? son componentes de hardware del ordenador? O son componentes del sistema operativo? Son visibles los archivos del SO desde el explorador de carpetas del disco duro?
   
  17- Cuando instalé el SO en mi intento anterior intenté actualizar firefox como hacía con Windows pero no me salía la opción de “actualizar” en el mismo firefox. Es necesario que inicie sesión como Root para que me aparezca? O solo es posible hacerlo reinstalado todo el programa firefox? Los complementos de firefox de Windows valen igual para Linux?
   
  18- Tema de codecs para video y audio. Cuales formatos de video y audio puedo reproducir en Ubuntu? Tenéis una lista? Algún pack de codecs/contenedores recomendado? Tipo klite para Windows.
   
  19- Es necesario reiniciar el PC después de instalar programas o drivers? Es suficiente con cerrar cesión y abrir otra vez? Es igual de eficiente?
   
  20- Como se desinstala un programa? Se hacen todos igual? Hay algún aplicativo especifico donde salgan todos los programas instalados para poder desinstalarlos uno a uno?
   
  21- Como se desinstala un driver? Debo desinstalar un driver viejo si tengo una actualización? Lo digo por la tarjeta grafica ya que suelo actualizar los drivers con frecuencia.
   
  22- Como desfragmentar el disco duro?
   
  23- Puedo escribir y leer en particiones con NTFS?
   
  24- Como puedo ordenarme el “menú inicio” donde salen accesos directos a todos los programas? Es decir, crear accesos directos a los programas, crear carpetas en el menú de programas, etc.
   
  25- Si se va la luz y se me apaga el PC de golpe, en Linux, se me puede fastidiar el SO como en Windows? Supongo que es igualmente recomendable apagarlo bien, pero los daños son igualmente graves?
   
  26- Se pueden instalar programas para Windows en Linux? Como? Funcionan igual de bien? :)
   
  En fin, creo que con esto para empezar será suficiente.  Si puedo hacer todo esto el siguiente paso sería instalarme los dos SO para usarlos de forma general porque prácticamente podría hacer lo mismo que con Windows.
   
  Quiero aprender a usar Linux porque la verdad es que ya estoy harto del Windows. Tengo un ordenador potente y a pesar de que lo he instalado todo perfectamente y tengo todos los parches de seguridad tengo la sensación de tener un PC lento y muchas veces inestable.
   
  A ver si entre todos y algunos días podéis aclararme estas dudas pliz!!!!
   
  Muchas gracias de antemano!!!
   
  PD he comprimido todos los archivos de drivers en un pack .rar y lo he subido a rapidshare. Así veréis lo que tengo y creo que será más fácil. Lo podéis descargar de la siguiente dirección (son 75MB) y estad tranquilos que hay virus ni troyanos jeje :P
   
  [http://rapidshare.com/files/256130148/Linux_Drivers.rar](http://rapidshare.com/files/256130148/Linux_Drivers.rar)
   
  PD2 el tema de la impresora y algunas dudas de las interfaces graficas como el kde y todo eso lo dejaremos para otro día jeje :) aunque espero que con todas estas dudas aclaradas pueda hacerlo por mí mismo y no tenga que venir a molestar cada 2x3 :P

---

### Post by Carlos C on 2009-07-15
Hola. Voy a cerrar este post. La razón es que acumulas demasiadas preguntas en un sólo thread. La idea es plantear cada duda en un thread independiente. Por favor trata de ser lo más ordenado posible y piensa en que otros que tengan tus mismas dudas puedan dar con tu post mediante el buscador.
Antes de publicar nuevamente tus dudas te voy a pedir que busques información en internet con google. No lo digo como una forma de agredirte, solo lo digo para que en el foro plantees únicamente aquellas dudas que no has podido resolver por tu cuenta luego de buscar y leer a conciencia. Por favor lee el siguiente thread:

[http://ubuntuforums.org/showthread.php?t=1198911](http://ubuntuforums.org/showthread.php?t=1198911)

Allí encontrarás respuesta a la gran mayoría de tus dudas.
Tampoco olvides leer las normas del foro:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Saludos y gracias de antemano por tu comprensión.

---

