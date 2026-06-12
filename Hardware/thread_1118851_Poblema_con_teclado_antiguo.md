---
title: "Poblema con teclado antiguo"
date: 2009-04-07
forum: Hardware
---

### Post by ramiro_md on 2009-04-07
Gente reaparezco por estos lados solicitando su ayuda. Resulta que estoy intentando reciclar mi Pentium II 333 MHz, pero el eclado no me funciona. Es decir, cuando intento entrar al setup para configurar el orden de booteo y los discos, por más que aprete la tecla supr/del como un desquiciado no hay caso, la computadora sigue en el proceso de arranque y se queda en "WAIT...".
Aclaro que probé con 5 teclados, y ya dudo que los 5 estén rotos. QUé podrá ser ?
UN saludo y gracias.

---

### Post by guillermolisi on 2009-04-07
> **ramiro_md said:**
> Gente reaparezco por estos lados solicitando su ayuda. Resulta que estoy intentando reciclar mi Pentium II 333 MHz, pero el eclado no me funciona. Es decir, cuando intento entrar al setup para configurar el orden de booteo y los discos, por más que aprete la tecla supr/del como un desquiciado no hay caso, la computadora sigue en el proceso de arranque y se queda en "WAIT...".
Aclaro que probé con 5 teclados, y ya dudo que los 5 estén rotos. QUé podrá ser ?
UN saludo y gracias.

Por casualidad, revisaste la motherboard para ver si tiene electroliticos hinchados o directamente explotados y secos ?

Es una Soyo de la serie 6BA o BA+ ?

Estaba funcionando bien toda la maquina ?
Cuanto hace que no se utiliza ?

---

### Post by ramiro_md on 2009-04-07
> **guillermolisi said:**
> Por casualidad, revisaste la motherboard para ver si tiene electroliticos hinchados o directamente explotados y secos ?

Es una Soyo de la serie 6BA o BA+ ?

Estaba funcionando bien toda la maquina ?
Cuanto hace que no se utiliza ?

La maquina en si hace unos 4 ó 5 meses que estaba parada. La mother ni idea la marca, pero después me fijo. EL sabado la probé y andaba todo (el teclado inclusive).

---

### Post by infernus92 on 2009-04-07
una forma facil de ver si el problema es del teclado que no ande es probarlo en otra computadora... y tmb fijate si cuando inicias la petium II de la que hablas prende las luces de num lock, caps lock y scroll lock (proba tocando las correspondientes teclas tambien) si no las prende creeria que el problema es mas serio que cambiar de teclado

saludos

---

### Post by ramiro_md on 2009-04-07
> **infernus92 said:**
> una forma facil de ver si el problema es del teclado que no ande es probarlo en otra computadora... y tmb fijate si cuando inicias la petium II de la que hablas prende las luces de num lock, caps lock y scroll lock (proba tocando las correspondientes teclas tambien) si no las prende creeria que el problema es mas serio que cambiar de teclado

saludos

Si, las luces prenden al iniciar, pero cuando se queda el WAIT.. en la pantalla...por mas que toques numbloq, bloqmayus y demás no prenden más.

---

### Post by ramiro_md on 2009-04-07
Acabo de descartar la piosibilidad del teclado. Debe ser algun conflicto con los discos.
Resulta que tiene un lector de dvd y un disco de 6 gb, al desconectar ambos la maquina "vuelve a la vida"y me deja entrar al bios.
El tema que problema de jumpers nocreo que sean, porque no tiene ninguno de los perifericos.
Espero que con este "avanze" me ayuden a roslver este tema.
Un saludo y gracias.

---

### Post by Hernán-Amaya on 2009-04-07
Como tenés conectado el disco y el lector sobre un mismo cable ide? igual fijate los jumpers. Otra cosa proba solo con el disco rígido para ver si anda.

---

### Post by guillermolisi on 2009-04-07
> **ramiro_md said:**
> Acabo de descartar la piosibilidad del teclado. Debe ser algun conflicto con los discos.
Resulta que tiene un lector de dvd y un disco de 6 gb, al desconectar ambos la maquina "vuelve a la vida"y me deja entrar al bios.
El tema que problema de jumpers nocreo que sean, porque no tiene ninguno de los perifericos.
Espero que con este "avanze" me ayuden a roslver este tema.
Un saludo y gracias.
Como que no tienen jumpers ?

Depende como los conectes a los canales IDE de la motherboard debera ser la ubicacion del jumper en cada unidad para que el sistema los reconozca como Master, Slave o, llegado el caso, CableSelect.

Ademas de eso tenes cables de 40 hilos y cables de 80 hilos. Esto no es algo menor ya que con 80 hilos logras que la unidad te rinda al maximo de sus posibilidades (UDMA33, UDMA66, UDMA100, etc.)

---

### Post by ramiro_md on 2009-04-07
Problema resuelto, eran lso cables ides :|. Los cambié y salió andando todo 10 puntos.
Gracias por la ayuda, en cuanto tenga otra consulta no dudo en volver a recurri al foro je.

---

