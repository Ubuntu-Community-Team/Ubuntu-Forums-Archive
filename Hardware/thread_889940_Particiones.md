---
title: "Particiones"
date: 2008-08-14
forum: Hardware
---

### Post by benjamin_linux on 2008-08-14
Hola a todos,

tengo el disco particionado: 67g para Windows y 33g para Ubuntu. Sólamente para romperme la cabeza, quiero instalar Solaris, pero al momento de instalarlo me dice obviamente que no tengo lugar, cómo hago para quitar espacio a la partición de Windows y así poder darle 10 gigas a Solaris?? Porque desde la instalación no puedo hacerlo.

Gracias! :D

---

### Post by sergiom99 on 2008-08-14
proba de bootear con el LiveCD de Ubuntu y usar el gparted.

---

### Post by pol666 on 2008-08-14
NOO Te lo pido por el amor a la humanidad. No instales Solaris si tenes un linux. No tiene compatiblidad con las swap de linux y te deja un error irremobible  en el arranque que solo lo solucionas eliminado la particion de solaris, ubuntu, y la swap y volverlas a crear. Busca si queres en google BAD PBR SIG y corrobora lo que digo,  experiencia propia :(

---

### Post by faktorqm on 2008-08-14
Che pero ese error es del grub que toma mal los cambios, no de la tabla de particiones. va, lo lei aca [http://asupergeek.blogspot.com/2007/06/bad-pbr-sig.html](http://asupergeek.blogspot.com/2007/06/bad-pbr-sig.html) capaz lei todo mal. salu2!

---

### Post by pol666 on 2008-08-15
yo habia leido que era algo con la swap, y de hecho la otra vez me meti en gparted y veia que la swap tenia la etiqueta SOLARIS igual, ya lo habia sacado, no se que onda por que persistia

---

### Post by benjamin_linux on 2008-08-15
Hola,

gracias a todos por las respuestas, por lo que pude investigar... 

[http://www.infolinuxblog.com/how-tos/un-linuxero-en-solaris](http://www.infolinuxblog.com/how-tos/un-linuxero-en-solaris)

[http://www.sun.com/bigadmin/features/articles/multiboot_laptop.jsp](http://www.sun.com/bigadmin/features/articles/multiboot_laptop.jsp)

puede hacerse sin problemas, pero muy probablemente haya complicaciones, que tienen solución, obviamente, más o menos simples... pero es casi un hecho que no detecte a Linux, entonces hay que meterse en el grub, no es muy alentador, sobre todo si no sabés "mucho" (nada :P) como yo.

Lamentablemente lo dejaré para más adelante, supongo...

gracias de nuevo! :D

---

### Post by pol666 on 2008-08-15
Solaris esta hecho para servidores sparc. por que no te probas un linux distinto a ubuntu o algo mas dificil para ir aprendiendo...

---

### Post by benjamin_linux on 2008-08-15
Era esa la idea... qué me recomiendan? OpenSolaris, por lo que vi, es un Solaris linuxero, bastante similar a Ubuntu en algunas cosas (Gnome, por ejemplo).
Qué distribución me recomiendan, más compleja y... distinta?

Muchísimas gracias a todos eh :D

---

### Post by pol666 on 2008-08-15
nah, el escritorio es lo de menos, Depende a que tanto quieras llegar, 
Algo dificil? medio? parecido a ubuntu? con gnome? depende

Solaris no es linux, es unix

---

### Post by faktorqm on 2008-08-15
Slackware proba. Aunque no se por que le tenes tanto miedo al grub... proba Solaris, animate! que es lo peor que te puede pasar? tener que reinstalar el grub? no pasa nada!
Igual Solaris no es solo para sparc, tambien hay para x86/x64. Lo que me queda la duda es si hay para ppc pero bueno. Aparte Solaris adoptó una banda de herramientas de gnu/linux para que sea mas facil de usar. Salu2!!

---

### Post by benjamin_linux on 2008-08-15
A ver,

la versión que tengo de Solaris para instalar es la Express Developer Edition...  y en el mismo sitio de Sun, todas las páginas de soporte, sobre el sistema, ahora te redireccionan a OpenSolaris, como que no va más...

Tendría que descargar, Solaris u OpenSolaris...
pero ustedes me ayudan cuando tenga que meterme en el grub :tongue:

---

### Post by crosssover on 2008-08-16
proba con open solaris, te vas a sorprender lo bien que funciona, ojo yo solo lo probe en modo live, no lo instale oprque lei por ahi que tenia problemas con los grubs de linux al hacer doble booteo, pero creo que no va a haber problemas instalando el grub de solaris en la misma particion donde esta instalado y despues crear el enlace en el boot de linux

---

### Post by benjamin_linux on 2008-08-16
Es lo que me decidí a hacer, ordené a Sun el CD, apenas me llegue lo instalo. En la página oficial hay unas guías y te explica cómo solucionar el problema enel GRUB, así que espero no tener problemas!

Me queda pendiente nada más el tema de la partición, cómo sacarle 10/15g a una de las otras particiones para hacer una nueva en la que instalarlo.

---

### Post by Air23 on 2008-08-19
> **benjamin_linux said:**
> Me queda pendiente nada más el tema de la partición, cómo sacarle 10/15g a una de las otras particiones para hacer una nueva en la que instalarlo.

Para modificar particiones tenes que bootear desde el cd de ubuntu e ir al modo live cd. Luego abris gparted (Sistema>Administracion>Editor de particiones) y con el boton derecho del mouse sobre la particion de interes ir a "redimensionar/mover" donde pones el nuevo tamaño de la particion.

---

### Post by [P]oli on 2008-08-19
> **Air23 said:**
> Para modificar particiones tenes que bootear desde el cd de ubuntu e ir al modo live cd. Luego abris gparted (Sistema>Administracion>Editor de particiones) y con el boton derecho del mouse sobre la particion de interes ir a "redimensionar/mover" donde pones el nuevo tamaño de la particion.

La poca experiencia que tengo **redimensionando** particiones, me hizo perder lo que tenía en la partición que modifiqué, te recomendaría (creo que no soy el único) que hagas un backup de lo más importante de esa partición

---

### Post by benjamin_linux on 2008-08-23
Hola a todos,

les cuento que estos días fui a las JRSL y, participando de una charla sobre OpenSolaris, me dieron el cd... por lo que:

1) Lunes/martes hago un back up de Ubuntu, particiono e instalo OS.

2) Como había ordenado una copia del CD a Sun, esta semana o la otra me va a llegar otro cd... si a alguno le interesa se lo alcanzo, sea en persona o por correo (vivo a diez cuadras de Congreso).

Les contaré los resultados (o los problemas :P).

Y díganme si quieren el CD!

---

### Post by z37a on 2008-08-23
Un consejo, bajate o pedite pro correo OpenSolaris, tambien te lo madan pro correo, y utilizalo en una virtual machine, por que en mi poca experiencia con solaris hize ****** un hdd, el tipo de particiones que usa solaris requiere que si o si destruyas la tabla de particiones para eliminarlas, si no no podes eliminarlas, y a lo sumo intentando eliminarlas sin borrar la tabla podes cagar el rigido(asi fue como lo hize *****).

PD: Por suerte era un disco ageno de un curso que hize y un hdd de 20 o 40Gb de los berretas, asi que no paso nada jajajaj, pero si era mio me daba algo de dolor!!!

---

### Post by benjamin_linux on 2008-08-24
Hola,

ya pedí que me lo envíen por correo, por eso es que lo estoy ofreciendo para aquel que le interese, pues ya me dieron uno el jueves en las jornadas de software libre.

Y aparentemente el OpenSolaris no tiene ese inconveniente. Tanto por lo que me dijeron acá como por lo que encontré en por ahí y lo que dijeron en las charlas sobre el sistema el único problema es que no reconoce la partición de Linux, por lo que hay que copiar el Grub antes de instalarlo... y nada más! (en teoría)

---

### Post by benjamin_linux on 2008-09-09
Los vuelvo a molestar!!

Finalmente me puse, quité 30g a la partición NTFS del Vista, pero no puedo asignárselos a la ext3 porque está siendo utilizada... intenté desde el LiveCD pero no me deja ni puedo desmontarla, alguien sabe cómo puedo hacer??

Gracias :D

---

### Post by zeroadrenaline on 2008-09-09
Desde el Live cd, es bastante simple trabajar las particiones.
Es claro que para poder utilizar Gparted, nececitas que las particiones no esten montadas.
Una vez que arranca el live cd, no deveria de montar las particiones automaticamente, asi que ese problema no lo tenes.
Abris g parted, vas a ver que arriba a la derecha hay una solapa donde podes elegir el disco (fisico) que queres trabajar en caso de que tengas mas de uno en tu gabinete.
Elegis el disco en cuestion, y te va a mostar la tabla de particiones de ese disco.
Si ves que aparece algun candado en alguna de las particiones, significa que esta montada (insisto que esto no deveria de aparecer, pero no esta de mas aclararlo).
En este caso, hay varios temas que pueden ser motivo de tu imposibilidad de terminar el trabajo.
Tu tabla, hasta donde yo entiendo debe tener esta estructura a saber:

........linux (ext2/3).......swap...win(ntfs)......espacio libre(sin formato).....
Puede variar la hubicacion, pero el asunto es este, si vos lo que querias era crear una particion extra para solaris, no tiene mucho sentido lo que planteas cuando decis que queres agregarcelo a la ext3 (que supongo es de linux) porque vos en ese espacio libre queres poner otro sistema, con lo cual tendrias que crear una nueva particion en ese espacio libre (click sobre "espacio Libre", Click sobre boton "Nueva", y bueno ahi, con las flechitas que tiene el dibujito a la iz y a la derecha, dimensiona la particion, o dejale todo el tamaño que tiene, como quieras, aceptas, y esa va a ser tu particion solaris).
Ahora si lo que queres es realmente darle ese espacio libre a la ext3, la estructura del fstab tiene qeu quedarte asi a saber :

........linux.........Espacio libre......swap ....win

Lo que quiero decir es que si queres redimencionar, agrandar puntualment,e la ext3, el espacio libre tiene que estar al lado, esto lo conceguis moviendo las particiones win, y swap haia la derecha, y dejando al lado de la ext3 el espacio libre, esto lo haces todo (tanto el mover como el redimensionar) con la opcion redimensionar o mover.
Leete algo mas claro si no te sive, o si no me explique bien, pero creo que se entiende, si no estas seguro de lo que estas haciendo mejor lee un poco mas, no serias el primero que arruina mucha informacion por no saber partir un disco (HOLA SOY ZEROADRENALINE Y GASTE $400 EN RECUPERAR DATOS POR JUGAR CON GPARTED SIN SABER JEJEJEJEJE).
Perdon por ser tan extenso, espero soluciones.Un abrazo, y si te sirvio, y valio el esfuerzo (cabe destacar que si se postea el horario pueden ver qeu todo esto lo escribi mnientras estoy en el laburo, a riesgo de ser sancionado, bue tampoco tanto pero masomenos, asique tiene mas merito aun!) agregas la medallita y todos contentos.Perdon por la ortografia, espero que les haya gustadoooooooo chau!!:

PAZ!

---

### Post by benjamin_linux on 2008-09-09
A ver... ahora sí necesito ayuda jaja.

Intenté una vez más desde el LiveCD y probé "desactivar el intercambio" del SWAP y ahí sí me permitió modificar la partición de linux. Le había quitado 30g a Windows, que estaban libres y se la asigné. Estuvo media hora comprobando el espacio y cuando empieza a chequear por errores en el sistema de archivos, me tira un mensaje de error. Dos veces, intenté hacerlo y se queda ahí. 
El **PROBLEMA** es que ahora: el sistema operativo me sigue diciendo que hay 5g utilizados y 29 libres, como antes, la partición de Windows ya está sin los 30g que le quité... y si voy al Gparted me dice que la partición de linux ocupa 58, pero que hay 27g ocupados... o sea, **los 30g que le quise agregar están DESAPARECIDOS**, están pero no están, cómo hago, please!

---

