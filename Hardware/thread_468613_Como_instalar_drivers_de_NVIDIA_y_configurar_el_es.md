---
title: "Como instalar drivers de NVIDIA y configurar el escritorio 3d"
date: 2007-06-09
forum: Hardware
---

### Post by gpone on 2007-06-09
Hola gente les comento que recien baje la ultima version del ubuntu para probarlo y me encontre con que no puedo activar la aceleracion 3d para mi nvdia 7600gt si alguien me puede dar una mano con eso se lo agradeceria.:p

La instalacion es fresh y esta instalada en el disco rigido, no estoy corriendo el live CD :P

---

### Post by guillermolisi on 2007-06-09
Gpone

Es una instalacion fresh o una actualizacion desde la 6.10 ?

Si es una actualizacion, antes de hacerla funcionaba la aceleracion 3d ?

Si tenes el CD de la 7.04, probaste si la aceleracion 3d funciona iniciando la maquina con el LiveCD ?

---

### Post by Mafber on 2007-06-09
Hola!!!
Pregunta: instalaste ubuntu o lo estas corriendo desde el cd (LiveCD)?
-Si tenés instalado Ubuntu andá a Sistema/Administración/Gestor de controladores restringidos y activá los drivers de nvidia.
Para los efectos 3d: andá a Sistema/Preferencias/Efectos de escritorio y activalos.
-Si es desde el cd: no tengo ideas, tal vez sea igual, pero no se
Espero que te sirva... Suerte!!!

---

### Post by gpone on 2007-06-09
Hola gente, ante todo gracias por responderme. 
La instalacion es fresh y esta instalado el ubuntu 7.04 en el disco rigido.
El escritorio 3d que viene con ubuntu es tipo beryl? de no ser asi, me podrian indicar como instalar la ultima version de beryl sin tener conexion a internet ( no tengo acceso a internet en la maquuina con ubuntu :D)

---

### Post by QUASAR_FREAK on 2007-06-10
ubuntu viene con compiz, osea el cubo 3d lo tenes, pero si queres beryl si o si necesitas bajar los paquetes de internet.

con conexión solo haces:

sudo aptitude install beryl-manager beryl-ubuntu emerald

Tendrias que fijaret que paquetes y dependencias te quiere bajar y bajarlas en alguna maquina con internet y pasar los paquetes de alguna forma a la maquina de ubuntu al directorio /var/cache/apt/archives

---

### Post by erickelrojas on 2009-11-10
Esta instalación es más sencilla y eficiente [http://www.elleonplateadodeojosrojos.es/blog/controladores-de-nvidia/](http://www.elleonplateadodeojosrojos.es/blog/controladores-de-nvidia/)

---

### Post by josecuervo86 on 2009-11-10
Este thread tiene mas de dos años ;)

---

