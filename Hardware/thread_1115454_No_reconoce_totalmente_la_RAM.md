---
title: "No reconoce totalmente la RAM"
date: 2009-04-03
forum: Hardware
---

### Post by josecuervo86 on 2009-04-03
Como andan gente? Espero que bien.

Paso a relatarles el problema. Hace una semana compre 2Gb de RAM para agregarle a los 2GB que ya tenia mi PC. Cuando prendo la pc la BIOS me reconoce los 4096MB (4GB). Una vez adentro, corri el comando:
```
sudo lshw-gtk
```
y este tambien me reconoce los 4Gb.
El problema surge en el Monitor del sistema (Sistema - Administracion - Monitor del sistema) que solo me reconoce 3.2Gb.
Estuve investigando bastante y segun encontre en internet el problema puede ser del kernel, que no estaria preparado para manejar esas cantidades de memoria, aunque he visto gente que puede usarlos tranquilamente. 
Me gustaria terminar de descartar cualquier posibilidad que se les ocurra para hacerlo andar, a excepcion de poner el kernel de la edicion server, porque no soporta los graficos de nVidia.
Les aclaro que tengo Ubuntu Intrepid Ibex x86-64 (64 bits)
Un saludo

---

### Post by pablo.s on 2009-04-03
-Vas a tener que bajarte los paquetes source del kernel que tenés
-Después a la manera de los guapos hacer make menuconfig 
-Ir a la parte donde gestiona la cantidad de memoria
-Despues con make-kpkg buildpackage lo compila y hace paquete
-Instalalo

Me hace acordar a esa navidad que salió el kernel 2.6 y me emocioné
mucho mucho y le hice pelota la cuenta de telefono a mi viejo por
bajar 24 MB por dial up. Esos eran los dias...

---

### Post by josecuervo86 on 2009-04-03
Gracias pablo, lo voy a probar!

Tengo una pregunta que hace rato me vengo haciendo: se nota que sabes mucho de linux, pero por que solo tenes 133 comments? Usabas otra distro antes?

---

### Post by pablo.s on 2009-04-03
> **josecuervo86 said:**
>  se nota que sabes mucho de linux, pero por que solo tenes 133 comments? Usabas otra distro antes?

Usé Mandrake desde el año 1998 hasta mediados del 2oo5, 
cuando me harté de su politica comercial y elitista de club
de barrio, con sus versiones Community, Club, etc. que
discriminaban a los usuarios según su billetera.

Un dia leí en el blog de Jeff Waugh que habia un super
proyecto secreto de hacer una distribución "Debian reloaded"
que iba a cambiar el mundo (toda la fe del mundo se tenían
los muchachos).
Cuando salió la primera versión de Ubuntu la probé pero
no me funcionaba bien la placa de red, mucho no me
preocupé por arreglarla porque habian avisado que en
seis meses iban a lanzar una versión nueva. Dicho y hecho,
a los seis meses salió, la instalé y me gustó tanto que
pedí 20 discos para regalar entre amigos. Dos solamente
aceptaron.
Desde entonces es la distribución que uso. En cuanto a los
posts, antes entraba al foro pero anda mas leia lo que
posteaban. Pero como ahora trabajo desde mi casa puedo
tener mas tiempo para estar conectado y ayudar.

Traté de resumir, porque la historia es mas larga.
Saludos.

---

### Post by josecuervo86 on 2009-04-03
ya me parecia que alguien con tanta experiencia no podia tener tan pocos post. Un abrazo, y ya empiezo a probar lo que me dijiste

---

### Post by pablo.s on 2009-04-03
Pero tené mucho cuidado, vas a despanzurrar el 
motor de la nave para despues armarlo.
Si lo hacés mal no te arranca, eh
Avisé. Saludos

---

### Post by euzkoarima on 2009-04-06
Duda: y no puede ser que si tenés video incorporado en la mother, te "esté sacando" ram, en la cuenta que hace el monitor del sistema ????????

Saludos,
Eduardo

---

### Post by josecuervo86 on 2009-04-06
> **euzkoarima said:**
> Duda: y no puede ser que si tenés video incorporado en la mother, te "esté sacando" ram, en la cuenta que hace el monitor del sistema ????????

Saludos,
Eduardo

La analize a esa, pero si fuera asi creo que cuando tenia 2Gb tambien me tendria que haber "confiscado" lo de la targeta. Tengo una Geforce 8400GS que me chupa 256Mb pero eso esta lejos de los 800Mb que me estan faltando :)

