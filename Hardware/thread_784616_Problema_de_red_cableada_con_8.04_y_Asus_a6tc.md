---
title: "Problema de red cableada con 8.04 y Asus a6tc"
date: 2008-05-06
forum: Hardware
---

### Post by pabloatilio on 2008-05-06
Amigos:
He instalado el 8.04 vs AMD64 desde cero, no una actualización, en una asus A6tc , antes tenía el 7.01 y no había problemas con la placa de red, pero ahora si los tengo, si no estoy equivocado el controlador que utiliza es el RTL8168B-811B.
El problema es el siguiente, aparentemente hay algún tipo de conectividad porque el router (tengo una pequeña red hogareña) reconoce el nombre del equipo, le asigna una dirección ip (todo funciona bajo dhcp), pero levanta y da de baja la conexión permanentemente ya que a veces aparece en el resumen de los equipos conectados a la red y a veces no.
Es imposible llegar con ping ni siquiera al router. probé usar el network-manager, después desabilite y probé de configurar /etc/network/interfaces de la siguiente manera :

auto eth0
iface eth0 inet dhcp

Como dije antes, lo de dhcp es lo de menos ya que ni siquiera llego al router con ping.

Con el comando lspci me sale lo siguiente :
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 1)

Con el comando ifconfig sale:
Link encap:Ethernet direcciónHW 00:xx:xx:xx:xx:xx
dirección inet6: fexx::xxx:dxff:fxcx:dxxf/xx Alcance:Vínculo
ARRIBA DIFUSIÓN CORRIENDO MULTICAST MTU:1500 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:46 overruns:0 carrier:0
colisiones:0 txqueuelen:1000
RX bytes:2360 (2.3 KB) TX bytes:0 (0.0 MB)
Interrupción:253 Dirección base: 0x6000

Como se ve no sale ninguna información del tipo "inet dirección:xxx.xxx.x.xx Difusión:xxx.xxx.x.xxx Máscara:xxx.xxx.xxx.xxx" y además no hay información enviada ni nada de eso.

Probé de instalar el driver desde la página del fabricante "www.realtek.com.tw", pero me da error el archivo make.
También lo más simple, como ser de configurar por network-manager , desactivar y activar red, etc.
Lo que más me fastidia es que andaba bien en ubuntu 7.01 sin tocar nada y anda bien en el "innombrable" del sr puertas. En fin... gracias por su tiempo y por su ayuda.

La última prueba que hago hace lo siguiente sistematicamente : desactivo la red, vuelvo a activar, reconoce el router la máquina (nombre + dirección MAC) al minuto la deja de tener en su listado de equipos conectados. Vuelvo a hacer lo mismo, la vuelve a reconocer y al minuto a bajar. Nunca tengo conectividad, ni por direccionamiento ip directo, por ej poner la dirección ip de una página ni llego al router.
Saludos.

PabloAtilio****

---

### Post by faktorqm on 2008-05-07
Hola loco, todo bien? bueno vamos a ver que esta pasando. Consideraciones al respecto: 
a) 8.04 vs AMD64?  no será 8.04 para AMD64? 
b) la version 7.01 de ubuntu NO existe, hay 6.06, 7.04, 7.10, 8.04.
c) mas o menos pasa cada un minuto que te da conexion y corta? tenes ahi un connection time out que te lo tira el kernel. eso lo vemos despues.
d) tenes paquetes enviados pero no recibidos, eso es un problema enteramente del driver, pensaria que es el cable, pero decis que en win anda perfecto, asi que nos dedicamos directamente al driver.
e) make es un archivo, estamos de acuerdo, pero tiene la particularidad de que es ejecutable, por lo tanto podemos pensar en un comando. Sirve para compilar, y exactamente es el eje de la cuestion. 
f) de vuelta, ocurre cada un minuto por que es un valor seteado de conecction time out, lo mismo que el punto d.

Necesitariamos para poder ayudarte mejor, saber si tenes solo wireless, o wireless mas cable. Version del kernel (la averiguas con el comando "uname -r") y link a donde bajaste los fuentes para compilar.
Para compilar, primero tenes que leer el readme y fijarte que tenes que hacer, luego instalate el paquete build-essential (lo haces con sudo apt-get install build-essential) y fijarte.

Te aviso por las dudas, por que me parece que lo tenes que saber, que como cambio la version del kernel de la 8.04 respecto de la 7.10 hay algunas cosas que quiza no funcionen, y otras que no funcionaban antes quiza ahora si funcionen. Lo que hizo un admin de este foro, es quedarse con 8.04, pero instalo el kernel anterior, es decir, el que venia con la version 7.10. De esa manera se ahorro muchos dolores de cabeza y le sirvio. Si vos no tenias ningun problema con la 7.10 y con la 8.04 no te anda eso, es una opcion cambiar de kernel.

Espero haberte ayudado, esperamos tus dudas. Salu2!!

---

### Post by pabloatilio on 2008-05-07
> **faktorqm said:**
> Hola loco, todo bien? bueno vamos a ver que esta pasando. Consideraciones al respecto: 
a) 8.04 vs AMD64?  no será 8.04 para AMD64? 
b) la version 7.01 de ubuntu NO existe, hay 6.06, 7.04, 7.10, 8.04.
c) mas o menos pasa cada un minuto que te da conexion y corta? tenes ahi un connection time out que te lo tira el kernel. eso lo vemos despues.
d) tenes paquetes enviados pero no recibidos, eso es un problema enteramente del driver, pensaria que es el cable, pero decis que en win anda perfecto, asi que nos dedicamos directamente al driver.
e) make es un archivo, estamos de acuerdo, pero tiene la particularidad de que es ejecutable, por lo tanto podemos pensar en un comando. Sirve para compilar, y exactamente es el eje de la cuestion. 
f) de vuelta, ocurre cada un minuto por que es un valor seteado de conecction time out, lo mismo que el punto d.

Necesitariamos para poder ayudarte mejor, saber si tenes solo wireless, o wireless mas cable. Version del kernel (la averiguas con el comando "uname -r") y link a donde bajaste los fuentes para compilar.
Para compilar, primero tenes que leer el readme y fijarte que tenes que hacer, luego instalate el paquete build-essential (lo haces con sudo apt-get install build-essential) y fijarte.

Te aviso por las dudas, por que me parece que lo tenes que saber, que como cambio la version del kernel de la 8.04 respecto de la 7.10 hay algunas cosas que quiza no funcionen, y otras que no funcionaban antes quiza ahora si funcionen. Lo que hizo un admin de este foro, es quedarse con 8.04, pero instalo el kernel anterior, es decir, el que venia con la version 7.10. De esa manera se ahorro muchos dolores de cabeza y le sirvio. Si vos no tenias ningun problema con la 7.10 y con la 8.04 no te anda eso, es una opcion cambiar de kernel.

