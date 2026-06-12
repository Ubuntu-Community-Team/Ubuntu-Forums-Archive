---
title: "Instalación con UEFI"
date: 2013-05-28
forum: Hardware
---

### Post by SSNova on 2013-05-28
Hola a todos

  Hace poco adquirí una notebook dell 14Z que posee UEFI. Al tratar de bootear con un pen con ubuntu 13.04 64bits la pantalla quedaba en negro, luego de deshabilitar el UEFI pude correr sin problemas el live excepto que no me detectaba la placa wifi (me figura como dell wireless 1704)

  Mi pregunta es, puedo instalar ubuntu sin problemas y mantener el UEFI deshabilitado?

---

### Post by gmunioz on 2013-05-29
La respuesta es no.
Para instalar Ubuntu junto a windows 8 es necesario:
1- Crear una partición desde Windows, reduciendo sus particiones y dejando espacio libre, por ejemplo siguiendo esta guía:
[http://www.conecta-pc.es/windows/crear-particiones-windows-8.html](http://www.conecta-pc.es/windows/crear-particiones-windows-8.html)

2- Descargar la imagen iso de X/K/L/Ubuntu 12.10 ó superior versión de 64 bits

2- Grabar la imagen .iso, en un Dvd a baja velocidad (Imageburn, [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)) o en pendrive Usb (Universal USB Installer, [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/))

3- Desde Windows 8, ir al menú de apagado y pulsar en el botón de Reiniciar, manteniendo presionado la tecla Mayúsculas.

4- En la ventana emergente de Windows seleccionar: Resolver problemas

5- En la siguiente ventana emergente seleccionar: Configuración del firmware UEFI

6- Reiniciado el ordenador, ingresar a la Bios
Desactivar:
Secure Boot
La opción del boot que esta debajo de Secure Boot
Cambiar:
La secuencia de inicio al dispositivo que aloja X/K/L/Ubuntu 12.10 ó superior 64 bits
Guardar la configuración
Insertar el dispositivo e iniciar desde él.

7- X/K/L/Ubuntu deberá iniciar en modo EFI, con un menú diferente al usual.

8- Tanto si se inicia la instalación directamente como si se prueba el sistema y luego se inicia la instalación, al llegar a particionamiento se elige avanzado, y se crea en el espacio liberado desde Windows, las siguientes particiones:

Una de unos 250 Mb en Sistema de arranque EFI
Una de 30 Gb sistema de archivos ext4, punto de montaje /
Una de 2 Gb uso común, triple de la ram para hibernar y/o suspender sistema de intercambio, montaje por defecto
Una del espacio sobrante, sistema de archivos ext4, punto de montaje /home

El Grub en la partición asignada a /

9 -Al reiniciar, luego de terminada la instalación entrara automáticamente a Ubuntu y no habrá acceso para Windows, es necesario instalar Boot-Repair
Se abre una terminal y se ejecuta en ella:

> sudo su
add-apt-repository ppa:yannubuntu/boot-repair
apt-get update
apt-get install -y boot-repair
boot-repair

10 - Boot repair, mostrara una ventana donde informa un sistema EFI, que requiere corrección del Grub,
Se aplica y listo.
Al reiniciar tanto Ubuntu como Windows 8 podrían, si hubo suerte, ser iniciados.

Particularmente, trataria de buscar, si asi me fuere necesario (no uso portables y por ahora no pienso usar)
como activar el wifi, si esto fuera posible, eliminaría Windows 8 e instalaria solo una distribución Gnu/Linux
con tabla de particiones mbr sin uefi.

---

### Post by leizzer on 2013-05-31
Buenas, estoy recien registrado porque estoy con la misma computadora, una Dell 14z.

Tiene Win8 y quiero una particion con Ubuntu porque lo necesito para el trabajo.

Segui demaciadas guias de como instalar Ubuntu en una maquina con UEFI, tengo todo desactivado y repeti los paso muchas veces.

Lo  que me pasa a mi, es que el LiveUSB con Ubuntu 13 64bit que cree  (siguiendo la guia en la pagina de ubuntu), lo puedo bootear con UEFI.  Pero luego de ver el menu de 'Try Ubuntu' o 'Install Ubuntu', luego de  dar enter sobre cualquiera de esas 2 opciones, el led del usb flashea un  par de veces y luego nada... no hay actividad ni de disco, ni de usb, y  la pantalla queda totalmente en negro. Por mas que lo deje durante  varios minutos nada pasa.
Incluso intente agregar la opcion de nomodeset=1 en el grub.conf del USB

La vez anterior que probe instale Ubuntu 12.04 LTS 64bit en modo Legacy.

Cree  una particion de 1MB para el boot, una para swap de 5GB y otra de 150GB  para Linux. (Desde un espacio libre que deje desde Windows)

Luego  de terminar la instalacion trate de bootear varias veces el HDD en modo  legacy y solo conseguia un error por consola de que reconecte el cable o  algo asi (no recuerdo en este momento)

 Asi que inicie el Try Ubuntu en modo legacy y trate de reparar con boot-repair. Me dio este alerta:
[I]
'The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?'[/I]

Le  di 'Yes' y me reparo el boot mostrandome Grub al iniciar la pc en modo  UEFI, pero Ubuntu no iniciaba... y si mal no recuerdo Win8 tambien dejo  de iniciar (luego renegando arruine todas las particiones y fue un caos  pero es otro tema).

Ahora, luego de renegar recuperando las  particiones con el CD de Dell, llegue al mismo punto, antes del  Boot-Repair. Esta vez instale Ubuntu 13 64bit y tengo miedo de repetir  los mismos pasos y llegar al mismo resultado.

Realmente tengo miedo de seguir, no quiero caer en los mismos problemas de la ultima vez.

Ruego por ayuda,
Desde ya muchas gracias.

Dejo Info (de necesitar mas info solo pidan)
El  disco es hibrido, tendo desactivado todo lo que no debe estar activado  (Las cosas de inicio Rapido de Inte, Secure Boot, y demas)

Boot-Repair Pastie
[http://paste.ubuntu.com/5721829/](http://paste.ubuntu.com/5721829/)

GParted
[IMG]https://dl.dropboxusercontent.com/u/5847684/Screenshot%20from%202013-06-01%2003%3A34%3A11.png[/IMG]

---

### Post by SSNova on 2013-06-01
Gracias por las respuestas, las voy a poner a prueba estos días y les comento que paso

---

### Post by leizzer on 2013-06-02
SSNova, si tus intenciones es dejar UEFI desactivado (osea modo legacy). Creo que vas a tener que reinstalar Win8, ya que está instalado en modo UEFI. No estoy totalmente seguro.

---

### Post by gmunioz on 2013-06-02
Aclaraciones:
Para intentar instalar Ubuntu 64 bits en modo Uefi, solo hace falta desactivar secure boot.
Para instalar Ubuntu junto a Windows 7/8  en modo legacy, es necesario reinstalar Windows
en un disco con tabla de particiones msdos, con mbr.

---

### Post by leizzer on 2013-06-02
Miren acá encontré tal cual mi problema: Yo no podía iniciar el LiveUSB en UEFI mode.

[http://ubuntuforums.org/showthread.php?t=2144853&page=2&highlight=liveusb+doesn%27t+boot+uefi](http://ubuntuforums.org/showthread.php?t=2144853&page=2&highlight=liveusb+doesn%27t+boot+uefi)

@SSNova, buscá la parte donde describe los pasos siguio. Termino de hacerlo y tengo Ubuntu corriendo en UEFI mode con Win8. Hace 5min terminé la instalación y está todo bien.

Al parecer lo que complica el inicio del LiveUSB en modo UEFI es tener NIC activado, hay que desactivarlo desde el setup.

Lo único que me falta ahora, es ver si boot-repair me agrega Windows al Grub porque no está. (Igualmente se puede iniciar desde el listado de booteo que aparece al apretar F12 en las Dell 14z)

Saludos.

PD: SSNova, si necesitás ayuda porque está en inglés, avisame.


EDIT -> Boot-Repair

Cómo usar Boot-Repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Termino de probar Boot-Repair y agregó Win8 a Grub2. Soy feliz xD

Lo que falta a criterio de cada uno es quitar algunas opciones del Grub porque vas a ver qeu agrega muchas opciones de Windows que algunas te van a fallar y otras no.

---

### Post by HumanAfterAll5 on 2013-07-15
> **leizzer said:**
> .

Consulta, por que yo hace un par de semanas me compre el mismo equipo, intenté de mil formas instalar Ubuntu con el Win 8 que ya viene en el equipo y no me detectaba las particiones, como si no tuviese disco. En fin, no sé por que no entré en este foro hace 1 semana y me ahorraba ciertos problemas y cosas de newbie que tengo con Ubuntu.

El tema es el siguiente y te pregunto a vos leizzer que al parecer pudiste instalar los dos SO, te funcionó la red?? (tanto cable como wireless).

Comento que yo instale Windows 7 con MBR, desde esta instalación dejé el SSD de 32gb sin particionar y 250gb (mitad de HDD) también sin particionar, los otros 250gb para Windows 7 en NTFS. Ahora bien Ubuntu no me detectaba ningún SO instalado!, busqué y busqué en ingles, en español y no encontré nada, solo algunos decían que volvieron a reinstalar Windows y luego les apareció. Aunque ahora si detectó los discos, no detectaba particion alguna.
Ahora bien, resignado a esto (aparte estaba con la cabeza quemada, hice todo en una tarde-noche) me dije a mi mismo "Va Ubuntu solo". Seguí los pasos de un tipo de como puso el \, el \home y demás y no funcionó. "Bueno... vamos con la ayuda de Ubuntu". Quise meter el SO en el 32gb (flashe mal yo...) y me tiró un error con el grub. Bueno... tire la instalación en el de 500 HDD, instaló todo y luego arrancó, funcionó. Ahora el problema es que no tengo wired ni wireless... Conecto el cable y nada, la Wifi no arranca.
Si detecta la placa wifi y me dice que el drivers no fue liberado (o algo así) pero me da la opción de instalar; el tema es que se descarga por red...
Se que esto lo hace funcionar por que en la instalación, si esperaba un rato me tiraba el aviso del driver y si lo quería activar, al darle a activar el driver se instalaba y la wireless funcionaba perfecto; debe ser por que en el CD de instalación se encuentra el driver, o no sé. Pero después de instalar el SO no me deja para nada. Hay alguna forma de instalar el driver de la wireless? leí sobre los repositorios, pero todavia no lo pude ver muy bien y en un principio no entendí muy bien como utilizarlos.

Lo ideal para mi es instalar Windows 7 y Ubuntu, pero necesito el Ubuntu sí o sí por que necesito aprender algunas cosas (aparte de que me parece tremendo SO). Volver a instalar el Windows 8 no lo voy a hacer, así que ya fue. Tampoco me molestaría mucho utilizar Ubuntu. Volví a instalar Windows 7 pero no volví a probar si Ubuntu me detecta a Win 7 como instalado.

EDITO:
[http://www.solonotebooks.net/products/6270-dell-inspiron-14z-ultrabook-i7-3517u-8-gb-500-gb-hd-7570m/](http://www.solonotebooks.net/products/6270-dell-inspiron-14z-ultrabook-i7-3517u-8-gb-500-gb-hd-7570m/)

Ese es el modelo exacto, por que 14z hay i5 e i3 creo. Ya se tambien que la placa dedicada va a ser un dolor de ... hacerla funcionar, pero tampoco me preocupa mucho si es que puedo hacer arrancar Windows 7 también.

Gracias a la persona que me responda, y si no me entendió me volveré a expresar de otra forma.

Saludos!,

Mauro.

---

### Post by guillermolisi on 2013-07-15
Concretamente, el inconveniente que estas teniendo es solo con la placa inalambrica ?
Si es asi entonces este post genera un nuevo hilo porque es Off Topic en este.

Cuando se usa dual boot con Windows, primero hay que instalar este y despues Ubuntu para que el GRUB detecte y genere la informacion de arranque para ambos SOs. Si se hace al reves, se pierde el arranque de Ubuntu y hay que recuperarlo mediante operaciones avanzadas (o reinstalandolo).

---

