---
title: "Modem Zyxel 630-C Serie USB"
date: 2008-07-03
forum: Hardware
---

### Post by Leooo on 2008-07-03
Hola que tal quise instalar este modem Zyxel 630-C Serie USB en Ubunto 8.0.4 segui una guia y me termino tirando este error necesitaria q me ayuden

```
leandro@leandro-desktop:~$ sudo pon dsl-provider
/usr/sbin/pppd: /usr/lib/pppd/2.4.4/rppppoe.: cannot open shared object file: No such file or directory
/usr/sbin/pppd: Couldn't load plugin rppppoe.
```


si me ayudan cuanto antes, perdon si postie mal mi mail es [email]le0_massa@hotmail.com[/email] toy desesperado la verdad todo el dia de ayer intentando

---

### Post by Mauro22 on 2008-07-03
Probaste esto:

```
sudo apt-get install ppp ppp-dev
```


??

---

### Post by Leooo on 2008-07-03
> **Mauro22 said:**
> Probaste esto:

```
sudo apt-get install ppp ppp-dev
```


??

Me tira un error me dice E: nose encuentra el paquete ppp-dev :S

que tengo que hacer?

---

### Post by Mauro22 on 2008-07-03
trata de agregar mas repositorios:

```
sudo gedit /etc/apt/sources.list
```

Y saca el # a los repositorios de restricted multiverse universe

y despues un:

```
sudo apt-get update
```

y volve a inentar lo de antes

---

### Post by Leooo on 2008-07-03
Sigo con los problemas hice lo que me indicaste y mira lo que me tira.

```
leandro@leandro-desktop:~$ sudo gedit /etc/apt/sources.list
[sudo] password for leandro: 
leandro@leandro-desktop:~$ sudo apt-get update
Err http://ar.archive.ubuntu.com hardy Release.gpg
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy/main Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy/restricted Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy/universe Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy/multiverse Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy-updates Release.gpg
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy-updates/main Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy-updates/restricted Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy-updates/universe Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy-updates/multiverse Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy-backports Release.gpg
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy-backports/main Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy-backports/restricted Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy-backports/universe Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://ar.archive.ubuntu.com hardy-backports/multiverse Translation-es
  No pude resolver 'ar.archive.ubuntu.com'
Err http://security.ubuntu.com hardy-security Release.gpg
  No pude resolver 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/main Translation-es
  No pude resolver 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/restricted Translation-es
  No pude resolver 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/universe Translation-es
  No pude resolver 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/multiverse Translation-es
  No pude resolver 'security.ubuntu.com'
Leyendo lista de paquetes... Hecho
W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-es.bz2  No pude resolver 'ar.archive.ubuntu.com'

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  No pude resolver 'security.ubuntu.com'

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2  No pude resolver 'security.ubuntu.com'

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-es.bz2  No pude resolver 'security.ubuntu.com'

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2  No pude resolver 'security.ubuntu.com'

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2  No pude resolver 'security.ubuntu.com'

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas
leandro@leandro-desktop:~$ sudo apt-get install ppp ppp-dev
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
ppp ya está en su versión más reciente.
E: No se pudo encontrar el paquete ppp-dev
leandro@leandro-desktop:~$ 

```

---

### Post by Mauro22 on 2008-07-03
Estuve buscando sobre ese error :S


proba:

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

---

### Post by faktorqm on 2008-07-03
Hola, no vas a poder hacer nunca sudo apt-get install blabla por que por defecto ubuntu te configura la busqueda de paquetes a traves de internet, y si tenes problemas para conectarte, no tenes internet, entonces no podes bajarlos, y te dice por que no puede: No pude resolver 'ar.archive.ubuntu.com' o sea, no puede llegar a los DNS siquiera!

Por defecto, los paquetes ppp, pppoconf y pppconfig vienen incluidos en la instalacion por defecto en ubuntu 8.04, asi que ya los tenes.

Yo ahora estoy investigando sobre ese tema, mañana para las 8 de la mañana te lo posteo, aca no lo tengo, es un nuevo script que lo hace todo automagicamente y ya. Salu2!!

---

### Post by faktorqm on 2008-07-04
Bue se me hizo un poqui tarde... aca va el script.

Descomprimis el archivo, abris una consola y haces:

```
sudo sh black_script_cxacru-fw_v0.4.sh
```

y listo. Te deberia funcionar sin mayores problemas. si no te anda, postea el error.

---

### Post by Leooo on 2008-07-04
Hice lo que me dijiste extrai todo en el escritorio y lo ejecute segui los pasos del scrip (lo hice con el modem desconectado y despues lo puse) y cuando pongo el comando para conectar pasa esto.

```
leandro@leandro-desktop:~/Escritorio$ sudo sh black_script_cxacru-fw_v0.4.sh

¿Qué empresa posee?

1- Speedy (Telefónica)
2- Arnet (Telecom)
3- Otra
4- Salir

1
(Leyendo la base de datos ...  
96050 ficheros y directorios instalados actualmente.)
Preparando para reemplazar br2684ctl 20040226-1 (usando br2684ctl_20040226-1_i386.deb) ...
Desempaquetando el reemplazo de br2684ctl ...
Configurando br2684ctl (20040226-1) ...

Introduzca su nombre de usuario:
********@speedy1m

Introduzca su contraseña:
******
: not foundt_cxacru-fw_v0.4.sh: 85: 
br2684ctl[5925]: Interface "nas0" could not be created, reason: File exists
br2684ctl[5925]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[5925]: Fatal: failed to connect on socket
SIOCSIFFLAGS: Argumento inválido
Plugin rp-pppoe.so loaded.
sendPacket: send: Network is down
leandro@leandro-desktop:~/Escritorio$ pon dsl-provider
/usr/sbin/pppd: /usr/lib/pppd/2.4.4/rppppoe.: cannot open shared object file: No such file or directory
/usr/sbin/pppd: Couldn't load plugin rppppoe.
leandro@leandro-desktop:~/Escritorio$ pon dsl-provider
/usr/sbin/pppd: /usr/lib/pppd/2.4.4/rppppoe.: cannot open shared object file: No such file or directory
/usr/sbin/pppd: Couldn't load plugin rppppoe.


```

