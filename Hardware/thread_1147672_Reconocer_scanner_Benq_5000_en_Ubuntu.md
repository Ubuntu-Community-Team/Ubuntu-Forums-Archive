---
title: "Reconocer scanner Benq 5000 en Ubuntu"
date: 2009-05-03
forum: Hardware
---

### Post by cor_stellae on 2009-05-03
Hola gente:

Estoy tratando de lograr que mi Ubuntu reconozca todos mis periféricos. Hasta ahora, he tenido problemas para que el XSane reconozca mis Scanner Benq 5000. Lo puede ver, pero no lo puede cargar.

Por lo que encontré googleando, es posible cargar los drivers de Windows y que el Ubuntu los reconozca, pero no comprendí bien el [proceso]("http://www.ubuntu-es.org/index.php?q=node/93952#comment-265794") y, sobre todo, no funcionó cuando lo intenté, tal vez porque todavía soy muy novata con el uso de las consolas.

¿Alguien sabe cómo lograr que Ubuntu reconozca bien el BenQ?

---

### Post by pablo.s on 2009-05-03
Para comenzar, no estaría de
más que pruebes algo sencillo:

**[COLOR=DarkGreen]sudo xsane[/COLOR]**

en una terminal. Y ver que sucede.
Sino, vamos paso a paso con el
procedimiento que explican en
el otro foro..

---

### Post by Hei Ku on 2009-05-03
Movido a Hardware, porque el scanner se puede patear. ;)

Estaría bueno que postees el resultado de ejecutar lsusb en una terminal. De esa manera podemos tener mas datos sobre el scanner.

---

### Post by cor_stellae on 2009-05-03
Me temo que me están hablando un poco en "chino" o, para ser más exactos, en "Ubuntu"... A ver, Pablo, cuando pida la terminal y solicite "sudo xsane", ¿luego qué? ¿Nada más escribo eso....?

Hei Ku, cómo es eso de "movido a Hardware"... soy bastante nueva en Ubuntu (apenas hace tres días que con mucha ayuda de Pablo y José logré instalarlo exitosamente), así que no entiendo si es un comando que tengo que dar, tener el scanner desconectado o cuál otra misteriosa acción...

Muchas gracias por responder y por la paciencia de siempre.

---

### Post by Mauro22 on 2009-05-03
> Me temo que me están hablando un poco en "chino" o, para ser más exactos, en "Ubuntu"... A ver, Pablo, cuando pida la terminal y solicite "sudo xsane", ¿luego qué? ¿Nada más escribo eso....?


Para hacer eso, tenes que ir a 

Accesorios -> Terminal

alli pones:

sudo xsane le das enter y te va a pedir tu contraseña (tranqui que no se lo que escribis, pero ahi esta), das enter nuevamente y se abre el xsane y en la terminal van a ir apareciendo todos los "errores" o cosas interesantes. Copia y pegas esas "cosas".

> 
Hei Ku, cómo es eso de "movido a Hardware"... soy bastante nueva en Ubuntu (apenas hace tres días que con mucha ayuda de Pablo y José logré instalarlo exitosamente), así que no entiendo si es un comando que tengo que dar, tener el scanner desconectado o cuál otra misteriosa acción...

Como el scanner es algo que se puede patear (y si que dan ganas), Hei Ku lo movio al subforo "Hardware" donde se pone todo lo referido a todo lo que se puede patear jejej...

El comando que dice Hei Ku, es el comando lsusb (idem anterior) Terminar, lsusb enter. Sale un detalle de todo el hardware conectado a los usb (es usb el scanner ese ?? ), copia y pega aqui.


Saludos!! y vamos que linux no muerde!

---

### Post by pablo.s on 2009-05-03
Si, como primer paso tienes
que escribir **[COLOR=DarkGreen]sudo xsane[/COLOR]**, luego
te devuelve o un mensaje de
error o el programa (ejecutandose
como superusuario).

Lo que dice nuestro querido
administrador es que un scanner
es un aparato físico, por lo que
la categoria de la pregunta es
Hardware. A veces usa la ironia,
pero a mi me esta vedado el
uso de la ironia justamente por
abuso...

---

