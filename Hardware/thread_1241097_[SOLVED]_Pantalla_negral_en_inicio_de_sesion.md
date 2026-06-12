---
title: "[SOLVED] Pantalla negral en inicio de sesion"
date: 2009-08-15
forum: Hardware
---

### Post by jorgebada on 2009-08-15
hola instale mi placa nvidia 5200 y despues de eso cuando arranco la pc y llega a la parte de inicio de sesion me queda en pantalla negra, pongo mi nombre y mi contraseña sin ver poruqe esta todo negro y entra pero no se porque me aparece la pantalla negra estoy usando el ubuntu 8.04

---

### Post by harry2006 on 2009-08-15
> **jorgebada said:**
> hola instale mi placa nvidia 5200 y despues de eso cuando arranco la pc y llega a la parte de inicio de sesion me queda en pantalla negra, pongo mi nombre y mi contraseña sin ver poruqe esta todo negro y entra pero no se porque me aparece la pantalla negra estoy usando el ubuntu 8.04
if you are expecting a quick response try posting your threads in "English"...

---

### Post by guillermolisi on 2009-08-15
> **harry2006 said:**
> if you are expecting a quick response try posting your threads in "English"...
Thank you very much, Harry, but we are in Latin America and Spanish is the "default" language (except Brazil).

Note that this is the Argentina LoCo Tema Forum (or subForum considering Ubuntu Forums as a whole)

---

### Post by harry2006 on 2009-08-15
i completely agree...but it was a suggestion so as to let others make use of the solution...

---

### Post by guillermolisi on 2009-08-15
> **jorgebada said:**
> hola instale mi placa nvidia 5200 y despues de eso cuando arranco la pc y llega a la parte de inicio de sesion me queda en pantalla negra, pongo mi nombre y mi contraseña sin ver poruqe esta todo negro y entra pero no se porque me aparece la pantalla negra estoy usando el ubuntu 8.04
No te animas a actualizar o instalar 9.04 ?

---

### Post by josecuervo86 on 2009-08-15
Por lo que decis el problema pareceria estar en el GDM(donde pones tu nombre de usuario y contraseña) pero no en el escritorio en si, no?

Si es asi, se me ocurren dos posibilidades:

1- Que modifiques el logueo para que lo haga automaticamente: **Sistema**>**Administración**>**Ventana de entrada** y luego de ahi te vas a la pestaña seguridad y marcas donde dice "Activar entrada automática" (primera opción) y seleccionas tu usuario (si es que hay mas de uno)

2- Que pruebes cambiar la ventana de entrada, o algun parametro de la misma. Esto se hace tambien en **Sistema**>**Administración**>**Ventana de entrada**

Si no es en el GDM avisa, porque al menos eso es lo que yo entendí

---

### Post by jorgebada on 2009-08-17
Puse automatico todavia no lo pruebo. Con respecto a actualizarlo a la ultima version como lo hago, me tengo q bajar el ubuntu completo, porque yo lo tengo actualizado desde SISTEMA/ADMINISTRACION/GESTOR DE ACTUALIZACION, no se pierden las cosas q le agrege, me mate agregandolas y no las quiero perder.

---

### Post by guillermolisi on 2009-08-17
> **jorgebada said:**
> Puse automatico todavia no lo pruebo. Con respecto a actualizarlo a la ultima version como lo hago, me tengo q bajar el ubuntu completo, porque yo lo tengo actualizado desde SISTEMA/ADMINISTRACION/GESTOR DE ACTUALIZACION, no se pierden las cosas q le agrege, me mate agregandolas y no las quiero perder.
La actualizacion a una nueva version se hace a traves de Synaptic o del Update Manager.

Una vez que pusiste al dia la version que estas usando, tendrias que ver un aviso en el Update Manager que te advierte sobre una nueva version. Si haces click en ese aviso comienza el proceso de actualizacion a la nueva version.

Solo actualiza lo relacionado con el sistema operativo y paquetes instalados via repositorios normales. Los repositorios que agregaste los desactiva hasta haber terminado la actualizacion con lo cual los tenes que volver a activar a mano (un click nada mas) despues que todo el proceso finalizo e iniciaste la maquina con la nueva version.

Antes de activar los repositorios que agregaste, tenes que revisarlos porque como cambiaste de version es posible que tengas que modificar alguno o todos (los que tienen raiz Intrepid deberian tener raiz Jaunty a partir de ese momento).

Tambien es probable que con ciertos paquetes el sistema te consulte sobre cietos archivos de configuracion, para saber si deja el archivo existente o lo reemplaza por la version del maintainer. En esta operacion te deja ver las diferencias entre un archivo y otro para que vos decidas.

Mi recomendacion es no dejar desatendida la actualizacion ya que los mensajes que se generan podrian ayudar mucho llegado el caso de algun inconveniente.

---

### Post by jorgebada on 2009-08-17
no logro encontrar como actualizarlo al 9, me fui a SISTEMA/ADMINISTRACION/ GESTOR DE ACTUALIZACION y me dice q no hay actualizaciones disponibles y no me aparece nada. en el Synaptic no se como actualizarlo busque pero no encontre nada

---

### Post by guillermolisi on 2009-08-17
> **jorgebada said:**
> no logro encontrar como actualizarlo al 9, me fui a SISTEMA/ADMINISTRACION/ GESTOR DE ACTUALIZACION y me dice q no hay actualizaciones disponibles y no me aparece nada. en el Synaptic no se como actualizarlo busque pero no encontre nada
Tenes que ir a Software Sources, Updates y fijarte en Release Upgrade. Tiene que decir Normal Releases (disculpa, tengo todo en Ingles).

Recien ahi te aparecera el aviso de una nueva version.
Va a tardar un buen rato, varias horas.

La version 8.04 es LTS (Long Term Support) y estas versiones por defecto se actualizan cuando sale otra que tambien sea LTS (Abril del 2010).

---

### Post by jorgebada on 2009-08-17
ahi me aparecio pero la 8.10 no mas como es esto actualizo a esta version y despues me me va a ir dando la opcion de ir actualizando mas o solo esa version.

Tengo screenlets en el escritorio eso se pierde??? tb tengo los codecs instalados eso tb c pierde??. No se si me conviene actualizar q beneficios me da. Estas versiones vienen en español o solo en ingles???

---

### Post by josecuervo86 on 2009-08-17
Cuando actualizas de esa manera no perdes **nada**. Tus programas siguen estando, sus configuraciones tambien, los codecs, el fondo de pantalla. Actualiza tranquilo que no pasa nada. Como experiencia, ayer le actualize a Jaunty la notebook a mi vieja (4 horas con 1 mega de velocidad) y quedo tal y  como venia haciendolo en Intrepid

---

### Post by jorgebada on 2009-08-20
Muchas gracias ya lo actualice y quedo expectacular, lo unico que me cambio fue que no me puso los efectos de escritorio y por eso no me andaba el avant windows navigator

---

