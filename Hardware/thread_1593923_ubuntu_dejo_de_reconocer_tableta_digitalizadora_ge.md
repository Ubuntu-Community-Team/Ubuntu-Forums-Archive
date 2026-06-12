---
title: "ubuntu dejo de reconocer tableta digitalizadora genius"
date: 2010-10-11
forum: Hardware
---

### Post by goldenfox on 2010-10-11
bueno tengo una tabla digitalizadora genius easyPen I405

la abia instalado en lucid y funcionaba. Pero actualice a maverick y dejo de funcionar :S
probé reinstalar los drivers pero sigue sin funcionar

pd: estoy usando el driver wizardpen y tengo ubuntu 10.10

---

### Post by sys.adm.og on 2010-10-12
Como realizaste tu actualización?

---

### Post by goldenfox on 2010-10-12
actualice como hise siempre 
alt+f2 y luego update-manager -d

---

### Post by maxmaster1990 on 2010-10-13
> **negora said:**
> Hello. I've been really busy for some time and have not been able to follow this thread (family matters).

I've found what seems to be a bug on Ubuntu 10.10, after installing the package xserver-xorg-input-wizardpen 0.7.4-2maverick0. The file /usr/lib/X11/xorg.conf.d/70-wizardpen.conf seems to be completely ignored by the X11 server. I've tried to copy it to /usr/share/X11/xorg.conf.d, together with the rest of the default X11 configuration files, and it works perfectly.

¡Encontré esto hace unas horas!
Hay que copiar este archivo >> **/usr/lib/X11/xorg.conf.d/70-wizardpen.conf**
en este directorio >> **/usr/share/X11/xorg.conf.d**
al lado de los otros archivos de configuración, reinicias y lista la sopa.
Lo que pasa es que hay un bug en 10.10 donde el xorg ignora el archivo, si lo metes allá te va a funcionar perfecto sin tener que haber cambiado nada, con la instalación del paquete xserver-**xorg-input-wizardpen** de DoctorMO normalito basta.
Para instalarlo, agrega este repositorio >> ppa:doctormo/xorg-wizardpen

Escribe en la terminal 
>> **sudo add-apt-repository ppa:doctormo/xorg-wizardpen **
luego
>> **sudo apt-get update**
por ultimo
>> **sudo apt-get install xserver-xorg-input-wizardpen** 

La solución de mover el archivo viene del usuario [**negora**]("http://ubuntuforums.org/member.php?u=561051") como cité arriba desde este **[post]("http://ubuntuforums.org/showthread.php?p=9960656")**
Corran la voz :P

---

### Post by goldenfox on 2010-10-13
muchas gracias hise lo que se decia en el post y funciona ahora

muchas gracias :D
marco el post como solucionado

---

