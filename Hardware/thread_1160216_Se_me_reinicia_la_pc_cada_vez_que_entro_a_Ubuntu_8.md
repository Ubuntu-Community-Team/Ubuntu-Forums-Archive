---
title: "Se me reinicia la pc cada vez que entro a Ubuntu 8.10"
date: 2009-05-15
forum: Hardware
---

### Post by driftking20 on 2009-05-15
Hola gente

soy nuevo aca, vine por un problema grosso que tengo cada vez que entro a ubuntu 8.10 y que me obliga usar windows xp:lolflag:

Resulta que cada vez que entro a ubuntu anda todo perfecto, pero por ahi se queda trabado todo y se reinicia la maquina....

nose que puede ser, mi maquina es :

micro : Tipo de procesador    AMD Sempron LE-1150, 2000 MHz (10 x 200)
mother: Nombre de la Placa Base    Biostar MCP6P-M2  (2 PCI, 1 PCI-E x16, 2 DDR2 DIMM, Audio, Video, LAN)
Placa de video: Tarjeta gráfica    NVIDIA GeForce 6150SE nForce 430  (512 MB)
Placa de sonido: Tarjeta de sonido    Realtek ALC662 @ nVIDIA MCP61 - High Definition Audio Controller
Disco duro: Disco duro    ST380011A  (80 GB, 7200 RPM, Ultra-ATA/100)
Lan: Tarjeta de Red    NVIDIA nForce Networking Controller  (10.0.0.3)

nose si tenga algo que ver con el hadware o alguna mala configuracion jejej

por favor ayudenme :lolflag:

saludos

---

### Post by guillermolisi on 2009-05-15
> **driftking20 said:**
> Hola gente

soy nuevo aca, vine por un problema grosso que tengo cada vez que entro a ubuntu 8.10 y que me obliga usar windows xp:lolflag:

Resulta que cada vez que entro a ubuntu anda todo perfecto, pero por ahi se queda trabado todo y se reinicia la maquina....

nose que puede ser, mi maquina es :

micro : Tipo de procesador    AMD Sempron LE-1150, 2000 MHz (10 x 200)
mother: Nombre de la Placa Base    Biostar MCP6P-M2  (2 PCI, 1 PCI-E x16, 2 DDR2 DIMM, Audio, Video, LAN)
Placa de video: Tarjeta gráfica    NVIDIA GeForce 6150SE nForce 430  (512 MB)
Placa de sonido: Tarjeta de sonido    Realtek ALC662 @ nVIDIA MCP61 - High Definition Audio Controller
Disco duro: Disco duro    ST380011A  (80 GB, 7200 RPM, Ultra-ATA/100)
Lan: Tarjeta de Red    NVIDIA nForce Networking Controller  (10.0.0.3)

nose si tenga algo que ver con el hadware o alguna mala configuracion jejej

por favor ayudenme :lolflag:

saludos
Con Windows nunca te pasa eso ?

---

### Post by driftking20 on 2009-05-15
> **guillermolisi said:**
> Con Windows nunca te pasa eso ?

no, windwos anda pefercto jeje

---

### Post by emiliano_raso on 2009-05-15
> **driftking20 said:**
> no, windwos anda pefercto jeje

Se te queda toda la maquina dura como si estuvieras viendo un screenshot, no? xD
A mi me pasaba lo mismo cuando abría un video en Hardy Heron o emulo con Wine el "MU ONLINE" en las ultimas dos versiones?

Primero que nada, probá si te pasa en otros entornos graficos, instalate lxde:
```
sudo aptitude install lxde
```
Iniciá sesion en ese entorno y fijate si se te traba de nuevo.

Si te sigue pasando entonces ya se cual es la solucion.

---

### Post by guillermolisi on 2009-05-15
> **emiliano_raso said:**
> Se te queda toda la maquina dura como si estuvieras viendo un screenshot, no? xD
A mi me pasaba lo mismo cuando abría un video en Hardy Heron o emulo con Wine el "MU ONLINE" en las ultimas dos versiones?

