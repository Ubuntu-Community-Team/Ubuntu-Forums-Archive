---
title: "Auxilio actualizaba a ubuntu 9.04 mi maquina se apago"
date: 2009-05-01
forum: Hardware
---

### Post by pocohombre on 2009-05-01
HOLA MIENTRAS ACTUALIZA A UBUNTU 9.04 MI COMPU SE APAGO A LA MITAD DE LA 
 
INSTALACION AL VOLVERLA A PRENDER ME PIDE MI USUARIO DE MANERA NORMAL 
 
PERO NO DETECTA NI EL TECLADO NI EL MAUSE INTENTE RESOLVERLO CON ALGO
 
QUE DECIA sajnox pero no puedo Y PUES COMO VERAN SOY NUEVO EN ESTAs cosas
 
por favor ayuda  
 
saludos y gracias

---

### Post by cartos on 2009-05-01
probaste con el live cd haber si te funciona todo?

---

### Post by pocohombre on 2009-05-01
si todo funciona....

---

### Post by cartos on 2009-05-01
joya que bueno!!!!! reinstalalo y disfrutarlo!!!!!!!!!!!!!

saludos!!!

---

### Post by pocohombre on 2009-05-01
a ok gracias, no sabras otra forma?  esque no quiero perder el software que utilizo.... como se hacerca la presentacion de mi tesis
 
 
gracias

---

### Post by ADICTOALMAXIMO on 2009-05-02
A mi me paso seguido

y no e consegudio mas solucion que reinstalar
saludos

---

### Post by gmunioz on 2009-05-02
Hola poc...:

Al iniciar el ordenador, pulsa escape.

En el menu del Grub elige recuperación.

En el submenu emergente elige netroot

Iniciarás como administrador sin contraseña, en consola

Ejecuta en la consola

dpkg --configure -a

apt-get update

apt-get upgrade

reboot

Repite el procedimiento, pero en el submenu elige fix de las graficas

Reinicia e intenta iniciar en modo normal.

Saludos.

---

### Post by pocohombre on 2009-05-02
GRACIAS ADICTO ALMAXIMO CREEME QUE ME ESTOY DESESPERANDP Y NO TENDRE DE OTRA.
 
HOLA gmunioz PERFECTO YA SEGUI TUS RECOMENDACIONES Y TENGO LO SIGUIENTE
 
AL APRETAR ESC APARECE:
 
 
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.27-11-generic
Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.27-9-generic
Ubuntu 9.04, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.27-7-generic
Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode) 
Ubuntu 9.04, memtest86*
 
ENTONCES ELEGI 
 
Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode) 
 
ASI SE DESPLIEGA:
 
Recovery Menu  
                 
                  resume
                  clean
                   dpkg

---

### Post by pocohombre on 2009-05-02
Recovery Menu 

resume
clean
dpkg
fsck
root
xfix
 
DE LA CUAL ELEGI
 
root
 
Y TECLEO
 
dpkg --configure -a

ME DESPLIEGA EL SIGUIENTE MENSAJE
 
Processing was halted because thre were too many errors
 
Y CUANDO INTENTO CON
 
apt-get update

apt-get upgrade
 
DESPLIEGA
 
Err [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty Release.gpg
  Could not resolve 'mx.archive.ubuntu.com'
 
 
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty Release.gpg
  Could not resolve 'security.ubuntu.com'
 
QUE CRES QUE DEBA HACER?
 
GRACIAS POR TU AYUDA

---

### Post by Hei Ku on 2009-05-02
Si sos nuevo con Linux, lo mas rapido es que reinstales. Se puede solucionar, pero requiere mucha pericia con el dpkg, que evidentemente no tenes. Si estas apurado por tu tesis, reinstala.

---

### Post by pocohombre on 2009-05-02
Ok me doy por vencido ya reinstale jajajajj

saludos y gracias por todo

---

