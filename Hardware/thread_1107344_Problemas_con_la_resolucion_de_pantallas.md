---
title: "Problemas con la resolucion de pantallas"
date: 2009-03-26
forum: Hardware
---

### Post by drazhe on 2009-03-26
Hola, instale Ubuntu 8.04.2 en mi maquina y esta vez quedo con una resolucion de 1024z768 en un monitor de 17" osea que se ve inmenso, pero recuerdo haberlo instalado antes a la version 8.04.1 y esta llego a tener una resolucion de 1120x1024 o algo asi (era un numero medio caprichoso) no la 1280x1024 que usa Windows en el mismo monitor 

Lo unico raro ademas de la version un poco mas nueva que la anterior es que esta vez instale ubuntu conectado a internet... sera por eso que cargo esta resolucion enorme? como la puedo cambiar? 

ya fui a SISTEMA > PREFERENCIAS > RESOLUCION DE PANTALLA y la mas grande que me permite poner es esta de 1024x768, pero se ve muy grande y feo..... 

Alguna solucion???

---

### Post by joseangelini on 2009-03-26
Que tarjeta de video tenes?
Si no la conoces, tenes que hacer en una consola

lspci

---

### Post by drazhe on 2009-03-26
> **joseangelini said:**
> Que tarjeta de video tenes?
Si no la conoces, tenes que hacer en una consola

lspci

Si es una MSI GeForce 6200TC (TurboCache) de 256mb

baje los controlados y esta activada, pero aun activada o desactivada, la resolucion maxima que soporta es de 1024x768

---

### Post by pablo.s on 2009-03-26
> **drazhe said:**
> Si es una MSI GeForce 6200TC (TurboCache)

Tenés el panel de configuración de NVidia? Probá con ese panel.

---

### Post by josecuervo86 on 2009-03-26
Por que no le agregas la resolución de pantalla que queres al archivo xorg.conf?

---

### Post by drazhe on 2009-03-26
> **josecuervo86 said:**
> Por que no le agregas la resolución de pantalla que queres al archivo xorg.conf?

Y como hago eso??? advierto que soy muy novato en esto asi que por favor, tenes que ser muy claro en tu explicacion.. jejeje

como lo busco, donde lo busco y como lo cambio....

---

### Post by drazhe on 2009-03-26
> **josecuervo86 said:**
> Por que no le agregas la resolución de pantalla que queres al archivo xorg.conf?

bueno, googleando por ahi encontre como editar el xorg.com no tuve mayores problemas... solo que ahora se ve todo chupado para arriba.. jejeje... y no soporta la resolucion 1280x1024 que usa windows.... sin embargo y aunque yo la cargue, la maxima resolucion que acepta es la de 1280x800 y mi monitor tiene un ratio 4:3 asi que no me sirve esa... 
lo que si aparecio fue la del valor caprichoso... 1152x768, pero aun esta se ve medio chupada para arriba... es normal que se vea asi?

---

### Post by drazhe on 2009-03-26
Problema solucionado..... no me di cuenta y yo copie y pegue la solucion de la pagina de la que hablo mas adelante, y en esa pagina la resolucion mas alta era la de 1280x800 jejeje que gil lo mio no haber leido antes.... agregando el valor 1280x1024 cargo la resolucion deseada y ahora esta con un ratio 4:3 sin deformaciones ni nada por el estilo... 

Gracias a todos por la ayuda!

---

### Post by drazhe on 2009-03-26
una ultima que la resolucion, me acabo de dar cuenta que se me movieron algunos botones del lugar en el escritorio

aca dejo una imagen de lo que veo

[http://s3.subirimagenes.com/imagen/previo/thump_2236161pantallazo.png](http://s3.subirimagenes.com/imagen/previo/thump_2236161pantallazo.png)

el boton de apagar antes de cambiar la resolucion estaba bien en la esquina superior derecha, y y llendo para la izquierda en la misma linea, tenia el dia y la fecha, aplicaciones abiertas, mi nombre de usuario

y debajo en la parte inferior izquieda la papelera y al lado las 2 pantallaz del SO, ahora la papelera la tengo medio corrida para un costado... como se soluciona eso? o me tengo que acostumbrar a ver esos botones ahi

---

### Post by josecuervo86 on 2009-03-26
Eso lo podes cambiar apretando con el boton derecho arriba del iconito y luego seleccionas "mover". Despues lo arrastras hasta donde quieras

---

### Post by drazhe on 2009-03-26
pero con esos botones (el de apagar y el de la papelera) no me da la opcion de mover.... 

lo mismo pasa con las del Evolution y el de ayuda ?... hacer volar el icono del firefox para poner el de opera tambien me costo un poco... y no lo pude poner en donde queria...

---

### Post by drazhe on 2009-03-27
> **josecuervo86 said:**
> Eso lo podes cambiar apretando con el boton derecho arriba del iconito y luego seleccionas "mover". Despues lo arrastras hasta donde quieras

que gil lo mio.... estaba tilda la opcion "bloquear panel" asi nunca lo iba a poder mover... jejeje.... entiendame soy muy nuevo en esto de ubuntu.. jejeje

---

### Post by FMGS on 2009-03-27
proba esto
manu 
1  sistema
2  administracion
3  pantallas y graficos
pestaña -  modelo y busca la resolucion que queres
si es widescrren activa la casilla monitor panoramico  y te habilita otras resoluciones aceptas y elejis la resolucion que queres.

ojo esto a mi me funciono de maravilla con el driver nvidia 
espero te sea util
:P

---

### Post by drazhe on 2009-03-27
mira, pude solucionar el tema editando el archivo xorg cuando entraba en las preferencias la resolucion mas alta que daba era la 1024x768 en un monitor de 17" esa resolucion se ve enorme... despues de editar el xorg y cargar la resolucion estandar de un monitor asi alcanzo la 1280x1024, y ahora se ve de maravilla.

Gracias a todos por la ayuda!

---