Primero que nada, probá si te pasa en otros entornos graficos, instalate lxde:
```
sudo aptitude install lxde
```Iniciá sesion en ese entorno y fijate si se te traba de nuevo.

Si te sigue pasando entonces ya se cual es la solucion.
Y por que no se la decis ahora o al menos explicas sus fundamentos ?

Si despues no quiere seguir con LXDE, como deberia hacer para volver a como tiene la maquina hoy (sin necesidad de abrir otro thread o buscar en el foro o con Google) ?

Solo sugerencias como para que el interesado despues no se vea contrariado por seguir consejos sin saber de antemano algunas consecuencias y el que sugiere con animo de ayudar no quede mal parado.

---

### Post by emiliano_raso on 2009-05-15
> **guillermolisi said:**
> Y por que no se la decis ahora o al menos explicas sus fundamentos ?

Si despues no quiere seguir con LXDE, como deberia hacer para volver a como tiene la maquina hoy (sin necesidad de abrir otro thread o buscar en el foro o con Google) ?

Solo sugerencias como para que el interesado despues no se vea contrariado por seguir consejos sin saber de antemano algunas consecuencias y el que sugiere con animo de ayudar no quede mal parado.

Jajaja xD Tenes razon.. el problema es que... NO ME ACUERDO LA SOLUCION XD
La tiene un amigo xD Y no está conectado, por eso hasta que el me responda, mi amigo seguro se conecta y me da la solucion xD
Sin embargo, si quiere volver simplemente elige Gnome en el login y listo :-S

---

### Post by guillermolisi on 2009-05-15
> **emiliano_raso said:**
> Jajaja xD Tenes razon.. el problema es que... NO ME ACUERDO LA SOLUCION XD
La tiene un amigo xD Y no está conectado, por eso hasta que el me responda, mi amigo seguro se conecta y me da la solucion xD
Sin embargo, si quiere volver simplemente elige Gnome en el login y listo :-S
Ok. Pero entonces que la sugerencia no sea tan "liviana" porque tal vez pudiste resolver alguna situacion inesperada pero no sabes si el que te esta leyendo reune esas mismas condiciones y, queriendo ayudar, se empeora.

---

### Post by emiliano_raso on 2009-05-15
> **guillermolisi said:**
> Ok. Pero entonces que la sugerencia no sea tan "liviana" porque tal vez pudiste resolver alguna situacion inesperada pero no sabes si el que te esta leyendo reune esas mismas condiciones y, queriendo ayudar, se empeora.

Ok. Entonces mi solucion no sirve, porque lo que había hecho fue instalar varias librerias de distintas cosas relacionadas con el video hasta que funcionó.
Asi que, teniendo en cuenta que el instalar lxde para despues no usarlo puede generar un problema para alguien, entonces instalar librerias al pepe puede resultar peor.

A mi no me generó ningun problema, pero es cierto que a otro le puede afectar.
Sea como sea, es la unica solucion que le encontré a ese problema. Me revolví la interne' entera y no encontre nada mas.

---

### Post by driftking20 on 2009-05-16
> **emiliano_raso said:**
> Se te queda toda la maquina dura como si estuvieras viendo un screenshot, no? xD
A mi me pasaba lo mismo cuando abría un video en Hardy Heron o emulo con Wine el "MU ONLINE" en las ultimas dos versiones?

Primero que nada, probá si te pasa en otros entornos graficos, instalate lxde:
```
sudo aptitude install lxde
```Iniciá sesion en ese entorno y fijate si se te traba de nuevo.

Si te sigue pasando entonces ya se cual es la solucion.

intente con ese comando, y me sale error en del dkpg o algo asi   :p y cuando reincie, se reinicia directamente al pc.... no sera, que esta version de ubuntu no es compatible con la pc?

