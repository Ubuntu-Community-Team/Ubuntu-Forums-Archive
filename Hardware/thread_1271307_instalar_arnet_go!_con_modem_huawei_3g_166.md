---
title: "instalar arnet go! con modem huawei 3g 166"
date: 2009-09-20
forum: Hardware
---

### Post by hora92 on 2009-09-20
Hola, desde hace algunas horas estoy disfrutando de Ubuntu, como en casa tengo wifi no tengo inconvenientes en cuanto a conexión, salvo cuando estoy fuera... les comento tengo el pack de arnet go y me pasa que no puedo instalar el modem 3g en Ubuntu.
El modem es el Huawei e160 y la empresa prestadora del servicio es personal

Desde ya muchas gracias

---

### Post by guillermolisi on 2009-09-20
> **hora92 said:**
> Hola, desde hace algunas horas estoy disfrutando de Ubuntu, como en casa tengo wifi no tengo inconvenientes en cuanto a conexión, salvo cuando estoy fuera... les comento tengo el pack de arnet go y me pasa que no puedo instalar el modem 3g en Ubuntu.
El modem es el Huawei e160 y la empresa prestadora del servicio es personal

Desde ya muchas gracias
Dale una leida a [este tutorial]("http://ubuntu-ar.org/node/197") que esta en la seccion Tutoriales del website de Ubuntu-ar.

---

### Post by gmunioz on 2009-09-20
Hola hor...:

Simplemente, cuando quieras utilizar la conexion 3g:

1- Pulsa con el boton derecho en el icono de red y desactivalo.

2- Inserta el modem

3- Pasados unos segundos, edita conexiones de red, elige banda

ancha 3g y configurala con tus parametros, la primera vez, a

partir de alli, despues de insertarlo intentara conectarse.

4- En el supuesto que fuere reconocido como cdrom, lo desmontas

y lo vuelves a montar.

---

### Post by hora92 on 2009-09-26
Gracias Gabriel, ya me reconoce el modem, lo únnico es que ahora me pide la contraseña de personal y del modem, probe con la contraseña que aparece en el tuto que me paso Guillermo, pero no funciona, desde ya muchas gracias

---

### Post by gmunioz on 2009-09-26
Hola hor....:

Estos son los parametros de Personal:

Número de telefono: --- *99#

Usuario: --- gprs 

Password: --- adgj  ó  gprs

Init adicional: ---AT+CGDCONT=1,"IP","gprs.personal.com"

Si usas wvdial, wvdial.conf es:

[Dialer Defaults]
Modem = /dev/ttyUSB0
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init = ATZ
Init2 = AT+CFUN=1
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","gprs.personal.com"
Phone = *99#
Dial Prefix =
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Username = gprs
Password = gprs
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off
Idle Seconds = 0
Auto DNS = off
;Domain =
;Nameserver = 172.25.7.6
;Nameserver2 = 172.25.7.7
;Minimize = off
;Dock = on

---

