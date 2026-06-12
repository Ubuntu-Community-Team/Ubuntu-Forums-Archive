---
title: "Problema con Coneccion Telefonica a Internet"
date: 2011-09-15
forum: Instalación y Actualización
---

### Post by leizar on 2011-09-15
hola amigos, les cuento mi problema, resulta que actualicé mi ubuntu del 10.4LTS a 11.04, y lo primero que resalta es "it seems that you do not have the hardware required to run unity. please choose ubuntu clasic at the login screen and you will be using the tradicional environment"
bueno, después de iniciar sesión, conecto mi celular lg ks360 o gt360 y creo la conexión (gsm creo) pero es imposible conectarme, intenta conectarse pero en menos de un segundo resalta el mensaje de que no está conectado.
bueno eso, este problema ocurre desde que instale 11.04 porque en la versión 10.4LTS conectaba el teléfono, creaba la conexión seleccionando país, proveedor y plan, y listo
eso, saludos

---

### Post by charlymx on 2011-09-17
Se un poco mas especifico con el problema, que quieres hacer realmente? quieres que tu computadora se conecte a internet por medio de tu celular?  o solo quieres saber porque te salio el mensaje al actaulizar en relación al hardware?.

esperamos tu respuesta para ver si te podemos ayudar.:)

---

### Post by leizar on 2011-09-22
> **charlymx said:**
> Se un poco mas especifico con el problema, que quieres hacer realmente? quieres que tu computadora se conecte a internet por medio de tu celular?  o solo quieres saber porque te salio el mensaje al actaulizar en relación al hardware?.

esperamos tu respuesta para ver si te podemos ayudar.:)
hola amigo, gracias por tu respuesta, y disculpa por la demora, el laburo aveces no deja ni respirar, lo que quiero hacer es conectar mi desktop a internet por medio de mi telefono celular, lo curioso, es que con la version 10.4 me funciona hasta con el live CD (previo a seleccionar pais, proveedor y plan)
bueno de antemano gracias =}

---

### Post by asterix77 on 2011-09-22
Creo aún que faltan datos para poder ayudarte

a) La conexión la quieres hacer a través de cable o bluetooth?
b) Que usabas para conectarte en Lucid?. Deduzco network-manager
c) A que empresa ISP te quieres conectar?

Hay varias formas de poder conectarte, yo en personal por ejemplo, uso bluetooth para conectarme a mi celular a mi notebook vía wvdial, y de este modo tener acceso a internet

Puedes usar network-manager, wvdial, o gnome ppp por darte algún ejemplo.


Saludos

---

### Post by leizar on 2011-09-23
> **asterix77 said:**
> Creo aún que faltan datos para poder ayudarte

a) La conexión la quieres hacer a través de cable o bluetooth?
b) Que usabas para conectarte en Lucid?. Deduzco network-manager
c) A que empresa ISP te quieres conectar?

Hay varias formas de poder conectarte, yo en personal por ejemplo, uso bluetooth para conectarme a mi celular a mi notebook vía wvdial, y de este modo tener acceso a internet

Puedes usar network-manager, wvdial, o gnome ppp por darte algún ejemplo.


Saludos
aah claro, bueno mi pc es un desktop, conecto el celular por el cable usb, en ubuntu me conecto con el programa que viene por defecto
y la empresa a la que me quiero conectar es a entel
y prove con los 2 opciones
bam.entelpcs.cl
y imovil.entelpcs.cl
nuevamente gracias por tus respuestas =)

---

### Post by asterix77 on 2011-09-27
Espero no sea tarde para responder.

Bueno, lo primero que debes saber es si tu celular es detectado como módem. Ejecuta en una terminal el siguiente comando y pégalo acá.
$lsusb

Aunque para serte sincero, nunca he conectado mi celular por cable usb. Me resulta más cómodo hacerlo por bluetooth.

fíjate además si es que tienes instalado el paquete usb-modeswitch, de lo contrario, instálalo.

Saludos

PD: La salida del comando lsusb hazlo primero sin instalar el paquete, y luego con el usb-modeswitch instalado para ver si hay algún cambio, y obviamente con el celular conectado.

---

### Post by leizar on 2011-09-27
> **asterix77 said:**
> Espero no sea tarde para responder.

Bueno, lo primero que debes saber es si tu celular es detectado como módem. Ejecuta en una terminal el siguiente comando y pégalo acá.
$lsusb

Aunque para serte sincero, nunca he conectado mi celular por cable usb. Me resulta más cómodo hacerlo por bluetooth.

fíjate además si es que tienes instalado el paquete usb-modeswitch, de lo contrario, instálalo.

Saludos

PD: La salida del comando lsusb hazlo primero sin instalar el paquete, y luego con el usb-modeswitch instalado para ver si hay algún cambio, y obviamente con el celular conectado.
gracias por tu respuesta, no la verdad es que no es tarde =)
ejecutare el comando en tanto llege a la casa, pero existe alguna forma de descargar el paquete usb-modeswitch desde winSO y para llevarlo a casa?

---

### Post by asterix77 on 2011-09-27
Si se puede, aunque la gracia de hacerlo conectado a Internet por cualquier otra vía, es que si tiene dependencias, te las descarga de forma automática.

Te dejo el link del paquete usb-modeswitch-data

[https://launchpad.net/ubuntu/natty/+package/usb-modeswitch-data](https://launchpad.net/ubuntu/natty/+package/usb-modeswitch-data)

Debes escoger según tu arquitectura (archivo con extensión .deb)

Además el paquete anterior depende de usb-modeswitch

[https://launchpad.net/ubuntu/+source/usb-modeswitch/1.1.7-1](https://launchpad.net/ubuntu/+source/usb-modeswitch/1.1.7-1)

Debes escoger según arquitectura aquí.
       **Builds**

                [Natty]("https://launchpad.net/ubuntu/natty"):                        [IMG]https://launchpad.net/@@/build-success[/IMG]             [amd64]("https://launchpad.net/ubuntu/+source/usb-modeswitch/1.1.7-1/+build/2303817")                                                                            [IMG]https://launchpad.net/@@/build-success[/IMG]             [armel]("https://launchpad.net/ubuntu/+source/usb-modeswitch/1.1.7-1/+build/2303818")                                                                            [IMG]https://launchpad.net/@@/build-success[/IMG]             [i386]("https://launchpad.net/ubuntu/+source/usb-modeswitch/1.1.7-1/+build/2303819")                                                                            [IMG]https://launchpad.net/@@/build-success[/IMG]             [powerpc]("https://launchpad.net/ubuntu/+source/usb-modeswitch/1.1.7-1/+build/2303820")                                                             
            


Simplemente después le das un doble click y listo. Creo que debes instalar usb-modeswitch primero.

Saludos

---