Espero haberte ayudado, esperamos tus dudas. Salu2!!

Hola amigo, gracias por responder, te paso la info de las cosas que me preguntaste :

a) si, es 8.04 version (vs) AMD64
b) es la version 7.10 , suelo escribir al reves, en fin...
c) me da conexión por un tiempo menor a un minuto a partir del momento que activo la red, y de nuevo cuando vuelvo a desactivar, pero OJO, no es que en ese momento tengo conexion sino que el router detecta el equipo y sale en el sumario de equipos detectados (detecta la direccion mac y el nombre que yo le asigné al equipo) despues se cae la deteccion del equipo, conexion no tengo nunca, ni siquiera al router mediante la ip para entrar a administrarlo
d) en win anda perfecto, no es el cable, la conexión física está bien, eso hay que descartarlo, y la configuración del router (antes en ubuntu 7.10 andaba todo perfecto)
e) hay un problema cuando ejecuto el comando make con las instrucciones que trae el driver, ya te escribo más de eso enseguida

Este equipo trae wireless y ethernet rj-45 que aparece como eth0, yo estoy tratando de que funcione la conexion cableada, la wireless no la pude hacer andar antes (en 7.10) y no me fije mucho ahora pero tampoco se podía.

El kernel es 2.6.24-16-generic. No tengo problemas de cambiar al kernel anterior pero no tengo ni idea como hacer eso, de hecho estoy pensando el volver a instalar el 7.10 y listo. Te pregunto a ver si sabes ¿este problema que tengo se puede dar que se solucione en el futuro con actualizaciones que aparezcan específicamente para el kernel  ? , no entiendo como una version mas nueva puede dejar colgada cosas que antes andaban bien.

La dirección del driver es : 
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110S-32/RTL8110SB(L)/RTL8169SB(L)/RTL8169SC(L)%3Cbr%3ERTL8169](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110S-32/RTL8110SB(L)/RTL8169SB(L)/RTL8169SC(L)%3Cbr%3ERTL8169)
Eligo el segundo que aparece como a mitad de página, no el primero, osea elijo el RTL8169

Al querer instalar el kernel siguiendo las instrucciones del archivo readme me tira lo siguiente :

pabloatilio@pabloatilio-laptop:~/r8169-6.006.00$ sudo make clean modules
make -C src/ clean
make[1]: se ingresa al directorio `/home/pabloatilio/r8169-6.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: se sale del directorio `/home/pabloatilio/r8169-6.006.00/src'
make -C src/ modules
make[1]: se ingresa al directorio `/home/pabloatilio/r8169-6.006.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No existe el fichero ó directorio
make[3]: *** No hay ninguna regla para construir el objetivo `/src/Makefile'.  Alto.
make[2]: *** [_module_/src] Error 2
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: se sale del directorio `/home/pabloatilio/r8169-6.006.00/src'
make: *** [modules] Error 2

Puede que no esté siguiendo bien las instrucciones, en fin, los requerimientos para instalar el driver aparentemente estan todos
Me fijé de instalar el build-essential , osea, esta todo.
Gracias por tu tiempo, saludos.

---

### Post by faktorqm on 2008-05-07
lo veo mañana, asi a ojo de buey te falta ejecutar algun ./configure, que es el que te genera el archivo Makefile que te dice que falta. Me bajo el driver y te cuento como es, sino sajnox te va a explicar como instalar el kernel anterior, o como instalar 7.10, actualizar y que te quede 8.04 con el kernel viejo. Salu2!

---

### Post by faktorqm on 2008-05-08
Hola, bue ya me baje el archivo y lei el readme. 

Basicamente, tenes que mirar primero que no tengas el modulo levantado, para esto haces 

```
lsmod | grep r8169
```

ejemplo en mi maquina para que veas:

```

faktorqm@the-edge:~$ lsmod | grep r8169
faktorqm@the-edge:~$ lsmod | grep nvidia
nvidia               7825536  24 
agpgart                34760  1 nvidia
i2c_core               24832  2 nvidia,i2c_nforce2
faktorqm@the-edge:~$ 

```

obviamente no tenia el modulo cargado pero si el de nvidia. o sea, si a vos en vez de no mostrarte nada te muestra que esta cargado, tenes que hacer:

```
rmmod r8169
```

en el archivo dice:

"note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remove it again or reboot your computer."

nota: Si el driver es embebido no puede ser removido por rmmod. por favor edite /etc/modprobe.conf y comente la linea 'alias eth0 r8169'. Luego remuevalo otra vez (se refiere a hacerlo con rmmod) o reinicie su computadora.

Una vez que lo tenes hecho, lo ubicas en una carpeta, aca en el ejemplo que te voy a dar lo hago en /home/faktorqm/lan_drv.
Entonces descomprimis el tar.gz ahi en tu home y luego le cambias el nombre al directorio como mas te guste.

Primero, nos aseguramos de tener todas las cosas para compilar, para esto hacemos:

```
sudo aptitude install build-essential linux-headers-`uname -r` binutils gcc
```

si ya tenes instalado algo quedate tranquilo que te lo saltea. 

Luego, una vez terminado esto, nos metemos en el directorio donde tenemos el driver descomprimido:

```
cd /home/faktorqm/lan_drv/
```

Luego hacemos: 

```
sudo make clean modules
```
```
sudo make install
```
```
sudo depmod -a
```
```
sudo insmod ./src/r8169.ko
```

Bueno, si nada te tiró error, hacés 

```
lsmod | grep r8169
```

y te tiene que aparecer algo, luego hacemos:

```
ifconfig
```

y te tiene que mostrar algo parecido a esto:

```

eth0      Link encap:Ethernet  direcciónHW 00:e0:4d:3f:ab:98  
          inet dirección:123.123.123.123  Difusión:123.123.123.255  Máscara:255.255.255.252
          dirección inet6: fe80::2e0:4dff:fe3f:ab98/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:12794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9457 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:5921012 (5.6 MB)  TX bytes:1643864 (1.5 MB)
          Interrupción:220 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:464 (464.0 B)  TX bytes:464 (464.0 B)

```

Ahora, hay que fijarse que nombre le puso, por lo general eth0. y lo configuramos:

```
sudo ifconfig eth0 123.123.123.123 netmask 255.255.0.0 broadcast 123.123.123.255 up
```

obviamente el primer valor es el ip, el segundo la mascara, y el broadcast. yo puse cualquier cosa para que lo veas.
A partir de aca supuestamente ya te tiene que empezar a andar. 

Igual en realidad esta parte podrias hacer "sudo ifconfig eth0 up" y despues hacer el resto desde el network manager que es grafico y no te complicas la vida con comandos. 

Bueno espero la salida de los comandos jajajajaj Salu2!!

---

### Post by pabloatilio on 2008-05-08
> **faktorqm said:**
> Hola, bue ya me baje el archivo y lei el readme. 

Basicamente, tenes que mirar primero que no tengas el modulo levantado, para esto haces 

```
lsmod | grep r8169
```

ejemplo en mi maquina para que veas:

```

