---
title: "Ubuntu 8.10 reconoce modems 3g y da DNS erroneos !"
date: 2009-02-15
forum: Hardware
---

### Post by feder1991 on 2009-02-15
Bueno, primero les paso a comentar: una de las cosas que me mantenia ligado a window$ era la conexion a internet (uso el modem de claro 3g huawei e226), pero ahora me entere que ubuntu 8.10 nos tubo en cuenta y reconoce automaticamente un modem con la etiqueta de banda ancha movil.

Dicho y hecho, instale ubuntu y aparecio banda ancha movil bla bla bla: para configurarlo, haz click aqui. Despues de poner usuario, contraseña y muchas cosas mas.. fui a la pestaña iv4 donde decia servidores DNS: y por lo que habia visto en un foro yankee, si ponia esos dns me iba a conectar pero no iba a navegar. Prove a ver si conectaba, y el modem prendio la luz y conecto, pero no recibia datos (asi que no andaba, como lo predijo el foro yankee), entonces decian que hay que poner un DNS Publico.

Probe como con 20 convinaciones de dns publicos y NADA

Linuxeros: quiero saber cual es la configuracion que usan para el modem 3g de claro? por que sino estoy condenado a seguir usando windows y eso ya me esta artando...

Muchas gracias señores y señoras por leer el mensaje, los invito a responder

---

### Post by faktorqm on 2009-02-15
Probate con los de openDNS? salu2!

---

### Post by staar on 2009-02-15
mira yo tengo ese mismo modem, y logre que andara despues de mucho renegar, no habia forma de que el nm se acordara los dns, asi que me conectaba, y despues los cambiaba en el resolv.conf, hasta que, no se como, el nm decidio andar bien, y ahora joya, eso si, yo ponia los dns de claro: 170.51.255.100 y 170.51.242.18

saludos

---

### Post by villa77 on 2009-02-15
Acá tenés la respuesta.
[http://ubuntu-ar.org/node/197](http://ubuntu-ar.org/node/197)

---

