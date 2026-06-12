---
title: "Algo me consume MUCHA CPU!!"
date: 2011-11-24
forum: Hardware
---

### Post by pernoroca on 2011-11-24
Estimados, necesito su ayuda. Hace relativamente poco que uso Ubuntu y apenas si me la estoy empezando a arreglar. En este momento tengo instalado la 11.10 usando Unity. Tengo abiertas 4 ventanas de Chromium y el Monitor del sistema que me informa que el consumo de mis 2 nucleos (AMD Athlon 64 X2 Dual Core 5000+) varía constantemente entre 50% y 100%! Cuando me fijo los procesos me aparecen 3 ventanas de chromium consumiendo entre 2% y 20% c/u y el Monitor entre 30% y 50% además de otros 40 procesos durmiendo o zombies. Para que se den una idea, termino de teclear cada oración 1 segundo antes de que aparezca en la pantalla.
Espero que puedan tenderme una idea, porque yo no tengo demasiadas. Grax.

---

### Post by guillermolisi on 2011-11-25
Empecemos por el principio. Mostranos las salidas de ```
sudo lshw
``` ```
uname -a
``` y ```
lsmod
```
No deberias tener procesos zombies.
Deberias tener el sistema actualizado al dia.

---

