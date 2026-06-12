---
title: "Problema internet"
date: 2008-10-02
forum: Hardware
---

### Post by yo33 on 2008-10-02
Wenas, primero que nada, quiero decirles ke soy nuevo en linux, asi ke no tengo idea de nada.

Mi modem es un HUAWEI SmartAX MT880. No tengo idea de como conectarme a internet, lei que en el terminal tengo que poner "sudo pppoeconf" pero cualquier comando que escriba que incluya la palabra "sudo" me dice "unable to resolve host name: zarky-desktop" y mas abajo me dice que ponga la pass, pero no me deja teclearla.

Muchisimas gracias a todos, chao y suerte ^^

PD: Tengo ubuntu 8.04 desktop edition de 64 bits. Mi procesador es un AMD 64 x2 de 2,7ghz

---

### Post by ArgentinoGuy on 2008-10-02
uhhh, la verdad que no tengo idea que problema es ese, capaz es algun bug del hardy 64, yo tengo de 32 en todo caso en vez de usar sudo directamente entra como root y hace todo lo que quieras y despues lo deslogueas.
Entrando como root ya no necesitas usar el comando sudo.

---

### Post by yo33 on 2008-10-02
Como entro como root? el root es el usuario ke tiene los privilegios de administrador, no? porke nomas tengo 1 usuario xD

---

### Post by luks911 on 2008-10-02
> **yo33 said:**
> Como entro como root? el root es el usuario ke tiene los privilegios de administrador, no? porke nomas tengo 1 usuario xD

Para entrar como root, el comando es o uno de ellos, no lo tengo claro

```
su -s
```

luego la contraseña

---

### Post by sajnox on 2008-10-02
> **luks911 said:**
> Para entrar como root, el comando es o uno de ellos, no lo tengo claro

```
su -s
```

luego la contraseña

No es necesario hacer esto, sino que es hasta peligroso. 

Por seguridad (y te aconsejo que lo dejes asi) el usuario root no esta habilitado a simple vista, podes hacer todo lo que haces como root utilizando el comando sudo antes del comando.

"no me deja poner contraseña" Vos no lo podes ver, pero si estas ingresando el dato. No te preocupes.

Cual es la contraseña? Es tu contraseña de usuario, el usuario que instalo la maquina tiene permisos para el comando sudo.

Por el lado del error "unable to resolve host" mira este link [1] que explica como solucionarlo

[1] [http://mundogeek.net/archivos/2008/04/27/ubuntu-sudo-unable-to-resolve-host/](http://mundogeek.net/archivos/2008/04/27/ubuntu-sudo-unable-to-resolve-host/)

---

### Post by yo33 on 2008-10-02
Oks, ya probe, probe, y el pppoeconf se abre, puse todo como lei ke tiene ke estar, y sigo sin internet.

Sera que tengo que configurar el modem para que sea router? xD

Muchisimas gracias gente, suerte ^^

---

### Post by faktorqm on 2008-10-03
si configuralo en modo router y olvidate del pppoe-blabla. busca en el foro que ya se postio un paso a paso de como hacerlo. salu2!

---

### Post by yo33 on 2008-10-03
Oks, muchisimas gracias, pero una dudita... si lo configuro como router, va a cambiar algo? osea... voy a tener ke conectarme de diferente manera en windows?

Gracias, y suerte xD

---

### Post by sajnox on 2008-10-03
> **yo33 said:**
> Oks, muchisimas gracias, pero una dudita... si lo configuro como router, va a cambiar algo? osea... voy a tener ke conectarme de diferente manera en windows?

Gracias, y suerte xD

Si, te conectas en forma distinta...pasa a ser mucho mas facil ya que el que se encarga de gestionar la conexion es el router y no tu PC. Si funciona bien, simplemente no tenes que tocar nada por que ya estas conectado

---

### Post by yo33 on 2008-10-03
Acabo de configurarlo como router (con windows XP) y tube ke resetear el modem, porke no me andaba internet.

Sera porke lo hice con windows XP? si lo hago con ubuntu, tampoco voy a necesitar poner el usuario y pass de inet con windows?

Muchisimas gracias, nos vemos.

---

### Post by faktorqm on 2008-10-03
no, justamente si lo pones en el router no necesitas ponerlo mas en ningun sistema operativo que uses. pone las placas de red en dhcp y listo, y cerciorate de haberlas puesto bien (nunca esta de mas una revisada). Salu2!

---

