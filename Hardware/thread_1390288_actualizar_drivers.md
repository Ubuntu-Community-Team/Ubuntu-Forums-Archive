---
title: "actualizar drivers"
date: 2010-01-25
forum: Hardware
---

### Post by Hefestos on 2010-01-25
hace unos dias que me cambie a ubuntu y por falta de experiencia no se como actualizar, o que drivers usar para este sistema operativo, alguien seria tan amable de indicarme cual programa descargar para actualizar mi pc?¡, o como actualizar los controladores?¡

intente ya con el drivergen... pero unicamente tiene opciones para windows... 

un saludo y espero que alguien me pueda ayudar

---

### Post by juancarlospaco on 2010-01-25
[B]Sistema--->Administracion--->Gestor de Actualizaciones

Boton "Comprobar"

Boton "Instalar Actualizaciones"[/B] *(si aplica)*

:)

---

### Post by luks911 on 2010-01-25
> **Hefestos said:**
> hace unos dias que me cambie a ubuntu y por falta de experiencia no se como actualizar, o que drivers usar para este sistema operativo, alguien seria tan amable de indicarme cual programa descargar para actualizar mi pc?¡, o como actualizar los controladores?¡

intente ya con el drivergen... pero unicamente tiene opciones para windows... 

un saludo y espero que alguien me pueda ayudar
¿Te hace falta algún controlador? ¿Hay algún hard que no funcione correctamente? ¿Placa de video, wifi, etc?

---

### Post by Darfeynt on 2010-08-14
[SIZE=3]hey gente de ubuntu me pueden dar una mano con eso de los controladores.
yo he intentando dandole clic en sistema[/SIZE],  [SIZE=3]luego en administracion, y por ultimo en controladores de hardware, el detalle es que solo me encuentra el controlador de video[/SIZE], [SIZE=3]entonces no se si tengo que buscar por otro lado para poder encontrar los otros controladores del procesador, lan, audio entre otros.[/SIZE]
[SIZE=3]sera que ya ubuntu los incluye?[/SIZE] [SIZE=3]porcierto en su opinion que quemador de isos les parece bueno?[/SIZE]

[SIZE=3]bueno eso es todo, un saludo desde colombia[/SIZE]..
[SIZE=3]todo bien se cuidan[/SIZE]

---

### Post by Darfeynt on 2010-08-14
[SIZE=3]hey gente de ubuntu me pueden dar una mano con eso de los controladores.
yo he intentando dandole clic en sistema[/SIZE],  [SIZE=3]luego en administracion, y por ultimo en controladores de hardware, el detalle es que solo me encuentra el controlador de video[/SIZE], [SIZE=3]entonces  no se si tengo que buscar por otro lado para poder encontrar los otros  controladores del procesador, lan, audio entre otros.[/SIZE]
[SIZE=3]sera que ya ubuntu los incluye?[/SIZE] [SIZE=3]porcierto en su opinion que quemador de isos les parece bueno?[/SIZE]

[SIZE=3]bueno eso es todo, un saludo desde colombia[/SIZE]..
[SIZE=3]todo bien se cuidan[/SIZE]

---

### Post by Darfeynt on 2010-08-14
[URL="http://ubuntuforums.org/member.php?u=784640"][SIZE=3][COLOR=Black]_hey juancarlospaco ya hice lo que dijiste pero como se que ya tengo todos los controladores instalados ?_[/COLOR][/SIZE]
[/URL]

---

### Post by Applelnx on 2010-08-14
Hola Darfeynt, creo que cuando vas a Sistema - Administracion - Controladores de Hardware, lo que te salen son los controladores privativos. Pero no estoy muy seguro de esto. Si queres una respuesta, deberias abrir un nuevo thread (verificando que no exista uno similar que te de la respuesta).

En cuanto al programa para quemar iso, yo uso el Brasero que viene por default. Si no, tenes tambien el k3b. De nuevo, si tenes dudas puntuales sobre esto, corresponderia que las plantees en un nuevo thread.

