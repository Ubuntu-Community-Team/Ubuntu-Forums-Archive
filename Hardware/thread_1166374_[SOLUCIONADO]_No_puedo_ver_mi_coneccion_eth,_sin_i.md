---
title: "[SOLUCIONADO] No puedo ver mi coneccion eth, sin internet"
date: 2009-05-21
forum: Hardware
---

### Post by flakojaime on 2009-05-21
HOla.
 
Uso ubuntu 9.04 en un note dell 1730. 
Tiene una tarjeta ethernet broadcom nextreme bcm5754m gigabit pci express y una inalambrica  pro/wireless 3945abg de intel.
 
 
1.- En mi trabajo, uso la conexion inalambrica (que tiene dominio usuario y contraseña) y me puedo conectar a internet por medio del firefox, pero no puedo actualizar paquetes por  red (me sale un aviso que no tengo internet). Configuro los parametros en firefox y en el proxy de la red. Cuando hago ping por medio de herramientas de red, me sale 0% de paquetes.
 
 
2.- En mi casa tengo conexion por medio de Telefonica banda ancha de 4 megas por medio de un modem zyxel 660rt1 ethernet. Configure el dsl en conexiones de red con nombre de usuario y contraseña. Quite el proxy y puse  **pon dsl-provider** en la consola y me sale:
 
**Plugin rp-pppoe.so loaded**
 
Cuando hago un ping en herramientas de red (google) me sale un 100% de paquetes, pero no tengo conexion a internet ni me sale el icono en la barra de estado (solo la inalambrica)
 
Trate de dejar el modem zyxel como router, pero no pude, asi que la otra opcion es poder configurar bien el dsl.
 
3.- Lo otro es que no puedo conectarme a redes inalambricas sin clave. solo sale un par de circulos verdes y despues me dice que no conecta.
 
Muchas Gracias por su tiempo.
 
Jiame

---

### Post by Carlos C on 2009-05-21
Parece que tienes dos problemas, por lo tanto debieras tratar de abrir un hilo para cada uno. Por favor en el futuro intenta no mezclar problemas en una sola conversación. Cuando te surjan dudas puedes mirar [acá.]("http://ubuntuforums.org/showthread.php?t=1162750")
> 
Cuando hago un ping en herramientas de red (google) me sale un 100% de paquetes, pero no tengo conexion a internet ni me sale el icono en la barra de estado (solo la inalambrica)

¿Estás seguro que no tienes internet? Prueba escribiendo el ip de google en firefox. Cuando le hago un ping me indica que su dirección de IP es 208.67.217.231 Si puedes ver los sitios escribiendo su IP entonces tu problema es de DNS.

Saludos.

---

### Post by moreback on 2009-05-21
El comando **pon dsl-provider** inicia una conexión DSL, te autentifica y agrega las rutas correspondientes en tu sistema, pero Network-Manager no maneja esta conexión así que para él todavía estás desconectado.

Esto último hace que Firefox inicie en modo "Trabajar sin conexión" y que otras aplicaciones no se conecten, como Pidgin o Emphaty.

Lo ideal es que hagas la conexión PPPoE usando solamente Network-Manager.

---

### Post by flakojaime on 2009-05-21
holas
 
Puse el ip de google y no funciona.
 
En conexiones de red, tambien tengo configurado el dsl, con usuario y contraseña.
 
Si hago ping por medio de herramientas de red en otros sitios, me sale 0% de paquetes.
 
La red cableada me sale que el dispositivo no esta gestionado.
 
En **/etc/network/interfaces** me dice lo sgte:
 
**auto lo**
**iface inet loopback**
 
**auto dsl-provider**
**iface dsl-provider inet ppp**
**pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf**
**provider dsl-provider**
 
**auto eth0**
**iface eth0 inet manual**
 
Gracias!

---

### Post by moreback on 2009-05-21
Si quieres manejar todas la conexiones con Network-Manager tu **/etc/network/interfaces **debiera lucir como el mío:

```
auto lo
iface lo inet loopback
```Las otras conexiones las agregas con botón derecho sobre el ícono de Network-Manager y eligiendo la opción "**Editar las conexiones...**".

Supongo que para que te funcione el ASDL deberías _*quitarle*_ la opción **Conectar automáticamente** a la conexión **Auto eth0** y luego configurar una conexión **DSL** con tus datos.

Si quieres que esa conexión quede forzada a una tarjeta de red en particular, ingresa la Dirección MAC en la pestaña **Cableada** de las opciones de la conexión DSL (la dirección la puedes obtener con el comando **ifconfig**).

Saludos.

---

### Post by flakojaime on 2009-05-23
> **moreback said:**
> Si quieres manejar todas la conexiones con Network-Manager tu **/etc/network/interfaces **debiera lucir como el mío:

```
auto lo
iface lo inet loopback
```

Hola..

Solo dejo esas dos lineas?

PD: La conexion inalambrica esta funcionando de maravilla.

jaime

---

### Post by moreback on 2009-05-23
> **flakojaime said:**
> Hola..

Solo dejo esas dos lineas?

PD: La conexion inalambrica esta funcionando de maravilla.

jaime


Correcto, el resto de las conexiones se manejan con Network-Manager y no van en este archivo. Ese archivo es para hacer conexiones permanentes o cosas que no puede hacer el NM.

Saludos.

---

### Post by flakojaime on 2009-05-23
Gracias... ahora me conecto por medio del NM la conexion ethernet.

Ahora tengo otro problema, lo voy a tratar de resolver.

Si  no puedo, les pido ayuda.

jaime

---

### Post by XcamiloX on 2009-11-17
Hola, pues ahora me puedo conectar con NM pero quedo como automática eth0 y no se deja eliminar ni mucho menos editar, ahora cada vez que me conecto toca darle manualmente conectar en al parte DSL.


ALGUIEN SABE COMO ELIMINAR eth0 DE LA SECCIÓN CABLEADA O EDITARLA DE FORMA QUE NO INICIE AUTOMÁTICAMENTE.

Espero ayuda :p

---