### Post by cor_stellae on 2009-05-03
Bien, ya lo hice y dice:
[snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.

---

### Post by Mauro22 on 2009-05-03
Segun eso falta el firmware del scanner que es un archivo .bin que viene junto al CD...


A ver quien mas tiene un scanner para opinar!??

---

### Post by cor_stellae on 2009-05-03
Sí, exacto, ahora, ¿cómo le instalo el firmware? Ya lo bajé de la página oficial y también tengo los drivers originales en su CD. Lo que no sé es cómo instalárselos a Ubuntu...

Digo... tomando en cuenta que no existe versión para Linux, y la compañía solamente ofrece los drivers para Windows  :(

---

### Post by josecuervo86 on 2009-05-03
Hola de nuevo, mira aca [0] esta la pagina de Sane con los drivers de tu scanner. No entiendo nada de configuracion de scanners, pero podes empezar por bajarlo y ver que pasa
[0] [URL="http://www.sane-project.org/sane-mfgs.html#Z-BENQ"]
http://www.sane-project.org/sane-mfgs.html#Z-BENQ[/URL]

---

### Post by pablo.s on 2009-05-03
Vamos paso a paso con el
procedimiento que cuentan
en el otro foro:

1) Bajate el archivo .bin de
[aqui]("http://latam.benq.com/support/downloads/downloads.cfm?product=305") (el archivo que dice
mirascanv501u07etcetc..)

2)Descomprimilo a una 
carpeta que se llame **scanner**
en tu escritorio

3)En la carpeta **scanner** va a
haber una carpeta llamada **Bin**

4)Abrís una terminal. Escribí
[COLOR=DarkGreen]**cd /home/[COLOR=DarkOrange]tu_nombre_de_usuario[/COLOR]/Escritorio/scanner/**[/COLOR][COLOR=DarkGreen]**MiraScan \v5.01u07**[/COLOR][COLOR=DarkGreen]**/Bin**[/COLOR]

5)Siguiendo en la misma terminal,
escribí [B][COLOR=DarkGreen]sudo mv u176v046.bin /usr/share/sane/snapscan/

[/COLOR][/B][COLOR=Black]6)Ahora escribís [/COLOR][B][COLOR=DarkGreen]sudo gedit /etc/sane.d/snapscan.conf

[/COLOR][/B][COLOR=DarkGreen][COLOR=Black]7)En la cuarta linea, donde dice
[COLOR=DarkOrange]***firmware /usr/share/sane/snapscan/your-firmwarefile.bin***[/COLOR]

lo cambias por  [/COLOR][/COLOR] [I][B][COLOR=DarkOrange]firmware /usr/share/sane/snapscan/u176v046.bin

[/COLOR][/B][/I][COLOR=Black]8) La linea donde dice:

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb[/COLOR][I][B][COLOR=DarkOrange]

[/COLOR][/B][/I][COLOR=Black]tiene que quedar asi:

# For USB scanners also specify bus=usb, e.g.
/dev/usb/scanner0 bus=usb[/COLOR][I][B][COLOR=DarkOrange]

[/COLOR][/B][/I][COLOR=Black]o sea le borras el numeral del
principio a la segunda linea[/COLOR][I][B][COLOR=DarkOrange]

[/COLOR][/B][/I][COLOR=Black]9) Con eso tendria que funciona[/COLOR][COLOR=Black]r[/COLOR][I][B][COLOR=DarkOrange]
[/COLOR][/B][/I]

---

### Post by cor_stellae on 2009-05-04
¡Muchas gracias, Pablo! Lo intentaré esta noche cuando regrese a casa; en este momento estoy en mi trabajo, con el odioso Windows, aunque estoy casi segura de que instalaré aquí Ubuntu dentro de Windows, porque me estoy haciendo adicta a algunos programitas que solo corren por allá. En la noche te cuento cómo me fue.

---

### Post by cor_stellae on 2009-05-04
Hola Pablo:

Estuve tratando de seguir el procedimiento paso por paso, pero cuando pongo esto en la terminal: [COLOR=DarkGreen]**cd /home/[COLOR=DarkOrange]tu_nombre_de_usuario[/COLOR]/Escritorio/scanner/**[/COLOR][COLOR=DarkGreen]**MiraScan \v5.01u07**[/COLOR][COLOR=DarkGreen]**/Bin**[/COLOR], me dice que "No existe el fichero o directorio".

