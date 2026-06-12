---
title: "Compaq y Kernel 2.6.24-17"
date: 2008-05-27
forum: Hardware
---

### Post by Flechagorda on 2008-05-27
Como les va....

Tengo una Compaq F756A, que apenas instale Hardy, habia reconocido todo sin problemas....

Anoche habia 18 actualizaciones, entre ellas la de Kernel, del 16 al 17..

Obviamente instale etc etc...
Cuando reinicio, me quede sin WIFI (Chip Atheros)... Volvi a hacer todos los pases que buen resultado me habian dado, pero sigue igual...
Encima, ahora me quede son sonido (despues de reinstalar los Restricted Modules...
Probe reiniciando con el Kernel 16, pero sigue todo igual!!
Alguien mas tuvo problemas con esta actualizacion????

Saludosss

Santi

---

### Post by niko_3100 on 2008-05-27
Yo actualice hoy a la mañana mi compaq v3415 y anda todo joya y ESPERO que mejor.

---

### Post by lega on 2008-05-27
A raiz de este mensaje me fije en la notebook de mi sra. y ya no me da la opcion configurar una conexion wireless como antes de aplicar el metodo en este foro si figuraba antes de la actualización, aunque no habia podido probarla, pero ya no esta mas, el sonido si sigue andando, Compaq F755

---

### Post by Flechagorda on 2008-05-28
Al final, reinstale Ubuntu, que me hacia falta, porque como un ***** habia hecho una sola particion para todo...
Asi que de paso, meti un par de particiones, y deje la instalacion bien limpia...
Actualize todo, Kernel 17 etc etc...cuando quedo todo al dia, procedi a instalar los drivers Madwifi y quedo jooooya!!!!
Aca copio los pasos que hice, procedentes de este post: 

[http://www.ubuntu-es.org/index.php?q=node/83054]("http://www.ubuntu-es.org/index.php?q=node/83054")


[B]El paso a paso sería el siguiente.

1- Bajás el driver que te indiqué ([http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)).

Lo que sigue desde un terminal :

2- Instalás lo necesario para compilar el driver con:

$ sudo apt-get install build-essential linux-headers-`uname -r`

3- Extraés los archivos que habías bajado:

$ sudo tar -xzvf /directorio_en_el_que_lo_guardaste/madwifi-nr-r3366+ar5007.tar.gz

4- Te movés al nuevo directorio:

$ cd /directorio_donde_descomprimiste/madwifi-nr-r3366+ar5007

5- Compilás:

$ sudo make

6- Borrás posibles instalaciones anteriores de Madwifi:

$ sudo rm -rf /lib/modules/`uname -r`/madwifi 

7- Instalás el driver:

$ sudo make install

8- Reiniciás[/B]


Abrazo para todos....

---

### Post by niko_3100 on 2008-05-28
Que grande a segui disfrutando ubuntu y la compaq.

---

