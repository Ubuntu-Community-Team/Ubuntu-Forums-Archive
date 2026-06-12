---
title: "¿Qué adaptador Bluetooth usan?"
date: 2009-07-28
forum: Hardware
---

### Post by felipemaxim on 2009-07-28
¿Alguien tiene idea de si los adaptadores Bluetooth por USB que se consiguen en Bs. As. (Encore, Noga, etc) funcionan bien en Ubuntu?

---

### Post by gmunioz on 2009-07-29
Hola fel...:

Un poco de historia:

Me solicitaron, pasar unos archivos desde una pc

con Windows a un celular mediante un dispositivo

bluetooth, despues de varias fallas del sistema y

del lector de cd, decidi probar en mi pc con Jaunty

y automaticamente funcionó con solo insertarlo, al

pulsar Sistema - Preferencias - Bluetoth me sugirió

conectarse a ese celular y al mio que tambien tiene

y nunca había usado bluetooth.

Entusiasmado por la facilidad de uso, inmediatamente

me compré un genérico a $45 camino a casa.

En mi domicilio, conectado que fue a mi pc con Jaunty

con lsusb lo detectaba como Integrated System Solution 

Corp. Bluetooth Device sin embargo no habia forma de 

conectarme al celular, cambiado el dispositivo a mi pc

con karmic, perfecto igual que la de mi trabajo, conexión

al instante.

Controladas las diferencias entre los dos jaunty, 32 en mi

trabajo 64 en mi domicilio, la diferencia sustancial que

aparecía era que en mi trabajo tengo el kernel 2.6.30.3 y en

mi domicilio el kernel 2.6.29.6, esto es asi porque en mi

domicilio uso graficas nvidia y el driver de jaunty no funciona

en los kernels 2.6.30, así que pinning mediante, instalé el

driver nvidia de karmic y luego el kernel 2.6.30.3, reiniciado

el sistema con ese kernel, el dispositivo funciona sin problemas.

Conclusión:

1- En karmic funciona cualquier dispositivo bluetooth genérico.

2- En jaunty, únicamente si instalas el kernel 2.6.30

---

### Post by felipemaxim on 2009-07-29
Muchas gracias, muchacho.  
Siguiendo tu experiencia traté de actualizar el kernel a la última versión estable 2.6.30 desde 
[HTML]http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/[/HTML]

Instalé primero el paquete linux-source y después linux-image. Pero me tiró este error que aparece en el archivo adjunto. Aparentemente es un error en un módulo aic7xxx, pero como soy medio nuevo en esto la verdad es que no tengo idea. 
¿Tenés idea qué puede estar pasando?

---

### Post by gmunioz on 2009-07-30
Hola Felipe:

Te faltaron aparentemente paquetes.

Los paquetes amd64 son los siguientes:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-source-2.6.30_2.6.30-02063003_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-source-2.6.30_2.6.30-02063003_all.deb)

Puestos todos, en un directorio, 

se instalan con la orden:

sudo dpkg -i *.deb

Para el caso de una versión de 32 bits

los dos paquetes amd64 se cambian por los i386

y los restantes son comunes.

---

### Post by felipemaxim on 2009-07-30
Gracias nuevamente, don. Pero debo estar haciendo algo mal.

Corro uname -r y corroboro que la versión instalada del kernel es 2.6.30-02063003-generic
 
[HTML]sudo apt-cache search linux-headers[/HTML]

terminaba con estas últimas cuatro líneas 

```

linux-headers-server - Linux kernel headers on Server Equipment.
linux-headers-virtual - Linux kernel headers for virtual machines
linux-libc-dev - Linux Kernel Headers for development
linux-source-2.6.28 - Linux kernel source for version 2.6.28 with Ubuntu patches
linux-headers-2.6.30-02063003-generic - Linux kernel headers for version 2.6.30 on x86/x86_64
linux-source-2.6.30 - Linux kernel source for version 2.6.30 with Ubuntu patches
linux-headers-2.6.30-02063003 - Header files related to Linux kernel version 2.6.30
```

Eso quiere decir que las cabeceras están instaladas, ¿no? 

Pero para Synaptic sigue vigente la versión anterior,  2.6.28.13.17 y todas sus dependencias.

¿Por qué será?

---

### Post by gmunioz on 2009-07-31
Hola Felipe:

No estas haciendo nada mal.

Los repositorios ppa no son oficiales.

Synaptic, solo toma los paquetes oficiales

para las actualizaciones, así que siempre 

continuará en esta version, actualizando

solo los paquetes oficiales, en este caso

el kernel 2.6.28.

Una vez que estes completamente satisfecho 

con el funcionamiento del kernel 2.6.30, debes

desde Synaptic desinstalar los kernels 2.6.28

para que no los siga actualizando.

---

### Post by Hei Ku on 2009-07-31
En realidad, lo que "hiciste mal" fue copiar los archivos .deb del PPA, en vez de agregar ese PPA a Synaptic.
Son dos formas de hacerlo, pero si lo hubieras agregado a la lista de repositorios, ahora te apareceria ese como ultima actualizacion. Fijate que hay un Sticky sobre como agregar PPAs.

---

### Post by felipemaxim on 2009-07-31
Son muy amables, gracias.

---

### Post by gmunioz on 2009-07-31
Hola Hei-ku:

Según hasta donde se, que es muy poco, el

sitio de los kernels ppa mainline

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

No se puede agregar como repositorio y demanda

que los kernels se actualicen en forma manual.

---

