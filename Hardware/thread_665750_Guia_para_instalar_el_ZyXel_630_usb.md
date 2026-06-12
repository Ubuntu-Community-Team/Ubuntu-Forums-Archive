---
title: "Guia para instalar el ZyXel 630 usb"
date: 2008-01-12
forum: Hardware
---

### Post by steve_ignorant on 2008-01-12
buenoquiero subir una guia aca para poder hacer andar el modem que da speedy, en mi caso tenia un speed touch 330, pero los muchachos de telefonica mandaron corriente a los cables para secarlos despues de una tormenta y fallecio mi speedtouch, llame a speedy y pedi el cambio de modem, y pedi un eth. y me trajeron este que es solamente por usb,

logre hacerlo andar y pregunto si puedo postearla, si bien la encontre en ingles en estos foros, no encontre una guia en castellano, y pienso que no todos saben ingles, y que quizas poniendo la guia que hice yo en castellano pueda servir de algo.

---

### Post by erginemr on 2008-01-12
Hola,

No le he entendido bien, porque mi castellano no es si bueno, pero ha usted podido installar el modem usb a Ubuntu? Si no, he encontrado un programa en deb quien puede installarlo fácilmente y puedo postarlo aquí si usted quiere.

Hay también una guia sobre los modems ADSL aquí:
[http://ar.geocities.com/novatocba/doc/frame/modem-blog.htm](http://ar.geocities.com/novatocba/doc/frame/modem-blog.htm)

---

### Post by sajnox on 2008-01-14
Steve Ignorant,

Si tenes una guia de configuracion del modem, por favor subila!! siempre son utiles. (Salvo que estes seguro que funciona para TODOS los casos, aclara que es lo que a vos te sirvio y con que hardware la hiciste andar)

Saludos

---

### Post by steve_ignorant on 2008-01-26
COMO INSTALAR EL MODEM ZyXel 600 PRESTIGE(usb) EN GNU/LINUX
Este modem lo provee telefonica de argentina, en mi caso particular fue por un cambio de modem anteriormente tenia el modem SpeedTouch 330. asi pues en este pequeño manual dare a seguir los pasos que realize para que funcione.

como primer paso principal es bajar los “drivers” o como se conocen para linux los “firmware” el cual es “cxacru”, un aplicativo que se llama “br2684ctl”
los pasos que hay que realizar, son los siguientes:
1)copiar el firmware en la carpeta lib/firmware
2)incluir en el modulo la palabra pppoatm
3)inatalar el  br2684ctl
4)iniciar el  br2684ctl
5)iniciar el pppoeconf
6)reiniciar
7)conectarse
una vez que hayamos bajado y descomprimido el driver en la carpeta local hacemos la copia al  directorio que le corresponde, esta copia la hacemos abriendo una terminal y con permisos de root/administrador con el comando:
(si no sabemos como obtener los permisos de administrador/root ponemos en la terminal  sudo su y el password del administrador/root
   sudo cp cxacru-fw.bin /lib/firmware
si ese comando no funciona podemos probarcon este otro:
   sudo chown root /lib/firmware/cxacru-fw.bin
nota importante: si anteriormente tenias el speedtouch y funcionaba en linux, te recomiendo que antes de iniciar el linux desconectes el modem(ya que en windou$ debemos instalarlo desconectado) hasta que puedas iniciar sesion una vez que te aparezca lapantalla de inicio de sesion conecta el modem y veras que enlaza(aun no tenemos conexión a internet pero enlaza que es importante)

2)Incluir el módulo pppoatm
bien ahora lo que hayque haces es modificar el modulo agregandole la palabra “pppoatm”  al final del modulo mismo, como lo editamos con el siguiente comando desde la terminal:
    gksudo gedit /etc/modules
