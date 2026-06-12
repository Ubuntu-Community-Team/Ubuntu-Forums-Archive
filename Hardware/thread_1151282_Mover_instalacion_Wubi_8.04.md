---
title: "Mover instalacion Wubi 8.04"
date: 2009-05-06
forum: Hardware
---

### Post by Jorgel on 2009-05-06
Saludos a tod@s desde Puerto Rico. 

Actualmente estoy utilizando Wubi 8.04 en mi Laptop (Toshiba Satellite A-105) en "dual boot" con XP . La instalacion esta hecha en un disco duro externo USB SimpleTech. El disco duro interno de la computadora tiene una particion vacia de 50 GB's a la cual quisiera mover la instalacion de Wubi 8.04 (Ubuntu) ya que quisiera liberar el espacio de almcenaje del disco externo ademas de que es mas comodo no tener que conectar el disco externo para poder utilizar Ubuntu.

Cada dia me encuentro utilizando mas Linux, pero todavia soy muy novato en cuanto a el aspecto de programacion y comandos. Podria alguiuen ayudarme con esta situacion? Muchas gracias.

Jorge

---

### Post by staar on 2009-05-06
mover la instalación que tenés con wubi, no creo que se pueda...

lo que podés hacer es un respaldo del contenido (incluidos archivos ocultos) de tu /home, instalar ubuntu en la partición que tenés vacia, y luego copiar el respaldo en la nueva instalación, con esto conservarías las configuraciones de tus programas, no así los programas en si, que tendrías que volver a instalar...

un consejo, ya que sos nuevo y vas a instalar, para ahorrarte problemas con el particionado, te recomiendo que directamente borres la partición que tenés, y dejes el espacio libre sin particionar en el disco, luego en el instalador seleccioná 'usar espacio libre' para que ubuntu cree las particiones necesarias alli...

saludos

---

### Post by Jorgel on 2009-05-07
Gracias por tu respuesta **staar** intentare tu sugerencia y os dejare saber los resultados.

---

### Post by guillermolisi on 2009-05-07
> **Jorgel said:**
> Gracias por tu respuesta **staar** intentare tu sugerencia y os dejare saber los resultados.
Si no interpreto mal lo que comenta staar, lo que te esta sugiriendo es para hacer una instalacion de Ubuntu que coexiste con Windows en el mismo disco rigido, distinta particion, y que se conoce como "dual boot" ya que al iniciar te aparecera un menu con la opcion de seleccionar iniciar con Win o con Ubuntu.

Esto no es Wubi sino una instalacion completa en su propia particion. Wubi logra que ubuntu "este dentro" de Windows, sin particionar, como si "fuera" una aplicacion Windows mas.

Es esto lo que estas buscando ? (el dual boot ?)

---

### Post by Jorgel on 2009-05-07
Entendi lo mismo. Si tengo que mencionar que la particion que existe vacia en el disco duro de la computadora fue en un momento una instalacion "dual boot" de Ubuntu, pero por alguna razon, esa instalacion daba problemas y tube diferentes situaciones con el 
"hardware" entre ellas situaciones con el sonido y video.

La unica manera que he podido utilizar sin problemas Ubuntu ha sido con Wubi. Es por esto que pensaba solo mover los archivos de Wubi.Podria intentar nuevamente la instalacion completa,. :confused:

Gracias.

---

### Post by staar on 2009-05-08
si tuviste problemas con versiones anteriores, te recomiendo que pruebes el livecd de la última versión de ubuntu, 9.04 jaunty jackalope, el soporte para laptops a mejorado muchisimo en estas últimas versiones, y, si te anda bien, la instales en dual boot...

por lo que pude googlear, los problemas con tu modelo de laptop eran en versiones de hardy para atrás, y en intrepid (y jaunty) aparentemente fueron solucionados, asi que es probable que no tengas problemas...

saludos

---

### Post by infernus92 on 2009-05-08
de paso que vas a instalar sistema, te recomendaria que actualices a JJ o a II por lo menos, traen muchas cosas nuevas muy interesantes... pero no se si crearia conflictos con el /home viejo

Saludos

---

### Post by Jorgel on 2009-05-08
Gracias a tod@s. Me estoy inclinando mas por hacer la nueva instalacion como me han recomendado. La verdad es que no tengo tanta informacion en mi /home como para no hacer una instalacion nueva.

He leido varios problemas con JJ al momento, creen que seria riesgoso tratar de instalarlo ahora y que deberia esperar un poco mas o puedo tomar el riesgo y hacerlo desde ahora?

Gracias nuevamente, por lo menos se que si tengo algun problema puedo contar con uds.

Jorge

---

### Post by guillermolisi on 2009-05-08
> **Jorgel said:**
> Gracias a tod@s. Me estoy inclinando mas por hacer la nueva instalacion como me han recomendado. La verdad es que no tengo tanta informacion en mi /home como para no hacer una instalacion nueva.

He leido varios problemas con JJ al momento, creen que seria riesgoso tratar de instalarlo ahora y que deberia esperar un poco mas o puedo tomar el riesgo y hacerlo desde ahora?

Gracias nuevamente, por lo menos se que si tengo algun problema puedo contar con uds.

Jorge
Depende de para que vas a usar la maquina con Ubuntu.

Si es para interiorizarte y acostumbrarte a el, dale derecho JJ y de paso vas viendo como se resuelven algunos problemas.

Si la usas para laburar, tal vez convendria que instales II que esta mas probado, igual de bueno (sobre todo para note/netbooks) y una vez que el nivel de bugs en JJ se haya reducido, actualizas de version y listo.

---

### Post by Jorgel on 2009-05-08
He bajado JJ :D 

Ahora trato de correr en "Livecd" pero luego de elegir el idoma y escoger la funcion de utilizar sin hacer cambios al sistema se cuelga y no procede :confused:

---

### Post by guillermolisi on 2009-05-09
> **Jorgel said:**
> He bajado JJ :D 

Ahora trato de correr en "Livecd" pero luego de elegir el idoma y escoger la funcion de utilizar sin hacer cambios al sistema se cuelga y no procede :confused:
Esa maquina tiene video ATI, cierto ?

Proba iniciando desde el CD seleccionando con F6 (creo que era esa la que habla de Video modes/options) y elegi VGA o modo seguro (se nota que hace mucho no uso el LiveCD ?)

Proba y conta como te fue.

---

### Post by Jorgel on 2009-05-09
Gracias nuevamente Guillermo y los demas que me han asistido. Lo que termine haciendo fue instalar 8.10 y estoy super contento. Nuevamente les agradezco su ayuda.

En este momento estoy actualizando la instalacion y utilizare 8.10 por un tiempo, ya luego hare la actualizacion a 9.04 cuando se estabilize mas.

---

