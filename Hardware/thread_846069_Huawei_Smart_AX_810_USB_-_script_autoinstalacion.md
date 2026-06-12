---
title: "Huawei Smart AX 810 USB - script autoinstalacion"
date: 2008-07-01
forum: Hardware
---

### Post by faktorqm on 2008-07-01
Hola loco, queda un mes para la inauguracion oficial de la pagina, y bueno, yo estuve laburando en lo mio para ir manejando mejor los tiempos. 
La cosa es que finalicé en un script de instalacion que tiene todo lo necesario (supuestamente) para que vos ni bien terminas de poner el cd de ubuntu 8.04, corras el script y el alfajor del diablo cambie su nombre por "alfajor amansado por faktorqm" :P :P

La cosa es la siguiente, como no tengo el modem, lo unico que hago es colgar la terminal, pero supuestamente anda el script. Como no se programar en bash, pero si en C, me di un ratito la kbza contra el monitor y saque andando algo, pero que necesito de alguien que ya haya hecho esto me ayude un poqui y me tire alguna manito. Les dejo el paquete de instalacion y el script. El paquete ya incluye el script, yo lo pego aca para que aquel que me quiera ayudar no se tenga ke bajar el paquete y etcetc

AVISO 1: ESTE SCRIPT ES SOLO PARA 32 bits. si lo queres para 64 tenes que cambiar la linea del br2684ctl por el paquete de 64. Cuando alguien ponga el if que anda despues le pregunto al usuario si tiene 32 o 64 bits.

AVISO 2: Hay que corregir algunas cosas como el tema de los permisos innecesarios, digamos, yo orienté todo a utilizar lo minimizimo necesario para hacer que ande, ni mas, ni menos. Por eso el paquete pesa 25kb xD

AVISO 3: Si lo probaste y no te anda, posteá la salida del script digamos, que el br2684ctl por lo general dice cual es error, la salida de lsmod y dmesg | tail.


```

#!/bin/bash

echo ""
echo "¿Qué empresa posee?"
echo ""
echo "1- Speedy (Telefónica)"
echo "2- Arnet (Telecom)"
echo "3- Otra"
echo "4- Salir"
echo ""
read ISP
# Muestro mensaje de opcion para que el user elija empresa y
# "leo" lo que ingreso

case $ISP in
"1")
VCI="8"
VPI="35"
;;
"2")
VCI="0"
VPI="33"
;;
"3")
echo ""
echo "Ingrese VCI:"
read VCI
echo ""
echo "Ingrese VPI:"
read VPI
;;
"4")
exit 0
;;
*)
echo "Opción incorrecta, se sale del script"
exit 0
;;
esac

# Estructura case MUY similar a C, si elije otra compañia ingresa a mano
# los datos, el asterisco es el equivalente al default en C

mkdir -m 777 -p /lib/firmware/ueagle
# Creo el directorio ueagle y le doy permisos totales (FEO FEO)

cp -af "`pwd`"/firmware/eagleII.fw /lib/firmware/ueagle/eagleII.fw
# Copio el firmware a la carpeta que cree antes, desde la ubicacion actual
# (posicion relativa) las comillas son para evitar carpetas con nombres  con espacios

dpkg -i br2684ctl_20040226-1_i386.deb
# Instalo el paquete br2684 necesario para hacer pppoe.
####
# Aca deberia ir una estructura de tipo if que haga:
# if [ uname -m = i686 ]
# dpkg -i br2684ctl_20040226-1_i386.deb
# else
# dpkg -i br2684ctl_20040226-1_amd64.deb
# fi
# pero lamentablemente no me salio....
####

echo "Introduzca su nombre de usuario:"
read USER
# Pido nombre de usuario

echo "Introduzca su contraseña:"
read PASS
# Pido contraseña

echo "noipdefault" > /etc/ppp/peers/proveedor
echo "defaultroute" >> /etc/ppp/peers/proveedor
echo "user '$USER'" >> /etc/ppp/peers/proveedor
echo "password '$PASS'" >> /etc/ppp/peers/proveedor
echo "noauth" >> /etc/ppp/peers/proveedor
echo "updetach" >> /etc/ppp/peers/proveedor
echo "usepeerdns" >> /etc/ppp/peers/proveedor
echo "plugin rp-pppoe.so" >> /etc/ppp/peers/proveedor
echo "nas0" >> /etc/ppp/peers/proveedor
# Acá lo que hago es hacer a mano lo que hace el pppoeconf digamos, que es
# crearte el archivo con las opciones de ppp, y lo llamo proveedor. 
# Notar que el primero NO CONCATENA, si existe lo limpia y lo hace de
# vuelta, esto lo hice para los usuarios que corren el script 20 veces....

echo "\"$USER\" \"*\" \"$PASS\"" > /etc/ppp/chap-secrets
echo "\"$USER\" \"*\" \"$PASS\"" > /etc/ppp/pap-secrets
chmod 744 /etc/ppp/chap-secrets
chmod 744 /etc/ppp/pap-secrets
# Guardo usuario y contraseña en esos dos archivos, pero no se por que cuando lo
# hago me lo crea como root (en realidad esta bien por que lo corro con sudo) pero
# no se si el usuario despues lo puede usar... de ultima es cuestion de probar

echo "#!/bin/bash" > /etc/init.d/adsl_up
echo "br2684ctl -b -c 0 -a $VCI.$VPI" >> /etc/init.d/adsl_up
echo "ifconfig nas0 up" >> /etc/init.d/adsl_up
echo "pon dsl-provider" >> /etc/init.d/adsl_up
# Aca creo el script para que cuando arranque el sistema se conecte automaticamente

# sh /etc/init.d/adsl_up
# Con esta instruccion tengo dudas, por que yo lo que queria hacer era que el usuario
# no reinicie la primera vez, pero me parecia mal repetir el codigo que iba al script
# de inicio, entonces decidi autoejecutarlo desde acá, así es mas prolijo. Peeeeero
# tampoco me salio... :( me dice que no puedo correr eso sin permisos creo.

exit 0
# Con esto salgo sin error, esto es para mantener el "unix-style"

```

