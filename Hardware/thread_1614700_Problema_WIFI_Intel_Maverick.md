---
title: "Problema WIFI Intel Maverick"
date: 2010-11-06
forum: Hardware
---

### Post by pestefo on 2010-11-06
Hola a todos,

En karmic no tenia problemas con el wifi, pero al actualizar a Maverick no puedo conectarme ya que no está activada la "red" (eso es lo q aparece en el network manager).

Acá está lo q arrojó lspci
[http://pastebin.com/eFWSc0r4](http://pastebin.com/eFWSc0r4)

Al ejecutar iwconfig arroja
[http://pastebin.com/qYxEkrfG](http://pastebin.com/qYxEkrfG)


No kcho q puede ser, he buscado pero no es sobre mi tarjeta. Pregunté en el canal #ubuntu-cl y me comentaron que era raro pq en general las tarjetas intel funcan bien.

Espero puedan echarme una mano :D

---

### Post by moreback on 2010-11-06
Tu iwconfig se parece al mío y yo tengo mi tarjeta inalámbrica Intel desconectada mediante un botón en mi notebook. ¿Tienes algún botón que la habilite en tu pc?

A lo mejor esto ayuda: [http://ubuntuforums.org/showthread.php?t=1359647](http://ubuntuforums.org/showthread.php?t=1359647)

Saludos.

---

### Post by pestefo on 2010-11-06
> **moreback said:**
> Tu iwconfig se parece al mío y yo tengo mi tarjeta inalámbrica Intel desconectada mediante un botón en mi notebook. ¿Tienes algún botón que la habilite en tu pc?

Mi notebook tiene un switch.
El pto es que mande el note a un servicio tecnico pa q le cambiaran el back cover (no creo q haya implicado la falla a menos q flaytemente me hubieran cambiado la placa madre por una que no funca el wifi) pero no corroboré si funcionaba el wifi con la instalacion que tenia cuando lo envié que era un Ubuntu 10.04. Simplemente instale el ubuntu 10.10 desde 0 y cuando lo prendi no funcaba el wifi. Me dije "si no funciona con el ubuntu 10.04(SO que tenia antes de enviar y que SÍ funcionaba), algo le hicieron a mi maquina y voy a reclamar". Asi q lo instalé y funcionó. Decidí upgradear a Ubuntu 10.10 y murio de nuevo D:. Probé con el último Fedora que salió (el 14 me parece) y tpco funcionó. Instalé debian squeeze inclusive y nada, lo actualicé (quedó con el ultimo kernel disponible q es el 2.6.32 me parece) y cueek. Nada.

Asi que de momento preferí volver a instalar Ubuntu 10.04 para poder al menos usar el notebook.


Será alguna falla con el kernel 2.6.32? 
Alguna otra idea.

---

### Post by moreback on 2010-11-06
puede ser algo con el driver del kernel, podrías ver qué modulos tiene cargado tu 10.04 con lsmod. Pega la salida acá. A lo mejor en 10.10 cambiaron el driver y hay que usar el de 10.04.

Saludos.

---

### Post by pestefo on 2010-11-06
Aquí está lo q arrojó lsmod
[http://pastebin.com/Bj0pjG31](http://pastebin.com/Bj0pjG31)

Acabo de actualizar el Ubuntu 10.04, con lo q actualizó al ultimo kernel... al hacer uname -r me dice: 2.6.32-24-generic

Gracias x tu disposición

---

### Post by pestefo on 2010-11-07
Me parece q cuando actualicé el kernel lo actualicé a 2.6.32-25-generic (desde 2.6.32-24-generic), y ahi estaba con wifi. Reinicié luego de la actualizacion y ahora dejó de funcionar.

Aquí está el lsmod (usando el kernel 2.6.32-25-generic)
[http://pastebin.com/tH4WX6cc](http://pastebin.com/tH4WX6cc)

Ehm, eso :P

---

### Post by pestefo on 2010-11-08
Acabo de ver y con el kernel 2.6.32-25-generic sí funciona.

Pero me da cosa upgradear a 10.10

---

### Post by pestefo on 2010-11-25
upgradeé a Maverick de nuevo y como me esperaba no funca.
Actualicé hoy al kernel 2.6.35-23-generic y tpco funciona

lsmod --> [http://pastebin.com/fqSuYV0A](http://pastebin.com/fqSuYV0A)

Espero me puedan ayudar, ya llevo como un mes y ni idea como poder arreglarlo :S

Gracias de antemano.

Saludos

---

### Post by asterix77 on 2010-11-26
¿Que es lo que te aparece al ejecutar lo siguiente por consola?

#sudo iwlist wlan0 scan

(Debería detectar tu punto de acceso)


Podrías intentar también hacer lo siguiente:

#sudo rmmod iwl3945
#sudo modprobe iwl3945

Y después de esto ver si te conecta.

Saludos

---

### Post by pestefo on 2010-11-26
Al ejecutar "sudo iwlist iwlan0 scan", sale:
wlan0     Interface doesn't support scanning : Network is down

hice lo otro que me dijiste sin resultados satisfactorios :S

Con iwconfig (luego de hacer lo del rmmod y modprobe) sale:

#lo        no wireless extensions.

#eth0      no wireless extensions.

#wlan0     IEEE 802.11abg  ESSID: off/any  
          #Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          #Retry  long limit:7   RTS thr: off   Fragment thr: off
          #Power Management: off


Asi que sigo igual =/, gracias x la ayuda :)

---

### Post by moreback on 2010-11-26
A lo mejor te sirven las soluciones que aparecen al final de este post: [http://ubuntuforums.org/showthread.php?t=1529993](http://ubuntuforums.org/showthread.php?t=1529993)

Saludos.

PD: busca en google ambos términos "iwl3945" y "Tx-Power=off", de ahí saqué ese resultado.

---

### Post by pestefo on 2010-11-27
FUNCIONÓ!

[COLOR=Red]**SOLUCION**[/COLOR]

Lo que hice fue aplicar la solucion que sale en la respuesta #10 del post [http://ubuntuforums.org/showthread.php?t=1529993](http://ubuntuforums.org/showthread.php?t=1529993)

La copio acá x si alguien le sirve:

1. rmod tu_modulo_de_wifi
2. rfkill block all
3. rfkill unblock all
4. modprobe tu_modulo_de_wifi
5. rfkill unblock all

(algunas instucciones hay q ejecutarlas como root)
En mi caso, el módulo era iwl3945

Muchas gracias [moreback]("http://ubuntuforums.org/member.php?u=633286") por la ayuda, y también a [asterix77]("http://ubuntuforums.org/member.php?u=840386") :) !!

---

