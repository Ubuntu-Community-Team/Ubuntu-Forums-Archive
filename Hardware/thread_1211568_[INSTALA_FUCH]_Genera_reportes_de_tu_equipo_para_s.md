---
title: "[INSTALA FUCH] Genera reportes de tu equipo para solicitar ayuda"
date: 2009-07-12
forum: Hardware
---

### Post by pagondel on 2009-07-12
Junto con CrisitianVirtual, nos complacemos en presentarles la primera versión de Fuch (Foros Ubuntu Chile), un pequeño front end en Python, que planea facilitar dar soporte. Tan Solo se debe instalar y podrán encontrarlo en:

```
Aplicaciones/Herramientas del Sistema/Foros Ubuntu Chile
```

[IMG]http://img10.imageshack.us/img10/5715/pantallazoly.png[/IMG]

Tal y como dice nuestro amigo Patriciologico, esta idea surgió en base a la [idea original de tatadeluxe](https://wiki.ubuntu.com/ChileanTeam/ManualUbuntero/Script). hay que reconocerle y agradecerle sus aportes ;). Gracias Tata!

Y por si alguno quiere interiorizarse con el proyecto puede visitar [esta pagina](https://code.launchpad.net/~ubuntu-cl-foros/+junk/fuch) o bajar las fuentes por medio de bazaar:

```
bzr branch lp:~ubuntu-cl-foros/+junk/fuch
```

[EDIT]

Tenemos con nosotros la versión 2.0 =D! gracias al gran aporte de Fabio Durán!

[Descargala de aquí](http://pagondel.org/Descargas/fuch_2.0-1_all.deb)

PD: en tanto descubra como subir bien los archivos tendremos un PPA =D!


Enjoy!

---

### Post by cristianvirtual on 2009-07-12
weena pagondel! no me habias contado que ya lo habias empaquetado :p

---

### Post by nopersona on 2009-07-12
Genial, excelente aplicación. Yo le editaría el título por algo así como "Instalar Fuch antes de pedir ayuda", para oficializar el soporte por este medio. 

Felicitaciones por la iniciativa :p

---

### Post by moreback on 2009-07-14
Buena iniciativa, pero yo también corregiría la ortografía:

1. "entragará" por "entregará"
2. "podamo" por "podamos"

Saludos.

:-P

---

### Post by Carlos C on 2009-07-14
> **moreback said:**
> Buena iniciatiba, pero yo también corregiría la ortografía:

1. "entragará" por "entregará"
2. "podamo" por "podamos"

Saludos.

:-P
+1 :lolflag:

---

### Post by kamus on 2009-07-14
> **Carlos C said:**
> +1 :lolflag:

buenaa :guitar:

---

### Post by Patriciologico on 2009-07-22
Muy bueno! tambien voto por que cambies el titulo, para que piquen mas :p

¿Este proyecto tiene que ver con lo que hizo anteriormente tatadeluxe[1]?


Saludos!

[1] [https://wiki.ubuntu.com/ChileanTeam/ManualUbuntero/Script](https://wiki.ubuntu.com/ChileanTeam/ManualUbuntero/Script)

---

### Post by armagedonc on 2009-07-23
ortografia primero. :)

---

### Post by aledruetta on 2009-07-23
Está bueno!! Nos va a facilitar la vida a los que todavía nos perdemos un poco en la consola de comandos, y claro, también, a los que tienen que responder nuestras preguntas poco precisas.

---

### Post by pagondel on 2009-07-24
Nueva version de fuch =D!... tiene pequeñas correcciones, incluyendo las faltas de ortografia recalcadas por moreback... -_-u xD! A ver si ahora q toy de vacaciones tiene algunos cambios más drasticos!
Saludos!

---

### Post by jorval on 2009-07-24
¡Qué fantástico trabajo!. Recuerdo que cuando recién llegué a Ubuntu-cl Tata me guió para que empleara su excelente script para informar mi problema de conexión Wifi y de ello hasta me hizo reportar un bug mediante launchpad. Siempre dije que el único pero que le encontraba era el nombre, creo que se llamaba Manual Ubuntero, ahora veo que lo ha arreglado. Saludos.

---

### Post by ppellet on 2009-08-21
:KS¡Excelente!, lo acabo de instalar y funciona creo sin problemas en mi laptop
(por si sirve de algo: un Dell Inspiron 6400 con Ubuntu 9.04, ATI Technologies Inc Radeon Mobility X1400).

Saludos,

---

### Post by sergiom99 on 2009-09-01
Que buena iniciativa. Los felicito.

Se puede ampliar al resto de los sub-foros de habla castellana?

---

### Post by Patriciologico on 2009-09-01
> **sergiom99 said:**
> Que buena iniciativa. Los felicito.

Se puede ampliar al resto de los sub-foros de habla castellana?

Entiendo que esta licenciado bajo GPL, puedes ver las fuentes en [https://code.launchpad.net/~ubuntu-cl-foros/+junk/fuch](https://code.launchpad.net/~ubuntu-cl-foros/+junk/fuch) y adaptarlo segun la necesidad.

Saludos!

---

### Post by cristianvirtual on 2009-09-01
Como bien dice patriciologico, puedes descargarlo y modificarlo

pero más interesante sería que te unieras a trabajar con nosotros y nos ayudaras a mejorarlo y convertirlo en algo util para mas gente que solo el foro de chile. podriamos partir por "internacionalizarlo" para ingles y español :)
eres mas que bienvenido a sumarte :)
q opinas?

alguien más dijo "yo"??

---

### Post by Patriciologico on 2009-09-02
Excelente idea Cristian, no lo vi de ese modo :p Extendere la invitacion en los otros Team.

Pd: eso sera croosposting??

---

### Post by sergiom99 on 2009-09-02
> **cristianvirtual said:**
> Como bien dice patriciologico, puedes descargarlo y modificarlo

pero más interesante sería que te unieras a trabajar con nosotros y nos ayudaras a mejorarlo y convertirlo en algo util para mas gente que solo el foro de chile. podriamos partir por "internacionalizarlo" para ingles y español :)
eres mas que bienvenido a sumarte :)
q opinas?

