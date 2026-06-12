---
title: "Ayuda en Instalacion"
date: 2009-10-07
forum: Instalación y Actualización
---

### Post by Chano28 on 2009-10-07
hola compatriotas , soy nuevo en esto , asi que necesito su ayuda en un tema especifico ,

quiero instalar world of warcraft en mi ubuntu , segui los pasos que daban en cierta pagina de internet , pero no pasa nada , al actualizar me sale un error asi

"W:error de GPG: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy release las firmas siguientes no se pudieron verificar por que su llave publica no esta disponible : no_pubkey  584033026387EE263" algo asi me sale

si alguien sabe como instalarlo o ayudarme con este error se lo agradeceria , ya que me aburri de jugar wow en Wilson

Gracias  a todos

---

### Post by themasterdark on 2009-10-07
Hola... mira te falta la llave de autentificacion de ese repositorio...

En una consola escribe

> wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

y luego en consola tambien

> sudo apt-get update

y para instalar wine

> sudo apt-get install wine

-----------------------------------------------------

para lo de world of craft

mira la guia de ubuntu.

[http://www.guia-ubuntu.org/index.php?title=World_of_Warcraft#Instalando_los_paquetes_necesarios](http://www.guia-ubuntu.org/index.php?title=World_of_Warcraft#Instalando_los_paquetes_necesarios)

Saludos.

---

### Post by nopersona on 2009-10-07
También sería bueno conocer "la cierta pagina de internet"

---

### Post by themasterdark on 2009-10-07
mmm... si pero esperemos a ver si con lo que escribi mas arriba se solucionó su problema...

saludos

---

### Post by Chano28 on 2009-10-08
hago lo que me dices pero me sale este error :"E: dpkg  was interrupted , you  must manually  run 'dpkg --configure  - a '  to correct  the problem" eso es .

saludos

---

### Post by themasterdark on 2009-10-08
debes fijarte... los mensajes que te da, mira...

esta parte:

> "E: dpkg was interrupted , you must manually run 'dpkg --configure - a ' to correct the problem"

ahi dice en ingles claro... xD
que ejecutes dpkg --configure -a ----> es sin espacio entre el guion y la a final

por lo tanto deberias hacer:

> sudo dpkg --configure -a

y luego:

> sudo apt-get update

Saludos

---

### Post by Chano28 on 2009-10-08
ahora si funciono , ahora es el juego que no se marca el boton aceptar , para poder continuar la activacion , (antes de eso me pedia los direct y esta claro que no lo iba encontrar , sera que por ahi sera el problema) cual seria el reemplazo de los direct , Open gl mmmm 
 
saludos y desde yamuchas gracias

---

### Post by themasterdark on 2009-10-08
[http://doc.ubuntu-es.org/Instalar_Directx_usando_Wine](http://doc.ubuntu-es.org/Instalar_Directx_usando_Wine)

para el problema de direct X
busca en google primero antes de consultar.

Saludos

---