faktorqm@the-edge:~$ lsmod | grep r8169
faktorqm@the-edge:~$ lsmod | grep nvidia
nvidia               7825536  24 
agpgart                34760  1 nvidia
i2c_core               24832  2 nvidia,i2c_nforce2
faktorqm@the-edge:~$ 

```

obviamente no tenia el modulo cargado pero si el de nvidia. o sea, si a vos en vez de no mostrarte nada te muestra que esta cargado, tenes que hacer:

```
rmmod r8169
```

en el archivo dice:

"note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remove it again or reboot your computer."

nota: Si el driver es embebido no puede ser removido por rmmod. por favor edite /etc/modprobe.conf y comente la linea 'alias eth0 r8169'. Luego remuevalo otra vez (se refiere a hacerlo con rmmod) o reinicie su computadora.

Una vez que lo tenes hecho, lo ubicas en una carpeta, aca en el ejemplo que te voy a dar lo hago en /home/faktorqm/lan_drv.
Entonces descomprimis el tar.gz ahi en tu home y luego le cambias el nombre al directorio como mas te guste.

Primero, nos aseguramos de tener todas las cosas para compilar, para esto hacemos:

```
sudo aptitude install build-essential linux-headers-`uname -r` binutils gcc
```

si ya tenes instalado algo quedate tranquilo que te lo saltea. 

Luego, una vez terminado esto, nos metemos en el directorio donde tenemos el driver descomprimido:

```
cd /home/faktorqm/lan_drv/
```

Luego hacemos: 

```
sudo make clean modules
```
```
sudo make install
```
```
sudo depmod -a
```
```
sudo insmod ./src/r8169.ko
```

Bueno, si nada te tiró error, hacés 

```
lsmod | grep r8169
```

y te tiene que aparecer algo, luego hacemos:

```
ifconfig
```

y te tiene que mostrar algo parecido a esto:

```

eth0      Link encap:Ethernet  direcciónHW 00:e0:4d:3f:ab:98  
          inet dirección:123.123.123.123  Difusión:123.123.123.255  Máscara:255.255.255.252
          dirección inet6: fe80::2e0:4dff:fe3f:ab98/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:12794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9457 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:5921012 (5.6 MB)  TX bytes:1643864 (1.5 MB)
          Interrupción:220 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:464 (464.0 B)  TX bytes:464 (464.0 B)