Es lo mismo correrlo en una maquina virtual con el modem enchufado? No lo voy a hacer, pero me queria sacar la duda xD para ver si alguien se copaba :D

Bueno, escucho ofertas. Salu2!!!

---

### Post by faktorqm on 2008-07-04
Bueno, acá va el script con mil mejoras... y el nuevo paquete. Este parece que anda :P 

```

#!/bin/bash

echo ""
echo "¿Qué empresa posee?"
echo ""
echo "1- Speedy (Telefónica)"
echo "2- Arnet (Telecom)"
echo "3- Otra"
echo "4- Salir"
echo ""
read ISP
# Muestro mensaje de opcion para que el user elija empresa y
# "leo" lo que ingreso

case $ISP in
"1")
VCI="8"
VPI="35"
;;
"2")
VCI="0"
VPI="33"
;;
"3")
echo ""
echo "Ingrese VCI:"
read VCI
echo ""
echo "Ingrese VPI:"
read VPI
;;
"4")
exit 0
;;
*)
echo "Opción incorrecta, se sale del script"
exit 0
;;
esac

# Estructura case MUY similar a C, si elije otra compañia ingresa a mano
# los datos, el asterisco es el equivalente al default en C

mkdir -m 777 -p /lib/firmware/ueagle
# Creo el directorio ueagle y le doy permisos totales (FEO FEO)

cp -af "$(pwd)"/firmware/eagleII.fw /lib/firmware/ueagle/eagleII.fw
# Copio el firmware a la carpeta que cree antes, desde la ubicacion actual
# (posicion relativa) y le pongo comillas para costear el problema de las
# carpetas con espacios.

if [ $(uname -m) = "i686" ]; then
	dpkg -i br2684ctl_20040226-1_i386.deb
else
	dpkg -i br2684ctl_20040226-1_amd64.deb
fi
# Me fijo si tiene 32 o 64 bits e instalo el paquete correcto

echo ""
echo "Introduzca su nombre de usuario:"
read USUARIO
# Pido nombre de usuario

echo ""
echo "Introduzca su contraseña:"
read PASS
# Pido contraseña

echo "noipdefault
defaultroute
hide-password
user '$USUARIO'
password '$PASS'
noauth
updetach
usepeerdns
plugin rp-pppoe.so
nas0" > /etc/ppp/peers/proveedor

chmod 744 /etc/ppp/peers/proveedor
# Acá lo que hago es hacer a mano lo que hace el pppoeconf digamos, que es
# crearte el archivo con las opciones de ppp, y lo llamo proveedor. 
# Notar que NO CONCATENA, si existe lo limpia y lo hace de
# vuelta, esto lo hice para los usuarios que corren el script 20 veces...


echo "\"$USUARIO\" \"*\" \"$PASS\"" > /etc/ppp/chap-secrets
echo "\"$USUARIO\" \"*\" \"$PASS\"" > /etc/ppp/pap-secrets
chmod 755 /etc/ppp/chap-secrets
chmod 755 /etc/ppp/pap-secrets
# Guardo usuario y contraseña en esos dos archivos, pero no se por que cuando lo
# hago me lo crea como root (en realidad esta bien por que lo corro con sudo) pero
# no se si el usuario despues lo puede usar... de ultima es cuestion de probar

echo "#!/bin/bash
br2684ctl -b -c 0 -a $VCI.$VPI
ifconfig nas0 up
pon proveedor" > /etc/init.d/adsl_up

chmod +x /etc/init.d/adsl_up
# Aca creo el script para que cuando arranque el sistema se conecte automaticamente
# y le doy permisos de ejecucion

/etc/init.d/adsl_up
# Ejecuto el script creado anteriormente y me conecto

exit 0
# Con esto salgo sin error.

```

