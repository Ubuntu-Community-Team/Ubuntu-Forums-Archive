---
title: "epson 6200l"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by llunoll on 2007-04-16
hola gente!, disculpen que escriba en un foro de ingles, y lo haga en castellano, pero estoy desesperado. siempre quise usar linux, pero, siempre he tenido problemas tras problemas. ahora tengo instalada la xubuntu 7,04 y los problemas no se hacen esperar. Tengo la impresora epson epl 6200l la cual figura como soportada, pero me dicer error epsoepl, antes en la kubuntu y ubuntu no me salia ese error, pero jamas imprimia.

existe alguna manera de hacer funcionar esta impresora??

gracias!!

---

### Post by llunoll on 2007-04-16
que frustrante es esto, ni en esta, la pagina oficial dan ayuda.

---

### Post by llunoll on 2007-04-17
que hay que hacer para que me ayuden????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????

---

### Post by llunoll on 2007-04-18
no es esta la pagina oficial de soporte para ubuntu??? entonces por que no me ayudan???
o por lo menos me dicen si ubuntu soporta la epson epl6200l

---

### Post by llunoll on 2007-04-18
no se olviden que tengo problemas

---

### Post by llunoll on 2007-04-20
pagina oficial!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! necesito ayudaaaaaaaaaaaaaaaaaa

---

### Post by llunoll on 2007-04-23
Amigos! estos son los pasos:

Para que esto funcione se necesitan 2 ficheros: **Epson-EPL-6200L-epl6200l.ppd y epsoneplijs_0.4.0-2_i386.deb**

1º Instalar paquetes (con Synaptic u otro medio) **alien y gs-afpl**
2º Conseguir/Descargar los 2 ficheros** (Epson-EPL-6200L-epl6200l.ppd y epsoneplijs_0.4.0-2_i386.deb)**
3º Desde terminal crear carpeta:> sudo mkdir /usr/share/foomatic/db/source/PPD/Epson

4º Ir donde tengamos los ficheros, por ejemplo escritorio del usuario pepe: > cd /home/pepe/Desktop
5º Copiar fichero:> sudo cp *.ppd /usr/share/foomatic/db/source/PPD/Epson
6º Instalar paquete:> sudo dpkg -i epsoneplijs_0.4.0-2_i386.deb
7º Ahora por fin se debe poder elegir la impresora correcta, así que vamos a Sistema --> Administración--> Impresoras--> Añadir--> Epson EPL 6200L
8º Cambiar texto *"gs"* por *"gs-afpl"* en:> sudo gedit /etc/cups/ppd/EPL-6200L.ppd
Ajustes finales:
· Propiedades de impresora--> Conexión--> Tipo de impresora --> Impresora local o detectada (Puerto USB)

· Menú contextual de impresora --> Convertir en predeterminada

y aqui estan los ficheros
[http://d.turboupload.com/d/1740335/ficherosepsonepl6200l.zip.html](http://d.turboupload.com/d/1740335/ficherosepsonepl6200l.zip.html)

deberian ser incluidos en la proxima version de ubuntu o liberar un parche, ya que los que hay en internet hasta ahora, se referian a la 6200 esto es para la 6200L que son drasticamente diferentes.

---

