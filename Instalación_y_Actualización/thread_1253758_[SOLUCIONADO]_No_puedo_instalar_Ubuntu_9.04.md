---
title: "[SOLUCIONADO] No puedo instalar Ubuntu 9.04"
date: 2009-08-30
forum: Instalación y Actualización
---

### Post by cottita on 2009-08-30
oliiiii soy nueva por aca y espero de todo corazon que puedan ayudarme

bueno de verdad que ya no se que hacer con mi pc
antes ya le habia instalado ubuntu 8.10
y resulta que despues de haber pasado unos meses de nuevo con Windows
me aburri y quiero mi pc con Ubuntu otra vez
lo malo es que descargue la nueva version 9.04 y ya la he grabado y descargado como 10 veces... SII tambien probe grabar discos en otro pc pensando que era mi grabador que estaba mal... pero nada
y cuando reinicio el pc, para instalar Ubuntu... algunos CD que grabe no botean y otros que si botea les tira error
toy desesperada
trate de instalar con el CD antiguo de 8.10 y tampoco... se queda mil horas pegado
y me tira error cuando dice Loading Hardware Drivers.... [fail]

estas son las especificaciones de mi pc y ya le he instalado Ubuntu antes y ningun problema, asi que no creo que haya drama con el hardware

Pentium 4 de 2.93 GHz
992 GB de RAM
El sonido y video vienen integrados y son VIA, no es de lo mejor
pero creanme este pc ya a tenido Fedora 10 y Ubuntu 8.10
y sin ningun problema

porfiiiii help me!!! toy que pateo el pc
aaaahhh me faltaba decir que no puedo entrar a la BIOS (por si es que se necesitase) porque tiene una clave que le pusieron en Ripley, que es donde lo compre y por ende jamas me he sabido... asi que olviden a la BIOS
he visto en la web como resetear esa clave, pero me da cuco echarme el pc
asi que mejor la BIOS dejemosla tranquilita
jejejeje

ahora siiiiiiiii HEEEEEELP MEEEEEEEEEE!!!!
tengo el pc con el chanta windows... esperando poder instalar mi Ubuntu
ayudenme!! porfa

---

### Post by AlexDDR on 2009-08-30
como siempre en estos casos , lo primero es empezar a descartar a traves de prueba y error.

1) descartar problemas en el CD, el live cd de ubuntu lo puede comprobar
2) con el mismo live comprueba la ram (tambien en el primer menu que aparece al cargar el live cd.
3) te carga windows?? U otro LINUX actualmente desde el CD en modo live CD?

Seria recomendable que pudiese anotar el error especifico y completo que tira al iniciar, ya sea tomandole una foto o haciendole un video, ya que es raro que no instale ni lo de ahora ni lo de antes

Si le pudiese comprar una tarjeta de video nvidia aunque sea de las mas baratas, y si es AGP talvez consigas una en los sitios de venta online como mercadolibre bien baratas, lo que te permitiria aprovechar mucho mas la potencia de Ubuntu, ya que el vidio tambien acelera el 2d de los programas en la pantalla no solo el 3d de Compiz fusion que tambien ayuda bastante.


BUeno vamos descartando y seguimos con esto, necesitamos toda la info que pueda ser relevante


saludos

---

### Post by cottita on 2009-08-30
yap dire todo mas ordenado

1. tengo 3 CD con el 9.04 grabado, 2 de ellos no andan, es decir, yo pongo el CD y al botear ni siquiera los identifica e inicia simplemente a windows. El otro CD si inicia, pero ya sea en la opcion instalar o en la opcion probar ubuntu, me dice aparece una ventanita que dice Error Boot con un boton que dice Reiniciar.

2. Por otro lado tengo mi CD antiguo de Ubuntu 8.10, que cuando le pido que lo instale, aparece como cargando el ubuntu, luego de unos 40 min (sii, mucho tiempo) empieza a cargar y al final dice Loading Hardware Drivers... [[COLOR=Red]fail[/COLOR]]

3. los ISO los baje por torrent y por FTP, estan quemados con Nero a 10x
voy a tratar de quemarlos a 4x, para ver si algo cambia.

En cuanto pueda comprare una NVIDIA, se que mi pc me lo agradecera :P

en realidad no se que podra ser :confused:

---

### Post by AlexDDR on 2009-08-30
raro es, pero puedes iniciar windows mi imagino??


