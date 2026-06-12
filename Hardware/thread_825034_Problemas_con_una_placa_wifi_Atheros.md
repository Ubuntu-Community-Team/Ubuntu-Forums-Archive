---
title: "Problemas con una placa wifi Atheros"
date: 2008-06-10
forum: Hardware
---

### Post by gustmarti on 2008-06-10
Hola gente, estoy instalando ubuntu HH en una Acer Aspire 4315 y tuve problemas con la placa wifi.
Buscando con google sólo encontré sitios en ingles, con el cual me defiendo pero no a nivel técnico.
La placa wifi es: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
La maquina tiene un procesador Intel Celeron 550 de 2.00GHz y 1gb de memoria.
También necesito q me digan como configurar la webcam que trae integrada la máquina. El modelo de càmara no lo pude encontrar. Gracias:)

---

### Post by Hei Ku on 2008-06-10
escribi lsusb en la consola y postea aca el resultado. Eso va a dar una idea del chipset de la webcam.

---

### Post by Flechagorda on 2008-06-10
Gustimarti...

Para la placa Atheros, proba con esto:

[http://www.ubuntu-es.org/index.php?q=node/83054](http://www.ubuntu-es.org/index.php?q=node/83054)

Te lo copio para que no abras otra pagina...

El paso a paso sería el siguiente.

1- Bajás el driver que te indiqué ([http://snapshots.madwifi.org/special...+ar5007.tar.gz](http://snapshots.madwifi.org/special...+ar5007.tar.gz)).

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

8- Reiniciás

Con esto instale en mi Compaq F756 con la misma Atheros que vos...

Con respecto a la webcam, probala con el Cheese a ver si anda...
Yo no encontre en ningun lado como cambiar opciones o configuracion...

Abrazooooo

---

### Post by gustmarti on 2008-06-11
Tuve problemas con el punto 4. Me tiró que "no existe fichero ó directorio", a partir de ahí no pude hacer nada más.
El driver lo baje a /home/usuario y se descomprimió ahí. Cuando el punto 4 pidió que cambie de directorio... no pasó nada.

Respecto de la cámara cuando tiré lsusb me salió

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 04f2:b026 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Espero su respuesta... Gracias...

---

### Post by gustmarti on 2008-06-12
> **gustmarti said:**
> Tuve problemas con el punto 4. Me tiró que "no existe fichero ó directorio", a partir de ahí no pude hacer nada más.
El driver lo baje a /home/usuario y se descomprimió ahí. Cuando el punto 4 pidió que cambie de directorio... no pasó nada.

Respecto de la cámara cuando tiré lsusb me salió

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 04f2:b026 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Espero su respuesta... Gracias...

Todavía no pude encontrarle la vuelta!!!
A uds. que les parece?

---

### Post by luks911 on 2008-06-12
Hola,
Si el archivo lo descomprimiste en /home/usuario entonces se tiene que haber creado una carpeta home/usuario/madwifi-nr-r3366+ar5007 y a esa es a la que tenés que ir con cd home/usuario/madwifi-nr-r3366+ar5007.

Saludos

PD: Me suscribí al post, así que cualquier cosa, chiflá.

---

### Post by xpelaox on 2008-06-12
no se mucho yo... pero esto no se puede isntalar con ndiswepeer o como sea que se llama? para mi notebook HP funciono en su momento.

---

### Post by luks911 on 2008-06-12
> **xpelaox said:**
> no se mucho yo... pero esto no se puede isntalar con ndiswepeer o como sea que se llama? para mi notebook HP funciono en su momento.

Posiblemente, la verdad es que no lo sé. Pero con Madwifi evitás tener que usar los driver para Windows y, se te interesa, podés usar la placa en modo monitor. Por otra parte, más allá de los inconvenientes que puedan surgir en cada caso, si todo sale bien ;) no es más que escribir seis líneas en una terminal.

Para Ubuntu de 64bits sí no hay más remedio que ndiswrapper.

Saludos

---

### Post by gustmarti on 2008-06-12
Buenas noticias!!! Encontré el problema. Se nota que no soy muy bueno con la cosola. Lo que pasó fue lo siguiente: el paquete del driver estaba mal titulado "madwifi-nr-r3366+ar5007" y cuando lo descomprimís aparece como "madwifi-[SIZE="4"]ng[/SIZE]-r3366+ar5007" de lo que sólo pude darme cuenta descomprimiendo el paquete con el botón derecho del mouse. Ahora la placa anda perectamente!!! De hecho la estoy usando.
Una menos!! buenisimo!!! Sólo me queda solucionar lo de la cámara. Gracias a todos por la ayuda.

---

### Post by Flechagorda on 2008-06-12
Excelentes noticias gustmarti...

Con la webcam, la probaste con Cheese a ver si la reconoce???
Si no lo tenes, lo instalas desde AÑADIR Y QUITAR del menu APLICACIONES, pero me parece que Hardy ya lo trae incorporado......

Abrazo

---

### Post by gustmarti on 2008-06-13
Bueno gente, finalmente la camariata es una BELLESA como diria el bambino. Anda perfecto.
Lo único que me faltaría para que todo ande de maravillas es el microfono incorporado. Puse el Alsa mixer al mango pero con grabador de sonido no pude tomar nada.
Alguna idea?

---

