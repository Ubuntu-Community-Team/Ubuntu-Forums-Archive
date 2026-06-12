---
title: "[SOLUCIONADO]Actualizaciones de ubuntu 9.04"
date: 2009-08-20
forum: Instalación y Actualización
---

### Post by delarge on 2009-08-20
Caballeros, que tal ?

Mi consulta es precisa: 

Al menos 4 veces por semana el "gestor de actualizaciones" aparece diciendo que hay nuevas actualizaciones de 35 MB aprox, siempre las instalo pero me pregunto lo siguiente: ¿cada cuanto hay nuevos updates?¿que pasa si no los instalo? porque si sigo instalando todo lo que sugiere ubuntu me quedaré sin disco duro en 1 mes.

Saludos y de ante mano gracias.

---

### Post by bichopro on 2009-08-20
Pudes vaciar el cache de actualizaciones:

Limpiando la memoria cache de aptitude

Cuando instalamos programas desde los repositorios, lo primero que hace es bajar los instaladores para luego instalarlos. Pero después de instalarlos, estos archivos se quedan en el ordenador. Estos ficheros se pueden borrar ya que si se necesitan otra vez los bajará de nuevo.  Para borrar estos ficheros tendremos que ejecutar la siguiente orden:

> sudo aptitude clean

---

### Post by Carlos C on 2009-08-21
¿De qué tamaño es tu partición "/"? Porque mi sistema nunca ha ocupado más de 4,5 Gb.

---

### Post by asterix77 on 2009-08-26
En todo caso al actualizar un determinado paquete he observado que el anterior es desinstalado, por lo que me imagino que libera un espacio, pero es ocupado nuevamente por la nueva versión. ¿o me equivoco?. No creo que los nuevos paquetes sean excesivamente más grande que el anterior.

Lo mejor es hacer lo que propone bichopro.

Saludos

---

### Post by mruiz on 2009-08-28
> **delarge said:**
> Caballeros, que tal ?

Mi consulta es precisa: 

Al menos 4 veces por semana el "gestor de actualizaciones" aparece diciendo que hay nuevas actualizaciones de 35 MB aprox, siempre las instalo pero me pregunto lo siguiente: ¿cada cuanto hay nuevos updates?¿que pasa si no los instalo? porque si sigo instalando todo lo que sugiere ubuntu me quedaré sin disco duro en 1 mes.

Saludos y de ante mano gracias.

Los updates generalmente obedecen a mejoras en las aplicaciones, parches de seguridad y otros. Por lo anterior, es difícil decir cuando y cuántas actualizaciones tendrá un paquete durante un ciclo de desarrollo.

Siempre se recomienda instalar los updates, ya que contarás con un sistema más robusto y mejor. Si no consideras las actualizaciones puedes correr un riesgo, que se aproveche alguna vulnerabilidad o que algún programa no funcione como corresponda.

Como la solución está a mano, es decisión tuya si la tomas o no ...

Saludos!

---

### Post by jorval on 2009-08-28
Estimado Delarge: Te aconsejo que te guíes por la respuesta de don MRuiz. Las actualizaciones son necesarias por lo que él explica. No te preocupes por tu disco duro, yo, que tengo Ubuntu 8.04 y bajo todas las actualizaciones que aparecen recién mi SO ha ocupado 3.06 GB (tengo /home separado). Saludos.

---

### Post by moreback on 2009-08-30
Las actualizaciones **reemplazan** los paquetes que ya tienes instalados, por lo que tu apreciación de que se te va a acabar el disco duro luego es errónea.

Saludos.

---

### Post by moreback on 2009-08-30
Las actualizaciones **reemplazan** los paquetes que ya tienes instalados, por lo que tu apreciación de que se te va a acabar el disco duro luego es errónea.

Saludos.

---

### Post by delarge on 2009-09-03
se agradece señores.Todo  claro entonces  :D

---

### Post by AlexDDR on 2009-09-06
De todas formas en SISTEMA-->ADMINISTRACION-->>Origenes de software, en la pesataña actualizaciones
  puesde variar el tiempo que se avisan las actualizaciones , en diariamente, dos dias, una semana y dos semanas, asi ya no serán tan molestosas, pero en todo caso algunas ves yo mismo me meto a synaptic y aprieto recargar para asegurarme de que no queda nada por actualizar, y algunas veces quedan algunos paquetes no considerados

saludos

---