```

Ahora, hay que fijarse que nombre le puso, por lo general eth0. y lo configuramos:

```
sudo ifconfig eth0 123.123.123.123 netmask 255.255.0.0 broadcast 123.123.123.255 up
```

obviamente el primer valor es el ip, el segundo la mascara, y el broadcast. yo puse cualquier cosa para que lo veas.
A partir de aca supuestamente ya te tiene que empezar a andar. 

Igual en realidad esta parte podrias hacer "sudo ifconfig eth0 up" y despues hacer el resto desde el network manager que es grafico y no te complicas la vida con comandos. 

Bueno espero la salida de los comandos jajajajaj Salu2!!



Estimado amigo, antes que nada quiero darle las gracias por todo el trabajo que ha hecho para ayudarme con mi problema, agradezco sinceramente su tiempo dedicado.

Entiendo perfectamente su explicación, creo que están todos los pasos bien dados, el build-essential linux-headers-`uname -r` binutils gcc están correctamente instalados, descomprimo el archivo en home/pabloatilio/r8169-6.006.00, primero remuevo el módulo de memoria, pero al momento de hacer "sudo make clean modules" me sale el mismo error de siempre, es decir el siguiente : 
...
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No existe el fichero ó directorio
make[3]: *** No hay ninguna regla para construir el objetivo `/src/Makefile'. Alto.
make[2]: *** [_module_/src] Error 2
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: se sale del directorio `/home/pabloatilio/r8169-6.006.00/src'
make: *** [modules] Error 2
...

Lo que he notado, que tal vez no tenga absolutamente nada que ver, es que no existe nada adentro de /home/pabloatilio/r8169-6.006.00/src, el directorio está vacío, y sin embargo si existe algo para otro driver que es el r8168. es decir el el driver r8168 descomprimido, adentro de /src hay un archivo Makefile, otro Makefile_linux24x, otro r8168.h, y dos o tres mas, que no estan presentes en el subdirectorio /src correspondientes al driver que quiero instalar ¿eso sera el mensaje de error ?, no creo porque al querer instalar este (que dice el archivo readme que tambien sirve, me sale lo mismo).

Otra cosa es que antes, al mirar para editar el archivo /etc/modprobe.conf, el mismo no existe, hay uno en ese directorio que se llama modules y no tiene nada relativo al driver que quiero instalar.

Encontré en la siguiente página : [http://gentoo-wiki.com/HARDWARE_Asus_A6T#Ethernet](http://gentoo-wiki.com/HARDWARE_Asus_A6T#Ethernet) algo de información, pero no me fué necesaria tenerla en cuenta para ubuntu 7.10, quien sabe si para 8.04 sea útil-

Probé de volver en el tiempo y ejecutar el live cd de ubuntu **7.10** y anda P e r f e c t o , por lo tanto si no es algo obvio lo que pueda estar haciendo mal, le agradezco muchísimo su tiempo, pero no quiero abusar de su predisposición y paciencia, me estaría volviendo al 7.10 hasta ver que onda con este nuevo.

Gracias de nuevo. Saludos

PabloA

---

### Post by guillermolisi on 2008-05-08
Pero que maestro !!

Excelente explicacion.

---

### Post by faktorqm on 2008-05-08
Bueno estuve leyendo un poco mas. Al parecer, por lo que dice ahi la gente de gentoo el coso este anda con el driver de la placa antecesora, la 8168.

Hagamos la prueba rapida, el tema del rmmod, todo igual, si ya lo hiciste saltealo. (ahh me olvidaba, siempre que no sepas donde esta algo, ¡preguntale a la consola! 

```
whereis modprobe.conf
```

donde esta modprobe.conf? esta en /etc/modprobe.d :D (en realidad no lo verifique, supongo que debe estar ahi) )

Sigamos todo lo anterior igual pero con el driver 8168 ok?
lo unico que habria que cambiar es la parte que dice

```
sudo insmod ./src/r8169.ko
```

por:

```
sudo insmod ./src/r8168.ko
```

y la parte que consultas por el modulo casi al final:

```
lsmod | grep r8169
```

por:

```
lsmod | grep r8168
```

Proba, y me contas. Sino vemos alguna otra solucion. Salu2!

---

### Post by pabloatilio on 2008-05-09
> **faktorqm said:**
> Bueno estuve leyendo un poco mas. Al parecer, por lo que dice ahi la gente de gentoo el coso este anda con el driver de la placa antecesora, la 8168.

Hagamos la prueba rapida, el tema del rmmod, todo igual, si ya lo hiciste saltealo. (ahh me olvidaba, siempre que no sepas donde esta algo, ¡preguntale a la consola! 

```
whereis modprobe.conf
```

donde esta modprobe.conf? esta en /etc/modprobe.d :D (en realidad no lo verifique, supongo que debe estar ahi) )

Sigamos todo lo anterior igual pero con el driver 8168 ok?
lo unico que habria que cambiar es la parte que dice

```
sudo insmod ./src/r8169.ko
```

por:

```
sudo insmod ./src/r8168.ko
```

y la parte que consultas por el modulo casi al final:

```
lsmod | grep r8169
```

por:

```
lsmod | grep r8168
```

Proba, y me contas. Sino vemos alguna otra solucion. Salu2!


Hola de nuevo, estimado amigo,  (ya no me dá la cara para seguir preguntándote) 

Te cuento como sigue la cosa, haciendo lo mismo  con el modulo r8168 tiraba el mismo error, osea error 2 no hay ninguna regla bla bla bla, PEROOOOooooooo, buscando en internet en éste foro :
[http://ubuntuforums.org/showthread.php?t=755002](http://ubuntuforums.org/showthread.php?t=755002)

encontré que bajando el siguiente archivo 

[http://ubuntuforums.org/attachment.php?attachmentid=66030&d=1208224861](http://ubuntuforums.org/attachment.php?attachmentid=66030&d=1208224861)

después copiándolo en el subdirectorio scr del driver descomprimido
y después haciendo 

patch < r8168-8.005.00.hardy.diff.txt
cd ..
make clean
make modules
sudo make install
sudo depmod -a
sudo insmod ./src/r8168.ko

¡¡¡ el módulo se instala !!! (si se instalará bien so sé jeje)

Lo interesante es que si hago :

lsmod | grep r8168                puedo ver 
r8168            38544 0         osea carga el nuevo módulo instaldo

pero , si hago

lsmod | grep r8169               ¡también aparece!
r8169           36612 0

y creo que me "pisa" el nuevo driver que instalé, probé de tratar de hacer
que no se cargue el anterior (que es el más nuevo, osea el r8169) de la siguiente manera :

añadiéndolo en cuanto putx.... blacklist encontré leyendo en internet caso por ej :
sudo gedit /etc/modprobe.d/blacklist 
sudo gedit /etc/modprobe.d/blacklist-oss
sudo gedit /etc/modprobe.d/blacklist-netwotk (ésta no estaba pero igual la hice porque la sugerían en algún lado)

y poniendo el nombre del módulo "r8169" al final de la forma que están los otros , es decir : blacklist r8169 (algunos dicen que hay que darle un "enter" y dejar un renglón, probé de las dos formas y nada)

También probé con (por ahi es una animalada lo que estoy haciendo, en fin)

sudo gedit /etc/default/linux-restricted-modules-common

y en la línea DISABLED_MODULES="" 
DISABLED_MODULES="r8169"

Y no hay caso, cada vez que reincio me aparecen los DOS módulos, quien sabe si el nuevo que instalé (que en realidad es una versión más vieja) funcione, pero se me ocurre que hasta no eliminar al !$#¿&@&¡¡ del r8169 nunca lo sabré.

Gracias por todo tu tiempo y respuestas. Saludos

Pablo

---

### Post by pabloatilio on 2008-05-10
Bueno, finalmente logré remover la carga del módulo r8169 a partir de la info de la página : [http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html) y de la info que me dió el amigo Faktorqm, notar que el módulo que funciona compilado es el r8168-8.005.00 y no el r8168-8.006.00, los comandos hay que ejecutarlos como explica Faktorqm y previamente hacer el patch como explica la otra página, pero con los comandos hay que seguir lo que está en este foro. 
Gracias Faktorqm por tu ayuda, gracias a todos, saludos.

PD : yo actualicé desde ubuntu/pool/main a pata los linux headers, kernel etc porque habia una actualización para amd64 pero no solucionó el problema aunque me tomó el blacklist de r8169, creo que otra forma es hacer "sudo update-initramfs -c -k -all" y borrar unos archivos temporales, está todo explicado en la dirección que dejé arriba y con los pasos que se indican aquí.

---

### Post by faktorqm on 2008-05-11
grosso chabon! bien ahi que dejaste la solucion, no todos lo hacen.
Perdoná q no t respondi mas, es que rendi el sabado algebra 2, luego futbol, luego boliche y hoy estaba "roto" :D
Salu2!!

---

### Post by pabloatilio on 2008-05-12
> **faktorqm said:**
> grosso chabon! bien ahi que dejaste la solucion, no todos lo hacen.
Perdoná q no t respondi mas, es que rendi el sabado algebra 2, luego futbol, luego boliche y hoy estaba "roto" :D
Salu2!!


La verdad que despues de tanto ****, si uno encontró la solución y no la deja para ver si le puede servir a los demás, es bastante ortiva y no es mi estilo. Gracias por tu ayuda. Saludos (que te recuperes del finde).

PabloAtilio

---

### Post by sneider on 2008-05-18
Hay alguna forma mas sencilla de poder solucionarlo? yo tambien tengo un portatil a6tc, y la red me funcionaba justo antes de actualizar al ubuntu 8.04

Ahora al no poder usar la red no puedo bajarme los fuentes ni nada, ademas que nunca he compilado algo y me parece todo bastante complicado como para hacerlo :(

Soy usuario de ubuntu y todo lo que he ido instalando y configurando, ha sido con synaptic y en modo visual.

¿Sabeis si los responsables de ubuntu o del kernel de linux van a sacar una solucion al respecto?

---

### Post by faktorqm on 2008-05-18
La verdad, no lo creo, lo que si puedo hacer es armar ""LA GUIA"" de vuelta con las actualizaciones de pablo para que quede para siempre, si te interesa y le pones ganas... solo postealo :D
Salu2!!

---

### Post by K-Pi on 2008-05-20
Hola, yo tambien tengo un A6TC y tengo el mismo problema. Soy un novato total en linux y me pierdo en los pasos que ha seguido Pabloatilio. Puedes porfavor factorqm hacer una guia de lo que debo hacer paso a paso? Te lo agradeceria mucho. Es que probe Hardy Heron en mi sobremesa y me encanto, pero al ponerlo en el portatil... problemon de red al canto. Gracias anticipadas. Sl2

---

### Post by faktorqm on 2008-05-20
Bueno, vamos con la guía versión 2.

Ubuntu nos pone un módulo que no funciona con esta placa, por lo tanto primero hay que "bajarlo" para luego poner el nuestro que es el que anda bien. Para esto hacemos:

```
lsmod | grep r8169
```

ejemplo en mi máquina para que veas:

```

