---
title: "Audifonos sin sonido Ubuntu 10.04"
date: 2010-08-31
forum: Hardware
---

### Post by _Alfonso_ on 2010-08-31
hola linuxeros,es un gusto saludarlos,pues bien este es mi problema.Soy nuevo en linux,hace un par de semanas lo instale y la verdad que me gusto mucho por su velocidad,pero tengo el problema de los audifonos como muchos usuarios,creo haber leido la mayoria de temas similares a este y no encuentro solucion a mi problema.

Mi tarjeta de sonido es la siguiente. Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

intente instalar gnome alsamixer,pero me aparecio el siguiente error.W: Falló al obtener [http://pe.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-alsamixer/gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_i386.deb](http://pe.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-alsamixer/gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_i386.deb)
Algo malo sucedió resolviendo «'pe.archive.ubuntu.com:http» (-5 - No hay dirección asociada con el nombre de host):confused:

espero su ayuda ansiosamente:)

---

### Post by guillermolisi on 2010-08-31
Hola Alfonso

Ese error pareceria tener como causa algun problema en la conexion con el servidor que contiene los repositorios de paquetes, esto suponiendo que tu lista de repositorios este correcta.

Por que no probas cambiando de servidor a traves de la opcion Origenes de Software ? Aqui en Argentina muchos usamos servidores de otros paises, Brasil por ejemplo, porque los locales no siempre funcionan bien.

Bienvenido

---

### Post by josecuervo86 on 2010-08-31
Alfonso, podes probar lo que te dijo guillermo, o proba directamente bajando el deb desde la dirección donde supuestamente lo quiere obtener. O sea de aca [http://pe.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-alsamixer/gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_i386.deb](http://pe.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-alsamixer/gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_i386.deb). Te digo esto, porque probe y lo baja bien!

Saludos!

---

### Post by _Alfonso_ on 2010-08-31
muchas gracias muchachos,voy a seguir sus consejos,espero que instalando este paquete se solucione el problema del sonido,pero tengo algo que decirles,cuando intente instalar el paquete por synaptic antes que me apareciera el error antes mencionado me salto un aviso de advertencia.

[IMG]http://i55.tinypic.com/vgjziw.png[/IMG]

(disculpen pero no se como hacer mas pequeña la imagen - noob xD- )

ustedes que opinan.

saludos.

---

### Post by josecuervo86 on 2010-08-31
Alfonso, fijate que no se ve la imagen. Proba subiendola aca: [http://imagehost.org/](http://imagehost.org/)

---

### Post by _Alfonso_ on 2010-09-01
[IMG]http://j.imagehost.org/0245/aviso.png[/IMG]

[-o<[-o<[-o<

---

### Post by guillermolisi on 2010-09-01
Algo no esta bien o en tu lista de repositorios (/etc/apt/sources.list y /etc/apt/sources.d.list) o en el servidor que estas utilizando para bajar los paquetes. Ese error se da cuando el repositorio no posee la firma digital que lo valida o posee una invalida.

---