Con respecto a compilar el kernel, ya lo tengo casi listo, solo tengo que conseguir un par de librerias que misteriosamente no estan en los repos y lo compilo. Voy a arriesgar bastante, considerando que me da bastante p**a hacer un backup de todo, pero si me sale bien valdra la pena

---

### Post by pablo.s on 2009-04-06
> **josecuervo86 said:**
> La analize a esa, pero si fuera asi creo que cuando tenia 2Gb tambien me tendria que haber "confiscado" lo de la targeta. Tengo una Geforce 8400GS que me chupa 256Mb pero eso esta lejos de los 800Mb que me estan faltando :)

Con respecto a compilar el kernel, ya lo tengo casi listo, solo tengo que conseguir un par de librerias que misteriosamente no estan en los repos y lo compilo. Voy a arriesgar bastante, considerando que me da bastante p**a hacer un backup de todo, pero si me sale bien valdra la pena

Eh? No papá, que backup? Vos armás el kernel como
paquete, lo instalás y en grub van a figurar también los
kernels anteriores, si por una de esas no te sale bien, 
booteas con el kernel anterior y asi vas probando hasta 
que te salga bien. Nunca te aparecieron en grub dos
kernels? Esto es asi, no quise asustarte, era solamente
para que te concentraras, porque si te decia esto de 
entrada te iba a dar p**a y anda a saber si lo hacias.

Y la tarjeta de video no creo que te saque memoria,
si debe tener incorporada su propia memoria.

---

### Post by josecuervo86 on 2009-04-06
Pablo, vos decis que en el menu.lst del grub, cargue mi kernel? porque yo segui una guia que funcaba de otra forma.

Y la placa de video tiene 256Mb, pero yo le puse que le robe 256 a la Ram para que ande "mas mejor" :P

Edit: Ampliamos la información :P

Segui este tutorial [0], y tenes razón, no te caga nada, yo recien ahora me doy cuenta, pero me parece que elegi el camino largo. Tuve que crear el kernel, hacer algo llamado vmzlinuz con ese kernel y lo que me falta es crear el initrd del kernel, para lo cual necesito unos paquetes llamados initrd-tools y otro mas que no me acuerdo. Luego dentro del grub, creas un nuevo boot con el kernel, el vmzlinuz y el initrd para que los pueda cargar. Me parece que lo hice de la manera larga no? :)