faktorqm@the-edge:~$ lsmod | grep r8169
faktorqm@the-edge:~$ lsmod | grep nvidia
nvidia               7825536  24 
agpgart                34760  1 nvidia
i2c_core               24832  2 nvidia,i2c_nforce2
faktorqm@the-edge:~$

```

Obviamente no tenia el módulo cargado pero si el de nvidia. O sea, si a vos en vez de no mostrarte nada te muestra que está cargado, tenás que hacer:

```
rmmod r8169
```

Ahora que ya lo dimos de baja, vamos a hacer que cuando reiniciemos no se vuelva a levantar:

```
sudo gedit /etc/modprobe.d/blacklist
```

Ahi se nos abre el gedit y nos muestra el archivo, debemos agregar la siguiente linea al final PERO SI O SI HAY QUE APRETAR ENTER AL FINAL DE LA LINEA.

```
blacklist r8169
```

Cuando hacemos 

```
cat /etc/modprobe.d/blacklist
```

te tiene que quedar algo asi:

```

...
...
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
blacklist r8169

faktorqm@the-edge:/etc/modprobe.d$ 

```

EL ESPACIO ENTRE DONDE DICE "blacklist r8169" y "faktorqm" es el CLAVE. Si haces cat a ese archivo y te lo muestra asi:

```

...
...
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
blacklist r8169
faktorqm@the-edge:/etc/modprobe.d$ 

```

**_[SIZE="3"]¡ESTA MAL! [/SIZE]_**

Ahora vamos a actualizar la imagen del kernel:

```
sudo update-initramfs -u
```

Bien, ahora ya estamos seguros de que ese módulo no va a volver.

Instalemos todo lo necesario para compilar el driver:

```
sudo aptitude install build-essential linux-headers-`uname -r` binutils gcc automake
```

Si ya tenes instalado algo quedate tranquilo que te lo saltea.

Vamos a nuestro home:

```
cd $HOME
```

Bajamos el driver de Realtek:

```
wget ftp://66.104.77.130/cn/nic/r8168-8.005.00.tar.bz2
```

Lo descomprimimos:

```
tar jvxf r8168-8.005.00.tar.bz2
```

Acá lamentablemente no podemos hacer este paso en consola, pero con cualquier explorador bajate este archivo:

```
http://ubuntuforums.org/attachment.php?attachmentid=66030&d=1208224861
```

y ponelo en la carpeta src adentro de la carpeta que te creo la descompresion del archivo del driver, o sea, /home/<nombre_de_usuario>/r8168-8.005.00/src

Ahora volvemos a la consola:

```
cd ~/r8168-8.005.00/src
```

Ahora parcheamos el driver:

```
patch < r8168-8.005.00.hardy.diff.txt
```

Salimos de src:

```
cd ..
```

Compilamos:

```
sudo make clean
```

```
sudo make modules
```

```
sudo make install
```

```
sudo depmod -a
```

Ahora cargamos el módulo:

```
sudo insmod ./src/r8168.ko
```

Bueno, si nada tiró error hacemos:

```
lsmod | grep r8168
```

y te tira algo asi:

```
r8168 38544 0
```

Luego nos fijamos bajo que nombre te puso la placa:

```
ifconfig
```

y te tiene que mostrar algo parecido a esto:

```

[COLOR="Red"]**eth0**[/COLOR]      Link encap:Ethernet  direcciónHW 00:e0:4d:3f:ab:98  
          inet dirección:123.123.123.123  Difusión:123.123.123.255  Máscara:255.255.255.252
          dirección inet6: fe80::2e0:4dff:fe3f:ab98/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:12794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9457 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:5921012 (5.6 MB)  TX bytes:1643864 (1.5 MB)
          Interrupción:220 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:464 (464.0 B)  TX bytes:464 (464.0 B)

```

Ahora, hay que fijarse que nombre le puso, por lo general eth0. Así "levantamos" la interfaz:

```
sudo ifconfig eth0 up
```

Con esto bastaría para ir al network-manager y configurar la red, si tenemos conexión "automatica", caso modems motorola de fibertel, y similares, no hace falta mas nada. Abran el navegador a ver que pasa :KS

Espero que les haya servido, y si alguien se COPA con un espacio para poner el driver parcheado y ahorrarnos unos buenos pasos todos le estariamos muy agradecidos :D Salu2 y suerte!!
Cualquier duda posteen la salida de los comandos.

---

### Post by K-Pi on 2008-05-20
Nada, te estoy muy agradecido, pero el primer paso ya no va ---> rmmod r8169
Operation not permitted. No lo entiendo soy el administrador ROOT. :S

---

### Post by faktorqm on 2008-05-20
Estas seguro que sos root? Para mi que no eh!!

Yo tire abajo un modulo aca a ver que pasaba y me muestra esto:

```

faktorqm@the-edge:~$ rmmod fan
ERROR: Removing 'fan': Operation not permitted
faktorqm@the-edge:~$ sudo rmmod fan
faktorqm@the-edge:~$

```

Entonces me paso a root y no necesito mas el "sudo":

```
faktorqm@the-edge:~$ su
Contraseña: 
root@the-edge:/home/faktorqm# rmmod fbcon
root@the-edge:/home/faktorqm# 

```

Bueno tire dos modulos abajo que no se para que sirven. No lo prueben en casa!!! :lolflag: Salu2!

---

### Post by K-Pi on 2008-05-20
Consegui hacer --> rmmod r8169  con "sudo" delante, apartir de aqui todo bien hasta: 

carlos@carlos-asus-linux:~/kpi/drivers/realtek$ sudo make clean 
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset 
carlos@carlos-asus-linux:~/kpi/drivers/realtek$ sudo make modules 
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic' 
scripts/Makefile.build:41: /src/Makefile: No such file or directory 
make[2]: *** No rule to make target `/src/Makefile'.  Stop. 
make[1]: *** [_module_/src] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic' 
make: *** [modules] Error 2 

Espero que tenga solucion... Gracias

---

### Post by pabloatilio on 2008-05-20
> **K-Pi said:**
> Consegui hacer --> rmmod r8169  con "sudo" delante, apartir de aqui todo bien hasta: 