Ya intenté de todas las maneras posibles y verifiqué que yo estuviera respetando todas las mayúsculas y espacios. ¿Qué puede estar sucediendo?

---

### Post by pablo.s on 2009-05-04
Donde dice tu_nombre_de_usuario
tienes que reemplazarlo por tu nombre
de usuario.
Por ejemplo, si fuera el mio, ahi
pondria cd /home/pablo/etc etc etc...

---

### Post by cor_stellae on 2009-05-04
Sí... desde luego, así fue como lo hice... pero igual no funciona...

---

### Post by josecuervo86 on 2009-05-04
Respetaste mayusculas y minusculas??

---

### Post by pablo.s on 2009-05-04
Prueba cambiar de nombre la
carpeta "**MiraScan v5.0...**"
por un nombre como **driver** y
asegurate de volver a escribir la
linea que antes no salia pero 
reemplazando donde dice **MiraScan**
por **driver**.

---

### Post by cor_stellae on 2009-05-04
Ya lo intenté de nuevo y nada... Respeto mayùsculas, minùsculas, espacios y dirección de la barra, pero nada...

---

### Post by pablo.s on 2009-05-04
Probaste con el cambio de nombre
que puse antes?
Es facil, renombra la carpeta
Mirascan (la que está dentro de
la carpeta scanner) y luego
cuando escribes la linea que no 
te sale le cambias de vuelta el
nombre...

---

### Post by staar on 2009-05-04
tu sistema está en inglés o español? fijate en tu carpeta personal (o home), tenés una carpeta que se llama Escritorio? o se llama Desktop?...

saludos

EDIT: hay un pequeñito error en esa linea: ```
cd /home/tu_nombre_de_usuario/Escritorio/scanner/MiraSca[COLOR="#ff0000"]n \v[/COLOR]5.01u07/Bin
```
debería ser:
```
cd /home/tu_nombre_de_usuario/Escritorio/scanner/MiraSca[COLOR="Red"]n\ v5[/COLOR].01u07/Bin
```

cuestión de los nombres de directorios con espacios y la terminal, nada grave, pero sino, no funca :-P

---

### Post by pablo.s on 2009-05-04
:oops:

Tarea para el hogar para mi mismo:
Escribir 100 veces: "No hay que presuponer
el idioma de la instalación"

Ni yo mismo lo tengo en español...

---

### Post by staar on 2009-05-05
jajaja, yo lo puse en español, y no me cambió el nombre de la carpeta al toque (bah, de ninguna del home), hay que reiniciar sesión, y a veces ni así lo hace, se queda en Desktop nomás, y hay que ir al gconf-editor...

PD: fijate que edite mi post, le pifiaste en la barra de la carpeta con espacio...

saludos

---

### Post by cor_stellae on 2009-05-05
Prosigue el misterio:

- Sí, tengo un Escritorio y no un Desktop. Solo por si acaso, también probé con Desktop y no funcionó.
- Sí, había probado el cambio de nombre
- No, ni cambiando el orden el espacio y el slash hay efecto alguno. ¿Habrá algo más ahí que deba cambiarse, la dirección del slash, otro espacio?

---

### Post by pablo.s on 2009-05-05
A ver vamoa a hacerlo a lo
bestia kamikaze bonzo:

Escribí en una terminal:

sudo nautilus

Ahi te abre una ventana con
los directorios siendo root.

copia el archivito que termina 
en .bin (**[COLOR=DarkGreen]u176v046.bin)[/COLOR]**que 
habia contado en el paso a paso
a la carpeta **[COLOR=DarkGreen]/usr/share/sane/snapscan/[/COLOR]**

---

### Post by cor_stellae on 2009-05-05
Okay... al pedir sudo nautilus se abre una ventana, en efecto, en root... lo que no veo ahí en ningún lugar es la carpeta [B][COLOR=DarkGreen]/usr/share/sane/snapscan/ 
[/COLOR][/B][COLOR=DarkGreen]
[COLOR=Black]¿Dónde está eso?[/COLOR][/COLOR][B][COLOR=DarkGreen]
[/COLOR][/B]

