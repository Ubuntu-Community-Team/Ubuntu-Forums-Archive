---
title: "[Problema] No me reconoce la red"
date: 2009-03-25
forum: Hardware
---

### Post by cllejero on 2009-03-25
Hola a todos, soy nuevo en Ubuntu.

Hoy lo instale en mi maquina Ubuntu, en una partición, y lo corro junto con Windows (ya que soy principiante en esto).

Mi problema es el siguiente,

Tengo una red domestica, de 4 computadoras. Todas las computadoras poseen Windows XP, salvo una que posee Windows XP/**Ubuntu**.

*Cuando a esa maquina la inicio con Ubuntu no me reconoce la red.*

Todas estan conectadas a traves de un switch. Y poseo un router para internet.

**Router:** Zyxel Prestige 600 series

**Ubuntu Version:** 8.04.2

Probé configurar la red por el **pppoeconf** pero me tira este error: *"Sorry, I scanned 1 interface, but the Acess Concentrator of your provider did not respond."*

Reinicie la pc, y segui intentando, pero me siguió tirando el mismo error.

Verifique el cableado, tengo todo conectado, y la Red con Windows no me da problemas.

Si necesitan mas datos pidanmelos.

Espero una respuesta, saludos.

---

### Post by Mauro22 on 2009-03-25
mmm Raro..


Por lo general el tema de red cableado está cocinado.

Poné datos sobre la placa, marca, modelo, si es onboard, etc...

y postea el resultado del comando lspci

---

### Post by infernus92 on 2009-03-26
una cosa que tienen todos los que recien empiezan... reiniciar por nada...
pero es raro tu problema... a mi me detecto red sin tener que configurar nada... y eso que la red estaba funcionando con 3 SO diferentes... van a hacer falta mas datos para poder solucionar tu problema... pero se lo dejo a usuarios mas avanzados... yo soy apenas un poquito mas que principiante...

saludos

---

### Post by luks911 on 2009-03-26
Además de lo que dice Mauro22, postea el resultado del comando
```
cat /etc/network/interfaces
```

Y usar pppoeconf no es necesario si el router funciona como tal, es decir que se encarga de marcar la conexión.

---

### Post by ZeT76 on 2009-03-26
Buenas. Usaste la version de 64 bits de Ubuntu? Te pregunto proque si tu respuesta es afirmativa, probá con la versión de 32 bits. Yo lo instalé hace poquito y la de 64 bits no había forma de hacerla andar. Con la de 32 funciona todo OK. Saludos!

---

### Post by cllejero on 2009-03-26
No me puteen, recien empiezo en esto, y como ven no tengo mucha idea, pero quiero aprender.

> **Mauro22 said:**
> mmm Raro..


Por lo general el tema de red cableado está cocinado.

Poné datos sobre la placa, marca, modelo, si es onboard, etc...

y postea el resultado del comando lspci

**Placa base:**
Tipo de procesador: DualCore Intel Core 2 Duo E4400, 2000 MHz (10 x 200)
Chipset de la Placa Base: SiS 671/671DX/671FX
Memoria del Sistema: 2048 MB
Tipo de BIOS: AMI (09/17/07){
Fabricante: ASUSTeK Computer INC.

**Monitor:**
Tarjeta gráfica: NVIDIA GeForce 8500 GT (512 MB)
Acelerador 3D: nVIDIA GeForce 8500 GT

**Red:**
Dirección IP principal: 192.168.1.4
Dirección MAC principal: 00-1E-8C-82-E4-39
Tarjeta de Red: SiS191 1000/100/10 Ethernet Device (192.168.1.4)


> **luks911 said:**
> Además de lo que dice Mauro22, postea el resultado del comando
```
cat /etc/network/interfaces
```

Y usar pppoeconf no es necesario si el router funciona como tal, es decir que se encarga de marcar la conexión.

Soy nuevo en ubuntu,

eso lo mando por Terminal? Todo el comando junto? (no me tira nada)

Ahora voy a probar por separado. Se me hace dificil, ya que estoy en la misma pc de Ubuntu ahora.

> **ZeT76 said:**
> Buenas. Usaste la version de 64 bits de Ubuntu? Te pregunto proque si tu respuesta es afirmativa, probá con la versión de 32 bits. Yo lo instalé hace poquito y la de 64 bits no había forma de hacerla andar. Con la de 32 funciona todo OK. Saludos!

No, es la version de 32 bits.

---

### Post by luks911 on 2009-03-26
> **cllejero said:**
> Soy nuevo en ubuntu,

eso lo mando por Terminal? Todo el comando junto? (no me tira nada)

Ahora voy a probar por separado. Se me hace dificil, ya que estoy en la misma pc de Ubuntu ahora.

Todo bien, todos aprendemos.

Sí, todo junto en una terminal y después, claro, Enter. Debería devolverte algo y ese algo es el contenido del archivo /etc/network/interfaces

---

### Post by pablo.s on 2009-03-26
Hola: Te recomiendo que actualices a) El núcleo a uno mas actual ó
                                                                        b) A la versión mas actual de Ubuntu, que es
Jaunty. Antes de instalar podés probar con la versión live cd desktop. Asi
chequeás que te funcione la red, sonido, video, etc.
A veces parece una gran molestia pero algunos problemas se solucionan de este
modo. Avisame si te sirve. Saludos.

---

### Post by cllejero on 2009-03-26
Aca va un pantallazo de lo que me aparece en /etc/network/interfaces

[http://i43.tinypic.com/2dqov45.jpg](http://i43.tinypic.com/2dqov45.jpg)

NOTA: Pongo el link solo porque esta en 1024 x 768.

> **pablo.s said:**
> Hola: Te recomiendo que actualices a) El núcleo a uno mas actual ó
                                                                        b) A la versión mas actual de Ubuntu, que es
Jaunty. Antes de instalar podés probar con la versión live cd desktop. Asi
chequeás que te funcione la red, sonido, video, etc.
A veces parece una gran molestia pero algunos problemas se solucionan de este
modo. Avisame si te sirve. Saludos.

Ok, voy a ver que ago.

No entendi la parte "a".

Saludos

---

### Post by luks911 on 2009-03-26
Si el router es el que se encarga de asignar las IP y no son fijas, entonces me parece que lo que deberías hacer es comentar algunas líneas del archivo /etc/network/interfaces. Probalo, en el peor de los casos lo volvés a editar para que quede como antes. 
Hacé lo siguiente: editás el archivo ejecutando en una terminal ```
sudo gedit /etc/network/interfaces
```
y comentá (es decir agregás el signo # delante) las cuatro líneas  del medio que forman un grupo. Tiene que queddar así

```
auto lo
iface lo inet loopback

#iface eth0 inet dhcp
#address 192.168.1.2
#netmask 255.255.255.0
#gateway 192.168.1.1

auto eth0
```

Después, claro, guardalo y, creo, hace falta reiniciar, o al menos reiniciar la red pero ahora no me acuerdo cómo se hace :P.

---

### Post by cllejero on 2009-03-26
> **luks911 said:**
> Si el router es el que se encarga de asignar las IP y no son fijas, entonces me parece que lo que deberías hacer es comentar algunas líneas del archivo /etc/network/interfaces. Probalo, en el peor de los casos lo volvés a editar para que quede como antes. 
Hacé lo siguiente: editás el archivo ejecutando en una terminal ```
sudo gedit /etc/network/interfaces
```
y comentá (es decir agregás el signo # delante) las cuatro líneas  del medio que forman un grupo. Tiene que queddar así

```
auto lo
iface lo inet loopback

#iface eth0 inet dhcp
#address 192.168.1.2
#netmask 255.255.255.0
#gateway 192.168.1.1

auto eth0
```

Después, claro, guardalo y, creo, hace falta reiniciar, o al menos reiniciar la red pero ahora no me acuerdo cómo se hace :P.

Gracias por la ayuda.

Pero hice tal cual me indicaste y paso esto.

[http://i39.tinypic.com/dqn9f.jpg](http://i39.tinypic.com/dqn9f.jpg)

:confused:

---

### Post by luks911 on 2009-03-26
Es que estás queriendo guardar/crear el archivo interfaces en /home/diego/etc/network, es decir en tu home, cuando el archivo que tenés que editar está en la carpeta /etc/network (fijate la diferencia que hay en la ruta). Para editarlo, escribí tal cual o copia y pegá en la terminal

```
sudo gedit /etc/network/interfaces
```

Te va a pedir tu contraseña porque lo tenés que editar como root y se va a abrir el archivo que vas a poder modificar y guardar.

---

### Post by faktorqm on 2009-03-27
Pasa que no te anda nada por que tenes una ensalada ahi tremenda.

Para editar el archivo, tenes que ir a aplicaciones -> accesorios -> terminal (prejuzgo que estas con gnome) y ahi escribis

```
sudo nano /etc/network/interfaces
```

te pide tu contraseña, la metes y listo.

Hecho eso, vamos por partes, si tenes 8.10 NO tenes que usar el archivo que te recomendo lucas por que inmediatamente entra en conflicto con el network manager. Si desinstalas el network manager (cosa que recomiendo) y tocas el archivo, pasan dos cosas:

A) si queres una direccion estatica esta mal especificada por decirlo de alguna manera, esto es

```
auto lo
iface lo inet loopback

**#iface eth0 inet dhcp**
#address 192.168.1.2
#netmask 255.255.255.0
#gateway 192.168.1.1

auto eth0
```

la linea que te marque en negrita, si vos queres direccion estatica, debe ser

```
iface eth0 inet static
```

asi que deberia quedar:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

```

B) si queres asignar una direccion dinamica, tambien esta mal!!! vos tenes que sacar la parte que especifica ip, mascara y puerta de enlace. te tiene que quedar asi:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

Ahora bien, con el archivo tocado, y correctamente guardado segun tus preferencias, escribis en la terminal

```
sudo /etc/init.d/networking restart
```

y eso te reinicia todos los servicios de red. 

SI TE QUEDO ALGUNA DUDA NO TOQUES NADA Y PREGUNTA POR FAVOR ANTES DE HACER MACANAS. :lolflag:

---

### Post by cllejero on 2009-03-27
> **luks911 said:**
> Es que estás queriendo guardar/crear el archivo interfaces en /home/diego/etc/network, es decir en tu home, cuando el archivo que tenés que editar está en la carpeta /etc/network (fijate la diferencia que hay en la ruta). Para editarlo, escribí tal cual o copia y pegá en la terminal

```
sudo gedit /etc/network/interfaces
```

Te va a pedir tu contraseña porque lo tenés que editar como root y se va a abrir el archivo que vas a poder modificar y guardar.

Anoche cuando hice los pasos que vos me dijiste, me aparecio "Modo de red desconectado".

> **faktorqm said:**
> Pasa que no te anda nada por que tenes una ensalada ahi tremenda.

Para editar el archivo, tenes que ir a aplicaciones -> accesorios -> terminal (prejuzgo que estas con gnome) y ahi escribis

```
sudo nano /etc/network/interfaces
```

te pide tu contraseña, la metes y listo.

Hecho eso, vamos por partes, si tenes 8.10 NO tenes que usar el archivo que te recomendo lucas por que inmediatamente entra en conflicto con el network manager. Si desinstalas el network manager (cosa que recomiendo) y tocas el archivo, pasan dos cosas:

A) si queres una direccion estatica esta mal especificada por decirlo de alguna manera, esto es

```
auto lo
iface lo inet loopback

**#iface eth0 inet dhcp**
#address 192.168.1.2
#netmask 255.255.255.0
#gateway 192.168.1.1

auto eth0
```

la linea que te marque en negrita, si vos queres direccion estatica, debe ser

```
iface eth0 inet static
```

asi que deberia quedar:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

```

B) si queres asignar una direccion dinamica, tambien esta mal!!! vos tenes que sacar la parte que especifica ip, mascara y puerta de enlace. te tiene que quedar asi:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

Ahora bien, con el archivo tocado, y correctamente guardado segun tus preferencias, escribis en la terminal

```
sudo /etc/init.d/networking restart
```

y eso te reinicia todos los servicios de red. 

SI TE QUEDO ALGUNA DUDA NO TOQUES NADA Y PREGUNTA POR FAVOR ANTES DE HACER MACANAS. :lolflag:

Tengo Ubuntu 8.04.2

Desinstale el **network manager** y segui los pasos tal cual me dijiste, aca te mando unas screen.

**A-**
[http://i43.tinypic.com/296gbon.png](http://i43.tinypic.com/296gbon.png)
[http://i44.tinypic.com/24grslx.png](http://i44.tinypic.com/24grslx.png)

**B-**
[http://i44.tinypic.com/t7bkuu.png](http://i44.tinypic.com/t7bkuu.png)
(despues probe con el address 192.168.1.4, que tambien esta libre, y paso lo mismo)
[http://i40.tinypic.com/29pu5w2.png](http://i40.tinypic.com/29pu5w2.png)

*Primera screen de lo que guarde en /etc/network/interfaces
*Segunda screen del sudo /etc/init.d/networking restart

Saludos ](*,)

---

### Post by faktorqm on 2009-03-27
que raro que no te tome el dhcp.... hace una cosa, ponelo a mano y fijate que error te tira:

```
sudo ifconfig eth0 192.168.1.4 netmask 255.255.255.0 broadcast 192.168.1.255 up
```

y despues pone 

```
sudo route add default gw 192.168.1.1
```

y edita el archivo /etc/resolv.conf y que te quede asi:

```
sudo nano /etc/resolv.conf
```

y en el archivo te tiene que quedar una linea asi:

```
nameserver    192.168.1.1
```

Y tambien por las dudas si tenes un windows a mano posteame el comando "ipconfig /all" a ver como esta configurado. salu2!

---

### Post by cllejero on 2009-03-27
Aca te dejo unos pantallazos de lo que me pediste:

[http://i43.tinypic.com/2pquh55.jpg](http://i43.tinypic.com/2pquh55.jpg)

Y aca de lo que me dijiste que haga:

[http://i44.tinypic.com/331j5t0.png](http://i44.tinypic.com/331j5t0.png)
[http://i43.tinypic.com/1693gbc.png](http://i43.tinypic.com/1693gbc.png)
[http://i44.tinypic.com/2dsqvfd.png](http://i44.tinypic.com/2dsqvfd.png)

Antes, cuando en el navegardos ponia cualquier direccion de algun sitio de web, automaticamente me aparecía "Pagina no encontrada", ahora se queda como buscandola y no me aparece nada.


Y aca,

sudo ifconfig eth0 192.168.1.4 netmask 255.255.255.0 **broadcast 192.168.1.255** up

no tengo que poner 192.168.1.1 ?

Saludos ](*,)

---

### Post by cllejero on 2009-03-28
Esto significa que no voy a poder tener internet en Ubuntu :(:confused:

---

### Post by Hei Ku on 2009-03-28
No, significa que de vez en cuando Faktor tiene vida y no te puede responder enseguida. Te solicitamos paciencia, por favor.

---

