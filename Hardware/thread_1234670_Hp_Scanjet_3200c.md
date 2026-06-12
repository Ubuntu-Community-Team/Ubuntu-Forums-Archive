---
title: "Hp Scanjet 3200c"
date: 2009-08-08
forum: Hardware
---

### Post by NickCis on 2009-08-08
Hola, despues de un poco de google, encontre como hacer andar este escanner, edite el archivo /etc/sane.d/dll.conf  comentando todo menos umax_pp. Y dsp en el archivo /etc/sane.d/umax_pp.conf y cambie lo que decia de port por port auto. (Editar el fichero /etc/sane.d/dll.conf y comentamos TODOS los módulos, excepto el umax_pp. ( Fuente [http://crysol.org/en/node/926](http://crysol.org/en/node/926) )
Probe si me reconocia el scanner: 
```
newpc@newpc-desktop:/usr/local/etc$ sudo scanimage -L
device `umax_pp:/dev/parport0' is a UMAX Astra 2000P flatbed scanner

```

El problema es que al ejecutar el xsane en consola, no me reconoce ningun scanner. Para que me reconosca el scanner tengo que ejecutar el xsane con privilegios de root, como podria solucionar esto?.

Saludos.

---

### Post by Hei Ku on 2009-08-08
Puede ser que tu usuario no tenga permisos para el puerto donde esta el scanner.
O quizas tenga que estar en el grupo scanner.

---

### Post by NickCis on 2009-08-09
> **Hei Ku said:**
> Puede ser que tu usuario no tenga permisos para el puerto donde esta el scanner.
O quizas tenga que estar en el grupo scanner.

Ahh,,, y como reviso eso en Kubuntu 9.04? =S...

Saludos y gracias

---

### Post by guillermolisi on 2009-08-09
El tema users/groups lo revisas con Kuser (System - Kuser).

---

### Post by NickCis on 2009-08-11
No encontre el grupo "scanner", lo tengo qe crear?. 
Lo unico q encontre fue un grupo llamado saned, pense que tenia algo qe ver con lo del escaner por lo de sane, pero al agregar a mi usuario al grupo, sigo sin poder usar el scanner.

Alguna idea?.

Saludos.

---

### Post by NickCis on 2009-08-13
Alguna idea?

---

### Post by Hei Ku on 2009-08-13
Este thread parece similar a lo que te pasa a vos:
[http://ubuntuforums.org/showthread.php?t=166944](http://ubuntuforums.org/showthread.php?t=166944)

---

### Post by NickCis on 2009-08-15
Entendi como es el proceso, pero no se a que le tengo qe cambiar los permisos, mi scanner es por puerto serial, no por usb como esta el ejemplo de ahi...

Please help xD...

Saludos, y gracias =P

---

### Post by Hei Ku on 2009-08-15
/dev/parport0 es el port del scanner

---

### Post by guillermolisi on 2009-08-15
> **Hei Ku said:**
> /dev/parport0 es el port del scanner
Ese no es el port paralelo ?

No deberia se /dev/stty o algo similar ? (ahora me doy cuenta que hace muuuucho tiempo que no uso un puerto serial)

---

### Post by Hei Ku on 2009-08-15
sip, pero es lo que le aparece.

device `umax_pp:/dev/parport0' is a UMAX Astra 2000P flatbed scanner

---

### Post by guillermolisi on 2009-08-15
> **Hei Ku said:**
> sip, pero es lo que le aparece.

device `umax_pp:/dev/parport0' is a UMAX Astra 2000P flatbed scanner
Entonces es parallel not serial (conector Centronics de algo de 40 pines)

---

### Post by matutetandil on 2010-05-24
Hola... hay que cambiar los permisos del parport0
sudo chmod a+w /dev/parport0
sudo chmod a+r /dev/parport0

y listo!!!! sale andando!!!!
Ha... para los que sigan sin detectar el scaner, despues de hacer las modificaciones en los dos archivos, asegurense de que en la BIOS, el puerto paralelo esta configurado como EPP

---