Cuando lo ejecuto ocurre lo siguiente:

```

faktorqm@the-edge:~$ sudo sh black_script_eagle_v0.4.sh
[sudo] password for faktorqm: 

¿Qué empresa posee?

1- Speedy (Telefónica)
2- Arnet (Telecom)
3- Otra
4- Salir

1
(Leyendo la base de datos ...  
93673 ficheros y directorios instalados actualmente.)
Preparando para reemplazar br2684ctl 20040226-1 (usando br2684ctl_20040226-1_i386.deb) ...
Desempaquetando el reemplazo de br2684ctl ...
Configurando br2684ctl (20040226-1) ...

Introduzca su nombre de usuario:
ricardo

Introduzca su contraseña:
tuvieja
[SIZE="4"][COLOR="Red"]: not foundt_eagle_v0.4.sh: 85: [/COLOR][/SIZE]
br2684ctl[6630]: Interface "nas0" could not be created, reason: File exists
br2684ctl[6630]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[6630]: Fatal: failed to connect on socket
SIOCSIFFLAGS: Argumento inválido
Plugin rp-pppoe.so loaded.
sendPacket: send: Network is down
faktorqm@the-edge:~$ 

```

Bueno el único problema que tengo es la linea marcada en rojo... no se que significa por que es como que escribe arriba del error, y la linea 85 es vacia, la anterior es ```
chmod 744 /etc/ppp/peers/proveedor
``` y la siguiente es ```
echo "\"$USUARIO\" \"*\" \"$PASS\"" > /etc/ppp/chap-secrets
``` ¿Alguna sugerencia?

Dejo el paquete nuevo. Agradeceria que alguien que tiene el modem lo probara. :KS Salu2!

---

### Post by faktorqm on 2008-07-14
Hola loco, nueva versión del script de instalación, ahora quedo una masa, ya me estoy acercando a algo un poco más profesional, por que la verdad que las betas anteriores dejaban bastante que desear... :D

