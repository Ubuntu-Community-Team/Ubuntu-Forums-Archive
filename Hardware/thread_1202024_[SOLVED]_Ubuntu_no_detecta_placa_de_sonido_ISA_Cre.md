---
title: "[SOLVED] Ubuntu no detecta placa de sonido ISA Creative"
date: 2009-07-01
forum: Hardware
---

### Post by Einfachlacm on 2009-07-01
Hola,

como dice el titulo, tengo esta placa y ni Ubuntu ni Xubuntu la detectan, no se que hacer para activarla. La placa andaba lo mas bien en el XP antes de que le instalara Ubuntu arriba.

Al hacer click en el parlantito aparec una leyenda que dice: "GStreamer no pudo detectar ningun dispositivo de sonido. Puede que falten algunos paquetes especificos del sistema de sonido GStreamer. Tambien puede ser un problema de permisos." En el Synaptic ya instalé todo lo que dice GStreamer y ALSA y no pasa nada todavia.

Alguna sugerencia de que puedo hacer?

Gracias de antemano.

---

### Post by guillermolisi on 2009-07-01
> **Einfachlacm said:**
> Hola,

como dice el titulo, tengo esta placa y ni Ubuntu ni Xubuntu la detectan, no se que hacer para activarla. La placa andaba lo mas bien en el XP antes de que le instalara Ubuntu arriba.

Al hacer click en el parlantito aparec una leyenda que dice: "GStreamer no pudo detectar ningun dispositivo de sonido. Puede que falten algunos paquetes especificos del sistema de sonido GStreamer. Tambien puede ser un problema de permisos." En el Synaptic ya instalé todo lo que dice GStreamer y ALSA y no pasa nada todavia.

Alguna sugerencia de que puedo hacer?

Gracias de antemano.
Que versiones de Ubuntu/Xubuntu probaste ?

---

### Post by Einfachlacm on 2009-07-01
Probé con Ubuntu Jaunty, ahora con Xubuntu Jaunty.


La placa es esta : CREATIVE LABS SOUND BLASTER 16 (16F) - CT2940

