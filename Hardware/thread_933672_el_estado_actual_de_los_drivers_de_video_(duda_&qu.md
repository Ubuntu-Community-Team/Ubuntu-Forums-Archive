---
title: "el estado actual de los drivers de video (duda &quot;filosófica&quot;)"
date: 2008-09-29
forum: Hardware
---

### Post by Kantier on 2008-09-29
me agarró la duda... ¿qué onda los drivers de ati hoy día?

Hasta hace no mucho, en ati los drivers linuxeros eran casi inexistentes. hace poco leí que estaban laburando con una capa de abstracción para hacer un mismo driver para todas las placas... pero ni idea si ya andan bien o todavía les falta.

¿alguna experiencia para comentar? (por favor absténganse de los "me comentaron que..." - si no lo vieron en persona, link o no existe.)

---

### Post by leo_rockway on 2008-09-29
El driver privativo se puede decir que funciona bien (no quiero afirmarlo definitivamente porque no tengo una ATI de cada modelo, yo hablo por experiencia con mi placa). De todas formas yo tenía que usar una versión en particular (creo que de mayo) porque las nuevas versiones hacían que X se volviese loco cuando quería reproducir algun video.

Yo ahora estoy usando uno de los drivers libres (radeonHD) y no tengo aceleración 2D ni 3D, pero al menos funcionan con mi placa (antes no levantaban nada). Ciertas placas ya tienen aceleración 2D y 3D, pero no funcionan ambos tipos de aceleración al mismo tiempo. Para uso diario de aplicaciones que no sean juegos (por el tema de la aceleración) a mi me andan muy bien. Ciertas aplicaciones 3D que no necesitan aceleración por hardware también me andan bien (Blender, Marble).

No sé como funciona ninguno de los drivers con dos monitores o salida de TV porque nunca probé esas cosas.

Si tenés alguna duda preguntame y te contesto, no sé que otras cosas te pueden llegar a interesar puntualmente.

---

### Post by zeroadrenaline on 2008-09-29
El driver de la ati mobility radeon x1400 8-6 es el mejorcito que prove, tube el 8-7 y no recuerdo si sacaron el 8-8 . pero con el 7 mil bardos, estan laburando bastante, funcionan bien, y sacan actualizacion cada 3 o 4 meses.
Al aprecer se estan poniendo las pilas.
Yo probe la salida para dos monitores, y con el 8-6 funciona perfectirijillo!.

---

### Post by leo_rockway on 2008-09-29
ATI Radeon Mobility x1400 es la que tengo yo.
Vi el avance que tenían los drivers libres y como los drivers privativos seguían haciendo prueba y error con unos bugs muy obvios me cansé y decidí instalar los libres (que además es una de las pocas cosas privativas que tenía, ahora sólo me queda el firmware de la placa wifi).
Las actualizaciones del privativo salen exactamente una vez por mes (lo tengo en Akregator ;- ) )

---

### Post by pol666 on 2008-09-29
No se yo uso Nvidia (privativos) y andan mas que bien, los libres andan bien a pesar de no proveer acelaracion 3D.

La unica vez que instale Ubuntu en una ATI, la reconocio automaticamente, creo que tenia acelaracion 2D pero no 3D. Por lo menos no  me preocupe en lograrlo, Simplemente saque el ubuntu. por que no andaba el wireless y no era mi PC como para seguir intentando en ello.

---

