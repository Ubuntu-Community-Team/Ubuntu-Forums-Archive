---
title: "Modem ZTE MF626 de Claro en Ubuntu 9.10"
date: 2009-11-08
forum: Hardware
---

### Post by darkneo on 2009-11-08
Saludos a todos los ubunteros Argentinos, como el nombre del mensaje lo indica, tengo problemas con el modem ZTE MF626 de Claro en Ubuntu Karmic Koala. Busque en varios lados las configuraciones del modem pero tengo un problema en uno de los pasos, les dejo la direccion con los pasos de la configuracion para decirle cual es mi problema:

[http://www.taringa.net/posts/linux/2318037/Configurar-internet-en-Ubuntu-modem-ZTE-mf626.html](http://www.taringa.net/posts/linux/2318037/Configurar-internet-en-Ubuntu-modem-ZTE-mf626.html)

Cuando llego al paso 8, el que dice: "Ejecutar en Terminal "sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf". Con esto le cambiaremos el modo y ahora el sistema lo va a ver como un módem. Si hacen "lsusb" de nuevo, debería haber cambiado a ID 19d2:0031 ", ingreso eso en la terminal pero me dice que el directorio no es correcto.

Cual podria ser el problema?? Que esta en otro directorio el modem y lo tengo que cambiar??
Les agradezco su ayuda, nos vemos!!

---

### Post by marianom on 2009-11-09
Yo tengo ese modem de porquería andando en mi JJ (gracias por comentarme que sigue igual en KK) y lo hice siguiendo las instrucciones que vos mencionás.
Si te da ese error, es muy posible que no hayas instalado [usb_modeswitch]("http://www.draisberghof.de/usb_modeswitch/"). 
Instalar es desempaquetar y correr sudo make install y listo, nada más.

Una vez lo tengas listo, no te vayas a creer que todo es enchufar el modem y que vas a salir andando: en mi caso, es casi parecido a jugar al twisted: lo saco y lo pongo como tres veces: si se cae la conexión y no la puedo levantar tengo que reiniciar la máquina (seguro que hay una solución mejor pero lo uso pocas semanas al año como para que valga la pena invertir más horas) y no me tomó los datos por defecto de CTI que vienen en el network manager: lo hice andar con 
APN: internet.ctimovil.com.ar
usuario: ctigprs
password: ctigprs (creo que es la misma: esta toda en ***)

Espero no haberte deprimido, que tengas toda la suerte.

---

### Post by darkneo on 2009-11-09
amigo, hago el sudo make install, pero cuando llego al paso que me tendria que reconocer el aparato como modem para luego seguir adelante y terminar la configuracion, me dice que no existe el directorio para esto: sudo /usr/sbin/usb_modeswitch -W -c /etc/usb_modeswitch.conf, hago eso y me tira error. No se que puede ser, si soluciono esto me quedo definitivamente en ubuntu, porque sin internet, no tiene gracia.

---

### Post by marianom on 2009-11-09
Fijate donde está realmente el archivo:
 hace
```
sudo updatedb
```
cuando termine de correr, hace
```
locate usb_modeswitch.conf
```
y fijate donde te indica que está guardado y cambias la ruta para que refleje la realidad.

---

### Post by darkneo on 2009-11-09
No che, nada, por ahi soy yo el gil que no lo sabe hacer, pero creo que los directorios estan bien, porque los archivos estan donde dice la terminal, pero no se que puede ser.

---

### Post by marianom on 2009-11-09
Veamos entonces. Te pido que corras el comando y tanto el comando como la salida lo copies textual por aca.

---

### Post by ceci.c on 2010-01-30
Hola! Soy nueva en esto. Y tengo el mismo problema con el dichoso módem. Como tengo una Pentium III y con WinXP no puedo hacer que funcione la placa de sonido proque supuestamente falta un driver que está reinstalado un millón de veces, me recomendaron que usara Xubuntu para ver si se solucionaba el tema de los drivers. Lo instalé y todo muy lindo, excepto porque me pedía bajar de internet los controladores de sonido y algo más que no recuerdo ahora. El tema es que intenté poner en práctica el tutorial que se indicaba en el primer post y hasta el paso 9 todo bárbaro, como no tengo gedit en xubuntu, hice el archivo con el notepad en winxp, le cambié la extensiónb a .fdi y lo guardé donde decía el tuto. El modem es reconocido, pero nunca pude abrir ningún otro menú que no sea el de "Habilitar red o desahabilitar", y cada vez que lo conecto gira la ruedita (lo intenta conectar) y así está un largo tiempo -más de 10 minutos- y aparece el cartelito de No tiene conexión de Red o algo similar, como notarán no lo intenté tantas veces, ya que me pudrí y sigo con el win que me hace muy lenta la máquina. Hay alguna solución definitiva para esto? Por lo menos hasta cumplir el año de contrato y revocarlo sin tener que pagar de más..
 
Desde ya gracias! :)

---

### Post by marianom on 2010-01-31
Hola Ceci, bienvenida!!
El otro día tuve que instalar usb_modeswitch en una máquina nueva y para mi sorpresa no andaba (más o menos como vos decis): era extraño porque antes siempre lo hice andar. Resulta que la versión nueva de usb_modeswitch no permite que ande este modem en particular. Por suerte pude dar con la última versión donde si me anduvo (que es la 0.9.7) y salió andando lo más bien.
Yo creo que en relación a tu problema, vamos a empezar por ahí. Dame el link exacto de donde bajaste el programa antes mencionado así vemos que versión es y desde ahi partimos.

---

### Post by JuanitoMint on 2010-02-01
para aquellos que quieran evitarse todo el lio del usbmodeswitch les comento que el modem trae unos comandos para deshabilitar el autorun del CD
AT+ZCDRUN=8 
se deshabilita
AT+ZCDRUN=9
lo volvemos al estado anterior o sea con el autorun
yo probe con varios modelos en karmic y los detecta correctamente, pero igual no puedo establecer la conexion
(estos comandos se pueden mandar desde el hyperteminal en un windows o cualquier otro emulador de terminal )

---

### Post by ceci.c on 2010-02-04
Gracias Mariano por la bienvenida. El usb_mode.. lo bajé de esta página: [http://www.draisberghof.de/**usb_modeswitch**/]("http://www.draisberghof.de/usb_modeswitch/"), que era la que recomendaba el tutorial. La versión es la 0.9.7. 
JuanitoMint, cómo es eso? (la verdad no entendí ni medio, no soy muy amiga de los comandos ^^)
Saludos y gracias anticipadas! :)

---

