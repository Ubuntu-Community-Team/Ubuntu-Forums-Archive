---
title: "[SOLVED] DELL VOSTRO 1400 con Intel 3945ABG"
date: 2008-08-14
forum: Hardware
---

### Post by thejavo on 2008-08-14
Hola a todos. Hace unos meses me compré esta maravilla, y le instale Ubuntu 8.04. Al principio no tuve ningún problema, pero en la primera ronda de actualizaciones comencé a tener problemas con la placa inalambrica - Intel PRO/Wireless 3945 ABG (rev 02) - no me conectaba en casa con un router Linksys BEFW11S4 V4. 802.11 b, no habia manera. Me di cuenta tambien que la luz no encendia y comencé mi ronda de busquedas por internet para solucionar el problema. Lo primero que encontré, y que finalmente hoy anda perfecto es instalar el paquete linux-backports-modules-hardy-generic ó

sudo apt-get install linux-backports-modules-hardy-generic

eso, con la versión actual de kernel 2.6.24-19 debería solucionar todos sus problemas. Pero unos meses atrás esto no causaba ninguna diferencia por lo que me incline a instalar el driver anterior ipw3945, con esto me anduvo perfecto, el problema radicaba en que cada nueva actualización del kernel debía volver a compilar el driver la solución completa la encuentran acá:

[http://ph.ubuntuforums.com/showpost.php?p=4932513&postcount=13](http://ph.ubuntuforums.com/showpost.php?p=4932513&postcount=13)

despues de hacer todo lo que dice ahi el problema que me quedaba era que cada vez que iniciaba la maquina debia volver a tipear sudo modprobe ipw3945. Lo solucione editando el archivo /etc/modules y agregando la linea ipw3945 al final. No se si esto último era lo que debía hacer, pero a mi me funcionó bien hasta que se me actualizó a la versión 20 del kernel (tenía habilitado el repositorio hardy-proposed) que me hizo crema mi pobre notebook. Asi que reinstale la partición raiz, actualicé todo el sistema, y al final, para mi sorpresa, el linux-backports-modules-hardy-generic esta vez hizo la magia.

Hay un enlace mas en español que dá instrucciones mas detalladas para compilar el ipw3945 pero ultimamente no me funciona, se los dejo igualmente:

[http://www.ubuntu-es.org/index.php?q=node/88882](http://www.ubuntu-es.org/index.php?q=node/88882)

Espero que les haya sido de ayuda.

---

