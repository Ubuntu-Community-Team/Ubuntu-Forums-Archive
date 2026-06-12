---
title: "wifi no funciona"
date: 2010-07-21
forum: Hardware
---

### Post by capcabgue on 2010-07-21
Hola a todos:

Les cuento que quise probar el escritorio KDE, por lo cual instalé kubuntu-desktop, efectivamente me quedó instalado kubuntu, como esperaba.
Ahora los problemas, al conectarme a internet, por ethernet, ningún problema, sin embargo, si trato de conectarme de manera inalambrica no puedo (no me entregha IP).
Lo raro, es que en Ubuntu, funciona sin problema (tuve que activar primero los driver restrictivos), y en kubuntu ya esta activado.
No entiendo que pasa, el mapeo de redes ve algunas redes existentes (por lo cual me reconoce la antena), Ubuntu captura todas.
En fin quisiera probar el ambiente de trabajo en KDE, alguien me puede decir que puedo hacer.
Las carácterísticas de su PC son las siguientes:
Dell Inspiron 1525, Processor	Intel Core 2 Duo T5450 1.66GHz, Screen	15.4&#8221; WXGA Widescreen, RAM	2GB, HDD	160GB, Optical Drive	DVD+-RW, Intel Graphics Media Accelerator X3100
Network	Ethernet, Intel 3945 802.11abg.

Espero me puedan ayudar

---

### Post by asterix77 on 2010-07-21
¿Quien es tu proveedor de servicios de internet?. Te pregunto esto porque en mi caso es Telefonica del sur, el cual usa un marcado pppoe sobre wifi.

Puedes detectar las redes wifi a tu alrededor e inclusive puedes conectarte a ellas, pero no tendrás acceso a internet (salvo que te conectes directamente al router AP por cable) ya que debes configurar pppoe (nombre de usuario y contraseña es diferente a la usada para conectarte a router wifi).

Si este es tu caso debes correr 

#pppoeconfig

y sigues los pasos, di a todo que sí. Ojo que primero debes asociarte al AP primero para que la configuración sea la correcta.


De todos modos no sería malo que digitaras que arroja el comando

#ifconfig
#iwconfig

Saludos

---

### Post by capcabgue on 2010-07-21
Mi Proveedor es Timofonica.
Pero definitivamente no creo que sea eso de la configuración PPOEt, ya que si enchufo e la red mi notebook salgo como cañon, pero por wifi no.
Ahora lo más raro es que si estoy en ubuntu no tengo problemas, pero en Kubuntu, solamente me reconoce la tarjeta wifi, pero no me da IP.
COn el comando ifconfig, la eth1 (wifi) no tiene IP

Espero sea útil esto

---

