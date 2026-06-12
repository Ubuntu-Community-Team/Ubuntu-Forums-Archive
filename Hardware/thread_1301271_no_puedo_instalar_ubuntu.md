---
title: "no puedo instalar ubuntu"
date: 2009-10-25
forum: Hardware
---

### Post by juanma10 on 2009-10-25
hola a todos!!
alguien me podra ayudar?
no puedo instalar ubuntu.
lo descargue, lo descomprimi, pero cuando empieza a instalar , sequeda colgado, la pantalla negra del sistema, con el titulo ubuntu, y la barra de progreso, que se queda quieta.

puede ser que mi pc sea incompatible.?
ojala alguien me ayude, gracias

---

### Post by josecuervo86 on 2009-10-25
Hola juanma10, podrias contarnos en que maquina estas tratando de instalarlo (procesador, memoria ram y todo lo que sepas)?

---

### Post by juanma10 on 2009-10-25
> **josecuervo86 said:**
> Hola juanma10, podrias contarnos en que maquina estas tratando de instalarlo (procesador, memoria ram y todo lo que sepas)?
hola gracias por responderme!!!
te comento: 
procesador:pentiun 4  2.66 ghz , 
memoria: 1 gb de ram,
disco de 80 gb
tengo windows xp, service pack 3
placa de video geforce 128 mb
nose que mas puedo contar.
ojala me puedan ayudar!!!!

saludos

---

### Post by josecuervo86 on 2009-10-25
Ok, pareciera que de Hardware vas bien! A ver, un par de preguntas: Cuanto esperaste hasta decidir que la barra esta trabada y no avanza? La carga de la barra suele variar dependiendo del hardware. La barra en algún momento avanzo o siempre se quedo "trabada"? Esa barra que se traba te aprece cuando queres cargar el liveCD o cuando directamente queres instalar?
Con esas preguntas contestadas vemos como seguimos!

---

### Post by juanma10 on 2009-10-25
> **josecuervo86 said:**
> Ok, pareciera que de Hardware vas bien! A ver, un par de preguntas: Cuanto esperaste hasta decidir que la barra esta trabada y no avanza? La carga de la barra suele variar dependiendo del hardware. La barra en algún momento avanzo o siempre se quedo "trabada"? Esa barra que se traba te aprece cuando queres cargar el liveCD o cuando directamente queres instalar?
Con esas preguntas contestadas vemos como seguimos!
bueno te comento:

1_ la ultima vez espere mas o menos 35 minutos
2_la barra empieza a moverse, va y viene, luego se queda trabada casi al inicio.
3_probe de las dos maneras arrancando desde el cd, cambiando el booteo o instalando sin el cd., la barra aparece despues de que seleccione el idioma, despues de que elijo por ejemplo ver la demo sin instalar.

salu2

---

### Post by guillermolisi on 2009-10-25
> **juanma10 said:**
> hola gracias por responderme!!!
te comento: 
procesador:pentiun 4  2.66 ghz , 
memoria: 1 gb de ram,
disco de 80 gb
tengo windows xp, service pack 3
placa de video geforce 128 mb
nose que mas puedo contar.
ojala me puedan ayudar!!!!

saludos
El disco es IDE o SATA ?

Si es IDE, esta como master del canal IDE primario ?
La unidad de CD es IDE o SATA ?

Tenes marca y modelo de la motherboard ?

---

### Post by josecuervo86 on 2009-10-25
Mira, sinceramente desde hardware parecieras no tener problemas, el liveCD de ubuntu necesita 384M de Ram para funcionar correctamente, y el procesador ese se la deberia bancar. Si a nadie se le ocurre otra idea, te recomendaria que pruebes con la versión Alternate de instalación que la podes bajar de aca: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). No es tan linda como la del liveCD pero anda sobre cualquier maquina!
De cualquier manera, si queres esperar a que otro aporte algo, dale nomas!

---

### Post by juanma10 on 2009-10-25
> **guillermolisi said:**
> El disco es IDE o SATA ?

Si es IDE, esta como master del canal IDE primario ?
La unidad de CD es IDE o SATA ?

Tenes marca y modelo de la motherboard ?
gracias:

estuve viendo en administrador de dispositivos del disco y me aparece esto:

controladoras ide ata/atapi:

intel(r)82801eb ultra ata storage controllers
intel(r)82801eb ultra ata storage controllers

me aparece dos veces, puede ser el problema??

---

### Post by juanma10 on 2009-10-25
> **josecuervo86 said:**
> Mira, sinceramente desde hardware parecieras no tener problemas, el liveCD de ubuntu necesita 384M de Ram para funcionar correctamente, y el procesador ese se la deberia bancar. Si a nadie se le ocurre otra idea, te recomendaria que pruebes con la versión Alternate de instalación que la podes bajar de aca: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). No es tan linda como la del liveCD pero anda sobre cualquier maquina!
De cualquier manera, si queres esperar a que otro aporte algo, dale nomas!
gracias:

estuve viendo en administrador de dispositivos del disco y me aparece esto:

controladoras ide ata/atapi:

intel(r)82801eb ultra ata storage controllers
intel(r)82801eb ultra ata storage controllers
me aparece dos veces, puede ser el problema??

---

### Post by juanma10 on 2009-10-25
> **guillermolisi said:**
> El disco es IDE o SATA ?

Si es IDE, esta como master del canal IDE primario ?
La unidad de CD es IDE o SATA ?

Tenes marca y modelo de la motherboard ?
la marca y el modelo es asrock:

775i65gv el modelo

---

### Post by juanma10 on 2009-10-25
> **guillermolisi said:**
> El disco es IDE o SATA ?

Si es IDE, esta como master del canal IDE primario ?
La unidad de CD es IDE o SATA ?

Tenes marca y modelo de la motherboard ?
hola:

primary ide master: atapi cd-rom


sata1: hard disk

salu2

---

### Post by Geruntu on 2009-10-26
Probaste grabando ubuntu en un cd de ditinta marca al q lo al anterior q grabaste?:P

---

### Post by Fak89 on 2009-10-26
Leí el post y me quedo entendido de que descargaste la imagen de cd de Ubuntu, la descomprimiste e intentaste instalar desde ahí.. esta bien?
Si es así, intentaste grabando la imagen en un cd e instalar desde el cd?

---

### Post by juanma10 on 2009-10-26
> **Fak89 said:**
> Leí el post y me quedo entendido de que descargaste la imagen de cd de Ubuntu, la descomprimiste e intentaste instalar desde ahí.. esta bien?
Si es así, intentaste grabando la imagen en un cd e instalar desde el cd?
si tambien lo grabe y pasa lo mismo
no probe con otro cd

---

### Post by Mauro22 on 2009-10-26
Tendrias que modificar el lanzamiento del menu del cd y agregarle la opcion "nosplash" para que no muestre la barra y ver porqué se traba...


Esto es válido en el livecd??


Otra que se me ocurre es instalarlo con Wubi? -> Descartaría cd y hardware.

---

### Post by juanma10 on 2009-10-26
hola Mauro22
 
tambien lo hize de esa  manera y pasa los mismo
 
puede ser que el ubuntu no sea compatible con el mother asrock y la placa de video geforce???
lei algo por ahi que podria pasar eso.
pero no estoy seguro
 
salu2

---

### Post by Fak89 on 2009-10-26
> **juanma10 said:**
> hola Mauro22
 
tambien lo hize de esa  manera y pasa los mismo
 
puede ser que el ubuntu no sea compatible con el mother asrock y la placa de video geforce???
lei algo por ahi que podria pasar eso.
pero no estoy seguro
 
salu2

No creo, mira, mi compu vieja era una Pentium 4 igual, con una Asrock, 1Gb de ram y una nVidia 5500 y andaba.. a menos que sea por la placa grafica...

---

### Post by guillermolisi on 2009-10-26
La placa es de 128Mb RAM pero no decis nada sobre su marca y modelo.

---

### Post by juanma10 on 2009-10-26
> **guillermolisi said:**
> La placa es de 128Mb RAM pero no decis nada sobre su marca y modelo.
 
 
hola la placa es nvidia geforce 5200

---

### Post by juanma10 on 2009-10-26
> **juanma10 said:**
> hola la placa es nvidia geforce 5200
por otros foros lei que esos dos equipos dan errores.
ademas en la guia de ubuntu, en la compatibilidad con el hardware, no aparecen el mother asrock.
salu2

---

### Post by guillermolisi on 2009-10-26
> **juanma10 said:**
> la marca y el modelo es asrock:

775i65gv el modelo
Esa placa tiene:
> North Bridge:
Intel® 865GV chipset, FSB @ 800 / 533 MHz,
supports Hyper-Threading Technology (see CAUTION 1)
South Bridge:
Intel® ICH5, supports SATA 1.5Gb/s

Ademas, en su manual dice que soporta bien placas nVidia 5200 con 128Mb RAM en su slot AGP (AGI), precisamente habla de AOPEN Aeolus FX5200-V128. con lo cual deberia funcionar razonablemente bien con Ubuntu a menos que estes usando una placa de video cuya implementacion nVidia difiera de la mencionada.

---

### Post by juanma10 on 2009-10-26
> **guillermolisi said:**
> Esa placa tiene:

Ademas, en su manual dice que soporta bien placas nVidia 5200 con 128Mb RAM en su slot AGP (AGI), precisamente habla de AOPEN Aeolus FX5200-V128. con lo cual deberia funcionar razonablemente bien con Ubuntu a menos que estes usando una placa de video cuya implementacion nVidia difiera de la mencionada.
gracias.
lo revisare otra vez.
si eso esta bien, cual podria ser el problema??
salu2

---