carlos@carlos-asus-linux:~/kpi/drivers/realtek$ sudo make clean 
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset 
carlos@carlos-asus-linux:~/kpi/drivers/realtek$ sudo make modules 
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic' 
scripts/Makefile.build:41: /src/Makefile: No such file or directory 
make[2]: *** No rule to make target `/src/Makefile'.  Stop. 
make[1]: *** [_module_/src] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic' 
make: *** [modules] Error 2 

Espero que tenga solucion... Gracias

Probá de hacer lo mismo sin sudo o probá de parchear de nuevo el driver, a mi me salió ese error y alguna de las dos cosas que te digo era la forma de solucionarlo, no recuerdo exactamente cual. Creo que también hice patch sin nada y después patch como se indica en ésta guía, lo mío era prueba y error a lo bestia, seguramente los muchachos del foro que la tienen un poco más clara te van a saber decir como es la onda. Doy fe que funciona porque en este preciso momento te estoy escribiendo desde la asus a6tc en ubuntu 8.04 , así que a no desanimarse que ya te va a salir !!. La guía que armó faktorqm está perfecta, así son los pasos.Ojo, mucho cuidado de bajar exactamente el driver que corresponde,les dejo a continuación los archivos que usé yo para instalarlo en mi máquina.

driver y patch : [http://rapidshare.com/files/116296015/r8168_scripts.zip.html](http://rapidshare.com/files/116296015/r8168_scripts.zip.html)
solo el driver : [http://rapidshare.com/files/116296641/r8168-8.005.00.tar.bz2.html](http://rapidshare.com/files/116296641/r8168-8.005.00.tar.bz2.html)

Te dejo una copia del historial de comandos de mi equipo de cuando instalé el PxTx (no me dejan poner malas palabras) driver, a ver si encontras algo que te sirva, fijate que "make clean" y "make modules" lo hice sin "sudo", por ahí no tiene nada que ver pero ésta es la forma en que lo pude instalar yo. Otra cosa que había hecho antes por probar es actualizar el kernel a pata, fijate que la versión mía es 2.6.24-17-generic, me bajé los archivos desde otro equipo y actualicé para probar si se arreglaba el problema, después hice ésta instalación, supongo que no es necesario que actualices, porque como dije, eso no corrigió el problema. El historial de comandos me tira lo siguiente :

sudo rmmod r8169  (remueve el módulo r8169)
sudo gedit /etc/modprobe.d/blacklist (para avisar al sistema que no cargue el módulo r8169, agrega a blacklist)
cd r8168-8.005.00
cd src
patch < r8168-8.005.00.hardy.diff.txt
cd ..
make clean
make modules
sudo make install
sudo depmod -a
sudo insmod ./src/r8168.ko
lsmod | grep r8168 (comprueba que el nuevo módulo se cargó)

( a partir de ésta línea lo leí en algún lado pero no creo que sea necesario que lo hagas yo lo hice porque tenia problemas con el blacklist)

cd
uname -r
cd /lib/modules/2.6.24-17-generic/kernel/drivers/net/
mv 8169.ko r8169.ko.bak
mv r8169.ko r8169.ko.bak
sudo mv r8169.ko r8169.ko.bak
lsmod | grep r8168
lsmod | grep r8169

Saludos
Pablo

---

### Post by K-Pi on 2008-05-20
Es que hago todo y como lo ha puesto en la guia. Nose, alomejor mi archivo descargado no es el correcto. Pasame el que utilizaste tu si no te sabe mal a [email]carlosbenitoservera@gmail.com[/email] 

Gracias

---

### Post by pabloatilio on 2008-05-20
> **K-Pi said:**
> Es que hago todo y como lo ha puesto en la guia. Nose, alomejor mi archivo descargado no es el correcto. Pasame el que utilizaste tu si no te sabe mal a [email]carlosbenitoservera@gmail.com[/email] 

Gracias

fijate ahi actualicé mi post anterior, tenés los enlaces con los drivers y el detalle del historial de comandos, seguilo como está a ver que pasa. Suerte !
Saludos
Pablo

---

### Post by K-Pi on 2008-05-20
LO CONSEGUI!!! mil gracias. Lo que me faltaba era el r8168.ko yo no lo tenia!! Gracias de verdad. Ahora solo me falta conectarlo mediante wifi (cosa más complicada verdad?) Saludos a los 2.

---

### Post by pabloatilio on 2008-05-20
> **K-Pi said:**
> LO CONSEGUI!!! mil gracias. Lo que me faltaba era el r8168.ko yo no lo tenia!! Gracias de verdad. Ahora solo me falta conectarlo mediante wifi (cosa más complicada verdad?) Saludos a los 2.

En principio creo que el .ko te lo genera el make pero si lo hiciste andar loco todo bien, me alegro por vos. Tenemos el mismo equipo, asi que te cuento que el wifi en cuanto me ponga a verlo si lo hago andar aviso por éste foro, y tengo un problemita también con el control de volúmen de sonido de gnome que si veo que es también dejo dicho. 

Felicitaciones, saludos.

Pablo

---

### Post by K-Pi on 2008-05-20
Gracias. Sí!! el control de volumen tambien, a cero o atope. Pero bueno... poco a poco. Saludos maquina!!

---

### Post by faktorqm on 2008-05-20
Che como hiciste al final, el .ko supuestamente es lo que compilaste. O te lo paso Pablo? por que si no podemos hacer 2 cosas, subir el driver parcheado para compilar, o pasar el .ko compilado (en este caso habria que ver el tema de 32 y 64 bits) y el tutorial se reduce a "nada", sin compilacion. Yo despues lo veo cualquier cosa. A todo esto, alguien con ubuntu 64 bits, se copa para compilar el driver y pasar el .ko compilado? Salu2!

---

### Post by pabloatilio on 2008-05-20
> **faktorqm said:**
> Che como hiciste al final, el .ko supuestamente es lo que compilaste. O te lo paso Pablo? por que si no podemos hacer 2 cosas, subir el driver parcheado para compilar, o pasar el .ko compilado (en este caso habria que ver el tema de 32 y 64 bits) y el tutorial se reduce a "nada", sin compilacion. Yo despues lo veo cualquier cosa. A todo esto, alguien con ubuntu 64 bits, se copa para compilar el driver y pasar el .ko compilado? Salu2!

En principio parece que el amigo copio el driver, de todos modos si una opción válida es pasar el .ko compilado , además de pasar a el blacklist el que no funciona (r8169) , le serviría a mucha gente  a la que le cuesta el  manejo de todo esto por consola, si es así, les dejo el driver compilado en 64 bits para AMD (osea AMD64) a continuación :

[http://rapidshare.com/files/116365285/r8168.ko.html](http://rapidshare.com/files/116365285/r8168.ko.html)

En uno de los enlaces que pase anteriormente también hay un .ko pero desconozco el orígen y la versión, el enlace es :

[http://rapidshare.com/files/116296015/r8168_scripts.zip.html](http://rapidshare.com/files/116296015/r8168_scripts.zip.html) (tiene el driver , el patch y el .ko)

Y el driver solamente , para compilar y divertirse el domingo mientras tomamos unos mates con la patrona está en :

[http://rapidshare.com/files/116296641/r8168-8.005.00.tar.bz2.html](http://rapidshare.com/files/116296641/r8168-8.005.00.tar.bz2.html)

Saludos
Pablo Atilio

---

### Post by faktorqm on 2008-05-20
Bueno, acá les paso lo que hice, al final compile el modulo yo :P y no me tiro ningún error, para mi que se mandaron alguna ustedes... :D
Igual no importa, respecto a lo que dije anteriormente, la notebook solo tiene AMD64, yo igual por las dudas quiero dejar el .ko para 32 bits, por si alguna vez esa placa sale en algun formato pci o pci-expresso usb.
Yo arranqué desde la compilacion, por supuesto no puedo sacar algo que n tengo :D

```

