---
title: "Problema espacio hdd"
date: 2010-03-15
forum: Hardware
---

### Post by JoeGregov on 2010-03-15
Buenos dias a todos antes que nada, vengo aqui con el fin de pedir ayuda con un problema que me ha causado unos dolores de cabeza bastante grandes. Les paso a comentar, hace  unos meses tenia ubuntu 9.10, genial andaba todo muy bien pero por un motivo de juegos me pase a windows devuelta, cosa que detesto, pero esta vez me canse, windows lo tire a la basura, rompi el cd, no quiero ni verlo, soy un linux-adicto, ahora se me presento este problema. Yo tengo un disco hitachi de 82gb supuestamente, igual siempre en las pc marca 76, osea que lo normal seria 76 gb, lo que siempre me aparecia, ahora bueno, formatie con ubuntu y instale el ubuntu, pero entro y me marca que tengo 66gb de espacio, es muy raro voy a la utilidad de discos y me aparece que tengo 79gb, es algo muy raro al ver eso lo que pense es que se habian dañado algunos sectores del hdd, asi que hice un low level format, todo perfecto eso, y bueno reinstale ubuntu, el mismo problema, no se me ocurre que puede llegar  a ser, aunque no hay tanto diferencia unos 10 gb nunca vienen mal al no tener un hd tan grande.
Gracias a todos por leer.
Cualquier sugerencia sera agradecida. Muchas gracias

---

### Post by guillermolisi on 2010-03-15
Normalmente el fabricante de discos expone la capacidad fisica bruta del dispositivo. Luego y en funcion de las caracteristicas de tipo de sistema de archivos que utilices, sera la capacidad real neta (luego del analisis de superficie y posterior formateo).

Si durante el analisis de superficie se encontraron puntos defectuosos, estos se marcan y se utilizan sectores alternativos en su lugar para evitar perdida de datos. Si esto sucede indefectiblemente tendras menos capacidad final ya que el tamaño fisico del disco es fijo.

---

### Post by JoeGregov on 2010-03-15
Antes que nada gracias por responder.
Eso ya lo sabia es normal pero el tema es que antes de volver a instalar ubuntu, me aparecian los 76 gb de espacio, ahora 66 gb , es algo raro. Nunca me marco errores en el disco, hice varios scaneos con varios programas, y la verdad no decia nada, pero sigue siendo muy raro. Mira a continuacion te muestro unas fotos en donde se ve el cambio:
[IMG]http://img519.imageshack.us/img519/3918/pantallazo1x.png[/IMG]


Aqui dejo la otra:
[IMG]http://img51.imageshack.us/img51/1174/pantallazopo.png[/IMG]
PD: Esta muy feo mi ubuntu porque lo tengo recien instalado :p

Muchas gracias a todos

---

### Post by guillermolisi on 2010-03-15
No logro ver cual es el problema. Palimpsest te dice que el disco es de 77GiB y el primer screenshot, donde te descuenta el espacio que ya usas con lo instalado, te da 65.7GiB lo que da alrededor de 10Gb ocupados.

Salvo que este dejando de lado algo, para mi estan normales las relaciones que se muestran

---

### Post by JoeGregov on 2010-03-15
Guillermo ,gracias por responder denuevo. 

Si pero lo que pasa es que es una instalacion limpia, antes cuando lo ponia me dejaba 70 gb si recuerdo bien, no es un tema de tanta importancia, vengo aca asi puedo hablar con expertos y saber que puede ser, no es algo que preocupe mucho pero siempre uno esta dispuesto a aprender y ir solucionando pequeñeses :p es algo raro, no tengo nada en el disco, eso es lo que no enteindo pero bueno, puede ser que sea lo que decis y estoy calculando algo mal.

Muchas gracias!

---

### Post by guillermolisi on 2010-03-15
El "antes" era tambien con ext4 o usabas otro file system ?