```

#!/bin/bash

ARCHIVO_FIRMWARE_ORIGEN="$(pwd)/firmware/eagleII.fw"
DIR_DESTINO="/lib/firmware/ueagle/"
DIR_CONF="/etc/ppp"
BR_32="br2684ctl_20040226-1_i386.deb"
BR_64="br2684ctl_20040226-1_amd64.deb"
PPP_32="pppoe_3.8-3_i386.deb"
PPP_64="pppoe_3.8-3_amd64.deb"
# Declaro etiquetas

echo "
Script de instalación para modems adsl usb con chipset eagle

¿Qué empresa posee?

1- Speedy (Telefónica)
2- Arnet (Telecom)
3- Otra
4- Salir
"
read ISP
# Muestro mensaje de opcion para que el user elija empresa

case $ISP in
"1")
VCI="8"
VPI="35"
;;
"2")
VCI="0"
VPI="33"
;;
"3")
echo "
Ingrese VCI:"
read VCI
echo "
Ingrese VPI:"
read VPI
;;
"4")
echo "
Se sale del script
"
exit 0
;;
*)
echo "Opción incorrecta, se sale del script"
exit 0
;;
esac
# Estructura case, si elije otra compañia ingresa a mano
# los datos, el asterisco es la opcion por defecto

mkdir -m 755 -p $DIR_DESTINO
# Creo el directorio ueagle y le doy permisos

cp -af "$ARCHIVO_FIRMWARE_ORIGEN" $DIR_DESTINO
# Copio el firmware a la carpeta que cree antes, desde la ubicacion actual
# (posicion relativa) y le pongo comillas para costear el problema
# de las carpetas con espacios.

if [ $(uname -m) = "i686" ]; then
	dpkg -i -G -O -E $BR_32 $PPP_32
else
	dpkg -i -G -O -E $BR_64 $PPP_64
fi
# Me fijo si tiene 32 o 64 bits e instalo los paquetes correctos, si tiene
# instaladas versiones posteriores o una version idéntica a la que yo quiero
# instalar, lo saltea. Aparte de esto solo selecciona estos 2 paquetes, asi
# salteo el problema de las actualizaciones y demás.

echo "
Introduzca su nombre de usuario: "
read USUARIO
# Pido nombre de usuario

echo "
Introduzca su contraseña: "
read PASS
# Pido contraseña

echo "noipdefault
defaultroute
hide-password
user '$USUARIO'
password '$PASS'
noauth
updetach
usepeerdns
plugin rp-pppoe.so
nas0" | tee /etc/ppp/peers/proveedor
# Acá lo que hago es hacer a mano lo que hace el pppoeconf digamos, que es
# crearte el archivo con las opciones de ppp, y lo llamo proveedor. 
# Notar que NO CONCATENA, si existe lo limpia

echo "\"$USUARIO\" \"*\" \"$PASS\"" | tee $DIR_CONF/chap-secrets $DIR_CONF/pap-secrets
# Guardo usuario y contraseña en esos dos archivos, borra lo que esta y escribe

echo "pppoatm
br2684" | tee -a /etc/modules
# Escribo el archivo modules para que levante esos dos modulos cada vez que inicie
# con el append del tee, para no borrar lo que estaba antes

modprobe -a pppoatm br2684
# Levanto los 2 modulos a mano solo para no reiniciar la primera vez

echo "#!/bin/bash

br2684ctl -b -c 0 -a $VCI.$VPI
ifconfig nas0 up
pon proveedor" | tee /etc/init.d/adsl_up

chmod +x /etc/init.d/adsl_up
# Aca creo el script para que cuando arranque el sistema se conecte automaticamente
# y le doy permisos de ejecucion

/etc/init.d/adsl_up
# Ejecuto el script creado anteriormente y me conecto

exit 0
# Con esto salgo sin error.

```

Bueno el error es el mismo que el de arriba, solo que ahora lo muestra en la linea 97. No se que pasa, si ejecuto la ultima instruccion por separado no me tira ningun error. Todo mal con eso, pero bueno. El script funciona perfecto! Aun con esa especie de "warning". Tendre que usar algún pause? Salu2!!!

---

### Post by faktorqm on 2008-07-23
Tiro un bump acá a ver si de casualidad a alguien se le pasó este thread y me puede ayudar :D Salu2!!

---

### Post by FlyerDie on 2008-07-23
no tendras un null en vez de un CR por ahi no? en la linea 95 digo..
Ojo, no tengo grandes conocimientos en programacion, pero se que aveces esas cosas pueden joder

---