[COLOR="Red"]faktorqm@the-edge:~$[/COLOR] wget ftp://66.104.77.130/cn/nic/r8168-8.005.00.tar.bz2
--20:41:36--  ftp://66.104.77.130/cn/nic/r8168-8.005.00.tar.bz2
           => `r8168-8.005.00.tar.bz2'
Conectando a 66.104.77.130:21... conectado.
Identificándose como anonymous ... ¡Conectado!
==> SYST ... hecho.    ==> PWD ... hecho.
==> TYPE I ... hecho.  ==> CWD /cn/nic ... hecho.
==> PASV ... hecho.    ==> RETR r8168-8.005.00.tar.bz2 ... hecho.
Longitud: 41.614 (41K) (no autenticado)

100%[====================================>] 41.614        28.42K/s             

20:41:41(28.36 KB/s) - `r8168-8.005.00.tar.bz2' guardado [41614]

[COLOR="#ff0000"]faktorqm@the-edge:~$[/COLOR] tar jvxf r8168-8.005.00.tar.bz2
r8168-8.005.00/
r8168-8.005.00/Makefile
r8168-8.005.00/readme
r8168-8.005.00/.svn/
r8168-8.005.00/.svn/format
r8168-8.005.00/.svn/all-wcprops
r8168-8.005.00/.svn/prop-base/
r8168-8.005.00/.svn/text-base/
r8168-8.005.00/.svn/text-base/Makefile.svn-base
r8168-8.005.00/.svn/text-base/release_note.txt.svn-base
r8168-8.005.00/.svn/text-base/README.svn-base
r8168-8.005.00/.svn/entries
r8168-8.005.00/.svn/tmp/
r8168-8.005.00/.svn/tmp/prop-base/
r8168-8.005.00/.svn/tmp/text-base/
r8168-8.005.00/.svn/tmp/props/
r8168-8.005.00/.svn/props/
r8168-8.005.00/release_note.txt
r8168-8.005.00/src/
r8168-8.005.00/src/rtl_ioctl.h
r8168-8.005.00/src/Makefile
r8168-8.005.00/src/r8168_n.c
r8168-8.005.00/src/r8168.h
r8168-8.005.00/src/.svn/
r8168-8.005.00/src/.svn/format
r8168-8.005.00/src/.svn/all-wcprops
r8168-8.005.00/src/.svn/prop-base/
r8168-8.005.00/src/.svn/text-base/
r8168-8.005.00/src/.svn/text-base/Makefile.svn-base
r8168-8.005.00/src/.svn/text-base/rtl_ioctl.c.svn-base
r8168-8.005.00/src/.svn/text-base/r8168_n.c.svn-base
r8168-8.005.00/src/.svn/text-base/r8168.h.svn-base
r8168-8.005.00/src/.svn/text-base/rtl_ioctl.h.svn-base
r8168-8.005.00/src/.svn/entries
r8168-8.005.00/src/.svn/tmp/
r8168-8.005.00/src/.svn/tmp/prop-base/
r8168-8.005.00/src/.svn/tmp/text-base/
r8168-8.005.00/src/.svn/tmp/props/
r8168-8.005.00/src/.svn/props/
r8168-8.005.00/src/rtl_ioctl.c
r8168-8.005.00/src/Makefile_linux24x
[COLOR="#ff0000"]faktorqm@the-edge:~$[/COLOR] cd ~/r8168-8.005.00/src
[COLOR="#ff0000"]faktorqm@the-edge:~/r8168-8.005.00/src$[/COLOR]

```

Acá bajo el archivo .diff y el directorio src me queda:

```

[COLOR="#ff0000"]faktorqm@the-edge:~/r8168-8.005.00/src$[/COLOR] ls
Makefile           r8168-8.005.00.hardy.diff.txt  r8168_n.c    rtl_ioctl.h
Makefile_linux24x  r8168.h                        rtl_ioctl.c
[COLOR="#ff0000"]faktorqm@the-edge:~/r8168-8.005.00/src$[/COLOR] patch < r8168-8.005.00.hardy.diff.txt
patching file r8168.h
patching file r8168_n.c
[COLOR="#ff0000"]faktorqm@the-edge:~/r8168-8.005.00/src$[/COLOR] cd ..
[COLOR="#ff0000"]faktorqm@the-edge:~/r8168-8.005.00$[/COLOR] make clean
make -C src/ clean
make[1]: se ingresa al directorio `/home/faktorqm/r8168-8.005.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: se sale del directorio `/home/faktorqm/r8168-8.005.00/src'
[COLOR="#ff0000"]faktorqm@the-edge:~/r8168-8.005.00$[/COLOR] make modules
make -C src/ modules
make[1]: se ingresa al directorio `/home/faktorqm/r8168-8.005.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/faktorqm/r8168-8.005.00/src modules
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/faktorqm/r8168-8.005.00/src/r8168_n.o
/home/faktorqm/r8168-8.005.00/src/r8168_n.c:2236: aviso: se definió &#8216;rtl8168_phy_power_down&#8217; pero no se usa
include/asm/io_32.h: En la función &#8216;memcpy_fromio&#8217;:
include/asm/io_32.h:211: aviso: el paso del argumento 2 de &#8216;__memcpy&#8217; descarta los calificadores del tipo del destino del puntero
  LD [M]  /home/faktorqm/r8168-8.005.00/src/r8168.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/faktorqm/r8168-8.005.00/src/r8168.mod.o
  LD [M]  /home/faktorqm/r8168-8.005.00/src/r8168.ko
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.24-16-generic'
strip --strip-debug r8168.ko
make[1]: se sale del directorio `/home/faktorqm/r8168-8.005.00/src'
[COLOR="#ff0000"]faktorqm@the-edge:~/r8168-8.005.00$[/COLOR] cd src
[COLOR="#ff0000"]faktorqm@the-edge:~/r8168-8.005.00/src$[/COLOR] ls
Makefile  Makefile_linux24x  Module.symvers  r8168-8.005.00.hardy.diff.txt  r8168.h  [COLOR="Blue"]**r8168.ko**[/COLOR]  r8168.mod.c  r8168.mod.o  r8168_n.c  r8168_n.o  r8168.o  rtl_ioctl.c  rtl_ioctl.h
[COLOR="Red"]faktorqm@the-edge:~/r8168-8.005.00/src$[/COLOR] 