alguien más dijo "yo"??

No se nada de programación (soy *casi* veterinario) pero sí puedo comenzar por probarlo y testearlo.

Seguramente alguno de Ubuntu-Ar también se prenda.

_**Update**_: Y acá les hago el primer reporte :)
En Kubuntu JJ no lo pude hacer funcionar. Lo instalé sin problemas desde el .deb adjunto al primer post, y al hacer clic en el icono del menu, no pasó nada. Fui a consola y
> sergio@kubuntu:~$ /usr/bin/fuch
/usr/bin/fuch: line 6: kdsudo: orden no encontrada

debería decir kdesudo?

---

### Post by cristianvirtual on 2009-09-02
> **sergiom99 said:**
> 
[...]
_**Update**_: Y acá les hago el primer reporte :)
En Kubuntu JJ no lo pude hacer funcionar. Lo instalé sin problemas desde el .deb adjunto al primer post, y al hacer clic en el icono del menu, no pasó nada. Fui a consola y

debería decir kdesudo?

toda la razon, ya esta reparado, ahora hay q esperar q pagondel lo empaquete

se me olvidaba decir **gracias** ;)

---

### Post by pagondel on 2009-09-02
Gracias sergiom99!
Hemos arreglado el error y reempaquetado, puedes descargarla donde mismo descargaste antes (solo q ahora es la version 1.02). Cuentanos como te va ;)!
Saludos!

---

### Post by sergiom99 on 2009-09-03
> **pagondel said:**
> Gracias sergiom99!
Hemos arreglado el error y reempaquetado, puedes descargarla donde mismo descargaste antes (solo q ahora es la version 1.02). Cuentanos como te va ;)!
Saludos!

Excelente, ahora sí funcionó.
Puedo sugerir features?
1. En la primera parte donde dice "Escritorio", se podría agregar versión del escritorio, de Ubuntu, del kernel, de Qt/Gtk.
2. Se podría armar un reporte de "Todo": Entorno del soft, hardware (dmidecode, lsusb/pci, etc, etc), mas los que ya estan de Audio, Video, Wifi, etc.
3. La información que recoge el comando 'ubuntu-bug', se puede utilizar para algo?

Gracias!
Un saludo- Sergio

PS: Pregunta: se puede armar un PPA en Launchpad para tenerlo como repo?

---

### Post by aolivares on 2009-09-06
A medida que iba leyendo pensé que sería genial tener un ppa de fuch (pagondel me gustaba el nombre original, pero mr tijeras pudo más :D ) 

Otra cosa, deberían cacarear un poco más este huevito. 

Los felicito!!

---

### Post by Blackaiser on 2009-10-16
Gracias por la aplicación, es genial, pero a modo de retroalimentación... soy novato en el área de Tux y no podía entender que diablos hacia FUCH o para que sirve hasta que lo instalé y probé... podrían agregar al título o en el encabezado algo como "GENERA REPORTES DE TU EQUIPO PARA SOLICITAR AYUDA EN EL FORO". 

Gracias por el esfuerzo... se agradece muchísimo.

---

### Post by Patriciologico on 2009-10-16
Gracias Blackaiser, por tu sugerencia, acogida.

Saludos!

---

### Post by tuxsarge on 2009-11-12
excelente apliación

Se las mandaron, se agradece

SAludos :D

---

### Post by kamus on 2010-01-12
Bueno, solo quería dar un recordatorio para animar un poco este thread... les cuento que el desarrollo de este proyecto, ahora llamado huuf se encuentra activo y pueden instalar la actual version desde [https://launchpad.net/huuf](https://launchpad.net/huuf) , donde pueden encontrar un repositorio ppa y las fuentes para descargar. No está demas decir que si quieren aportar al proyecto en la tarea que sea, será bienvenido(a)!.

Saludos!:o

---

