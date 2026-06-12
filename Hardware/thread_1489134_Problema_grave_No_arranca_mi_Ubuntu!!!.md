---
title: "Problema grave: No arranca mi Ubuntu!!!"
date: 2010-05-20
forum: Hardware
---

### Post by dam1977 on 2010-05-20
Al iniciar el Grub y elegir Ubuntu 10.04 me aparece lo siguiente:
Gave up waiting for root device. Common problems:
  -Boot args (cat /proc/cmdline)
    -Check rootdelay= (did the system wait long enough?)
    -Check root= (did the system wait for the right device?)
  -Missing modules (cat /proc/modules; ls/dev)
Alert! /dev/disk/by-uuid/7ecfbbe4-dac0-41aa-8621-dfd486ecf438 does not exist opping to a shell!

Qué podrá significar todo esto y como puedo restaurar mi querido Ubuntu?

---

### Post by guillermolisi on 2010-05-20
Me suena a que se cambuio la UUID del disco. En algun momento se montaba con una UUID que ahora no es la misma y por eso no encuentra el disco.

Modificaste la conexion del disco a la controladora ?
Algun cambio en el hardware que incluya al disco ?

---

### Post by dam1977 on 2010-05-21
Terminamos de configurar Virtualbox con XP. Lo usamos perfecto y anduvo un rato. Pero en un momento se colgó, y al reiniciar con el botón de la PC empezó a hacer estas cosas raras. ¿Tendrá algo que ver el Virtualbox? Me parece raro. Quizás la manera de reiniciar. En realidad cuando se colgó el Virtualbox yo no estaba. Les pasó a mis hijos. Ahora me extraña que después de tantos intentos fallidos de arreglarlo (usando el CD de instalación) ahora me arrancó perfecto. ¿???

---

### Post by guillermolisi on 2010-05-21
No, VirtualBox no produce este tipo de situaciones.

Revisa los cables que van de la motherboard al disco. Puede que no esten bien ya que si el disco no tiene alimentacion o el cable de datos no esta con una conexion franca si pueden producir estas cosas.

---

### Post by dam1977 on 2010-05-21
Guillermolisi!!! Me vas a tener que pasar la cuenta de tus servicios!!! No tenes idea cuanto te agradezco tu ayuda. Cuando llegue a casa voy a chequear las conexiones que me dijiste. Ahora estoy pensando en cambiar el disco q tengo con Ubuntu (Maxtor de 80 gigas medio jovatito) porque recuerdo que con Windows xp tambien me causaba algunos fallos. De golpe te aparecia un mensaje que no encontraba el disco y cosas así.

---

### Post by alfplayer on 2010-05-21
> **dam1977 said:**
> Guillermolisi!!! Me vas a tener que pasar la cuenta de tus servicios!!! No tenes idea cuanto te agradezco tu ayuda. Cuando llegue a casa voy a chequear las conexiones que me dijiste. Ahora estoy pensando en cambiar el disco q tengo con Ubuntu (Maxtor de 80 gigas medio jovatito) porque recuerdo que con Windows xp tambien me causaba algunos fallos. De golpe te aparecia un mensaje que no encontraba el disco y cosas así.

El disco puede estar llegando al fin de su vida útil.

---

### Post by dam1977 on 2010-05-21
Creo que por ahí anda la cosa. Por ahora (no se por qué) anda todo bien. Pero estamos por darle la jubilación al disquito. Ya cambiamos el micro. Tenemos un modesto (pero mejor de lo que había antes) Dual Core que instalamos en una nueva placa madre. Pero bueh... seguiremos cambiando cosas...

---

