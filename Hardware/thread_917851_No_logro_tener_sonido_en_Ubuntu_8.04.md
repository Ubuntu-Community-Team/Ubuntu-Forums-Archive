---
title: "No logro tener sonido en Ubuntu 8.04"
date: 2008-09-12
forum: Hardware
---

### Post by wild-days on 2008-09-12
[B]Hola gente me presento me llamo Hernan y soy nuevo en la comunidad, durante cadi toda mi vida utilice windows pero harto de llenarme de problemas virus y de ver como microsoft te imposibilita que aprendas como controlar el SO decidi pasamr a Ubuntu ya que lei muy buenas criticas sobre este, y que sinceramente estoy de acuerdo en que es un mundo diferente y que propone un desafio a los conocimientos de cualquiera.
Bueno voy al tema en concreto, justamente como propone un desafio se me ha estad ocomplicando la cosa consegui el ubuntu en un CD lo instale (si mal no recuerdo era la version 6.10 o algo asi, lo actualice a la 8.04 pero no me anda el sonido, y con la version anterior si me andaba. no logro hacer que ande me reconoce la placa y todo esta copnfigurado el volume al tope pero no sale ningun sonido .
Si necesitan que pegue algo diganme y yo con gusto pasa que no se que mostrar porq les repito esto es nuevo para mi.

Agradezco de antemano la ayuda que puedan facilitarme y aviso, que esta no es la unica consulta :P pero estableci prioridades

Saludos

Nan[/B]

---

### Post by sajnox on 2008-09-12
Bienvenido,

Primero necesitamos saber que placa de sonido tenes, abri una terminal y ejecuta

```
asoundconf list
```

Lo que devuelve copialo y pegalo aca para que veamos como podemos ayudar

Saludos

---

### Post by wild-days on 2008-09-12
casa@casa-desktop:~$ asoundconf list
Names of available sound cards:
CS46xx
V8235
casa@casa-desktop:~$ 



Eso es lo que me aparece cuando ingreso el comando. La de abajo es la que viene con el mother un mother Biostar M7vig 400 y la otra es una que le puse yo.

Muchas Gracias espero respuestas!! 

Saludos

---

### Post by leo_rockway on 2008-09-12
Esto es lo que encontré sobre esa placa: [http://www.uluga.ubuntuforums.org/showthread.php?t=249822](http://www.uluga.ubuntuforums.org/showthread.php?t=249822)

EDIT: pequeño detalle, wild-days me pasó por IRC el modelo de la placa. Es este: ```
00:0a.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
```

El modelo de la placa del link que dejé yo no es exactamente igual, pero quizás pueda servir.

---

### Post by wild-days on 2008-09-13
Leo te agradezco la informacion, les cuento que cree el archivo que decia en ese foro y lo guarde reinicie pero no parece haber cambios, se reconoce todo correctamente pero el parlante no emite sonidos...
Es frustrante porque tengo todo funcionando al pelo pero el audio que es una de las cosas que mas uso no anda.

Por favor AYUDAA!!!! ...

---

### Post by faktorqm on 2008-09-13
Hola y bienvenido a la comunidad.
Deshabilitaste la placa de sonido on-board desde el setup del bios? eso es importante.
Si ya lo hiciste, fuiste a sistema -> preferencias -> sonido y te fijaste con que servidores estas trabajando? yo por ejemplo tengo todo en autodetectar, pero podrias poner ALSA (Advanced Linux Sound Architecture) y probar desde ahi, a ver cual es el que suena. y bueno, ahi tenes varias cosas para tocar, que se yo. Despues si no te anduvo anda de esto postea. salu2!

---

### Post by sajnox on 2008-09-13
Me estan convenciendo.......

---

### Post by wild-days on 2008-09-13
Bueno gente de la comunidad de Ubuntu, logre solucionar el problema, era exactamente eso, solo tenia que deshabilitar la onboard en el bios, no se porque no lo hice antes, asi que ya esta el sonido andando, les agradezco muchisimo a los que me dieron una mano, y no va a ser la ultima vez que les pida una mano.

Soy nuevo en Linux pero mi deseo es aprenderlo a fondo y poder ayudar con lo que sepa!!.

Nuevamente Gracias a todos , thread solucionado!!! :):):)
Saludos a Todos.

NaN

---

### Post by leo_rockway on 2008-09-13
> **wild-days said:**
> solo tenia que deshabilitar la onboard en el bios

Fue lo primero que te comenté por IRC, pensé que lo habías probado en ese momento cuando reiniciaste.

---

### Post by wild-days on 2008-09-13
Bueno crei que mi problema estaba solucionado pero todavia no. Si bien tengo sonido, no es bueno, cuando estoy viendo un video en you tube o pongo una cancion en el Amarok pega como saltos el sonido... la calidad es muuy baja se escucha con interferencia y a cada rato saltea de una parte de la cancion a la otra.. porque puede ser?!!! :|

AYUDA!

---

