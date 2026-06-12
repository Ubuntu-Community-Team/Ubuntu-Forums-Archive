---
title: "Murio Mi disco recien WTF!"
date: 2008-08-20
forum: Hardware
---

### Post by pol666 on 2008-08-20
Estaba en windows tocando al guitarrita apague la pc, me acorde que tenia que buscar algo la volvia prender y no booteaba. Meto un live cd de ubuntu y en la carga em decia DRDY ERR blablabla y un error ciclico no leia el sata.

Reviso el gabinete todo ok, saco el cable y ahi booteo el live cd (desde donde les estoy hablando) no hay muchos datos de loq ue me pudo haber pasado pero todo indica que murio el disco, algun error logico tal vez, la bios lo reconoce bien, perfectamente pero no responde, no bootea, y no hay forma de iniciar un sistema si el disco esta conectado osea, no puedo formatear bajo ninguna forma.

Ahora me imagino que voya tener que comprar un disco
lo que me va a salir de 150 a 300 pesos, y no si voy a comprar un sata  o un ide

ensima tenia info importante, 3 sistemas o, 20gb de musica, TABLATURAS un monton, fotos, libros, archivos, configuracion AAAAAAAAAAh

---

### Post by Hei Ku on 2008-08-20
lo cambiaste de interfaz al disco? ponelo como esclavo en otra interfaz IDE, o cambialo de interfaz SATA. Y obviamente fijate el orden de booteo para que arranque primero el CD despues del cambio.

---

### Post by faktorqm on 2008-08-20
Tocando la guitarra a las 3 de la mañana? no tenes vecinos?
Con respecto a los datos lo mismo de siempre, hubieras hecho back-up.
Con respecto al disco ponele la mano encima cuando arrancas la compu y fijate que hace. Tendrias que sentir que vibra, y eso estaria indicando algo asi como que la aguja se mueve.
Cuando pones el gparted te muestra las particiones que tenias antes de todo? O que te muestra? Por que decis que no lo podes formatear? Para que queres formatear alguna de las particiones? uhh te mate a preguntas perdon ajjaja salu2!!

---

### Post by Lokkete on 2008-08-20
mm antes de comprar un rigido te recomiendo q bajes los "tools hd" de la pagina del fabricante... normalmente es un iso el cual grabas en un cd o un diskette, los cuales son de booteo... entontonces booteas con el cd o diskette q hayas creado y bue ahi empeza a leer porque cada fabricante tiene su suftware. 

Igualmente son muy intuitivos esos soft y faciles de usar suelen tener 3 seguro

quick scan: escaneo rapido
full scan: escaneo profundo con test de superficie
exercise: ejercitio del hd para ver si responde bien

sino funciona eso puedes intentar un formato de bajo nivel en el peor de los casos, el software tambien te lo bajas de la pagina del fabricante

PD: mira bien en bajar el soft para tu modelo de hd

---

### Post by sergiom99 on 2008-08-20
o buscate en el emule el "hirens boot cd", que tiene un monton de utilidades, incluyendo los de los fabricantes de HDD.
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

creo que no pone link de descarga, pero en P2P esta.

Link descargas: [http://www.9down.com/Hiren-s-BootCD-9-5-23765/](http://www.9down.com/Hiren-s-BootCD-9-5-23765/)

---

### Post by Mauro22 on 2008-08-20
Te lo frito windows jejej


Hablando en serio.

Proba levantandolo en otra PC, asi tenes herramientas en entorno grafico :)

Sino ya te lo dijeron, el hirens, el System Rescue CD, etc etc..

En fin, si no hace ruido groso al girar, tal vez esta salvado.

Suerte! y para la proxima hace backup!



PD: Windows es como las mujeres. Cuando mas la necesitas te abandonan. :(

---

### Post by pol666 on 2008-08-20
1- Era a las 12 y estaba con auriculares grabando :P
2- Tengo un pequeño back up pero nada comparable con muchas cosas que tenia (que me iba a imaginar que iba a morir el disco )
3- el disco tiene conector sata nomas, como que lo conecte a IDE?
4- no, no puedo bootear el ubuntu si el disco esta conectado por lo tanto no puedo usar gparted.
5- ok, voy a descargar el hirens boot

Gracias ;)