### Post by faktorqm on 2008-07-24
Si yo pensé lo mismo... pero no era... :(
Acá dejo el paquete con el último script funcionando salvo ese pequeñisimo error... Salu2!

---

### Post by godzeus on 2008-07-24
Faktorqm:
         muy bueno el aporte, te comento un poco mi caso.
Yo lo tenia andando al alfajorcito del diablo, por un tutorial que saque de los foros de kubuntu, lo adapte a Ubuntu(el cambio es minimo)y lo tenia andando joya. Ahora me compre un router ethernet y al disquito del demonio lo archive.
El tema es que no sabria como probarlo, porque ya tengo instalado todos los paquetes, modulos y dependencias.
Si me podes tirar alguna idea de como probarlo (yo pensaria en una VM, pero no se si servira), seguro que te puedo ayudar para resolver el error que sale.
O si alguien de el foro quiere el modem, se lo doy para que pruebe y de paso podemos terminar de solucionar el error, y dejar el script chiche bombón.

Saludos:)

---

### Post by faktorqm on 2008-07-24
Gracias! :KS

Es que sabés lo que pasa? el script anda! ya lo probó un chabón antes, y se conecto feliz, el tema esa especie de warning que sale.... estoy pensando que capaz es un tema de bash pero es facil hecharle la culpa a otro :P 
En una VM no tengo idea si anda, de hecho lo pregunte mas arriba, si lo queres probar..... lo dejo a tu criterio jajajaja

Tendria que hacer un desinstalador de este script, así cuando ocurre un caso como el tuyo se liberan los paquetes que ya no se usan... me voy a poner a hacer tonces... pasame el tuto que hiciste vos y lo veo (yo vi mil y son todos distintos :o)

Gracias y saludos!!!!

---

### Post by godzeus on 2008-07-30
> **faktorqm said:**
> Gracias! :KS

Es que sabés lo que pasa? el script anda! ya lo probó un chabón antes, y se conecto feliz, el tema esa especie de warning que sale.... estoy pensando que capaz es un tema de bash pero es facil hecharle la culpa a otro :P 
En una VM no tengo idea si anda, de hecho lo pregunte mas arriba, si lo queres probar..... lo dejo a tu criterio jajajaja

Tendria que hacer un desinstalador de este script, así cuando ocurre un caso como el tuyo se liberan los paquetes que ya no se usan... me voy a poner a hacer tonces... pasame el tuto que hiciste vos y lo veo (yo vi mil y son todos distintos :o)

Gracias y saludos!!!!

Mil disculpas por la demora, pero estoy a full en el laburo, el link de donde saque el tuto es [http://www.ubuntu-es.org/index.php?q=node/36369](http://www.ubuntu-es.org/index.php?q=node/36369), el mismo lo empece a usar en Edgy y lo fui adaptando a medida que actualizaba, para Hardy la unica diferencia es que al principio pide conpilar los drivers, cosa que no hay que hacer porque Hardy ya los trae soportados en el kernel, solo hay que copiar el firmware.
El resto lo hice todo al pie de la letra y siempre funciono.

Saludos:)

---

### Post by faktorqm on 2008-09-02
Tenemos nueva versión!

Corregido el error de la linea que tiraba warning, actualizacion de la cantidad de informacion mostrada en pantalla, corregido el dpkg para que seleccione los paquetes, creacion de un desinstalador, mejora en script de inicio.

Explicación de uso:

1) bajar el paquete en el escritorio
2) click derecho -> extraer aqui
3) aplicaciones -> accesorios terminal
4) copiar y pegar el siguiente comando:

```
sudo sh Escritorio/huawei810v0.7/black_script_eagle_v0.7.sh
```

eso arrancará el instalador que instalará 2 paquetes, te pregunta empresa, usuario y contraseña.
5) abrir el navegador y si todo salio bien, a disfrutar!

Para desinstalar: (con el paquete en el escritorio)

1) aplicaciones -> accesorios terminal
2) copiar y pegar el siguiente comando:

```
sudo sh Escritorio/huawei810v0.7/eagle_uninstaller_v0.1.sh
```

Salu2!!!

---

### Post by victor_nesta on 2008-09-02
Gracias lo tengo que probar.
Abría que hacer un Sticky de estos scrips!

---