```

Bueno ahi le puse colores para que vean que la secuencia de comandos es la misma que yo les puse en la guia y que me genera el .ko perfectamente y sin error. Acá el link, igual me parece que voy a armar otra guía con los modulos compilados con el driver ya parcheado, es mas facil, aunque a mas de uno le habra gustado mandarse esta proeza :lolflag:

[http://rapidshare.com/files/116401304/r8168.ko](http://rapidshare.com/files/116401304/r8168.ko) 

32 BITS OJO!!!!!!!!!

Bueno creo que por hoy nada más, mañana reviso y recopilo la versión 3 de la guía, quería agradecerles también a ustedes dos por dar feedback y ponerle onda a solucionar los problems :D Salu2!!!

---

### Post by pabloatilio on 2008-05-21
Aclaro que yo compilé sin problemas , haciendo todo como aparece en el historial de comandos que puse más arriba y salió todo bien, pude instalar todo siguiendo la guía de faktorqm y bajando el driver correcto , por eso es que dejé también un enlace con el driver compilado para AMD64 (ver también más arriba). En un momento me tiró un error pero problablemente fue un garfio mal puesto, porque volví a hacer todo y salió todo bien, nunca hice una copia del driver. Por eso quiero aclarar que el que **no quiera compilar** y tenga un equipo con arquitectura AMD64 puede usar tranquilo el driver que dejé, que no va a tener  problemas.

Pasando en limpio

El **driver compilado para amd64** lo tienen en :

[http://rapidshare.com/files/116365285/r8168.ko.html](http://rapidshare.com/files/116365285/r8168.ko.html)

El **driver para compilar, el patch y el .ko** lo tienen en :

[http://rapidshare.com/files/116296015/r8168_scripts.zip.html](http://rapidshare.com/files/116296015/r8168_scripts.zip.html)

Solo el **driver para compilar**:

[http://rapidshare.com/files/116296641/r8168-8.005.00.tar.bz2.html](http://rapidshare.com/files/116296641/r8168-8.005.00.tar.bz2.html)

El **driver compilado 32 bits** gentileza de faktorqm:

[http://rapidshare.com/files/116401304/r8168.ko](http://rapidshare.com/files/116401304/r8168.ko)


Salu2
PabloAtilio

---

### Post by sneider on 2008-06-13
**Muchisimas gracias por la explicacion y por el archivo .ko**

Al ser un problema de red, no podia conectar desde linux para compilar, asi que el fichero ya compilado me ha venido de perlas.

por fin vuelvo a tener mi linux utilizable en mi portatil, parece mentira, pero hoy dia sin internet un ordenador parece un trasto inutil :)

Ahora me gustaria conseguir que via wifi tambien funcione, y el que funcione bien el control de volumen estaria bien, ese nunca me ha funciona bien en ninguna version de ubuntu. Ademas de sonar a tope, hay una posicion de la barra de audio en la que se acopla el sonido y te deja sordo :mad:

En fin, muchas gracias de nuevo. Me habeis alegrado el dia :lolflag:

---

### Post by sneider on 2008-06-13
¡Horror! Al tener ubuntu recuperado con internet, le di a actualizar, y parece que con la ultima actualizacion el .ko ya no se puede usar.

al hacer el insmod me dice:

Error inserting 'r8168.ko': -1 Invalid module format

---

### Post by pabloatilio on 2008-06-16
> **sneider said:**
> ¡Horror! Al tener ubuntu recuperado con internet, le di a actualizar, y parece que con la ultima actualizacion el .ko ya no se puede usar.

al hacer el insmod me dice:

Error inserting 'r8168.ko': -1 Invalid module format

Hola, yo no tuve ese problema, a mi me funcionó bien siempre, a pesar de todas las actualizaciones que hice, probá de compilar vos mismo el driver , siguiendo las explicaciones que se dejaron en éste post deberías poder hacerlo sin problemas, o sino probá de instalarlo de nuevo como sea que lo hayas hecho. Es raro, quizás pusiste un driver compilado para una versión de kernel y después en alguna actualización te cambió el kernel (por ej 64 bits versus 32 bits o amd64 a i386), probá de copiar alguno de los otros drivers compilados y reemplazarlo a ver que pasa,  que es la forma más fácil si no estás muy ducho en todo esto de compilar y esas cosas.

Con respecto al WiFi de mi notebook que es una Asus a6tc es el BCM4318 de Broadcom Corporation estoy trabajando en eso,  si tengo alguna solución la dejo publicada en éste foro y del volúmen ya veremos.

Saludos

---

### Post by faktorqm on 2008-06-17
Che por que no abris un nuevo thread con eso a ver si podemos hacerla andar? Salu2!

---

### Post by pabloatilio on 2008-06-18
> **pabloatilio said:**
> Hola, yo no tuve ese problema, a mi me funcionó bien siempre, a pesar de todas las actualizaciones que hice, probá de compilar vos mismo el driver , siguiendo las explicaciones que se dejaron en éste post deberías poder hacerlo sin problemas, o sino probá de instalarlo de nuevo como sea que lo hayas hecho. Es raro, quizás pusiste un driver compilado para una versión de kernel y después en alguna actualización te cambió el kernel (por ej 64 bits versus 32 bits o amd64 a i386), probá de copiar alguno de los otros drivers compilados y reemplazarlo a ver que pasa,  que es la forma más fácil si no estás muy ducho en todo esto de compilar y esas cosas.

Con respecto al WiFi de mi notebook que es una Asus a6tc es el BCM4318 de Broadcom Corporation estoy trabajando en eso,  si tengo alguna solución la dejo publicada en éste foro y del volúmen ya veremos.

Saludos

Amigo, con las actualizaciones que venia haciendo no tuve problemas, pero ayer a la noche actualicé al  2.6.24-19-generic y me desconfiguró la tarjeta de video y la placa de red, de todos modos, imagino que la solución es la misma que te comentaba antes, yo por ahora inicio con el kernel anterior hasta que tenga ganas de ponerme con eso. Tenías razón.
Saludos
Pablo

---

### Post by pabloatilio on 2008-06-18
> **faktorqm said:**
> Che por que no abris un nuevo thread con eso a ver si podemos hacerla andar? Salu2!

Hola 
Imagino que te referís al wi-fi y al sonido, estoy corto de tiempo estos días, pero en cuanto safe de los compromisos , si soluciono lo de la red   o lo del volumen dejo la solución en el foro (creo que ya estoy cerca).
Saludos

---