[0] [http://www.ubuntu-ve.org/?q=node/79]("http://www.ubuntu-ve.org/?q=node/79")

---

### Post by pablo.s on 2009-04-06
> **josecuervo86 said:**
> Pablo, vos decis que en el menu.lst del grub, cargue mi kernel? porque yo segui una guia que funcaba de otra forma.

Y la placa de video tiene 256Mb, pero yo le puse que le robe 256 a la Ram para que ande "mas mejor" :P

Si el kernel que armás vos lo termina haciendo
paquete, creo que se agrega automagicamente
al menu.lst (aunque hay un margen de error &#8723;1)

Los 256 MB que le agregaste a la tarjeta de video
se lo agregaste a la tarjeta on-board, que desde el
vamos si tenés una tarjeta PCI Express tenés que 
desactivar ( a menos que uses dos monitores o
más) aunque por tu firma veo que no.
En la BIOS lo desactivas y le das prioridad a la
tarjeta principal para que arranque. Fijate que
son 256 MB al gas que estás asignando a la nada.
En el foro hay mucha gente que anda cortina de
memoria, queda feo che.

---

### Post by josecuervo86 on 2009-04-06
Pablo, antes que nada, lee el post anterior que amplie la info :P

En cuanto a la Tarjeta, esta en particular viene con 256Mb de Ram ddr2, pero con la opción de ampliarla a 512, obviamente choreada de la Ram del equipo. Cuando me fijo en nVidia Settings me da que tiene asignados 512 de Ram en total. Obviamente que la placa onboard la desactive a la m****a :D

---

### Post by pablo.s on 2009-04-06
Y que hacés con 512 MB de memoria de video?
Ah, no me digas nada... Ya me autorespondi...

Bueno, asunto solucionado entonces.
Saludos.

---

### Post by josecuervo86 on 2009-04-06
> **pablo.s said:**
> Y que hacés con 512 MB de memoria de video?
Ah, no me digas nada... Ya me autorespondi...

Bueno, asunto solucionado entonces.
Saludos.

pera pera, queda el asunto del kernel, decime si lo hice de la forma correcta o mande fruta en codigo :P. En la pagina anterior te deje mas info en forma de edit.

---

### Post by faktorqm on 2009-04-07
Yo cuando compile mi kernel lo hice asi tambien, de hecho no conozco otra manera. Genere el archivo de configuracion con el make menu-config, arme la imagen vmlinuz, hice el init-rd, etcetc y no hace falta agregar a mano la entrada en el grub, cuando haces update-grub (deberia figurar en alguna parte del tutorial) te lo agrega solo. De hecho si mal no recuerdo la secuencia era generar el vmlinuz, (que se te generaba solo en la compilacion, solo habia que copiarlo a /boot y cambiarle el nombre), hacer init-ramfs-<algo>, update-grub y reiniciabas y listo. (y listo no, ya podias ver tu primer kernel panic xD)

Salu2!!!

---

### Post by josecuervo86 on 2009-04-07
Faktor, si, eso es lo que estaba trantando de hacer. Puse "trataba" porque al querer hacer la initrd del kernel me tiro unos cuantos errores, asique despues veo si lo compilo nuevamente desde cero.

---

### Post by josecuervo86 on 2009-04-07
Faktor, no se si sos adivino, o pai Unbanda, pero tal como dijiste: acabo de tener mi primer kernel panic!! Y sobrevivi :P . Y como dijiste vos tambien, me cargo el kernel al grub solito, ni siquiera tuve que poner el comando que dijiste vos. Se ve que no estaba muy bien compilado que digamos :D

---

### Post by faktorqm on 2009-04-07
Vas por buen camino! Asi se empieza. Yo estuve alrededor de 3 meses leyendo documentaciones de cosas hasta que pude armar algo que funcionara, (mal, pero andaba) y deberia ver todavia algunas cosas, (por ejemplo mi webcam no es reconocida por mi kernel pero si por el generico, y asi un par de "cositas").

Salu2!

---

### Post by juancra on 2009-05-23
Hola gente!

este es mi primer post en esta comunidad, hace poco empece con Ubuntu (tengo puesto el Jaunty 9,04), aunque ya hace años habia probado un tiempo con Mandriva. 
Lo cierto es que la distro me gusta mucho.. es mas eclectica que cualquier windows y mucho mas rapida!
Concretamente les escribo porque tengo un problema parecido al del chico que empezo este thread: Tengo 2 gb de memoria en la maquina (una AMD Athlon 64 x2 ) pero chusmeando en el resumen del sistema veo que solo me reconoce 400 y pico MB... 
Busque un tutorial sobre como editar el kernel (algo ya sabia porque en Mandriva tuve que modificarlo para usar un modem AMIGO usb que tenia) pero no me encuentro bien y no se que modificar para disfrutar toda la ram de la maquina. ¿No me podrian dar una mano?
Aun asi .. me sorprende lo bien que anda y lo estable que es con esa poca ram!

Gracias gente, espero que puedan ayudarme!.

---

### Post by Hei Ku on 2009-05-23
Que programa usaste para fijarte cuanto te reconoce de memoria?

Podes poner esto en una terminal y postear lo que te tira?

lshw | grep memory -A 4

---

### Post by juancra on 2009-05-23
hola Hei! Gracias por darme una mano!

Lo que me da el comando que me pedis es lo siguiente: 


*-memory             
          description: System memory
          physical id: 0
          size: 510MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+

Gracias y espero que lo podamos arreglar.. no puedo esperar a ver como corre con los 2 gb!

---

### Post by Hei Ku on 2009-05-23
Si entras al setup del BIOS de tu PC te muestra correctamente los 2GB?

---

### Post by juancra on 2009-05-23
Si! asi lo tenia en WIN XP. En realidad serian unos 1.5 GB porque 512 los tengo para la Radeon Xpress 1250 on board que uso.

---

### Post by z37a on 2009-05-23
Desde el live CD si corres el memtest+ que te dice????

---

### Post by juancra on 2009-05-23
Hola gente!

Acabo de solucionar el problema (aunque no tocando el kernel) . Resetee la computadora y con asombro observe que la bios me decia "installed RAM : 1024mb" no! como puede ser? me dije, temiendo lo peor. Apague la computadora y saque los slots (dos Super talent de 1gb cada uno DDR 667MhZ) y los intercambie de lugar: Santo remedio.. ahora marca 1,5GB , como tiene que ser. 
Lamento las molestias ocasionadas y haber empezado mi participacion con el pie izquierdo!

Gracias por la ayuda, 
Sebastian!

---

### Post by NickCis on 2009-05-23
El problema del autor del post no puede ser que SO de 32 bits te reconoces hasta 3,2 Gib (o ese es un mito que dios solo sabe de donde lo saque).
No tendria que usar la vercion de 64bits de Ubuntu?.
Perdonenme si me equivoco.
Saludos.

---

### Post by guillermolisi on 2009-05-23
> **juancra said:**
> Hola gente!

Acabo de solucionar el problema (aunque no tocando el kernel) . Resetee la computadora y con asombro observe que la bios me decia "installed RAM : 1024mb" no! como puede ser? me dije, temiendo lo peor. Apague la computadora y saque los slots (dos Super talent de 1gb cada uno DDR 667MhZ) y los intercambie de lugar: Santo remedio.. ahora marca 1,5GB , como tiene que ser. 
Lamento las molestias ocasionadas y haber empezado mi participacion con el pie izquierdo!

Gracias por la ayuda, 
Sebastian!
En este foro hubo casos asi en el que el interesado tenia la solucion a su alcance y tuvieron que indemnizar a los que se devanaron los sesos pensando en cual era el problema y su posible arreglo, con un pancho y una cocacola. Dejamos esto a tu criterio :D

Bienvenido, buen debut y gracias por darnos un detalle mas a tener en cuenta para cuando alguien venga con algo parecido.

---

### Post by pablo.s on 2009-05-23
> **guillermolisi said:**
> tuvieron que indemnizar a los que se devanaron los sesos pensando en cual era el problema y su posible arreglo, con un pancho y una cocacola.

Este es un post heredado
(o continuado). Yo intervine
en el post. Me toca recibir
compensación igual?
Que dice el departamento
legales? Aunque sea media
recompensa...

---

### Post by josecuervo86 on 2009-05-23
y al que empezo el post? hablando en serio, voy a probar intercambiando los slots, igual no creo que funque por que la bios me los reconoce :S

---

### Post by juancra on 2009-05-24
Jajaja! bueno, entonces coca y sanguche para los colaboradores!

Voy bastante bien con el Ubuntu.. tengo 2 problemitas nada mas: cuando reseteo la pc, la conexion a internet deja de andar: Tengo que apagarla y resetear el router (zyxel P600) para que agarre. Lo otro es que la maldita resolucion no se queda cuando reseteo! uso el comando xrandr -s 2 para setearla como me gusta pero no se guarda con el reset. Alguna idea pa' empezar? Veo que hay bocha de users de LP.. empeze a trabajar ahi hace unos meses y la verdad le tome cariño a la ciudad! 

Nos vemos gente!
Gracias por la mano y la buena onda.

---

### Post by juancra on 2009-05-24
Chicos, el problema que tenia con Internet lo pude resolver de la siguiente manera: 

Tras establecer que el problema era que al resetear se cambiaba la direccion de DNS que yo tenia por una que no funcionaba, encontre este post ([http://ubuntuforums.org/showpost.php?p=1364482&postcount=19](http://ubuntuforums.org/showpost.php?p=1364482&postcount=19)) que me brindo la solucion. 

Se que es un off topic total, pero lo cuelgo para cualquiera que le pueda servir!

Gracias!

---

### Post by anarko on 2009-05-26
> **josecuervo86 said:**
> y al que empezo el post? hablando en serio, voy a probar intercambiando los slots, igual no creo que funque por que la bios me los reconoce :S

Pudiste compilar el kernel?
Si no, proba con este tutorial[1], en el menuconfig cuando eleguis el tema del manejo de memoria, lei por ahi que tenes que ponerle para que gestione 64Gb para que puedas ver los 4Gb enteros, sino queda siempre limitado a 3.2.
O en su defecto clavate un x86_64.



[1] [http://www.esdebian.org/articulos/23843/compilar-kernel-estilo-debian](http://www.esdebian.org/articulos/23843/compilar-kernel-estilo-debian)

---

### Post by josecuervo86 on 2009-05-26
gracias anarko, voy a analizar el link que me pasaste y luego comento que tal me fue

---

