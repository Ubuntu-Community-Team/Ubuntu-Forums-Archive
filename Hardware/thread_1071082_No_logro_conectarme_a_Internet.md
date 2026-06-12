---
title: "No logro conectarme a Internet"
date: 2009-02-15
forum: Hardware
---

### Post by Terraman on 2009-02-15
¡Hola a todos!

He instalado Ubuntu 8.04 en versión mínima para la Notebook que figura en la firma con LXDE como gestor de ventanas. Al momento de instalar Ubuntu, no poseía la tarjeta para conectar al modem. Ahora he coseguido una y no logro conectarme a Internet a pesar de que la tarjeta es reconocida. He leído diversos tutoriales sin lograr el objetivo.

¿Alguién me podrá ayudar?

Les paso el detalle del comando "lshw":
```
     *-network DISABLED
          description: Ethernet interface
          product: 3cCFE575BT Megahertz 10/100 LAN CardBus [Cyclone]
          vendor: 3Com Corporation
          physical id: 0
          bus info: pci@0000:05:00.0
          logical name: eth1
          version: 01
          serial: 00:10:4b:7c:9a:16
          size: 10MB/s
          capacity: 100MB/s
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=yes maxlatency=5 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
```

También los datos del comando "ifconfig":```
eth1      Link encap:Ethernet  HWaddr 00:10:4b:7c:9a:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xc000 

```

Desde ya muchas gracias.

---

### Post by Hei Ku on 2009-02-15
figura como disabled.

Postea el archivo /etc/network/interfaces

Y que pasa si haces?

sudo /etc/init.d/network restart

---

### Post by Terraman on 2009-02-16
> **Hei Ku said:**
> figura como disabled.

Postea el archivo /etc/network/interfaces

Y que pasa si haces?

sudo /etc/init.d/network restart

Postea el archivo /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

Y que pasa si haces?

sudo /etc/init.d/network restart:```
command not found
```

No poseo el programa "network", pero si el "networking":

sudo /etc/init.d/networking restart:
```
Reconfiguring network interfaces...done.
```

Sigue todo igual...

---

### Post by fmsismo on 2009-02-16
Hace
< sudo ifconfig -a
Y copianos que te devuelve por acá.

Estas usando entorno gráfico.

Para probar hace:

< sudo ifconfig eth1 up
< sudo dhclient eth1

Verifica que el eth1 sea tu placa, por lo que posteas veo que tenes una placa como eth1 (no se porque no la vió como eth0)

Si el ifconfig -a te listo una placa eth0 que no veías proba de ejecutar los comandos que te pase con esa placa.

Todos los comandos que te pase no hacen modificaciones permanentes, cuando reinicies volves a donde estabas pero nos va a servir para ver como dejar la configuración ok.

---

### Post by Terraman on 2009-02-16
fmsismo,

< sudo ifconfig -a> eth1      Link encap:Ethernet  HWaddr 00:10:4b:7c:9a:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)


< sudo ifconfig eth1 up
< sudo dhclient eth1

Con los comandos de arriba comenzó a funcionar Internet. De hecho estoy escribiendo dsde la Notebook. ¿Dónde instalo los comandos para que funcione al arranque?

Muchas gracias,

---

### Post by fmsismo on 2009-02-16
Excelente!

Bueno tenes que agregar las siguientes lineas en el archivo /etc/network/interfaces

# The primary network interface
auto eth1
iface eth1 inet dhcp

Esto lo podes hacer con el nano o con el vi

< sudo vi

o 

< sudo nano

Los hombres de pelo en pecho usan vi ;-)

Cualquier cosa avisa así vemos de seguir "amacando" el problema.

Saludos

---

### Post by Hei Ku on 2009-02-16
Para abrirlo directamente con el nano:

```

sudo nano /etc/network/interfaces

```

Los hombres de espalda peluda editan directo en hexa. :p

---

### Post by Terraman on 2009-02-17
fmsismo,

Como tengo pelo en pecho edito en vi

Muchas gracias,

---

### Post by Terraman on 2009-02-17
Hei Ku,

A pesar de tener espalda peluda, no me da para editar en hexa.

Muchas gracias,

---

### Post by guillermolisi on 2009-02-17
Es que Sismo y HeiKu son el Yeti y el Hombre Lobo, respectivamente :)

(disculpen la licencia, pero no pude aguantar la tentacion)

---

