---
title: "Pantalla Hp dv6768se apagado raro"
date: 2009-04-19
forum: Hardware
---

### Post by .NicK_LoVe on 2009-04-19
Hola gente tengo una duda con el apagado, se pone toda blanca la pantalla y empieza a ponerse negra desde los costados hacia dentro.

La verdad me gustaría que se ponga negra de una, ya que no se si esto pudiera afectarla.

Saludos !!

---

### Post by juancarlospaco on 2009-04-21
Agrega a los Scripts de apagado *( /etc/RC(algo) )*

[B]#!/bin/bash
xset dpms force off[/B]

---

### Post by .NicK_LoVe on 2009-04-30
No entiendo como se hace eso :(

---

### Post by .NicK_LoVe on 2009-05-05
Alguien que me guíe un poquito ???? :confused:

---

### Post by juancarlospaco on 2009-05-05
[B]ALT + F2

gksudo gedit /etc/default/halt

xset dpms force off

Agregar eso al final de ese archivo de configuracion, Guardar, Cerrar, reiniciar.[/B]

[I]Apagar de nuevo, deberia apagarse el monitor de una con ese comando extra, 
tambien podes ejecutarlo manualmente, sin sudo, es inofensivo.[/I]

---

### Post by .NicK_LoVe on 2009-05-10
juancarlospaco, hice lo que me dijiste pero sigue haciendo lo mismo...

---

### Post by Mauro22 on 2009-05-10
Hace un script para apagar asi, a ver que onda.


Abri un documento nuevo y pone:

```
#!/bin/bash


xset dpms force off
gnome-power-cmd shutdown
```



Guardalo, y dale permiso de ejecuccion:

* Clic derecho, propiedades, Permisos, "Permitir ejecutar...."

* O desde la consola con: 

```
chmod +x archivo
```



Dale doble click y ejecutalo, deberia apagarse la pantalla primero y luego la pc.



PD: Usas Gnome, no?

---

### Post by .NicK_LoVe on 2009-05-11
Mauro22, probé eso y tampoco...

Si tengo gnome.

Saludos

---

### Post by .NicK_LoVe on 2009-05-15
ayuda!!!8-[

---

