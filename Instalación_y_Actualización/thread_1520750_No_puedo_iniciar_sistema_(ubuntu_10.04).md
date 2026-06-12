---
title: "No puedo iniciar sistema (ubuntu 10.04)"
date: 2010-06-29
forum: Instalación y Actualización
---

### Post by Cholon on 2010-06-29
Mi problema es que acabo de instalar ubuntu (lo instale sin desintalar windows)y al iniciar sesion la primera ves despues de instalarlo me salia un error(no recuerdo cual) despues me salia el inicio de sesion pero con un fondo negro y un error en la esquina relacionado con el gestor de energia, al colocar la contraseña se ponia la pantalla negra y volvia denuevo a pedirmela como si no se la hubiese dado .................................................................al tratar otra ves de iniciar sesion reiniciando el pc ya no llega al inicio de sesion si no que me sale la pantalla negra como chekeando cosas y se queda pegado en cheking battery state ............................................................tambien al ingresar en modo recuperacion me sale el siguiente mensaje...........................................................-bash: no se puede crear un fichero temporal para el documento aqui: No hay espacio libre en el dispositivo................................................aunque nose si eso algo tenga que ver...............................................................................................las frases las separe con puntos por que no me pesca el espacio

---

### Post by BenjaminChile on 2010-06-30
hOLA,

SI ESTUVIERA EN TU CASO Y CON EL CD ORIGINAL DE UBUNTU 10.04, LO PONDRIA, Y LE PEDIRIA LA OPCION PROBAR cd, VERIFICARIA QUE TODO ANDA BIEN CON EL LIVE CD DE UBUNTU Y SI ME CONECTA TODOS MIS TARJETAS DE AUDIO, VIDEO, DE RED, DE WIFI SI ES UN NOTEBOOK, WEBCAM, ETC....ACCESO A INTERNET. 2DO PASO IRIA A LUGARES Y VERIFICARIA QUE VEA A MIS UNIDADES DE FILESYSTEM (CORRESPONDE A UBUNTU), CD UBUNTU, Y OTRA PARTICION ESTIMADA XNUMERO DE gb QUE CORRESPONDERIA A LA PARTICION EN QUE DEJO EL INSTALADOR DE UBUNTU A MI SISTEMA COMPARTIDO DE WINDOWS (C:).
3ERO SI VEO TODO LO ANTERIOR EN LOS LUGARES DE DISPOSITIVOS/UNIDADES (ANTES EXPUESTO) ME QUEDARIA TRANQUILO QUE AUN MI SISTEMA WINDOWS ESTA INTACTO EN MI DISCO EN OTRA PARTICION. ASI CON ESTE DISCO ORIGINAL DE UBUNTU PROCEDERIA A HACER DOBLE CLIC A LA OPCION INSTALAR QUE ME APARECE EN EL ESCRITORIO, PARA INICIAR NUEVAMENTE LOS PASOS BASICOS DE INSTALACION: LUGAR, FECHA, TECLADO...Y LLEGARIA A PARTICIONADO.