se te abrira el gedit y deberas poner la palabra “pppoatm” en la ultima linea y quedaria algo asi:
   # /etc/modules: kernel modules to load at boot time. 
   # 
   # This file contains the names of kernel modules that should be          loaded 
   # at boot time, one per line. Lines beginning with "#" are    ignored. 
   fuse 
   lp 
   sbp2 
   pppoatm <---- deberia quedar asi

 guardamos los cambios y cerramos el editor. Configurando esto lo que hacemos es hacer que cuando inicie el sistema el modulo que agregamos nosotros(pppoatm) sea cargado

3 Instalar el br2684ctl 
este paquete es autoejecutable o  autoinstalable solo debemos hacer doble click en el o tipear en la consola el comando:
sudo dpkg -i br2684ctl_20040226_1_i386.deb
aparecera un aplicativo(si ya lo teniamos instalado podemos reinstalarlo) y se instalara solo
luego hay que configurar el br1684ctl en la terminal con el comando:
sudo br2684ctl -b -c 0 -a 8.35

(8.35 son los valores de VPI/VCI de telefonica los de telecom son 0.33)
Una vez que escribas eso, debería motrar algo así:
br2684ctl[6767]: Interface “nas0&#8243; created sucessfully
br2684ctl[6767]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[6767]: Interface configured
5 Iniciar pppoe (esta es la parte mas facil se hace solo)

Ahora ejecutar el programa de configuracion de pppoe tipeando en la terminal:
Comando:
sudo pppoeconf
Debes seguir las instrucciones y responder las preguntas que hace el configurador de la conexión. Cuando pide interface, elegir nas0, luego pide nombre de usuario(deberia ser usuario@speedy) y luego el password que usas para conectarte a internet. 
Luego dale enter a lo que te ofrezca salvo la opcion de conectarte en el inicio de Linux, porque no va a andar ya que el modem tarda un rato en sincronizar. (Para cuando el modem deja de parpadear, ya estas en el desktop).
Así que para conectarte vas a tener que tipear un par de lineas en la terminal cada vez, estas son: 
   sudo br2684ctl -b -c 0 -a 8.35
   ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up 
   pon dsl-provider
esto lo tendras que poner cada vez que quieras conectarte, cuando pongas pon dsl-provider te aparecera en la terminal “Plugin rp-pppoe.so loaded.”
6)Reiniciar
si anteriomente tenias el speedtouch recomiendo que desconectes el modem mientras carga el sistema, y cuando te aparezca la pantalla de inicio de sesion ahi lo vuelvas a conectar porque puede hacer que el linux se cuelgue al bootear con el modem conectado:
- desconetar entes de que empiece la carga del sistema
- conectar cuando aparezca al pantalla de inicio de session en donde pide el usuario y luego la contraseña 
7) conectar a internet
Una vez reiniciado el sistema, antes de hacer el próximo paso asegurarse que la luz de ADSL ya este fija, sin titilar y encendida. Ahora tipear lo siguiente para conectarse a internet:
sudo br2684ctl -b -c 0 -a 8.35
Se verá esto:
r2684ctl[6767]: Interface “nas0&#8243; created sucessfully
br2684ctl[6767]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[6767]: Interface configured
Luego escribes:
pon dsl-provider <----- (comando con el cual se conecta a internet)
Se verá esto:
“Plugin rp-pppoe.so loaded.” 
Y deberia conectarse. Abre el explorador y trata de navegar o realiza alguna otra actividad en Internet.
Atención: Si tira un error de “invalid nic-nas0&#8243; editar el archivo
/etc/ppp/peers/dsl-provider y modificar “nic-nas0&#8243; por “nas0&#8243;.
Grabarlo y desde la terminal volver a tipear 
pon dsl-provider
Esto es todo.
Para ver informacion que te puede servir para entender que es lo que esta pasando cuando cargas algo, podes tipear “dmesg” en la terminal para ver mucha info de todo lo que va pasando, o “plog” para ver solo lo referido a la conexión.

---

### Post by vagoybostero on 2009-01-04
Vamos a probarla.. yo tengo el mismo modem!

---

### Post by Hei Ku on 2009-01-04
Ojo que esta guía es para versiones bastante anteriores de Ubuntu, y puede que no funcionen bien con las versiones más recientes.

---

