---
title: "conectar ubuntu con puppy"
date: 2009-03-23
forum: Hardware
---

### Post by cristhian1625 on 2009-03-23
Hola a todos,mi nombre es cristhian y es la primera vez que ecribo, muy bueno el foro.Aqui va mi pregunta:
Instale hace mas de una semana ubuntu de un cd el cual me enviaron, en un amd Athlon 64 con 512 mb de ram, despues de luchar y navegar por varios foros pude hacer andar el famoso Huawei "alfajor" de arnet, via usb, ahora me gustaria poder conectar en red para compartir internet con una maquina PIII con 90 mb con Puppy linux 4.0 instalado.A la pc las conectopor un cable de red cruzado, no se si esto esta bien o hay que usar uno sin cruzar?
Aca se me complica porque e intentado
pero nada, por eso pido su ayuda, en consola con el comando ifconfig me aparece en la amd que tiene coneccion a internet esto :

cristhian@cristhian-pc:~$ ifconfig 
eth0      Link encap:Ethernet  direcciónHW 00:19:21:f9:b9:13  
          dirección inet6: fe80::219:21ff:fef9:b913/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:573 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:77802 (75.9 KB)  TX bytes:111430 (108.8 KB)
          Interrupción:252 Dirección base: 0x2000 

eth0:avahi Link encap:Ethernet  direcciónHW 00:19:21:f9:b9:13  
          inet dirección:169.254.6.138  Difusión:169.254.255.255  Máscara:255.255.0.0
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          Interrupción:252 Dirección base: 0x2000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:2649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2649 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:168847 (164.8 KB)  TX bytes:168847 (164.8 KB)

nas0      Link encap:Ethernet  direcciónHW 00:73:05:11:f4:05  
          dirección inet6: fe80::273:5ff:fe11:f405/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:141726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88226 errors:13 dropped:0 overruns:13 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:175223316 (167.1 MB)  TX bytes:10747311 (10.2 MB)

ppp0      Link encap:Protocolo punto a punto  
          inet dirección:190.136.144.194  P-t-P:200.3.60.11  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1492  Métrica:1
          RX packets:129092 errors:130147 dropped:0 overruns:0 frame:0
          TX packets:76480 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:164620164 (156.9 MB)  TX bytes:6294560 (6.0 MB)

cristhian@cristhian-pc:~$ 




[COLOR="Blue"]Y en el PIII con Pupy aparece esto:[/COLOR]

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:02:EE:2C:6E  
          inet addr:127.0.1.1  Bcast:127.0.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89869 (87.7 KiB)  TX bytes:77568 (75.7 KiB)
          Interrupt:10 Base address:0x8f80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49164 (48.0 KiB)  TX bytes:49164 (48.0 KiB)
Si alguien me puede ayudar, desde ya se los agradesco.
saludos a todos.

---

### Post by ramiro_md on 2009-03-23
Lo de los cables mucho ni idea, pero para compartir tanto archivos como impresoras necesitas Samba. Leete este artículo de la wiki [http://www.guia-ubuntu.org/index.php?title=Samba](http://www.guia-ubuntu.org/index.php?title=Samba).
UN saludo, espero que te sea de utilidad la info.

---

### Post by cristhian1625 on 2009-03-25
Tengo entendido que samba es para compartir carpetas o discos y no interne, cualquier consejo les agradeceria

---

### Post by ramiro_md on 2009-03-25
si tenés razón entendí mal jeje..probaste con un router ? muchos hacemos eso para llevar internet a otras pc de la casa.

---

### Post by yaroto98 on 2009-03-25
Ayuda [esto]("http://blog.chewearn.com/2009/01/28/internet-connection-sharing-in-ubuntu-intrepid/")?

---

### Post by cristhian1625 on 2009-03-25
con respecto a lo que lei yaroto98, aplique "sudo apt-get install dnsmasq-base" pero el nm-applet no me aparece, ademas esa caja de dialogo de conecciones de red no la tengo o es muy distinta a la que aparece en el ej, 
Encontre algo parecido en : 
"http://www.taringa.net/posts/info/1067887/Compartir-internet-entre-Ubuntu-y-varias-maquinas-sin-switch.html" 
Es algo parecido, solamente que con dos maquinas y dos placas ehernet, lo que veo distinto es que tiene imternet via usb pero a el le aparece como eth2 siendo usb, y a mi me aparece como:
lo        Link encap:Bucle local 
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1613 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:82326 (80.3 KB)  TX bytes:82326 (80.3 KB)

nas0      Link encap:Ethernet  direcciónHW 00:73:05:11:f4:05  
          dirección inet6: fe80::273:5ff:fe11:f405/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:4041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3240 errors:7 dropped:0 overruns:7 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:2168438 (2.0 MB)  TX bytes:637312 (622.3 KB)

ppp0      Link encap:Protocolo punto a punto  
          inet dirección:190.224.120.205  P-t-P:200.3.60.11  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1492  Métrica:1
          RX packets:3767 errors:4039 dropped:0 overruns:0 frame:0
          TX packets:3076 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:2126332 (2.0 MB)  TX bytes:539762 (527.1 KB)

Tendria que cambiar mi configuracion de internet, o se puede hacer como esta en taringa, desde ya cualquier consejo ya que no quiero hacer desastres.saludos

---

### Post by faktorqm on 2009-03-27
Hola, no usaste la funcion "buscar" en el foro, deberias usarla la proxima...

Esta bien que hayas usado un cable cruzado para interconectar asi que hasta ahi vamos bien. 

Dos observaciones:

1) En la pc con ubuntu no configuraste la red. Tenes que poner:

direccion ip: 192.168.1.1
mascara de subred: 255.255.255.0
puerta de enlace: NADA
DNS: NADA

No va nada en los datos por que tu placa de salida es nas0, ok?

En la pc cliente (puppy) tenes que poner:

direccion ip: 192.168.1.2
mascara de subred: 255.255.255.0
puerta de enlace: 192.168.1.1
DNS: 192.168.1.1

2) Para no complicarte la existencia, te recomiendo que te instales firestarter, es un programa grafico para controlar el firewall, y una de las opciones ni bien arranca la primera vez es ayudarte _MUY_ facilmente a compartir la conexion a internet. Ahi seleccionas nas0 como origen y eth0 como destino, y el tipo te hace todo automaticamente.

Salu2!

---

