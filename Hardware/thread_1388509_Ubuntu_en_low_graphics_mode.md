---
title: "Ubuntu en low graphics mode"
date: 2010-01-23
forum: Hardware
---

### Post by Applelnx on 2010-01-23
Hola, el otro dia reinicie la maquina y no se por que me salto el siguiente error:

```
The following error was encountered. 
You may need to update your configuration to solve this.

(EE) [drm] drmOpen failed.
(EE) fglrx(0): DRIScreeninit failed!
```

A alguno le paso algo similar y sabe que hacer? Saludos

---

### Post by Applelnx on 2010-01-25
Me olvide de decir que corre Ubuntu en "low graphics mode". Tengo los drivers privativos bajados de la pagina oficial de ATI.

---

### Post by luks911 on 2010-01-25
Mmm... ¿alguna actualización del kernel? ¿Probaste reinstalando los drivers?

---

### Post by Applelnx on 2010-01-25
Hola luks. La verdad que no quise hacer nada por las dudas, porque siempre que toco algo de los graficos me sale mal. Al parecer del error que me salto al abrir el ATI Catalyst Center (ver screen), tengo que reinstalarlos. Hago una pregunta: si los desinstalo vuelven los drivers default de Ubuntu? 

[ATTACH]144984[/ATTACH]

---

### Post by luks911 on 2010-01-25
Lo que te dice el error es que no están instalados los drivers propietarios. 
Se supone que ya están desinstalados. Ahora, hay que ver cómo se lleva tu placa con los drivers que vienen con Ubuntu que son libres. Por lo que decís no funciona, por eso te deja en low graphics mode.
Creo que las opciones son: 1) instalar los drivers privativos que ofrece Ubuntu, en Sistema > Administración > Controladores de Hardware, 2) instalar los privativos descargados de la página de ATI o 3) usar envy. En la máquina de un amigo fue la última opción la que me dejó los drivers instalados y andando. No sé por qué, pero por más que seguía las guías para instalar los de ATI o los de Ubuntu nunca quedaban funcionales.

---

### Post by Applelnx on 2010-01-25
Los del repositorio de Ubuntu me han hecho desastres. Los default de Ubuntu me funcionaban apenas lo instale. Por ultimo, si voy a usr/share/ati ahi estan todos los archivos instalados. Voy a intentar reinstalarlos y vere que tanto lio hago.

---

### Post by Applelnx on 2010-01-25
Reinstalados y funcionando perfecto :D
Muchas gracias!

---

### Post by guillermolisi on 2010-08-14
> **Darfeynt said:**
> [SIZE=3]hey gente de ubuntu me pueden dar una mano con eso de los controladores.
yo he intentando dandole clic en sistema[/SIZE],  [SIZE=3]luego en administracion, y por ultimo en controladores de hardware, el detalle es que solo me encuentra el controlador de video[/SIZE], [SIZE=3]entonces no se si tengo que buscar por otro lado para poder encontrar los otros controladores del procesador, lan, audio entre otros.[/SIZE]
[SIZE=3]sera que ya ubuntu los incluye?[/SIZE] [SIZE=3]porcierto en su opinion que quemador de isos les parece bueno?[/SIZE]

[SIZE=3]bueno eso es todo, un saludo desde colombia[/SIZE]..
[SIZE=3]todo bien se cuidan[/SIZE]
No podes postear en todo thread que exista ni en este subforo ni en UbuntuForums.

Tenes que elegir un thread o abrir uno nuevo, si tu tema no fue tratado, pero solo uno ya que las respuestas se diluyen y no se concentran en un solo caso.

Gracias por considerar esto para futuros mensajes.

---

