---
title: "Problema con D510MO"
date: 2010-11-22
forum: Hardware
---

### Post by adcoma on 2010-11-22
Hola!!

Paso aqui para molestarlos con una consulta:

Tengo una motherboard D510MO la cual tiene una tarjeta de red Realteck 8111DL y ubuntu carga los drivers de la 8169... en ocaciones funciona perfecto y en otras tantas no funciona anda!!!

Ya estoy desesperado llevo dias buscando solucion y nada, esta pagina explica bien lo que pasa y da una solucion: [http://amk1.wordpress.com/2009/06/09/realtek-8168-module-issue](http://amk1.wordpress.com/2009/06/09/realtek-8168-module-issue)

Pero por alguna razon no me funciona... aunque la placa no es la misma el problema y la tarjeta de red es identico.

Alguien sabe de esto???

Saludos.

---

### Post by alfplayer on 2010-11-22
La red en esa motherboard funciona sin problema en mi Arch Linux, sin hacer cambios de ningún tipo. La salida de lshw:

```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 00:27:0e:07:33:3a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="Blue"]driver=r8169 driverversion=2.3LK-NAPI[/COLOR] duplex=full ip=192.168.1.1 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff memory:f0020000-f003ffff
```

Qué versión de Ubuntu?

Ese link es de julio, puede tener información muy vieja para ser útil.

Si es un bug de Ubuntu, se puede buscar en [http://bugs.launchpad.net]("http://bugs.launchpad.net").

---

### Post by adcoma on 2010-11-22
Mil gracias por tu respuesta!

El ubuntu que uso es el 10.04 Desktop, que version de Arch Linux tienes?

Saludos.

---

### Post by alfplayer on 2010-11-22
Arch Linux es "rolling-release". No lo actualizo hace unas semanas, y está funcionando bien hace unos meses.

---

### Post by adcoma on 2010-11-22
Bajare Arch Linux y probare... el PC que quiero levantar deberia de tener dos NIC la integrada y una mas en el PCI ya que mi intencion es armar firewall!

Esto con Zentyal, veremos como anda Arch Linux...

Pero si alguienmas tiene la solucion a esto se los agradeceria. ya que Zential esta basado en ubuntu.

Saludos.

---

### Post by alfplayer on 2010-11-22
No es necesario instalar Arch Linux. Sería cuestión de instalar el driver correcto a ubuntu (repito, si el problema es un bug de ubuntu y no otro problema como cableado).

---

### Post by adcoma on 2010-11-22
Entiendo lo que me dices... mira he seguido muchos tutoriales y nada... y si esta reportado en: [launchpad]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=r8168&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=").

Saludos.

---

### Post by alfplayer on 2010-11-22
En Launchpad y en Ubuntu Forums no encontré nada para el caso, lo que hace pensar que funciona bien. Podría ser un problema solucionado actualizando el BIOS.

En Arch estoy usando el paquete kernel26 para i686 versión 2.6.35.7-1.

---

### Post by adcoma on 2010-11-22
OK, revisare lo del BIOS quiza halla algo.

Dejo unos links tratando el tema y con algunas soluciones, no solo en ubuntu tambien en otras distros:

[http://amk1.wordpress.com/2009/06/09/realtek-8168-module-issue/](http://amk1.wordpress.com/2009/06/09/realtek-8168-module-issue/)

[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

[http://wiki.linuxmce.org/index.php/R8168#Hacking_the_r8169_module](http://wiki.linuxmce.org/index.php/R8168#Hacking_the_r8169_module)

[http://samiux.blogspot.com/2010/02/howto-untangle-71-on-intel-desktop.html](http://samiux.blogspot.com/2010/02/howto-untangle-71-on-intel-desktop.html)

Pero... ninguno me funciona!

Saludos! 

PD: Informare del BIOS mas tarde, al llegar a casa.

---

### Post by alfplayer on 2010-11-22
Estoy recordando que a veces, copiando archivos grandes al D510MO con rsync y sshfs (con el servidor ssh en el D510MO), la conexión de sshfs se corta, pero puedo reconectar sshfs inmediatamente después. Puede estar relacionado con este problema.

---

### Post by adcoma on 2010-11-23
Bueno pues por aca de nuevo... el BIOS lo actualize a la ultima version para esta mother y ni al caso, sigue el mismo detalle.

Ya estoy siguiendo estos hilos en lounchpad: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252307](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252307)
[https://bugs.launchpad.net/ubuntu/+bug/208012](https://bugs.launchpad.net/ubuntu/+bug/208012)

Saludos.

---

### Post by alfplayer on 2010-11-23
Hola.

Esos links de Launchpad no especifican la versión DL, que es la que tiene el motherboard, aunque pueden estar relacionados.

Como solución aunque sea temporal, podría probarse una versión superior de Linux.

---

### Post by adcoma on 2010-11-23
Si en efecto, quiero probar la 8.04 y la 10.10  aver como va... al llegar a casa lo intento.

Saludos.

---

### Post by adcoma on 2010-11-24
Pues probado con estas dos versiones y la situación prevalece!

Saludos.

---

### Post by alfplayer on 2010-11-24
Lo mejor que se me ocurre es probar con un live de Arch Linux. También creo que puede ser un problema del motherboard.

---

### Post by alfplayer on 2011-02-09
Novedades?

Ahora tengo errores en NFS. Creo que pueden tener la misma causa.

---

