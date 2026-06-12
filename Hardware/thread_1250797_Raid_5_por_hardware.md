---
title: "Raid 5 por hardware"
date: 2009-08-26
forum: Hardware
---

### Post by sistemmas on 2009-08-26
Buenas gente, estoy tratando de instalar ubuntu en raid 5 por hardware.:P
Los 3 discos SATAll ya están configurados en una controladora intel ICH10R, integrada en un mother msi platimun p45.
Cuando llego al paso de seleccion de disco en donde quiero instalar el SO me muestra los 3 discos y no me los toma como 1 solo.
Elijo el 1ero, comienza la instalacion normalmente pero cuando termina y al reiniciar me tira "ERROR 2".
Busque por varios foros pero no hay mucha info de raid 5 por hard en ubuntu...:confused:
Si alguien hizo algo parecido o me puede guiar se lo agradecere.
tnks!

---

### Post by guillermolisi on 2009-08-27
> **sistemmas said:**
> Buenas gente, estoy tratando de instalar ubuntu en raid 5 por hardware.:P
Los 3 discos SATAll ya están configurados en una controladora intel ICH10R, integrada en un mother msi platimun p45.
Cuando llego al paso de seleccion de disco en donde quiero instalar el SO me muestra los 3 discos y no me los toma como 1 solo.
Elijo el 1ero, comienza la instalacion normalmente pero cuando termina y al reiniciar me tira "ERROR 2".
Busque por varios foros pero no hay mucha info de raid 5 por hard en ubuntu...:confused:
Si alguien hizo algo parecido o me puede guiar se lo agradecere.
tnks!
Si esa controladora es hibrida, o sea que realiza un fake RAID, nunca te va a funcionar tal como queres salvo que encuentres, cosas bastante dificil porque Intel hace rato que no actualiza, el driver correcto para esa placa y para el kernel que estas utilizando.

Si aun queres insistir con RAID o pones hardware "inteligente" (RAID por hardware, que sale sus pesos) o haces RAID por software pero perdes la posibilidad del Hot Swap, en caso que los discos sean de esa caracteristica.

---

### Post by z37a on 2009-08-29
Te confirmo parte de lo que dijo Guillermo, esa controladora es FakeRAID, o sea, no hace raid, simplemente el driver de windows toma como si ubiese un RAID, pero en realidad el raid lo esta realizando un software. En linux esto tambien podes hacerlo, en el caso de Ubuntu, necesitas un Alternate o Ubuntu Server, en la parte de las patrticiones debes crear una particion entera para cada disco que sea "LINUX RAID" y luego te desplegara la opcion de RAID, alli seleccionas las 3 particiones y que se usen en RAID5 y listo. El unico incoveniente es que estarias haciendo RAID sobre particiones, y una vez armado el raid te da una particion y no un dispositivo entero para particionar, asi que te recomiendo armar en cada disco el particionado en formato RAID y luego armar los diferentes RAID deacurdo a lo que quieras.

PD: Las controladoras RAID5 por Hard salen fortuna, hablamos de mas de 200 dolares(Algunas superan los mil), NINGUNA placa con controladora Onboard trae RAID por Hardware. Aparte de esto estas controladoras enserio traen baterias para evitar perdidas de datos y su propio procesador, para evitar utilizar al CPU en la tarea de realizar el RAID.

---