---

### Post by guillermolisi on 2009-05-16
> **driftking20 said:**
> intente con ese comando, y me sale error en del dkpg o algo asi   :p y cuando reincie, se reinicia directamente al pc.... no sera, que esta version de ubuntu no es compatible con la pc?
Es de mejores practicas hacer un ```
sudo apt-get update
``` antes de instalar algun paquete.

El CD que usaste para instalar, esta testeado en su integridad ?
El menu que aparece apenas se inicia la maquina con el CD de Ubuntu posee una opcion para probar la integridad del CD antes de instalar (otra recomendacion de mejores practicas).

---

### Post by Hei Ku on 2009-05-16
Otra buena practica es que nos copies el mensaje de error exacto que da.
En Linux, los mensajes de error sirven para algo, a diferencia de otros sistemas operativos.

---

### Post by driftking20 on 2009-05-16
> **guillermolisi said:**
> Es de mejores practicas hacer un ```
sudo apt-get update
``` antes de instalar algun paquete.

El CD que usaste para instalar, esta testeado en su integridad ?
El menu que aparece apenas se inicia la maquina con el CD de Ubuntu posee una opcion para probar la integridad del CD antes de instalar (otra recomendacion de mejores practicas).

si, ya probe sin instalar, y andaba de 10... despues de instalar se empeso a reiniciar solo

---

### Post by guillermolisi on 2009-05-16
> **driftking20 said:**
> si, ya probe sin instalar, y andaba de 10... despues de instalar se empeso a reiniciar solo
Me parece que contestaste a otra pregunta y no a la que hice.

---

### Post by driftking20 on 2009-05-16
> **guillermolisi said:**
> Me parece que contestaste a otra pregunta y no a la que hice.
uh, recien me doy cuenta jejej

si el cd esta testeado y dice que esta bien.....

ahora pruebo con el que me dijiste recien y les paso el error que me sale

---

### Post by driftking20 on 2009-05-16
aca tengo los errores o cosas que me salen xD

> E: dpkg was interrupted, you must manually run dpkg configure -a to correct the problem

y otro que me salio, cuando quise instalar un programa es...

> E: dpkg was interrupted, you must manually run dpkg configure -a to correct the problem
E -cache->open () falied, please report

que son esos errores? :confused:

a, probe con el otro comando, y empeso a andar mejor.... voy a dejar la maquina andando en ubuntu hoy, para ver si se vuelve a resetear ;)

---

### Post by staar on 2009-05-16
```
E: dpkg was interrupted, you must manually run dpkg configure -a to correct the problem
``` = ```
E: dpkg fue interrumpido, debe correr manualmente dpkg configure -a para corregir el problema
``` es bastante claro (si entendés inglés), tenés que correr en una Terminal ```
sudo dpkg configure -a
``` para corregir los errores que se generaron después de interrumpir al administrador de paquetes...

---

### Post by driftking20 on 2009-05-17
> **staar said:**
> ```
E: dpkg was interrupted, you must manually run dpkg configure -a to correct the problem
``` = ```
E: dpkg fue interrumpido, debe correr manualmente dpkg configure -a para corregir el problema
``` es bastante claro (si entendés inglés), tenés que correr en una Terminal ```
sudo dpkg configure -a
``` para corregir los errores que se generaron después de interrumpir al administrador de paquetes...


probe con eso, pero sigue igual... se resetea la maquina a cada rato :-(

---

### Post by staar on 2009-05-17
no no, eso que te dije es para que puedas instalar, o quitar, paquetes, el administrador de paquetes se habia interrumpido, por lo que no podías instalar nada, ese comando lo 'arregla' (en realidad, le hace terminar de hacer lo que estaba haciendo antes de que fuera interrumpido)

para el tema de los reinicios, correte un memtest (la tercera entrada de ubuntu en el grub) para verificar que las memorias estén bien y descartar que venga por ese lado...

saludos

---

