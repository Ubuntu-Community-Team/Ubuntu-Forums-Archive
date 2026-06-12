---
title: "No me funciona el escalado de frecuencia ni me detecta algunos sensores"
date: 2009-11-26
forum: Hardware
---

### Post by madbyte on 2009-11-26
Buenas,

Tengo una Asus P5W DH Deluxe y tengo algunos problemas para poder ver datos desde lm-sensors y no me funciona el escalado de frecuencia (Tengo XP y Windows 7 y en ambos el escalado funciona bien)

Este es el resultado de sudo sensors-detect:

[I]#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
f75375s
w83627ehf
coretemp
#----cut here----
[/I]
Puedo cargar todos los módulos menos el w83627ehf que me tira un error:

[I]FATAL: Error inserting w83627ehf (/lib/modules/2.6.31-15-generic/kernel/drivers/hwmon/w83627ehf.ko): Device or resource busy
[/I]
El applet Monitor de Frecuencia de CPU cuando lo cargo me tira:

**Escalado de frecuencia de la CPU no soportado**
*No podrá modificar la frecuencia de su máquina. Su máquina puede estar mal configurada o no tener soporte hardware para el escalado de frecuencia de la CPU.*

Alguna ayuda o sugerencia??

Muchas gracias

---

### Post by z37a on 2009-11-26
Por casualidad no tendrás un Celeron no?

---

### Post by guillermolisi on 2009-11-26
> **z37a said:**
> Por casualidad no tendrás un Celeron no?
Intel soporta escalado de frecuencia ? Me parece que no.

---

### Post by madbyte on 2009-11-26
Tengo un Intel Core 2 Duo E6400, y tiene soporte EIST, SpeedStep, desde el bios puedo seleccionar el factor de escalado entre 6 y 8 o dejar que lo haga el sistema operativo automaticamente, tanto en XP como en Windows 7 puedo ver como este factor cambia, modificando la frecuencia final de operación del cpu, tambien esto se observa en las temperaturas, en Windows tengo el cpu en unos 47/48 grados sin hacer nada, en cambio con Ubuntu, en la misma situación, el cpu se va a unos 60/61 grados, según los datos que me tira lm-sensors y como no puedo cargar el modulo *w83627ehf* no puedo ver que velocidades tienen los coolers.

Saludos

---

### Post by z37a on 2009-11-27
> **guillermolisi said:**
> Intel soporta escalado de frecuencia ? Me parece que no.


Si Intel soporta, el problema viene con los drivers mentirosos en Window$, en mi caso mi laptop usa un M520 el cual en Windows soporta escalado, pero en la realidad no posee escalado, y no hay forma de hacerlo andar.

En este caso el micro deberia andar bien, que Bus tiene esa placa madre? P5W no se bien que hipset es.

---

### Post by madbyte on 2009-11-27
El chipset de mi mb es Intel 975X, todavía no le encontre solución... sigo buscando... creo que cuando funcione el modulo que no puedo cargar va a salir andando el escalado

---

### Post by madbyte on 2009-12-03
Buenas, actualizo mi post:

Despues de andar buscando encontré que el problema esta en el driver para el ATK0110 ACPI que traen algunas Asus como la mia, me baje la ultima version de** lm-sensors 3.1.1** del sitio oficial y ahora me detecta todos los sensores de la mb como debe ser.

Sigo buscando solución para el escalado de frecuencia.

Saludos

---