Hay una forma de hacer que el file system reserve menos espacio para sectores dañados pero no es aplicable a particiones que incluyan la del sistema. Normalmente ext4 reserva aproximadamente el 10% del tamaño total del disco para esos fines, por eso la percepcion de que ocupa mucho lugar.

---

### Post by JoeGregov on 2010-03-15
Eso podria ser, yo lo que hice, despues de hacer el low level format, agarre el partition magic y desde otra pc lo formatie para linux segun decia, creo que era ext3.
Bueno cuestion, ya esta 10 gb menos no me cambia la vida, pero muchisimas gracias Guillermo por todo.

---

### Post by guillermolisi on 2010-03-15
Te cito un comentario por un tema parecido que se esta conversando por la lista de soporte via e-mail:
> >> Estoy seguro que esa diferencia es por el espacio reservado que usa el
>> ext3/ext4 por defecto (5%); lo que es una barbaridad para un disco
>> moderno (en este caso se reservan como 35 GB). Una solución es
>> modificar este espacio con:
>>
>> sudo tune2fs -m 1 /dev/sdXX
>>
>> De esta forma se reserva 1% del espacio en esa partición, que en este
>> caso son como 7 GB. Ahora si la partición no es la de sistema (es una
>> partición para datos solamente, como cualquiera que se monta en
>> /media/XXX o una partición separada para home) podés deshabilitar
>> completamente el espacio reservado con:
>>
>> sudo tune2fs -m 0 /dev/sdXX
>>
>> pero remarco que este último comando NO SE TIENE QUE EJECUTAR EN LA
>> PARTICIÓN DE SISTEMA, porque te puede traer muchos problemas si se te
>> llena (léase no te arranca más el sistema, ni siquiera en failsafe, y
>> tenés que arrancar con un livecd y borrar cosas para que vuelva a
>> funcionar).
>>
>> Según el man de tune2fs este espacio reservado además sirve para
>> evitar la fragmentación, pero yo tengo deshabilitado este espacio
>> reservado en dos discos que tengo (uno de 500GB y otro de 80GB) y no
>> noté hasta ahora ningún problema de velocidad en la lectura de ambos
>> (el de 500GB es ext4 y el de 80GB es ext3).
>>
>> --
>> Sebastián Abate
>> Quattro-D
>> 15-3589-7730
>> [EMAIL="abates@quattrod.com.ar"]abates@quattrod.com.ar[/EMAIL]

---

### Post by JoeGregov on 2010-03-15
Guille, la verdad sos un genio. Me solucionaste el problema ahora me volvio el espacio que tenia antes. Enserio muchas gracias, pero te hago una pregunta antes de finalizar el tema, luego de correr ese comando que estaba en aquella cita, puedo perder rendimiento o algo por el estilo?, es recomendable dejarlo asi?
Gracias!

---

### Post by guillermolisi on 2010-03-15
> **JoeGregov said:**
> Guille, la verdad sos un genio. Me solucionaste el problema ahora me volvio el espacio que tenia antes. Enserio muchas gracias, pero te hago una pregunta antes de finalizar el tema, luego de correr ese comando que estaba en aquella cita, puedo perder rendimiento o algo por el estilo?, es recomendable dejarlo asi?
Gracias!
Siempre que no lo apliques a la particion que contenga el directorio raiz (/ - root directory), no deberias experimentar perdida de rendimiento, por lo menos es lo que dicen quienes lo han modificado (y se basan en que si el disco es moderno y esta en optimas condiciones con reservar algo menos de espacio en disco es suficiente).

Mi posicion personal, y aqui juega mi vivencia de cuando usaba Unix, es que si los discos modernos son cada vez mas grandes no deberia molestarme que se asignen algunos cientos de Gb para fines funcionales (sea mapa de sectores alternativos, logging, journaling, etc.). Para darte una opinion mas categorica deberia leer mas en detalle sobre el tema.

---

