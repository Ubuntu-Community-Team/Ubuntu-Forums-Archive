---
title: "(casi) nueva en ubuntu... MI NO ENTENDER!"
date: 2009-01-23
forum: Hardware
---

### Post by celestezul on 2009-01-23
Hola gente!
aso a relatar mi caso: hace un par de semanas encargue el cd de ubuntu, y hoy me llego, a lo que corrí a mi computadora a ver el demo. Ahora, que pasa: hice como me decía el menu; dejé el cd en la lectora la computadora se reinició pero nada cambió... siguió windows como si nada... revisé todos los archivos del cd, intentando encontrar alguna pista xD pero nada... 
intenté con la ultima de las 3 opciones del menu de bienvenida, la que te "ayuda" a correr el cd... esta vez pareció funcionar: en modo DOS se me daba la opcion de correr el sistema en windows o ubuntu. elegi ubuntu, se me empezo a cargar con el logo de ubuntu y todo... pero despues me sale otra pantalla DOS que dice un monton de cosas que no entiendo, y se queda asi...
que jápened??

ayudenmeeeee![-o<

quiero probar el ubuntu! no se si lo voy a dejar como definitivo, porque me parece que voy a necesitar un monton de programas de windows este año en la facultad... pero al menos quiero probarlo!

saludos!!

---

### Post by staar on 2009-01-23
hola, bienvenida a ubuntu
seria importante que nos transcribas exactamente lo que te dice esa pantalla "en modo DOS" (en realidad no es MS-DOS, solo es similar en aspecto, es GNU/Linux ;) ) para asi poder ayudarte, lo que te puedo decir asi, ahora, es que evidentemente tenes un  problema que no deja arrancar el entorno grafico (el "escritorio") por lo que te deja en modo texto, supongo

(antes no te arranco desde el CD porque la pc estaba configurada para iniciar primero desde el disco duro, y no desde la lectora de cd, supongo que ya habras arreglado eso ;) )

saludos

---

### Post by el_itur on 2009-01-24
Yo te recomendaría que recurras a tu nerd más cercano. 

Vas a ahorrarte dolores de cabeza, evitar perdidas de datos y te va a ser más fácil agarrarle la mano a las cosas que son diferentes a windows de entrada.

---

### Post by gmunioz on 2009-01-24
Hola cel...:
1- Una opción es introducir el cd estando en Windows, al autoejecutarse puedes elegir la opción de instalarlo en Windows. Se instalará como un programa más de Windows, sobre el sistema de archivos de Windows. Al reiniciar el ordenador tendrás la opción en modo texto de elegir el sistema operativo para iniciar la pc, Windows o Ubuntu. Tendrás un Ubuntu funcionante, sin muchas funcionalidades específicas y propias de ese sistema, que por el momento no te harán falta. Si te gusta y decides instalarlo en forma completa o si no te agrada y decides eliminarlo simplemente desde una sesión de Windows, mediante la opción de eliminar aplicaciones lo desinstalas, tal como harías con cualquier aplicación de ese operativo.
2- Otra opción es instalar el sistema operativo con todas sus funcionalidades en particiones separadas, reduciendo la del operativo de Microsoft, para un arranque dual Windows - Ubuntu. para este caso, debes primero entrar al setup del ordenador, pulsando segun chipset (generalmente en la pantalla te sugiere pulse xxx para setup) Suprimir F9 F11, y una vez dentro del setup elegir como dispositivo inicial de booteo el cdrom, grabar los cambios e iniciar con el cd de ubuntu dentro del lector, iniciará con las opciones de sesión-live para probar y luego instalar o con la opción de iniciar la instalación directamente y de ahi en más instalar de acuerdo con el tutorial que más te convenga.
Saludos.
Gabriel.
**Solo doy soporte para Ubuntu** - *Mad Jaunty User *

---

### Post by celestezul on 2009-01-26
Gracias por responder!!
mmm a ver: lo que me aparece es lo siguiente:

[0.2960108] ..MP_BIOS bug . 8254 timer not connected to IO-APIC
loading, please wait...

BusyBox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)

Entonces, escribo help a ver si aparece algo :lol:

y queda help al lado de (initramfs) obviamente, y a bajo una lista de comandos que no entiendo XD

Built-in commands:

.: [ [[ alias break cd chdir command continue echo eval exec exit export false getopts hash help let local pwd read  readonly unalias unset wait [[[ ash awk basename cat chmod chroot chvt clear cmp cp cut deallocvt dumpkmap echo egrep env expr false fbset fdf lush fgrep find grep hostname if config ip kill loadfont loadkmap ls mkdir mkinfo mknod mkswap mktemp more mount mv openvt pidof printf ps pwd readlink reset rm rmdir sed setkeycodes sh sleep sort stat sync tail tee test touch trtve  tty umount uname uniq luget yes


y nada mas.


para salir tengo que apretar ctrl+alt+supr no se sale con "exit" asi que ni eso entiendo xD
enn fin...
alguna idea?:confused:



saludos y gracias!

---

### Post by staar on 2009-01-26
es un error que ocurre en ubuntu y depende del hardware, generalmente es culpa de la placa madre, por suerte hay una opcion en el arranque para solucionarlo, pasate por [**ESTE THREAD**](http://ubuntuforums.org/showthread.php?t=911212), que ahi explican bien como solucionarlo

saludos

---

### Post by celestezul on 2009-01-27
gracias staar!

igual eso no va a afectar al sistema de windows, la velocidad ni nada no?

---

### Post by staar on 2009-01-27
nope, es una opcion del kernel linux, solo afecta a ubuntu, y por lo que se, no tiene consecuencias en el rendimiento (en muy pocos casos puede haber problemas con los dispositivos USB, pero esto era hace mucho, supongo que ya no)

en realidad estas teniendo un problema con el I/O APIC, que es un sistema interno de la PC para controlar hardware (IRQ, direcciones...), muchas BIOS vienen con problemas y bugs en este aspecto, y a veces una actualizacion del BIOS basta, pero generalmente es innecesario y no afecta al usuario promedio

saludos

---