---

### Post by pablo.s on 2009-05-05
Tienes que subir hasta la barra
y ahi hay una carpeta llamada /usr,
dentro hay una llamada /share, 
dentro de esa hay una llamada /sane
y dentro de /sane hay una llamada
/snapscan.

Dentro de la última va el archivito
punto bin que está en la carpeta
que descomprimiste antes.

---

### Post by cor_stellae on 2009-05-05
Okay... ya logré encontrar casi todas las carpetas excepto la ùltima... Dentro de la carpeta "sane" no hay ninguna "snapscan". Solamente hay dos: gt68xx y xsane.

---

### Post by pablo.s on 2009-05-05
Bueno, vas a tener que hacer una
carpeta nueva con nombre **[COLOR=Black]snapscan[/COLOR]**.

Copia ahi dentro el archivo.

El tutorial este que me pasaste
está incompleto, eh.

---

### Post by cor_stellae on 2009-05-05
Casi casi... llegó más lejos que nunca, el scanner hasta comenzó a moverse, pero al final da un aviso de error: 

Falló al abrir dispositivo 'snapscan:libusb:002:003:Error durante E/S de dispositivo

---

### Post by cor_stellae on 2009-05-05
Aparte del error, el escáner comienza a tener un comportamiento errático: la lámpara se mueve, se queda a medio camino, llega hasta el final, se detiene... y ahí mejor lo desconecté cuando se quedó pegada y vibrando en lugar de regresar a la posición inicial...

Como para mí es muy tarde, me temo que esto quedará para mañana.

Muchas gracias!!!!

---

### Post by pablo.s on 2009-05-05
Buuuu :cry: me voy a dormir...
Mañana lo seguimos viendo!

---

### Post by euzkoarima on 2009-05-05
> **cor_stellae said:**
> Casi casi... llegó más lejos que nunca, el scanner hasta comenzó a moverse, pero al final da un aviso de error: 

Falló al abrir dispositivo 'snapscan:libusb:002:003:Error durante E/S de dispositivo

Hace poco instalé una impresora multifunción (o sea con scanner) y al abrir el xsane me daba error de E/S.

En el FAQ del fabricante dice:


> Ubuntu 8.04/8.04.1, 8.10
    1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file.
    2. Edit "0664" to "0666" in "USB devices" section.

    Before the edit---------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
    SUBSYSTEM=="usb_device",                MODE="0664"

    After the edit----------------------------------

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
    SUBSYSTEM=="usb_device",                MODE="0666"

    3. Restart the OS. 

y se arregló con eso. Ojalá sirva en tu caso.

Saludos,
Eduardo.

---

### Post by cor_stellae on 2009-05-07
Hola Eduardo:

Muchas gracias por la respuesta. Debo confesar que no lo he intentado, principalmente porque no entendí muy bien... Así somos las novatas. :)

---

### Post by staar on 2009-05-07
Traducción para novatas :-D:-D:

1- Alt + F2 (se abre el diálogo 'Ejecutar una aplicación')

2- ejecutar: gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules

3- buscar esto: > # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

4- cambiar ambos 4 por sendos 6, quedando así: > # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

5- guardar, cerrar y reiniciar

6- contar acá como fue

7- saludos

---

### Post by cor_stellae on 2009-05-07
Ja ja ja ja ja ja!!!! Mejor me río... logré llegar hasta la solicitud del archivo de permission.rules, pero salió en blanco....!!!!!! ¡Este escáner no se deja!!!!  :rolleyes:

---

### Post by staar on 2009-05-07
pregunta... estás segura que el firmware (el archivo .bin) que estás usando, es el correcto para tu scanner?

necesitariamos saber el modelo exacto, porque hay un Benq 5000, otro 5000u y otro 5000e (aparentemente, estos últimos son iguales entre sí, pero el primero, no), postea la salida de ```
lsusb
``` (con el scanner conectado)

te vino algún cd con el scanner, aunque sea con drivers para Ventanas? generalmente incluyen el firmware por algún lado...

saludos

---

### Post by cor_stellae on 2009-05-07
Ya coloqué el driver que viene en el disco original y no pasa nada... Sigue sin reconocer el escáner.

---