podrias probar  instalarlo dentro de windows , con wubi, que viene el el cd de ubuntu , asi instala una particion virtual dentro de la de windows que no es lo ideal pero si funciona, es cosa de probar. Solo debes ejecutar el instalador dentro de windows, si es que el auto arranque no lo auto ejecuta.

o talvez crear un pendrive con la instalacion , pero como no hay acceso a la bios talvez no funcione, si es que no viene bien configurada, pero generalmente en el boot las placas madres dan la opcion de elegir la unidad de boteo, es cosa de probar con un pendrive de 1Gb o mas


Saludos

---

### Post by bichopro on 2009-08-30
Es por alguna razon un olidata?
si es asi la clave de la bios deberia ser olipro. asi podrias intentarlo desde un pendrive
no entendi si probaste la version para instalar en modo live cd osea cargando el escritorio o desde la opcion instalar donde solo carga el instalador.
En la version live cd donde carga el escritorio tambien puedes hacer la instalacion.

---

### Post by cottita on 2009-08-30
tengo una buena y una mala noticia
la buena noticia es que el CD funcionó, incluso ahora mismo estoy "probando ubuntu sin alterar el sistema"

yaa y todo muy lindo... peeeero
cuando ya le había puesto instalar
hice las particiones y todo
llevaba 94% y me dice que no puede instalar Grub
y quedé :confused:

emmm siii el pc el Olidata, traté con la clave que me diste pero me dijo que NONES!

any idea?!?!?!?!

en serio... estoy que le prendo fuego al pc ¬¬

---

### Post by AlexDDR on 2009-08-30
en internet sale que todos los pc olidatas tiene la clave "olipro" pero que si puede llamar al callcenter de olidata y te la dan


otra cosa es sacar la pila de la placa madre y puede que la pierda


pero sigo creyendo que el tema es el lector de cd de tu computador esta defectuoso y algunas veces lee bien y otras mal, incluso puede ser la marca del cd que no los lea bien, ya que no me confiaria mucho de la calidad de los lectores que pone olidata (sorry)


con que programa grabas la iso?

---

### Post by cottita on 2009-08-30
it works!!! finally!!!

:KS ahora siiiiiiiiiiiiiiiiiiii ^^

Les cuento lo que hice para arreglar el GRUB
San Google me contó que GRUB tenía que ver con el arranque
así que casi al final de la instalación, cuando entrega el resumen
puse Avanzado y ahí puse que instalara el GRUB en la partición "/"
no sé si se entiende... según lo que leí, el error es que el GRUB no sabe donde instalarse
algo así... el punto es que funcionó, lo único que quedó extraño fue al inicio
que pone una pantalla azul [como la de la BIOS] y me dice:

Ya existe un servidor X en ejecución en la pantalla :0 Desea intentar otro numero de pantalla? si responde no, GDM volverá a intentar iniciar el servidor en :0 otra vez...

la cosa es que si pongo Si... sale una y otra vez la pantalla azul
y si pongo No, busca en otro "servidor" y comienza ubuntu...

no sé que será eso... pero la cosa es que el SO funciona por lo menos ^^

si alguien sabe como arreglar eso... bienvenido sea...

y toda la razón Alex, definitivamente mi lector está muriendo... si el pc ya tiene sus años... creo que tendré que cambiarle varias cosas...
de todas formas viene un macbook en camino :) pero dejaré mi pc de escritorio con Ubuntu y usaré mi macbook y adios Window$
muahahahaha 

gracias por todo!!!

---

### Post by uylug on 2009-08-30
Que suerte que por lo menos lo hiciste andar. Pero tambien podes probar a instalarlo desde un USB?

Si tenes uno, podes probar con unetbootin

```
sudo apt-get install unetbootin
```

Suerte!!

---

### Post by Patriciologico on 2009-08-31
> **cottita said:**
> it works!!! finally!!!

:KS ahora siiiiiiiiiiiiiiiiiiii ^^

lo único que quedó extraño fue al inicio
que pone una pantalla azul [como la de la BIOS] y me dice:

Ya existe un servidor X en ejecución en la pantalla :0 Desea intentar otro numero de pantalla? si responde no, GDM volverá a intentar iniciar el servidor en :0 otra vez...

la cosa es que si pongo Si... sale una y otra vez la pantalla azul
y si pongo No, busca en otro "servidor" y comienza ubuntu...

no sé que será eso... pero la cosa es que el SO funciona por lo menos ^^

si alguien sabe como arreglar eso... bienvenido sea...

Hola cottita, me alegro que ya este instalado, sobre tu otro problema, debes abrir un nuevo Thread, para no confundir los temas, 

Saludos!

---

