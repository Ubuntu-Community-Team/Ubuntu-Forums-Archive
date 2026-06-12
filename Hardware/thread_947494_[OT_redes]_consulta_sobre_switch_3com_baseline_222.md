---
title: "[OT: redes] consulta sobre switch 3com baseline 2226"
date: 2008-10-14
forum: Hardware
---

### Post by faktorqm on 2008-10-14
Hola a todos, los molesto en esta oportunidad para saber algo en realidad, por que no tengo idea de donde buscarlo.
Tengo en mi trabajo un switch 3com baseline 2226 plus, y lo estoy configurando. Quiero poner uno de los puertos gigabit en modo trunk, o sea, uno ya lo tengo de uplink, conectado a un backbone. El otro, lo quiero en modo trunk para conectarle un server y de ahi poder rutear entre dos vlan's (es de 24 bocas, necesito hacer unas pruebas, y puse 3 bocas para la vlan 2, el resto las deje asi) y bueno, me lei el manual, el faq en internet, pero no encontre en ningun lado que diga que no se puede, y cuando yo lo quiero hacer me dice que tengo que poner los 2 puertos gigabit en el grupo id 3 (el 25 y el 26), como que no puedo poner uno solo. (el 25 quiero dejarlo asi, el 26 a modo trunk)
Alguien ya lo hizo? se le ocurre alguna idea? Gracias y salu2!

---

### Post by sebastianabate on 2008-10-15
Me parece que acá tenés un error de concepto. En los switch 3com el término TRUNK hace referencia al agrupamiento de puertos para que funcionen como uno solo, y no al TRUNK VLAN (802.1Q). Es por eso que te está pidiendo que pongas los dos puertos giga en ese modo, para que funcionen como un solo puerto de 2 GB.

En los switch 3com creo que el trunk vlan se llama VLT (VLan Trunk). Pero mejor confirmá todo lo que te estoy diciendo, porque hace bastante que no manejo vlans en un switch 3com.

---

### Post by faktorqm on 2008-10-15
Muchas gracias! confirmé lo que dijiste hoy a la mañana, cuando fui al faq de 3com y estuve 3 horas leyendo... lo que ellos entienden por "Link Aggregation" es el modo trunk que decis vos, que es usar los dos puertos como si fuera uno solo, para tener 2 cables fisicos digamos pero que tome todo con un puerto.
Ahora yo lo que quiero es usar 802.1Q. Como hago 802.1Q? lo unico que pude inventar (leyendo el faq en linea y el manual) es que, creo por ejemplo la vlan 2, le asigno el puerto 24 "untagged" (solo ellos saben que significa) y el 26 "tagged". Luego creo la vlan 3, le asigno el 23 "untagged" y el 26 "tagged". En teoria, el puerto marcado como "tagged" deberia ser el que hace vlan trunk. Mañana lo pruebo y te aviso si no lo hace. Gracias y saludos!!!:)

---

### Post by sebastianabate on 2008-10-15
Es exactamente como vos decís, para que un puerto pueda pertenecer a varias vlans tiene que ser tagged, los puertos untagged sólo pueden pertenecer a una vlan (por defecto la vlan 1, que es la que viene de fábrica y a la que pertenecen todos los puertos del switch).

---

### Post by faktorqm on 2008-10-15
Gracias loco!!!!! es bueno tener una certeza de vez en cuando...
Ahora le voy a ir poniendo al vconfig las placas con el vlan id y vemos como hace todo. MUCHAS GRACIAS!!!

---