### Post by staar on 2009-10-26
otra vez una el dichoso puerto AGI? en estos threads se trata este tema, que tiene solución: [http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi]("http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi")
[http://ubuntuforums.org/showthread.php?t=1237729&highlight=agi]("http://ubuntuforums.org/showthread.php?t=1237729&highlight=agi")

saludos

---

### Post by juanma10 on 2009-10-26
> **staar said:**
> otra vez una el dichoso puerto AGI? en estos threads se trata este tema, que tiene solución: [http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi]("http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi")
[http://ubuntuforums.org/showthread.php?t=1237729&highlight=agi]("http://ubuntuforums.org/showthread.php?t=1237729&highlight=agi")

saludos
hola, gracias por ayudar.
hay que saber algo de linux-ubuntu para solucionar porque veo que aparece otro link.
y soy principiante en esto

---

### Post by staar on 2009-10-26
no es un procedimiento complicado, lo que hay que hacer es quitar y desactivar la placa nvidia, iniciar el ubuntu con la placa intel integrada en el mother, instalarlo normalmente, luego iniciarlo, editar (con permisos de administrador) un archivo de texto, agregar una línea para que no cargue la placa intel, apagar la pc, poner de nuevo la placa nvidia, arrancar ubuntu, y listo :-D

saludos

---

### Post by Fak89 on 2009-10-26
> **staar said:**
> no es un procedimiento complicado, lo que hay que hacer es quitar y desactivar la placa nvidia, iniciar el ubuntu con la placa intel integrada en el mother, instalarlo normalmente, luego iniciarlo, editar (con permisos de administrador) un archivo de texto, agregar una línea para que no cargue la placa intel, apagar la pc, poner de nuevo la placa nvidia, arrancar ubuntu, y listo :-D

saludos

Una pregunta staar, que puede llegar a ser algo obvia. Al hacer esto no queda inhabilitada la placa nvidia? es decir, ubuntu solo usaría la placa onboard..?

---

### Post by guillermolisi on 2009-10-26
> **Fak89 said:**
> Una pregunta staar, que puede llegar a ser algo obvia. Al hacer esto no queda inhabilitada la placa nvidia? es decir, ubuntu solo usaría la placa onboard..?
Si revisas el procedimiento veras que recolocada la placa nVidia esta es reconocida, se instala el driver correspondiente y a partir de ello comenzas a disfrutar a pleno de la aceleracion 3D en Ubuntu :)

Como la placa de video Intel queda en la lista negra (blacklisted) sus drivers/modulos no se cargaran y no habra conflicto con los de nVidia.

---

### Post by juanma10 on 2009-10-27
> **guillermolisi said:**
> Si revisas el procedimiento veras que recolocada la placa nVidia esta es reconocida, se instala el driver correspondiente y a partir de ello comenzas a disfrutar a pleno de la aceleracion 3D en Ubuntu :)

Como la placa de video Intel queda en la lista negra (blacklisted) sus drivers/modulos no se cargaran y no habra conflicto con los de nVidia.
gracias a todos!!!!!!!!!!!!!!!!!!!!!!!!, ya instale el ubuntu
 
me faltaria hacer eso de la blacklist
gracias!!!!!!!!!!!!!

---

### Post by lrcaballero on 2009-10-27
Que tal Juanma?

Yo te recomiendo que vuelvas y bajes un nuevo ISO del distro de tu preferencia en tu caso es Ubuntu 9.04 esto es asi?? quemalo usando imgburner, ya una ves haciendo esto, reinicia tu ordenador pero as el boot-up del cd drive y entra a jugar con el sistema operativo y lo pruebas haber como funciona todo. Ya una vez hayas probado todo corre la instalacion desde el Live CD. Suerte... la perseverancia te da la maestria.....


Luis:KS

---

### Post by juanma10 on 2009-10-27
> **lrcaballero said:**
> Que tal Juanma?

Yo te recomiendo que vuelvas y bajes un nuevo ISO del distro de tu preferencia en tu caso es Ubuntu 9.04 esto es asi?? quemalo usando imgburner, ya una ves haciendo esto, reinicia tu ordenador pero as el boot-up del cd drive y entra a jugar con el sistema operativo y lo pruebas haber como funciona todo. Ya una vez hayas probado todo corre la instalacion desde el Live CD. Suerte... la perseverancia te da la maestria.....


Luis:KS
hola, gracias.
si eso lo probe, y me pasa lo mismo
 
saludos!!

---

### Post by guillermolisi on 2009-10-28
> **juanma10 said:**
> gracias a todos!!!!!!!!!!!!!!!!!!!!!!!!, ya instale el ubuntu
 
me faltaria hacer eso de la blacklist
gracias!!!!!!!!!!!!!
Con esta declaracion se da por resuelto el thread. El resto fue movido a [http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi](http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi)

---

### Post by juanma10 on 2009-10-28
> **guillermolisi said:**
> Con esta declaracion se da por resuelto el thread. El resto fue movido a [http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi](http://ubuntuforums.org/showthread.php?t=1170549&highlight=agi)
hola pero con lo de los drivers coomo puedo hacer?
 
puede ser que no se pueda instalar los drivers definitivamente

---

### Post by guillermolisi on 2009-10-28
> **juanma10 said:**
> hola pero con lo de los drivers coomo puedo hacer?
 
puede ser que no se pueda instalar los drivers definitivamente
Segui el tema en el thread que indique porque la instalacion fue resuelta y lo que te falta no tiene que ver con la instalacion sino con la puesta en marcha de la placa de video, asi que es otro tema relacionado con ese otro thread y no con este.

---

