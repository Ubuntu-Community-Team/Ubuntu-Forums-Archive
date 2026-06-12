---
title: "Conectar ubuntu jaunty a internet ip estática."
date: 2009-07-21
forum: Instalación y Actualización
---

### Post by aolivares on 2009-07-21
Hola amigos.
Tengo una amiga que tiene un problema, necesita conectar ubuntu jaunty a una red por cable que le da ip estática.

Lo primero es que me digan los datos que debo pedir y para que me expliquen lo que tiene que hacer.

Ella tiene todos los datos pa meter y configuarar la red pero no sabe como hacerlo.

Saludos.

---

### Post by pagondel on 2009-07-21
Necesitas: IP, Mascara de subred, puerta de enlace (gateway) y dns (si no me equivoco esta todo xD).
Una vez tienes esos datos, te conectas a internet, luego te dirijes a NetworkManager y con el boton derecho haces click y seleccionas la opcion "Editar las conexiones". Una vez seleccionada la interface de red a utilizar, haces click en editar la conexion te dirijes a la pestaña "Ajustes IPv4" y donde dice "Metodo" cambias a "Manual", haces click en añadir, llenas los datos. Te deberia quedar algo asi:
[[IMG]http://img229.imageshack.us/img229/7079/pantallazoyhm.th.png[/IMG]](http://img229.imageshack.us/i/pantallazoyhm.png/)

Saludos!

---

### Post by aolivares on 2009-07-21
Gracias pato espero que le sirva.

Saludos.

---

