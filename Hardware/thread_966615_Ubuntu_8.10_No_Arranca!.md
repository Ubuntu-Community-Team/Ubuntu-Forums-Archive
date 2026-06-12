---
title: "Ubuntu 8.10 No Arranca!"
date: 2008-11-01
forum: Hardware
---

### Post by acade07 on 2008-11-01
Saludos a todos soy nuevo en el foro y les comento mi problema.
Despues de instalar Ubuntu8.10 (instalacion desde cero como las anteriores versiones de Ubuntu) no lo carga, dejandome este mensaje:

"kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)"

...y me quede ahi sin conocer todabia mi Ubuntu 8.10. :( 
Bueno si alguien tiene el mismo problema estaria bueno q lo comenten Saludos!


In English: 
My Ubuntu 8.10 Not load before instalation...
This is the message I can see:

"kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)"

---

### Post by ENigma885 on 2008-11-01
Posting ur problem in _English_, or even trying to do so, will increase ur chance of having a quick reply.

---

### Post by clasificado on 2008-11-01
> **ENigma885 said:**
> 
"kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)".

Es un conocido error del kernel, Ya nos habia pasado con la versión breezy hace un par de años, ¿será que volvió?

Te diria que trates de iniciar el sistema con una versión anterior del kernel.

UCH! ahora que leo bien, es una instalación de cero :P

Tengo una pregunta: ¿el Live CD arranca?

clasificado

---

### Post by acade07 on 2008-11-01
> **clasificado said:**
> Not here, ENigma885. This is the Argentina LoCo Team and its ok to speak in spanish ;)


Es un conocido error del kernel, Ya nos habia pasado con la versión breezy hace un par de años, ¿será que volvió?



Nunca tuve este problema con ninguna de las versiones anteriores y eso q la uso desde la 5.10

Los problemas empezaron cuando quise probarlo sin instalarlo (live CD) y quedaba en una parte q decia "Staring Bluetooth"
Hasta q descubri q era por el modem Speedtouch 330 pero problema q no surgia en ninguna de las versiones anteriores, por eso me extraña q pase esto en esta nueva version.

Despues de desconectarlo (al modem) decidi instalarlo como siempre, como todas las versiones anteriores...dejar un espacio sin particionar y usar le espacio libre contiguo (opcion en el proceso de instalacion)

Todo bien hasta el momendo de reiniciar y q arranque...pero no arranca obvio.
Sera un problema de incompativilidad con mi mother ASUS A7v8x-x?
Saludos!

---

### Post by sam_award on 2008-11-01
mira si arranca desde al live cd , ps ya la hiciste , prueba instalando una vercion anterior , cn el hardy. y si tanto te interesa el intrepid , es igual al hardy , nomas tiene una q otra mejorilla, y ps puedes actualizar al intrepid desde el hardy , y pues suerte

---

### Post by acade07 on 2008-11-01
> **sam_award said:**
> mira si arranca desde al live cd , ps ya la hiciste , prueba instalando una vercion anterior , cn el hardy. y si tanto te interesa el intrepid , es igual al hardy , nomas tiene una q otra mejorilla, y ps puedes actualizar al intrepid desde el hardy , y pues suerte

Esa seria la solucion mas facil..pero hasta q no me digan "Es incompatible con tu PC" seguire buscando la solucion... 
ya q esta paso la configuracion de mi pc.

Amd sempron 2500+ 1Gb ram ddr
Asus a7v8x-x Nvidia 5200 128mb

Saludos y gracias!

---

### Post by acade07 on 2008-11-01
> **sam_award said:**
> mira si arranca desde al live cd , ps ya la hiciste , prueba instalando una vercion anterior , cn el hardy. y si tanto te interesa el intrepid , es igual al hardy , nomas tiene una q otra mejorilla, y ps puedes actualizar al intrepid desde el hardy , y pues suerte

Esa seria la solucion mas facil..pero hasta q no me digan "Es incompatible con tu PC" seguire buscando la solucion... 
ya q esta paso la configuracion de mi pc.

Amd sempron 2500 (1.750)+ 1Gb ram ddr
Asus a7v8x-x Nvidia 5200 128mb

Saludos y gracias!

---

### Post by acade07 on 2008-11-01
> **sam_award said:**
> mira si arranca desde al live cd , ps ya la hiciste , prueba instalando una vercion anterior , cn el hardy. y si tanto te interesa el intrepid , es igual al hardy , nomas tiene una q otra mejorilla, y ps puedes actualizar al intrepid desde el hardy , y pues suerte

Esa seria la solucion mas facil..pero hasta q no me digan "Es incompatible con tu PC" seguire buscando la solucion... 
Ademas temo q si alctualizo desde Hardy aparezca el mismo error ya q se actualizaria el kernel.

Ya q esta paso la configuracion de mi pc.

Amd sempron 2500 (1.750)+ 1Gb ram ddr
Asus a7v8x-x Nvidia 5200 128mb

Saludos y gracias!

---

### Post by faktorqm on 2008-11-03
> **ENigma885 said:**
> Posting ur problem in _English_, or even trying to do so, will increase ur chance of having a quick reply.

Never will be increase your chance of having a quick reply in this forum. We talk Spanish, and some not understand the english language. More faster in spanish.... ;) 


Nunca incrementara sus chances de tener una rapida respuesta en este foro. Hablamos español, y algunos no sabe ingles. Mas rapido en español... ;) y quedate piyo, no armes bondi por que se te pudre! jajaja

---

### Post by acade07 on 2008-11-04
Bueno me repondo a mi mismo jaja..
Descubri cual era la falla de este error:
"kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)"
El problema era q yo habia dejado la particion de intercambio de Hardy (8.04) y cuando Intrepid cargaba aparentemente tomaba la de hardy y no la propia de el.
Lo solucione borrando las particiones de intercambio y dejando un solo espacio no particionado. 
Instale Ubuntu 8.10 y ahora si arranca...
Ahora solo me queda hacer andar el Modem Usb Speedtouch330 q no me deja cargar ubuntu (si esta conectado),y q por ahora no puedo configurarlo para conectarme.
Saludos!

---

### Post by acade07 on 2008-11-04
Bueno ya escribiendo de Ubuntu 8.10 :p
Para quienes Tengan el Modem Usb Speedtouch330 lean el post siguiente para q les funcione ya q hay un bug reportado con este Modem Usb
[http://ubuntuforums.org/showthread.php?t=964772](http://ubuntuforums.org/showthread.php?t=964772)
Saludos!

---

