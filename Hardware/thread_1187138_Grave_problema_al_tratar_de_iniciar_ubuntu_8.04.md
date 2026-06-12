---
title: "Grave problema al tratar de iniciar ubuntu 8.04"
date: 2009-06-14
forum: Hardware
---

### Post by julicabrini on 2009-06-14
hola:
 
ayer un amigo me presto el cd original de ubuntu 8.04, hoy lo traté de instalar pero me encontre con esta falla que impide que inicie ubuntu. Lo que hice fué instalarlo dentro del mismo windows xp que tengo (puse el cd mientras windows corría y lo instale). Hasta ahi todo bien pero cuando reinicio y elijo iniciar con ubuntu me aparece este error:
 
MP-Bios bug: 8254 timer not connected to IO-APIC
 
 
Kernel panic- not syncing: IO-APIC + timer doesn't work! Boot with apic = debug and send a report. Then try booting with the 'noapic' option.
 
 
El mensaje está tal cual me aparece... si me pueden dar una solucion se los agradeceria muchisimo...

---

### Post by Hei Ku on 2009-06-14
Then try booting with the 'noapic' option. --> Esta es la solucion.

En el momento que te muestra el menu, apreta F6 para otras opciones, te va a mostrar cuatro lineas que son el comando de inicio del kernel. Movete a la segunda o tercera, es una que dice "splash quiet" al final. Apretas e, agregas noapic al final de todo, apretas Enter y la tecla b. Con eso debería iniciar.

Anda fijandote las instrucciones, porque yo te lo dije de memoria.

Recomendacion: Lee los mensajes de error que te aparezcan, porque tienen info importante. Y no te pongas nervioso, aunque sea tu primera vez. ;)

---

### Post by fmsismo on 2009-06-14
Fijate de probar la 9.04 de versión a versión mejora mucho el soporte de hardware.

Que estas tratando de instalar?  Un servidor o una notebook?

Saludos

---

### Post by julicabrini on 2009-06-14
> **Hei Ku said:**
> Then try booting with the 'noapic' option. --> Esta es la solucion.
 
En el momento que te muestra el menu, apreta F6 para otras opciones, te va a mostrar cuatro lineas que son el comando de inicio del kernel. Movete a la segunda o tercera, es una que dice "splash quiet" al final. Apretas e, agregas noapic al final de todo, apretas Enter y la tecla b. Con eso debería iniciar.
 
Anda fijandote las instrucciones, porque yo te lo dije de memoria.
 
Recomendacion: Lee los mensajes de error que te aparezcan, porque tienen info importante. Y no te pongas nervioso, aunque sea tu primera vez. ;)
 
muchas gracias lo voy a intentar.
 
Despues probe la version 9.04 pero me daba un error en la lectura del boot cd, por eso probe con la version 8.04...
 
Quiero instalar ubuntu en un servidor..
 
Muchas gracias

---

### Post by guillermolisi on 2009-06-14
> **julicabrini said:**
> muchas gracias lo voy a intentar.
 
Despues probe la version 9.04 pero me daba un error en la lectura del boot cd, por eso probe con la version 8.04...
 
Quiero instalar ubuntu en un servidor..
 
Muchas gracias
Si sera un servidor porque dara servicios (web, mail, etc.) mi recomendacion va por una instalacion de Ubuntu server. Si el servidor estara en produccion, eligiria la version 8.04 que es LTS, asi no te quedas sin soporte antes de lo esperado y podes prepararte para una actualizacion poco traumatica.

Luego esta el tema de si va o no va un escritorio grafico .... un tema completo en si mismo.

---

### Post by fmsismo on 2009-06-14
Que equipo es?  Que mother? Si es para un servidor te recomiendo el 8.04 lts.  Fijate de tener la última versión de la iso (8.04.2) probablemente lo tenga solucionado ese tema.  Igual no instalaste la versión servidor desde el windows.

Proba de pasarle durante el inicio noapic nolapic (si seguis con bardo agregale acpi=off).

Fijate de instalar desde el cd booteable para servidores (8.04 o 9.04 si seguís con problemas)

Saludos

---

### Post by julicabrini on 2009-06-15
Muchas gracias a todos, Ubuntu me anda perfecto!!!

---