Saludos

---

### Post by guillermolisi on 2010-08-14
> **Darfeynt said:**
> [SIZE=3]hey gente de ubuntu me pueden dar una mano con eso de los controladores.
yo he intentando dandole clic en sistema[/SIZE],  [SIZE=3]luego en administracion, y por ultimo en controladores de hardware, el detalle es que solo me encuentra el controlador de video[/SIZE], [SIZE=3]entonces  no se si tengo que buscar por otro lado para poder encontrar los otros  controladores del procesador, lan, audio entre otros.[/SIZE]
[SIZE=3]sera que ya ubuntu los incluye?[/SIZE] [SIZE=3]porcierto en su opinion que quemador de isos les parece bueno?[/SIZE]

[SIZE=3]bueno eso es todo, un saludo desde colombia[/SIZE]..
[SIZE=3]todo bien se cuidan[/SIZE]
Y que placa/chip de video estas usando ?

Normalmente y salvo algunas pocas excepciones, Linux posee drivers para casi todo el hardware que se esta usando actualmente.

Sobre el tema grabadores de imagenes ISO abri otro thread ya que es off topic para este (no es driver un grabador de imagenes ISO).

Saludos a los ubunteros colombianos.

---

### Post by Darfeynt on 2010-08-14
[SIZE=2]jajaja si tienen toda la razon el tema de los isos no corresponde a este, me disculpo por ese detalle.
volviendo al tema estoy usando una place madre M4A785TD-V EVO y la CPU es un AMD phenom. por otra parte recuerdo que en windows uno abre el administrador de disposivos, y los controladores que faltan salen con un signo de interrogacion amarillo, para el caso de ubuntu instale un gestor de dispositivos y al ejecutarlo me sale un ventana muy similar a la de windows solo que esta muestra unos signos de interrogacion azules. no se si  esto significara que ese controlador esta faltando? supongo que si porque en windows si es asi[/SIZE],  [SIZE=2]tambien he entrado al centro de software de ubuntu pero salen tantos controladores que no se cual instalar [/SIZE]:confused:
[SIZE=2]
[COLOR=DarkRed]Applelnx[/COLOR] y [COLOR=DarkRed]Guillermolisi[/COLOR] Gracias por colaborarme en el tema [/SIZE]:D

---

### Post by guillermolisi on 2010-08-14
Vamos al foco de la cuestion.

En una consola/terminal ingresa el comando ```
sudo lshw
``` y mostra su larga salida.

El procesador no requiere drivers (como tambien sucede en Windows).

Luego, tenes sonido ? Funciona la red cableada y/o inalambrica ?

O sea, que es lo que no te funciona con Ubuntu ?

---

### Post by Darfeynt on 2010-08-14
[SIZE=2]no, ubuntu no me ha dado ningun problema; es que yo pensaba que el procesador requeria un driver, me daba la impresion de que si lo dejaba haci, mas adelante me daria problemas. pero vos decis que no se requiere. mmm me quitas un peso de encima gracias men 

saludos[/SIZE]

---

### Post by biale on 2010-08-14
> Normalmente y salvo algunas pocas excepciones, Linux posee drivers para casi todo el hardware que se esta usando actualmente.

Por las dudas no haya quedado claro: bajo Linux, en principio durante la instalación y el arranque, se seleccionan en forma automática los drivers adecuados al hardware. Es por eso que nos preocupamos solo cuando algo no funciona y todos te preguntan que es lo que no anda.

El caso del adaptador de video ("controladores de hardware") puede confundir. En realidad solo estarías reemplazando un driver ya instalado por otro driver, que podría ser mas adecuado.

Sin perjuicio del pedido que hizo Guillermo, en sistema/ administración/ controladores de hardware hay una forma de chequear que mas o menos todo este funcionando.

Un saludo a todos...

---

