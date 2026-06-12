---
title: "webcam en blanco y negro"
date: 2009-04-16
forum: Hardware
---

### Post by infernus92 on 2009-04-16
hola... copmo dice el tiyulo... se me ve la webcam en blanco y negro
el programa que use para verla es XawTV que lo baje con el paquete webcamd desde synaptic...
posteo el resultado de lsusb
> miusuario@micomputadora:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 003: ID 0c45:612a Microdia PC Camera (SN9C110)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


es la tercera... Microdia PC Camera (SN9C110)

no se si sera problema de drivers o si es el programa... la verdad ni idea... pero tambien se ve muy oscuro y le puse el brillo al mango y nada...

Saludos

---

### Post by Mauro22 on 2009-04-16
Probá con cheese, que es muy bueno para webcam, tenes efectos, sacar fotos y grabar videos


:popcorn:

---

### Post by staar on 2009-04-16
existe un programa para manejar la configuración de esas camaras, se llama gui-microdia, tenes que agregar estos repos ```
deb http://ppa.launchpad.net/nickel62metal/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/nickel62metal/ppa/ubuntu intrepid main
```

la llave ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xedacd18fa5ad30cc032d213f31cca643cc60ba1f
```

e instalar ```
sudo aptitude install guimicrodia
```

(tomado del blog de geowworld :-D)

saludos

---

### Post by infernus92 on 2009-04-16
estas seguro starr que se llama gui-microdia?? no lo encuentro ni en aptitude ni en synaptic... actualice los repositorios y tampoco...

probe con cheese... muy lindo y agradable el programa... pero sigo viendo en byn... se me ocurre que pueda ser problema de drivers... pero me la reconoce bien segun lo que parece... el unico problema sigue siendo que lo veo en byn

---

### Post by staar on 2009-04-16
es guimicrodia, sin el guión, podes bajarlo directamente del ppa: [https://launchpad.net/~nickel62metal/+archive/ppa]("https://launchpad.net/~nickel62metal/+archive/ppa") o del mensaje en google groups [https://groups.google.com/group/microdia/browse_thread/thread/ba72dcf40ac481a8/02d97178b5a83cb3]("https://groups.google.com/group/microdia/browse_thread/thread/ba72dcf40ac481a8/02d97178b5a83cb3")

saludos

---

### Post by infernus92 on 2009-04-17
esta bueno el programa... pero no me sirvio... la sigo viendo en byn... alguna idea???

Saludos

---

### Post by staar on 2009-04-17
por lo que pude googlear es un bug del driver de esa camara o algo asi, y no encontré niguna solución, para mas info fijate acá [0] OJO, está en inglés, y parece ilegible, pero es solo que el primer mensaje contiene un log y en los demñas mensajes lo citan, entonces cada mensaje queda enorme, lo importante es la primer parte de cada mensaje...

[0][https://groups.google.com/group/microdia/browse_thread/thread/cbc607753fc4f3c2/82c818f4a0e6dac9?lnk=gst&q=black+and+white#82c818f4a0e6dac9]("https://groups.google.com/group/microdia/browse_thread/thread/cbc607753fc4f3c2/82c818f4a0e6dac9?lnk=gst&q=black+and+white#82c818f4a0e6dac9")

saludos

---

