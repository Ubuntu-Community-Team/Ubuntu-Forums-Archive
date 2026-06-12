---
title: "Speedy problemas"
date: 2009-09-05
forum: Hardware
---

### Post by lexer98 on 2009-09-05
hola chicos hoy me llego el kit de speedy lo instale todo bien en xp anda perfecto pero en ubuntu tengo un problema demora en empesar a cagar las paginas a que me refiero con esto yo abro una pagina y  cuando empiesa a cagar las luces de DSL y ETHERNET del modem titilan en xp , en cambio en ubuntu mas de una vez abro una pagina y quedan las luces apagadas y despues de 10 o 15 segundos recien empiesa a titilar las luces y a cagar la pagina 
el modem es un huawei smartAX MT880


desde ya muchas gracias

---

### Post by facurdo on 2009-09-09
EL modem se conecta por usb o a la placa de red?
Estaria bueno que llames a Speedy, ellos conocen sus modems, seguro deben tener alguna solucion, por mas que sea speddy :( los tecnicos detestan a telefonica ajaja, seguro que algun tip deben tener ellos

---

### Post by community nerd on 2009-09-09
hel ho no understand espanish

---

### Post by guillermolisi on 2009-09-09
> **community nerd said:**
> hel ho no understand espanish
Sorry community nerd, but there are spanish subforums too and this is one of them.

There are a lot of people in the world that not understand English, too many speak and read Spanish only and for they there are these international LoCo team subforums.

---

### Post by gmunioz on 2009-09-09
Hola lex.....:

Prueba routear el modem.

El procedimiento se efectua desde MS Windows

y utilizando Internet Explorer.

Ingresa a la dirección ---> [http://192.168.1.1](http://192.168.1.1) 

es la página web del modem

Ingresa el nombre de usuario ---> admin

Ingresa la contraseña ---> 1234

Pulsa en Basic ----> WAN Settings

Clickea en el icono del lápiz en la columna Action

en la fila PVC-0

En el formulario coloca los siguientes parámetros

VPI ---> 8

VCI ---> 35 

Type ---> PPPoE

Encapsulation ---> LLC/SNAP

Username: ---> usuario@speedy

Password: ---> contraseña speedy

Session established by ---> Always On

Pulsa --->  Apply

Controla que todo este funcionando

Pulsa ---> Status ---> Service Information.

Interface Ethernet ----> Status OK checkeado verde

WAN Interface PVC-0 ---> Status OK checkeado verde

Pulsa --->  Save ALL 

Cierra el navegador

Cierra Windows

Reinicia con Ubuntu

Si tarda en abrir páginas:

Pulsa el botón derecho del mouse en el icono de red en la 
barra superior a la derecha.

Elige editar las conexiones.

En la ventana emergente que se abre, titulada conexiones de red,
ilumina tu conexión.

En la nueva ventana emergente, titulada Editando Auto etho, 
pulsa en la pestaña Ajustes de IPv4 Settings.

Dentro de Ajustes de IPv4, cambia en Metodo de Automatico (DHCP) 
a solo direcciones.

Pon en Servidores DNS Servers: 208.67.222.222, 208.67.220.220
  
Pulsa aplicar, y cierra todas las ventanas.

Pulsa Aplicaciones - Accesorios - Terminal, en la consola que se 
abre ejecuta las ordenes, escribiendolas y dando enter.

sudo cp /etc/resolv.conf /etc/resolv.conf.auto

sudo gedit /etc/dhcp3/dhclient.conf

En el archivo que se abre coloca al final la siguiente línea:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

Guarda el archivo.

Cierra gedit.

Cierra la consola

Pulsa el botón derecho del mouse en el icono de red en la 
barra superior a la derecha.

Desactiva la red

Activa la red

---

