---
title: "X/Ubuntu arranque fallido!"
date: 2010-05-01
forum: Instalación y Actualización
---

### Post by toshin696 on 2010-05-01
Hola cabros... buena comunidad...

Tengo el siguiente problema...
Tenía instalado el ubuntu 9.10 y funcionaba de maravilla, pero cuando quise actualizarlo a 10.04 me tiraba errores en lo respositorios para Chile, así que opte por instalación limpia bajando la iso 10.04. Todo va bien... Lo instale desde un usb y aparentemente se instaló sin problema alguno, PERO al momento del primer reinicio y luego de GRUB Lucid se niega a arrancar quedandose pegado en la pantalla negra con el palito(?) en horizontal...

Lo instale dos veces y lo mesmo... Así que se me ocurrio instalar el 9.10 y vóila arranco sin problema, así que se me ocurrio mandarle su actualización a 10.04 lts. Todo bien hasta el reinicio y me paso lo mismo...

Intente los modos recovery, pero = se va a negro...

Alguna idea... puede que sea un problema con el montaje de particiones... Me vendría bien una manita... SALUDOS...

---

### Post by Lutho on 2010-05-01
si mas lo recuerdo en alguno foros explicaban algo de que habia un problema con el grup... 
creo ubuntu se retraso por ese problema
el comando para reparar era

sudo grub-install --recheck /dev/sda 

aqui es donde saque la informacion

[http://www.taringa.net/posts/linux/5347280/ubuntu-10_04-se-retrasa,-pero-aqui-lo-podes-descargar!.html](http://www.taringa.net/posts/linux/5347280/ubuntu-10_04-se-retrasa,-pero-aqui-lo-podes-descargar!.html)

saludos espero que de algo ayude

---

### Post by toshin696 on 2010-05-02
Vale cumpa ppor responder... al final lo solucione... o más se solucionó...

Fue como un Poltergeist... ya que al primer arranque luego de actualización e instalación limpia el ubuntu se reusaba a bootear, pero apagando el pc completamente y dejarlo así por un rato to'o arranque sin problema...

Supongo que hay que dejar reposar al pc con ubunntu XD...

Saludos...:popcorn:

---

