---
title: "Problema con placa de red del Mother M5A78L-M LX3"
date: 2013-06-04
forum: Hardware
---

### Post by Leooo on 2013-06-04
Hola ¿Que tal? miren necesito ayuda, masomenos caso alguna muy poco en verdad, una vez instale un modem USB en ubuntu que me costo muchisisisimo. Bueno la cuestion que ahora tengo una pc nueva y tengo un modem de red que pongo directo a mi pc, cuestion que conecto el ubuntu live y no se conecta a internet, lo cual me llama la antencion porque probe la pc vieja y se conecta solo... con esta nueva en cambio no se conecta trato de crear una configuracion de Cableado, pero nada!.
Busque el tema por google bastante y encontre algunos datos pero dice si no mal entiendo sobre esta placa pero para uso WIFI algo asi, que no lo reconoce y lei que hay que bar un pack de cosas para que lo tome, pero no lo puedo conseguir! ([https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/217052](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/217052)) aca es donde deduci esto, la verdad que si alguien es buena onda no me daria un mano y decirme donde conseguir las cosas y como hacer para instalarlos, ya que no me animo a instalar el Ubuntu(enrealidad queria usar el Fedora pero capaz no lo logro configurar) y quedarme sin internet...

---

### Post by guillermolisi on 2013-06-05
Lo ideal seria que nos pases las salidas de la ejecucion de los siguientes comandos en consola/terminal: ```
sudo lshw
``` luego de ```
lspci
``` y por las dudas y como para completar la informacion, ```
lsusb
```
La primer salida es bien larga pero contiene una radiografia detallada del hardware de la maquina.

Cualquier duda respecto de estos procedimientos, ya sabes, con preguntar se va aprendiendo.

---

### Post by gmunioz on 2013-06-05
Tu tarjeta es una:
Atheros Communications Inc. AR8161
Necesitas descargar este paquete:
[https://www.kernel.org/pub/linux/kernel/projects/backports/2013/03/15/compat-drivers-2013-03-15-u.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/03/15/compat-drivers-2013-03-15-u.tar.bz2)
Debes tener instalados:
build-essential 
linux-headers-generic
Luego en una terminal, colocado en la carpeta donde se copio el archivo descargado ejecutar:

> sudo su
tar xjf compat-drivers-2013-03-15-u.tar.bz2
cd compat-drivers-2013-03-15-u/
./scripts/driver-select alx
make
make install
make unload
modprobe alx
modprobe ath9k
lsmod | grep alx
ifconfig


---

### Post by Leooo on 2013-06-06
> **gmunioz said:**
> Tu tarjeta es una:
Atheros Communications Inc. AR8161
Necesitas descargar este paquete:
[https://www.kernel.org/pub/linux/kernel/projects/backports/2013/03/15/compat-drivers-2013-03-15-u.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/03/15/compat-drivers-2013-03-15-u.tar.bz2)
Debes tener instalados:
build-essential 
linux-headers-generic
Luego en una terminal, colocado en la carpeta donde se copio el archivo descargado ejecutar:

Si tengo esa tarjeta!, ahora una consulta de noob, esto " build-essential 
linux-headers-generic " me viene con el ubuntu o tambien lo tengo que bajar? yo bajando esto desde una pc con internet despues con un pendrive los instalo lo mas bien?

---

### Post by gmunioz on 2013-06-07
Estimo que pueden estar en el cd/dvd/usb de instalación, si no estan los bajas desde los repositorios y los instalas desde un usb, presta atención a las dependencias necesarias para estos dos paquetes, para bajarlas tambien.

---

### Post by Leooo on 2013-06-12
acabo de instalar ubuntu, bajo lo que me dijiste e ejecute los comandos... esta fue la respuesta de la terminal, estoy muy perdido la verdad...

TERMINAL= [http://tny.cz/b7c29daa](http://tny.cz/b7c29daa)

---

### Post by guillermolisi on 2013-06-12
Hay una dependencia aparentemente no resuelta (o mal resuelta):

> 
make: *** /lib/modules/3.5.0-17-generic/build: No existe el archivo o el directorio. Alto. indica que esta faltando instalar algo o indicar, en el momento de configurar el paquete a compilar, donde tienen que buscar los modulos del kernel en uso.

---

### Post by Leooo on 2013-06-12
> indica que esta faltando instalar algo o indicar, en el momento de configurar el paquete a compilar, donde tienen que buscar los modulos del kernel en uso. 

Osea que tengo que instalar que paquete? ese "3.5.0-17-generic"?

---

### Post by guillermolisi on 2013-06-12
Condiciones que considero importantes para que este tipo de problemas se resuelvan adecuadamente:


[LIST]
[*]Leer y releer detenidamente las sugerencias que se hacen
[*]Preguntar lo que no resulte claro y verificar lo que se interpreta, inclusive lo que parezca obvio, para luego accionar sobre una base solida
[*]Tener la instalacion actualizada al dia. Problemas como estos pueden solucionarse con una actualizacion o generarse mas problemas al trabajar con una instalacion desactualizada.
[*]No ir mas rapido ni dar un paso mas largo del que uno puede. Las mejores habilidades se logran con constancia, dedicacion, lectura y aprendizaje. Todos hicimos este proceso asi que, si, se puede.
[*]Considerar que siempre hay mas de una forma de lograr el mismo objetivo
[/LIST]

---

### Post by guillermolisi on 2013-06-12
Si no tenes posiblidad de conectar esa PC a Internet de forma alguna, mi recomendacion practica es agregarle temporalmente un placa generica, que suelen funcionar de entrada sin trabajo alguno, llevar a cabo la resolucion del driver para la placa nativa de esa maquina   y despues retirar la generica.
Lo haria aun sabiendo como y que instalar manualmente para que la Atheros funcione.

---

