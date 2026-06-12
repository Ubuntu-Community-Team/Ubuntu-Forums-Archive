---
title: "Vbox XP sobre Ubuntu 10.04 - Problema con USB"
date: 2010-08-18
forum: Instalación y Actualización
---

### Post by rba1204 on 2010-08-18
Estimados,
Tengo instalado Vbox en Ubuntu 10.04 como hst y XP (sorry) como guest
Mi problema parece que es conocido pero he leido varios foros y buscado solucion desde hace varios dias y no lo he podido solucionar
Tengo instalados las GuestAdditions, y activado los filtros en VBox, pero cuando inserto un dispositvo USB me aparece no accesible, excepto una impresora  que si aparece accesible, HD, pendrive y otros no son accesibles desde XP
Por favor cualquier ayuda es bienvenida
Gracias de antemano

---

### Post by moreback on 2010-09-25
Si un dispositivo USB aparece como ocupado significa el sistema huésped (host) lo está utilizando, lo que significa que en tu Ubuntu se está reconociendo el driver para ese dispositivo y se está cargando en el kernel.

Creo que se pueden usar una blacklist (hay un archivo así en /etc, no me acuerdo el lugar preciso) para que el kernel no cargue el driver y con eso no ocupe el dispositivo (y lo puedas usar con VBox).

Saludos.

---

### Post by themasterdark on 2010-09-25
1.- Realiza lo que indica moreback, suele ser a veces la solución.

el archivo se encuentra en 

/etc/blacklist.conf

PD: debes saber cual es el modulo (driver) que usa tu hardware para ingresarlo al blacklist, eso lo buscas en google.

2.- Por otro lado cada vez que uses un nuevo dispositivo usb debes indicarle al sistema huesped por medio de los filtros el que usaras agregandolos antes de arrancar el sistema huesped.

Saludos y espero des con la solución

---

