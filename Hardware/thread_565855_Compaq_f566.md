---
title: "Compaq f566"
date: 2007-10-02
forum: Hardware
---

### Post by Apipote on 2007-10-02
Alguien sabe si anda bien con ubuntu??
Viene con Vista y me horroriza siquiera el prenderla.
Saludos.

---

### Post by leo_rockway on 2007-10-02
estas son las compaq del Laptop Testing Team: [https://wiki.ubuntu.com/LaptopTestingTeam/Compaq](https://wiki.ubuntu.com/LaptopTestingTeam/Compaq)

fijate si alguna de esas se parece a la tuya.

---

### Post by Apipote on 2007-10-02
No Leo que lastima, es nueva esta, sera por eso.
Gracias igual.

---

### Post by sajnox on 2007-10-02
Hola,

Mi mujer tiene una compaq F505 (creo que son de la misma linea) no tienen problemas con Ubuntu salvo en el inicio con el Live CD, tenes que elegir other options y agregar a vga=0

Con eso arranca, instalas Ubuntu y le cargas los drivers propietarios de Nvidia (por lo menos las de mi mujer trae una placa Nvidia)

Fijate y nos contas

---

### Post by LaHire on 2007-10-02
Indeed, 

incluso la gran mayoría de las Compaq tienen que ser instaladas con el CD Alternate de Ubuntu...o con la opción "vga=0" en "Other Options"

mi padre tiene una notebook similar (tambine Compaq HP)  y tiene ese mismo problema (aunq ya no porq le borré el Bad Vista y le metí un 7.04 sin siquiera tibutear)...


Espero q se solucione!

---

### Post by niko_3100 on 2007-10-02
Yo tengo una compaq v3415 con feisty y la verdad que no tube problemas con la resolucion lo unico que funciona a 50 hz y no a 60 hz como es normal pero se ve de diez igual. El unico problema fue el wifi broadcom pero con wine salio andando.

---

### Post by Apipote on 2007-10-03
Ok, bueno cuando me la entreguen les cuento.
Otra cosa, no perdere la garantia borrando el maldito vista?. 
Entiendo que ya viene instalado y no trae ningun disco aparte.
Slds

---

### Post by sajnox on 2007-10-03
Asi es viene instalado y sin disco, lo que trae es una particion desde la cual podes recuperar el sistema, mientras que no borres/deshagas esa particion mantenes el vista.


Saludos

---

### Post by Apipote on 2007-10-03
Sajnox
Podria de alguna manera hacer un back up de ese vista "para recuperacion" que trae en esa particion a un dvd y eventualmente reinstalarlo de ahi?

---

### Post by vk-cdg on 2007-10-03
Las notebooks suelen tener, al menos las HP, una utilidad dentro del menú de la PC (a veces es por soft, a veces por bios) para bajar a DVD esa partición.
De esa manera, si el disco de daña, tenés todavía esa opción de recuperación una vez que te cambiaron el disco.

Buscalo que debe estar por ahí.

---

### Post by Apipote on 2007-10-03
Gracias Vk !!

---

### Post by sajnox on 2007-10-03
> **vk-cdg said:**
> Las notebooks suelen tener, al menos las HP, una utilidad dentro del menú de la PC (a veces es por soft, a veces por bios) para bajar a DVD esa partición.
De esa manera, si el disco de daña, tenés todavía esa opción de recuperación una vez que te cambiaron el disco.

Buscalo que debe estar por ahí.

Ojo cuando lo haces, por que creo que te permite hacer un solo Backup

---

### Post by Apipote on 2007-10-06
Si Sajnox, haria un solo backup a un dvd y con eso me manejaria.
Ha tenido tu mujer problemas con el wifi ?

---

### Post by daz! on 2007-10-07
Yo tengo una Compaq v3000 (3515la creo) y lo primero que hice fue el back up de compaq (9 discos!!!!) y lo segundo instalé el Feisty sin problemas, es más me resultó más fácil que en mi PC.  

Con los drivers de Nvidia si tuve problemas pero mas que nada por mi inutilidad. Y el wirless todavía no lo configuré pero hay varios tutos dando vuelta al respecto 

Supongo que la garantía te la tendrían que reconocer igual ya que si se te rompe el hardware no veo que tenga que ver con el soft que le pongas. En todo caso, si tenés vista, tampoco podrías instalar ningún programa adicional. Me parece ridículo

Pero como la ridicules y la trampa no tienen límites:  

Acá tenés un caso de robo al comsumidor 
[http://www.theinquirer.es/2007/03/28/si_instalas_linux_en_tu_hp_olv.html](http://www.theinquirer.es/2007/03/28/si_instalas_linux_en_tu_hp_olv.html)

Acá tenés otro: 
[http://www.theinquirer.es/2007/09/12/no_le_reparan_el_ordenador_por_haber_instalado_linux.html](http://www.theinquirer.es/2007/09/12/no_le_reparan_el_ordenador_por_haber_instalado_linux.html)

Estoy convencido que siempre van a tener  una  excusa para no reconocerte la garantía, tengas vista o no. 

Suerte! 

Damian

---

### Post by Apipote on 2007-10-07
Si, no me cabe duda, siempre te *****.
Ahora bien, si hago un backup y luego instalo ubuntu, y eventualmente necesito la garantia........reinstalo vista y listo.
Es factible?

Wiifi, es fundamental para mi. si alguien me dice que anda bien, ni lo dudo, le meto el 7.10.

---

### Post by Apipote on 2007-10-08
Hay alguien ahi??
:(

---

### Post by sajnox on 2007-10-08
> **Apipote said:**
> 
Wiifi, es fundamental para mi. si alguien me dice que anda bien, ni lo dudo, le meto el 7.10.

Se que esa maquina es mañosa con los drivers wi fi...

Leo_rockway y (ahora no me acuerdo el nombre) estuvieron configurando una en la cafeconf...a ver si dan un mano

Saludos

---

### Post by niko_3100 on 2007-10-08
Si tu wifi es broadcom tenes que instalar los drivers de xp con wine y aderirlos al kernel, creo que era asi si queres te paso un how to.

---

### Post by leo_rockway on 2007-10-08
yo habia posteado un msg hermoso aca (o quizas me haya olvidado de apretar "post quick reply"... jaja)

el chico que mas se encargo del tema del wifi fue lucas. igualmente el que al final logro solucionarlo fue alguien de solar (porque se necesitaba conexión a internet... el creo que uso un adaptador usb)

la placa es una broadcom 3900, no? si no me equivoco habia un howto en el wiki de ubuntu. igual la onda es usar el ndiswrapper y el driver de win (me imagino que no es nada complicado)

---

### Post by Apipote on 2007-10-09
Gracias chicos, veremos como se porta con Gusty. 
No me gusta mucho la opción del wine.
Supongo que a la larga se solucionará.
Slds.

---

### Post by daz! on 2007-10-09
MIrá con respecto a restaurar el sistema con los discos de bkup, te cuento mi parecer. 

Yo busqué una Notebook sin SO porque instalarle ubuntu era "natural" para mi, o sea, no se me ocurre tener un Vista. El bkup lo hice porque pagué la licencia del SO y por el tema de la garantía. Pensé: " si alguna vez tengo problemas de hard y me piden vista por la garantía, bueno, se lo instalo". 

El problema es si se me rompe la lectora de CD!!!! :) Estoy hasta las manos!!! (dicho sea de paso es bastante frágil) 

No creo que lo vaya a usar así que no tuve remordimientos para formatear el disco :) JE! 

Además ahora Microsoft está ofreciendo hacer un downgrade a XP!! Así que imagináte qué se puede esperar de Vista.  

Saludos.

---

### Post by Apipote on 2008-06-22
Hola estimados
Como Uds ya saben, tengo una notebook antilinux, compaq f566la. De hecho, creo que todas las comapq y hp, lo son.
Este finde, me quede solo en casa y sin chicos ( placer de dioses ) e instale suse 11.0 ambas versiones i386 y x64, con kde4 y gnome. No solo que no reconocia mi asquerosa broadcom 4311, si no que a los 5 minutos cuelgues inexplicables.

Me fuí a Fedora 9.0 gnome...un poco mejor, pero al actualizar los drivers nvidia, otra vez los cuelgues. De la broadcom...ni pude intentar hacer algo. Aunque supuestamente y partiendome la cabeza podria hacerla funcionar con el kernel 2.6.25.

De nuevo a mi viejo y cada vez querido xp sp3...siempre anda todo y nunca falla.

Slds a todos

---

### Post by Mauro22 on 2008-06-22
Proba con Mandriva....   En mi pc anda mejor que Ubuntu. Y eso que ubuntu ada de 10!

:popcorn:

---

### Post by vk-cdg on 2008-06-22
Si, coincido con Mauro, en mi desktop, Mandriva detecta mejor algunas cosas que Ubuntu, como ser mi sintonizadora de TV.

---

### Post by Apipote on 2008-06-23
Pude instalar finalmente luego de actualizar los mas de 200 mb, los drivers de la broadcom en mi compaq f566la antilinux en Hardy.

Se prende la luz azul de la wifi, veo todas las conexiones perifericas a mi casa, incluso mi acces point con buena señal.
Pero no entiendo porque me conecto SIN actividad ( 0 % ) ,no anda internet y el pppoeconf se cuelga.

Si desconecto la wifi broadcom 4311, el pppoeconf...reconoce la ethernet y estoy escribiendo esto.

Es cosa de mandinga...ayudenme por favor !!

Saludos y gracias

---

### Post by faktorqm on 2008-06-23
Debes tener configurado el modem de adsl en modo router o si pusiste el modem adsl y atras un router wifi se esta conectando el router por vos. Si no es asi describi mejor tu problema a ver si te podemos ayudar. Salu2!!

---

### Post by Apipote on 2008-06-24
No entiendo bien Faktorqm. Te digo que si booteo con xp andan perfecto ambas conexiones.

El tema está en los drivers de Ubuntu o yo que no hago bien algo.
Las tengo a ambas conexiones como "roaming".

Intuyo que es una pelotudez

Alguna sugerencia?

Gracias.

---

### Post by niko_3100 on 2008-06-24
La placa wifi broadcom son un dolor de cabeza bajo ubuntu yo en mi anterior compaq v3415 tube que instalarla mediante ndiswrapper y los drivers de windows xp que.... esa no es la idea pero era la unica solucion, pero despues lo mejor es que tenia mejor señal que en xp jeje.

---

### Post by Apipote on 2008-06-25
> La placa wifi broadcom son un dolor de cabeza bajo ubuntu yo en mi anterior compaq v3415 tube que instalarla mediante ndiswrapper y los drivers de windows xp que.... esa no es la idea pero era la unica solucion, pero despues lo mejor es que tenia mejor señal que en xp jeje.

Y que lo digas, Google te tira miles de dramas con esa placa de ******. No se porque la usan tanto los fabricantes.

El Ndiswrapper no me convence, esperaría en todo caso a ver que pasa con intrepid. Lo tienen que solucionar con el kernel 2.6.25, porque irónicamente miles de notebooks tienen esa placa horrenda.

Slds

---

### Post by niko_3100 on 2008-06-25
mi nueva msi tiene una ralink que levanto de una, es muy buena tambien y creo que en la pagina oficial tienen soporte para linux.

---