---

### Post by Lokkete on 2008-08-20
por experiencia propia te digo bajatelo de la pagina del frabricante por nro de modelo.... pero es tu rigido haz lo q mejor te parezca

que preferis un soft del fabricante que sabe como es la arquitectura del hd o un soft de un tipo que cree saber la arquitectura del hd?!

---

### Post by pol666 on 2008-08-20
Se le diagnostico Muerte subita. Lo probe en la pc de mi hmana y le pasa lo mismo...

Alguien sabe de algun lugar donde restauren discos? me gustaria salvar algunas cosas todavia

---

### Post by sergiom99 on 2008-08-20
primero proba el hiren's boot cd a ver que pasa.
(ya incluye las utilidades propias de los principales fabricantes, el no invento nada)

se que la restauracion la hacen un lugares especiales, asepticos y que costaba un ojo de la cara.

---

### Post by [P]oli on 2008-08-20
> **faktorqm said:**
> 
Con respecto al disco ponele la mano encima cuando arrancas la compu y fijate que hace. Tendrias que sentir que vibra, y eso estaria indicando algo asi como que la aguja se mueve.


Probaste eso? fijate conectándolo como esclavo y decile a la BIOS que lo bootee último, cosa que puedas bootear con el HD que anda, así masomenos podés rebuscartela mejor, y probá con esos cd's de restauración que te dicen por ahí arriba, alguno servirá

---

### Post by pol666 on 2008-08-20
bah, vibrar vibra que se yo, no esta quemado, la bios lo reconoce, no hace ruidos extraños,

---

### Post by faktorqm on 2008-08-20
Y bueno, arranca con un live cd y fijate si te monta las cosas... y si no lo monta, ahi si abri el gparted y fijate si te lee las particiones. Acto seguido hiren's a ver que dice. si dice que esta sin particiones o con particion desconocida, es un problema logico, no pasa nada. si no te muestra nada o todo lo que queres hacer te tira error, es fisico. de todas maneras podes seguir probando cosas. salu2!

---

### Post by vk-cdg on 2008-08-21
Por lo que entendí, cuando el disco está conectado fisicamente al conector SATA la PC no levanta (arrancando con un LiveCD).

El disco palmó!

---

### Post by crosssover on 2008-08-21
a mi me paso lo mismo hace un mes con mi disco, prendia, giraba pero tenia un error fisico de **** madre y no pasaba ningun test de diagnostico, por suerte la garantia me dio otro pero la informacion se fue para siempre :(

---

### Post by pol666 on 2008-08-21
el tipo que me hizo la pc, no me dejo la garantia del disco, tengo la de la mother la de la grabadora y creo que la de la nvidia...

---

### Post by euzkoarima on 2008-08-21
Te tiro una, pero no le pongas mucha fe que digamos, a mi me funcionó una vez (y discos muertos ya tuve 7 aprox, así que las estadísticas no son buenas, pero...)
Sacas el disco, lo metes en una bolsita de nylon bien cerrada y en lo posible sin aire, mete el disco en el congealdor de la heladera unas horas, sacalo y probá.
YA SE, no tiene lógica, es más, cuando me lo contaron pensé: peor, las partes móbiles se van "agarrotar". Pero bueh, una vez me anduvo. Perdido x perdido...

Suerte.

---

### Post by pol666 on 2008-08-22
> **euzkoarima said:**
> Te tiro una, pero no le pongas mucha fe que digamos, a mi me funcionó una vez (y discos muertos ya tuve 7 aprox, así que las estadísticas no son buenas, pero...)
Sacas el disco, lo metes en una bolsita de nylon bien cerrada y en lo posible sin aire, mete el disco en el congealdor de la heladera unas horas, sacalo y probá.
YA SE, no tiene lógica, es más, cuando me lo contaron pensé: peor, las partes móbiles se van "agarrotar". Pero bueh, una vez me anduvo. Perdido x perdido...

Suerte.


Jaja, Gracias por el consejo ya estuvimos hablando de eso hoy, les cuento a los demas que lo deje a arreglar mientras me compre un disco de 250$. Con todo el dolor del mundo tema resuelto.

---