### Post by cor_stellae on 2009-05-07
Googleando y googleando, me encontré este tutorial para instalar drivers BenQ:

[http://www.ubuntu.org.uy/main/?q=node/261](http://www.ubuntu.org.uy/main/?q=node/261)

De hecho, ha funcionado muy bien, con la excepción de que cuando intento explorar o hacer vista previa el programa renuncia y obliga a renunciar a todas las aplicaciones que estén abiertas.

¿Alguna pista de por qué sucede?

Por cierto, volví a intentar seguir el procedimiento aquí para cambiar lo del USB y sigue saliendo en blanco el archivo de 40-rules.

---

### Post by cor_stellae on 2009-05-07
Parece que todavía me falta indicarle que se trata de un escáner USB. 

En otro foro dice: "luego de eso si tu scanner es usb tienes que indicarle que es usb y la localizacion del dispositivo los cual te pudes orientar dandole un lsusb"

¿Alguna pista de cómo se hace esto?

---

### Post by pablo.s on 2009-05-07
Escribe en una terminal

**[COLOR=DarkGreen]lsusb[/COLOR]**

---

### Post by cor_stellae on 2009-05-07
Sí... ya, me salen el escáner y mi webcam... ¿Eso es todo o hay que escribirle algo más?

---

### Post by pablo.s on 2009-05-07
Eso es todo lo que hace lsusb.

Es un comando que

**[COLOR=DarkGreen]l[/COLOR]**i**[COLOR=DarkGreen]s[/COLOR]**ta dispositivos **[COLOR=DarkGreen]USB[/COLOR]**

---

### Post by cor_stellae on 2009-05-07
A ver si te entiendo, Pablo:

Ahora, sabiendo lo que dice de mi escáner, tengo que modificar la siguiente línea:

[COLOR=Green]# For USB scanners also specify bus=usb, e.g.
/dev/usb/scanner0 bus=usb[/COLOR]

con la info de mi escáner...

¿Es así?

En ese caso, me imagino que lo que tengo que sustituir es "[COLOR=Green]scanner0[/COLOR]". 
Los datos que me da son:
Bus 002 Device 003 ID 04a5:20f8 Acer Peripherals Inc. (Now BenQ Corp.) BenQ500
0


¿Cuál de esos es el que tendría que poner arriba?

---

### Post by pablo.s on 2009-05-07
El scanner ya funciona, pero parece
que no funciona como debiera.

1) Si ejecutas sudo xsane:
¿Se cuelga igual?

2) Si desconectas la webcam:
¿Se cuelga igual?

---

### Post by cor_stellae on 2009-05-07
Respuestas:

1) Sí, se cuelga igual y además creo que dañó todo lo que había hecho, porque ahora ya no reconoce del todo al escáner... otra vez...

2) Sin la webcam, ya no reconoce a nadie...

---

### Post by staar on 2009-05-07
AVISO: no tenés que modificar donde dice scanner0, eso es un archivo de udev, no lo toques, el nombre es así (cualquier scanner usb que conectes va a usar esa ruta '/dev/usb/scanner' es donde el sistema busca ese tipo de dispositivos)
> **cor_stellae said:**
> Parece que todavía me falta indicarle que se trata de un escáner USB. 

En otro foro dice: "luego de eso si tu scanner es usb tienes que indicarle que es usb y la localizacion del dispositivo los cual te pudes orientar dandole un lsusb"

¿Alguna pista de cómo se hace esto?
eso ya lo hiciste al descomentar (borrar el # precedente) la línea > /dev/usb/scanner0 bus=usb en el snapscan.conf, estamos seguros ya que el scanner se movió y reaccionó al abrir sane, es decir que este programa lo buscó en el lugar correcto...

bueno, que firmware (archivo .bin en la carpeta /usr/share/sane/snapscan/) estás usando? porque el que te pasó pablo era para un Benq 5000u y vos tenés un Benq 5000, que no son iguales, y un firmware incorrecto puede terminar mal, y ser a causa del problema...

saludos

---

### Post by cor_stellae on 2009-05-07
Como ya dije antes... estoy usando el driver que venía en el disco instalador. De hecho, con el otro no funcionó del todo, esta vez cuando menos ya lo reconoce...

---