:S si se puede hacer algo, pense en formatear todo devuelta e reistalar. decime q opinas respecto a eso, la verdad muchas gracias por ponerle onda y ayudarme :).

saludos

---

### Post by steve_ignorant on 2008-07-04
[http://lihuen.info.unlp.edu.ar/index.php/Como_instalar_el_modem_ZyXel_600_PRESTIGE%28usb%29_en_GNU/LINUX](http://lihuen.info.unlp.edu.ar/index.php/Como_instalar_el_modem_ZyXel_600_PRESTIGE%28usb%29_en_GNU/LINUX)



entra aca, yo tengo el midmo modem lo configure, y lo logre hacer andar. 

solo vas a tener que cambiar los comandos su x sudo y demas...

---

### Post by faktorqm on 2008-07-05
Hola, bueno por lo que vi que paso steve proba de hacer primero 

```
sudo modprobe pppoatm
```

y despues 

```
sudo sh /etc/init.d/adsl_up
```

a ver que ocurre. Salu2!

---

### Post by Leooo on 2008-07-05
puse esos comandos y me dice esto.

```
leandro@leandro-desktop:~$ sudo modprobe pppoatmy
[sudo] password for leandro: 
FATAL: Module pppoatmy not found.
leandro@leandro-desktop:~$ sudo sh /etc/init.d/adsl_up
br2684ctl[5716]: Interface "nas0" could not be created, reason: File exists
br2684ctl[5716]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[5716]: Fatal: failed to connect on socket
Plugin rp-pppoe.so loaded.


Code:
```

---

### Post by faktorqm on 2008-07-05
Capo pone bien el comando, ahi ingresaste una letra "Y" (_I_ griega) de más. Salu2!

---

### Post by Leooo on 2008-07-06
No me habia dado cuenta que lo ingrese mal :S, ahi lo puse como corresponde.


```
leandro@leandro-desktop:~$ sudo modprobe pppoatm
[sudo] password for leandro: 
FATAL: Module pppoatmi not found.
leandro@leandro-desktop:~$ sudo sh /etc/init.d/adsl_up
br2684ctl[5729]: Interface "nas0" could not be created, reason: File exists
br2684ctl[5729]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[5729]: Fatal: failed to connect on socket
Plugin rp-pppoe.so loaded.
PPP session is 3418
Using interface ppp0
Connect: ppp0 <--> nas0
PAP authentication succeeded
peer from calling number 00:90:1A:40:C9:CC authorized
Cannot determine ethernet address for proxy ARP
local  IP address 190.50.186.213
remote IP address 200.51.241.245
primary   DNS address 200.51.211.7
secondary DNS address 200.51.212.7

```

---

### Post by Mauro22 on 2008-07-06
Tenes internet ahora?

---

### Post by Leooo on 2008-07-06
sigo igual. :S

---

### Post by faktorqm on 2008-07-07
ehh pero ahi te tiro los dns, deberias estar saliendo... que raro...

Bueno mira, vamos a hacer esto, primero instalate este paquete por que no te esta levantando el modulo que necesitas para conectarte, luego de que lo instalaste (supongo que tenes ubuntu 32 bits, si no es asi NO lo instales) pone "sudo sh /etc/init.d/adsl_up" y deberia funcionarte. Si sigue encaprichado, ponele "sudo modprobe pppoatm" y luego "sudo sh /etc/init.d/adsl_up". Salu2!!!

---

### Post by Leooo on 2008-07-07
segui los pasos que me recomendaste y sigue con error, cambio de errror esta vez.

```

leandro@leandro-desktop:~$ sudo sh /etc/init.d/adsl_up
[sudo] password for leandro: 
br2684ctl[6011]: Interface "nas0" could not be created, reason: File exists
br2684ctl[6011]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[6011]: Fatal: failed to connect on socket
Plugin rp-pppoe.so loaded.

```

---

### Post by faktorqm on 2008-07-08
ok, hace una cosa

```
sudo modprobe pppoatm
```

```
sudo modprobe br2684
```

```
sudo sh /etc/init.d/adsl_up
```

Ahi lo que te decia es que no podia levantar nas0. Esperemos que funcione. Salu2!!

---

### Post by Leooo on 2008-07-09
faktorqm te llevas todos los premios, logre que ande, es mas estoy desde el Ubuntu :). Muchas gracias fak. Verdaderamente muy agradecido.


saludos :)

---

### Post by faktorqm on 2008-07-09
ok, gracias! :D 

igual omiti decirte algo, que es que cuando reinicies eso se te va a "ir", y, que para que no ocurra, tenes que hacer:

```
sudo gedit /etc/init.d/adsl_up
```

y te va a mostrar esto:

```

#!/bin/bash
br2684ctl -b -c 0 -a 8.35
ifconfig nas0 up
pon proveedor
```

PERO TE TIENE QUE QUEDAR ASI:

```

#!/bin/bash
modprobe pppoatm
modprobe br2684
br2684ctl -b -c 0 -a 8.35
ifconfig nas0 up
pon proveedor
```

y listo el pollo. Gracias a vos por tenerme paciencia y probar mi script. Salu2!!

---

