---
title: "Problemas con la panatalla"
date: 2008-12-13
forum: Hardware
---

### Post by ghertzan on 2008-12-13
Hola!
Como va? acabo de instalar intrepid32,(Athlon 64 x2 -2gb RAM - Gforce 7300 GS) y cuando muevo ventanas o veo videos, se ve como un refresco de la pantalla, molesto, que no lo hacia en 8.04 y no lo hace en vista. estoy usando nvidia-settings para configurar la resolucion.
En todas las resoluciones me hace lo mismo...
Me anda bien mejor que hardy, pero el refreco ese me molesta mucho.
Me podran dar una mano con esto?

Gracias!!!

---

### Post by Hei Ku on 2008-12-13
Que version del driver estas usando?

---

### Post by ghertzan on 2008-12-14
Calculo que la ultima, lo upgradee desde el terminal.
de que otra forma puedo conseguirlos.... Soy medio nuevo en esto...

Gracias.

---

### Post by faktorqm on 2008-12-14
Pero instalaste los drivers de nvidia o nunca instalaste nada? Desde controladores restringidos? Si no lo hiciste desde ahi, Ubuntu te pone unos compatibles pero sin aceleracion 3d, por eso ves que cuando moves una ventana se "traba". Fijate de instalarlos con el envy que te hace todo automatico (si no los instalaste ya...):

```
sudo apt-get install envyng-gtk envyng-core
```

Salu2!!!

---

### Post by ghertzan on 2008-12-14
Puse los contoladores privativos... Viste cuando recien instalas te aparece el cartelito....
Y despues el nvidia-settings...
vos que me decis que haga ... desinstale los privativos y pruebe con envy??

---

### Post by faktorqm on 2008-12-15
No, esta bien, son esos los que van, envy te instala los mismos en definitiva. Fijate de hacer 

```
sudo displayconfig-gtk
```

y elegir el modelo de monitor y resolucion y tasa de refresco apropiados. Quiza tengas mal eso. Salu2!

---

