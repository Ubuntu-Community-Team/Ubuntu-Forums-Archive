---
title: "dudas sobre cómo particionar al cambiar windows por ubuntu"
date: 2009-07-13
forum: Instalación y Actualización
---

### Post by ghostrider01 on 2009-07-13
ok Señores.... acatando las sugerencias les agradezco el guiarme en el foro ya que en principio debi ser mas ordenado.

tengo las sgtes dudas con respecto a cambiar mi sistema desde winxp a ubuntu, ya me quedo claro que mejor bajare la ultima version de ubuntu con soporte para 64bit.

ya teniendo el sistema operativo mi primera duda es: actualmente tengo particionado mi disco duro de 500gb dejando 200gb para sistema y 300gb para guardar archivos. 

si comienzo la instalacion de ubuntu corro el riesgo de que tome mi disco completo para formatear y pierda mis archivos? de poder instalar solo en mi particion de sistema puedo hacer en esos 200gb todas las particiones que requiere ubuntu?.

se agradece.

---

### Post by Carlos C on 2009-07-14
> **ghostrider01 said:**
>  ya teniendo el sistema operativo mi primera duda es: actualmente tengo particionado mi disco duro de 500gb dejando 200gb para sistema y 300gb para guardar archivos. 

si comienzo la instalacion de ubuntu corro el riesgo de que tome mi disco completo para formatear y pierda mis archivos?
Puedes instalar sin perder tus archivos, lo importante es que hagas un particionado manual. Es una opción que se te da a escoger durante la instalación.

> **ghostrider01 said:**
>  de poder instalar solo en mi particion de sistema puedo hacer en esos 200gb todas las particiones que requiere ubuntu?.

Si, con 10Gi para tu sistema te sobra espacio (nunca he pasado los 5 Gi, pero es mi experiencia). Ahora, para tu "home" el espacio que necesites dependerá de tu gusto particular. Yo que tú haría una partición de alrededor de unos 10Gi para "/", una partición swap que dependerá de tu memoria ram y el resto lo dejaría todo para tu "home".
Seguramente esta información te debe generar muchas dudas, por lo tanto, te recomiendo que, antes de plantearlas en este mismo thread, leas atentamente la siguiente página de la Guía Ubuntu:

[http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)

Por favor leela completa, es breve y entenderás mejor a lo que me refiero.
Saludos.

---

### Post by ghostrider01 on 2009-07-14
ok..... ya cumpli con el primer paso, descarge y grabe una version de kubuntu (la ultima segun entendi) tb lei la guia sobre particiones. asi que solo queda hecharle mano al pc.

pero tengo otra duda?

como cargo los drivers de mi placa?

---

### Post by radixs on 2009-07-14
> **ghostrider01 said:**
> ok..... ya cumpli con el primer paso, descarge y grabe una version de kubuntu (la ultima segun entendi) tb lei la guia sobre particiones. asi que solo queda hecharle mano al pc.

pero tengo otra duda?

como cargo los drivers de mi placa?

Men que prueba el disco como live-cd y ahi veras si tienes problemas de driver. Si tu hardware estubiera soportado en GNU/Linux, todos tu drivers debiena intalarse de forma automatica...

PD: Leerce la documentacion de internet sobre ubuntu, de verdad hay bastante. Tampoco es neceario que instales Kubuntu en tu pc, pruebalo primero antes de intalar ;)

---

### Post by ppellet on 2009-07-15
> **ghostrider01 said:**
> ok Señores.... acatando las sugerencias les agradezco el guiarme en el foro ya que en principio debi ser mas ordenado.

tengo las sgtes dudas con respecto a cambiar mi sistema desde winxp a ubuntu, ya me quedo claro que mejor bajare la ultima version de ubuntu con soporte para 64bit.

ya teniendo el sistema operativo mi primera duda es: actualmente tengo particionado mi disco duro de 500gb dejando 200gb para sistema y 300gb para guardar archivos. 

si comienzo la instalacion de ubuntu corro el riesgo de que tome mi disco completo para formatear y pierda mis archivos? de poder instalar solo en mi particion de sistema puedo hacer en esos 200gb todas las particiones que requiere ubuntu?.

se agradece.

Hola ghostrider01

Te cuento mi experiencia: instalé ubuntu 8.04 junto con w.vista. Así puedo correr algunos programas propietarios como el de una grabadora digital (Sony), cuya extensión es msv y para la cual, aún no encuentro alguna aplicación en linux para transformar este tipo de archivos. Además, de un par de otros softwares de unos instrumentos que uso.

Si quieres tener los dos sistemas operando, primero debes desfragmentar tu disco en windows. Luego, comenzar con el Live CD, como te indican en otro post.

Yo tengo particionado mi disco (80 Gb) como sigue:
-20 Gb w.vista
-5 Gb vista-linux (esta es una partición donde puedo intercambiar archivos entre los dos OS, sin embargo, parece que a partir de ubuntu 8.04 se pueden leer y editar sin problema los archivos que existan en w.vista o w.xp, esto sin la necesidad de esa partición adicional. Yo aún no la elimino.).
-15 Gb sistema de archivos - ubuntu 8.04 LTS
-2 Gb swap - leí por ahí, hace mucho tiempo, que es conveniente una swap (memoria de intercambio) del doble de la memoria RAM, como tengo una memoria de 1 Gb...
-38 Gb para el /home

De preferencia, realizar el proceso de instalación teniendo conexión a internet para actualizar todo de una vez, aunque no es condición *sine qua non*.

Igual, conviene probar si todo funciona correctamente usando el live CD antes de instalar. Si ocurre algo mal puedes comenzar otro hilo y preguntar al respecto. Yo tuve una situación como esa hace unas semanas atrás y logré dar con la solución, a continuación instalé todo y ahora disfruto tranquilamente del trabajo realizado.

Espero te sirvan estos comentarios.

Saludos a todos y mucho éxito,

---

