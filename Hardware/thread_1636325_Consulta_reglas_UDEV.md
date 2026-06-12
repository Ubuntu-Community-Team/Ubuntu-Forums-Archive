---
title: "Consulta reglas UDEV"
date: 2010-12-02
forum: Hardware
---

### Post by wally88 on 2010-12-02
Hola gente, como andan?
Comento resumiendo que tengo ubuntu 10.10 x64 en una notebook acer, los drivers de synaptics para el touchpad no van como muchos deben saberlo ya, asi que me vi obligado a buscar una solucion sin usar los drivers de synaptics para desactivar el touchpad automaticamente cuando hay un mouse, cree el script para activar y desactivar y funciona perfecto pero tengo el problema de haber probado 1001 variantes de reglas UDEV para detectar la conexion y desconexion del mouse y no logro hacerla funcionar, probe desde las mas simples que vi en internet hasta las complejas modificando los valores correspondientes, tambien lei una guia sobre reglas UDEV y cree propias y no logro que lo detecte, por las dudas aclaro que la notebook es una Acer Aspire 5542-5241 con Ubuntu 10.10 x64 y por las dudas el mouse es un Genius NetScroll 310 USB
Por ahi alguien con mas experiencia pueda darme una mano con esto, es muy molesto tocar el touchpad sin querer cuando se esta escribiendo.

Saludos y gracias por adelantado!

La primer variante tomada de internet fue:
```

ACTION=="add", SUBSYSTEM=="input", ID_CLASS="mouse", RUN+="/usr/bin/desactivar.sh"

ACTION=="remove", SUBSYSTEM=="input", ID_CLASS="mouse", RUN+="/usr/bin/activar.sh"

```Mi ultimo intento fue:
```

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0458", ATTR{idProduct}=="003[0-9a]", RUN+="/usr/bin/desactivar.sh"

ACTION=="remove", SUBSYSTEM=="usb", ATTR{idVendor}=="0458", ATTR{idProduct}=="003[0-9a]", RUN+="/usr/bin/activar.sh"

```


EDITO: Segui intentando, me pudri del UDEV y hice con c++ mi propio daemon para detectar el mouse y ejecutar el script

---