4TO AQUI ME DETENGO EN PARTICIONADO PORQUE DEBERIA DARME OPCIONES IGUAL A LA VEZ ANTERIOR, POR DEFECTO ME VA OFRECER COMPARTIR CON UNA PARTICION (NUEVA) LAS 02 YA CREADAS POR TI ANTERIORMENTE (WINDOWS+UBUNTU). NO ACEPTO ESTA OFERTA ANTERIOR Y ELIJO ESPECIFICAR EL  PARTICIONADO EN FORMA MANUAL (AVANZADO) ( AFIN DE REINSTALAR UBUNTU NUEVAMENTE SOBRE LA ANTERIOR. PARA AYUDARTE LEE PRIMERO ESTE TUTORIAL Y OBSERVA CON CUIDADO LA SITUACION 5 ([http://paraisolinux.com/instalar-ubuntu-10-04-paso-a-paso/](http://paraisolinux.com/instalar-ubuntu-10-04-paso-a-paso/)). ENTONCES CON SIGUIENTE DEBES VER UNA VENTANA DE PARTICIONADO CON TODAS LAS PARTICIONES DE TU DISCO (LA DE WINDOWS DEBE APARECER COMO FAT32 o NTFS, LAS DE UBUNTU COMO SDAXNUMERO EXT4, Y ALLLI ADENTRO DEBES DISTINGUIR 2 EXT4-HOME- (ALLI ESTA EL SISTEMA UBUNTU QUE INSTALASTE ANTES, Y SWAP (ASIGNADA A FALTA DE MEMORIA RAM COMPARTIDA). DEBES ELEGIR UNA SOLA, LA DE LINUX EXT4-HOME-, HACER UN CLIC A ESTA, LA QUE SERIA FORMATEADA NUEVAMENTE EN FORMA AUTOMATICA POR UN TICK, SINO ESTA EL TICK MARCADO, TU DEBES MARCARLO, PARA QUE BORRE LOS PROBLEMAS ANTIGUOS QUE TE DA UBUNTU Y TE REINSTALE TODO DE NUEVO EN ESE MISMO ESPACIO DE GB. SI APARECIERA LA VENTANA DE NUEVO, QUE PUEDE PASAR, SELECCIONA EN LA PRIMERA OPCION ESTE SIMBOLO \ Y EL RESTO DE LAS VENTANAS HACIA ABAJO DEJALAS IGUAL CON LA MISMA CAPACIDAD DE GB.

5TO PASO FINAL, HACER CLIC A SIGUIENTE, TE SALDRA UN MENSAJE QUE SE FORMATEARAN LOS DATOS EN LA UNIDAD DE PARTICIONADO QUE ELEGISTE, MARCA ACEPTAR O SIGUIENTE, TE PEDIRA TUS DATOS (NOMBRE, NOMBRE DEL EQUIPO, Y CONTRASENA DE USUARIO) Y AVANZA CON SIGUIENTE PARA QUE SE INICIE EL PROCESO DE FORMATEO DE LA PARTICION QUE INDICASTE (EXT4-HOME) Y LA REINSTALACION ALLI DE UBUNTU POR SEGUNDA VEZ.

6TO RECOMIENDO QUE MIENTRAS SUCEDA ESTOS TU NOTEBOOK O EQUIPO PERMANEZCA CON CORRIENTE Y CONEXCION A INTERNET PARA QUE INSTALES LOS DRIVERS O CODECS QUE SE REQUIERAN PARA EL 100% DE FUNCIONAMIENTO DE TU JOYITA, Y ADEMAS DESCARGUES LA BIBLIOTECA DE ESPANOL PARA TU UBUNTU EN FORMA COMPLETA.

BUENA PEGA TIENES POR DELANTE...SI ESTO NO RESULTA AUN EXIUSTEN OTRAS FORMAS DE INTENTAR SOLUCIONARLO, PERO SON VIA TERMINAL (NO GRAFICAS)

SALUDOS DE CHILOE

---

### Post by Carlos C on 2010-06-30
Me salta una duda, dices que instalaste Ubuntu sin desinstalar wndows, pero, ¿cómo exactamente lo hiciste? Porque es muy distinto instalar Ubuntu en una partición aparte a hacerlo desde windows, con lo que cargarías Ubuntu como si se tratara de una aplicación más del sistema Microsoft.

Saludos.

---

### Post by BenjaminChile on 2010-06-30
Mis disculpas, pero no fuiste explicito en relacion a como instalaste incialmente ubuntu junto a windows. Porque existen 02 formas, exsiste una alternativa distinta a la que te explique anteriormente de particionado donde queda en una particion windows y en otras 2 particiones linux ubuntu. Y la otra alternativa que ofrece Ubuntu desde su version Hardy Heron 8.04 es mediante la virtualizacion de WUBI una aplicacion que crea un archivoe o area virtual en tu windows como una aplicacion mas del sistema Microsoft. Wubi se encarga de instalar todo ubuntu en este archivo virtual que tu windows agrega como un programa o aplicacion en el panel de  control (o sea revisa Agregar y Quitar programas de windows: alli esta wubi ubuntu. Y desde alli lo eliminas de tu windows. Luego puedes insertar el disco de ubuntu las veces que quieras mientras estas con windows ejecutandolo y aparacera el disco de ubuntu en tu escritorio de windows con las opciones de examinar o de usar wubi para instalar ubuntu dentro de windows como ese archivo virtual. Personalmente lo probe una sola vez el 2008, y me funciono bien en un windows xp professional.  Esta guia de tuxpepino es muy buena para revisar los pasos de instalar Ubuntu mediante wubi [http://tuxpepino.wordpress.com/2008/05/19/instalar-ubuntu-desde-windows-con-wubi/](http://tuxpepino.wordpress.com/2008/05/19/instalar-ubuntu-desde-windows-con-wubi/).

Saludos de Chiloe

---

### Post by BenjaminChile on 2010-06-30
Mis disculpas, pero no fuiste explicito en relacion a como instalaste incialmente ubuntu junto a windows. Porque existen 02 formas, exsiste una alternativa distinta a la que te explique anteriormente de particionado donde queda en una particion windows y en otras 2 particiones linux ubuntu. Y la otra alternativa que ofrece Ubuntu desde su version Hardy Heron 8.04 es mediante la virtualizacion de WUBI una aplicacion que crea un archivoe o area virtual en tu windows como una aplicacion mas del sistema Microsoft. Wubi se encarga de instalar todo ubuntu en este archivo virtual que tu windows agrega como un programa o aplicacion en el panel de  control (o sea revisa Agregar y Quitar programas de windows: alli esta wubi ubuntu. Y desde alli lo eliminas de tu windows. Luego puedes insertar el disco de ubuntu las veces que quieras mientras estas con windows ejecutandolo y aparacera el disco de ubuntu en tu escritorio de windows con las opciones de examinar o de usar wubi para instalar ubuntu dentro de windows como ese archivo virtual. Personalmente lo probe una sola vez el 2008, y me funciono bien en un windows xp professional.  Esta guia de tuxpepino es muy buena para revisar los pasos de instalar Ubuntu mediante wubi [http://tuxpepino.wordpress.com/2008/05/19/instalar-ubuntu-desde-windows-con-wubi/](http://tuxpepino.wordpress.com/2008/05/19/instalar-ubuntu-desde-windows-con-wubi/).

Saludos de Chiloe

---

### Post by Cholon on 2010-07-01
si lo habia instalado con cd, hice lo que me dijiste y resulto :D:D:D:D muchas gracias , lo unico diferente que hice fue que no le puse la opcion para q copiara mis documentos en el nuevo disco, lo que ahora me doy cuenta q era innecesario x q igual tengo acceso a ellos.  el unico problema que estoy teniendo es la conexion a internet que nose que tengo q hacer para q funcione , intente abriendo las conexiones y poniendo la ip pero eran tantas opciones de cosas que no entendia xd y no supe que hacer, pero buscare informacion para solucionarlo, ahora me voy a acostar (que ya son las 4 de la mañana XD)  muchas gracias denuevo  adios

---

### Post by BenjaminChile on 2010-07-01
Hola, 
respecto a tu conexion con la internet, debes informar primero como accedes a internet, que empresa es tu proveedor, si haces una llamado o discado a la compania, o si es internet via TVbale u otro proveedor. Asi te podremos ayudar mas y mejor.
 Saludos del sur de Chiloe... Espero que el sacudon de 5,1 hoy no provoco mucho danos alla en la zona central, amigo.

---

### Post by Cholon on 2010-07-02
nose porque no me funciono la conexion al comienzo, (tengo banda ancha de vtr), pero mi hermano entro ayer y se pillo con que el problema se había arreglado solo xD

denuevo gracias por ayudarme

el remesón de ayer ni lo sentí , sera por la costumbre alomejor

adiós

---

### Post by mulderito on 2010-07-05
holas!! soy nuevo acá y nuevo en todo lo que es Ubuntu...instalé la versión 10.04 en mi pc, pero al parecer no reconoce la tarjeta de red ni el sonido....lo de la conex a internet me urge, tengo conexión de VTR 15 gigas, con modem motorola...ojalá me puedan ayudar, saludos!!!!

---

### Post by BenjaminChile on 2010-07-05
Hola,

puedes agregar mas detalles de como realizaste tu instalacion (compartida con otro sistema operativo, Windows por ejemplo; o fue una instalacion de Ubuntu 10.04 como unico sistema operativo formateando todo tu disco). Hiciste esta instaalcion sin porbar el live cd que te ofrece un menu incial de Probar Ubuntu y  de Instalar Ubuntu, cual elegiste ahi? Y estaba conectado a tu red cableada de VTR o posees una conexion WIFI con VTR , revisaste editar las conexions con el boton derecho sobre el icono de networkmanager al lado del indicador de energia. Pudiste acceder al escritorio de Ubuntu despues de realizar tu instalacion? etc...

Saludos de Chiloé.:)

---

### Post by asterix77 on 2010-07-06
Veamos una cosa a la vez, y ya que te urge lo de la red veamoslo primero.

Escribe lo siguiente en consola y pégalo acá.

#lspci

Pega además lo siguiente:

#ifconfig

¿te conectas por cable a tu pc (terminal rj45)? o por wifi?. Si es por este último también pega

#Iwconfig.

Describe además el cableado de tu conexión, por ejemplo yo poseo una conexión adsl de telsur, el cual me llega a través de un modem, y que este después se conecta a un router wifi. Luego a través de un cable rj45 se conecta a la placa de red de mi pc de escritorio. Tengo además un notebook que lo conecto al router a través de wifi.


Saludos

PD: algún moderador debiera mover el post y cambiarle el nombre, ya que se aparta del título el tema.

---

### Post by mulderito on 2010-07-06
> **BenjaminChile said:**
> Hola,
 
puedes agregar mas detalles de como realizaste tu instalacion (compartida con otro sistema operativo, Windows por ejemplo; o fue una instalacion de Ubuntu 10.04 como unico sistema operativo formateando todo tu disco). Hiciste esta instaalcion sin porbar el live cd que te ofrece un menu incial de Probar Ubuntu y de Instalar Ubuntu, cual elegiste ahi? Y estaba conectado a tu red cableada de VTR o posees una conexion WIFI con VTR , revisaste editar las conexions con el boton derecho sobre el icono de networkmanager al lado del indicador de energia. Pudiste acceder al escritorio de Ubuntu despues de realizar tu instalacion? etc...
 
Saludos de Chiloé.:)
 
 
MMM, a ver: 
- la instalación fue como único sistema operativo
- fue instalación directa, sin probar nada, bajé el sistema a un CD como imagen y hizo el boot desde el arranque.
- el pc está conectado a la red cableada que sale del modem wi fi de VTR.
- revisé las conexiones pero aparece red cableada desconectada.
- pude acceder al escritorio desde el primer momento...
 
Saludos y gracias!!!!

---

### Post by Carlos C on 2010-07-06
Lo lamento, pero este thread se ha desordenado demasiado. Se supone que cada consulta debe ir en un thread individual y no mezclar los temas. Por favor, todos los que consultaron en este hilo, lean esto:

[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Procedo a cerrar el thread. Quienes tengan consultas, por favor, abran un hilo en el subforo adecuado.

Saludos.

---