### Post by faktorqm on 2008-09-02
Todavia no, cuando tengamos version 1.0 (o version estable en su defecto) lo ponemos. en el xubu no se si anda por que no se que paquetes por defecto trae la instalacion, asi que si lo corres este y no te anda, vamos a tener que ver que paquetes estan y que no, por que originalmente este script lo hice para ubuntu 8.04. asi que de paso cañaso capaz me vendria bien hacerlo extensivo a xubuntu y capaz a kubuntu. Salu2!

---

### Post by Hei Ku on 2008-09-08
Faktor, viste esta herramienta? [http://www.ubudsl.com](http://www.ubudsl.com)
Capaz podrias integrar tu trabajo ahí. El único tema es que no tiene traducción al español, pero gente de la comunidad podríamos ayudar para eso.

---

### Post by faktorqm on 2008-09-08
Si lo vi, uno mando un mail a la lista hace un tiempo y le respondi. La cosa es que ese programa es incompatible con lo que yo quiero hacer, yo quiero lograr un script, con lo justo y necesario para que funcione el modem, en ubuntu y en argentina. Ese invento con interfaz grafica necesita muchas bibliotecas, y es para los modems de todo el mundo, y para muchos gnu/linux's distintos (aunque ahora solo soporten 2...).
De todas maneras ahora que lo pienso un segundo más, sin dejar de "hacer entrega en mi formato" muy tranquilamente se lo puedo pasar para que lo agreguen a su "cosa" y aportar algo que quiza les sirva a ellos. 
Salu2!!

---

### Post by Hei Ku on 2008-12-05
Esto esta actualizado? Si es así, lo pongo como sticky.

---

### Post by faktorqm on 2008-12-06
El post que va es este: [http://ubuntuforums.org/showpost.php?p=5712035&postcount=10](http://ubuntuforums.org/showpost.php?p=5712035&postcount=10)

Lo que en algunos casos vi es que levanta la conexión en el momento de la instalación, pero no cuando apagas y volves a prender la compu. A otros les anduvo de una. Sería cuestión, o de conseguir a alguien que le sobre el modem, me lo preste y probar a full, o que vayan haciendo feedback hasta que tengamos la certeza de que anda 100%.

Salu2!

---

### Post by alemasdiez on 2009-04-11
gente.. muuuy util el post; por primera vez me siento cerca de lograrlo :)

mi problema es el siguiente, en ningun momento parpadean u algo las 3 luces está siempre prendidas y creo que es por eso que no puedo conectarme, adjunto imagen del error.

saludos y gracias

---

### Post by alemasdiez on 2009-04-11
gente, había toqueteado taaanto que ya no se podía hacer análisis alguno ergo reinstalé ubuntu 8.10 y utilicé el script de uds.

Ahora las luces tienen un comportamiento "normal" (simil al que tengo con windows) pero sigo sin poder conectarme.

Adjunto imagen de error:

---

### Post by faktorqm on 2009-04-14
Hola, me alegro de que estes probando mi script y que hagas feedback.

El comando lo tenes que correr asi:

```
sudo sh black_script_eagle_v0.7.sh
```

y ahi te va a pedir tu contraseña (la que usas cuando arrancas la compu) y ahi vas a ver que te deja de decir "permiso denegado" por todos lados. salu2!!!

---

### Post by alemasdiez on 2009-04-14
al reves! gracias a vos pincha por contestar y ayudar! 

Formatié, volví a instalar pero... volví al primer problema:
"
update-rc.d: warning: /etc/init.d/adsl_up missing LSB style header
"

en contexto:

alejandro@indio00:~/Escritorio/huawei810v0.7$ sudo sh black_script_eagle_v0.7.sh
Script de instalación para modems adsl usb con chipset eagle

¿Qué empresa posee?
1- Speedy (Telefónica)
2- Arnet (Telecom)
3- Otra
4- Salir
2

Introduzca su nombre de usuario: 
alevit@arnet-rosario-apd
Introduzca su contraseña: 
****


update-rc.d: warning: /etc/init.d/adsl_up missing LSB style header

La instalación ha finalizado con éxito

nótese que me dice que que se ha instalado con éxito, sin embargo está ese erros y no me puedo conectar (la luz del modem no indica conexión y al abrir el firefox no accede a ninguna web).


Gracias por la atención!

---

### Post by alemasdiez on 2009-04-14
me faltó aclarar que br2684ctl está instalado...

---

### Post by faktorqm on 2009-04-15
Hola, el error ese es por que no tiene un encabezado que lo pusieron hace poco los de debian (por lo tanto ubuntu tambien) y no interfiere en la ejecucion del script, por eso te dice que termino con exito, por que en realidad verdaderamente lo hizo. 

Lo que hay que agregar en el script para que no te tire ese error es:

```

### BEGIN INIT INFO
    # Provides:          faktorqm
    # Required-Start:    $syslog
    # Required-Stop:     $syslog
    # Should-Start:	 
    # Should-Stop:	
    # Default-Start:     2 3 4 5
    # Default-Stop:      1 6
    # Short-Description: Starts the ADSL connection at boot time
    # Description:       Controls the ADSL USB modem trough 
    #                    br2684ctl package.
### END INIT INFO

```

y esto va debajo de donde dice #!/bin/bash

Voy a consultar el problema con una persona y vemos la solución, hace rato que quiero terminar con esto. Gracias por la paciencia y saludos!

---

### Post by alemasdiez on 2009-04-17
HOLA faktorqm!!!" a qué no sabés de dónde te estoy llamando?"(no creo que nadie se acuerde de esa publi)


MUUUUUUUUUUCHAS GRACIAS!!!


Me da un poco de vergüenza decir mi error de novato pero le puede llegar a pasar a otro asi lo que lo dejo registrado:
en el firefox tenía marcada la opcion "trabajar sin conexión" sé que soy un pichon ...

---

### Post by faktorqm on 2009-04-17
ahh bueno pero entonces te anduvo bien?? queria saber eso. por que estaba hablando con marco de hoyos (un groso que sabe de verdad) y no encontrabamos el problema, pensamos que estaba en la parte que inicia la conexion cuando arranca la computadora, pero habia que ver 1500 cosas.... :(

Bueno me alegro mucho de que te haya funcionado, uno mas a la lista! :D Saludos!!!!

---

### Post by alemasdiez on 2009-04-23
sep, muchas gracias otra vez!

ah, por cierto no encuentro la "medallita"

---

### Post by faktorqm on 2009-04-23
Lamentablemente la sacaron, no recuerdo muy bien por que, igual lo habian comentado en algun post por ahi. Y ahora, shaunn como va a saber quien ayuda mas en el foro? JAUJAJAJJAJAJa
Salu2!

---

### Post by revan24 on 2009-08-15
No se si esta post seguira activo pero quisiera saber si este script funciona para ubuntu 9.04 porq no he podido hacer andar este modem..
Saludos

---

### Post by alemasdiez on 2009-08-16
> **revan24 said:**
> No se si esta post seguira activo pero quisiera saber si este script funciona para ubuntu 9.04 porq no he podido hacer andar este modem..
Saludos

sep, hasta hace poco andaba de 10 ahora me pasé al pirelli; pero deberías llamar a telecom/telefónica (la compañia que te provee el servicio a Internet) para que te lo cambien porque no anda bien; a mi me lo hicieron "sin cargo".

Saludos

---

### Post by faktorqm on 2009-08-25
estoy, estoy. problema? descripcion? zona de residencia? que es lo que no te anda? tenes todos los cables bien? ejecutaste para 9.04 y no te anduvo? solo queres saberlo? decime que onda. En un principio si no cambiaron muuuuucho los paquetes creo que deberia andar. Sino siempre podes consultar un proyecto que anda bastante bien (aunque a mi no me gusta, no por favoritismo por mi script, claro esta, sino por que te instala demasiadas cosas para algo tan concreto como conectarte a internet) que se llama ubudsl. ([http://www.ubudsl.com/es/inicio.php](http://www.ubudsl.com/es/inicio.php))

Yo me contacte con el desarrollador, que aparte de tener cero onda su unica respuesta fue "su script no tiene nada que no haga el mio y viceversa". Lo cual por un lado me dejo mas tranquilo, pero por otro me saco las ganas de seguir preguntandole algo. 

Nada, comenta que onda. salu2!

---

