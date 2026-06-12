---
title: "Problema para conectar modem Huawei E1756 en Ubuntu 10.04."
date: 2010-08-07
forum: Hardware
---

### Post by neothehacker on 2010-08-07
¡Hola a todos!.
Mi nombre es Ariel.Soy un usuario nuevo de esta página y también nuevo en Ubuntu.
Les comento que he tratado de conectar el modem huawei e1756 en el ubuntu 10.04 LTS y para empezar ,de todas las veces que instalé el sistema,en ningún momento reconoció automáticamente el modem.Me doy cuenta porque en "conexiones de red" > "Banda ancha movil" > "Añadir" no parece reconocerlo.
A través de windows ,sistema que ya hace meses que tengo y quiero dejar,y con mi navegador firefox del cual estoy muy contento por su mejor funcionamiento a diferencia de internet explorer,busqué cómo instalar el modem huawei e1756 en ubuntu pero encontré una explicación para Ubuntu 9.04 y creí que me iban a servir para el 10.04 lts y bajé el archivo "usb-modeswitch-1.1.3.tar.bz2" en Taringa en donde dicen como descomprimirlo e instalarlo en linux.Las instrucciones son estas:

Desde la terminal de ubuntu y posicionado sobre la carpeta donde está el archivo .tar.bz2 escribir:

tar xvfj usb-modeswitch-1.1.3.tar.bz2

y darle enter.

Esto extrae los archivos en una carpeta del mismo nombre que el archivo comprimido y dentro del directorio del mismo.
Después hay que subir hasta ese directorio ( cd usb-modeswitch-1.1.3 ) y escribir :

sudo make install

Después ese mismo post de taringa dice que hay que agregar las siguientes líneas de código en el archivo usb_modeswitch-1.1.3.conf ( o creo que así era el nombre del archivo): (*)

# Huawei E1692/E1756
DefaultVendor= 0x12d1
DefaultProduct= 0x1446

TargetVendor= 0x12d1
TargetProduct= 0x140c

MessageContent="55534243000000000000000000000011060000000000000000000000000000"

CheckSuccess=5

y cerrar el archivo.
Después crear un archivo de nombre "15-huawei.rules" con las siguientes líneas de código y guardarlo en /etc/udev/rules.d :

SUBSYSTEM=="block",
ACTION=="add",
SYSFS{idVendor}=="12d1",
SYSFS{idProduct}=="1446",
OPTIONS="ignore_device"

SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/usr/sbin/usb_modeswitch"


y reiniciar el servicio de puertos usb con la siguiente instrucción:

service udev restart

La primera vez que hice esto no me funcionó nada.Me volví  "bastante tarado" para tratar de saber por qué no funcionó.Busqué de usar la ayuda de ubuntu y no me ofrecía grandes manuales,solo me decía que si ubuntu no lo detectaba automaticamente que fuera a conexiones de red y en banda ancha movil pudiera añadir.
Pero así tampoco funcionó.
Como tampoco sabía desinstalar programas en ubuntu (por ser mi primera vez) no tuve más remedio que reinstalar el sistema operativo en donde solo tuve que especificar mi  país,idioma del teclado,usuario y contraseña,la opción iniciar sesión automaticamente, y darle en "adelante".

Después de largas horas de ver como hacerlo funcionar se me ocurrió que antes de instalarlo con la instrucción sudo make install sería mejor que agregara las líneas de código en "1" y después instalarlo y agregar el archivo "15-huawei.rules" en /etc/udev/rules.d .Y parecía funcionar porque abrí firefox y pude navegar un rato.Después se me dió por desconectar internet con el botón superior derecho del panel superior y poner desconectar para reiniciar la computadora y ver si se iniciaba automaticamente (previamente configuré todo en conexiones de red >banda ancha movil> añadir y parecía reconocerlo) y reinicié la computadora .internet se conectaba automaticamente pero al poner desconectar nuevamente y reiniciar ya no se conectaba.
Por supuesto todo esto lo hice en un horario a la madrugada (creo que eran las 4 am)
y no recuerdo qué hice para que funcionara y me lo reconociera  pero después no pude volver a ponerlo de ninguna manera aún reinstalando el sistema operativo y reinstalando de todas las formas posibles el paquete.No resultó nada.
Si me pudieran ayudar con esto les agradecería un montón así empiezo a usar definitivamente ubuntu.

Gracias por la ayuda que me puedan ofrecer.

---

### Post by al204 on 2011-03-30
hola,
recibe un saludo desde Venezuela. pudiste resolver el problema q tenias con el modem huawei E1756 y ubuntu 10.04 lts? cambia mucho el procedimiento de ubuntu 10.04 a 11.04? yo acabo de comprar ese modem a telefonica y lo estoy usando a traves de windows, pero quiero cambiarme por completo a ubuntu. 

estoy leyendo y buscando informacion antes de intentar instalarlo y navegar. cualquier ayuda es bien recibida. gracias.
alvaro

---

