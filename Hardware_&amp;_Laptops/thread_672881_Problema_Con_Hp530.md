---
title: "Problema Con Hp530"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by ricnar456 on 2008-01-20
Tengo un problema con la HP530 de mi hermano, al principio instalamos ubuntu gutsy y todo funcionaba perfectamente tanto wireless como la red, pero luego el formateo esa instalacion puso windows, y luego volvio a instalar ubuntu con un CD chequeado (el mismo que habia suado en la primera instalacion) y ahora en windows funciona la red y funciona wifi, pero en ubuntu solo funciona wifi, en la lista de hardawre aparece la placa de red bien detectada, pero no sale en ADMINISRACION-RED la opcion para configurar la red, solo la conexion telefonica y la wifi, lo instalamos 5 veces, bajamos actualizaciones, bajamos de todo, le instalamos drivers a mano de la pagina de HP, y no hay caso.
En la lista de controladores restringidos solo aparece el wifi, y el de red no.
Nos e si se habra cambiado algo en el setup del bios, aunque no tiene muchas opciones, las toque a todas y no hubo caso, no se ya que hacer, lo peor es que cuando instalamos ubuntu antes funciono perfecto, y ahora no hay forma de que detecte y funcione por red.

Esto ocurre tanto con el live cd como con la instalacion

si alguien sabe algo que pueda ser de ayuda se los agradezco enormemente.

ricnar

---

### Post by ricnar456 on 2008-01-21
Comoe s un problema medio extraño y que afecta solo a estas maquinas y la solucion fue redificil de hallar googleando solo 1 persona puso la solucion correcta y esta aqui por si a alguien mas le pasa lo mismo.

el tema era que al activar la tarjeta de red en el BIOS salia este cartel

Initializing Intel(R) Boot Agent GE v1.2.31
PXE-E05: The LAN adapter's configuration is corrupted or 
has not been initialized. The Boot Agent cannot continue.

se ve que se activaba parcialmente la placa d ered o algo asi porque a mi hermano le iba en windows, pero en mi casa no iba, y ambos tenemos cablemodem, que no hay que hacer nada solo enchufarlo y funciona, no podia navegar en mi casa, y en la de el si con windows, en ubuntu no navegaba con en ninguna.

al final di con la pagina de este que le paso lo mismo y que hizo una imagen de CD booteable que arranca un archivo que es provisto por intel para configurar esto y solo ejecutarlo como dice alli y activar en el BIOS ahora ya no daba error, y empezo a navegar tanto en windows en todos lados, como en ubuntu perfectamente.

[http://www.matinfo.ch/blog/archive/2007/01/26/intel-nic-pxe-e05-error.html](http://www.matinfo.ch/blog/archive/2007/01/26/intel-nic-pxe-e05-error.html)

por si a alguien le pasa, ahi esta la solucion, funciona perfecto.
gracias
ricnar

---

