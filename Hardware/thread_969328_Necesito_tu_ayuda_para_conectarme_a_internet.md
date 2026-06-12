---
title: "Necesito tu ayuda para conectarme a internet"
date: 2008-11-03
forum: Hardware
---

### Post by leo_liet on 2008-11-03
Hola a todos, resulta que estuve dando muchas, muchas vueltas con mi placa de red SiS191.

 Al principio creia que era mi router HUAWEI pero este estaba OK.
 Asi que tenia que ser la placa de red, tenia que serlo.
 Y luego de semanas de buscar y buscar encontre esta posible solucion [http://tecnicos.fce.unam.edu.ar/content/view/273/2/](http://tecnicos.fce.unam.edu.ar/content/view/273/2/) pero para llevar a cabo la misma tengo que descargar el codigo del kernel desde internet. Y he ahi el problema, no puedo descargarlo si no tengo internet, y no tengo acceso a otra PC con ubuntu y que tenga internet asi que si alguien puede descargar este paquete por mi y pasarmelo se lo agradeceria infinitamente

> 
  $ sudo apt-get install linux-source-2.6.24
  $ sudo apt-get install libncurses5-dev


 Esos son los dos que necesito


       Muchas gracias desde ya por su tiempo!

---

### Post by c4d0rn4 on 2008-11-03
lo del kernel tengo entendido que está en el build-essential, corrijanme si no es así. Notese el CREO.

si te animas a hacer el intento de que sea eso, se puede instalar con el cd de instalación de ubuntu hardy que usaste

aquí lo explican [http://ubuntuforums.org/showthread.php?t=381532](http://ubuntuforums.org/showthread.php?t=381532)


por otro lado:
[http://packages.ubuntu.com/hardy/linux-source-2.6.24](http://packages.ubuntu.com/hardy/linux-source-2.6.24)
ahí está el kernel


[http://packages.ubuntu.com/hardy/libncurses5-dev](http://packages.ubuntu.com/hardy/libncurses5-dev)
ahí el libncurses5-dev

Fijate que de esa página se pueden bajar los deb de los paquetes que acostumbras a bajar por apt-get

---

### Post by leo_liet on 2008-11-03
Gracias por tu respuesta. Crees que con eso voy a poder solucionar mi problema?
 O sabes de alguna forma de poder solucionarlo?


     Gracias

---