[http://www.manotechsolutions.com/shop/surprise-bin-23/used-creative-labs-sound-blaster-16-16f-ct2940-16.html](http://www.manotechsolutions.com/shop/surprise-bin-23/used-creative-labs-sound-blaster-16-16f-ct2940-16.html)

---

### Post by gmunioz on 2009-07-01
Hola ein....:

En el caso de los dispositivos ISA, especificamente audio; como es tu 

tarjeta la deteccion automatica es desactivada para evitar problemas con

las interrupciones

1- Instala: isapnptool

2- Ejecuta:  sudo pnpdump>info

3- Ejecuta: sudo isapnp info

4. Ejecuta: sudo gedit /etc/modules

Agrega 

snd-sbawe 

Al final del archivo /etc/modules

=============fin=============
Este paso es obsoleto

5- habilita tu usuario para los grupos everybody y audio

---

### Post by Einfachlacm on 2009-07-01
Hola Gabriel,

Gracias por tu respuesta!

Ya hice todo hasta el punto 4, instalé la version 1.26.5 de isapnptools. E la terminal quedo así:

gil@familiagil:~$ sudo pnpdump>info
[sudo] password for gil: 
gil@familiagil:~$ sudo isapnp info
Board 1 has Identity 37 10 0c 29 d2 24 00 8c 0e:  CTL0024 Serial No 269232594 [checksum 37]
gil@familiagil:~$ sudo gedit /etc/modules

el primer comando, como se ve ahi, no me respondio nada.
Ahora lo que no se como hacer es el paso 5, habilitar tu usario para los grupos everybody y audio, como puedo hacerlo?

Gracias!

---

### Post by Einfachlacm on 2009-07-01
Por cierto, creo que el segundo punto si hizo algo, me aparecio un archivo "info" en la home:


# $Id: pnpdump_main.c,v 1.27 2001/04/30 21:54:53 fox Exp $
# Release isapnptools-1.26
# 
# This is free software, see the sources for details.
# This software has NO WARRANTY, use at your OWN RISK
# 
# For details of the output file format, see isapnp.conf
# 
# For latest information and FAQ on isapnp and pnpdump see:
# [http://www.roestock.demon.co.uk/isapnptools/](http://www.roestock.demon.co.uk/isapnptools/)
# 
# Compiler flags:  -DREALTIME -DHAVE_PROC -DENABLE_PCI -DHAVE_SCHED_SETSCHEDULER -DHAVE_NANOSLEEP -DWANT_TO_VALIDATE
# 
# Trying port address 0273
# Board 1 has serial identifier 37 10 0c 29 d2 24 00 8c 0e

# (DEBUG)
(READPORT 0x0273)
(ISOLATE PRESERVE)
(IDENTIFY 
(VERBOSITY 2)
(CONFLICT (IO FATAL)(IRQ FATAL)(DMA FATAL)(MEM FATAL)) # or WARNING

# Card 1: (serial identifier 37 10 0c 29 d2 24 00 8c 0e)
# Vendor Id CTL0024, Serial Number 269232594, checksum 0x37.
# Version 1.0, Vendor version 1.0
# ANSI string -Creative SB16 PnP-
#
# Logical device id CTL0031
#     Device supports vendor reserved register @ 38
#     Device supports vendor reserved register @ 0x3f
#
# Edit the entries below to uncomment out the configuration required.
# Note that only the first value of any range is given, this may be changed if required
# Don't forget to uncomment the activate (ACT Y) when happy

(CONFIGURE CTL0024/269232594 (LD 0
#     ANSI string -->Audio<--

# Multiple choice time, choose one only !

#     Start dependent functions: priority preferred
#       IRQ 5.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)
#       First DMA channel 1.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 1))
#       Next DMA channel 5.
#             16 bit DMA only
#             Logical device is not a bus master
#             DMA may not execute in count by byte mode
#             DMA may execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 5))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0220
#             IO base alignment 1 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0330
#             Maximum IO base address 0x0330
#             IO base alignment 1 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0330))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0388
#             Maximum IO base address 0x0388
#             IO base alignment 1 bytes
#             Number of IO addresses required: 4
# (IO 2 (SIZE 4) (BASE 0x0388))

#       Start dependent functions: priority acceptable
#       IRQ 5, 7 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL )
#       Next DMA channel 5, 6 or 7.
#             16 bit DMA only
#             Logical device is not a bus master
#             DMA may not execute in count by byte mode
#             DMA may execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 5))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 48 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0388
#             Maximum IO base address 0x0388
#             IO base alignment 1 bytes
#             Number of IO addresses required: 4
# (IO 2 (SIZE 4) (BASE 0x0388))

#       Start dependent functions: priority acceptable
#       IRQ 5, 7 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Next DMA channel 5, 6 or 7.
#             16 bit DMA only
#             Logical device is not a bus master
#             DMA may not execute in count by byte mode
#             DMA may execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 5))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 48 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))

#       Start dependent functions: priority functional
#       IRQ 5, 7 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Next DMA channel 5, 6 or 7.
#             16 bit DMA only
#             Logical device is not a bus master
#             DMA may not execute in count by byte mode
#             DMA may execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 1 (CHANNEL 5))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))

#       Start dependent functions: priority functional
#       IRQ 5, 7 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 48 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0388
#             Maximum IO base address 0x0388
#             IO base alignment 1 bytes
#             Number of IO addresses required: 4
# (IO 2 (SIZE 4) (BASE 0x0388))

#       Start dependent functions: priority functional
#       IRQ 5, 7 or 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x0330
#             IO base alignment 48 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x0300))

#       Start dependent functions: priority functional
#       IRQ 5, 7, 10 or 11.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 5 (MODE +E)))
#       First DMA channel 0, 1 or 3.
#             8 bit DMA only
#             Logical device is not a bus master
#             DMA may execute in count by byte mode
#             DMA may not execute in count by word mode
#             DMA channel speed in compatible mode
# (DMA 0 (CHANNEL 0))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0220
#             Maximum IO base address 0x0280
#             IO base alignment 32 bytes
#             Number of IO addresses required: 16
# (IO 0 (SIZE 16) (BASE 0x0220))

#     End dependent functions
 (NAME "CTL0024/269232594[0]{Audio               }")
# (ACT Y)
))
#
# Logical device id CTL2011
#     Device supports vendor reserved register @ 0x38
#     Device supports vendor reserved register @ 0x3f
#
# Edit the entries below to uncomment out the configuration required.
# Note that only the first value of any range is given, this may be changed if required
# Don't forget to uncomment the activate (ACT Y) when happy

(CONFIGURE CTL0024/269232594 (LD 1
#     Compatible device id PNP0600
#     ANSI string -->IDE<--

# Multiple choice time, choose one only !

#     Start dependent functions: priority preferred
#       IRQ 10.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 10 (MODE +E)))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0168
#             Maximum IO base address 0x0168
#             IO base alignment 1 bytes
#             Number of IO addresses required: 8
# (IO 0 (SIZE 8) (BASE 0x0168))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x036e
#             Maximum IO base address 0x036e
#             IO base alignment 1 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x036e))

#       Start dependent functions: priority acceptable
#       IRQ 11.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 11 (MODE +E)))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x01e8
#             Maximum IO base address 0x01e8
#             IO base alignment 1 bytes
#             Number of IO addresses required: 8
# (IO 0 (SIZE 8) (BASE 0x01e8))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x03ee
#             Maximum IO base address 0x03ee
#             IO base alignment 1 bytes
#             Number of IO addresses required: 2
# (IO 1 (SIZE 2) (BASE 0x03ee))

#       Start dependent functions: priority acceptable
#       IRQ 10, 11 or 15.
#             High true, edge sensitive interrupt (by default)
# (INT 0 (IRQ 10 (MODE +E)))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0100
#             Maximum IO base address 0x01f8
#             IO base alignment 8 bytes
#             Number of IO addresses required: 8
# (IO 0 (SIZE 8) (BASE 0x0100))
#       Logical device decodes 16 bit IO address lines
#             Minimum IO base address 0x0300
#             Maximum IO base address 0x03fe
#             IO base alignment 2 bytes
#             Number of IO addresses required: 2

---

### Post by gmunioz on 2009-07-02
Hola ein....:

Estuve revisando y esos grupos de usuarios ya no existen mas.

Asi que el paso 5 olvídalo, es más voy a editarlo y dejarlo

como obsoleto.

Si agregaste el módulo en /etc/modules, teóricamente

ya estaría reconocida.

---

### Post by Einfachlacm on 2009-07-03
Gracias gabriel, ya tengo placa de sonido!

---

### Post by totolinux on 2009-08-05
Hola a todos acá sigo
yo con mi mediacenter
Tengo problemas con el
sonido es que la pc 
tiene una sb 16 isa
anteriormente en ubuntu 8.04
tenia que agregar el modulo
snd-sbawe a etc/modules creo.
y salia andando perooo.
en ubuntu 9.04 no puedo hacerlo 
(he visto varios threads y creo que varios 
la tienen clara con estas placas infernales) 
pd: 
   he agregado el susodicho módulo pero sigue sin funcionar. 
   con otros sistemas la placa funciona bien por ej: livecd de elive
   este problema lo tenía desde que salio ubuntu 8.10 y 9.04
   con 8.04 todo bién.

desde ya muchas gracias.

---

### Post by guillermolisi on 2009-08-05
[Aqui tenes lo que necesitas saber para solucionarlo]("http://ubuntuforums.org/showthread.php?t=1202024&highlight=isa").

Usen las funciones de busqueda del Foro ! :)

---

### Post by totolinux on 2009-08-05
Gracias mañana con la fresca pruebo  y comento saludos:D

---

### Post by guillermolisi on 2009-08-05
> **totolinux said:**
> Gracias mañana con la fresca pruebo  y comento saludos:D
De paso y por las dudas, en una terminal/consola ingresa "alsamixer" (sin las comillas) y revisa lo niveles de cada canal, inclusive que no esten silenciados.

---

### Post by totolinux on 2009-08-05
[QUOTE=gmunioz;7548265]Hola ein....:

En el caso de los dispositivos ISA, especificamente audio; como es tu 

tarjeta la deteccion automatica es desactivada para evitar problemas con

las interrupciones

1- Instala: isapnptool

2- Ejecuta:  sudo pnpdump>info

3- Ejecuta: sudo isapnp info

4. Ejecuta: sudo gedit /etc/modules

en realidad aquí es donde quedo, no puedo instalar el paquete  (1)
  el resultado es este:
diego@diego-desktop:~$ sudo apt-get install isapnptool
[sudo] password for diego:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete isapnptool

diego@diego-desktop:~$ sudo apt-get install isapnptools
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete isapnptools

y no se cual es el nombre correcto del paquete o tengo que agregar un repo. ya se que es básico pero se me complicó.:oops:
desde ya gracias

---

### Post by guillermolisi on 2009-08-05
Algo paso con ese paquete porque no esta en los repos de Jaunty ni en los de Debian.

El sitio del proyecto es [http://www.roestock.demon.co.uk/isapnptools/](http://www.roestock.demon.co.uk/isapnptools/) y hay distribucion fuente (compilar) y binarios en formato tar.gz.

Voy a indagar un poco mas al respecto.

Edit: Bueno, las alternativas son dos. Bajar, instalar y usar isapnptools desde el site que pase o cambiar la placa por una PCI. Confirmado con la lectura de algunos threads, como [este]("http://ubuntuforums.org/showthread.php?t=1229688&highlight=isapnptools") (en Ingles)

---

### Post by totolinux on 2009-08-06
Gracias de nuevo Guillermo he logrado hacer funcionar la placa baje el tar.gz de la pagina [http://www.roestock.demon.co.uk/isapnptools/](http://www.roestock.demon.co.uk/isapnptools/) 
es muy simple instalarlo luego alsamixer te deja el canal master por el piso lo levanté y funciona completo mi MEDIACENTER Saludos..

---

### Post by guillermolisi on 2009-08-06
> **totolinux said:**
> Gracias de nuevo Guillermo he logrado hacer funcionar la placa baje el tar.gz de la pagina [http://www.roestock.demon.co.uk/isapnptools/](http://www.roestock.demon.co.uk/isapnptools/) 
es muy simple instalarlo luego alsamixer te deja el canal master por el piso lo levanté y funciona completo mi MEDIACENTER Saludos..
Excelente, me alegra mucho que lo hayas logrado !

---

